# Regression tests

## Purpose

The skill makes claims about 30 specific writing patterns. The regression tests check whether the skill can back those claims up: given text that's loaded with AI patterns, can it actually fix them without breaking the prose?

A traditional test suite won't work here. The skill's output depends on an LLM's judgment, so the test runner is itself a Claude agent. It applies the skill, then turns around and audits the result using the same 30 checks.

## Running the tests

In Claude Code, from the project root:

```
/regtest
```

This runs the slash command defined in `.claude/commands/regtest.md`. It processes every `.md` file in `tests/regression/corpus/`, writes per-file results to `tests/regression/results/`, and prints a summary table.

## How it works

Each corpus file goes through three phases:

### Phase 1: Fix

The agent reads the skill definition and applies it to the corpus text. It rewrites the text with all 30 warning signs addressed. The rewrite must preserve every core fact, keep structural elements (lists, headings), and follow the skill's rewrite principles.

When the original text uses marketing language with no real fact behind it (e.g., "powerful platform" for a fictional product), the agent substitutes a plausible concrete detail rather than leaving the vague word in place.

### Phase 2: Verify

The agent re-reads the skill and checks its own Phase 1 output against all 30 warning signs, as if reviewing someone else's work. This catches patterns that the fix pass introduced or missed. Each remaining violation is recorded with its W-number, severity, and the specific offending phrase.

### Phase 3: Readability

The agent checks that the fixed text still works as prose:

- Grammatically correct
- Coherent flow, no orphaned sentences
- Core meaning preserved from the original
- Genre intact (a product page still reads like a product page)

## Pass criteria

A text passes when:

- Zero High-severity violations remain
- Two or fewer Medium-severity violations remain
- Readability check passes

A text fails when any of those conditions isn't met.

## Corpus

Test inputs live in `tests/regression/corpus/`. Each file is plain markdown containing prose that exhibits AI writing patterns. The initial set of 11 texts covers blog posts, product pages, newsletters, LinkedIn posts, corporate memos, tutorials, pitch decks, self-help articles, product reviews, landing pages, and meeting summaries.

### Adding new texts

Drop a `.md` file in `tests/regression/corpus/`. The runner picks up every `.md` file in that directory automatically. No config file, no manifest, no registration step.

Naming convention: `{NN}-{short-name}.md` where `NN` is a two-digit number for sort order. The number doesn't affect test behavior; it just keeps the directory listing readable.

Good corpus additions target gaps: texts that exercise warning signs the current corpus doesn't cover, or genres where the skill struggles.

## Results

Per-run outputs go to `tests/regression/results/`. Each file contains the fixed text, any remaining violations, the readability verdict, and a pass/fail result. These files are gitignored since they're generated artifacts that vary between runs.

The summary table printed to the conversation looks like:

```
Text                  | High | Med | Low | Readable | Result
--------------------- | ---- | --- | --- | -------- | ------
01-blog-post          |    0 |   1 |   0 |      yes | PASS
02-product-page       |    0 |   0 |   2 |      yes | PASS
07-startup-pitch      |    1 |   0 |   0 |      yes | FAIL
```

## What failures mean

A failing text points to one of two problems:

1. **The skill definition is unclear.** The fix instructions for a warning sign are ambiguous enough that the agent can't apply them correctly. Fix the skill.
2. **The rewrite introduced new violations.** Fixing one pattern created another. This usually means the rewrite principles need a constraint added.

Either way, the fix belongs in `skills/deslop-text/SKILL.md`, not in the test runner.

## Limitations

The test runner is non-deterministic. The same corpus text can produce different results across runs because an LLM does the fixing and the judging. A text that passes one run might fail the next. Consistent failures are signal; occasional ones are noise.

The readability check is also LLM-judged. It catches gross problems (garbled sentences, lost meaning) but won't flag subtle tone shifts or awkward phrasing that a human reader would notice.

There's no per-warning-sign coverage tracking yet. The corpus covers most of the 30 signs, but there's no automated check confirming that every W-number appears in at least one corpus file.

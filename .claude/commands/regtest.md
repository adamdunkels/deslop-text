You are running a regression test for the deslop-text skill. The test checks whether the skill can actually fix the AI writing patterns it claims to detect.

## Setup

1. Read the skill definition from `skills/deslop-text/SKILL.md`. This contains the warning signs and rewrite principles used by each subagent.
2. Find all `.md` files under `tests/regression/corpus/` recursively. The corpus is organized into subdirectories by source (e.g. `corpus/claude/`, `corpus/chatgpt/`). Each `.md` file is a test input.

## Run each corpus file in a subagent

Spawn one subagent per corpus file. Run them in parallel (batch all Agent calls in one message).

Each subagent receives this prompt (fill in the bracketed values):

---

You are running a single regression test for the deslop-text skill.

Read the skill from `skills/deslop-text/SKILL.md`, then read the test input from `[corpus-file-path]`.

### Phase 1: Review original

Run the skill's warning signs against the original input text. For each warning sign, check independently and note every violation.

Record:
- Which warning signs have violations (by W-number)
- The severity of each (High / Medium / Low, per the skill's classification)
- The specific phrase that triggered it

### Phase 2: Fix

Apply the skill to the text. Follow the skill's instructions exactly: check all warning signs, then rewrite the text with all violations fixed. Produce the complete rewritten text.

Rules for fixing:
- Preserve every core fact and claim from the original. Do not invent new information.
- Preserve structural elements (bullet lists stay as lists, headings stay as headings).
- Follow the skill's rewrite principles — especially: every rewrite must preserve original meaning, marketing language must become specific and factual (not just a different adjective), and "not X, it is Y" keeps the Y.
- Where the skill says to replace marketing language with a specific factual claim but the original has no underlying fact to draw from, use a plausible concrete detail rather than leaving the vague adjective.

### Phase 3: Verify

Run the skill's warning signs against your Phase 2 output as if reviewing someone else's text. For each warning sign, check independently and note any remaining violations. Be strict — the point is to catch what Phase 2 missed.

Record:
- Which warning signs still have violations (by W-number)
- The severity of each (High / Medium / Low, per the skill's classification)
- The specific phrase that triggered it

### Phase 4: Readability

Check the Phase 2 output for:
- Grammatical correctness
- Coherent flow (no orphaned sentences, no abrupt jumps)
- Core meaning preserved from the original
- The text still makes sense as the type of writing it is (a product page still reads like a product page, a memo still reads like a memo)

Mark readable: yes or no. If no, note what broke.

### Output

Write the result to `tests/regression/results/[source]/[filename]-result.md` (create the subdirectory if needed) with this format:

```
# Result: [source]/[filename]

## Original violations

{list of W-numbers, severity, and the offending phrase}

**Totals: {high_count} High, {med_count} Medium, {low_count} Low**

## Fixed text

{the Phase 2 output}

## Remaining violations

{list of W-numbers, severity, and the offending phrase — or "None"}

## Readability

{yes/no, with notes if no}

## Verdict: {PASS or FAIL}
```

Then return a single summary line in exactly this format:
`[source]/[filename] | {before_high}/{before_med}/{before_low} | {after_high} | {after_med} | {after_low} | {yes/no} | {PASS/FAIL}`

---

### Pass criteria (include in each subagent prompt)

- **PASS**: zero High-severity violations remaining, no more than 2 Medium-severity violations remaining, and readability is yes.
- **FAIL**: any High-severity violation survives, or 3+ Medium-severity violations remain, or readability is no.

## Collect results

After all subagents complete, gather their summary lines and print a table:

```
Text                          | Before (H/M/L) | High | Med | Low | Readable | Result
----------------------------- | -------------- | ---- | --- | --- | -------- | ------
claude/01-blog-post           |        5/3/2   |    0 |   1 |   0 |      yes | PASS
chatgpt/03-email-newsletter   |        2/4/1   |    0 |   0 |   2 |      yes | PASS
...
```

## Final summary

End with one line: "{N} of {total} texts passed."

If any text failed, list which warning signs caused failures — these are candidates for skill improvement.

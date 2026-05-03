You are running a regression test for the deslop-text skill. The test checks whether the skill can actually fix the AI writing patterns it claims to detect.

## Setup

1. Read the skill definition from `skills/deslop-text/SKILL.md`. This contains the 30 warning signs and rewrite principles you will use.
2. List all `.md` files in `tests/regression/corpus/`. Each file is a test input — plain prose loaded with AI writing patterns.

## For each corpus file

Run three phases:

### Phase 1: Fix

Apply the skill to the text. Follow the skill's instructions exactly: check all 30 warning signs, then rewrite the text with all violations fixed. Produce the complete rewritten text.

Rules for fixing:
- Preserve every core fact and claim from the original. Do not invent new information.
- Preserve structural elements (bullet lists stay as lists, headings stay as headings).
- Follow the skill's rewrite principles — especially: every rewrite must preserve original meaning, marketing language must become specific and factual (not just a different adjective), and "not X, it is Y" keeps the Y.
- Where the skill says to replace marketing language with a specific factual claim but the original has no underlying fact to draw from, use a plausible concrete detail rather than leaving the vague adjective.

### Phase 2: Verify

Run the skill's 30 warning signs against your Phase 1 output as if reviewing someone else's text. For each warning sign, check independently and note any remaining violations. Be strict — the point is to catch what Phase 1 missed.

Record:
- Which warning signs still have violations (by W-number)
- The severity of each (High / Medium / Low, per the skill's classification)
- The specific phrase that triggered it

### Phase 3: Readability

Check the Phase 1 output for:
- Grammatical correctness
- Coherent flow (no orphaned sentences, no abrupt jumps)
- Core meaning preserved from the original
- The text still makes sense as the type of writing it is (a product page still reads like a product page, a memo still reads like a memo)

Mark readable: yes or no. If no, note what broke.

## Output

### Per-text results

Write each result to `tests/regression/results/{original-filename}-result.md` with this format:

```
# Result: {filename}

## Fixed text

{the Phase 1 output}

## Remaining violations

{list of W-numbers, severity, and the offending phrase — or "None"}

## Readability

{yes/no, with notes if no}

## Verdict: {PASS or FAIL}
```

### Summary table

After processing all files, print a summary table to the conversation:

```
Text                  | High | Med | Low | Readable | Result
--------------------- | ---- | --- | --- | -------- | ------
01-blog-post          |    0 |   1 |   0 |      yes | PASS
...
```

## Pass criteria

- **PASS**: zero High-severity violations remaining, no more than 2 Medium-severity violations remaining, and readability is yes.
- **FAIL**: any High-severity violation survives, or 3+ Medium-severity violations remain, or readability is no.

## Final summary

End with one line: "{N} of {total} texts passed."

If any text failed, list which warning signs caused failures — these are candidates for skill improvement.

# deslop-text

An Agent Skill that detects AI-generated writing patterns and fixes them.

AI text has a recognisable fingerprint: filler phrases, paired adjectives, marketing superlatives, metronomic sentence lengths, uncontracted verbs. Readers spot it instantly. This skill runs 30 checks against any prose and suggests concrete rewrites for every violation it finds.

## Install

Copy the skill into your project's `.claude/skills/` directory:

```bash
# From your project root
mkdir -p .claude/skills
cp -r path/to/deslop-text/skills/deslop-text .claude/skills/
```

Or for global availability across all projects:

```bash
mkdir -p ~/.claude/skills
cp -r path/to/deslop-text/skills/deslop-text ~/.claude/skills/
```

The skill activates when you ask your agent to review or deslop text.

## What it checks

30 warning signs, grouped by severity.

**High** (instant AI tells):
- W1 Filler phrases ("it's worth noting", "leverage", "nuanced")
- W2 "Not X, it is Y" contrastive framing
- W5 Marketing language ("powerful", "seamless", "revolutionary")
- W6 Generic openings ("In today's connected world...")
- W9 Paired adjectives ("simple yet powerful")
- W15 "Excited to announce" openers
- W16 "Whether you're X or Y" false inclusivity
- W17 Faux-conversational pivots ("Here's the thing:")
- W21 Corporate cliches ("move the needle", "synergy")
- W24 Triple-value lists ("excellence, collaboration, and innovation")

**Medium** (weaken the writing):
- W3 Em-dash overuse
- W4 Rhetorical questions as transitions
- W7 Passive voice as habit
- W8 Excessive hedging
- W10 Meta-references ("In this post...")
- W11 Mechanical transitions ("Furthermore", "Moreover")
- W12 Bold emphasis as selling technique
- W13 Scare quotes
- W14 Section-end summaries
- W18 Exclamation mark clusters
- W19 Repetitive "You" starters
- W22 Hashtag blocks
- W23 Emoji as emphasis
- W25 Informal corporate slang
- W26 Uncontracted forms throughout
- W30 Heading emoji

**Low** (matter in aggregate):
- W20 The word "very"
- W27 Typographic/curly quotes
- W28 Repetitive word use
- W29 Sentence length uniformity

## How it works

The skill reviews text in two modes:

**Review mode** — reports violations with citations and suggested rewrites, grouped by severity. Ends with a count: "X violations found across Y of 30 checks."

**Fix mode** — applies all rewrites and returns the cleaned text.

Core principles:
- Rewrites preserve the original meaning. Removing slop does not mean changing what the text says.
- Marketing language must become specific and factual, not just softer marketing language.
- When violations overlap in one sentence, one combined rewrite replaces them all.
- Clean text is not bland text. The goal is writing with a specific voice, not writing with all personality removed.

## Compatibility

This skill follows the [Agent Skills open standard](https://agentskills.io). It works with any tool that supports the standard: Claude Code, Cursor, GitHub Copilot, Gemini CLI, and others.

## License

MIT

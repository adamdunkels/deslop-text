# deslop-text — Overview

## What it does

deslop-text is an Agent Skill that reviews written text for AI-generated writing patterns and fixes them. It checks 32 specific warning signs — filler phrases, marketing language, passive voice, hedging, paired adjectives, repeated thematic points, internet cliches, and other patterns that make prose immediately recognisable as machine-generated.

## Project structure

```
deslop-text/
├── CLAUDE.md                     # Project guardrails
├── LICENSE                       # MIT
├── README.md                     # Public-facing docs and install instructions
├── .gitignore
├── .claude/
│   └── commands/
│       └── regtest.md            # Slash command to run regression tests
├── .claude-plugin/
│   └── marketplace.json          # Agent Skills marketplace metadata
├── skills/
│   └── deslop-text/
│       └── SKILL.md              # The skill itself — this is the core artifact
├── tests/
│   └── regression/
│       ├── corpus/               # Input texts with AI patterns (add .md files here)
│       └── results/              # Generated per run (gitignored)
├── docs/
│   ├── overview.md               # This file
│   ├── proposed-claude-md-additions.md
│   └── deep-dive/                # Subsystem docs (added as project grows)
```

## Skill format

The skill follows the Agent Skills open standard (agentskills.io). The entry point is `skills/deslop-text/SKILL.md` with YAML frontmatter:

```yaml
---
name: deslop-text
description: Review written text for AI-generated writing patterns and fix them.
---
```

The body contains instructions, the 32 warning signs, severity classification, and rewrite principles.

## Distribution

- **GitHub**: clone or download, copy `skills/deslop-text/` to your `.claude/skills/` directory
- **Marketplace**: `.claude-plugin/marketplace.json` enables distribution through Agent Skills marketplaces

## Compatibility

The Agent Skills standard works across 40+ tools: Claude Code, Cursor, GitHub Copilot, Gemini CLI, and others. Any tool that reads SKILL.md files can use this skill.

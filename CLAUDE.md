# CLAUDE.md — deslop-text

## What this project is

An open-source Agent Skill that detects and fixes AI-generated writing patterns. The skill works across any tool that supports the Agent Skills open standard (Claude Code, Cursor, GitHub Copilot, Gemini CLI, and others).

The core artifact is `skills/deslop-text/SKILL.md` — a structured checklist of 30 warning signs that make text immediately recognisable as machine-generated. The skill reviews prose, flags violations by severity, and suggests concrete rewrites.

---

## Mandatory rules

### Writing style — no AI-isms

> This project is a tool for removing AI writing patterns. Everything written in this repo must pass its own checks.

- No filler phrases, marketing language, or corporate cliches.
- No em-dashes for dramatic effect. No rhetorical questions as transitions.
- No "not X, it is Y" constructions. Say what it is.
- No paired adjectives joined by "yet"/"and".
- No generic openings, meta-references, or section-end summaries.
- No exclamation mark clusters. No emoji unless requested.
- No hedging. Commit to claims or cut them.
- Use contractions. Write like a person.
- **Post-draft review is mandatory.** After writing any text a human will read, review against the 30 warning signs in the skill before presenting it.

### Documentation

- The `docs/` tree is the source of truth for how this project works.
- Every change to the skill or project structure must update the relevant `docs/` files.
- Deep-dive docs must be sufficient on their own — a new contributor should understand the project by reading `docs/` without reading source files.

### Secrets

- Secrets never enter the repo. API keys, tokens, and credentials live in environment variables or gitignored `.env.local` files.

### Regression tests

- After any change to `skills/deslop-text/SKILL.md`, run `/regtest` and confirm all texts pass before presenting the change as done.

### Code changes

- Surgical edits only. Do not refactor, rename, or restructure unless asked.
- Do not add features beyond what was asked for.
- Default to writing no comments. Only add one when the WHY is non-obvious.

### `.gitignore`

- When a change introduces a new build output, dependency directory, or secret-bearing file pattern, add the corresponding entry to `.gitignore` in the same step.

---

## When in doubt

- Ask the user before proceeding.
- Never fabricate facts. Say "I don't know" when uncertain.
- Prefer doing less over doing more.

---

## Things to never do

- Do not modify `CLAUDE.md` without explicit approval. Proposed additions go to `docs/proposed-claude-md-additions.md`.
- Do not push to any remote branch without being asked.
- Do not install packages globally.

---

## Documentation Map

- Rules and guardrails: `CLAUDE.md` (this file)
- `docs/overview.md` — project structure, skill format, distribution
- `docs/deep-dive/regression-tests.md` — how the agent-driven regression tests work, corpus format, pass criteria

# YGG Sui Bootcamp (2 Days)

Hands-on lesson material for the 2026 YGG Philippines Sui + Move bootcamp.

This repository is designed for **AI-assisted learning**: you do not just get answers, you get guided prompts that help you think, attempt, and retain.

## What This Repo Is For

- Teaching Sui + Move fundamentals through instructor slides and exercises
- Moving learners from concepts to shipping on devnet/testnet
- Practicing clean smart contract thinking: object modeling, abilities, access control, and testing
- Running a homework/hackathon workflow around verifiable contribution systems

## Learning Outcomes

By the end of the bootcamp, learners should be able to:

- Explain Sui's object-centric model and why it differs from account-centric chains
- Build and test basic Move modules safely
- Publish packages and interact with on-chain state
- Use the Sui TypeScript SDK for reads and transactions
- Design a simple on-chain product with stronger trust guarantees

## Repository Layout

- `slides/bootcamp.md` - main Day 1 + Day 2 bootcamp deck (Marp markdown source)
- `slides/homework.md` - homework brief and submission flow
- `slides/README.md` - how to preview/export slides with Marp
- `ai/core/` - canonical AI learning rule(s)
- `ai/adapters/` - model-specific adapters that point to canonical rules
- `ai/registry/` - indexes for rules, adapters, and skills

## AI-Assisted Learning Setup

This project is intentionally configured with one teaching guardrail across tools:

- Rule: `ai/core/socratic-first-response.md`
- Policy: first response should guide recall and attempt first (Socratic), not instantly dump full solutions
- Goal: improve long-term understanding, debugging habits, and transfer learning

### How The AI Rules Are Wired

Entrypoints in each agent environment load adapters, and adapters load canonical rules:

- Cursor: `.cursor/rules/socratic-first-response.mdc` -> `ai/adapters/cursor/rules/socratic-first-response.mdc`
- Claude: `CLAUDE.md` -> `ai/adapters/claude/CLAUDE.md`
- Codex: `AGENTS.md` -> `ai/adapters/codex/AGENTS.md`
- Canonical source of truth: `ai/core/socratic-first-response.md`

This keeps behavior consistent even if you switch assistants.

## Prompting Style For Better Learning

Use this format when asking AI for help:

1. **Context** - what you are building and current file/module
2. **Attempt** - what you already tried (code, command, reasoning)
3. **Blocker** - exact error, confusion, or failing test
4. **Ask type** - hint first, targeted fix, or full answer

Example:

```text
I am implementing a soulbound passport module in Move.
I tried enforcing non-transfer by removing `store`, but I still do not trust my transfer path.
Current blocker: I am unsure if a public transfer function can still leak through another module.
Give me hints + checks first, then a full fix only if I ask again.
```

## Recommended AI Learning Loop

- Read a concept from the slide deck
- Attempt implementation yourself
- Ask AI for hints and diagnostic questions first
- Revise and re-run tests/commands
- Ask for full solution only after your second attempt when needed

This loop is slower at first but dramatically better for retention and interview readiness.

## Working With Slides

To preview/export slides, follow instructions in `slides/README.md`.

Quick start:

```bash
# Install Marp CLI
npm install -g @marp-team/marp-cli

# Export the main deck
marp slides/bootcamp.md --html -o slides/bootcamp.html
marp slides/bootcamp.md --html --pdf -o slides/bootcamp.pdf
```

## Homework

Homework details live in `slides/homework.md`.

Core expectation: publish a Move package to devnet/testnet and submit your package ID with proof.

## Notes For Maintainers

- Keep learning rules canonical in `ai/core/`
- Keep tool-specific files as thin adapters only
- Update `ai/registry/*.yaml` when rule wiring changes

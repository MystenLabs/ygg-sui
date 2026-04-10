# AI Governance Layout

Single source of truth lives in `ai/core/`.

- Rules registry: `ai/registry/rules-index.yaml`
- Skills registry: `ai/registry/skills-index.yaml`
- Adapter map: `ai/registry/adapters-index.yaml`

Tool entrypoints (`CLAUDE.md`, `.cursor/rules/*.mdc`, `AGENTS.md`, `CODEX.md`) must only point to adapter files.
Adapter files must only point to canonical files in `ai/core/` (rules) or `ai/skills/` (skills).

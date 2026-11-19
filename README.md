# altr-kit

A collection of tool configs, code snippets and prompt snippets that I reuse across projects.

- `.agents/skills/` — vendored agent skills, linked into `.claude/skills/`. Reinstall with `mise run skills`.
- `prompts/` — prompts to paste into a session: `coding/` for project work, `generative/` for image generation (with example outputs).
- `assets/` — shared CSS and JS for HTML documents (themes, code highlighting, diagrams, glossary cards). The setup prompt downloads them into a project's `docs/shared/`.
- `tools/` — shared tool configs: `mise.toml` and `ruff.toml`.

## Coding prompts

- [Set up a project](prompts/coding/setup-project.md) — sets up local-issue skills and adds project docs, HTML document rules, records and tool conventions to `CLAUDE.md`.
- [Implement tickets](prompts/coding/implement.md) — works through a feature's tickets one at a time, with a fresh subagent per ticket.

## Tools

- [mise.toml](tools/mise.toml) — pinned tool versions (bun, just, node, uv) and tasks to install the agent skills (`mise run skills`) and the altr-skills plugin (`mise run plugins`).

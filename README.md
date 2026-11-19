# altr-kit

A collection of tool configs, code snippets and prompt snippets that I reuse across projects.

- `prompts/` — prompts to paste into a session: `coding/` for project work, `generative/` for image generation (with example outputs).
- `assets/` — shared CSS and JS for HTML documents (themes, code highlighting, diagrams, glossary cards). The setup prompt downloads them into a project's `docs/shared/`.
- `tools/` — shared tool configs: `mise.toml`, `ruff.toml` and a `gitignore` template.

## Coding prompts

- [Set up a project](prompts/coding/setup-project.md) — sets up local-issue skills and adds project docs, HTML document rules, records and tool conventions to `CLAUDE.md`.
- [Implement tickets](prompts/coding/implement.md) — works through a feature's tickets one at a time, with a fresh subagent per ticket.

## Tools

- [mise.toml](tools/mise.toml) — pinned tool versions (bun, just, node, uv) and tasks to install the agent skills (`mise run skills`) and the altr-skills plugin (`mise run plugins`).
- [gitignore](tools/gitignore) — basic ignore rules for OS, editor, Python, Jupyter, Node, secret and Claude Code local files. The setup prompt merges it into a project's `.gitignore`.

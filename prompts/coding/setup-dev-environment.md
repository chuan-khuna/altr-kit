# Set up the dev environment

How to install the plugins that the coding prompts use. Do this before you run
[Set up a project](setup-project.md).

## pstack

pstack is Cursor's plugin of agent skills and subagents. It comes from the `cursor-plugins`
marketplace (`cursor/plugins` on GitHub).

### Choose a scope

| Scope | Settings file | Who gets it | Commit it? |
| --- | --- | --- | --- |
| `local` | `.claude/settings.local.json` | Only you, only in this project | No (gitignored) |
| `project` | `.claude/settings.json` | Everyone who opens this project | Yes |
| `user` | `~/.claude/settings.json` | Only you, in every project | — |

- Use `local` to try pstack in one project without changing the project for others.
- Use `project` when the whole team uses pstack in this project.
- Use `user` when you want pstack everywhere.

### Install

1. Go to the project root. (Skip this step for the `user` scope.)
2. Run the three commands for your scope.

**Local** (or run `mise run pstack` with [`tools/mise.toml`](../../tools/mise.toml))

```sh
claude plugin marketplace add cursor/plugins --scope local
claude plugin install pstack@cursor-plugins --scope local
claude plugin update pstack@cursor-plugins --scope local
```

**Project**

```sh
claude plugin marketplace add cursor/plugins --scope project
claude plugin install pstack@cursor-plugins --scope project
claude plugin update pstack@cursor-plugins --scope project
```

**User**

```sh
claude plugin marketplace add cursor/plugins --scope user
claude plugin install pstack@cursor-plugins --scope user
claude plugin update pstack@cursor-plugins --scope user
```

The first command adds the marketplace. The second installs pstack. The third updates
pstack to the latest version; run it again later to upgrade.

### Configure

1. Start a new Claude Code session.
2. Run `/setup-pstack` to choose which models pstack uses for each role.

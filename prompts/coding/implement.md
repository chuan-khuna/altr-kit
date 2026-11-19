# Implement tickets

Prompts that work through a feature's tickets one at a time, with a fresh subagent per ticket.

**How to use:** pick a variant, copy its block, and replace `<feature-slug>` with the folder
under `.scratch/`.

| Variant | Use when |
| --- | --- |
| [A. With `/implement`, TDD and review](#a-with-implement-tdd-and-review) | You want tests written first and a `/code-review` pass on every ticket |
| [B. Plain](#b-plain) | You want a faster run: implement, typecheck, test, commit |

---

## A. With `/implement`, TDD and review

```text
/implement @.scratch/<feature-slug>

Implement every ticket in issues/, one at a time:

- Spawn a fresh subagent for each ticket. Start one only after the previous one has finished.
- Go in dependency order (the "Blocked by" lines). When there's a tie, take the lowest number
  first.
- Each subagent: write tests first with /tdd, run typecheck and tests, run /code-review and fix
  what it finds, set the ticket's Status to resolved, then commit and push to the current branch.
- Skip tickets that need credentials, live infrastructure or a decision from me (e.g. deploy).
  List them at the end.
- If a subagent gets blocked or tests fail, stop and tell me. Don't move on to the next ticket.
- After each ticket, give me a one-line update: ticket, commit SHA, test result.
```

---

## B. Plain

```text
@.scratch/<feature-slug>

Implement every ticket, one at a time:

- Spawn a fresh subagent for each ticket. Start one only after the previous one has finished.
- Go in dependency order (the "Blocked by" lines). When there's a tie, take the lowest number
  first.
- Each subagent: read the ticket and the spec, implement it, run typecheck and the tests,
  set the ticket's Status to resolved, then commit and push to the current branch.
- Skip tickets that need credentials, live infrastructure or a decision from me (e.g. deploy).
  List them at the end.
- If a subagent gets blocked or tests fail, stop and tell me. Don't move on to the next ticket.
- After each ticket, give me a one-line update: ticket, commit SHA, test result.
```

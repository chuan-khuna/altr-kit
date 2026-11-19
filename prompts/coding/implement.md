/implement `@.scratch/<feature-slug>`

```
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

`@.scratch/<feature-slug>`

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

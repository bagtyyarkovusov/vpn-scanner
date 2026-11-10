# Issue tracker

GitHub Issues on `bagtyyarkovusov/vpn-scanner` holds specs, tickets and bug reports.
<!-- kickoff: Set GITHUB_REPOSITORY to owner/repo after confirming repository identity. -->
Use [GitHub operations](github-operations.md) for CLI reads and writes.
Use [domain terms](domain.md) in titles and acceptance criteria.
Private repositories still require secret-safe issue bodies and screenshots.

## Ticket shape

`to-spec` writes the parent spec; `to-tickets` produces the dependency graph.
Each ticket describes a vertical slice a PR can finish under the
[delivery contract](coding-workflow.md#delivery-contract).
Write outcomes and acceptance criteria; avoid speculative implementation inventories.

```markdown
## Parent
#<spec issue>, or None.

## What to build
The behavior this ticket makes work, and for whom.

## Acceptance criteria
- [ ] Observable outcome.
- [ ] Failure/recovery outcome, when relevant.

## Blocked by
#<issue>, or None; omit when native dependency links record this.
```

For bugs, include reproduction, observed/expected behavior and relevant environment.
Include proof expectations and explicit exclusions when they constrain delivery.
Use native sub-issues/dependencies where available; otherwise preserve edges in the body.
Start only after all blocking tickets are resolved; a readiness label alone is insufficient.

## Intake

When a skill says "publish to the issue tracker", create a GitHub issue.
When it says "fetch the ticket", read its full criteria and governing discussion.
Use `triage` and exactly one [triage label](triage-labels.md).
Requests enter as issues; PRs show implementation and proof.
Close completed tickets through the PR closing reference.
For work declined without implementation, explain why and close as not planned.

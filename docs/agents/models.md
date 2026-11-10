# Models and effort

This is the kit default; the project may override it explicitly here.
Keep model selection separate from the [delivery workflow](coding-workflow.md).

## Default model

Project override, founder decision 2026-11-10: use Claude for all agent work for
now, including implementation, research, `sol-loop` review and `babysit-pr` fixes.
Delegates run on the session's own Claude model.
Reason: the Codex provider failed its capability check on the founder's machine
that day (app-server exits on a missing `@openai/codex-darwin-arm64` dependency).
Sol 6.1 (`gpt-6.1-sol`, Codex provider) stays the intended model for later
analysis. Return to it only when the founder says so and the provider passes the
capability check.
If Claude is unavailable, ask; never silently switch.

## Effort

| Work | Effort |
|---|---|
| Lookups, simple research, mechanical edits | `low` |
| Implementation, `sol-loop`, babysit fixes | `medium` |
| Auth, permissions, migrations, data deletion, payments, concurrency | `xhigh` |
| Council | `high` |

Sol uses `reasoningEffort`; Opus uses `effort`.
Use no max/ultra, Fast mode or priority tier unless asked.
Check available providers and options through the
[environment delegation procedure](environment.md#delegation-and-background-work).

## Council

Use these members at `high` effort:

- Sol 6.1: `gpt-6.1-sol`, Codex provider.
- Opus 5.5: `claude-opus-5-5`, Claude provider.
- Muse Wonder 1.0: `muse-wonder-1.0`, Muse Code provider.

If a member is unavailable, run with reachable members and name the missing ones.
While the override above is in force, that includes Sol.

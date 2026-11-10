# vpn-scanner agent instructions

<!-- kickoff: Set PROJECT_NAME from the product goal; add only essential project routing. -->
Read the request and acceptance criteria, then the owning source and tests.
[Domain guidance](docs/agents/domain.md) explains document authority and vocabulary.
Configuration owns commands and versions; inspect it before running tools.
Follow the [delivery workflow](docs/agents/coding-workflow.md) for every change.

| When working on | Read before acting |
|---|---|
| Domain logic, ownership or documentation | [Domain guidance](docs/agents/domain.md) |
| Modules, behavior, tests or standards review | [Coding standards](docs/agents/coding-standards.md) |
| External dependency or service | [Documentation lookups](docs/agents/documentation-lookups.md) |
| Model choice, delegation or review effort | [Models and effort](docs/agents/models.md) |
| Running the stack, signing in or proving runtime behavior | [Local testing](docs/agents/local-testing.md) |
| Devices, browser, Docker, CI, hosting or deploys | [Environment](docs/agents/environment.md) |
| Issues, scope or readiness | [Issue tracker](docs/agents/issue-tracker.md) and [triage labels](docs/agents/triage-labels.md) |
| GitHub reads, writes or PR waits | [GitHub operations](docs/agents/github-operations.md) |
| Screens, navigation or user interactions | Affected source, tests, approved issue and the UI review requirements in the delivery workflow |

## Skills and harness

Project skills live in `.claude/skills/`.
Track `.agents/skills` as a relative symlink to `../.claude/skills` for Codex.
Claude Code reads `.claude/skills`; Codex reads `.agents/skills`.
Open the installed `SKILL.md` manually when the host cannot discover a named skill.
Per-project kit skills must not also be global: personal skills can override them.
Only `kickoff` and unrelated personal skills stay global.
`.agent-kit.json` records the kit commit, installed skills and sets, chosen extras,
and the source kit commit for each applied template file.

T3 Code is the reference harness for the machine-level examples below. If another
host is used, follow its equivalent device, browser, delegation and secret tools;
the guide names the fallback and permission boundary in
[Environment](docs/agents/environment.md#machine-level).

Write only in your own worktree or `/tmp`. Preserve unrelated changes.
Report host guard refusals without retrying through another tool.

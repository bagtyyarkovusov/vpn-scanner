# Environment

This guide owns tool use and permission boundaries.
[Local testing](local-testing.md) owns the project run/sign-in procedure.

## Machine-level

T3 Code and macOS are the reference harness examples. On another host, inspect
its available device, browser, delegation and secret tools and use their supported
equivalents; report missing capabilities and keep the permission boundaries below.
Outside T3, use plain CLI equivalents supported by the host.

### Devices

Use iOS Simulator or Android Emulator according to the ticket and project setup.
In T3, call `device_list`, then `device_open` with `hostId` and device `id`.
Use the returned `agent-device` command for every app launch/relaunch, deep link,
tap, text entry, alert, setting, snapshot, screenshot and recording.
Open the app before taking snapshots or input; inspect `help <command>` for options.
Use `device_screenshot` to look at the screen and refresh element refs after navigation.
Use neither `simctl`, `idb` nor `adb` for UI. Build/install tools may collect logs, forward
ports and perform operations unavailable through agent-device.
For a remote device, use the same tools; drive over SSH only when explicitly asked.
If a device tool fails, quote the error and follow its advice once.
If it still fails, report and stop device work. Never reuse or close another session.
Release only your own device session when finished.

### Browser and visuals

Use `preview_*` only when asked for browser work, including a named page or tab.
Start with `preview_status`, then `preview_open` if no tab can be automated.
Prefer snapshot locators. Switch browsers only when tools are absent, opening is
unsupported, the user asks, or two preview calls fail on one step; quote the error.
For public-page reading without a browser request, use fetch/search.
Close tabs you opened unless the user asked for them or uses them.
For requested visuals or trend/comparison charts, pass HTML to `html_preview`,
then `html_render`; do not start a server just to display them.
For an image intended for posting or use elsewhere, provide a PNG file and path.

### Delegation and background work

Ordinary coding needs no orchestration tools. Delegate only when the task or
applicable skill calls for it; obey a request to work without delegates.
Use native subagents for same-provider work with inherited settings that finishes
this turn. Use `delegate_task` for another provider, requested settings, a separate
checkout (`isolation: "worktree"`), background work, or an explicit tool request.
Call `orchestrator_capabilities` once before the first delegate; settings belong
in `target.options`. Let the tool create child worktrees.
Follow a delegate's returned `next`; never poll its status or sleep for it.
Start each delegate review/re-check as a new task; fix small findings yourself.
Cancel replaced or unneeded delegates with `task_cancel`, never by interrupting
the child thread. Given a thread ID, read it with `t3_thread_read` before answering
about it; reference the returned thread link.
Create top-level threads only when the founder asks for a new thread.
Use `t3_background_wait` for supported background-command completion.
[Models](models.md) owns model and effort selection.

### Local tools and secrets

Docker is the local dependency sandbox. Inspect existing containers, ports and
worktree ownership before starting another stack; stop only processes you own.
Use an isolated local database for destructive tests and disposable fixtures.
`gh` uses existing authentication; [GitHub operations](github-operations.md) owns usage.
For a configured project, use its hosting provider CLI or API for status/logs/metrics
and its mobile-build provider CLI or API for profiles; Railway and EAS are examples,
not defaults.
Inspect the selected project and environment before any remote command.
Use `request_secret` for secrets in T3; pass its secret reference to tools or request
file delivery for shell use. Outside T3, use the host's secure credential mechanism.
Keep credentials, tokens and personal data out of output, commits and screenshots.

## Permissions

Within authorized task scope, agents may inspect source and remote status/logs,
edit in their worktree, run local checks, build/install development apps, start or
stop their local processes, migrate/seed/reset isolated local test data, and rerun CI.
Do not destroy a shared Docker volume as if it were an isolated test database.
PR merge authorization follows the [delivery contract](coding-workflow.md#delivery-contract).

Ask the founder before:

- Production deploys or data deletion/resets outside the local stack.
- Any hosting or mobile-build provider settings/variables, new services or environments
  (including Railway, EAS, Vercel and Fly).
- Store submissions, paid services or billable infrastructure/builds, or legal commitments.
- Force-pushing another person's branch or closing another person's PR.
- Deleting shared Docker volumes or changing shared CI/protection settings.

Existing explicit authorization covers the named action; do not ask again.
Report host guard refusals through the rule in [AGENTS.md](../../AGENTS.md).

## Project-level

Kickoff fills this section from grilling; use `not used` for absent services.
Do not infer that these services exist from the machine tool list.

| Fact | Project value |
|---|---|
| Toolchain/config entry point | {{TOOLCHAIN_CONFIG}} |
| Local services and port allocation | {{LOCAL_SERVICES}} |
| Hosting provider, project and services | {{HOSTING_SERVICES}} |
| Staging URL | {{STAGING_URL}} |
| Production URL | {{PRODUCTION_URL}} |
| Mobile-build provider, project and profiles | {{MOBILE_BUILD_PROFILES}} |
| Simulator/device targets and app identifiers | {{DEVICE_SETUP}} |
| Deployment triggers, migrations and rollback runbook | {{DEPLOYMENT_SETUP}} |
| CI lanes and required checks | {{CI_CHECKS}} |

<!-- kickoff: Grill stack, hosting and platforms; fill each value or mark not used.
Record identifiers and config paths, never credential values. Scaffold tickets
establish actual commands, CI and deployment behavior before these are claimed ready. -->

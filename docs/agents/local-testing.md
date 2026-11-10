# Local testing

<!-- kickoff: Fill from stack and proof grilling; verify commands during scaffold tickets.
Use not used for absent surfaces. Preserve gaps as explicit scaffold acceptance criteria. -->
This is the executable local runbook. [Environment](environment.md) owns device,
browser, secrets and permission rules; do not duplicate those tool instructions here.

## Prepare

- Install dependencies with the configured package manager: {{INSTALL_COMMAND}}.
- Create ignored local environment files from: {{ENV_SETUP}}.
- Start dependencies and apply local migrations/seeds: {{LOCAL_DATA_SETUP}}.
- Check existing processes and ports against Environment's project-level table.

Keep local configuration pointed at isolated development services.
Never copy production data into a local fixture without explicit authorization.

## Run the stack

Start from your own worktree using: {{START_COMMANDS}}.
Confirm readiness using: {{READINESS_CHECKS}}.
Record which process serves which worktree; a running server may serve another checkout.
Use background execution supported by the harness and keep logs under `/tmp`.

## Sign in

Local test account roles and safe provisioning: {{TEST_ACCOUNTS}}.
Sign-in flow and local-only code/credential retrieval: {{LOCAL_SIGN_IN}}.
Admin or privileged test flow: {{PRIVILEGED_SIGN_IN}}.
Describe secret retrieval, never secret values. Use synthetic accounts.
Keep sessions when safe instead of repeatedly consuming rate-limited sign-in codes.

## Simulator or emulator flow

Preferred platform, target and app identifier come from Environment's device setup.
Build/install and development-server connection: {{DEVICE_RUN_COMMANDS}}.
Navigation to the test surface: {{DEVICE_TEST_FLOW}}.
Native rebuild triggers for this stack: {{NATIVE_REBUILD_RULES}}.
Mark this section not used when there is no native app.

## Proof

The [delivery workflow](coding-workflow.md#prove) owns required evidence.
Project-specific acceptance checks and runtime proof: {{PROJECT_PROOF}}.
Include accessibility, error recovery and target platform coverage where applicable.
For documentation-only changes, check links, placeholders and independence.
Report unavailable environments and exactly which behavior remains unobserved.

## Finish

Project cleanup and generated-file caveats: {{LOCAL_CLEANUP}}.
Stop only processes started by your session and release only your device/browser sessions.
Inspect `git diff` for generated noise before committing.
Leave shared services in their previous state unless the task authorized a change.

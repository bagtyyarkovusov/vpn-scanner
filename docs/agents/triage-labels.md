# Triage labels

`triage` assigns exactly one of these labels to each issue.
Native dependencies track blocking separately; see the [issue tracker](issue-tracker.md).

| Label | Meaning |
|---|---|
| `needs-triage` | Founder evaluation needed; default for incoming issues. |
| `needs-info` | Waiting on the reporter for details. |
| `ready-for-agent` | Fully specified; an agent can pick it up cold. |
| `ready-for-human` | Needs founder judgment, design or a sensitive decision. |
| `wontfix` | Will not be done. |

## Create labels

Kickoff runs these against the confirmed repository; `--force` updates existing labels.
Follow [GitHub operations](github-operations.md) for repository selection.

```bash
gh label create needs-triage --color D4C5F9 --description "Founder evaluation needed" --force
gh label create needs-info --color FEF2C0 --description "Waiting for reporter details" --force
gh label create ready-for-agent --color 0E8A16 --description "Specified and ready for an agent" --force
gh label create ready-for-human --color FBCA04 --description "Founder judgment needed" --force
gh label create wontfix --color FFFFFF --description "Will not be done" --force
```

## Change state

Remove the old triage label and add the new one in the same edit:

```bash
gh issue edit <number> --remove-label needs-triage --add-label ready-for-agent
```

A `wontfix` label records disposition; also close the issue with a reason.
Area/type labels may supplement these states but must not replace them.

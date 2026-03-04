---
description: "Show task status and pick one to discuss"
---

Read and follow ~/.claude/skills/formats.md

## Behavior

Show task status and let the user pick one to discuss.

1. Read `doc/backlog.md`.
2. Print status summary: `Status: 1 prioritized | 2 planned | 3 unplanned | 1 blocked`.
3. Group open tasks by state: prioritized `[>]`, planned `[p]`, unplanned `[ ]`, blocked `[!]`.
4. Show plan file path and blocked reason if applicable.
5. User picks a task number to start discussion (proceeds as `hanf-discuss-task`).

---
description: "Retry the first blocked task"
---

Read and follow ~/.claude/skills/workflow.md
Read and follow ~/.claude/skills/code-quality.md
Read and follow ~/.claude/skills/formats.md
Read and follow ~/.claude/skills/llm-context.md

## Behavior

Retry the first blocked task.

1. Find first `[!]` task with `plan:` sub-bullet in `doc/backlog.md`.
2. Read plan file, find first `- [!]` step (or first `- [ ]` if no `[!]`).
3. Implement remaining steps, marking as `- [x]`.
   - Use `python ~/.claude/scripts/hanf_task_complete.py <plan-file>` to mark steps.
4. If a step fails again: mark `- [!]` and stay blocked.
   - Use `python ~/.claude/scripts/hanf_task_block.py <plan-file> "<reason>"`.
5. If all steps complete:
   - Delete task from `doc/backlog.md` using `python ~/.claude/scripts/hanf_task_complete.py --delete doc/backlog.md`.
   - Update `doc/changelog.md` with a dated entry describing what was done.
6. Does **not** commit.

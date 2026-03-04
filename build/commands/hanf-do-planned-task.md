---
description: "Implement the next planned task (does not commit)"
---

Read and follow ~/.claude/skills/workflow.md
Read and follow ~/.claude/skills/code-quality.md
Read and follow ~/.claude/skills/formats.md
Read and follow ~/.claude/skills/llm-context.md

## Behavior

Implement the next planned task. Does **not** commit.

1. Find next planned task: first `[>]` with `plan:`, then first `[p]` with `plan:`, then first `[ ]` with `plan:`.
   - Use `python ~/.claude/scripts/hanf_task_get.py --include-planned doc/backlog.md` to extract the task.
2. Read the plan file.
3. Implement each `- [ ]` step, marking as `- [x]` immediately after completion.
   - Use `python ~/.claude/scripts/hanf_task_complete.py <plan-file>` to mark steps.
4. If a step fails: mark `- [!]` and block the task.
   - Use `python ~/.claude/scripts/hanf_task_block.py <plan-file> "<reason>"`.
5. Run build + test after all steps (see `~/.claude/skills/csharp-build.md`).
6. If all steps complete:
   - Delete task from `doc/backlog.md` using `python ~/.claude/scripts/hanf_task_complete.py --delete doc/backlog.md`.
   - Update `doc/changelog.md` with a dated entry describing what was done.
7. Does **not** commit — user calls `hanf-commit` when ready.

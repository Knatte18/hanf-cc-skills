---
description: "Implement all planned tasks, committing after each"
---

Read and follow ~/.claude/skills/workflow.md
Read and follow ~/.claude/skills/code-quality.md
Read and follow ~/.claude/skills/formats.md
Read and follow ~/.claude/skills/llm-context.md
Read and follow ~/.claude/skills/git.md

## Behavior

Implement all planned tasks. Commits after **each** completed task.

1. Loop through planned tasks using `--include-planned` (those with `plan:` sub-bullet, priority: `[>]` → `[p]` → `[ ]`).
   - Use `python ~/.claude/scripts/hanf_task_get.py --include-planned doc/backlog.md` to extract the next task.
2. For each task:
   1. Read the plan file.
   2. Implement each `- [ ]` step, marking as `- [x]`.
      - Use `python ~/.claude/scripts/hanf_task_complete.py <plan-file>` to mark steps.
   3. If a step fails: mark `- [!]`, block the task, move to the next task.
      - Use `python ~/.claude/scripts/hanf_task_block.py <plan-file> "<reason>"`.
   4. Run build + test (see `~/.claude/skills/csharp-build.md`).
   5. Delete task from `doc/backlog.md` using `python ~/.claude/scripts/hanf_task_complete.py --delete doc/backlog.md`.
   6. Update `doc/changelog.md` with a dated entry describing what was done.
   7. Commit and push (using `hanf-commit` workflow).
3. Stop when no planned tasks remain.

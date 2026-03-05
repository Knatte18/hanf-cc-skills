---
description: "Discuss a backlog task without writing a plan"
argument-hint: "<task name>"
---

Read and follow ~/.claude/skills/workflow.md
Read and follow ~/.claude/skills/code-quality.md
Read and follow ~/.claude/skills/formats.md
Read and follow ~/.claude/skills/llm-context.md

## Behavior

Discuss a backlog task. Does **not** write a plan.

1. Find task from `doc/backlog.md`: by name if provided, otherwise first `[>]`, then first `[ ]`. Skips `[N]` tasks (already claimed by another thread).
   - Use `python ~/.claude/scripts/hanf_task_get.py doc/backlog.md` to extract the task.
2. Claim the task by running `python ~/.claude/scripts/hanf_task_claim.py doc/backlog.md "<task name>"`.
3. If the task has a `plan:` sub-bullet, read and summarize the existing plan, then continue discussion from there.
4. Read relevant codebase sections.
5. Ask clarifying questions about approach, constraints, and design.
6. Discussion continues until the user calls `hanf-finalize-plan`.
7. Do not enter plan mode or write plan files. This command is discussion only.

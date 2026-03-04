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

1. Find task from `doc/backlog.md`: by name if provided, otherwise first `[>]`, then first `[ ]`.
   - Use `python ~/.claude/scripts/hanf_task_get.py doc/backlog.md` to extract the task.
2. If the task has a `plan:` sub-bullet, read and summarize the existing plan, then continue discussion from there.
3. Read relevant codebase sections.
4. Ask clarifying questions about approach, constraints, and design.
5. Discussion continues until the user calls `hanf-finalize-plan`.

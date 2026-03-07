---
name: workflow
description: Skill invocation table, task completion rules. ALWAYS use on startup.
---

# Workflow Skill

Rules for how work is coordinated: branch policy, task completion, and skill invocation.

---

## Skill Invocation Table

Use the appropriate skill based on the current activity:

| Situation | Skill |
|-----------|-------|
| Before editing code | `@taskmill:code-quality` |
| When running shell commands | `@taskmill:cli` |
| For project-specific style rules | `@taskmill:linting` |
| For C# comments, tests, or build | `@taskmill:csharp-*` |
| For all git operations | `@taskmill:git` |
| For file format specs (backlog, plans) | `@taskmill:formats` |
| For response style guidelines | `@taskmill:conversation` |
| For file placement and .llm/ rules | `@taskmill:llm-context` |
| For workflow and completion rules | `@taskmill:workflow` |

---

## Backlog Mutations

Never use Edit or Write on `doc/backlog.md`. All mutations must go through scripts:

| Action | Script |
|--------|--------|
| Add task | `task_add.py` |
| Claim for discussion | `task_claim.py` |
| Set planned + link plan | `task_plan.py` |
| Complete / delete | `task_complete.py` |
| Block with reason | `task_block.py` |

Reading `doc/backlog.md` with the Read tool is allowed.

---

## Task Completion

- Run build + tests after each completed task (see `@taskmill:csharp-build` for details).
- When a task is fully complete, update:
  1. The plan file (all steps marked `[x]`)
  2. `doc/backlog.md` (task entry deleted via `task_complete.py --delete`)
  3. `doc/changelog.md` (dated entry describing what was done)

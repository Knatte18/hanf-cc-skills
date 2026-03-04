# Workflow Skill

Rules for how work is coordinated: branch policy, task completion, and skill invocation.

---

## Skill Invocation Table

Use the appropriate skill based on the current activity:

| Situation | Skill |
|-----------|-------|
| Before editing code | `~/.claude/skills/code-quality.md` |
| When running shell commands | `~/.claude/skills/cli.md` |
| For project-specific style rules | `~/.claude/skills/linting.md` |
| For C# comments, tests, or build | `~/.claude/skills/csharp-*.md` |
| For all git operations | `~/.claude/skills/git.md` |
| For file format specs (backlog, plans) | `~/.claude/skills/formats.md` |
| For response style guidelines | `~/.claude/skills/conversation.md` |
| For file placement and .llm/ rules | `~/.claude/skills/llm-context.md` |
| For workflow and completion rules | `~/.claude/skills/workflow.md` |

---

## Task Completion

- Run build + tests after each completed task (see `skill-build` for details).
- When a task is fully complete, update:
  1. The plan file (all steps marked `[x]`)
  2. `doc/backlog.md` (task entry deleted)
  3. `doc/changelog.md` (dated entry describing what was done)

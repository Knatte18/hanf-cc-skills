---
description: "Print commands to reinstall the taskmill plugin"
---

## Behavior

Print the commands the user needs to run in a terminal to reinstall the plugin. Do NOT run them — they must be run outside Claude Code.

### Output

Print this:

```
Run these in a terminal (not inside Claude Code):

claude plugin uninstall taskmill@taskmill
claude plugin install taskmill@taskmill
```

If `claude` is not on PATH, use `npx @anthropic-ai/claude-code` instead of `claude`.

Then remind the user to restart Claude Code after running them.

### First-time setup

If the marketplace has not been added yet, also print:

```
claude plugin marketplace add c:/Code/taskmill
```

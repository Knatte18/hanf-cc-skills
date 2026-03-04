# Scripts Skill

Python scripts that operate on files with `- [ ]` checkbox format. Same scripts work for `doc/backlog.md` and `.llm/plans/*.md`.

**Purpose:** Reduce token usage. CC does not read the entire file — it gets only the relevant extract via script output.

---

## hanf_task_get.py

Extract the next incomplete task/step with its context lines.

```
Usage: hanf_task_get.py [--include-planned] <file-path>
```

Selection priority (default):
1. First `[>]` (prioritized) item
2. First `[ ]` (unplanned/undone) item

With `--include-planned`:
1. First `[>]` (prioritized) item
2. First `[p]` (planned) item
3. First `[ ]` (unplanned/undone) item

Output: the task line and all indented sub-bullets below it. Exit code 0 if found, 1 if no incomplete items.

---

## hanf_task_add.py

Append a new item to a file.

```
Usage: hanf_task_add.py <file-path> <Title: description>
```

If the input contains a colon, the part before becomes a bold title and the part after becomes an indented description. If no colon, the entire input becomes the bold title with no description. Appends the entry followed by a trailing blank line. Creates the file if it doesn't exist.

---

## hanf_task_complete.py

Mark the first incomplete item as done.

```
Usage: hanf_task_complete.py [--delete] <file-path>
```

Finds first `[ ]`, `[>]`, or `[p]` item and replaces with `[x]`. Prints the completed item. Exit code 0 if found, 1 if no incomplete items.

With `--delete`: instead of marking `[x]`, deletes the matched entry entirely (the task line, all indented sub-bullets below it, and any trailing blank line). Used for backlog tasks where `doc/changelog.md` already records the completion.

---

## hanf_task_block.py

Mark the first incomplete item as blocked.

```
Usage: hanf_task_block.py <file-path> [reason]
```

Finds first `[ ]`, `[>]`, or `[p]` item and replaces with `[!]`. Optionally inserts a `blocked: <reason>` sub-bullet. Exit code 0 if found, 1 if no incomplete items.

---

## Checkbox matching

All scripts that search for or replace checkbox states **must** use line-start-anchored regex to avoid false matches when bracket patterns like `[p]` or `[x]` appear inside task title text.

**Detection pattern:** `r'^\s*- \[(.)\] '` — matches a checkbox only at line start (with optional leading whitespace for indented plan sub-steps). The capture group yields the state character.

**Replacement:** Use `re.sub(r'^(\s*- \[)[>p ](])' , r'\1x\2', line)` (or the appropriate target state) instead of `str.replace()`. This ensures only the leading checkbox is modified, never bracket text in titles.

Scripts affected: `hanf_task_get.py`, `hanf_task_complete.py`, `hanf_task_block.py`. `hanf_task_add.py` only appends and is unaffected.

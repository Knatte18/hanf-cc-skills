---
description: "Generate a work-journal entry from recent git commits"
argument-hint: "<cutoff> [language-prefix] [guidance]"
---

Generate a work-journal entry from recent git commits. Prints to stdout only — does not modify any files.

## Steps

1. Parse arguments (any order):
   - **Cutoff (required):** ISO 8601 timestamp or natural-language date (e.g. `today`, `yesterday`, `2h ago`, `2026-03-01`). No default — the user must specify when to start from.
   - **Language prefix (optional):** any recognizable prefix of a language name. Examples: `nor`, `no`, `norwegian`, `eng`, `en`, `english`, `fr`, `french`. Default: English.
   - **Guidance (optional):** free-text for emphasis, length, or focus. Examples: `"Emphasize the refactoring work"`, `"3 sentences"`, `brief`, `detailed`. Quoted strings are treated as guidance.
2. Run `git log --oneline --since=<cutoff>` to gather commits since the cutoff.
3. Generate plain narrative prose — dense, technical, work-journal style. No headings, no bullet points, no markdown formatting.
4. Print the entry to stdout. Do NOT read or write any files.
5. Do NOT read `doc/changelog.md`.

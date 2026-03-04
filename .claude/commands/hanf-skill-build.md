---
description: "Build skills from doc/ specs into build/"
---

Read and follow BUILD.md

## Behavior

Generate all skill files from `doc/` into `build/`. Follow the rules in BUILD.md exactly.

1. Clean `build/skills/`, `build/commands/`, `build/scripts/` (remove all generated files, keep `.gitkeep`).
2. Read all spec files under `doc/`.
3. Generate into `build/` following BUILD.md rules:
   - Skills → `build/skills/`
   - Commands → `build/commands/`
   - Scripts → `build/scripts/`
   - CLAUDE.md → `build/CLAUDE.md`
4. Print a summary of generated files.

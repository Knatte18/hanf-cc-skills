- [ ] **Add UTC clock time to plan filenames**
  Change plan naming from YYYY-MM-DD-<slug>.md to YYYY-MM-DD-HHMM-<slug>.md so plans sort correctly and newest ones are easy to find

- [ ] **Plan steps should not use slash command syntax**
  Plan steps like 'Run /hanf-skill-build' confuse the LLM executor — it may interpret slash commands as requiring user invocation rather than executing the underlying action itself. Steps should describe concrete actions (e.g. 'Regenerate scripts from updated spec' or 'Run python build_skills.py') instead of referencing slash commands. Update skill-formats.md plan format spec and hanf-finalize-plan command to enforce this


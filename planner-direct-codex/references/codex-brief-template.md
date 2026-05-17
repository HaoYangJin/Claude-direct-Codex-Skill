# Codex Brief Template

Return exactly this structure as plain Markdown.
Do not wrap it in code fences unless the user explicitly asks.
Do not add any explanation before or after it.

```md
Goal:
<single concrete outcome>

Why:
<why this task matters now>

Scope:
- <work item>
- <work item>

Out of Scope:
- <non-goal>

Constraints:
- <technical or product constraint>
- <implementation constraint>

Acceptance Criteria:
- <observable completion condition>
- <observable completion condition>

Deliverables:
- <files or artifacts expected>

Validation:
- <tests/checks/review Codex should perform>

Output Format:
- Summary
- Files changed
- Validation results
- Risks or follow-ups
```

Additional rules:

- Keep headers exactly as written.
- Use English section titles even if the surrounding conversation is in Chinese.
- Keep the brief limited to one bounded slice of work.
- Make `Validation` realistic for the type of task.
- Use `Out of Scope` aggressively to prevent prompt sprawl.

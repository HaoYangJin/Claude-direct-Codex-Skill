---
name: planner-direct-codex
description: Creates one bounded Codex brief. Use for "plan a Codex task", "give me a Codex brief", "direct Codex", "/skill planner-direct-codex", "task brief", "copyable prompt", "任务单", or "派活给 Codex".
---

# Planner Direct Codex

Turn the user's latest request into one task brief that can be pasted directly into Codex.
Optimize for execution clarity, not discussion.

## Parse The Request

Treat the text after `/skill` as the user's goal and context.
If the user gives a broad objective, choose the single highest-priority slice that unblocks the rest.
If the user provides explicit constraints, preserve them.
If constraints are missing, add only the smallest safe defaults.

## Produce One Bounded Brief

Always produce one brief with these section headers exactly:

- `Goal`
- `Why`
- `Scope`
- `Out of Scope`
- `Constraints`
- `Acceptance Criteria`
- `Deliverables`
- `Validation`
- `Output Format`

Prefer work items like:

- implement one feature slice
- fix one reproducible bug
- review one patch or PR
- create one workflow, design, or architecture artifact

Avoid work items like:

- rewrite the whole app
- improve everything
- solve multiple unrelated problems in one brief

## Output Discipline

Use the exact format in `references/codex-brief-template.md`.
Unless the user explicitly asks for explanation, output only the Codex brief with no preface and no closing sentence.
Keep the section headers in English exactly as defined in the template so the brief stays stable across rounds.
Keep the `Output Format` bullets exactly as `Summary`, `Files changed`, `Validation results`, and `Risks or follow-ups` so the paired receiver can answer in a stable shape.
Keep the contents concise, specific, and directly actionable.

## Reference Use

Read `references/codex-brief-template.md` for the exact direct-copy output contract.
Read `references/slicing-rules.md` when choosing the bounded slice or contributor-maintained slicing policy matters.
Read `references/example-invocations.md` only when you need examples of how to slice or phrase a request.

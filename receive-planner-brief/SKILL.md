---
name: receive-planner-brief
description: Consume and execute a planner-direct-codex brief pasted into Codex. Use when input starts with Goal: or contains the standard planner headers Goal / Why / Scope / Out of Scope / Constraints / Acceptance Criteria / Deliverables / Validation / Output Format, and return Summary / Files changed / Validation results / Risks or follow-ups.
---

# Receive Planner Brief

Use this skill when Codex receives a task brief emitted by `planner-direct-codex`.
Treat the pasted brief as the source of truth for the current round.

## Parse The Brief

Identify these planner headers exactly, in this order:

- `Goal`
- `Why`
- `Scope`
- `Out of Scope`
- `Constraints`
- `Acceptance Criteria`
- `Deliverables`
- `Validation`
- `Output Format`

If a section is missing but the task is still executable, proceed with the smallest safe assumption and report it under `Risks or follow-ups`.
If the missing section blocks safe execution, ask one concise question before editing.

## Execute The Brief

Follow this discipline:

- Inspect the repository before choosing an implementation path.
- Keep all work inside `Scope`.
- Treat every `Out of Scope` item as a hard boundary.
- Apply `Constraints` before tool, architecture, or validation choices.
- Use `Acceptance Criteria` as the completion checklist.
- Produce only the requested `Deliverables`.
- Run the requested `Validation` when available and practical.
- Do not expand the task because nearby code suggests extra cleanup.

Ask back only when:

- the target repository, file, or system cannot be identified
- two brief requirements directly conflict
- proceeding could damage user data, credentials, production state, or unrelated work
- validation needs unavailable permissions and there is no useful local substitute

Otherwise, inspect, implement, validate, and report.

## Response Contract

Always reply with these top-level headers exactly, in this order:

- `Summary`
- `Files changed`
- `Validation results`
- `Risks or follow-ups`

Keep the headers in English even when the conversation uses another language.
Do not add new top-level sections.
Under `Files changed`, list changed paths or write `None`.
Under `Validation results`, list checks run and their results; if validation was not run, state why.
Under `Risks or follow-ups`, list remaining uncertainty, assumptions, or next steps.

## Pairing With Planner Direct Codex

`planner-direct-codex` creates one bounded brief with the same nine headers and pins the expected reply format to `Summary`, `Files changed`, `Validation results`, and `Risks or follow-ups`.
This receiver consumes that contract on the Codex side so the planner-to-executor round trip stays stable without requiring the user to re-explain the protocol.

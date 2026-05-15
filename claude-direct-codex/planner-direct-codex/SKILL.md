---
name: planner-direct-codex
description: Turn a user's product or engineering goal into one bounded, Codex-ready execution brief that a planning model can output for direct copy/paste. Use when the user wants one model to plan or direct Codex, asks for a `/skill` workflow, mentions copyable prompts, task decomposition, acceptance criteria, or wants the planner to choose the next coding step for another agent.
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

Always produce:

- one concrete `Goal`
- one short `Why`
- `Scope` limited to the current work slice
- explicit `Out of Scope` boundaries
- only the constraints that materially affect implementation
- observable `Acceptance Criteria`
- concrete `Deliverables`
- `Validation` that Codex should perform
- a fixed `Output Format` section

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
Keep the contents concise, specific, and directly actionable.

## Slicing Rules

- prefer phase one over a full roadmap
- preserve existing architecture unless the user asks for structural change
- if repository details are unknown, tell Codex to inspect before locking implementation details
- if ambiguity remains, make the smallest reasonable assumption and encode it in `Constraints`
- if the user asks for several things, choose the current top-priority slice and defer the rest

## Reference Use

Read `references/codex-brief-template.md` for the exact direct-copy output contract.
Read `references/example-invocations.md` only when you need examples of how to slice or phrase a request.

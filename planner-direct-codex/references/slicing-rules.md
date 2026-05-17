# Slicing Rules

Use these rules when turning a broad planner request into one Codex-ready brief.
They are separated from `SKILL.md` so contributors can refine slicing behavior without changing the core routing contract.

## Core Rules

- Prefer phase one over a full roadmap.
- Preserve existing architecture unless the user asks for structural change.
- If repository details are unknown, tell Codex to inspect before locking implementation details.
- If ambiguity remains, make the smallest reasonable assumption and encode it in `Constraints`.
- If the user asks for several things, choose the current top-priority slice and defer the rest.

## Feature Work

- Choose the first slice that creates a usable path or proves the integration point.
- Keep UI, data, API, and documentation work together only when they are required for the same observable outcome.
- Defer polish, secondary states, migrations, and broad refactors unless they are necessary for the first slice to work.

## Bug Fix Work

- Ask Codex to reproduce or localize the bug before editing when the root cause is not already explicit.
- Keep validation tied to the reported failure mode.
- Avoid unrelated cleanup in the same brief, even when the surrounding code is messy.

## Review Work

- Make review-only requests explicitly review-only.
- Ask Codex to prioritize bugs, regressions, security risks, data loss, user-visible behavior changes, and missing tests.
- Do not mix implementation with review unless the user asks Codex to address findings in the same task.

## Research And Analysis Work

- Prefer reproducibility, evaluation, and artifact-quality slices over open-ended research direction changes.
- Ask Codex to inspect existing scripts, notebooks, configs, datasets, and result files before changing methodology.
- Defer claims about model quality unless the requested validation actually supports them.

# planner-direct-codex v0.1.0

Initial public release of `planner-direct-codex`, a Claude Skill that turns broad product, engineering, research, or review requests into one bounded Codex-ready task brief.

## Highlights

- Adds the `planner-direct-codex` skill with a stable nine-section brief contract:
  `Goal`, `Why`, `Scope`, `Out of Scope`, `Constraints`, `Acceptance Criteria`, `Deliverables`, `Validation`, and `Output Format`.
- Includes reference templates and slicing rules so planner-side output stays concise, executable, and easy to paste into Codex.
- Documents the paired Codex workflow with `receive-planner-brief`, including the fixed response shape:
  `Summary`, `Files changed`, `Validation results`, and `Risks or follow-ups`.
- Adds bilingual README and usage documentation for Claude Code, Claude.ai ZIP installation, and quick-start invocation.
- Includes a workflow tutorial image under `assets/claude-direct-codex-workflow.png`.

## Installation

### Claude Code

Copy the skill into your personal Claude skills directory:

```powershell
$skillDir = Join-Path $HOME ".claude\skills\planner-direct-codex"
New-Item -ItemType Directory -Force $skillDir | Out-Null
Copy-Item -Recurse -Force .\SKILL.md, .\references $skillDir
```

For project-local use, copy the repository contents to:

```text
.claude\skills\planner-direct-codex\
```

### Claude.ai

Upload the release ZIP whose top-level folder is `planner-direct-codex/` and contains:

- `SKILL.md`
- `references/`
- documentation files
- tutorial image assets

## Quick Start

```text
/skill planner-direct-codex Fix the duplicate order submission bug on the checkout page and give me a Codex brief.
```

The skill returns a copy-pasteable Codex brief with scope, acceptance criteria, validation instructions, and the expected Codex response format.

## Release Asset

Use `planner-direct-codex-v0.1.0.zip` for Claude.ai upload or manual distribution.

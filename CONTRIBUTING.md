# Contributing

## 中文

感谢你改进 `planner-direct-codex`。这个仓库的核心目标是保持 planner 到 Codex 的 brief contract 稳定，同时让切片规则和示例可以持续演进。

### 工作流

1. Fork 这个仓库。
2. 从 `main` 创建一个描述性分支，例如 `docs/add-ml-example` 或 `rules/review-slicing`。
3. 保持改动聚焦：一个 PR 只解决一个规则、一个示例组或一个文档问题。
4. 打开 PR，并说明你修改的是 routing、brief contract、slicing rules、examples，还是文档。

### 修改 slicing rules

`slicing-rules.md` 是最适合贡献的地方。新增规则时请说明它适用的请求类型，例如 feature、bug fix、review、research，避免把某个项目里的特殊约束写成通用规则。

### 增加 example invocations

新增样例时保留两个部分：`User input` 和 `Preferred slicing`。示例可以来自中文或英文真实工作流，但解释应保持简洁。

### 样式规则

- 不要改动 brief 的九个顶层标题：`Goal`, `Why`, `Scope`, `Out of Scope`, `Constraints`, `Acceptance Criteria`, `Deliverables`, `Validation`, `Output Format`。
- 不要改动 `Output Format` 的四个条目：`Summary`, `Files changed`, `Validation results`, `Risks or follow-ups`。
- 不要把多个无关任务放进一个示例 brief。
- 保持 `SKILL.md` 简短，把可扩展的细节放到 `references/`。

## English

Thank you for improving `planner-direct-codex`. The project should keep the planner-to-Codex brief contract stable while allowing slicing rules and examples to evolve.

### Workflow

1. Fork the repository.
2. Create a descriptive branch from `main`, such as `docs/add-ml-example` or `rules/review-slicing`.
3. Keep each PR focused on one rule, one example group, or one documentation issue.
4. Open a PR and explain whether the change affects routing, the brief contract, slicing rules, examples, or documentation.

### Proposing slicing rules

`references/slicing-rules.md` is the best place for new behavior. When adding a rule, name the request type it applies to, such as feature work, bug fixes, review, or research. Avoid turning one project's local constraint into a global rule.

### Adding example invocations

Keep each new example in two parts: `User input` and `Preferred slicing`. Inputs may be Chinese or English, but the slicing explanation should stay concise.

### Style rules

- Do not change the nine top-level brief headers: `Goal`, `Why`, `Scope`, `Out of Scope`, `Constraints`, `Acceptance Criteria`, `Deliverables`, `Validation`, `Output Format`.
- Do not change the four `Output Format` items: `Summary`, `Files changed`, `Validation results`, `Risks or follow-ups`.
- Do not combine unrelated tasks into one example brief.
- Keep `SKILL.md` short and move expandable detail into `references/`.

## Main-only Maintenance

This repository is maintained directly on `main`; do not create `codex-*` feature branches for routine updates. Keep maintenance logs, local plans, transcripts, cache directories, packaging snapshots, and other generated artifacts out of version control.

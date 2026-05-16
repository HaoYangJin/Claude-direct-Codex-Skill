# Claude(Planner) Direct Codex Skill

![Version](https://img.shields.io/badge/version-0.1.0-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![Skill](https://img.shields.io/badge/skill-claude--direct--codex-purple)

## 教程图 / Tutorial Image

![Claude-direct-Codex workflow tutorial](assets/claude-direct-codex-workflow.png)

## 中文

`planner-direct-codex` 是一个给规划模型使用的 Claude Skill。它把用户的产品、工程、研究或审查需求压缩成一个边界清晰、可以直接粘贴给 Codex 执行的任务单。

它适合这些场景：

- 你想先让 Claude 做规划，再让 Codex 改代码。
- 你需要一个稳定的 Codex brief，而不是长篇讨论。
- 你希望任务包含范围、验收标准、验证方式和固定回报格式。
- 你想把大需求切成第一阶段可执行的最小任务。

### 如何与Codex协作

`planner-direct-codex` 负责在 Claude 侧产出任务单；Codex 侧可以安装配套的 `receive-planner-brief` skill 来读取同一组固定标题，并按 `Summary / Files changed / Validation results / Risks or follow-ups` 的格式回报执行结果。两个 skill 不需要共享代码，但它们共享 brief contract。

### 安装到 Claude Code

将这个目录作为个人 skill 放到 Claude Code 的 skills 目录中：

```powershell
$skillDir = Join-Path $HOME ".claude\skills\planner-direct-codex"
New-Item -ItemType Directory -Force $skillDir | Out-Null
Copy-Item -Recurse -Force .\SKILL.md, .\references $skillDir
```

也可以作为项目 skill 放到当前项目的 `.claude\skills\planner-direct-codex\`。

### 安装到 Claude.ai

创建一个 ZIP，里面的顶层目录应为 `planner-direct-codex/`，并包含 `SKILL.md` 和 `references/`。在 Claude.ai 的 Skills 或 Capabilities 设置中上传并启用这个 ZIP。

### 快速开始

输入：

```text
/skill planner-direct-codex 为现有 Next.js 项目加登录注册功能，先给 Codex 最优先的一步。
```

输出片段：

```md
Goal:
Add the first bounded authentication slice to the existing Next.js project.

Why:
Login and registration unblock user-specific workflows, but the repo needs inspection before choosing the correct integration point.

Scope:
- Inspect the existing routing, auth, and data-access structure.
- Implement the smallest first authentication entry point that matches the current architecture.
```

把完整 brief 粘贴给 Codex，Codex 执行后按固定格式回报。

## English

`planner-direct-codex` is a Claude Skill for planner-side workflows. It turns a product, engineering, research, or review request into one bounded Codex-ready task brief.

Use it when you want Claude to plan the next coding step and Codex to execute it with clear scope, acceptance criteria, validation, and a stable response format.

### How it pairs with Codex

`planner-direct-codex` emits the task brief on the Claude side. On the Codex side, the paired `receive-planner-brief` skill can consume the same fixed headers and respond with `Summary / Files changed / Validation results / Risks or follow-ups`. The two skills are separate, but they share the brief contract.

### Install in Claude Code

Copy this repository into a personal skill directory:

```powershell
$skillDir = Join-Path $HOME ".claude\skills\planner-direct-codex"
New-Item -ItemType Directory -Force $skillDir | Out-Null
Copy-Item -Recurse -Force .\SKILL.md, .\references $skillDir
```

For project-local use, copy it to `.claude\skills\planner-direct-codex\` inside the project.

### Install in Claude.ai

Create a ZIP whose top-level directory is `planner-direct-codex/` and contains `SKILL.md` plus `references/`. Upload and enable it from the Claude.ai Skills or Capabilities settings.

### Quick Start

Prompt:

```text
/skill planner-direct-codex Fix the duplicate order submission bug on the checkout page and give me a Codex brief.
```

Brief snippet:

```md
Goal:
Fix the duplicate order submission path on the checkout page.

Why:
Duplicate submissions can create incorrect orders or payments and should be addressed before broader checkout cleanup.
```

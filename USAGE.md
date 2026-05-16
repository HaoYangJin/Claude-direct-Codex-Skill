# Usage

## 中文

### 安装

#### Claude Code

个人安装：

```powershell
$skillDir = Join-Path $HOME ".claude\skills\planner-direct-codex"
New-Item -ItemType Directory -Force $skillDir | Out-Null
Copy-Item -Recurse -Force .\SKILL.md, .\references $skillDir
```

项目安装：

```powershell
$skillDir = ".claude\skills\planner-direct-codex"
New-Item -ItemType Directory -Force $skillDir | Out-Null
Copy-Item -Recurse -Force .\SKILL.md, .\references $skillDir
```

#### Claude.ai

将 `planner-direct-codex/` 目录压缩成 ZIP。ZIP 内的顶层目录应包含 `SKILL.md` 和 `references/`。然后在 Claude.ai 的 Skills 或 Capabilities 设置中上传并启用。

### 第一次运行

在 Claude 中直接调用：

```text
/skill planner-direct-codex 帮我把这个前端项目的搜索功能做出来，先给 Codex 一个最优先任务单。
```

这个 skill 应输出一个只有 brief 的 Markdown 文档，标题固定为：

- `Goal`
- `Why`
- `Scope`
- `Out of Scope`
- `Constraints`
- `Acceptance Criteria`
- `Deliverables`
- `Validation`
- `Output Format`

### 如何阅读生成的 brief

- `Goal` 是 Codex 要完成的单一结果。
- `Why` 说明这个任务为什么现在值得做。
- `Scope` 是本轮允许 Codex 做的工作。
- `Out of Scope` 是明确不能扩展的边界。
- `Constraints` 是实现和流程限制。
- `Acceptance Criteria` 是可观察的完成条件。
- `Deliverables` 是 Codex 应交付的文件或产物。
- `Validation` 是 Codex 应执行的检查。
- `Output Format` 是 Codex 最终回复的固定结构。

### 粘贴到 Codex

把完整 brief 原样粘贴给 Codex。不要删掉英文标题，也不要改写 `Output Format` 中的四个条目。Codex 端如果安装了 `receive-planner-brief`，会识别这些标题，执行任务，并按以下结构回报：

```md
Summary:
<what changed>

Files changed:
- <paths>

Validation results:
- <checks>

Risks or follow-ups:
- <remaining notes>
```

### 自定义

#### editing the slicing rules

编辑 `references/slicing-rules.md` 来调整大任务如何被切成第一阶段任务。保持 `SKILL.md` 中的九个标题不变，避免破坏 Codex 侧接收器的兼容性。

#### adding your own example invocations

编辑 `references/example-invocations.md` 来增加你所在团队的常见任务样例。推荐每个样例都包含 user input 和 preferred slicing 两部分。

## English

### Install

#### Claude Code

Personal install:

```powershell
$skillDir = Join-Path $HOME ".claude\skills\planner-direct-codex"
New-Item -ItemType Directory -Force $skillDir | Out-Null
Copy-Item -Recurse -Force .\SKILL.md, .\references $skillDir
```

Project install:

```powershell
$skillDir = ".claude\skills\planner-direct-codex"
New-Item -ItemType Directory -Force $skillDir | Out-Null
Copy-Item -Recurse -Force .\SKILL.md, .\references $skillDir
```

#### Claude.ai

Zip the `planner-direct-codex/` directory so the ZIP contains that top-level folder with `SKILL.md` and `references/`. Upload and enable the ZIP from the Claude.ai Skills or Capabilities settings.

### First Run

Invoke the skill directly:

```text
/skill planner-direct-codex Add account settings to the existing app and give me the first Codex task brief.
```

The skill should return only the Codex brief, using the fixed English headers listed in `references/codex-brief-template.md`.

### Reading The Brief

`Goal` is the single result Codex should produce. `Scope` and `Out of Scope` define the work boundary. `Acceptance Criteria` and `Validation` define how Codex should prove the task is complete. `Output Format` tells Codex how to report back.

### Paste Into Codex

Paste the full brief into Codex without changing the English headers. If Codex has the paired `receive-planner-brief` skill installed, it can consume the brief directly and return the stable response shape.

### Customization

#### editing the slicing rules

Edit `references/slicing-rules.md` to change how broad requests become one bounded task. Keep the nine canonical headers stable.

#### adding your own example invocations

Edit `references/example-invocations.md` to add team-specific prompts and slicing choices. Keep each example short enough to scan quickly.
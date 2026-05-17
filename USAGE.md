# Usage

## 中文

### 仓库结构

```text
planner-direct-codex/
  SKILL.md
  references/
receive-planner-brief/
  SKILL.md
```

`planner-direct-codex` 产出固定格式 brief；`receive-planner-brief` 消费同一份 brief contract 并执行。

### planner-direct-codex

在 Claude 中调用：

```text
/skill planner-direct-codex 帮我把这个前端项目的搜索功能做出来，先给 Codex 一个最优先任务单。
```

这个 skill 输出一个只有 brief 的 Markdown 文档，标题固定为：

- `Goal`
- `Why`
- `Scope`
- `Out of Scope`
- `Constraints`
- `Acceptance Criteria`
- `Deliverables`
- `Validation`
- `Output Format`

### receive-planner-brief

把完整 brief 原样粘贴给 Codex。不要删掉英文标题，也不要改写 `Output Format` 中的四个条目。Codex 端安装 `receive-planner-brief` 后，会按以下结构回报：

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

### 安装

Claude Code:

```powershell
$skillDir = Join-Path $HOME ".claude\skills\planner-direct-codex"
New-Item -ItemType Directory -Force $skillDir | Out-Null
Copy-Item -Recurse -Force .\planner-direct-codex\SKILL.md, .\planner-direct-codex\references $skillDir
```

Codex:

```powershell
$skillDir = Join-Path $HOME ".codex\skills\receive-planner-brief"
New-Item -ItemType Directory -Force $skillDir | Out-Null
Copy-Item -Force .\receive-planner-brief\SKILL.md $skillDir
```

## English

### Repository Layout

```text
planner-direct-codex/
  SKILL.md
  references/
receive-planner-brief/
  SKILL.md
```

`planner-direct-codex` emits the fixed brief. `receive-planner-brief` consumes the same brief contract and executes it.

### planner-direct-codex

Invoke in Claude:

```text
/skill planner-direct-codex Add account settings to the existing app and give me the first Codex task brief.
```

The skill returns only a Markdown brief with these fixed headers:

- `Goal`
- `Why`
- `Scope`
- `Out of Scope`
- `Constraints`
- `Acceptance Criteria`
- `Deliverables`
- `Validation`
- `Output Format`

### receive-planner-brief

Paste the full brief into Codex without changing the English headers. With `receive-planner-brief` installed, Codex returns:

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

### Install

Claude Code:

```powershell
$skillDir = Join-Path $HOME ".claude\skills\planner-direct-codex"
New-Item -ItemType Directory -Force $skillDir | Out-Null
Copy-Item -Recurse -Force .\planner-direct-codex\SKILL.md, .\planner-direct-codex\references $skillDir
```

Codex:

```powershell
$skillDir = Join-Path $HOME ".codex\skills\receive-planner-brief"
New-Item -ItemType Directory -Force $skillDir | Out-Null
Copy-Item -Force .\receive-planner-brief\SKILL.md $skillDir
```

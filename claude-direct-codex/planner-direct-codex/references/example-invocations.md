# Example Invocations

## Broad Feature Request

User input:

```text
/skill planner-direct-codex 为现有的 Next.js 项目加登录注册功能，先给 Codex 最优先的一步。
```

Preferred slicing:

- ask Codex to inspect the existing auth and routing structure first
- limit scope to scaffolding the auth entry point or wiring the first backend path
- explicitly defer full UI polish and downstream account flows

## Bug Fix Request

User input:

```text
/skill planner-direct-codex 修复支付页重复提交订单的问题，给我一个能直接贴给 Codex 的任务单。
```

Preferred slicing:

- focus on reproducing and fixing the duplicate-submit root cause
- ask for targeted regression validation
- defer unrelated checkout cleanup

## Review Request

User input:

```text
/skill planner-direct-codex 帮我让 Codex review 这个改动，重点找风险和漏测。
```

Preferred slicing:

- make the goal review-only
- ask Codex to prioritize bugs, regressions, and missing tests
- avoid mixing review with implementation in the same brief

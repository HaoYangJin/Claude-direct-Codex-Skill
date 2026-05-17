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

## ML Research Request

User input:

```text
/skill planner-direct-codex 帮我把多模态论文实验仓库整理一下，先让 Codex 做最能减少实验误差的一步。
```

Preferred slicing:

- ask Codex to inspect the current experiment scripts, config files, and result artifacts before choosing edits
- limit scope to one reproducibility slice such as config normalization, seed handling, metric logging, or a results-summary table
- require validation that is realistic for the repository, such as a dry run, unit check, schema check, or inspection of generated experiment metadata
- defer new model ideas, full retraining, benchmark claims, and paper-writing changes

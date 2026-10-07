---
title: "Current Effective Artifact Resolution"
version: "v1.0"
status: "ACTIVE"
scope: "CROSS_STAGE_REGRESSION"
---

# Current Effective Artifact Resolution

本合同只解决跨 Stage Regression 后下游应读取哪一个 Artifact，不新增 Stage、Agent、Repair System 或 Canon 层。

## 1. 声明位置

若当前单集没有 Regression，标准 Stage Artifact 是当前有效文件，不需要额外声明。

若任一 Stage 发生跨 Stage Regression，在 `01_story/current_effective_artifacts.md` 中维护该 Stage 的唯一当前声明。该文件是可更新的运行索引，不是 Story Canon 或历史证据；原始 FAIL、PASS_WITH_FIX 与全部 Regression 文件保持不变。

每条声明必须包含：

```text
STAGE =
CURRENT_EFFECTIVE_ARTIFACT =
CURRENT_EFFECTIVE_STATUS = PASS
SUPERSEDES =
```

`CURRENT_EFFECTIVE_ARTIFACT` 使用相对 `01_story/` 的明确文件路径。`SUPERSEDES` 指向被此次 PASS 取代的标准 Artifact 或上一 Regression；不得写“latest”“highest”或模糊描述。

## 2. 解析规则

1. 无 Regression：读取该 Stage 的标准 Artifact。
2. 有 Regression：只读取运行索引中该 Stage 唯一一条 `CURRENT_EFFECTIVE_STATUS = PASS` 的明确路径。
3. 声明路径不存在、指向非 PASS Artifact 或 Stage 不一致：`STATUS = BLOCKED`，不得继续下游。
4. 同一 Stage 有两个或以上当前 PASS 声明：

```text
STATUS = BLOCKED
BLOCK_REASON = MULTIPLE_CURRENT_EFFECTIVE_ARTIFACTS
```

5. 禁止按最高 regression 后缀、文件修改时间、创建时间、目录顺序或文件名排序选择当前文件。

## 3. 回退与下游失效

Stage 4 返回 Stage 2 或 Stage 3 时，先解析当前 Story Engine 与 Story Master，再重跑所有受影响下游：

`Story Quality → Story Consistency Check → Adaptation Handoff → Delivery`

旧的 Story Quality、Story Consistency Check、Adaptation Handoff 与 Delivery 只能作为历史证据，不再表示当前生产状态。`AUTO_REPAIR_ATTEMPTS = 3` 与所有历史 Artifact 保留规则不变。

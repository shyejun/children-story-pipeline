---
title: "Optional Project Constraints｜可选项目设定约束"
version: "v1.0"
status: "ACTIVE"
scope: "OPTIONAL_PROJECT_CANON"
---

# Optional Project Constraints｜可选项目设定约束

本 Skill 可以独立创作，也可以接入已有 IP、角色圣经、世界观或系列设定。

## 无项目设定时

`PROJECT_CONSTRAINT_MODE = STANDALONE`。用户给出的角色、世界、事实与禁止项就是当前任务的唯一约束；Skill 可在单集内部补足必要临时设定，但不得把临时设定自动声明为长期 Canon。

## 有项目设定时

`PROJECT_CONSTRAINT_MODE = CANON_AWARE`。读取用户提供或工作区中明确标记为权威的：

- Core / Series Bible；
- Character Cards；
- World / Location Rules；
- 已冻结的角色关系、能力与禁用项；
- 当前有效 Source / Fact Pack。

冲突优先级：

```text
User explicit instruction
→ Project Source of Truth
→ Frozen Core / Series Bible
→ Character / World Cards
→ Current Story Artifacts
→ This Skill
```

若上游资料互相冲突，或必须修改长期设定才能让单集成立：`STATUS = BLOCKED`，请求人工判断。

Stage 4 的 Story Consistency Check 在 CANON_AWARE 模式下额外检查设定兼容性；在 STANDALONE 模式下只检查故事内部连续性、用户约束与事实真实性。

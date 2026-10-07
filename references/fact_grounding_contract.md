---
title: "Fact Grounding Contract｜事实真实性合同"
version: "v1.0"
status: "ACTIVE"
scope: "GENERIC_CHILDREN_STORY_FACTS"
---

# Fact Grounding Contract｜事实真实性合同

当儿童故事涉及科学、自然、健康、历史、文化、社会规则等可核验内容时，必须先区分“角色体验”与“客观事实”。本合同不要求纯幻想故事查资料，也不把故事写成百科。

## 1. Claim 分层

```text
CHARACTER_PERCEPTION
STORY_OBSERVATION
GENERAL_FACT
VERIFIABLE_DOMAIN_CLAIM
```

- `CHARACTER_PERCEPTION`：角色当下的感觉、偏好、猜测，只需故事中真实发生。
- `STORY_OBSERVATION`：故事现场直接可见 / 可听 / 可比较的现象。
- `GENERAL_FACT`：日常客观事实；若存在不确定性，优先核查或缩小表述。
- `VERIFIABLE_DOMAIN_CLAIM`：科学、健康、历史、文化、自然机制、社会规则等，需要用户材料、项目 Source 或可靠权威来源。

## 2. Stage 0 字段

只有题材真正涉及可核验知识时记录：

```text
CORE_FACT_CLAIM =
FACT_TYPE =
FACT_SOURCE =
CHILD_CORE_DISCOVERY =
DO_NOT_OVERSTATE =
```

没有可靠来源时，不得把猜测升级为客观结论。可选择：缩小 Claim；改为角色感受；改成“观察到什么”；或 `HUMAN_DECISION_REQUIRED = YES`。

## 3. 故事化原则

事实负责边界，剧情负责体验。优先：

```text
真实情境 → 儿童问题 → 角色行动 → 可见反馈 → 小发现
```

避免：

```text
角色停下来 → 连续讲知识 → 总结正确答案
```

## 4. Gate

```text
CLAIM_GROUNDING = PASS | FAIL | REVIEW | N/A
```

核心事实、解决依据或儿童会带走的客观结论若缺乏可靠支撑，必须 `FAIL` 或阻塞；不影响主线的边缘性表述可 `REVIEW`。

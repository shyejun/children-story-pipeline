---
title: "Final Story Integrity Audit"
version: "v1.0"
status: "ACTIVE"
scope: "STAGE_2_CAUSAL_CHECK_AND_STAGE_3_FINAL_STORY_GATE"
---

# Final Story Integrity Audit

## Purpose

本 Reference 解决“故事结构完整、自评全 PASS，但最终正文仍存在事实矛盾、变量偷换、无依据 Claim 或儿童模仿风险”的问题。它不新增 Stage、Agent、Hook、Engine 或评分体系。

核心原则：

> **写得完整，不等于事实一致；因果写得顺，不等于因果是真的；模型说自己 PASS，不等于最终正文 PASS。**

## 1. Evidence Boundary

最终 Integrity Audit 以**最终连续故事正文**为第一事实证据。允许读取冻结 Story Brief Contract、当前有效 Stage 2 Story Spine / Causal Chain、必要项目约束（若有）与事实 Source 来核对边界。

以下内容不能用来“补救”正文：

- Event Draft；
- Rewrite working file；
- 模型先前的 Story Quality 自评；
- Beat Trace 自评；
- Story Lock / 场景表中正文没有发生的事件；
- “作者本意”“下游可以这样理解”。

正文与附录冲突时，不得靠附录判 PASS；应记录正文矛盾并返回修复。

## 2. Object State Continuity

对关键物体建立轻量状态链：

```text
IDENTITY → QUANTITY → LOCATION → COMPOSITION → VISIBLE_STATE
→ OWNER/HOLDER → USED/UNUSED → CHANGE_EVENT → NEW_STATE
```

检查：

- 新数量从哪里来？
- 新分组由什么动作产生？
- 新成分何时加入？
- 新颜色 / 外观是观察事实还是角色推测？
- 物体何时移动、被谁拿走、何时用过？
- 如果前文说“全部一样”，后文为何出现差异？

找不到 `CHANGE_EVENT`：

```text
OBJECT_STATE_CONTINUITY = FAIL
```

## 3. Causal Variable Integrity

当故事使用比较、实验、多 / 少、加 / 不加、快 / 慢、前 / 后、同样条件等机制时执行。

```text
WHAT_CHANGED =
WHAT_STAYED_THE_SAME =
CLAIMED_EFFECT =
VARIABLE_MATCH = YES | NO
```

典型错误：

- 液体总量更多 → 偷换成浓度更高；
- 份量更大 → 偷换成每一口更甜；
- 颜色不同 → 无依据推成营养更好；
- 同一配方 → 无事件依据突然出现两种成分状态。

如果故事核心发现依赖错误变量：

```text
CAUSAL_VARIABLE_INTEGRITY = FAIL
```

不适用时可 `N/A`，必须说明理由。

## 4. Claim Grounding

把核心 Claim 分为：

```text
CHARACTER_PERCEPTION
STORY_OBSERVATION
GENERAL_FACT
VERIFIABLE_DOMAIN_CLAIM
```

判断规则：

- `CHARACTER_PERCEPTION`：只需正文真实发生该体验，不外推。
- `STORY_OBSERVATION`：必须能从正文状态 / 动作看到。
- `GENERAL_FACT`：需要可靠事实依据；不确定时缩回角色体验或请求来源。
- `VERIFIABLE_DOMAIN_CLAIM`：必须有项目 Source、用户材料或已批准权威来源；不得模型自创。

状态：

```text
CLAIM_GROUNDING = PASS | FAIL | REVIEW
```

若 Claim 是核心发现、解决依据或儿童会带走的可核验事实结论，缺依据必须 FAIL / BLOCK，不得只标 REVIEW 后继续。

## 5. Child Imitation Safety

重点扫描儿童化角色是否直接操作：

- 火 / 明火；
- 烤炉、热锅、热烤盘、热水；
- 刀具、尖锐工具；
- 电器、机械；
- 高处、攀爬；
- 可吞咽小物或其他高模仿风险行为。

记录：

```text
HAZARD_PRESENT = YES | NO
CHILD_CHARACTER_DIRECTLY_OPERATES = YES | NO
CANON_SAFE_MECHANISM_EXISTS = YES | NO | N/A
IMITATION_RISK = LOW | MATERIAL
```

若高风险操作由儿童化角色直接完成，且无既有 Canon 安全机制：

```text
CHILD_IMITATION_SAFETY = FAIL
```

不得为了通过临时发明“绝对安全”的魔法、设备或永久世界规则。

## 6. Education Direction

教育题材检查两端：

```text
NO_SHAMING
DIRECTION_NOT_ERASED
```

- `NO_SHAMING`：不得通过羞辱儿童、群体、身体、能力、家庭或生活方式制造教育效果。
- `DIRECTION_NOT_ERASED`：若上游已有可靠的安全 / 健康 / 科学 / 社会规则方向，不得为了“温和”把它改写成“所有选择完全等价”。

状态：

```text
EDUCATION_DIRECTION = PASS | REVIEW | N/A
```

若故事明确传播错误或危险的客观结论，则不是 REVIEW，而是 `CLAIM_GROUNDING / HARD_GATE` FAIL。

## 7. Hard Gate Aggregate

```text
OBJECT_STATE_CONTINUITY =
CAUSAL_VARIABLE_INTEGRITY =
CLAIM_GROUNDING =
CHILD_IMITATION_SAFETY =
EDUCATION_DIRECTION =
HARD_GATE_STATUS = PASS | FAIL
```

Beat Trace、Story Quality 十一项、Canon 或 Information Sufficiency 均不能覆盖硬 FAIL。

## 8. Independent Final Review Mode

Hard Gate PASS 后再复核文学质量。不是新增 Agent；是证据读取范围受限的第二遍判断。

只使用：

```text
Frozen Story Brief Contract
Current Story Spine / Causal Chain
Final Continuous Story Text
Necessary Project Constraints (if any)
Necessary Fact Sources
```

不得用前一遍自评证明后一遍通过。输出：

```text
STORY_QUALITY_JUDGMENT = STRONG | ADEQUATE | NEEDS_REWRITE | HUMAN_REVIEW
FINAL_TEXT_CONTRADICTIONS =
UNSUPPORTED_CLAIMS =
SAFETY_FLAGS =
QUALITY_WEAKNESSES =
RETURN_TO = NONE | STAGE_0 | STAGE_1 | STAGE_2 | STAGE_3
```

关注：儿童视角、Want、人物不可替代性、Story Vitality、Curiosity、情绪推进、游戏感、对白、文学节奏、原创特异性。

不打总分；`STRONG` 也不等于真实儿童已经验证。

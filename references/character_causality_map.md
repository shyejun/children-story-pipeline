---
title: "Character Causality Map｜角色个性因果合同"
version: "v1.0"
status: "ACTIVE"
scope: "STAGE_1_TO_STAGE_2_CHARACTER_CAUSALITY"
---

# Character Causality Map｜角色个性因果合同

本 Reference 用于把 角色设定 从“性格标签 / 台词风格”转换成真正参与 Story Spine 的因果机制。它不新增永久角色设定、不修改用户已确认的角色卡、不要求每集制造冲突，也不取代 Stage 1 Character Dynamics、`story_spine_and_causality.md` 或 Story Engine。

核心原则：

> 角色个性只有在改变“怎么理解 → 怎么行动 → 产生什么后果 → 伙伴如何回应 → 最后怎样调整方法”时，才算进入故事因果。

不得只靠口头禅、语气、道具或形容词证明人物成立。

## 1. 每位主要角色的 CHARACTER_CAUSALITY_MAP

Stage 1 对每位 `MAIN_CHARACTER` 记录：

```text
CHARACTER =
CORE_TRAIT =
DEFAULT_INTERPRETATION =
DEFAULT_ACTION =
WHY_THIS_ACTION_FITS_CHARACTER =
OVERUSE_RISK =
UNIQUE_CONSEQUENCE =
PARTNER_RESPONSE_TRIGGERED =
FINAL_METHOD_ADJUSTMENT =
TRAIT_PRESERVED = YES | NO
```

字段含义：

- `CORE_TRAIT`：只引用 角色卡 / 用户已确认角色设定 已确认的长期性格 / 动力，不新增永久设定。
- `DEFAULT_INTERPRETATION`：面对本集局面时，这个角色第一眼会如何理解，不写成人抽象心理诊断。
- `DEFAULT_ACTION`：角色按自己的方法最自然会先做什么。
- `WHY_THIS_ACTION_FITS_CHARACTER`：用既有 Canon 说明为什么偏偏是这个行动。
- `OVERUSE_RISK`：已有优点 / 方法如果使用过头，会带来什么儿童尺度的小偏差；低冲突故事可记为注意力、节奏、关系或行动时机偏差，不强制“犯错”。
- `UNIQUE_CONSEQUENCE`：该角色方法必须在现场、物体、信息、关系或下一步行动中留下可见结果。
- `PARTNER_RESPONSE_TRIGGERED`：伙伴因为这个新条件，必须做出自己的角色化回应。
- `FINAL_METHOD_ADJUSTMENT`：结尾只调整“方法怎么用”，不把人物改造成相反性格。
- `TRAIT_PRESERVED`：长期人格应保持 `YES`。若必须写成 `NO` 才能让故事成立，返回 Stage 1 / Project Constraint Review，而不是靠单集改人格。

## 2. 双主角 RELATIONSHIP_CAUSAL_LOOP

普通双主角单集额外记录：

```text
RELATIONSHIP_CAUSAL_LOOP =
A_ACTION_CREATES =
B_RESPONSE_CREATES =
A_NEXT_ACTION_CHANGES_BECAUSE =
B_NEXT_ACTION_CHANGES_BECAUSE =
FINAL_SOLUTION_COMBINES =
```

要求：

```text
A 的角色化行动
→ 改变现场 / 问题 / 信息
→ B 按自己的角色方法回应
→ B 的回应改变 A 的下一步
→ A 的新行动继续影响 B 的行动 / 注意力 / 参与方式
→ 最终解决方式至少保留两种人物方法中的一部分

“双向”指行动与关系因果双向，不要求两位角色都获得成长弧。稳定型伙伴可以保持原有方法，只要其下一步确实因对方行动而改变，而不是从头到尾站在原地提供答案。
```

禁止退化成：

```text
A 犯错
→ B 说正确答案
→ A 改正
```

也禁止：

```text
A 做动作
→ B 只观察 / 夸赞
→ 结局由旁白或第三人完成
```

低冲突故事不强制失败、不强制加第二角色；角色因果可以体现为注意力、关系、行动时机或观察路径的变化。

低冲突发现型可以是：

```text
A 注意到 / 靠近
→ B 因自己的关注点看见另一层信息
→ A 改变注意力或动作
→ 两人共同形成新的观察 / 关系 / 温和回应
```

不强制失败、争执或互相纠正。

## 3. 三项 Character Causality Test

### REMOVE CHARACTER TEST

删除主要角色后，若只需把其一句台词 / 一个线索交给别人，主因果与最终解决几乎不变：

```text
REMOVE_CHARACTER_TEST = FAIL
```

Supporting Character 可被删而不改变主因果并不自动 FAIL，但应确认其存在理由；若只是观点载体，优先匿名化或删除。

### SWAP CHARACTER TEST

把主要角色与另一位已定义角色对换，若：

- 首次行动仍完全一样；
- 伙伴回应仍完全一样；
- 最终解决仍完全一样；

则：

```text
SWAP_CHARACTER_TEST = FAIL
```

通过条件不是“别人绝对做不到”，而是：换人后至少一个关键因果节点理应改变方法、节奏、注意力、互动方式或结果路径。SWAP TEST 不要求为测试额外加载全体 角色卡 / 用户已确认角色设定s；优先使用当前已读角色或 Runtime 已明确的角色方法作反事实检查，禁止为了测试扩大到全角色库。

### CONSEQUENCE TEST

每位主要角色至少产生一个来自自身方法的 `UNIQUE_CONSEQUENCE`。它可以是：

- 物体状态变化；
- 信息被发现或被错过；
- 行动时机变化；
- 伙伴被带入新的行动；
- 关系位置发生轻微变化；
- 低冲突故事中的注意力转向。

若性格只体现在台词、口头禅、表情或装饰道具，而不改变下一步：

```text
CONSEQUENCE_TEST = FAIL
```

## 4. Trait Preservation + Method Adjustment

幼儿系列故事的角色成长优先采用：

```text
TRAIT PRESERVED
+
METHOD ADJUSTED
```

例如：

- 爱庆祝 → 仍爱庆祝，但从“大装饰”改成“小记号”；
- 爱观察 → 仍爱观察，但看到关键线索后更快进入行动；
- 爱热闹 / 节奏 → 仍然活泼，但把大动作收成一个小节拍；
- 爱照顾别人 → 仍然温柔，但愿意说出自己的真实感受。

禁止为了教育结论写成明显人格反转，例如“活泼角色最后变得非常谨慎”“爱庆祝角色从此不装饰”。

## 5. Stage 2 Spine 接口

Stage 2 构造 Story Spine 时必须使用当前 Stage 1 的 `CHARACTER_CAUSALITY_MAP`，特别检查：

```text
WANT
→ DEFAULT_INTERPRETATION
→ ATTEMPT_1 / FIRST_OBSERVATION
→ UNIQUE_CONSEQUENCE
→ PARTNER_RESPONSE_TRIGGERED
→ NEW_INFORMATION
→ RETHINK
→ FINAL_ACTION
→ FINAL_METHOD_ADJUSTMENT
```

`ATTEMPT_1` 不能只是“符合角色设定”的动作，还必须来自角色的默认解释 / 方法；`NEW_INFORMATION` 不能只由万能旁白提供；`FINAL_ACTION` 应尽量是角色在保留自身特质的情况下采用的新方法。

## 6. Gate

Stage 1 / Stage 2 之间的角色因果 Gate：

```text
CHARACTER_CAUSALITY_MAP_COMPLETE = YES | NO
REMOVE_CHARACTER_TEST = PASS | FAIL
SWAP_CHARACTER_TEST = PASS | FAIL
CONSEQUENCE_TEST = PASS | FAIL
RELATIONSHIP_CAUSAL_LOOP = PASS | NOT_APPLICABLE
CHARACTER_CAUSALITY_RESULT = PASS | FAIL
```

普通双主角故事：`REMOVE / SWAP / CONSEQUENCE` 通过，且 `RELATIONSHIP_CAUSAL_LOOP` 能证明行动互相影响后，`CHARACTER_CAUSALITY_RESULT = PASS`。不要求两位角色都发生人格成长。

单主角 / 低冲突 / 群像特殊故事若 `RELATIONSHIP_CAUSAL_LOOP` 不适用，可记 `NOT_APPLICABLE` 并说明原因；不得为通过 Gate 强加第二角色。

FAIL 优先返回 Stage 1 调整角色职责与本集方法；若人物选择本身正确但 Story Spine 没有使用该因果，则在 Stage 2 修复。不得到 Stage 3 只靠“更有个性的对白”补救。

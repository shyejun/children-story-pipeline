---
title: "Story Spine 与因果构造"
version: "v1.1"
status: "ACTIVE"
scope: "STAGE_2_STORY_CONSTRUCTION"
---

# Story Spine 与因果构造

本 Reference 负责在 Stage 2 把选题构造成可写的故事。它不替换六类 Story Engine、现有两种 Story Structure Profile 或 `child_story_8beat.md`；既有 Story Vitality Reference 仍处理选择性的表现力提升，Visual Narrative Continuity Reference 仍处理正文中的叙事跳步。

## 1. 构造顺序

`Story Engine → Character Causality Map → Story Spine → Causal Chain → 8 Beat → Story Draft`。`CHARACTER_CAUSALITY_MAP` 来自 Stage 1，Stage 2 只验证和使用，不重写长期人物设定。不得只选一个 Engine 就直接写完整故事。Story Spine 是八主 Beat 的因果基础；八主 Beat 是它在儿童可感知事件中的展开。

## 2. Story Spine 十项

| 字段 | 必答问题 | Stage 2 输出字段 |
|---|---|---|
| `WHO` | 主角是谁？ | 已有 `main_characters` |
| `WANT` | 主角此刻具体想做或弄清什么？ | `CHARACTER_WANT` |
| `WHY_IT_MATTERS` | 为什么此刻对他重要？ | `WHY_IT_MATTERS_NOW` |
| `OBSTACLE` | 什么具体条件阻止或限制了他？ | `CORE_OBSTACLE` |
| `ATTEMPT_1` | 按角色自己的方法，首先做什么？ | `ATTEMPT_1` |
| `ATTEMPT_1_RESULT` | 第一次行动改变了什么，为什么尚未完成？ | `ATTEMPT_1_VISIBLE_RESULT` |
| `NEW_INFORMATION` | 角色从结果中得到什么新线索？ | `NEW_INFORMATION` |
| `RETHINK` | 新线索为何使角色改变下一步？ | `CHARACTER_RETHINK` |
| `FINAL_ACTION` | 角色主动采取什么新行动？ | `FINAL_ACTION` |
| `VISIBLE_CHANGE` | 物体、环境、关系或理解最终发生什么可见变化？ | `FINAL_VISIBLE_RESULT` |

另记 `EMOTIONAL_ECHO`：结尾回应开头已建立的愿望、关系期待或儿童经验，不追加教育总结。`WANT` 可以是 Canon 已支持的现有愿望或好奇，不为了填字段另加奖品、比赛、期限或压力。普通问题解决型的 `OBSTACLE` 必须真正阻止 `WANT`，来自环境、信息不足、角色误解、合理的首次判断、已有关系或 项目设定或世界条件；不随机制造事故。

核心因果：`WANT → CHARACTER_INTERPRETATION → CHARACTER_ACTION → UNIQUE_CONSEQUENCE → PARTNER_RESPONSE / NEW_INFORMATION → RETHINK → NEW_ACTION → CHANGE`。首次行动应同时符合 Story Spine 与 `character_causality_map.md`：不是只“符合性格”，而是由角色如何理解当前问题自然推出，并留下只有这种方法才会优先制造的后果。第一次行动应至少改变物体状态、信息状态、角色理解、角色关系或环境条件；不能只写“试了 → 不行”。新信息必须源于前文已发生的事，不突然加入知识、工具、成人答案、未铺垫角色或万能救援。最后关键变化主要由角色自己发现、选择和行动产生。

## 3. Stage 2 的 CAUSAL_CHAIN

用至少三组实际因果连接记录主要转折：

```text
因为……，所以……。
因为……，所以……。
因为……，所以……。
```

每组必须指向前一行动、反馈或发现，不以“然后……然后……”的事件清单代替。Stage 2 另附八行 Beat 功能映射；先通过 Spine 与因果，再展开 Beat。

## 4. Story Spine Gate 与 Causality Test

- `WHY NOW TEST`：为什么偏偏此时发生？若任何一天都一样，重查触发点。
- `WHY THIS CHARACTER TEST`：为什么必须由这个角色行动？若任一其他角色互换都成立，重查角色动力与方法。
- `SWAP CHARACTER TEST`：把主要角色替换成另一位 Canon 角色后，首次行动、伙伴回应、最终解决若都可原样保留，则 FAIL；换人后至少一个关键因果节点理应改变。
- `CONSEQUENCE TEST`：每位主要角色的方法至少造成一个 `UNIQUE_CONSEQUENCE`，并改变伙伴或下一步；只改变语气、口头禅、表情或道具不算。
- `BECAUSE / THEREFORE TEST`：主要 Beat 能否用“因为……所以……”相连？只能用“然后”串联则 `CAUSALITY = FAIL`。
- `REMOVE TEST`：删掉一个主 Beat，后续状态若完全不变，该 Beat 应删除、合并或重写；完整故事最终仍须保留八个有功能的主 Beat。

Stage 2 PASS 前确认：具体 WANT、与它相连的 OBSTACLE、能回链 `DEFAULT_INTERPRETATION / DEFAULT_ACTION` 的首次行动、角色方法造成的 `UNIQUE_CONSEQUENCE`、被该后果触发的伙伴回应或新信息、由信息引起的重新判断、与 `FINAL_METHOD_ADJUSTMENT` 一致的角色主动后续行动。普通双主角故事还要确认 `RELATIONSHIP_CAUSAL_LOOP` 双向成立。失败时在 Stage 2 修复，不把结构缺口留给 Stage 3 的文句润色。

## 5. LOW_CONFLICT_DISCOVERY 的等价处理

低冲突发现型仍填 Stage 2 字段，但 `CORE_OBSTACLE` 与问题解决意义上的 `ATTEMPT_1` 可明确记 `NOT_APPLICABLE`，不得暗中制造任务、失败或解决。用对应的 `FIRST_OBSERVATION`、`OBSERVATION_RESULT` 记首次主动靠近、观察或体验及其新细节；`NEW_INFORMATION` 是感知或关系发现，`CHARACTER_RETHINK` 是注意力或行动的轻调整，`FINAL_ACTION` 是主角主动回应，`FINAL_VISIBLE_RESULT` 是开放的现场、关系或情绪变化。

其因果链为：`注意到变化 → 主动靠近 → 体验 → 出现新细节 → 形成发现 → 主动回应 → 温和回声`。继续遵守 `FORCED_PROBLEM = FALSE`、`TOUR_GUIDE_FAILURE = FALSE` 与开放结尾 Gate。不能把“换一个地点”本身当作新信息。


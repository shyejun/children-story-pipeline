---
title: "儿童故事 QA"
version: "v1.4"
status: "ACTIVE"
scope: "GENERIC_CHILDREN_STORY"
---

# 儿童故事 QA

Stage 3 PASS 前逐项检查；Stage 4 继续执行正式 Story Consistency Check；若项目提供 Canon / 角色圣经 / 世界观规则，则同时检查兼容性。本表是现有 Gate 的辅助检查，不新增 Reviewer Agent、Hook、独立审核系统或修复循环。

| 检查项 | 可观察的通过条件 |
|---|---|
| `AGE_FIT` | 儿童经验、认知、角色行为、冲突、教育目标与角色对白符合 Story Brief 的核心年龄档；不以幼儿朗读语言限制成人母稿叙事 |
| `EIGHT_BEAT_INTEGRITY` | 完整故事八个主 Beat 各有功能；低冲突发现型未被迫制造冲突 |
| `CHARACTER_DRIVEN` | 主要角色的选择与行动推动下一步且能回链 `CHARACTER_CAUSALITY_MAP`；至少有 `UNIQUE_CONSEQUENCE`，主要角色互换后关键因果节点不能全部原样成立 |
| `CAUSALITY` | 关键变化、线索、首次执行与可见结果连续，陌生下游无需补造 |
| `ONE_CORE_DISCOVERY` | 只保留一个清晰的核心儿童发现 |
| `NO_PREACHING` | 教育意义主要从剧情结果产生，无直接训诫或答案机器 |
| `NO_KNOWLEDGE_OVERLOAD` | 科学、文化、自然与生活知识服从儿童问题与角色行动 |
| `CHILD_SAFETY` | 无鼓励儿童模仿危险动作、羞辱性表达或不安全行为；涉及火、烤炉、热器具、利器、电器、高处等时必须继续通过 `CHILD_IMITATION_SAFETY` |
| `CANON_COMPATIBILITY` | 若项目提供上游设定，则服从角色卡、世界观、地点规则与用户冻结约束；无项目 Canon 时为 N/A |
| `ADAPTATION_READINESS` | 故事事件完整、媒介无关，可供陌生下游改编 |
| `STORY_INFORMATION_SUFFICIENCY` | 完整正文单独可读；陌生下游无需借助结构化附录补写动机、动作过程、衔接、物体状态、决定依据、教育发现或结尾 Payoff |
| `CHILD_PARTICIPATION_EXECUTION` | 正文已按核心年龄档完成儿童参与闭环；每个闭环可追溯角色或现场邀请、儿童可执行动作、故事回应与参与后的继续推进，结构化接口未替代正文 |

角色因果辅助检查（不新增数值评分项）：

```text
CHARACTER_CAUSALITY_RESULT = PASS | FAIL
REMOVE_CHARACTER_TEST = PASS | FAIL
SWAP_CHARACTER_TEST = PASS | FAIL
CONSEQUENCE_TEST = PASS | FAIL
RELATIONSHIP_CAUSAL_LOOP = PASS | NOT_APPLICABLE
TRAIT_PRESERVED = YES | NO
```

若角色仅有不同说话风格，但问题制造、首次行动、伙伴回应和最终解决都可被其他角色无差别替换，`CHARACTER_DRIVEN` 必须 FAIL。低冲突 / 单主角故事不要求强行建立双主角循环。


## Final Story Integrity Hard Gate

在十一项 Story Quality 与 `STORY_INFORMATION_SUFFICIENCY` 之外，对**最终连续故事正文**执行以下硬检查；它们不是新的 Story Quality 评分项：

| 检查项 | 通过条件 |
|---|---|
| `OBJECT_STATE_CONTINUITY` | 关键物体的身份、数量、位置、成分、可见状态、持有者、使用状态及变化原因连续；任何新状态都能找到正文事件来源 |
| `CAUSAL_VARIABLE_INTEGRITY` | 比较 / 实验 / 多少 / 加减等故事中，真正变化的变量与故事声称的效果一致；未把体积、数量、浓度、甜度、颜色、健康性等不同变量偷换 |
| `CLAIM_GROUNDING` | 角色感觉、现场观察、一般事实、健康 / 科学 / 文化 Claim 被正确分层；核心客观 Claim 有正文证据或可靠事实来源 |
| `CHILD_IMITATION_SAFETY` | 儿童化角色没有在缺乏既有安全机制时直接执行高温、火、利器、电器、高处等易模仿危险动作 |
| `EDUCATION_DIRECTION` | 教育故事不羞辱儿童、群体、身体、能力或生活选择；若存在已确认的安全 / 健康 / 科学方向，不得为了温和而改写成“所有选择完全等价”；非教育题材可 N/A |

聚合：

```text
HARD_GATE_STATUS = PASS | FAIL
```

`OBJECT_STATE_CONTINUITY / CAUSAL_VARIABLE_INTEGRITY / CHILD_IMITATION_SAFETY` 任一 FAIL，或核心 `CLAIM_GROUNDING` FAIL，均必须令 `HARD_GATE_STATUS = FAIL`。不得用 Beat 齐全、语言流畅、Canon 正确或模型自评 PASS 覆盖。

## Independent Final Review

硬门槛通过后，以最终正文证据重新判断：

```text
STORY_QUALITY_JUDGMENT = STRONG | ADEQUATE | NEEDS_REWRITE | HUMAN_REVIEW
```

该判断不打分、不排名。`STRONG / ADEQUATE` 只表示当前文本的专业判断，不等于儿童实测；`NEEDS_REWRITE` 回最早必要层；`HUMAN_REVIEW` 必须把具体疑点传给 Stage 6。

`STORY_INFORMATION_SUFFICIENCY` 属于现有 Story Master Gate，不是 Story Quality 评分项。FAIL 时返回 Story Rewrite 补充最低充分细节；不能只在 Story Lock、场景表或 Adaptation Handoff 中补注，也不能按字数判断。

`CHILD_PARTICIPATION_EXECUTION` 同属现有 Story Master Gate，不新增 Story Quality 评分项。4–5 岁默认检查 2–4 个观察、预测或简单选择闭环。只有“可预测点”、问句标题、互动接口字段或 Handoff 说明，而正文没有 `INVITATION → CHILD_ACTION → STORY_ACKNOWLEDGEMENT → CAUSAL_CONTINUATION`，必须判 FAIL 并返回 Story Rewrite。

`Education Intent Contract` 不新增 Gate 或评分项，但必须与最终正文对齐：`CHILD_EXPERIENCE` 和 `MUST_PRESERVE_BEHAVIORAL_EVIDENCE` 能定位正文；`TRANSFERABLE_CAPABILITY` 只描述故事提供的练习机会，不把一次行为写成已经形成的能力；`ADULT_EDUCATION_INTENT` 不进入儿童正文；`REAL_GAP` 明确故事不能独立证明的长期结果。若合同夸大，优先缩小合同，而不是为合同增写剧情。

局部故事问题沿用既有 `AUTO_REPAIR_LOOP`：定位最早问题 Stage、保存 Regression、重验后继续。若问题必须修改用户冻结设定、外部事实来源或模板基线，按现有 `BLOCKED + HUMAN_DECISION_REQUIRED` 停止，不自行上改。

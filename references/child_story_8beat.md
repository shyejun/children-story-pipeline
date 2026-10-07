---
title: "儿童完整故事八主 Beat 合同"
version: "v1.1"
status: "ACTIVE"
scope: "GENERIC_CHILDREN_STORY"
---

# 儿童完整故事八主 Beat 合同

`MAIN_BEAT_COUNT = 8`。这是完整故事的 Narrative Beat Contract，不是第七类 Story Engine、第三种 Story Structure Profile，也也不替代当前选定的 Story Structure Profile。每个 Beat 要有不同的叙事功能：角色行动、儿童注意力、信息或现场状态至少一项发生可见变化。一个现有段落可以容纳多个 Beat，不必增设八个正文标题或八个场景。

## STANDARD_PROBLEM_SOLVING

| Beat | 功能 | 与现有七段式的常见映射 |
|---|---|---|
| 1 | 日常状态 | 第一段：今天要做什么 |
| 2 | 发现问题 | 第二段：出现小麻烦 |
| 3 | 角色决定行动 | 第二段末或第三段开端 |
| 4 | 第一次尝试 | 第三段：第一次尝试 |
| 5 | 意外反馈 / 新困难 | 第三段末或第四段：互动与重复 |
| 6 | 发现关键线索 | 第四段末或第五段：发现真正的方法 |
| 7 | 角色主动采取新行动 | 第五段至第六段：执行方法 |
| 8 | 问题解决 + 情绪回声 | 第六段至第七段：完成与生活迁移 |

首次尝试可以部分成功；反馈须改变后续行动，不要求纯失败或固定三次尝试。解决来自前文线索和角色行动，情绪回声不写成教育总结。

## LOW_CONFLICT_DISCOVERY

| Beat | 功能 | 与现有五段式的常见映射 |
|---|---|---|
| 1 | 日常状态 | ENTER |
| 2 | 注意到变化 | DISCOVER 开端 |
| 3 | 主动靠近 | DISCOVER 后续 |
| 4 | 第一次观察 / 体验 | DISCOVER 或 REPEAT_WITH_VARIATION 开端 |
| 5 | 出现新的细节 | REPEAT_WITH_VARIATION |
| 6 | 形成关键发现 | REPEAT_WITH_VARIATION 至 ADJUST |
| 7 | 主角主动回应 | ADJUST |
| 8 | 温和开放回声 | OPEN |

Beat 5 只需新细节，不是新困难；Beat 6 是感知或关系的发现，不是问题答案；Beat 7 是主动回应，不是补救。不得为了凑八个 Beat 创造任务、事故、失败、解决或完成庆祝。继续执行 Runtime 的 `CHARACTER_CAUSALITY`、`REPETITION_WITH_VARIATION`、`TOUR_GUIDE_FAILURE = FALSE`、`FORCED_PROBLEM = FALSE` 与 `OPEN_ENDING` Gate。

## 输出与媒介边界

Stage 2 的 Story Engine Plan 以八行映射表记录 `BEAT_ID / NARRATIVE_FUNCTION / CHARACTER_ACTION / VISIBLE_CHANGE / EXISTING_SECTION`；不在此写完整故事。Stage 3 检查八项功能在正文中均可找到，保留既有七段式或五段式模板。短动画与长动画都不删减八个主 Beat；时长和扩展方式只在 Adaptation Handoff 交接。5–7 分钟只增加 Beat 内必要动作、互动、情绪、环境反应或 Micro Beat。广告、预告片、宣传片、片段等非完整故事媒介不强制此合同。

## Beat Sequence Gate

Stage 2 展开八主 Beat 后必须记录 `BEAT_SEQUENCE_VALID = YES | NO`。以下四项全部成立才可为 `YES`：

1. 角色行动先于该行动产生的反馈或结果。
2. 新信息出现在产生它的行动、观察或反馈之后。
3. 最终行动出现在角色重想之后。
4. Beat 编号与计划中的实际时间顺序、因果顺序一致。

`NO` 表示 Stage 2 FAIL，必须先重排或重写 Beat；不得让 Stage 3 用正文掩盖顺序错误。

## Final Beat Trace Review

正式 Story Master 组装完成后、进入 Story Consistency Check 前，对最终文件本身逐 Beat 记录：

| 字段 | 要求 |
|---|---|
| `BEAT_ID` | 1–8 |
| `BEAT_FUNCTION` | 对应该 Structure Profile 的叙事功能 |
| `FINAL_STORY_EVIDENCE` | 最终正文中的具体动作、反馈、发现或回声 |
| `FINAL_LOCATION` | 最终文件中的标题、段落或可复核文本锚点 |
| `TRACE_STATUS` | `PASS | FAIL` |

一个 Beat 可以跨段，多个 Beat 也可以位于同一段；不得为了追踪强制建立八个章节或向儿童正文添加解释。若最终位置与 Stage 2 映射不同，当前追踪记录须写明新位置和差异，旧位置不得继续被引用为当前位置。八项 `TRACE_STATUS = PASS` 后仍须再次确认最终正文实际顺序满足 `BEAT_SEQUENCE_VALID = YES`。

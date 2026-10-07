---
name: children-story-pipeline
description: "Create and review original 3–6-year-old children's stories through a structured 0–6 stage pipeline: brief, character causality, story engine, 8-beat Story Master, consistency/quality audit, adaptation handoff, and human-review delivery. Works standalone or with an optional existing IP/Canon."
metadata:
  short-description: Generic children's story creation and QA pipeline
---

# Children Story Pipeline

版本：v2.0.0
状态：GENERIC_PRODUCTION_BASELINE
默认模式：FULL_AUTO_PRODUCTION

## 1. 目的

本 Skill 用于**通用 3–6 岁儿童原创故事创作**。它不绑定任何固定 IP、角色、世界观、食育主题、地点、品牌或系列。

核心链路：

```text
自然语言故事需求
→ Stage 0 Story Brief
→ Stage 1 Character Dynamics
→ Stage 2 Story Engine
→ Stage 3 Story Master
→ Stage 4 Story Consistency Check
→ Stage 5 Adaptation Handoff
→ Stage 6 Human Review Delivery
```

默认连续执行；只有用户明确要求暂停，或存在必须由人确认的事实 / 长期设定冲突时停止。

最高原则：

> **故事先成立，再谈教育；角色用行动进入因果；完整故事保留 8 Beat；质量审核不能被“设定正确”替代。**

## 2. 使用模式

### STANDALONE
没有现成 IP / Canon 时直接创作。用户给出的角色、背景、主题和禁止项就是当前任务约束。Skill 可以补足本集必要临时设定，但不得把它们自动升级成长期世界观。

### CANON_AWARE
用户提供角色圣经、世界观、系列设定、历史剧集或项目 Source 时，按 `references/project_constraints_optional.md` 读取并执行一致性检查。

Canon 是**可选约束**，不是运行本 Skill 的前置条件。

## 3. 全局不变量

1. 完整儿童故事默认 `MAIN_BEAT_COUNT = 8`。短时长压缩 Beat 展开，不先删除主 Beat。
2. Story Master 面向成人创作者与下游适配，是媒介中立的故事母版；不是最终绘本文字、动画配音稿、分镜或生图提示词。
3. 默认完整动画目标为 `90–120 秒`；5–7 分钟通过扩展 Beat 内动作、互动、情绪与 Micro Beat 实现。
4. 角色性格必须进入因果：`解释 → 行动 → 独特后果 → 伙伴回应 → 方法调整`。
5. 角色成长优先 `TRAIT_PRESERVED + METHOD_ADJUSTED`，不把人物教育成相反人格。
6. 每集只保留一个清晰核心儿童经验 / 发现，不堆叠多个教育目标。
7. 教育意义主要通过行动、反馈、选择与结果产生，不写“这个故事告诉我们”。
8. 科学、自然、健康、历史、文化等可核验 Claim 必须遵守 `fact_grounding_contract.md`。
9. 儿童模仿安全、物体状态连续、变量因果与事实真实性属于硬门槛。
10. 任何 Stage FAIL 先回到最早问题来源修复；同一 Stage 自动修复最多 3 次。
11. Regression 不覆盖旧 Artifact；下游只读取唯一明确的 Current Effective Artifact。
12. 下游绘本 / 动画可以改变“怎么讲”，不能擅自改变“讲什么、人物为什么这样做、核心事实是什么”。

## 4. 核心 References

正式任务按需读取：

- `references/child_age_profiles.md`
- `references/story_engine_profiles.md`
- `references/character_causality_map.md`
- `references/story_spine_and_causality.md`
- `references/child_story_8beat.md`
- `references/story_rewrite_protocol.md`
- `references/story_master_visual_narrative_continuity.md`
- `references/story_master_story_vitality.md`
- `references/children_story_prose.md`
- `references/education_without_preaching.md`
- `references/education_intent_contract.md`
- `references/fact_grounding_contract.md`
- `references/child_story_qa.md`
- `references/final_story_integrity_audit.md`
- `references/current_effective_artifact.md`
- `references/project_constraints_optional.md`（仅 CANON_AWARE）

不要一次性加载所有外部项目资料；只读取当前故事真正需要的角色、世界、事实和历史信息。

## 5. 输出目录

新故事统一使用：

```text
outputs/<STORY_ID>_<title>_vX/
└─ 01_story/
   ├─ 00_story_brief.md
   ├─ 01_character_dynamics_plan.md
   ├─ 02_story_engine_plan.md
   ├─ 03_story_master.md
   ├─ 04_story_consistency_check.md
   ├─ 05_adaptation_handoff.md
   ├─ current_effective_artifacts.md   # 只有发生 Regression 时需要
   └─ delivery/
      └─ 06_<title>_完整故事审阅版.docx  # 若运行环境支持 DOCX
```

若环境不支持 DOCX，Stage 6 生成等价 Markdown 审阅版，不因此阻塞完整故事生产。

## 6. 状态字段

所有 Stage 顶层状态：

```text
STATUS = PASS | FAIL | BLOCKED
```

流水线字段：

```text
PIPELINE_MODE
NEXT_STAGE_AVAILABLE
NEXT_STAGE
HUMAN_GATE_REQUIRED
AUTO_REPAIR_STATUS
HUMAN_DECISION_REQUIRED
DELIVERY_READY
```

Stage 4 结果：

```text
CONSISTENCY_CHECK_RESULT =
PASS | RETURN_TO_STORY_MASTER | RETURN_TO_STORY_ENGINE | PROJECT_CONSTRAINT_REVIEW | SOURCE_RECHECK_REQUIRED
```

## 7. 默认自动执行与暂停

默认：

```text
FULL_AUTO_PRODUCTION = ON
PAUSE_AFTER_STAGE = NONE
AUTO_REPAIR_ATTEMPTS = 3
```

识别自然语言暂停：

- “先给我看方向 / Brief” → `PAUSE_AFTER_STAGE = STORY_BRIEF`
- “角色先定一下” → `CHARACTER_DYNAMICS`
- “完整故事写完先给我看” → `STORY_MASTER`
- “审核后先停” → `CONSISTENCY_CHECK`

用户没有要求暂停时，不因角色名、地点名、标题、Engine 等可由创作者判断的事项反复追问。只有缺失信息会改变用户核心创作意图、事实真假或长期设定时才需要人工决策。

---

# Stage 0｜Story Brief

输入：用户需求；CANON_AWARE 时加必要项目设定；涉及可核验知识时加必要来源。

输出：`01_story/00_story_brief.md`，使用 `templates/00_story_brief_template.md`。

必须锁定：

- Story ID、暂定标题、版本；
- `TARGET_AGE = 3-4 | 4-5 | 5-6`；未指定时默认优先 4–5，并依据题材调整；
- 核心儿童经验 / 一个核心发现；
- 主要角色候选；
- 当前故事发生的具体情境；
- 题材类型与 Primary Engine 候选；
- 用户明确禁止项；
- 是否需要事实核查；
- `PROJECT_CONSTRAINT_MODE`；
- 下游偏好：90–120 秒动画 / 5–7 分钟动画 / 绘本 / 文本 / 未指定。

若涉及可核验知识，记录 `CORE_FACT_CLAIM / FACT_TYPE / FACT_SOURCE / CHILD_CORE_DISCOVERY / DO_NOT_OVERSTATE`。

Gate：

- 只有一个清晰核心儿童经验；
- 问题 / 发现属于儿童可经历的尺度；
- 没有把世界观介绍、知识讲解或角色名单当成故事；
- 核心事实无来源时不伪装成确定知识；
- CANON_AWARE 时人物与世界未越权。

PASS 后自动 Stage 1。

---

# Stage 1｜Character Dynamics

输入：Story Brief、必要角色设定、`character_causality_map.md`。

输出：`01_character_dynamics_plan.md`。

必须锁定：

- PRIMARY_DRIVER；
- KEY_OBSERVER；
- MAIN / SUPPORTING CHARACTERS；
- 每位主要角色的 `CHARACTER_CAUSALITY_MAP`；
- 双主角适用时的 `RELATIONSHIP_CAUSAL_LOOP`。

Gate：

- 每个主要角色都有不可替代行动；
- `REMOVE_CHARACTER_TEST = PASS`；
- `SWAP_CHARACTER_TEST = PASS`；
- `CONSEQUENCE_TEST = PASS`；
- `TRAIT_PRESERVED = YES`；
- 观察者 / 辅助角色不成为答案机器；
- 普通 4–5 岁单集优先 1 位核心主角 + 1–2 位辅助角色，但不是硬上限。

失败优先在 Stage 1 修角色职责与方法，不留到对白阶段“补人设”。

PASS 后自动 Stage 2。

---

# Stage 2｜Story Engine

输入：Stage 0–1、`story_engine_profiles.md`、`story_spine_and_causality.md`、`child_story_8beat.md`。

输出：`02_story_engine_plan.md`。

构造顺序固定：

```text
Story Engine
→ Character Causality Map
→ Story Spine
→ Causal Chain
→ 8 Beat
→ Story Draft
```

默认 Structure Profile：`STANDARD_PROBLEM_SOLVING`。真正的日常发现 / 自然观察 / 序章可用 `LOW_CONFLICT_DISCOVERY`。

从六类 Engine 中选主发动机：

```text
E1 Goal & Obstacle
E2 Curiosity & Discovery
E3 Relationship & Coordination
E4 Misunderstanding & Reframe
E5 Pattern & Variation
E6 Making & Transformation
```

Story Spine 至少建立：

```text
WHO / WANT / WHY_IT_MATTERS / OBSTACLE
ATTEMPT_1 / ATTEMPT_1_RESULT
NEW_INFORMATION / RETHINK
FINAL_ACTION / VISIBLE_CHANGE / EMOTIONAL_ECHO
```

并用至少三组“因为……所以……”建立 `CAUSAL_CHAIN`。

八个主 Beat：

1. 日常状态
2. 发现问题 / 变化
3. 角色决定行动 / 主动靠近
4. 第一次尝试 / 观察
5. 意外反馈 / 新细节
6. 关键线索 / 发现
7. 角色主动采取新行动 / 回应
8. 解决或温和开放回声

Gate：

- `CHARACTER_CAUSALITY_RESULT = PASS`；
- WANT、行动、反馈、新信息与最终行动相连；
- 不靠突然出现的成人答案、万能工具或未铺垫知识解决；
- `WHY NOW / WHY THIS CHARACTER / BECAUSE-THEREFORE / REMOVE` 通过；
- `BEAT_SEQUENCE_VALID = YES`；
- 比较 / 实验型故事执行 `CAUSAL_VARIABLE_CHECK`；
- 低冲突型不被迫增加事故、失败或庆祝。

Stage 2 只做计划，不写完整正文、分页、镜头或提示词。

PASS 后自动 Stage 3。

---

# Stage 3｜Story Master

输入：当前有效 Stage 0–2、相关 References；有外部项目设定时读取必要约束。

输出：`03_story_master.md`，使用 `templates/03_story_master_template.md`。

定位：

```text
Adult-facing + medium-neutral + adaptation-ready narrative master
```

它必须是完整、连续、可独立阅读、可被绘本 / 动画 / 朗读等下游改编的故事母版。

## 3.1 Education Intent Contract

从最终故事事实反推：

- CHILD_EXPERIENCE
- TRANSFERABLE_CAPABILITY
- ADULT_EDUCATION_INTENT
- REAL_GAP
- DO_NOT_TEACH_DIRECTLY
- MUST_PRESERVE_BEHAVIORAL_EVIDENCE

没有明确教育目标的游戏 / 审美 / 关系体验故事允许部分字段 `NOT_APPLICABLE`。

## 3.2 三轮写作

```text
PASS 1 = EVENT DRAFT
PASS 2 = NARRATIVE ENRICHMENT / STORY REWRITE
PASS 3 = LANGUAGE & DIALOGUE POLISH
```

第一稿不得直接当最终 Story Master。

Pass 2 内部回答：

```text
WHAT_CHANGES
WHY_KEEP_WATCHING
DO_CHARACTERS_AFFECT_EACH_OTHER
CHARACTER_CAUSALITY_PRESERVED
```

## 3.3 儿童参与闭环

互动只在适合故事时使用，不是每集硬配额。4–5 岁普通互动型故事可参考 2–4 个自然闭环：

```text
INVITATION
→ CHILD_ACTION
→ STORY_ACKNOWLEDGEMENT
→ CAUSAL_CONTINUATION
```

正式正文只保留自然对白、动作和回应，不嵌入字段名或教案标签。

## 3.4 Story Quality Review

以下十一项只判 `PASS | FAIL`，不打总分：

- STORY_CLARITY
- MOTIVATION_LOGIC
- CAUSE_EFFECT
- ATTEMPT_LOGIC
- CHARACTER_AGENCY
- CHARACTER_VOICE
- SCENE_PURPOSE
- DIALOGUE_FUNCTION
- LANGUAGE_FLUENCY
- READ_ALOUD_QUALITY
- ENDING_ECHO

同时执行：

```text
STORY_INFORMATION_SUFFICIENCY
FINAL_BEAT_TRACE_REVIEW
FINAL_STORY_INTEGRITY_AUDIT
INDEPENDENT_FINAL_REVIEW_MODE
```

硬门槛至少包含：

```text
OBJECT_STATE_CONTINUITY
CAUSAL_VARIABLE_INTEGRITY
CLAIM_GROUNDING
CHILD_IMITATION_SAFETY
EDUCATION_DIRECTION
HARD_GATE_STATUS
```

任何硬 FAIL 不能被“8 Beat 齐全”“语言流畅”或“符合 Canon”覆盖。

Story Master 正文目标是**最低充分细节**：只补“不写就会迫使下游猜”的信息。90–120 秒目标、8 Beat、2–3 位主要角色的中文正文可参考约 1200–2200 汉字，但不是长度 Gate。

PASS 后若未要求暂停，进入 Stage 4。

---

# Stage 4｜Story Consistency Check

输入：最终 Story Master、Stage 0–2、必要事实 Source；CANON_AWARE 时加项目设定。

输出：`04_story_consistency_check.md`。

逐项检查：

- 用户需求与禁止项；
- 角色动力与关系；
- Story Spine / 8 Beat 因果；
- 场景与世界连续性；
- 关键物体状态；
- 事实 Claim；
- 儿童模仿安全；
- 年龄适配；
- 教育边界；
- Story Master 媒介边界；
- 项目 Canon（仅 CANON_AWARE）。

结果：

```text
PASS
RETURN_TO_STORY_MASTER
RETURN_TO_STORY_ENGINE
PROJECT_CONSTRAINT_REVIEW
SOURCE_RECHECK_REQUIRED
```

局部故事问题进入 AUTO_REPAIR_LOOP；需要改长期角色 / 世界 / 事实基线时 BLOCKED，请人工判断。

PASS 后进入 Stage 5。

---

# Stage 5｜Adaptation Handoff

输入：当前有效 Story Master 与 Consistency Check。

输出：`05_adaptation_handoff.md`。

只交接：

- 必须保留的事件 / 因果 / 角色锚点；
- 核心儿童体验；
- `TRANSFERABLE_CAPABILITY` 与必须保留的行为证据；
- 可压缩信息；
- 项目设定约束（若有）；
- 已成立的儿童参与闭环；
- 尚待人工选择的媒介创意项；
- 下游时长参数。

默认：

```text
TARGET_ANIMATION_DURATION = 90–120 seconds
MAIN_BEAT_COUNT = 8
BEAT_EXPANSION_MODE = COMPACT
```

明确要求 5–7 分钟：

```text
TARGET_ANIMATION_DURATION = 5–7 minutes
MAIN_BEAT_COUNT = 8
BEAT_EXPANSION_MODE = EXPANDED_WITHIN_BEAT
```

本阶段**不得**生成绘本分页、镜头、Storyboard、视频提示词或视觉资产。

PASS 后进入 Stage 6。

---

# Stage 6｜Human Review Delivery

Stage 6 是 DELIVERY RENDER，不重新创作故事。

优先生成 DOCX；环境不支持时生成 Markdown。

人工审阅版结构：

1. 故事标题、编号、版本、适龄；
2. 100–200 字故事简介；
3. 本集发展意图（成人审阅，不进入儿童正文）；
4. 主要角色及本集作用；
5. 完整连续故事；
6. 审阅提示：核心儿童体验、必须保留行为证据、刻意不承担的内容、任何 HUMAN_REVIEW_NOTE。

不得展示 YAML、Runtime 字段、Gate 日志或内部测试名称。

Story Master 仍是正式内容母版；人工修改应先回写 Story Master，再重跑受影响的 Stage 4–6。

通过：

```text
STATUS = PASS
PIPELINE_MODE = COMPLETE
DELIVERY_READY = YES
NEXT_STAGE = NOT_RUN
```

---

# AUTO_REPAIR_LOOP

适用于当前故事内部可修复问题：

- 角色过多 / 可替代；
- 人物行动与既有设定不一致；
- 因果链断裂；
- 第一次尝试、线索与解决方式不连贯；
- Story Master 漂移成知识课；
- 辅助角色变成答案机器；
- 为凑 8 Beat 强加冲突；
- 物体状态矛盾；
- 比较变量偷换；
- 无依据事实升级；
- 可修复的儿童模仿安全问题；
- Story Master 与 Brief 偏差；
- Adaptation Handoff 与 Story Master 不一致。

处理：

```text
FAIL DETECTED
→ 找到最早出错 Stage
→ 修复该 Artifact
→ 保存 Regression
→ 声明唯一 Current Effective Artifact
→ 重跑受影响后续 Stage
→ PASS 后继续
```

同一 Stage 最多 3 次。超过后：

```text
STATUS = BLOCKED
AUTO_REPAIR_STATUS = EXHAUSTED
HUMAN_DECISION_REQUIRED = YES
```

Regression 解析严格遵守 `current_effective_artifact.md`，不得按文件时间或后缀猜“最新版”。

# 必须停止并请求人工判断

以下禁止自动修复：

- 必须改变用户明确主题、价值方向或禁止项；
- 必须修改已有 IP / 角色的长期设定、永久能力或关系；
- 必须修改既有世界 / 地点长期规则；
- 项目 Source of Truth 互相冲突；
- 核心科学 / 健康 / 历史 / 文化 Claim 缺乏可靠来源且无法安全缩小；
- 当前 8 Beat / Engine 合同确实无法承载用户要求的“完整故事”；
- 任务其实是广告、预告片、知识卡等非完整故事，却被误套完整故事 Pipeline；
- 自动修复次数耗尽。

输出阻塞原因与所需人类决策，不通过偷偷改设定让故事“通过”。

# 自然语言使用示例

直接创作：

> “写一个 4–5 岁儿童故事：一只急性子的小兔第一次学着等一颗种子发芽，做成 90 秒左右动画故事。”

系统自动完成 Stage 0–6。

已有 IP：

> “用我提供的角色圣经，写一集两个角色因为整理方式不同而需要合作的故事。不要新增永久能力。”

自动进入 `CANON_AWARE`。

暂停：

> “完整 Story Master 写完先给我看，后面的审核先不做。”

Stage 3 PASS 后停止。

# v2.0 静态验收

必须确认：

1. 不出现任何特定 IP、角色、地名、品牌、点心或食育项目依赖；
2. Stage 0–6 保留；
3. 8 Beat 保留；
4. Character Causality / Remove / Swap / Consequence Test 保留；
5. Story Spine / Causal Chain 保留；
6. 三轮写作与十一项 Story Quality 保留；
7. Final Beat Trace、Story Information Sufficiency、Final Story Integrity、Independent Final Review 保留；
8. Child Participation Loop 保留但不机械配额；
9. Education Intent Contract 保留且不说教；
10. 可核验知识改用通用 Fact Grounding，不绑定食育；
11. Canon 改为可选的 Project Constraint；
12. Story Consistency Check 可在无 Canon 情况独立运行；
13. 90–120 秒默认动画目标与 5–7 分钟扩展规则保留；
14. Adaptation Handoff 仍不生成分镜 / 分页 / 提示词；
15. AUTO_REPAIR_ATTEMPTS = 3 与 Current Effective Artifact 机制保留；
16. Stage 6 只是 Human Review Render，不成为新的 Source of Truth。

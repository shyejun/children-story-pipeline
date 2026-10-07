---
title: "Story Master 三轮写作与质量重写"
version: "v1.5"
status: "ACTIVE"
scope: "STAGE_3_WRITING_AND_REVIEW"
---

# Story Master 三轮写作与质量重写

`FIRST_COMPLETE_DRAFT ≠ FINAL_STORY_MASTER`。Stage 3 内部先完成三轮真实写作，再做 Story Quality Review；首次完整故事不得直接写成最终 `03_story_master.md`、进入 Story Consistency Check、生成 DOCX 或交付。Story Master 的直接读者是成人创作者与下游 Adaptation，不是儿童；儿童适龄继续约束故事认知、角色行为、冲突与角色对白。内部草稿可留在工作过程；确需文件审计时仅保存为当前单集的 working artifact 或既有 Regression，不堆入正式 Story Master，也不覆盖历史 Artifact。

## 1. 三轮写作

1. `PASS 1 = EVENT DRAFT`：写清谁、在哪里、此刻想做什么、采取什么行动、现场怎样改变、为什么继续、最后怎样。先保证事件连续、因果完整和动作可见，不追求漂亮语言。
2. `PASS 2 = NARRATIVE ENRICHMENT / STORY REWRITE`：在锁定的 Story Spine 和八主 Beat 内，补足故事完整性、最低充分动作过程、可见结果、角色反应、关系影响、感官锚点、情绪连续、环境与物体变化、转场和可改编细节；并把互动机会写成正文中的 `INVITATION → CHILD_ACTION → STORY_ACKNOWLEDGEMENT → CAUSAL_CONTINUATION`。内部回答 `WHAT_CHANGES / WHY_KEEP_WATCHING / DO_CHARACTERS_AFFECT_EACH_OTHER`，并为每项指出正文证据。同时执行 `CHARACTER_CAUSALITY_PRESERVED`：核对 Stage 1–2 锁定的 `DEFAULT_ACTION / UNIQUE_CONSEQUENCE / PARTNER_RESPONSE_TRIGGERED / FINAL_METHOD_ADJUSTMENT / RELATIONSHIP_CAUSAL_LOOP` 是否仍在最终故事中通过事件成立。不得增加新 冻结设定、新解决方案、意外事故或不必要角色，也不得改变已通过的 Spine。
3. `PASS 3 = LANGUAGE & DIALOGUE POLISH`：局部修正病句、搭配、语义重复、失控长句、报告语言、说教式或无用解释、僵硬或成人化对白、代词、时间顺序、动作主语与称呼。叙事文字以成人创作者清楚、自然、完整阅读为准；角色对白以 3–6 岁儿童能理解为准。不得把整篇母稿改写成幼儿朗读稿，不得为了短句或朗读时长删除剧情事实与适配信息。

随后执行 `STORY QUALITY REVIEW`。完整 Story Master 最终只保留已重写且通过检查的故事正文及既有模板要求的正式内容。

## 2. Story Information Sufficiency

Story Quality Review 前先检查：

```text
STORY_INFORMATION_SUFFICIENCY = PASS | FAIL
CHILD_PARTICIPATION_EXECUTION = PASS | FAIL
```

陌生的编剧、绘本作者、动画导演或下游 AI 只读取 Story Master、项目设定与 Adaptation Handoff 后，应能理解完整故事并开始改编，不需要补写角色动机、动作过程、事件衔接、物体状态、角色改变决定的依据、教育发现的事件来源或结尾成立原因。结构化附录不得代替正文。

FAIL 时返回 Pass 2 补充 `MINIMUM_SUFFICIENT_DETAIL`，不能只在表格或 Story Lock 中补注。普通 90–120 秒目标、8 Beat、2–3 位主要角色的正文可参考约 1200–2200 个汉字，但不得按字数判定 PASS，不得注水。

`CHILD_PARTICIPATION_EXECUTION` 检查实际正文，而不是字段是否存在。对 4–5 岁故事，默认至少建立 2 个、最多 4 个自然闭环；每个闭环都必须让儿童做得到，并由角色或叙事现场接住，再进入新的动作、反馈或理解。问句标题、纯心理预测机会、接口清单和“下游可停顿”说明均不能单独判 PASS。

Story Vitality 的本轮结果只允许：

- `ALREADY_PRESENT`：三问已有足够正文证据，保护现有作用。
- `NEEDS_REWRITE`：存在可由本轮局部重写解决的观看动力、状态变化或角色互相影响缺口。
- `HUMAN_REVIEW_NOTE`：故事可通过现有 Gate，但仍有平、工具化或观看动力偏弱的具体观察；不得自动判 FAIL，必须传入 Human Review。
- `NOT_APPLICABLE`：对应机制对本故事确实不适用，并说明理由。

不得为了把结果改成 `ALREADY_PRESENT` 而强行新增角色、固定扰动角色、事故、危险、冲突、笑点、工具、Canon 或教育目标。

## 3. Story Quality Review

以下各项只记 `PASS` 或 `FAIL`，不打分、不排名、不生成综合分数。检查基于实际正文，而非字段已填写就自动通过。

| 检查项 | PASS 条件 |
|---|---|
| `STORY_CLARITY` | 陌生读者能说清谁想做什么、遇到或发现什么、最后发生什么 |
| `MOTIVATION_LOGIC` | 主要角色此刻行动的理由可从前文理解 |
| `CAUSE_EFFECT` | 主要事件由前一行动、反馈或发现引出 |
| `ATTEMPT_LOGIC` | 问题解决型的首次尝试产生后续必需的新条件或信息；低冲突型检查首次观察的推进作用，不强制失败 |
| `CHARACTER_AGENCY` | 最后关键变化主要来自角色自己的发现、选择与行动；证据指出该行动如何影响现场、伙伴或下一步，并与 `FINAL_METHOD_ADJUSTMENT` 一致 |
| `CHARACTER_VOICE` | 对白和动作体现各自 Character Canon，不全员同声；证据必须指出角色方法如何制造 `UNIQUE_CONSEQUENCE`、触发伙伴回应或改变解决路径，不能只靠口头禅 / 语气证明人物成立 |
| `SCENE_PURPOSE` | 每个主要段落至少承担建立、推进、改变、发现、回应或解决中的一项，并说明场景改变了什么、为何值得继续看；低冲突型不强制解决 |
| `DIALOGUE_FUNCTION` | 每句保留的对白承担即时叙事或关系功能 |
| `LANGUAGE_FLUENCY` | 无明显病句、搭配错误、句法问题、指代混乱、逻辑或时间错位、无用重复 |
| `READ_ALOUD_QUALITY` | 角色对白与句段节奏自然，明显拗口处已改写；不要求全文成为可直接交付儿童的朗读稿，也不以目标时长删减信息 |
| `ENDING_ECHO` | 结尾回应开头问题、角色愿望或核心儿童体验；低冲突型保留温和开放回声 |

八个 Beat 齐全但只是流水账、结尾完整却没有角色选择、首次行动对后续无作用、对白正确却没有人物感、语法无错却像说明文、知识准确却不像故事，均不得判为 Story Quality PASS。Story Quality 与 Stage 4 Story Consistency Check 分开执行；设定一致不能代替故事质量通过。

十一项全部复查后，先组装正式 `03_story_master.md`，再按 `child_story_8beat.md` 对该最终文件执行 `FINAL_BEAT_TRACE_REVIEW`。此追踪属于既有 Story Master Gate，不是第十二项质量指标。追踪 FAIL 时按最早问题来源返回 Stage 2 或 Stage 3；不得直接进入 Story Consistency Check。

## 4. Final Story Integrity & Independent Review

Story Quality、Story Information Sufficiency 与 Final Beat Trace 都通过后，**仍不能直接视为最终可放行**。先对装配完成的连续正文执行 `final_story_integrity_audit.md`。重点不是“还有没有第八个 Beat”，而是检查最终文字事实是否自洽。

顺序：

```text
FINAL STORY TEXT
→ OBJECT STATE LEDGER
→ CAUSAL VARIABLE CHECK（适用时）
→ CLAIM GROUNDING
→ CHILD IMITATION SAFETY
→ EDUCATION DIRECTION（适用时）
→ HARD_GATE_STATUS
→ INDEPENDENT_FINAL_REVIEW_MODE
```

若硬 Gate FAIL，先修事实，再重新做受影响的 Story Quality / Information Sufficiency / Beat Trace；不得只改验证记录。

独立复核时只把 Final Story Text 当作正文事实来源；Story Lock、场景表、Quality Review、Beat Trace 等只能用于定位，不能补救正文矛盾。若正文与附录冲突，以“正文存在缺口 / 矛盾”处理，而不是让附录替正文解释。

`STORY_QUALITY_JUDGMENT` 采用 `STRONG / ADEQUATE / NEEDS_REWRITE / HUMAN_REVIEW`。它是专业质量判断，不是 Hard Gate、不打分，也不代表儿童已经验证。

## 5. 局部重写与正式 Regression

任一项 FAIL，先找最早问题来源，按 `Story Spine → Causality → Character Motivation → Beat Function → Scene Purpose → Dialogue → Prose → Grammar / Fluency` 的顺序定位，再只重写受影响部分并复查。结构错不能只润色语言；剧情正确、仅有病句时只改文句。Stage 3 内部重写不建立第二套 Repair System；同一 Stage 持续不能 PASS 时遵守既有 `AUTO_REPAIR_ATTEMPTS = 3` 停止边界。

若问题源于 Stage 1 的角色职责 / Character Causality Map，先回 Stage 1；若人物选择正确但问题源于 Stage 2 的 WANT、因果、首次行动、伙伴回应或解决来源，依现有 `AUTO_REPAIR_LOOP` 返回 Stage 2，保存新的 Regression、重验受影响 Stage，再继续 Stage 3。跨 Stage 文件命名、旧 FAIL 与 Regression 保留规则不变。

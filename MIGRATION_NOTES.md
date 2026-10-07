# Migration Notes｜GenericChildrenStory → Generic Children Story Pipeline

## 保留

- Stage 0–6 主链
- 8 Beat 完整故事结构
- Character Causality Map
- Story Spine / Causal Chain
- 三轮 Story Master 写作
- Story Quality Review
- Visual Narrative Continuity
- Story Vitality
- Child Participation Loop
- Education Intent Contract
- Final Story Integrity Audit
- Independent Final Review
- AUTO_REPAIR / Regression / Current Effective Artifact
- 90–120 秒与 5–7 分钟下游适配规则

## 去除 / 泛化

- 删除全部《》角色、地点、固定扰动角色与品牌专属约束。
- 删除食育 / 点心专属 `food_culture_story_rules.md` 与 `food_education_truth_contract.md`。
- 用 `fact_grounding_contract.md` 替代为科学、健康、自然、历史、文化等通用事实真实性合同。
- `Canon Check` 改为 `Story Consistency Check`；Canon 从必选上游降为可选 `CANON_AWARE` 模式。
- 新增 `story_engine_profiles.md`，把核心发动机放入 Skill 自身，不依赖外部 Runtime Module。
- 新增 0–5 阶段模板，使技能包本身可独立使用。

## 未扩张

本次没有增加 Agent、Hook、评分系统、自动发布或复杂 Router；目标只是完成“去 IP 化 + 自包含化”。

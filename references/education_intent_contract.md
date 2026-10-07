---
title: "Education Intent Contract"
version: "v1.0"
status: "ACTIVE"
scope: "GENERIC_CHILDREN_STORY_MASTER_AND_ADAPTATION"
---

# Education Intent Contract

## 1. 定位

`Education Intent Contract` 是面向成人创作者、教师审阅者与下游媒介 Adapter 的**创作语义锚点**。

它不是：

- 儿童故事正文；
- 角色需要说出的道理；
- 新的 Story Quality Gate；
- 评分表；
- 要求每个故事必须承担教育任务的机制。

最高原则：

> **先有真实故事经验，再解释它可能支持什么发展；不得先写宏大教育目标，再逼故事去证明。**

---

## 2. 标准字段

正式 Story Master 在 `Story Lock Summary` 之后建立：

```text
EDUCATION_INTENT_CONTRACT

CHILD_EXPERIENCE =
TRANSFERABLE_CAPABILITY =
ADULT_EDUCATION_INTENT =
REAL_GAP =
DO_NOT_TEACH_DIRECTLY =
MUST_PRESERVE_BEHAVIORAL_EVIDENCE =
```

### CHILD_EXPERIENCE

回答：

> 孩子在这个故事里真正经历、观察、尝试或选择的那一件事是什么？

要求：

- 与 Story Brief 的核心儿童经验一致；
- 用儿童能经历的行为或变化表达；
- 不写“学会责任感”“建立健康意识”等成人抽象词。

### TRANSFERABLE_CAPABILITY

回答：

> 这个故事里的行为模式，有什么可以迁移到故事情境之外？

可包括：

- 暂停；
- 观察；
- 比较；
- 等待；
- 预测；
- 表达真实感受；
- 协商；
- 重新选择；
- 与伙伴同步；
- 根据反馈调整方法。

要求：

- 必须由最终正文中的行为链支持；
- 不把一次行为直接写成“已经形成能力”；
- 没有真实迁移证据时使用 `NOT_APPLICABLE`。

### ADULT_EDUCATION_INTENT

回答：

> 成人创作者真正希望这次故事经验支持哪个发展方向？

要求：

- 只供成人理解；
- 不直接进入儿童对白、旁白、标题口号或结尾总结；
- 不得超过故事能承载的层级；
- 纯游戏、审美、幽默或关系体验为主时可以 `NOT_APPLICABLE`。

### REAL_GAP

回答：

> 这一集能提供什么体验，但**不能证明什么结果**？

典型表达：

- 能提供一次“停一下再决定”的体验，但不能证明儿童已经形成自我调节能力；
- 能帮助儿童经历一次比较与重新选择，但不能单集证明已经形成稳定习惯；
- 能让儿童看见伙伴协商，但不能证明儿童已能在真实冲突中稳定迁移。

`REAL_GAP` 不得省略。它用于阻止成人创作者、营销文案和下游媒介夸大故事效果。

### DO_NOT_TEACH_DIRECTLY

列出 1–3 个不得直接儿童化的成人概念或危险简化。

例如：

- 不让角色说“我要学会自我调节”；
- 不把某一种选择写成“好孩子”的唯一标准；
- 不把一次选择写成“从此养成健康习惯”；
- 不用“这个故事告诉我们……”总结。

### MUST_PRESERVE_BEHAVIORAL_EVIDENCE

列出 1–3 条教育意义真正依赖的**行为证据链**。

例如：

```text
继续加
→ 停一下
→ 重新看 / 闻
→ 发现变化
→ 自己改变决定
```

或：

```text
伙伴的方法造成新条件
→ 主角注意到反馈
→ 两人调整各自方法
→ 形成新的共同解决方式
```

这些行为证据必须已经存在于 Story Master 正文。Adapter 只能改变媒介实现，不能补造。

---

## 3. 与事实真实性合同的关系

当故事涉及科学、自然、健康、历史、文化、社会规则等可核验内容时，继续以 `fact_grounding_contract.md` 负责**事实边界与来源**。

`Education Intent Contract` 不替代事实核查，而负责回答：

> 已确认的事实，如何通过儿童可经历的事件与行动进入故事？

因此：

```text
Fact Grounding Contract = 事实边界
Education Intent Contract = 发展与迁移语义边界
```

两者不得互相覆盖。事实来源不足时，应缩小 Claim、改写成角色感受 / 故事观察，或进入人工核查；不得为了教育意图补造知识。

---

## 4. 与角色因果的关系

教育意图不得覆盖角色因果。

错误：

```text
因为本集想教“停一下”，
所以任何角色都突然学会停。
```

正确：

```text
角色自己的性格与行动
→ 产生后果
→ 故事里自然出现一次“停”的需要
→ 角色按自己的方法调整
→ 成人从中识别出可迁移的“暂停—观察—再选择”能力
```

顺序必须是：

```text
CHARACTER CAUSALITY
→ STORY EVENT
→ CHILD EXPERIENCE
→ TRANSFERABLE CAPABILITY
→ ADULT INTENT
```

不能反过来。

---

## 5. Story Master 呈现位置

顺序：

```text
Story Lock Summary
↓
Education Intent Contract
↓
Character Dynamics
↓
完整故事正文
```

合同应简短，通常每个字段 1–3 句；不能比 Story Lock 更长，更不能替代故事正文。

---

## 6. Adaptation Handoff 使用规则

绘本 / 动画优先读取：

```text
CHILD_EXPERIENCE
TRANSFERABLE_CAPABILITY
MUST_PRESERVE_BEHAVIORAL_EVIDENCE
```

`ADULT_EDUCATION_INTENT` 只作成人背景约束。

`REAL_GAP` 只用于防止夸大结果。

禁止：

- 把成人意图写成角色总结；
- 用字幕、旁白、教师台词把隐含教育直接讲出来；
- 为了让教育“更明显”增加 Story Master 不存在的事件；
- 删除所有关键行为证据后，只保留一句“正确结论”。

### 对绘本

`MUST_PRESERVE_BEHAVIORAL_EVIDENCE` 用于决定：

- 哪些 Page / Spread 不能被压缩掉；
- 哪些动作必须可见；
- 哪些注意力变化要由画面承担；
- 哪些 Page Turn 应保护“预测 → 反馈 → 重新选择”。

### 对动画

它用于决定：

- 哪个动作节奏不可删；
- 哪个停顿是故事事实而非剪辑装饰；
- 哪个声音 / 注意力转移是发现的前提；
- 哪个选择必须由角色自己完成。

---

## 7. Human Review DOCX

DOCX 不显示 Runtime 字段名。

建议自然语言呈现：

**本集发展意图（供成人审阅，不进入儿童正文）**

- **孩子经历什么：** ……
- **希望支持的能力：** ……
- **成人理解：** ……
- **本故事的边界：** ……
- **本集不直接教：** ……

其中“能力”必须使用“支持、提供体验、练习机会”等表述，避免写成“已经培养、已经形成、已经掌握”。

---

## 8. 轻量自检

不新增 Gate，只做对齐检查：

```text
[ ] CHILD_EXPERIENCE 能在最终正文中找到事件证据
[ ] TRANSFERABLE_CAPABILITY 没有超过一次故事体验能支持的范围
[ ] ADULT_EDUCATION_INTENT 没有进入儿童正文
[ ] REAL_GAP 明确且没有夸大教育效果
[ ] DO_NOT_TEACH_DIRECTLY 没有被正文违反
[ ] MUST_PRESERVE_BEHAVIORAL_EVIDENCE 能逐项定位正文
```

若不满足，优先缩小合同表述；只有当合同暴露出 Story Master 与 Story Brief 的真实冲突时，才按现有 Regression / AUTO_REPAIR 机制返回最早必要 Stage。

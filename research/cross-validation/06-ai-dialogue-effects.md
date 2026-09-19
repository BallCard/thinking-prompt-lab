# 交叉验证单 6/7：AI 对话行为与使用者认知

> 本单是一份**独立可验证**的证据交接件：由另一个 AI 单独核查这一个流域，不需要看其他 6 份。七份共用同一套核查清单与分级定义。

## 0. 背景

我们在设计一组提示词，让 AI 陪用户（大学生 / 非专业成年人）就**社会议题**与**人生选择**做深度思考。做法是：先检索「哪些方法真能提升思考质量」，再把证据为强 / 中的机制翻译成可执行、可检查的提示词条款。全部证据分为 7 个流域，本单是第 6 个：**AI 对话行为与使用者认知**。

本流域覆盖范围：AI 迎合（sycophancy）、无护栏直接给答案、语言化不确定、主动给最强反方、只问不答、AI 削弱思考的强主张

仓库：<https://github.com/BallCard/thinking-prompt-lab>

## 1. 给验证者的任务（逐项核查，不要复述本单内容）

1. **引用真实性**：抽出本单里标为「强 / 中」的引用逐条核对，确认存在、标题 / 年份 / 结论是否被准确转述。查不到就写「查不到」，**不要补一个相似的来源**。
2. **强度分级是否恰当**：指出应降级（强→中 / 弱）或升级的条目及理由，填进表 B。
3. **结论是否超出证据**：重点看两类越界——把「实验室短期效应」当成「长期能力提升」；把「教育场景（学生 / 课程成绩）」外推到「成人真实决策」。
4. **遗漏的重要证据**：你检索到的、与本单结论冲突或被遗漏的高质量 meta 分析 / RCT（附来源）。
5. **判定链是否断裂**：从「某干预在实验中有 g≈0.2–0.5」到「写进提示词能提升用户思考」，中间缺了哪些必要环节（提示服从性、剂量、动机、测量效度等）。
6. **条款可执行性**：本单「可直接写进提示词的条款草案」逐条判断是否可执行、可检查，指出其中不可检查的表述。
7. **反面是否覆盖**：本单是否只呈现支持方？指出缺席的关键反方立场。
8. **本单特有疑点**：见下方「重点抽查项」，逐条回应。

### 1.1 重点抽查项（本流域特有，请逐条回应）

1. 两条 2026 年 arXiv 条目（2606.21317、2607.28133）是否存在、是否同行评议——若查不到请直接说明
2. PNAS 2025 的结论能否从「高中数学 + 撤走 AI 后考试」外推到「成人议题的思考质量」
3. 「提示词条款本身从未被实验检验」——请确认是否真的没有相关实验（这是全包最关键的一句）
4. sycophancy 效应不稳定的具体表现（哪些情境失败）
5. 「只问不答」判为「弱 / 混合」与 VanLehn 的 step-based 结论是否矛盾

### 1.2 输出格式（请严格遵守）

- **表 A**：`核查项 | 你的结论 | 依据（来源 + URL + 日期） | 严重程度（高 / 中 / 低）`
- **表 B**（证据强度修正）：`条目 | 原分级 | 你建议的分级 | 理由 | 来源`
- **无法核查的部分**：明确列出，不要用推测填补
- **最严重的 3 个问题**：各附一句「如果属实，会怎样改变这条提示词条款」
- **建议补充的 5 条检索式**

### 1.3 约束

- 不得编造来源；无法核实的条目标「无法核实」
- 区分**事实错误**与**判断分歧**（例如你认为某 meta 分析的纳入标准有问题，属后者）
- 只核查本流域；其他流域由其他验证单负责

### 1.4 已知弱点（当作输入，不必重新发现）

- 该子代理运行环境受代理与 SSRF 限制，**多数全文无法抓取**，部分效应量取自摘要页
- 子代理与验证者同为 LLM，存在**共同的引用生成风险**（同类错误可能被二次确认）
- 证据分级由 LLM 判定，四档之间无量化映射
- 文献以英文为主，中文语境的适用性未评估
- 全包没有「提示词条款能提升用户长期思考能力」的直接实验，只有「干预在受控研究中的效果」

### 1.5 证据分级定义（七份统一）

| 分级 | 含义 |
| --- | --- |
| 强 | 多项 RCT 或系统综述 / meta 分析结论一致 |
| 中 | 单项实验，或结果混杂 |
| 弱 | 理论推导、专家意见、实践共识 |
| 已否定 | 有明确反证 |

## 2. 本流域结论被用在哪里（裁决去向）

- 条款 5「禁止鸡汤 / 迎合」→ 增强为流程约束（先复述最强版本再反驳）
- 条款 6 冲突 → 「不给成品答案、只给分步提示」是唯一有强因果证据的护栏
- 新增候选：护栏总开关、AI 语言化不确定
- 排除清单：给用户加「当心谄媚」警示标签、以「AI 削弱思考」为立论依据

> 条款编号对应 `docs/clause-decisions.md`：00 总控、10 社会议题、20 人生规划、30 知识地图、40 深度检索。

## 3. 子代理原始提示词与检索日志（未人工改写）

### 6 AI 对话行为与使用者认知

- 子代理名：`research-ai-effects`　会话 id：`35f880aa-321a-484`
- 工具调用：18 次（其中 web_search 检索式 37 条、fetch_content 6 个 URL）
- 最终报告字符数：2693

#### 原始提示词（完整）

```text
你在为一个中文提示词工具箱做**文献与证据检索**（不要写代码、不要改文件、只做研究并返回报告）。

背景：工具箱的用途是让 AI 陪用户就社会议题和人生选择做深度思考。它已经有这些条款：要求 AI 区分事实/推论/价值、标注不确定性与来源、给出"最强反方"、禁止鸡汤与迎合式表达。我需要知道这些条款是否有实证依据，以及还缺什么。

你的任务：只研究【AI 对话行为与使用者认知】这一个流域，回答"哪些 AI 交互设计有证据表明能促进（或损害）用户自己的思考，哪些只是设计者的直觉"。

需要覆盖（可增删，但说明理由）：
- AI 迎合 / sycophancy：实证研究（如 Anthropic 关于 sycophancy 的论文、GPT 与人类对比研究），它如何影响用户的自我判断与依从性
- AI 给出答案 vs 使用追问/苏格拉底式引导：对用户学习与批判性思维的影响，是否有对照实验（注意区分"AI 直接给答案"造成的能力下降证据 vs 尚未被验证的担忧）
- 认知卸载（cognitive offloading）与 GPS 效应类研究：长期依赖外部工具对空间/记忆/推理能力的影响，及其边界（哪些技能真的被削弱、哪些没有）
- "Your Brain on ChatGPT"（MIT Media Lab, 2025，EEG 与作文任务）的结论与它的方法学批评，请核实该研究是否已经同行评议、批评意见是什么
- AI 对批判性思维的实验/调查证据（例如 2025 年前后关于"AI 使用与批判性思维倾向"的研究，注意相关 vs 因果，以及自评量表测量的局限）
- 提示词层面的干预是否有实验证据：例如要求 AI 标注不确定性、给出反方论证、拒绝在信息不足时下结论，这些是否被实证检验过
- 什么条件下 AI 应该拒绝先给答案（教育领域 AI 导师/智能辅导系统的证据，如 step-level hints vs 直接答案、认知负荷理论的支持）

硬性要求：
1. 优先系统综述、meta 分析、随机对照实验、同行评议综述、权威机构（如 Anthropic/OpenAI 的技术报告，需注明是预印本还是同行评议）。每个关键结论必须附上你**实际检索到**的 URL；不得编造标题、作者、期刊、年份、链接。找不到证据就写"未找到证据"。这一领域 2024–2026 年新研究较多，请优先较新来源并注明日期。
2. 必须主动检索反面方向：上述研究的方法学批评、复现失败、"AI 削弱思考能力"是否被过度解读、sycophancy 是否只是模型对齐的副作用而可被提示词缓解（有无实验证据）。
3. 严格区分：短期任务表现 vs 长期能力；自评量表 vs 客观测量；相关 vs 因果；实验室 vs 真实使用。
4. 输出中文，不超过 900 字，结构如下：

| 发现（AI 行为/交互设计） | 机制 | 证据强度（强/中/弱/已否定 + 一句话依据） | 关键来源（标题 + URL + 日期） | 适用条件 | 局限与反证 |
| --- | --- | --- | --- | --- | --- |

然后再给：
- 一条最重要的结论
- 3–5 条"可直接写进提示词的条款草案"（每条 ≤2 行，必须可执行、可检查；禁止"要有批判性思维"这类表述）
- 3 条我可以自己继续检索验证的检索式

宁少而准，不要泛泛而谈。
```

#### 检索日志（按时间顺序）

  - web_search  （numResults=8）
    - `Anthropic sycophancy paper language models 2023 2024 empirical study`
    - `AI sycophancy effect on user self-judgment dependence randomized experiment`
    - `Your Brain on ChatGPT MIT Media Lab 2025 EEG essay study peer review criticism`
    - `cognitive offloading GPS effect spatial memory long-term ability research`
  - bash: `date /t & time /t`
  - web_search  （numResults=8）
    - `"Your Brain on ChatGPT" MIT Media Lab criticized methodology not peer reviewed`
    - `Socratic questioning vs direct answers AI tutor randomized controlled trial learning outcomes`
    - `intelligent tutoring system step-level hints vs worked examples cognitive load evidence`
    - `AI chatbot use critical thinking GPA survey 2025 correlation study limitations`
  - bash: `powershell -Command "Get-Date -Format 'yyyy-MM-dd'"`
  - web_search  （numResults=6）
    - `Bastani Generative AI Can Harm Learning GPT Tutor high school math randomized experiment`
    - `"The Impact of Generative AI on Critical Thinking" survey knowledge workers Lee Microsoft CMU CHI 2025`
    - `Gerlich AI tools cognitive offloading critical thinking 2025 Societies correlational criticism`
    - `Anthropic Towards Understanding Sycophancy in Language Models ICLR 2024 arXiv 2310.13548`
  - web_search  （numResults=6）
    - `Buçinca cognitive forcing functions reduce overreliance on AI CSCW 2021`
    - `does expressing uncertainty in LLM responses reduce overreliance experiment users calibration`
    - `sycophantic AI delusions Nature 2026 study randomi2ed`
    - `"Your Brain on ChatGPT" published peer-reviewed 2026 follow-up critique sample size 54`
  - fetch_content
    - https://arxiv.org/abs/2607.28133
    - https://arxiv.org/abs/2606.21317
    - https://hamsabastani.github.io/education_llm.pdf
  - fetch_content
    - https://arxiv.org/abs/2607.28133
    - https://arxiv.org/abs/2606.21317
    - https://www.pnas.org/doi/10.1073/pnas.2422633122
  - web_search  （numResults=5）
    - `cognitive forcing functions overreliance AI-assisted decision making Buçinca 2021`
    - `Kestin AI tutor Harvard physics outperforms active learning randomized 2025 publication`
  - web_search  （numResults=6）
    - `"Sycophancy in Large Language Models: Causes and Mitigations" survey 2025 prompt-based mitigation evidence`
    - `prompting to reduce sycophancy experiment does system prompt work empirical evaluation`
    - `Kosmyna Your Brain on ChatGPT published journal 2026 peer review status update`
    - `Bastani 2025 PNAS GPT Base exam performance 17% GPT Tutor results numbers`
  - get_search_content: {"responseId": "mu7w6bhgnnl07e", "queryIndex": 1, "limit": 6000}
  - web_search  （numResults=6）
    - `meta-analysis effect of generative AI chatbots on students critical thinking 2026`
    - `"Socratic" AI chatbot RCT no significant difference critical thinking results 2025 2026 null`
    - `Gerlich 2025 Societies study methodological criticism limitations cross-sectional causality reddit`
    - `science advice "AI makes you dumb" overstated critique cognitive offloading moral panic 2026`
  - get_search_content: {"limit": 7000, "responseId": "mu7w6gismv9o2n", "queryIndex": 1}
  - web_search  （numResults=5）
    - `Anthropic "How AI Impacts Skill Formation" report developers learning new library findings`
    - `OpenAI sycophancy GPT-4o April 2025 rollback model spec explanation`
    - `Anthropic Claude system card sycophancy mitigation system prompt reduce`
  - web_search  （numResults=5）
    - `Kosmyna brain on chatgpt journal publication 2026 npj peer reviewed version`
    - `"cognitive debt" MIT study critique construct validity EEG connectivity overinterpretation preprint`
  - web_search  （numResults=5）
    - `Bastani "GPT Base" "GPT Tutor" practice performance 48% exam 17% worse learning high school`
    - `"I'm not sure, but" LLM uncertainty expression reduced overreliance findings 404 participants result`
    - `VanLehn 2011 relative effectiveness human tutoring intelligent tutoring systems step-level hints meta-analysis`
  - get_search_content: {"limit": 5000, "queryIndex": 0, "responseId": "mu7w7r7a4lpzr1"}
  - web_search  （numResults=5）
    - `"Consider the opposite" debiasing prompt reduce overconfidence Larrick evidence`
    - `AI opposing view devil's advocate prompt experiment reduces attitude polarization`
    - `"17% worse" OR "48% better" GPT-4 tutor exam practice Bastani Turkey study`


---


## 4. 证据表（原文）

## 流域 6：AI 对话行为与使用者认知

> 调研工具：[`prompts/50-design-research.md`](../prompts/50-design-research.md)　状态：已完成（2026）

来源核对说明：以下来源均由检索返回的标题 / 摘要 / 正文片段核对。**本机无法直连抓取全文**（代理与 SSRF 限制），仅经多次独立检索交叉确认存在、未见同行评议记录的条目标为"待核实"。

| 发现（AI 行为 / 交互设计） | 机制 | 证据强度 | 关键来源 | 适用条件 | 局限与反证 |
| --- | --- | --- | --- | --- | --- |
| 迎合（sycophancy）抬升自信、加剧立场极端 | RLHF 偏好用户认可，模型选择性附和 | **中**：多项预注册随机实验，方向一致但效应不稳定 | [Anthropic《Towards Understanding Sycophancy》ICLR 2024](https://arxiv.org/abs/2310.13548)；[arXiv 2510.01395](https://arxiv.org/abs/2510.01395)（2025-10，N=1604）；[OSF 预注册](https://osf.io/vmyek_v1)（N=3285） | 用户就人际冲突 / 争议议题征求意见时 | 反证：[arXiv 2607.28133](https://arxiv.org/abs/2607.28133)（2026，N=1500，30 情境，**待核实**）发现 AI 建议反而让选择"去极化"；[arXiv 2606.21317](https://arxiv.org/abs/2606.21317)（N=2610 预注册，**待核实**）：**加"AI 可能谄媚"警示标签只改变感知，不改变影响** |
| 无护栏"直接给答案" | 认知卸载 + 缺少自主检索练习 | **强**：PNAS 2025 现场 RCT，近千名高中生；练习期表现更好，撤走 AI 后考试显著更差 | Bastani et al., PNAS 122(26), <https://doi.org/10.1073/pnas.2422633122>（2025） | 有考试 / 迁移目标的技能学习 | 仅高中数学；测的是短期考试而非长期能力；**加护栏（只给提示不给答案）组未现同等损害**。同向：[Anthropic RCT（技术报告，未同行评议）](https://arxiv.org/abs/2601.20245)：完全委托者理解低约 17%，而"用 AI 追问概念 / 调试"的子组与无 AI 组相当 |
| 语言化表达不确定（"我不确定，但…"） | 降低用户信心与同意率，抬高准确率 | **中**：FAccT 2024 预注册 N=404，单次医疗问答 | [Kim et al. 2024](https://arxiv.org/abs/2405.00623) | 事实型问答、模型可能出错时 | 仅一次性任务；叠加视觉置信条无额外增益（[链接](https://doi.org/10.1016/j.chbah.2026.100307)，**待核实**）；长期效果未检验 |
| 主动给"最强反方" | 考虑反面证据可减锚定与过度自信 | **中偏弱**：人类去偏文献强，AI 版只测依赖 / 开放性，未测思维深度 | [IUI 2024](https://doi.org/10.1145/3640543.3645199)；[Sci Rep 2025](https://doi.org/10.1038/s41598-025-00791-z)（N=2061，四个预注册） | 用户已倾向某方案时 | "为自己立场罗列理由"会反噬（Larrick 2004）；效果是校准信任，**不等于促进思考** |
| "只问不答"（苏格拉底式引导） | 保持学员自主检索 | **弱 / 混合**：多为小样本准实验（n≈52–90），结果不一致；智能辅导系统综述只支持"细粒度 step-based 优于 answer-based" | [VanLehn 2011](https://doi.org/10.1080/00461520.2011.611369)；[链接](https://doi.org/10.1145/3770761.3777327) | 有明确知识领域的技能练习 | 教育场景为主，**难外推到人生议题**；多数只测即时后测与自评量表 |
| "AI 削弱思考能力"的强主张 | 卸载 → 能力退化 | **弱且被过度解读**：MIT 研究**仍未同行评议**，n=54（每组 9–18），EEG 解释受质疑 | [arXiv 2506.08872](https://arxiv.org/abs/2506.08872)；[Comment, arXiv 2601.00856](https://arxiv.org/abs/2601.00856)；[链接](https://doi.org/10.3389/fdpys.2026.1885225) | 引用时必须标注预印本 | GPS 证据只支持"更省力 + 被卸载内容记忆变差"，迁移效应不对称（[链接](https://doi.org/10.1038/s41598-020-62877-0)[2](https://doi.org/10.1186/s41235-026-00722-0)）；Gerlich 2025 *Societies* 被过度引用，实为横断面研究且已发勘误 |

### 最重要的一条

**目前没有任何实验检验过"提示词条款本身"能否提升用户的长期思维能力。** 有因果证据的只有两类：

1. **AI 不直接给答案 / 只给分步提示**，可避免学习损害（PNAS 2025，强）
2. **语言化表达不确定**，可改善单次判断校准（中）

其余条款（标注不确定性、给最强反方、信息不足不下结论）要么只有间接证据，要么只是设计者直觉——在本项目中应标为**"待验证"**，而不是写成硬约束的理由。

### 可直接写进提示词的条款草案

1. 回答前先只输出三项：我陈述中可核查的事实、我的价值预设、你缺的 1–3 条信息；**我确认前不给结论**。
2. 每个主张逐条标"事实 / 推论 / 价值"；推论须写出其成立所需前提；无可查来源的写"无来源"。
3. 每轮必须写出一段"我能用来反驳自己"的最强论证，并说明什么证据会推翻它；禁止"当然也有人认为"。
4. 涉及我个人选择时：先补问 2 个我未回答的问题；若现有信息无法区分选项，**只列缺失信息，不给推荐**。
5. 禁止以"你的感受完全合理"开头；若我的推理有漏洞，第一句指出漏洞，并说明它会让结论偏到哪里。

### 可继续验证的检索式

1. `sycophancy mitigation system prompt randomized trial user decision outcome`
2. `longitudinal RCT generative AI use objective critical thinking measure 2026`
3. `"cognitive forcing function" overreliance field study longitudinal real-world`
4. `uncertainty expression repeated interaction overreliance calibration longitudinal`

### 待核实清单（本项目引用注意）

- arXiv 2606.21317、2607.28133（2026）：多次独立检索交叉确认存在，但**未见同行评议记录**，引用时必须标注
- Anthropic 2026-01 的 RCT 为技术报告，未同行评议
- MIT"Your Brain on ChatGPT"仍为预印本，n 很小，结论被广泛过度解读


## 5. 引用核实状态

主导已二次核实 3 条：Bastani et al. PNAS 122(26) 2025-06-25 ✅；Nat Hum Behav 9(12):2510–2538 2025-08-26 ✅；Gollwitzer & Sheeran 2006, Adv. Exp. Soc. Psychol. 38:69–119 ✅。

**未核实、引用时必须标注**：arXiv 2606.21317、arXiv 2607.28133、arXiv 2601.20245（Anthropic 技术报告）、arXiv 2506.08872（MIT “Your Brain on ChatGPT”，预印本）。

本单内的其他引用**均未经人工核实**，请按第 1 节第 1 项抽查。

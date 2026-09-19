# 交叉验证单 5/7：知识组织、理解与迁移

> 本单是一份**独立可验证**的证据交接件：由另一个 AI 单独核查这一个流域，不需要看其他 6 份。七份共用同一套核查清单与分级定义。

## 0. 背景

我们在设计一组提示词，让 AI 陪用户（大学生 / 非专业成年人）就**社会议题**与**人生选择**做深度思考。做法是：先检索「哪些方法真能提升思考质量」，再把证据为强 / 中的机制翻译成可执行、可检查的提示词条款。全部证据分为 7 个流域，本单是第 5 个：**知识组织、理解与迁移**。

本流域覆盖范围：检索练习、间隔练习、自我解释、交叉练习、概念地图、对比案例、学习即教学（费曼技巧）、专家—新手差异、远迁移、跨学科整合、自然频数

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

1. 「远迁移弱—近否定」的表述是否过强：二阶层 meta 的纳入研究多为认知训练而非教学干预
2. 「跨学科整合少有证据优于学科课程」——「少于」不等于「无效果」，我们据此删除承诺是否过头
3. 概念地图 g=0.58 的自生成与呈现两种条件是否被混为一谈
4. 把「检索 + 间隔练习」（强）写进「知识地图」模块，是否属于跨情境外推（原证据是事实记忆，不是判断）

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

- 条款 10「知识地图」→ 删除「建立知识体系 / 跨学科思维」承诺，改为可判错案例 + 默写
- 新增候选：1 天 / 7 天无提示默写、自然频数（x/1000）
- 排除清单：概念地图＝建立知识体系、跨学科整合本身的效果承诺

> 条款编号对应 `docs/clause-decisions.md`：00 总控、10 社会议题、20 人生规划、30 知识地图、40 深度检索。

## 3. 子代理原始提示词与检索日志（未人工改写）

### 5 知识组织、理解与迁移

- 子代理名：`research-knowledge`　会话 id：`9bdb2205-e0ef-432`
- 工具调用：28 次（其中 web_search 检索式 41 条、fetch_content 5 个 URL）
- 最终报告字符数：3865

#### 原始提示词（完整）

```text
你在为一个中文提示词工具箱做**文献与证据检索**（不要写代码、不要改文件、只做研究并返回报告）。

背景：工具箱包含一个"知识地图"模块，用于把陌生领域压成"能用于判断的最小知识集"，以及一个"跨学科视角"需求（用户希望积累跨学科认知，但明确反对信息过载）。设计约束是输出可检查、可落地。

你的任务：只研究【知识组织、理解与迁移】这一个流域，回答"哪些做法有证据表明能让人真正理解和用上跨学科知识，哪些只是流行说法"。

需要覆盖（可增删，但说明理由）：
- 概念地图（concept maps）/ 知识图谱式整理对理解与保持的效果（有无 meta 分析、效应量）
- 专家与新手的知识组织差异（chunking、图式、深层结构 vs 表面特征），以及"按专家结构组织知识"能否加速学习
- 精加工（elaboration）、自我解释、检索练习（retrieval practice）、间隔学习：哪些效应量最大（注意 retrieval practice 与 spacing 是教育心理学里证据最强的）
- 迁移（transfer）：远迁移是否稀有（如"学习的迁移"相关综述结论），对"学了方法论能否用到新问题"有何含义
- 费曼技巧 / 向他人解释（learning by teaching, protégé effect）的证据强度
- 案例法（case-based reasoning）与对比案例（contrasting cases）在形成可迁移判断上的证据
- 跨学科整合（interdisciplinarity）本身的效果证据，以及"广而浅"的风险（注意：这一块证据较弱，请如实标注）
- 领域内"数量级直觉"（order-of-magnitude sense）对判断的作用，是否有相关研究（如统计素养、base rate 教学）

硬性要求：
1. 优先系统综述、meta 分析、随机对照实验、同行评议综述。每个关键结论必须附上你**实际检索到**的 URL；不得编造标题、作者、期刊、年份、链接。找不到证据就写"未找到证据"。
2. 必须主动检索反面方向：概念地图效果是否被夸大、费曼技巧是否缺少直接实验证据、远迁移是否几乎不发生、跨学科学习是否常常流于表面。
3. 严格区分：实验室学习任务 vs 真实判断能力；记忆保持 vs 判断质量；相关 vs 因果。
4. 输出中文，不超过 900 字，结构如下：

| 方法 | 机制（为什么可能有用） | 证据强度（强/中/弱/已否定 + 一句话依据） | 关键来源（标题 + URL） | 适用条件 | 局限与反证 |
| --- | --- | --- | --- | --- | --- |

然后再给：
- 一条最重要的结论
- 3–5 条"可直接写进提示词的条款草案"（每条 ≤2 行，必须可执行、可检查；禁止"要建立知识体系"这类表述）
- 3 条我可以自己继续检索验证的检索式

宁少而准，不要泛泛而谈。
```

#### 检索日志（按时间顺序）

  - web_search  （numResults=8）
    - `concept map meta-analysis effect size comprehension retention`
    - `concept mapping criticism weak evidence exaggerated effect`
    - `expert novice differences chunking schema deep structure surface features review`
  - web_search  （numResults=8）
    - `retrieval practice testing effect meta-analysis effect size g`
    - `spacing effect meta-analysis effect size evidence strength`
    - `self-explanation elaboration effect size meta-analysis learning`
  - web_search  （provider=brave, numResults=8, workflow=none）
    - `concept maps criticism weak evidence not better than active learning`
    - `expert novice differences chunking schema deep structure review`
    - `spacing effect distributed practice meta-analysis effect size 2021`
  - web_search  （provider=tavily, numResults=8, workflow=none）
    - `far transfer of learning rare review "transfer of learning" Perkins Salomon`
    - `learning by teaching protégé effect evidence experiment`
    - `contrasting cases analogical transfer learning evidence Gentner`
  - web_search  （provider=["jina", "duckduckgo", "searxng"], numResults=5, workflow=none）
    - `concept map meta-analysis effect size g Schroeder`
  - web_search  （provider=["firecrawl", "perplexity", "gemini"], numResults=5, workflow=none）
    - `far transfer of learning rare evidence review`
  - web_search  （provider=['jina', 'duckduckgo', 'searxng'], numResults=5, workflow=none）
    - `concept map meta-analysis effect size Schroeder 2017`
  - web_search  （provider=['firecrawl', 'perplexity', 'gemini'], numResults=5, workflow=none）
    - `far transfer of learning rare evidence review education`
  - web_search  （provider=auto, numResults=6, workflow=none）
    - `far transfer of learning rare evidence review education`
  - fetch_content
    - https://duckduckgo.com/html/?q=%22far+transfer%22+learning+rare+review
  - web_search  （provider=auto, numResults=6, workflow=none）
    - `concept mapping criticism graphical organizer no better than active control`
    - `spacing effect meta-analysis distributed practice effect size Cepeda`
    - `Dunlosky 2013 improving students learning effective learning techniques utility assessment`
  - web_search  （provider=auto, numResults=6, workflow=none）
    - `expert novice differences knowledge organization chunking schema review Chi`
    - `learning by teaching protégé effect meta-analysis evidence`
    - `contrasting cases perceptual learning analogy transfer evidence`
  - web_search  （provider=auto, numResults=6, workflow=none）
    - `contrasting cases compare and contrast learning transfer experiment evidence`
    - `case-based reasoning teaching evidence effectiveness review`
  - web_search  （provider=auto, numResults=6, workflow=none）
    - `interdisciplinary education outcomes evidence meta-analysis critical review`
    - `statistical literacy base rate Bayesian reasoning training meta-analysis`
  - web_search  （provider=auto, numResults=6, workflow=none）
    - `Feynman technique evidence research does it work`
    - `strategies for teaching students to think critically meta-analysis Abrami`
  - web_search  （provider=auto, numResults=6, workflow=none）
    - `Sala Gobet cognitive training near far transfer second-order meta-analysis`
    - `interleaved practice meta-analysis Brunmair Richter effect size`
  - web_search  （provider=auto, numResults=6, workflow=none）
    - `Barnett Ceci taxonomy of transfer far transfer rare Detterman criticism`
    - `worked examples expertise reversal effect meta-analysis expert structure instruction`
  - fetch_content
    - https://link.springer.com/article/10.1007/s10648-017-9403-9
    - https://gwern.net/doc/psychology/spaced-repetition/2018-bisra.pdf
    - https://www.lrdc.pitt.edu/schunn/research/papers/ContrastingCasesMeta-AlfieriEtAl2013.pdf
    - https://livrepository.liverpool.ac.uk/3043493/1/203-3078-1-PB.pdf
  - get_search_content: {"responseId": "mu7w6d2te4sw3f", "findText": ["effect size", "g =", "d =", "random-effects", "moderate"]}
  - get_search_content: {"responseId": "mu7w6w7m61xhvw", "findText": ["Hedges", "g =", "effect size", "0.35", "0.56"]}
  - get_search_content: {"responseId": "mu7w6d2te4sw3f", "queryIndex": 0, "findText": ["effect size", "g =", "moderate", "retention", "creating"]}
  - get_search_content: {"responseId": "mu7w723b4z2vid", "queryIndex": 0, "findText": ["effect size", "g =", "d =", "random effects", "57 experiments"]}
  - web_search  （provider=auto, numResults=5, workflow=none）
    - `Alfieri Nokes-Malach Schunn 2013 case comparisons meta-analysis overall effect size d = 0.50`
    - `Sala Gobet 2019 near transfer far transfer effect size cognitive training second-order meta-analysis g`
  - web_search  （provider=auto, numResults=6, workflow=none）
    - `interdisciplinary learning outcomes systematic review "little evidence" methodological weaknesses shallow`
    - `McDowell Jacobs 2017 natural frequencies Bayesian reasoning meta-analysis effect size Hedges g`
  - get_search_content: {"findText": ["g =", "effect size", "Hedges", "moderate"], "queryIndex": 0, "responseId": "mu7w6burcusjl6"}
  - get_search_content: {"findText": ["effect size", "g =", "d =", "spacing effect"], "queryIndex": 1, "responseId": "mu7w6s8lca5dwh"}
  - web_search  （provider=auto, numResults=5, workflow=none）
    - `Bisra 2018 inducing self-explanation meta-analysis overall weighted mean effect size g 0.55`
    - `Yang 2021 testing quizzing boosts classroom learning meta-analysis effect size g 0.499 222 studies`
  - web_search  （provider=auto, numResults=5, workflow=none）
    - `Colliot Jamet when actively self-generating graphic organisers hinders undergraduates learning European Journal of Psychology of Education`
    - `"The State of the Empirical Evidence for Interdisciplinary Learning Outcomes in Higher Education" systematic review findings`


---


## 4. 证据表（原文）

## 流域 5：知识组织、理解与迁移

> 调研工具：[`prompts/50-design-research.md`](../prompts/50-design-research.md)　状态：已完成（2026）

研究说明：仅依据实际检索到的摘要 / 摘要页片段（环境代理拦截了全文抓取），因此效应量只写确实读到的数值；未读到即标"未获取具体数值"。

| 方法 | 机制 | 证据强度 | 关键来源 | 适用条件 | 局限与反证 |
| --- | --- | --- | --- | --- | --- |
| 检索练习（测试效应） | 主动提取强化提取路径与后续学习 | **强**：222 项研究、48,478 名学生的课堂 meta 分析；Dunlosky 等评为"高效用" | [Testing (Quizzing) Boosts Classroom Learning](https://doi.org/10.1037/bul0000309) | 需长期保持的事实 / 程序 | 结局多为事实记忆；迁移增益弱（[Pan & Rickard 2018](https://doi.org/10.31234/osf.io/4qpyn)） |
| 间隔 / 分散练习 | 遗忘后再提取 | **强**：317 个实验、184 篇文献的量化综述；"高效用" | [Distributed Practice in Verbal Recall Tasks](https://doi.org/10.1037/0033-2909.132.3.354) | 需长期保持 | 最优间隔随考试延迟变化 |
| 自我解释 / 精加工 | 生成因果与关系推断 | **中—强**：69 个效应量的 meta 分析 | [Inducing Self-Explanation: a Meta-Analysis](https://doi.org/10.1007/s10648-018-9434-x) | 材料有因果结构 | 需提示或训练；结局是理解测验，非判断质量 |
| 交叉练习（interleaving） | 迫使辨别类别、注意区别特征 | **中**：59 研究 / 238 效应量，受材料相似度调节 | [Similarity matters](https://doi.org/10.1037/bul0000209) | 易混淆类别 | 相似度不匹配时可能无效 |
| 概念地图 / 知识图谱 | 外化关系结构、降低工作记忆负担 | **中**：Schroeder 等 g=0.58（142 效应量，n=11,814） | [Studying and Constructing Concept Maps](https://doi.org/10.1007/s10648-017-9403-9) | 作为**学习活动**，而非美化笔记 | 自生成图式组织者可能反而有害（[Colliot & Jamet](https://doi.org/10.1007/s10212-025-01057-y)）；"检索练习优于概念图"部分被指为方法学假象（[链接](https://doi.org/10.3389/fpsyg.2023.1258359)）；结局全是学科成绩 / 保持，**未见"跨领域判断"证据** |
| 对比案例（含案例法 CBL） | 类比对迫使抽取关系图式 | **中**：57 实验 / 336 检验的 meta 分析；CBL 的 meta 分析结局基本是考试成绩 | [Learning Through Case Comparisons](https://doi.org/10.1080/00461520.2013.775712) | 两个以上案例并置 | 单案例易致表面特征依赖（[Gentner 等](https://groups.psych.northwestern.edu/gentner/papers/GentnerLoewensteinThompson03.pdf)） |
| 向他人解释 / 学习即教学（含"费曼技巧"） | 生成 + 提取 + 自我监控 | **中（解释 / 教学本身）**：g=0.35（备教）、0.56（备教并教）；**弱（"费曼技巧"这个名号）**：未找到高质量 RCT | [Learning by Preparing-to-Teach and Teaching: A Meta-Analysis](https://doi.org/10.1111/jpr.12221) | 预期要教、需组织输出 | 收益可能主要来自检索练习（[链接](https://pmc.ncbi.nlm.nih.gov/articles/PMC9130926/)）；以"费曼技巧"为名的研究多为小样本准实验（[链接](https://doi.org/10.32871/rmrj2109.02.06)） |
| 按专家结构组织知识 | 专家按深层原理 / 图式归类，新手按表面特征 | **相关证据强**（专家—新手差异），**干预证据中且反向** | [Categorization and Representation of Physics Problems](https://doi.org/10.1207/s15516709cog0502_2) | 新手入门阶段的样例与分类训练 | 强加专家结构对新手促进有限，存在"专长逆转"（[How People Learn](https://www.nationalacademies.org/read/9853/chapter/5)） |
| 远迁移（"方法论能否用上新问题"） | 抽象原理 + 多情境练习 | **弱 / 近否定**：二阶层 meta 分析——收益"几乎不超出所训练任务和相似任务" | [Near and Far Transfer in Cognitive Training: A Second-Order Meta-Analysis](https://doi.org/10.1525/collabra.203) | 近迁移、同领域新问题 | 象棋 / 音乐 / 工作记忆训练为负证据（[链接](https://doi.org/10.1177/0963721417712760)）；迁移需先定义维度（[Barnett & Ceci](https://doi.org/10.1037/0033-2909.128.4.612)）；批判性思维训练有小效应但需与学科内容结合（[Abrami 等](https://doi.org/10.3102/0034654314551063)） |
| 跨学科整合本身 | 多视角整合 | **弱**：系统综述称结果多样、设计薄弱；另有综述明确"少有证据表明跨学科课程优于学科课程" | [The State of the Empirical Evidence for Interdisciplinary Learning Outcomes](https://doi.org/10.1353/rhe.0.a920416)；[链接](https://doi.org/10.1353/rhe.2004.0028) | 有明确整合任务与产出 | 结局多为态度 / 自评；"广而浅"风险尚无量化证据（未找到证据） |
| 数量级直觉 / 基准率 | 用自然频数替代条件概率，降低计算负荷 | **中**：20 年研究的 meta 分析显示自然频数显著提升贝叶斯推理 | [Meta-analysis of the effect of natural frequencies on Bayesian reasoning](https://doi.org/10.1037/bul0000126) | 风险、诊断、筛检类判断 | 仍是计算任务；对现实"量级感"的迁移未验证（未找到证据） |

覆盖调整说明：合并"案例法"与"对比案例"（同一机制族）；增列交叉练习与自然频数（这两个是唯一直接测"判断质量"的）。

### 一条最重要的结论

证据最强的是"**让知识被反复取出、且跨时间取出**"（检索练习 + 间隔练习）；而"整理形式"（概念地图、知识图谱，以及"费曼技巧"这个名号本身）效应中等且高度依赖使用方式；**跨学科整合与远迁移的正向证据最弱**。

因此：提示词应把"判断力"写成**可检查的提取、反例与近迁移任务**，不能承诺"帮助你建立知识体系"或"形成跨学科思维"。

### 可直接写进提示词的条款草案

1. 每个新领域先写"必须能回答的 5 个问题"，每个问题配一个**可判错的具体案例**；没有案例的概念不进地图。
2. 地图最多 12 个节点，每个节点必须写"它排除了什么"（失效条件 / 反例）；缺此字段视为未完成。
3. 每条结论必须标注证据类型（meta / RCT / 综述 / 无）与情境（实验室 / 真实）；无标注的按"未验证"处理，不得用于决策。
4. 输出后隔 1 天与 7 天各做一次**无提示默写**，只保留两次都通过的内容。
5. 涉及量级或风险判断时，一律写成自然频数（x/1000）并给出基准率，禁止只给百分比。

### 可自行验证的检索式

1. `("concept map" OR "knowledge map") AND ("far transfer" OR "transfer of learning")`
2. `"learning by teaching" AND ("meta-analysis" OR "randomized") AND (retention OR transfer)`
3. `"interdisciplinary" AND ("learning outcomes" OR "critical thinking") AND ("systematic review" OR "meta-analysis") AND "effect size"`


## 5. 引用核实状态

主导已二次核实 3 条：Bastani et al. PNAS 122(26) 2025-06-25 ✅；Nat Hum Behav 9(12):2510–2538 2025-08-26 ✅；Gollwitzer & Sheeran 2006, Adv. Exp. Soc. Psychol. 38:69–119 ✅。

**未核实、引用时必须标注**：arXiv 2606.21317、arXiv 2607.28133、arXiv 2601.20245（Anthropic 技术报告）、arXiv 2506.08872（MIT “Your Brain on ChatGPT”，预印本）。

本单内的其他引用**均未经人工核实**，请按第 1 节第 1 项抽查。

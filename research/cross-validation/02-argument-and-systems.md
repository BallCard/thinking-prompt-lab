# 交叉验证单 2/7：论证结构与系统视角

> 本单是一份**独立可验证**的证据交接件：由另一个 AI 单独核查这一个流域，不需要看其他 6 份。七份共用同一套核查清单与分级定义。

## 0. 背景

我们在设计一组提示词，让 AI 陪用户（大学生 / 非专业成年人）就**社会议题**与**人生选择**做深度思考。做法是：先检索「哪些方法真能提升思考质量」，再把证据为强 / 中的机制翻译成可执行、可检查的提示词条款。全部证据分为 7 个流域，本单是第 2 个：**论证结构与系统视角**。

本流域覆盖范围：论证图、Toulmin 模型、多视角换位、反事实推理、因果回路图、情报界结构化分析技术（SATs）

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

1. 「ACH 几乎无收益甚至有害」的强度——请核对该批判性综述的纳入标准与被批评方回应
2. 「论证图需数小时练习、单次短练无效」——这决定我们能否用「AI 画一张图」的用法，请重点核
3. 流域整体 g=0.26 的适用范围（学生 / 教育场景）能否外推到成人真实议题
4. 「take perspective 弱、get 优于 take」的复现情况
5. 反事实干预「中—大效应但窄」是否被我们用来支持了过宽的条款

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

- 条款 2「最强反方」→ 修正为「写出可为真的反方证据」，删掉「设身处地」
- 条款 11「论证图 / CLD / Toulmin」→ 降级为可选产出物
- 新增候选：因果链接标注必要 / 充分 / 仅相关
- 排除清单：竞争假设矩阵（ACH）、Toulmin 当干预、CLD 当默认工具

> 条款编号对应 `docs/clause-decisions.md`：00 总控、10 社会议题、20 人生规划、30 知识地图、40 深度检索。

## 3. 子代理原始提示词与检索日志（未人工改写）

### 2 论证结构与系统视角

- 子代理名：`research-argument`　会话 id：`ed7e33a6-62af-474`
- 工具调用：24 次（其中 web_search 检索式 54 条、fetch_content 4 个 URL）
- 最终报告字符数：3375

#### 原始提示词（完整）

```text
你在为一个中文提示词工具箱做**文献与证据检索**（不要写代码、不要改文件、只做研究并返回报告）。

背景：工具箱的用途是让 AI 陪用户（大学生/非专业成年人，单个议题能投入 1–2 小时）就社会议题和人生选择做深度思考。设计约束是输出必须可检查（区分事实/推论/价值、来源分级、标注不确定性），而不是空泛地要求"要深刻、要多角度"。

你的任务：只研究【论证结构与系统视角】这一个流域，回答"哪些结构性方法有证据表明能提升推理与判断质量，哪些只是流行说法"。

需要覆盖（可增删，但说明理由）：
- 论证图 / argument mapping（如 Reason!Able、Rationale 类工具）对批判性思维技能的效果，是否有 RCT 与效应量
- Toulmin 论证模型在教学与实务中的实证支持
- 多视角/换位思考（perspective-taking、consider-the-other-side）对判断准确性与态度的效果（含"换位是否能减少偏见"的争议）
- 因果分层、必要/充分条件分析、反事实推理（counterfactual reasoning）的训练效果
- 系统思维 / 因果回路图（causal loop diagrams）、系统动力学在提升复杂问题理解上的证据
- 结构化分析技术（structured analytic techniques, SATs，情报分析领域）的实际效果证据（注意：这一领域有"缺乏实证支持"的批评，请核实）

硬性要求：
1. 优先系统综述、meta 分析、随机对照实验、同行评议综述。每个关键结论必须附上你**实际检索到**的 URL；不得编造标题、作者、期刊、年份、链接。找不到证据就写"未找到证据"。
2. 必须主动检索反面方向：无效、无显著效果、争议、复现失败、被过度宣传（尤其 SATs 与"批判性思维培训"的迁移效应是否成立、是否只在特定测量上有效）。
3. 严格区分：实验室短期效应 vs 长期能力提升；技能提升 vs 测量工具敏感度；相关 vs 因果。
4. 输出中文，不超过 900 字，结构如下：

| 方法 | 机制（为什么可能有用） | 证据强度（强/中/弱/已否定 + 一句话依据） | 关键来源（标题 + URL） | 适用条件 | 局限与反证 |
| --- | --- | --- | --- | --- | --- |

然后再给：
- 一条最重要的结论
- 3–5 条"可直接写进提示词的条款草案"（每条 ≤2 行，必须可执行、可检查；禁止"要深刻""多角度思考"这类表述）
- 3 条我可以自己继续检索验证的检索式

宁少而准，不要泛泛而谈。
```

#### 检索日志（按时间顺序）

  - web_search  （numResults=8, workflow=none）
    - `argument mapping critical thinking meta-analysis effect size randomized controlled trial`
    - `van Gelder Reason!Able argument mapping critical thinking gains effect size study`
    - `Toulmin argumentation model empirical evidence teaching effectiveness research`
    - `consider the opposite debiasing perspective taking accuracy reduce bias meta-analysis`
  - web_search  （numResults=8, workflow=none）
    - `structured analytic techniques intelligence analysis empirical evidence lack of support criticism`
    - `causal loop diagram systems thinking learning evidence experiment`
    - `counterfactual reasoning training improves judgment evidence`
    - `critical thinking training transfer far transfer meta-analysis limitations`
  - web_search  （provider=['brave', 'tavily', 'duckduckgo', 'searxng'], numResults=8, workflow=none）
    - `argument mapping critical thinking meta-analysis effect size`
    - `argument mapping randomized controlled trial van Gelder critical thinking gains`
    - `structured analytic techniques empirical evidence criticism intelligence analysis`
  - web_search  （provider=['brave', 'tavily', 'duckduckgo', 'searxng'], numResults=8, workflow=none）
    - `consider the opposite debiasing meta-analysis perspective taking bias`
    - `Toulmin model argumentation empirical research evidence`
    - `causal loop diagram systems thinking learning experiment evidence`
  - fetch_content
    - https://www.rand.org/content/dam/rand/pubs/research_reports/RR1400/RR1408/RAND_RR1408.pdf
    - https://www.tandfonline.com/doi/full/10.1080/08850607.2023.2243803
  - web_search  （provider=["duckduckgo"], numResults=8, workflow=none）
    - `perspective taking accuracy Epley egocentric anchoring adjustment does not improve accuracy`
    - `systems thinking intervention meta-analysis effectiveness evidence teaching`
    - `counterfactual thinking training debiasing hindsight bias evidence`
    - `critical thinking instruction meta-analysis Abrami effect size transfer critique`
  - web_search  （provider=['duckduckgo'], numResults=8, workflow=none）
    - `perspective taking fails to improve accuracy Epley egocentric anchoring adjustment`
    - `systems thinking intervention meta-analysis effectiveness evidence teaching`
    - `counterfactual thinking training debiasing hindsight bias evidence`
    - `critical thinking instruction meta-analysis Abrami effect size transfer critique`
  - fetch_content
    - https://philarchive.org/rec/DAVAMI-6
    - https://www.reasoninglab.com/wp-content/uploads/2013/10/TvG-Using-argument-mapping-to-improve-critical-thinking-skills-2015.pdf
  - bash: `cat "C:\Users\12855\.pi\agent\web-search.json" 2>/dev/null | head -60; echo "---ENV---"; env | grep -iE "api_key|apikey|SEARXNG|JINA|FIRECRAWL|TAVILY|BRAVE|EXA" | sed 's/=.*/=<set>/'`
  - web_search  （provider=["jina", "firecrawl", "search1api", "searxng"], numResults=6, workflow=none）
    - `perspective taking does not improve accuracy Epley 2004`
    - `systems thinking interventions meta-analysis effect size`
  - web_search  （provider=['jina', 'firecrawl', 'search1api', 'duckduckgo'], numResults=6, workflow=none）
    - `perspective taking does not improve accuracy Epley egocentric anchoring`
    - `systems thinking interventions meta-analysis effect size evidence`
  - web_search  （provider=['firecrawl', 'search1api', 'jina'], numResults=6, workflow=none）
    - `counterfactual thinking training debiasing evidence`
    - `necessary and sufficient conditions causal reasoning training`
  - bash: `sleep 25; echo ok`
  - web_search  （provider=["duckduckgo"], numResults=6, workflow=none）
    - `perspective taking does not improve accuracy Epley egocentric anchoring adjustment 2004`
  - web_search  （provider=['duckduckgo', 'exa'], numResults=6, workflow=none）
    - `perspective taking does not improve accuracy Epley egocentric anchoring adjustment 2004`
  - web_search  （provider=['exa', 'duckduckgo'], numResults=6, workflow=none）
    - `Chang Berdini Mandel Tetlock restructuring structured analytic techniques intelligence cognitive bias training`
    - `systems thinking interventions meta-analysis effect size student learning`
    - `critical thinking instruction meta-analysis Abrami 2015 strategies effectiveness`
  - web_search  （provider=['exa', 'duckduckgo'], numResults=6, workflow=none）
    - `counterfactual reasoning training improves reasoning evidence experiment`
    - `concept mapping meta-analysis effect size Nesbit Adesope`
    - `argument mapping criticism effect size inflated limitations critical thinking tests`
  - bash: `env | grep -iE "proxy" ; echo "---"; nslookup pubmed.ncbi.nlm.nih.gov 2>&1 | tail -5; echo "--- sleep"; sleep 30; echo ok`
  - web_search  （provider=['exa', 'duckduckgo'], numResults=6, workflow=none）
    - `Abrami 2015 strategies for teaching students to think critically meta-analysis effect size`
    - `Ludolph Schulz debiasing meta-analysis does debiasing training work`
    - `counterfactual reasoning training intervention improves causal reasoning students`
  - web_search  （provider=['exa', 'duckduckgo'], numResults=6, workflow=none）
    - `perspective taking intergroup bias meta-analysis does it reduce bias`
    - `Revisiting the Psychology of Structured Analytical Techniques empirical evidence three SATs`
    - `causal illusions intervention high school six-month follow-up results effective`
  - web_search  （provider=['exa', 'duckduckgo'], numResults=6, workflow=none）
    - `van Gelder Bissett Cumming 2004 cultivating expertise informal reasoning controlled trial Canadian Journal of Experimental Psychology`
    - `influence of causal loop diagrams systems thinking information use findings experiment`
    - `Davies Calma argument mapping systematic review effect size heterogeneity limitations`
  - web_search  （provider=['exa', 'duckduckgo'], numResults=6, workflow=none）
    - `meta-analysis debiasing interventions effectiveness Sellier Scopelliti Morewedge`
    - `Monat Gannon what is systems thinking review critique measurement definition`
    - `necessary and sufficient conditions instruction causal reasoning students evidence`
  - web_search  （provider=['exa', 'duckduckgo'], numResults=6, workflow=none）
    - `Systematic review meta-analysis educational approaches reduce cognitive biases students Nature Human Behaviour 54 randomized controlled trials moderators`
    - `RAND RR1408 assessing value structured analytic techniques intelligence community findings conclusion no evidence`
    - `Toulmin argumentation model critical thinking epistemological beliefs 68 students online results`
  - web_search  （provider=['exa', 'duckduckgo'], numResults=6, workflow=none）
    - `Teaching Critical Thinking With Argument Mapping 2024 political science results control group`
    - `argument mapping effect size critique control group comparison weak designs critical thinking measurement`
    - `debiasing meta-analysis students moderators which interventions work best longer duration`


---


## 4. 证据表（原文）

## 流域 2：论证结构与系统视角

> 调研工具：[`prompts/50-design-research.md`](../prompts/50-design-research.md)　状态：已完成（2026）

结构说明：情报分析的结构化技术（SATs）拆成两行——"头脑风暴 / 魔鬼代言人"与"ACH / 竞争假设矩阵"的证据方向相反，合并会掩盖差异；"多视角换位"与"consider-the-opposite"合并为一行，因机制家族相同但证据强度不同，在格内分列。

| 方法 | 机制 | 证据强度 | 关键来源 | 适用条件 | 局限与反证 |
| --- | --- | --- | --- | --- | --- |
| 论证图 argument mapping | 把隐含前提、反驳外显化，减工作记忆负荷，使"理由是否支持结论"可逐格检查 | **中—强**。86 项研究的系统综述 + meta 报大效应，作者自承异质性严重；Dwyer 对照实验仅"评价 / 归纳推理"两个分测验获益 | [Davies & Calma](https://philarchive.org/rec/DAVAMI-6)；[Dwyer 2011](https://eprints.teachingandlearning.ie/id/eprint/4010/1) | 需要**数小时级刻意练习**（[van Gelder 2004](https://doi.org/10.1037/h0085794)）；**单次短练无效** | 对照常是"无训练"；测试与训练同构；[Wiley 综述](https://doi.org/10.1111/hequ.70063)指单组前后测设计抬高效应 |
| Toulmin 模型 | 强制区分 claim / grounds / warrant / qualifier / rebuttal，暴露跳跃 | **弱**。仅见准实验 n=68，两组无显著差异 | [链接](https://doi.org/10.35923/jes.2024.2.09)（ERIC EJ1457482） | 只宜当"拆解清单"，不宜当"提升思维"的干预 | 无 RCT；地位来自教材惯例而非实证 |
| 多视角 / 换位 | 把反面证据拉进检索集，或从他人立场重建推理 | **分化**。consider-the-opposite 对锚定、确认偏差有个别实验支持；"想象他人视角（take perspective）"提升判断准确性的证据弱、常失败 | [Epley 2004](https://pubmed.ncbi.nlm.nih.gov/15382983/)；[Eyal 2018（25 实验："get"优于"take"）](https://doi.org/10.1037/pspa0000115)；[Todd & Galinsky](https://doi.org/10.1111/spc3.12116) | 明确要求"写出最强反方论证"，**而非**"设身处地" | 换位≠准确；想象他人以自身为锚；该类干预在偏见研究中多为轻触式、效果不持久 |
| 反事实 / 必要充分条件 | 用"若 X 不发生，Y 还在吗"逼出因果结构，替代相关即因果 | **中（窄）**。针对"因果错觉"的校本干预 n=1668、40 校，中—大效应且维持 6 个月 | [链接](https://doi.org/10.1098/rsos.240846)；[儿童类证据](https://doi.org/10.1111/cdev.13518) | 已有具体候选因果时做检验 | 限于青少年 + 特定偏差；成人、跨议题迁移未验证；"必要 / 充分条件"训练本身**未找到独立证据** |
| 系统思维 / 因果回路图 CLD | 把反馈、延迟、非线性结构画出 | **弱—中**。CLD 呈现能提升系统思维与信息使用，但多为小组、非随机、即时测量；"系统思维"定义本身无共识 | [链接](https://doi.org/10.1016/j.chbr.2025.100613)；[链接](https://doi.org/10.3390/systems14040378)；[Monat & Gannon](http://article.sapub.org/10.5923.j.ajss.20150401.02.html) | 用于生成"遗漏的反馈回路 / 延迟"清单 | 无公认测量工具；缺延迟后测与迁移证据；易退化为画图术语 |
| SATs：头脑风暴 / 魔鬼代言人 | 强制生成替代假设、制度化的角色对抗 | **中（仅此两项）**。综述称这两项有实证支持 | [链接](https://doi.org/10.1080/08850607.2023.2243803) | 团队、低时间压力 | 效果限于**生成数量**，不保证判断质量 |
| SATs：ACH / 竞争假设矩阵 | 用证据 × 假设矩阵强制反向检索 | **已否定 / 弱**。批判性综述（6 个实验）称"整体几乎无收益，甚至有害"；n=161 实验发现 ACH 式矩阵比"假设在行"更糟；RAND 指情报界从不系统评估 | [链接](https://doi.org/10.31234/osf.io/an32t)；[链接](https://doi.org/10.1186/s41235-024-00560-y)；[RAND RR1408](https://www.rand.org/pubs/research_reports/RR1408.html) | **不建议作为默认工具** | 制度化 ≠ 有效；部分技术可能新增偏差 |

### 该流域整体效应

54 项学生群体 RCT、383 个效应量、10,941 人的 meta 分析给出**小而非零的均值 g = 0.26**（[Nat Hum Behav 2025](https://doi.org/10.1038/s41562-025-02253-y)）。而且**仅"抽象讲授偏差存在"已被反复证明无效**（[链接](https://doi.org/10.3389/fpsyg.2021.629354)、[链接](https://doi.org/10.1177/0272989x17716672)；Abrami 2015 g+≈0.30 [链接](https://doi.org/10.3102/0034654314551063)）。

### 一条最重要的结论

本流域最佳可得证据只有**小的平均效应**，且效应随"对照条件变强"而缩水。真正稳定的收益来自**有具体产出物的结构化练习**（写出反方、做出矩阵、画出回路），而**不是**讲授方法论或要求"多角度"。

含义：提示词的价值不在于"告诉用户有哪些分析框架"，而在于**逼用户产出一个具体物件**（一张有三格的表、两条反方证据、一条回路）。这也是本工具箱与"AI 直接输出一份漂亮分析"的根本区别。

### 可直接写进提示词的条款草案

1. 每个关键主张必须拆成三格：`事实 / 推论 / 价值`，每格附来源等级（meta > 单一 RCT > 个案 > 无源）。
2. 必须写出 ≥2 条与己方结论相反的证据，并标注"若其为真，结论改变到哪一步"。
3. 对每条因果链接标注 `必要 / 充分 / 仅相关`，并给出一条能证伪它的具体观察。
4. 至少画出 1 条反馈回路，标注极性、延迟与可能的反弹点；未纳入的因素单列"未建模"。
5. 结尾必须给出 ≥2 条"证据不足 / 我不知道"，不得留空。

### 可继续验证的检索式

1. `"argument mapping" AND "active control" AND ("far transfer" OR "delayed posttest")`
2. `"debiasing" AND "follow-up" AND ("RCT" OR "meta-analysis") AND ("retention" OR "transfer")`
3. `"systems thinking" AND "causal loop diagram" AND ("delayed posttest" OR "transfer") NOT "self-report"`

### 未找到证据

- Toulmin 模型的 RCT
- "必要 / 充分条件"分析作为训练干预的独立效果研究
- CLD 的长期迁移实验

### 与项目的直接冲突

- `prompts/00-master.md` 现有的"**最强反方**"条款方向正确（consider-the-opposite 有支持），但必须改成"写出可为真的反方证据 + 说明结论改动"，**不能是"从对方视角想一想"**
- 论证图要写成**让用户自己产出一张表**，并且只在需要时用；几十秒的"AI 帮你画个论证图"没有证据支持（需要数小时级练习才有迁移收益）
- **不要引入竞争假设矩阵类工具**（ACH 已被否定）


## 5. 引用核实状态

主导已二次核实 3 条：Bastani et al. PNAS 122(26) 2025-06-25 ✅；Nat Hum Behav 9(12):2510–2538 2025-08-26 ✅；Gollwitzer & Sheeran 2006, Adv. Exp. Soc. Psychol. 38:69–119 ✅。

**未核实、引用时必须标注**：arXiv 2606.21317、arXiv 2607.28133、arXiv 2601.20245（Anthropic 技术报告）、arXiv 2506.08872（MIT “Your Brain on ChatGPT”，预印本）。

本单内的其他引用**均未经人工核实**，请按第 1 节第 1 项抽查。

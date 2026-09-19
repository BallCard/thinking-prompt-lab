# 交叉验证单 3/7：判断偏差干预与决策辅助

> 本单是一份**独立可验证**的证据交接件：由另一个 AI 单独核查这一个流域，不需要看其他 6 份。七份共用同一套核查清单与分级定义。

## 0. 背景

我们在设计一组提示词，让 AI 陪用户（大学生 / 非专业成年人）就**社会议题**与**人生选择**做深度思考。做法是：先检索「哪些方法真能提升思考质量」，再把证据为强 / 中的机制翻译成可执行、可检查的提示词条款。全部证据分为 7 个流域，本单是第 3 个：**判断偏差干预与决策辅助**。

本流域覆盖范围：premortem、反方论证 / 红队、参考类预测与基础比率、校准训练、决策复盘、决策日志、可逆 / 不可逆分类、检查清单、第三人称自我距离

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

1. premortem 判为「弱—中」是否低估：请确认是否存在我们漏掉的、以**决策质量**为结局指标的实验
2. 「决策日志无任何直接证据」——是检索不足还是确实空白
3. 校准训练 meta 的偏倚风险评级与 g 的置信区间
4. AAR d≈0.67 从团队 / 军事场景外推到「个人自我复盘」是否成立，以及 >1/3 效应为负这一异质性如何影响条款
5. 第三人称自我距离的结局是「明智推理评分」，把它写进人生规划条款是否越界

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

- 条款 8：premortem 不进默认流程；可逆性分类删掉「单向门」说法；决策日志删除
- 条款 9「置信度打分」→ 保留但必须绑定事后对账
- 新增候选：预测登记 + 到期对账（复盘三件套）、参考类预测、第三人称自我距离

> 条款编号对应 `docs/clause-decisions.md`：00 总控、10 社会议题、20 人生规划、30 知识地图、40 深度检索。

## 3. 子代理原始提示词与检索日志（未人工改写）

### 3 判断偏差干预与决策辅助

- 子代理名：`research-decision`　会话 id：`10d32038-eebb-442`
- 工具调用：25 次（其中 web_search 检索式 62 条、fetch_content 0 个 URL）
- 最终报告字符数：3717

#### 原始提示词（完整）

```text
你在为一个中文提示词工具箱做**文献与证据检索**（不要写代码、不要改文件、只做研究并返回报告）。

背景：工具箱的用途是让 AI 陪用户（大学生/非专业成年人）就社会议题和人生选择做深度思考，包含"人生规划/选择取舍"模块。设计约束是输出必须可检查，不能靠空泛的鼓励。

你的任务：只研究【判断偏差干预与决策辅助】这一个流域，回答"哪些干预手段有证据表明能提升判断质量，哪些只是流行说法"。这是本工具箱最需要证据支撑的部分，请特别在意证据强度与效应量。

需要覆盖（可增删，但说明理由）：
- 事前验尸 premortem（Klein）的真实实证支持程度，与"列出风险"相比是否更有效
- consider-the-opposite / 反方论证、devil's advocate、红队机制对减少确认偏误的效果（含"是否有反效果或象征性使用"的批评）
- 参考类预测（reference class forecasting）与基础比率的使用效果（如 Flyvbjerg 在大型项目成本预测上的证据）
- 概率校准训练、置信度评分与 Brier 分数、预测记录（如 Tetlock 的 Good Judgment Project 及其"能不能被训练"的结论）
- 决策日志/决策复盘（decision journal、after-action review）对后续判断的影响
- 可逆与不可逆决策分类、"最小可逆实验"这类做法的理论来源与实证支撑（注意区分贝索斯式管理箴言与真实证据）
- 过度自信的干预：能否通过训练、反馈、清单降低
- 检查清单（checklists）在专业决策中的效果（如外科手术清单研究）与局限

硬性要求：
1. 优先系统综述、meta 分析、随机对照实验、同行评议综述。每个关键结论必须附上你**实际检索到**的 URL；不得编造标题、作者、期刊、年份、链接。找不到证据就写"未找到证据"。
2. 必须主动检索反面方向：premortem 是否只有理论而无实验证据、devil's advocate 是否经常失效、校准训练效果能否迁移到真实决策、清单是否在复杂情境中失效（如某些研究显示清单可能降低专家表现）。
3. 严格区分：实验室任务效应 vs 真实决策改进；去偏（debiasing）是否真能持久。
4. 输出中文，不超过 900 字，结构如下：

| 方法 | 机制（为什么可能有用） | 证据强度（强/中/弱/已否定 + 一句话依据） | 关键来源（标题 + URL） | 适用条件 | 局限与反证 |
| --- | --- | --- | --- | --- | --- |

然后再给：
- 一条最重要的结论
- 3–5 条"可直接写进提示词的条款草案"（每条 ≤2 行，必须可执行、可检查；禁止"要理性""多角度思考"这类表述）
- 3 条我可以自己继续检索验证的检索式

宁少而准，不要泛泛而谈。
```

#### 检索日志（按时间顺序）

  - web_search  （numResults=8, workflow=none）
    - `premortem prospective hindsight empirical study evidence debiasing`
    - `Klein premortem experiment critical review lack of empirical evidence`
    - `consider the opposite debiasing confirmation bias meta-analysis`
    - `devil's advocate fails to reduce confirmation bias study evidence`
  - web_search  （numResults=8, workflow=none）
    - `reference class forecasting Flyvbjerg cost overrun evidence accuracy`
    - `debiasing training transfer to real world decisions meta-analysis long-term`
    - `Good Judgment Project forecasting tournaments training improvement Tetlock`
    - `calibration training Brier score probability judgment improve`
  - web_search  （provider=brave, numResults=8, workflow=none）
    - `premortem prospective hindsight empirical study evidence`
    - `consider the opposite debiasing meta-analysis confirmation bias`
    - `devil's advocate fails reduce confirmation bias study`
    - `reference class forecasting Flyvbjerg cost overrun accuracy`
  - web_search  （provider=tavily, numResults=8, workflow=none）
    - `Good Judgment Project forecasting training Tetlock results`
    - `debiasing training transfer real world decisions meta-analysis`
    - `surgical safety checklist evidence limitations Hawthorne effect`
    - `decision journal after action review improve judgment evidence`
  - bash: `cat "C:/Users/12855/.pi/agent/web-search.json" 2>/dev/null | head -60`
  - web_search  （provider=jina, numResults=8, workflow=none）
    - `premortem prospective hindsight empirical study evidence`
    - `consider the opposite debiasing meta-analysis confirmation bias`
  - web_search  （provider=duckduckgo, numResults=8, workflow=none）
    - `premortem prospective hindsight empirical study evidence`
    - `consider the opposite debiasing meta-analysis confirmation bias`
  - web_search  （provider=searxng, numResults=8, workflow=none）
    - `premortem prospective hindsight empirical study evidence`
    - `consider the opposite debiasing meta-analysis`
  - web_search  （provider=duckduckgo, numResults=6, workflow=none）
    - `Veinott Klein Wiggins 2010 premortem technique plan confidence ISCRAM evaluating effectiveness`
  - web_search  （provider=duckduckgo, numResults=6, workflow=none）
    - `Schulz-Hardt 2002 productive conflict group decision making genuine contrived dissent biased information seeking`
  - web_search  （provider=duckduckgo, numResults=6, workflow=none）
    - `Sellier Scopelliti Morewedge debiasing training improves decision making in the field`
  - web_search  （provider=duckduckgo, numResults=6, workflow=none）
    - `Urbach 2014 introduction surgical safety checklists Ontario Canada no reduction mortality NEJM`
  - web_search  （provider=perplexity, numResults=5, workflow=none）
    - `Veinott Klein Wiggins premortem effectiveness study`
  - web_search  （provider=gemini, numResults=5, workflow=none）
    - `Veinott Klein Wiggins premortem effectiveness study`
  - web_search  （provider=serper, numResults=5, workflow=none）
    - `Veinott Klein Wiggins premortem effectiveness study`
  - web_search  （provider=parallel-mcp, numResults=5, workflow=none）
    - `Veinott Klein Wiggins premortem effectiveness study`
  - web_search  （provider=parallel-mcp, numResults=6, workflow=none）
    - `Schulz-Hardt 2002 productive conflict genuine contrived dissent biased information seeking`
    - `Nemeth devil's advocate authentic dissent minority influence study`
    - `Sellier Scopelliti Morewedge debiasing training improves decision making field Psychological Science`
    - `devil's advocate ineffective red teaming critique evidence`
  - web_search  （provider=parallel-mcp, numResults=6, workflow=none）
    - `Flyvbjerg reference class forecasting cost overrun megaprojects evidence`
    - `Buehler Griffin Ross planning fallacy outside view personal past experience improve estimates`
    - `Good Judgment Project superforecasters training Mellers Tetlock results`
    - `Chang Chen Mellers Tetlock developing expert political judgment training forecasting tournament`
  - web_search  （provider=parallel-mcp, numResults=6, workflow=none）
    - `Urbach 2014 surgical safety checklists Ontario Canada no reduction mortality complications NEJM`
    - `systematic review meta-analysis surgical safety checklist effectiveness uncertain Bergs BMJ Open`
    - `Catchpole Russ the problem with checklists BMJ Quality Safety critique`
    - `Haynes 2009 WHO surgical safety checklist reduced mortality NEJM`
  - web_search  （provider=parallel-mcp, numResults=6, workflow=none）
    - `Tannenbaum Cerasoli 2013 do team and individual debriefs enhance performance meta-analysis`
    - `Einhorn Hogarth 1978 confidence in judgment persistence of the illusion of validity learning from experience`
    - `Sleesman 2012 escalation of commitment meta-analysis journal of applied psychology`
    - `Kluger DeNisi 1996 feedback interventions meta-analysis negative effects`
  - web_search  （provider=parallel-mcp, numResults=6, workflow=none）
    - `Larrick 2004 debiasing review consider the opposite most effective strategy`
    - `meta-analysis debiasing interventions effect size reduce cognitive bias generalization`
    - `Milkman Chugh Bazerman how can decision making be improved debiasing limits`
    - `Hirt Markman 1995 multiple explanation consider an alternative strategy debiasing judgments`
  - web_search  （provider=parallel-mcp, numResults=6）

  - web_search  （provider=parallel-mcp, numResults=6, workflow=none）
    - `premortem systematic review empirical evidence debiasing technique effectiveness limited`
    - `overconfidence debiasing intervention reduces overprecision training feedback study`
    - `Moore Healy 2008 trouble with overconfidence three types Psychological Review`
    - `Gallop 2016 premortem prospective hindsight study experimental`
  - web_search  （provider=parallel-mcp, numResults=6, workflow=none）
    - `irreversible decisions one-way door real options value of waiting empirical evidence`
    - `minimum viable experiment lean startup evidence randomized trial critique`
    - `reversibility of decisions effect on escalation commitment experiment`
    - `decision staging reversibility framing risky choice evidence experiment`
  - web_search  （provider=parallel-mcp, numResults=6, workflow=none）
    - `decision journal evidence effectiveness randomized study keeping record of decisions`
    - `checklist impairs expert performance complex task decrement study`
    - `self-distancing reflection improves reasoning Kross Grossmann evidence`
    - `reference class forecasting critique Themsen does not improve cost estimates`


---


## 4. 证据表（原文）

## 流域 3：判断偏差干预与决策辅助

> 调研工具：[`prompts/50-design-research.md`](../prompts/50-design-research.md)　状态：已完成（2026）

| 方法 | 机制 | 证据强度 | 关键来源 | 适用条件 | 局限与反证 |
| --- | --- | --- | --- | --- | --- |
| 事前验尸 premortem | 用"已经失败"的未来完成时逼出被忽略的失败路径 | **弱—中**。有几个受控实验，但结局指标是"信心下降 / 风险条数"而非决策质量；综述明言"实证研究很少" | [Veinott/Klein/Wiggins 2010](https://idl.iscram.org/files/veinott/2010/1049_Veinott_etal2010.pdf)；[Wiley 综述](https://onlinelibrary.wiley.com/doi/10.1002/ffo2.209) | 承诺前、单次、团队 | 比"列风险"强的只是降信心；游戏团队研究反见信心上升 <https://journals.sagepub.com/doi/10.1177/21695067231193680> |
| 反方论证 / 红队 | 强制生成反向证据，打断确认性信息搜索 | **中（限特定框架）**。"考虑相反面"是少数被反复验证的去偏策略；但指派"魔鬼代言人"弱于真实异见 | [Larrick 2004](http://web.stanford.edu/~knutson/jdm/larrick04.pdf)；[Schulz-Hardt 2002](https://doi.org/10.1016/S0749-5978%2802%2900001-8)；[Nemeth 2001](https://onlinelibrary.wiley.com/doi/10.1002/ejsp.58) | 由持真实异议者执行 | 象征性使用、被忽略；单纯"列理由"无效；过度使用可能反噬 |
| 参考类预测 / 基础比率 | 用同类已完结事件的分布替代对本次的想象 | **中—强（群体层面）**。大型项目成本与工期系统性低估有大量数据；回忆自己过去完成时间同样有效 | [Flyvbjerg](https://arxiv.org/pdf/1302.3642)；[Buehler 1994](https://web.mit.edu/curhan/www/docs/Articles/biases/67_J_Personality_and_Social_Psychology_366%2C_1994.pdf) | 存在够窄、够多的参考类 | 参考类定义带主观性；单案例研究显示 RCF 未改善精度 <https://onlinelibrary.wiley.com/doi/abs/10.1111/faam.12210> |
| 校准训练 / 过度自信干预 | 用概率替代二元判断，靠反馈压低"过精度" | **中（实验强、迁移弱）**。锦标赛中概率推理训练四年均改善 Brier 分；54 个 RCT 元分析合并 g=0.26 | [Chang 2016](http://goodjudgment.com/wp-content/uploads/2018/12/jdm16511.pdf)；[Nat Hum Behav 2025](https://www.nature.com/articles/s41562-025-02253-y) | 带反馈的重复练习 + 记分 | g 很小、偏倚风险高、课堂外迁移未知；"环境反馈"反而升高过度自信；三型过度自信不可一律"降低" |
| 决策复盘 AAR | 结构化回顾—归因—改进行动 | **中—强（表现类）**。46 个样本元分析 d=0.67（约 +25%），团队 / 个人、真实 / 模拟一致 | [Tannenbaum & Cerasoli 2013](https://journals.sagepub.com/doi/abs/10.1177/0018720812448394) | 有明确任务目标与可重复表现 | 反馈整体不稳：607 个效应中 >1/3 反而降低表现 <https://psycnet.apa.org/record/1996-02773-003>；噪声 / 延迟反馈下学不到东西 <https://eric.ed.gov/?id=EJ191793> |
| 决策日志 | 事前写预期，事后校准记忆与归因 | **未找到直接证据**。无针对"决策日志"的 RCT 或元分析 | 仅实务模板 <https://alliancefordecisioneducation.org/resources/keeping-a-decision-journal> | 作为 AAR 的输入件 | 不可单独宣传为有效技法 |
| 可逆 / 不可逆分类、最小可逆实验 | 不可逆产生"等待的期权价值"；小实验换信息 | **中（理论 + 经济计量），非通用实验证据**；"贝索斯单向门"未找到同行评议证据 | [McDonald & Siegel](https://www.nber.org/papers/w1019)；[Bulan 2005](https://ideas.repec.org/a/eee/revfin/v14y2005i3-4p241-254.html) | 高不确定 + 沉没成本 + 可延迟 | MVP 证据混杂，被批评助长增量实验 <https://journals.sagepub.com/doi/10.1177/01492063231226136>；"继续投入＝行动"的框架本身会推高升级承诺 d=0.37 |
| 检查清单 | 把可枚举的易漏步骤外置，绕过记忆 | **中（对"遗漏"有效，总体不一致）**。手术 / 航空有正效果，但人群级证据可为零 | [Haynes 2009](https://www.nejm.org/doi/full/10.1056/NEJMsa0810119)；[Bergs 2014 元分析](https://pubmed.ncbi.nlm.nih.gov/24469615) | 步骤稳定可枚举；只用于核对阶段 | 安大略 21 万例自然实验无显著改善 <https://www.nejm.org/doi/full/10.1056/NEJMsa1308261>；依从 73%、完整执行仅 51% <https://pubmed.ncbi.nlm.nih.gov/40186199>；但专家用在核对阶段并不受损 <https://pubmed.ncbi.nlm.nih.gov/23398016> |
| 第三人称 / 旁观者自我距离（增补） | 把自己当"另一个人"来推理 | **中**。三项 RCT（N=693）中自我距离消除"对己不如对人明智"的偏差 | [Grossmann & Kross 2014](https://pubmed.ncbi.nlm.nih.gov/24916084/) | 高利害、涉及自身的情绪化议题 | 指标是"明智推理评分"，不是真实决策结果；日记式训练仅一周实验 |

增补"自我距离"的理由：它是本清单里**唯一针对"人生选择类议题"有 RCT 支持的单一操作**，比泛泛的"多角度思考"可执行。

### 一条最重要的结论

本流域最强、最可迁移的效应来自**把判断外置成可计分、可反馈的流程**（复盘 d=0.67、校准训练、参考类预测）；而最响亮的流行说法——**事前验尸、单向门 / 双向门、决策日志**——证据最薄。去偏训练在受控任务上的平均效应只有 g≈0.26，且能否迁移到真实决策**仍未被证明**。

### 可直接写进提示词的条款草案

1. 每条关键判断必须给出 0–100 的概率，并注明"什么证据会让我把它下调 20 点以上"。
2. 先写出本议题同类事件的历史分布（发生频率或典型区间），再写本次预测；两者冲突时必须说明为何本次不同。
3. 强制生成至少 3 条反驳当前结论的具体证据来源，其中至少 1 条必须是持真实不同立场者会引用的（不是稻草人）。
4. 输出末尾固定给出：本次判断的可逆性、最小可逆验证动作、以及"何时回头复核"的时间点。
5. 复盘时只对照事前写下的预期与实际结果，逐条标出是哪一步推理出错；**不接受**"结果不好但过程没错"这种自评。

### 可继续验证的检索式

1. `premortem randomized controlled trial decision quality outcome (not confidence)`
2. `debiasing training transfer field setting follow-up effect size meta-analysis site:ssrn.com OR site:osf.io`
3. `checklist expertise reversal complex dynamic task performance decrement experiment`

### 未找到证据

- 决策日志的独立效果
- "单向门 / 双向门"分类的对照实验证据（只有期权理论 + 经济计量支持）

### 与流域 2、4 的交叉

- 流域 4 与本文都指向同一结论：**没有反馈就没有校准**，所以"置信度打分"必须绑定"事后回来对账"，否则只是形式。
- 校准效应（g≈0.26）比复盘（d≈0.67）小得多 → 提示词里"预测 + 对账"应作为复盘流程的一部分，而不是独立卖点。


## 5. 引用核实状态

主导已二次核实 3 条：Bastani et al. PNAS 122(26) 2025-06-25 ✅；Nat Hum Behav 9(12):2510–2538 2025-08-26 ✅；Gollwitzer & Sheeran 2006, Adv. Exp. Soc. Psychol. 38:69–119 ✅。

**未核实、引用时必须标注**：arXiv 2606.21317、arXiv 2607.28133、arXiv 2601.20245（Anthropic 技术报告）、arXiv 2506.08872（MIT “Your Brain on ChatGPT”，预印本）。

本单内的其他引用**均未经人工核实**，请按第 1 节第 1 项抽查。

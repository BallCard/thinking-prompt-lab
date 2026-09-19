# 交叉验证包：一套"促进思考"的提示词工具箱（阶段 1 证据 + 阶段 2 裁决）

生成方式：主导 AI + 7 个并行子代理，按第 2 节的方法提示词执行；全部检索日志见第 3 节。
产出仓库：<https://github.com/BallCard/thinking-prompt-lab>

> **本文件是生成物**：由 `prompts/50-design-research.md`、七个 `research/0*.md`、`docs/clause-decisions.md` 与子代理会话日志拼接而成（嵌入内容的标题已降一级）。要修改内容请改源文件后重新生成，不要直接编辑本文件。
一句话目标：设计一组提示词，让 AI 陪用户（大学生 / 非专业成年人）就**社会议题**与**人生选择**做深度思考。做法是**先检索"哪些方法真能提升思考质量"，再把证据为强 / 中的机制翻译成可执行、可检查的提示词条款**。

---

## 0. 给验证者的任务说明（请先读这一节）

你要核验的不是文字质量，而是**这套证据与结论能不能站住**。请独立检索，不要复述本文档内容。

### 0.1 请逐项核查

1. **引用真实性**：抽查至少 12 条引用（优先标为"强 / 中"的），核对其是否存在、标题 / 年份 / 结论是否被准确转述。查不到就写"查不到"，**不要补一个相似的来源**。
2. **强度分级是否恰当**：指出应当降级（强→中 / 弱）或升级的具体条目及理由。
3. **结论是否超出证据**：逐条指出。重点看两类越界：把"实验室短期效应"当成"长期能力提升"；把"教育场景（学生 / 课程成绩）"外推到"成人真实决策"。
4. **遗漏的重要证据**：你检索到的、与本包结论冲突或本包未覆盖的高质量 meta 分析 / RCT（附来源）。
5. **内部矛盾**：本包自相矛盾之处（例如第 4 节流域 3、4 反复要求"必须闭环到反馈"，而流域 6 又承认"提示词条款本身从未被实验检验"）。
6. **条款可执行性**：第 5 节的条款逐条判断是否"可执行、可检查"；指出其中不可检查的表述。
7. **判定链是否断裂**：从"某干预在实验中有 g≈0.2–0.5"到"写进提示词能提升用户思考"，中间缺了哪些必要环节（提示服从性、剂量、用户动机、测量效度等）。
8. **反面是否覆盖**：本包是否只呈现了支持方？指出缺席的关键反方立场。

### 0.2 输出格式（请严格遵守）

- **表 A**：`核查项 | 你的结论 | 依据（来源 + URL + 日期） | 严重程度（高 / 中 / 低）`
- **表 B**（证据强度修正）：`条目 | 原分级 | 你建议的分级 | 理由 | 来源`
- **无法核查的部分**：明确列出，不要用推测填补
- **最严重的 3 个问题**：各附一句"如果属实，会怎样改变这套提示词"
- **建议补充的 5 条检索式**

### 0.3 约束

- 不得编造来源；无法核实的条目标"无法核实"
- 区分**事实错误**与**判断分歧**（例如你认为某 meta 分析的纳入标准有问题，属后者）
- 不要重写这份文档，只做核查

### 0.4 本包已知弱点（请把它们当作输入，而不是需要你去发现的缺陷）

- 子代理运行环境受代理与 SSRF 限制，**多数全文无法抓取**，部分效应量取自摘要页
- 关键引用中只有 3 条经主导二次核实（见第 6 节），另有 4 条为未同行评议的预印本 / 技术报告
- 子代理与验证者同为 LLM，存在**共同的引用生成风险**（同一类错误可能被二次确认）
- 证据表测的是"干预在受控研究中的效果"，**没有**"提示词条款能提升用户长期思考能力"的直接实验
- 文献以英文为主，中文语境下的适用性未评估
- 证据分级由 LLM 判定，四档（强 / 中 / 弱 / 已否定）之间无量化映射

---

## 1. 方法与流程（可复现）

| 步骤 | 做法 |
| --- | --- |
| 1.1 定方法 | 先写一份"元层"检索提示词（第 2 节），规定流域清单、证据分级定义、反方检索要求、输出模板 |
| 1.2 拆流域 | 拆成 7 个流域：提问技术、论证与系统、决策与校准、反思与元认知、知识组织、AI 对话行为、伪科学核查 |
| 1.3 并行检索 | 每个流域交给一个独立子代理，用同一份硬性要求（附 URL、必做反方检索、区分短期 / 长期、给可落地条款草案）；原始提示词与全部检索式见第 3 节 |
| 1.4 归档 | 7 份证据表原文见第 4 节；每份含证据表、最重要的结论、条款草案、可自查检索式、未找到证据项 |
| 1.5 裁决 | 把证据逐条对照到现行条款与候选条款上，输出"保留 / 修正 / 删除 / 新增"，见第 5 节 |
| 1.6 抽查 | 主导对 3 条决定性引用做了二次核实，见第 6 节 |

证据分级定义（全包统一）：

| 分级 | 含义 |
| --- | --- |
| 强 | 多项 RCT 或系统综述 / meta 分析结论一致 |
| 中 | 单项实验，或结果混杂 |
| 弱 | 理论推导、专家意见、实践共识 |
| 已否定 | 有明确反证 |

---

## 2. 方法提示词（原文，用于指挥整个检索）

> 源文件：`prompts/50-design-research.md`

## 设计方法论检索模块（元层提示词）

你要检索的对象不是社会议题，而是"**如何设计一个促进人深度思考的提示词 / 对话流程**"这一问题的方法论。这不是科普任务：每条结论最终都要能翻译成可以直接写进提示词的条款，凡是不能落地的内容一律不要输出。

### 我的目标

我要设计一套 skill，让 AI 陪我就社会议题与人生选择做深度思考。我需要知道：**哪些提问方式、分析框架与干预机制，有证据表明能真正提升人的思考质量；哪些只是流行说法。**

最终产物：一份「方法 → 机制 → 证据强度 → 可直接写进提示词的条款」的映射表。

### 我的约束与现状

使用者与时间预算：**【例如：非专业成年人，单个议题能投入 1–2 小时】**

我已经在用的东西（不需要重复推荐，只需告诉我是否有证据支持、是否需要修正）：结构化分层输出、事实/推论/价值三分、来源分级与原文片段、最强反方论证、深度分档 L1–L3、收尾追问清单。

我不想加的东西：需要长期训练才能产生效果的方法、依赖我额外记录大量数据的机制、会让对话变成填表格的流程。

### 第一步：先给研究计划（等我确认后再执行）

1. 把我的目标改写成 5–7 条可检索的研究问题，并指出其中哪些是事实问题、哪些其实是价值问题
2. 针对下面的流域清单，说明每个流域要回答什么；可以增删流域，但必须说明理由
3. 说明证据不足时你打算怎么处理（宁可写"证据不足"，不要用观点或经验填充）

**拟覆盖的流域：**

- **提问技术**：苏格拉底式提问（elenchus / 苏格拉底研讨）、认知冲突、追问与脚手架（scaffolding）、反例与边界情形、探究式学习
- **论证与结构**：Toulmin 论证模型、论证图（argument mapping）对推理质量的效果、因果分层、系统思维与因果回路图、多视角换位
- **偏差与决策干预**：premortem（事前验尸）、consider-the-opposite、参考类预测、基础比率、决策日志、可逆与不可逆决策分类
- **元认知与校准**：置信度评分与校准训练（Brier 分数）、预测记录、区分"知道"与"不确定"、过度自信的干预效果
- **自我反思机制**：结构化复盘、自我抽离（第三人称自我对话）、书面表达与思考质量的关系、价值澄清方法（如 ACT 中的价值澄清）
- **跨学科知识组织**：概念地图、专家与新手的知识组织差异、精加工与检索练习、知识迁移、费曼式复述、多学科视角如何避免"什么都沾一点"
- **AI 对话层**：AI 迎合（sycophancy）的实证研究与缓解手段、什么条件下 AI 应当拒绝先给答案、长期依赖 AI 对独立思考的影响（包括削弱效应的证据）

### 第二步：检索要求

- 中英双语检索式，每个流域 3–5 条，总计不少于 20 条，并注明哪几条实际返回了有用结果、哪几条没有（检索式构造与限定符用法参照 `docs/evidence-standards.md`）
- 优先第一、二级来源：系统综述、meta 分析、随机对照实验、同行评议综述、权威机构指南。三手来源（自媒体、畅销书、公众号、课程宣传）只能用来发现问题，不能用来支撑结论
- **必须做反方检索**：每个流域都要搜"无效 / 无效果 / 争议 / 复现失败 / 批评 / 过度宣传"等方向。已知存在争议的做法要单独列出，例如学习风格（learning styles）理论、脑力训练类游戏、成长型思维的部分复现问题
- 每条结论给出：`来源名称 · 日期 · 链接` + 不超过 30 字的原文片段。只有一个来源就标注"单一来源"；找不到就写"未找到证据"

### 第三步：输出格式（按此顺序，分批交付）

#### 1. 一句话结论
哪些机制证据最强，哪些属于流行但缺乏证据。

#### 2. 证据强度表

| 方法 | 机制（为什么可能有用） | 证据强度 | 关键研究 / 来源 | 适用条件 | 局限与反证 |
| --- | --- | --- | --- | --- | --- |

证据强度分级固定为：`强（多项 RCT 或系统综述结论一致）`、`中（单项实验或结果混杂）`、`弱（理论推导、专家意见、实践共识）`、`存疑或已被否定`。

#### 3. 落地条款草案（本模块的核心产出）
把上表中证据为**强**或**中**的方法，逐条翻译成可直接粘贴进提示词的条款。每条包含：

- **条款原文**：不超过 2 行，必须可执行、可检查
- **机制**：它靠什么起作用，预期改变什么
- **生效观察点**：我怎么判断它真的起作用了（而不是输出变长而已）
- **失效条件**：什么情况下这条会变成形式主义

禁止出现"要深刻""要全面""多角度思考"这类不可检查的表述。

#### 4. 伪科学黑名单
看起来与"促进思考"相关、但证据不支持或已被否定的做法，写清不能采用的原因。同时列出**被过度宣传但部分有效**的做法，说明有效的那一部分究竟是什么。

#### 5. 争议地图
研究者之间的分歧点，以及分歧性质（数据不同 / 方法不同 / 价值前提不同）。

#### 6. 证据缺口
现有研究无法回答、只能靠实践试错的部分。明确说明我该怎么设计小实验来验证。

#### 7. 优先级建议
按"实现成本 / 预期收益"排序，指出哪些先试、哪些可以放弃，并说明放弃的理由。

#### 8. 对现有框架的改造建议
针对我正在使用的五件事（结构化分层、三分法、最强反方、深度分档、追问清单），逐项说明：有证据支持 / 需要修正 / 建议删除，并给出修正后的表述。

#### 9. 下一步检索式
给我 5 条可以自己搜的检索式，说明各自想验证什么。

### 反幻觉与自我检查

- 不得编造研究名称、作者、期刊、年份、数据、链接；无法确认就写"未能核实"
- 严格区分"某研究声称 X"与"X 已被证实"
- 不要把相关关系写成因果：尤其是"使用某方法的人思考质量更高"这类自选样本研究，必须指出选择效应
- 不要把实验室条件下的短期效应（几十分钟的干预）说成长期能力提升
- 某流域证据确实稀薄时直说，不要为了结构完整而注水
- 不要推荐需要付费课程、专有测评或无法核查的资料

### 输出节奏

先只输出研究计划与检索式清单，等我确认后再分批交付：**先证据表 → 我确认后给条款草案 → 最后给改造建议与优先级**。每批不超过 2000 字。


---

## 3. 子代理提示词与检索日志（原始记录）

## 检索日志与子代理提示词（原始记录）

> 由子代理会话记录（JSONL）离线解析生成，未人工改写。工具调用按时间顺序列出；每个子代理开头的"原始提示词"即主导发给它的完整指令。


---

### 1 提问技术

- 子代理名：`research-questioning`　会话 id：`02162b87-440a-4d3`
- 工具调用：42 次（其中 web_search 检索式 18 条、fetch_content 2 个 URL）
- 最终报告字符数：3349

#### 原始提示词（完整）

```text
你在为一个中文提示词工具箱做**文献与证据检索**（不要写代码、不要改文件、只做研究并返回报告）。

背景：工具箱的用途是让 AI 陪用户（大学生/非专业成年人，单个议题能投入 1–2 小时）就社会议题和人生选择做深度思考。设计约束是输出必须可检查（区分事实/推论/价值、来源分级、标注不确定性），而不是空泛地要求"要深刻、要多角度"。

你的任务：只研究【提问技术】这一个流域，回答"哪些提问方式有证据表明能真正提升人的推理质量或判断质量，哪些只是流行说法"。

需要覆盖（可增删，但说明理由）：
- 苏格拉底式提问 / elenchus / 苏格拉底研讨（Socratic seminar）在教学与成人推理中的效果
- 探究式学习（inquiry-based learning）与引导式探究的对比证据
- 认知冲突（cognitive conflict）与概念转变（conceptual change）
- 脚手架式追问（scaffolding）、追问的深度层级、Bloom 分类学相关提问对高阶思维的影响
- 反例法、边界情形提问、自我解释（self-explanation）与自我提问（self-questioning）
- "先让学生给出答案再纠正" vs "直接给答案"对学习与推理的影响

硬性要求：
1. 优先系统综述、meta 分析、随机对照实验、同行评议综述。每个关键结论必须附上你**实际检索到**的 URL；不得编造标题、作者、期刊、年份、链接。找不到证据就写"未找到证据"。
2. 必须主动检索反面方向：无效、无显著效果、争议、复现失败、被过度宣传（例如 Bloom 分类学的实证支持强度、学习风格类"按提问风格匹配学习者"的说法）。
3. 严格区分：实验室短期效应（几十分钟干预）vs 长期能力提升；相关 vs 因果；自选样本研究的偏差。
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
    - `Socratic questioning meta-analysis effect on critical thinking`
    - `Socratic seminar meta-analysis student outcomes randomized`
    - `elenchus Socratic method empirical evidence critical thinking effect`
  - web_search  （numResults=8, workflow=none）
    - `inquiry-based learning meta-analysis effect size Furtak 2012`
    - `guided inquiry vs unguided discovery learning meta-analysis Lazonder Harmsen`
    - `Alfieri 2011 does discovery-based instruction enhance learning meta-analysis`
  - web_search  （provider=['openai', 'brave'], numResults=8, workflow=none）
    - `Socratic questioning meta-analysis critical thinking effect size`
    - `Socratic seminar meta-analysis student outcomes`
  - web_search  （provider=['openai', 'brave'], numResults=8, workflow=none）
    - `inquiry-based learning meta-analysis effect size Furtak 2012 review of educational research`
    - `Lazonder Harmsen meta-analysis guided inquiry discovery learning 2016`
  - web_search  （provider=["searxng", "duckduckgo"], numResults=5, workflow=none）
    - `Socratic questioning meta-analysis critical thinking test`
  - web_search  （provider=["tavily", "firecrawl", "jina"], numResults=5, workflow=none）
    - `inquiry based learning meta-analysis effect size Furtak`
  - web_search  （provider=searxng, numResults=6, workflow=none）
    - `Socratic questioning meta-analysis critical thinking effect`
  - web_search  （provider=tavily, numResults=6, workflow=none）
    - `inquiry based learning meta-analysis effect size Furtak 2012 Review of Educational Research`
  - web_search  （provider=duckduckgo, numResults=6, workflow=none）
    - `Socratic questioning meta-analysis critical thinking effect`
  - web_search  （provider=firecrawl, numResults=6, workflow=none）
    - `Furtak 2012 meta-analysis inquiry-based science teaching effect size`
  - web_search  （provider=jina, numResults=6, workflow=none）
    - `self-explanation meta-analysis Bisra 2018 learning`
  - web_search  （provider=perplexity, numResults=6, workflow=none）
    - `Socratic questioning meta-analysis critical thinking effect size`
  - bash: `ls -la "C:/Users/12855/.pi/agent/" 2>/dev/null | head -40; echo "---"; cat "C:/Users/12855/.pi/agent/web-search.json" 2>/dev/null | head -60`
  - fetch_content
    - https://journals.sagepub.com/doi/10.3102/0034654312475400
    - https://pubmed.ncbi.nlm.nih.gov/?term=socratic+questioning+meta-analysis
  - bash: `curl -sL -m 25 -A "Mozilla/5.0" "https://api.crossref.org/works?query.bibliographic=socratic+questioning+meta-analysis+critical+thinking&rows=5&select=title,author,container-title,issued,DOI,type" | h`
  - bash: `which jq python python3 node 2>/dev/null; echo "---"; curl -s -m 20 "https://api.openalex.org/works?search=socratic%20questioning%20meta-analysis%20critical%20thinking&per-page=5" | head -c 400`
  - bash: `cat > /tmp/oa.py <<'EOF' import sys,json,urllib.request,urllib.parse def q(query,extra=""):     url="https://api.openalex.org/works?search="+urllib.parse.quote(query)+"&per-page=8"+extra     r=json.lo`
  - bash: `cat > /tmp/oa2.py <<'EOF' import sys,json,urllib.request,urllib.parse def q(query):     url="https://api.openalex.org/works?search="+urllib.parse.quote(query)+"&per-page=8"     r=json.load(urllib.requ`
  - bash: `cat > /tmp/oa.py <<'EOF' import sys,json,ssl,urllib.request,urllib.parse ctx=ssl._create_unverified_context() def q(query):     url="https://api.openalex.org/works?per-page=8&search="+urllib.parse.quo`
  - bash: `cat > /tmp/oa2.py <<'EOF' import sys,json,ssl,urllib.request,urllib.parse ctx=ssl._create_unverified_context() def q(query):     url="https://api.openalex.org/works?per-page=8&search="+urllib.parse.qu`
  - bash: `python3 /tmp/oa.py "cognitive conflict strategy conceptual change review" "refutation text meta-analysis conceptual change" "scaffolding meta-analysis Belland 2017" "Bloom taxonomy empirical validatio`
  - bash: `python3 /tmp/oa2.py "self-explanation meta-analysis learning Bisra" "self-questioning strategy instruction review Rosenshine" "pretesting prequestions meta-analysis learning" "productive failure meta-`
  - bash: `python3 /tmp/oa.py "inducing self-explanation meta-analysis Bisra" "When problem solving followed by instruction works productive failure review of educational research" "learning styles meshing hypot`
  - bash: `python3 /tmp/oa2.py "higher cognitive questions versus lower cognitive questions meta-analysis achievement" "wait time teacher questioning student achievement review" "Bloom taxonomy criticism empiric`
  - bash: `cat > /tmp/oq.py <<'EOF' import sys,json,ssl,urllib.request,urllib.parse,textwrap ctx=ssl._create_unverified_context() def inv2abs(inv):     if not inv: return ""     pos={}     for w,ps in inv.items(`
  - bash: `cat > /tmp/oq2.py <<'EOF' import sys,json,ssl,urllib.request,urllib.parse ctx=ssl._create_unverified_context() def inv2abs(inv):     if not inv: return ""     pos={}     for w,ps in inv.items():      `
  - bash: `python3 /tmp/oq.py "inducing self-explanation meta-analysis" "productive failure meta-analysis problem solving prior to instruction" "levels-of-processing analysis of Bloom taxonomy" "meta-analysis ex`
  - bash: `python3 /tmp/oq2.py "meta-analysis" "wait time higher cognitive level learning" "Socratic questioning" "dialogic teaching" 2>&1 | head -100`
  - bash: `export PYTHONIOENCODING=utf-8 cat > /tmp/ob.py <<'EOF' import sys,json,ssl,urllib.request,urllib.parse ctx=ssl._create_unverified_context() def inv2abs(inv):     if not inv: return ""     pos={}     f`
  - bash: `export PYTHONIOENCODING=utf-8 python3 /tmp/ob.py "critical thinking instruction meta-analysis strategies for teaching" "debiasing decision making single training intervention" "transfer of critical th`
  - bash: `export PYTHONIOENCODING=utf-8 cat > /tmp/odos.py <<'EOF' import sys,json,ssl,urllib.request ctx=ssl._create_unverified_context() def inv2abs(inv):     if not inv: return ""     pos={}     for w,ps in `
  - bash: `export PYTHONIOENCODING=utf-8 python3 /tmp/ob.py "learning from errors hypercorrection" "improving students learning effective learning techniques" "consider the opposite debiasing" "Socratic method s`
  - bash: `export PYTHONIOENCODING=utf-8 cat > /tmp/oe.py <<'EOF' import sys,json,ssl,urllib.request,urllib.parse ctx=ssl._create_unverified_context() def epmc(q):     url="https://www.ebi.ac.uk/europepmc/webser`
  - bash: `export PYTHONIOENCODING=utf-8 python3 /tmp/ob.py "meta-analysis teacher questioning behavior cognitive" "pretesting versus posttesting errorful generation retrieval practice" "evidence-based higher ed`
  - bash: `export PYTHONIOENCODING=utf-8 cat > /tmp/s2.py <<'EOF' import sys,json,ssl,urllib.request,urllib.parse ctx=ssl._create_unverified_context() for d in sys.argv[1:]:     try:         u="https://api.seman`
  - bash: `export PYTHONIOENCODING=utf-8 python3 /tmp/ob.py "levels of processing Bloom taxonomy Kunen" "self-explanation prior knowledge moderation" "cognitive conflict limitation conceptual change failure" 2>&`
  - bash: `export PYTHONIOENCODING=utf-8 python3 /tmp/s2.py 10.1146/annurev-psych-010416-044022 10.1037/a0037478 10.3389/fpsyg.2020.00164 10.1007/s10648-023-09814-5 10.1002/tea.21887 2>&1 | head -60`
  - bash: `curl -sL -m 30 -A "Mozilla/5.0 (Windows NT 10.0; Win64; x64)" "https://link.springer.com/article/10.1007/s10648-018-9434-x" | python3 -c " import sys,re,html t=sys.stdin.read() t=re.sub(r'<script.*?</`
  - bash: `curl -sL -m 30 -A "Mozilla/5.0" "https://link.springer.com/article/10.1007/s10648-021-09656-z" | python3 -c " import sys,re,html t=sys.stdin.read(); t=re.sub(r'<script.*?</script>','',t,flags=re.S); t`
  - bash: `export PYTHONIOENCODING=utf-8 python3 /tmp/ob.py "Socratic seminar critical thinking empirical study" "Bloom taxonomy critique higher order thinking" 2>&1 | head -40`
  - bash: `export PYTHONIOENCODING=utf-8 python3 /tmp/s2.py 10.1007/s11109-018-9443-y 10.1037/0022-0663.73.2.202 10.1007/s11423-018-9579-9 10.1177/1529100612453266 2>&1 | head -30 echo "==== crossref check ===="`
  - bash: `export PYTHONIOENCODING=utf-8 cat > /tmp/osort.py <<'EOF' import sys,json,ssl,urllib.request,urllib.parse ctx=ssl._create_unverified_context() def inv2abs(inv):     if not inv: return ""     pos={}   `


---

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

### 4 自我反思与元认知

- 子代理名：`research-reflection`　会话 id：`1d814bd8-5eaf-4cb`
- 工具调用：13 次（其中 web_search 检索式 29 条、fetch_content 2 个 URL）
- 最终报告字符数：4051

#### 原始提示词（完整）

```text
你在为一个中文提示词工具箱做**文献与证据检索**（不要写代码、不要改文件、只做研究并返回报告）。

背景：工具箱的用途是让 AI 陪用户（大学生/非专业成年人）就社会议题和人生选择做深度思考，包含"人生规划"模块，涉及自我认知、价值排序、情绪与状态判断。设计约束是输出必须可检查，不能用安慰代替分析。

你的任务：只研究【自我反思与元认知干预】这一个流域，回答"哪些反思/元认知做法有证据表明能改善判断与状态，哪些只是流行说法"。注意：这一领域心理机制研究较多、但容易过度宣称，请特别标注证据强度。

需要覆盖（可增删，但说明理由）：
- 结构化复盘 / 引导式反思（guided reflection、after-action review、debriefing）：对表现改进的证据，以及"结构化"是否比自由反思更有效
- 自我抽离/第三人称自我对话（self-distancing, Kross 等人）：对情绪调节与推理的影响，是否有复现证据与边界条件
- 表达性写作（expressive writing, Pennebaker）：对情绪与认知的作用、效应量与适用条件
- 元认知提示（metacognitive prompts，如"你对自己的判断有多大信心""你怎么知道自己知道"）对学习与判断校准的效果
- 价值澄清（values clarification，含 ACT 的 values work）：对决策满意度、动机与心理健康的证据
- 反刍（rumination）与反思的区别：什么形式的自我审视反而有害
- 目标设定与执行意图（implementation intentions, Gollwitzer）：对行动转化的效应量
- 情绪状态对判断的影响（如焦虑、疲劳下的决策质量），以及"先处理状态再处理问题"这一建议的证据

硬性要求：
1. 优先系统综述、meta 分析、随机对照实验、同行评议综述。每个关键结论必须附上你**实际检索到**的 URL；不得编造标题、作者、期刊、年份、链接。找不到证据就写"未找到证据"。
2. 必须主动检索反面方向：表达性写作效果是否被夸大、self-distancing 的复现情况、guided reflection 是否只是"感觉良好"而无行为改变、正念类干预的效应量争议。
3. 严格区分：主观感受改善 vs 客观判断改善；短期 vs 长期；相关 vs 因果；自选样本（如自愿参加冥想课程的人）的偏差。
4. 输出中文，不超过 900 字，结构如下：

| 方法 | 机制（为什么可能有用） | 证据强度（强/中/弱/已否定 + 一句话依据） | 关键来源（标题 + URL） | 适用条件 | 局限与反证 |
| --- | --- | --- | --- | --- | --- |

然后再给：
- 一条最重要的结论
- 3–5 条"可直接写进提示词的条款草案"（每条 ≤2 行，必须可执行、可检查；禁止"要真诚面对自己"这类表述）
- 3 条我可以自己继续检索验证的检索式

宁少而准，不要泛泛而谈。
```

#### 检索日志（按时间顺序）

  - web_search  （numResults=8）
    - `guided reflection after-action review meta-analysis effect on performance`
    - `self-distancing third-person self-talk Kross replication emotion regulation evidence`
    - `expressive writing meta-analysis effect size Pennebaker emotional writing cognitive outcomes`
    - `implementation intentions meta-analysis Gollwitzer effect size goal attainment`
  - web_search  （numResults=8）
    - `metacognitive prompts confidence calibration judgment accuracy randomized experiment`
    - `values clarification intervention meta-analysis wellbeing motivation ACT values`
    - `rumination vs reflection depression meta-analysis harmful self-focus`
    - `mindfulness meditation effect size controversy replication publication bias meta-analysis`
  - web_search  （provider=brave, numResults=8）
    - `Kross self-distancing third-person self-talk replication emotion regulation study`
    - `implementation intentions meta-analysis Gollwitzer effect size d goal attainment`
    - `values clarification intervention randomized trial wellbeing effects meta-analysis`
    - `rumination reflection meta-analysis depression brooding reflection distinct`
  - web_search  （provider=brave, numResults=8）
    - `expressive writing overrated criticism failed to replicate effects`
    - `anxiety effect on decision making quality experiment stress risk judgment`
    - `guided reflection journaling no behavior change criticism self-help`
    - `fatigue sleep deprivation decision making quality evidence review`
  - web_search  （numResults=8）
    - `Kross self-distancing third-person self-talk replication emotion regulation`
    - `implementation intentions meta-analysis effect size Gollwitzer goal attainment`
  - web_search  （numResults=8）
    - `rumination versus reflection meta-analysis depression brooding reflection distinct predictors`
    - `values clarification intervention effects wellbeing randomized controlled trial meta-analysis`
  - web_search  （numResults=8）
    - `expressive writing criticism overrated failed replication null effects`
    - `anxiety effects on decision making and judgment meta-analysis review`
    - `self-distancing boundary conditions high emotional intensity failed to reduce emotion`
  - web_search  （numResults=6）
    - `debriefing structure facilitation moderator meta-analysis Tannenbaum Cerasoli 25% improvement`
    - `ego depletion replication failure multilab registered replication report`
    - `reflection intervention well-being feels good but no behavior change evidence`
  - fetch_content
    - https://pubmed.ncbi.nlm.nih.gov/36256910/
    - https://eprints.whiterose.ac.uk/id/eprint/178930/1/Clarifying%20Values%20An%20Updated%20and%20Expanded%20Systematic%20Review%20and%20Meta-Analysis.pdf
  - web_search  （numResults=6）
    - `Stacey clarifying values updated systematic review meta-analysis findings decision quality no effect`
    - `affect labeling reduces emotional reactivity evidence Lieberman`
    - `Influence of Fear on Risk Taking meta-analysis findings`
  - get_search_content: {"findText": ["effect size", "g =", "d =", "small"], "url": "https://par.nsf.gov/servlets/purl/10174583", "responseId": "mu7w6wbe7i3isz"}
  - get_search_content: {"findText": ["0.79", "moderator", "structure", "facilitat"], "responseId": "mu7w61h4m9j34z", "queryIndex": 0}
  - get_search_content: {"findText": ["effect size", "risk taking", "small", "moderat"], "queryIndex": 2, "responseId": "mu7w6wbe7i3isz"}


---

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

### 7 伪科学黑名单（跨域核查）

- 子代理名：`research-debunked`　会话 id：`fb4a6241-ad21-4eb`
- 工具调用：16 次（其中 web_search 检索式 42 条、fetch_content 0 个 URL）
- 最终报告字符数：4038

#### 原始提示词（完整）

```text
你在为一个中文提示词工具箱做**证据核查**（不要写代码、不要改文件、只做研究并返回报告）。

背景：工具箱用于"促进深度思考"，涉及提问方法、学习法、决策法、自我反思、跨学科知识。我要列一份"伪科学黑名单"，防止把流行但站不住的做法写进提示词。用户是大学生/非专业成年人，容易在短视频和公众号上遇到这类说法。

你的任务：核查下面每一项"是否真的有实证支持"，并给出**证据强度分级**与**至少一个可查来源 URL**。特别注意：要区分"完全无效/伪科学"与"部分有效但被夸大"，这两类处理方式不同。

待核查清单：
1. 学习风格（learning styles / VAK，视觉型听觉型动觉型）匹配教学
2. 脑力训练游戏（brain training）提升智力或记忆力
3. 成长型思维（growth mindset）干预的效果与复现争议（含 2019 年国家级大样本实验的结论）
4. 左右脑分工型人格说法
5. 一万小时定律（Ericsson 刻意练习）被简化传播后的准确性，及 Macnamara 等人的 meta 分析结论
6. MBTI 等类型学人格测试用于自我认知与职业选择
7. 填鸭式/记忆术（如记忆宫殿）对"思考能力"的提升
8. "多巴胺戒断/dopamine detox"类说法
9. "批判性思维培训能提升智力"的迁移性主张
10. 阅读方法类流行说法：如"速读（speed reading）能保持理解"、"照相记忆"
11. 情绪与理性二分的说法（"要完全排除情绪才能理性决策"），请给出情绪在决策中作用的研究（如 Damasio 的躯体标记假说）来说明这种二分是否站得住
12. "思考必须靠写作/必须手写笔记"这类笔记媒介决定论说法（对照手写 vs 打字的笔记研究，含 Mueller & Oppenheimer 的研究及其后续批评与复现情况）

硬性要求：
1. 每个结论必须附上你**实际检索到**的 URL（综述、meta 分析或权威科普来源均可，但要标明类型）；不得编造标题、作者、期刊、年份、链接。找不到证据就写"未找到证据"。
2. 分级只用四档：`已被否定（有明确反证）`、`证据不足（无法支持宣称）`、`部分有效但被夸大（说明有效的那部分）`、`有较好支持`。
3. 明确标注每一项"过度宣称的具体点是什么"——例如证据支持"环境可变"但不支持"匹配学习风格能提高成绩"。
4. 输出中文，不超过 900 字，结构如下：

| 说法 | 分级 | 证据支持的部分 | 被夸大或错误的部分 | 关键来源（标题 + URL） | 提示词中应如何表述 |
| --- | --- | --- | --- | --- | --- |

然后再给：
- 3 条"最容易被人当真理、最需要警惕"的说法，以及为什么它们诱人
- 3 条我不能仅凭直觉判断、需要查证时应该搜什么（给你要用的检索式）

宁少而准。如果某一项你检索不到可靠来源，就写"未找到证据"，不要臆断。
```

#### 检索日志（按时间顺序）

  - web_search  （numResults=6, workflow=none）
    - `learning styles VAK matching instruction evidence Pashler Newton meta-analysis`
    - `brain training far transfer meta-analysis Simons Owen Melby-Lervag cognitive training`
    - `growth mindset National Study of Learning Mindsets 2019 Nature replication Sisk meta-analysis`
  - web_search  （numResults=6, workflow=none）
    - `left brain right brain personality myth Nielsen 2013 resting state functional connectivity`
    - `Macnamara deliberate practice meta-analysis 10000 hour rule criticism Ericsson response`
    - `MBTI validity test-retest reliability criticism Stein Swan 2019`
  - web_search  （numResults=6, workflow=none）
    - `memory palace mnemonic training reshape brain networks Dresler 2017 transfer general cognition`
    - `dopamine detox dopamine fasting scientific evidence critique`
    - `critical thinking instruction meta-analysis Abrami 2015 transfer to intelligence`
  - web_search  （numResults=6, workflow=none）
    - `speed reading comprehension Rayner 2016 review photoreading evidence no`
    - `somatic marker hypothesis Maia McClelland reexamination evidence criticism Damasio`
    - `handwriting versus typing notes replication Morehead 2019 Urry meta-analysis Mueller Oppenheimer`
  - web_search  （provider=brave, numResults=6, workflow=none）
    - `Yaeger 2019 Nature national study of learning mindsets growth mindset randomized trial effect size`
    - `Sisk 2018 meta-analysis growth mindset to succeed weak effects`
    - `left brain right brain personality myth neuroscience evidence Nielsen 2013`
  - web_search  （provider=brave, numResults=6, workflow=none）
    - `MBTI Myers-Briggs validity reliability scientific critique psychologists`
    - `dopamine detox fasting scientific evidence no support`
    - `Abrami 2015 meta-analysis critical thinking instruction strategies effect size`
  - web_search  （provider=brave, numResults=6, workflow=none）
    - `Rayner 2016 So much to read so little time speed reading comprehension review`
    - `emotional intelligence emotion decision making affect infusion reason dichotomy`
    - `photoreading evidence not supported speed reading claims debunked`
  - web_search  （provider=['tavily', 'searxng', 'duckduckgo'], numResults=6, workflow=none）
    - `Yeager 2019 Nature national study of learning mindsets growth mindset randomized trial effect size`
    - `Sisk 2018 meta-analysis growth mindset weak effects replication`
    - `left brain right brain myth Nielsen 2013 functional connectivity evidence`
  - web_search  （provider=jina, numResults=5, workflow=none）
    - `Yeager 2019 Nature national study of learning mindsets growth mindset randomized trial effect size`
  - web_search  （provider=firecrawl, numResults=5, workflow=none）
    - `Sisk 2018 meta-analysis growth mindset weak effects`
  - web_search  （provider=search1api, numResults=5, workflow=none）
    - `left brain right brain myth Nielsen 2013 functional connectivity`
  - web_search  （numResults=5, workflow=none）
    - `Sisk 2018 meta-analysis growth mindset weak effects Psychological Science`
    - `left brain right brain myth evidence resting state connectivity`
    - `MBTI Myers-Briggs validity reliability scientific critique`
  - web_search  （numResults=5, workflow=none）
    - `Yeager 2019 Nature A national experiment reveals where a growth mindset improves achievement`
    - `dopamine detox fasting scientific evidence no support critique psychiatrist`
    - `Abrami 2015 meta-analysis instructional interventions critical thinking skills`
  - web_search  （numResults=5, workflow=none）
    - `Rayner 2016 So Much to Read So Little Time speed reading help review Psychological Science in the Public Interest`
    - `photoreading evidence no support speed reading claims`
    - `affect and decision making emotion integral not opposite Lerner Loewenstein`
  - web_search  （numResults=5, workflow=none）
    - `dopamine detox fasting scientific evidence not supported myth`
    - `Lerner Li Weber 2015 Emotion and Decision Making Annual Review of Psychology affect`
    - `Dunlosky 2013 Improving Students Learning With Effective Learning Techniques mnemonics utility`
  - web_search  （numResults=5, workflow=none）
    - `Macnamara Burgoyne 2023 growth mindset meta-analysis interventions small effects`
    - `critical thinking training far transfer intelligence IQ evidence limits`
    - `learning styles 2024 meta-analysis neuromyth methodological flaws reanalysis`


---

## 4. 七份证据表（原文）


### 流域 1：源文件 `research/01-questioning-techniques.md`

## 流域 1：提问技术

> 调研工具：[`prompts/50-design-research.md`](../prompts/50-design-research.md)　状态：已完成（2026）

检索路径：OpenAlex / Crossref / Semantic Scholar / Europe PMC + Springer 全文摘要验证；下列 URL 为已验证的 DOI 短链。

| 方法 | 机制 | 证据强度 | 关键来源 | 适用条件 | 局限与反证 |
| --- | --- | --- | --- | --- | --- |
| 苏格拉底式提问 / 研讨 | 逼出隐含前提、检验自相矛盾 | **弱—中**：**无独立 meta 分析**，多为小样本准实验；2023 综述为叙事性 | [doi:10.1207/s15389286ajde1903_4](https://doi.org/10.1207/s15389286ajde1903_4)；[doi:10.1186/s12909-023-04134-2](https://doi.org/10.1186/s12909-023-04134-2) | 用户已给出明确观点、可被追问一致性时 | 常与"讨论 / 讲授"混淆；测量多为自评或自编量表；**对高焦虑者可能抑制表达** |
| 引导式探究 vs 无引导 | 自主探究 + 外部支架 | **强（方向一致）**：Furtak 2012 平均 ES=0.50，教师引导比学生主导高约 0.40；Lazonder & Harmsen 2016（72 研究）引导对学习结果 d=0.50；Kirschner 2006 指出最小引导对新手失败 | [doi:10.3102/0034654312457206](https://doi.org/10.3102/0034654312457206)；[doi:10.3102/0034654315627366](https://doi.org/10.3102/0034654315627366)；[doi:10.1207/s15326985ep4102_1](https://doi.org/10.1207/s15326985ep4102_1) | 新手或低先验知识者**必须配结构化支架** | 效应异质性大；"引导"定义不统一；"探究优于讲授"依赖学科 |
| 认知冲突 / 概念转变 | 制造矛盾 → 重组概念 | **中，且被高估**：Limón 2001 批判性综述称多数研究缺对照、冲突本身不足以产生转变；2023 JRST meta g=1.10 明显偏大（218 研究，多为弱设计 / 即时后测） | [doi:10.1016/S0959-4752(00)00037-2](https://doi.org/10.1016/S0959-4752(00)00037-2)；[doi:10.1002/tea.21887](https://doi.org/10.1002/tea.21887) | 存在可理解的反证、用户信念未固化时 | 冲突常与直接讲授捆绑，无法分离；强信念下可能无效 |
| 反例 / 反驳文本 | 先陈述错误认知再直接驳斥 | **中—强（短期）**：随机效应 meta g=0.41（44 组，n=3869），跨情境稳健 | [doi:10.1007/s10648-021-09656-z](https://doi.org/10.1007/s10648-021-09656-z) | 有明确可反驳的错误前提时 | 证据集中在**即时后测**；长期保持与行为迁移证据稀少 |
| 脚手架 / 追问深度分级 | 临时支持 + 逐步撤除 | **中**：Belland 2017 RER 贝叶斯网络 meta（56 研究）报告跨人群强效应 | [doi:10.3102/0034654317723009](https://doi.org/10.3102/0034654317723009) | 任务复杂度高于当前能力时 | 该 meta 基于"前—后测"内设计，易高估；撤除（fading）时机证据弱 |
| Bloom 层级提问 | 更"高"层级问题 → 高阶思维 | **弱 / 被过度宣传**：层级本身缺实证（Kunen 1981 加工水平分析不支持其层级性）；Redfield & Rousseau 1981（20 研究）仅显示高阶问题占主导时课程成绩有增益 | [doi:10.1037/0022-0663.73.2.202](https://doi.org/10.1037/0022-0663.73.2.202)；[doi:10.3102/00346543051002237](https://doi.org/10.3102/00346543051002237) | 只能当"提问分类清单"用 | **不能当"思维深度阶梯"**；无 RCT 表明按层级设计提问可提升推理质量 |
| 自我解释 | 生成因果 / 概念联结 | **强（短期）**：Bisra 2018 meta g=0.55（64 份报告）；Dunlosky 2013 评为"中等效用" | [doi:10.1007/s10648-018-9434-x](https://doi.org/10.1007/s10648-018-9434-x)；[doi:10.1177/1529100612453266](https://doi.org/10.1177/1529100612453266) | 用户已有最低限度先验知识 | 存在**先验知识阈值**，过低时失效；多为即时测验 |
| 自我提问 / 生成问题 | 主动加工、监控理解 | **中**：Rosenshine 1996 综述中位 ES=0.36（标准测验）但 0.86（研究者自编测验）——差额本身即测量偏差信号 | [doi:10.3102/00346543066002181](https://doi.org/10.3102/00346543066002181) | 阅读 / 材料理解类任务 | 效应大半来自研究者自编测量，外部效度低 |
| 先答后纠 vs 直接给答案 | 生成错误 → 反馈后深度编码 | **中—强**：Sinha & Kapur 2021（53 研究 / 166 比较）PS-I g=0.36，校正发表偏差后 0.87（区间极宽）；Pan & Sana 2021；Metcalfe 2017 高信心错误更易被纠正 | [doi:10.3102/00346543211019105](https://doi.org/10.3102/00346543211019105)；[doi:10.1037/xap0000345](https://doi.org/10.1037/xap0000345)；[doi:10.1146/annurev-psych-010416-044022](https://doi.org/10.1146/annurev-psych-010416-044022) | **必须随后给出正确答案与解释** | 无反馈时几乎无效；对纯记忆内容、低龄学习者效应反转 |

### 已否定的流行说法（本流域）

- **按学习风格匹配提问 / 呈现方式**：Pashler 2008 系统检索未找到任何符合方法学要求的研究支持"匹配假设"；Rogowsky 2015 直接实验亦未发现匹配优势（[doi:10.1111/j.1539-6053.2009.01038.x](https://doi.org/10.1111/j.1539-6053.2009.01038.x)；[doi:10.1037/a0037478](https://doi.org/10.1037/a0037478)）
- **"考虑相反面"迁移有限**：实验室可降低过度自信（[doi:10.1037/0022-3514.69.6.1069](https://doi.org/10.1037/0022-3514.69.6.1069)），但 2017 系统综述显示迁移有限（[doi:10.1177/0272989X17716672](https://doi.org/10.1177/0272989X17716672)）

### 一条最重要的结论

十年证据一致指向同一个变量：**不是"问得多深"，而是"是否强制生成 + 是否紧跟具体反馈"。**

生成类干预（自我解释、先答后纠、反驳文本）有稳定的中等效应；而"苏格拉底式""高阶思维提问"这类**以提问形式命名的技术反而缺少可分离的因果证据**，且几乎全部证据是短期、学者自编测量的实验室效应。

### 可直接写进提示词的条款草案

1. 每个结论必须标注 `[事实|推论|价值]`，并给出理由的层级（经验数据 / 类比 / 原则）。
2. 用户回答后，**先让 AI 复述用户主张的最强版本并确认，再提出反驳**；不得跳过确认直接纠正。
3. 每次只提 1 个问题；提问前必须声明"此问题要检验的是哪条隐含前提"。
4. 引入反例时，必须写出该反例被证伪所需的条件，或标注"此反例未经检验"。
5. 输出末段列出：本次未解决项、AI 不确定项、以及用户未提供的可能相关信息。

### 可自行验证的检索式

1. `("Socratic questioning" OR "Socratic method") AND (meta-analysis OR "randomized controlled trial") AND "critical thinking"` — 在 ERIC / PsycINFO 验证是否存在可用的 meta 分析
2. `("self-explanation" OR "question generation") AND ("far transfer" OR "delayed posttest") AND (meta-analysis)` — 检验长期保持证据
3. `("conceptual conflict" OR "cognitive conflict") AND ("continued influence" OR backfire) AND review` — 检验冲突干预的反向证据

### 对项目的直接含义

- 用户点名想要的**苏格拉底式提问，恰好是本流域证据最弱的一类**（以形式命名、无可分离因果证据）——需要在设计上做出取舍
- 相反，**"先答后纠"（生成 → 反馈）有中—强证据**，而且它要求 AI **先让用户答，再给正确答案**——这与"信息不足就先不给结论"的现有条款直接冲突
- **对高焦虑者，追问式提问可能抑制表达** → 人生规划模块（议题本身带情绪）需要一条降级路径


### 流域 2：源文件 `research/02-argument-and-systems.md`

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


### 流域 3：源文件 `research/03-decision-and-calibration.md`

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


### 流域 4：源文件 `research/04-reflection-and-metacognition.md`

## 流域 4：自我反思与元认知干预

> 调研工具：[`prompts/50-design-research.md`](../prompts/50-design-research.md)　状态：已完成（2026）

覆盖说明：计划内 8 项全部保留；"情绪状态"一项并入"状态优先"建议一起评估，并补入"情绪效价"与"意志力耗竭"两个反证——后者是最常见的过度推论来源。

| 方法 | 机制 | 证据强度 | 关键来源 | 适用条件 | 局限与反证 |
| --- | --- | --- | --- | --- | --- |
| 结构化复盘 / debrief | 反思 + 讨论 + 目标设定三合一，把经验转为可迁移假设 | **中偏强（客观绩效）**：Tannenbaum & Cerasoli 2013，46 样本 N=2136，d=0.67（约 25% 提升）；Keiser & Arthur 2021，61 研究 / 107 个效应量，AAR 总体 d=0.79 | [Do Team and Individual Debriefs Enhance Performance?](https://journals.sagepub.com/doi/10.1177/0018720812448394)；[After-Action Review Meta-Analysis](https://doi.org/10.1037/apl0000821) | 有明确任务与可观测结果；最好有外部引导 | 多为团队 / 演习场景，非生活决策；"结构优于自由反思"来自调节变量分析（alignment、facilitation、structure），属间接证据 |
| 自我抽离 / 第三人称自我对话 | 像看他人一样看自己 → 心理距离，认知成本低 | **中（主观情绪，小效应）**：2022 meta 48 研究 / 102 效应量 g=−0.26 [−0.36,−0.15]；Murdoch 等三层 meta 25 实验 g=0.19 [0.05,0.33] | [Reflect on emotional events from an observer's perspective](https://pubmed.ncbi.nlm.nih.gov/36256910/)；[Distancing 分类学与 meta](https://pmc.ncbi.nlm.nih.gov/articles/PMC6326885/) | 针对具体压力事件、中等情绪强度 | 高强度情绪下效果不稳定（Verduyn 2021）；PTSD 样本中降低生理指标但不降低主观痛苦；抑郁严重度是调节变量。多为即时主观情绪，**不是判断质量** |
| 表达性写作 | 情绪语言化，降低抑制负担、形成连贯叙事 | **弱（被夸大）**：Frattaroli 2006 全量 meta 整体 r≈.075；Reinhold 2018 对抑郁无显著长期效应；Mogk 2006 剔除异常值后无效应 | [Frattaroli 2006](https://bpb-us-e2.wpmucdn.com/faculty.sites.uci.edu/dist/c/602/files/2019/08/Frattaroli-psych-bulletin-2006.pdf)；[抑郁症状 meta](https://doi.org/10.1111/cpsp.12224)；[追索不稳定效应](https://doi.org/10.3389/fpsyg.2023.1192595) | 一次性、具体事件、含"接纳"指令、投入度高 | Smyth 1998 的 d=0.47 未被后续更严格 meta 复现；Pennebaker 本人承认原始研究"严重欠功效"；健康 / 免疫宣称属外推 |
| 元认知提示（信心校准） | 强制生成预测并与结果比对 | **弱 / 混合**：独立提示常无效（提示组 n=51 vs 控制组 n=150 无收益）；仅"重复练习 + 反馈"显著提升校准 | [Limits of Metacognitive Prompts](https://doi.org/10.1515/edu-2022-0209)；[Monitoring Prompts 与信心偏差](https://doi.org/10.1026/0049-8637/a000279)；[练习 + 反馈研究](https://doi.org/10.3102/1438448) | 必须闭环到反馈 | 无反馈的"你有多自信"可能只增加负担；对真实生活判断的迁移未验证 |
| 价值澄清 | 让价值显性化，检验选项—价值一致性 | **中（指标窄）**：显性价值澄清降低价值不一致选择（RD=−0.04）与决策冲突（SMD=−0.20）；多准则分析优于其他方法 | [Clarifying Values: Updated Systematic Review](https://pmc.ncbi.nlm.nih.gov/articles/PMC8482297/) | 有明确候选选项的决策 | 效应小；结局是"与自报价值一致"而非"决策更好"；ACT 整体有效 ≠ values 模块单独有效 |
| 反刍 vs 反思 | 反刍＝只问"为什么 / 我哪里不好"而无行动闭合 | **强（相关 + 纵向）**：brooding 与焦虑抑郁关联最强，reflection 因子关联弱且不稳 | [Specificity of Rumination meta](https://doi.org/10.1111/cpsp.12037)；[反刍元认知模型 meta](https://doi.org/10.1007/s10608-021-10260-2) | 用于筛查有害的自我审视 | 多为相关 / 纵向非实验；RRS 双因子结构本身有争议 |
| 执行意图 if-then | 预先指定何时 / 何地 / 如何，把行动托管给环境线索 | **强（行为）**：Gollwitzer & Sheeran 2006，94 个独立检验 d≈0.65；2024 版 642 个独立检验 d 在 .27–.66 | [Implementation Intentions and Goal Achievement](https://doi.org/10.1016/s0065-2601(06)38002-1)；[The when and how of planning](https://doi.org/10.1080/10463283.2024.2334563) | 目标已定、障碍可预期 | 只解决"执行"，不解决"目标对不对"；多为短期行为指标 |
| 状态对判断 + "先处理状态" | 高唤醒 / 不确定下，状态改变风险偏好与加工方式 | **中（方向存在、幅度小且异质）**：压力损害不确定情境决策；但特质焦虑与风险承担相关仅 r=−0.07（80 个效应量） | [Effects of stress on decisions under uncertainty](https://doi.org/10.1037/bul0000060)；[Do Anxious People Take Fewer Risks?](https://doi.org/10.1002/bdm.70054) | 只作"状态会污染判断"的弱支持 | "意志力耗竭"解释已被否定：多实验室 RRR d=0.06 不显著（[链接](https://doi.org/10.1177/0956797621989733)） |

### 一条最重要的结论

本流域里唯一同时满足"客观指标 + 中等以上效应 + 独立复现"的只有两件事：**把意图转成 if-then 计划**，以及**有外部结构与反馈的复盘**。而被当作标配的**表达性写作效应被显著夸大**；**自我抽离**只是小效应，且限于主观情绪强度。

因此：**反思模块应定位为产出"可核验的下一步动作"，而不是产出情绪舒缓。**

### 可直接写进提示词的条款草案

1. 每次反思必须输出三项：可核验事实、预测值与实际值的差、一个 if-then 动作（何时 / 何处 / 做什么）。缺任一项即视为反思未完成。
2. 用户做自我判断时先记 0–100 信心值；获得真实反馈后再记一次并给出差值。**无反馈时不得使用"校准"一词。**
3. 若连续两轮只出现"为什么我这样 / 我是不是很差"且无行动项，立即中断，要求给出一个可执行动作或明确声明"本轮不处理"。
4. 面临选项抉择时，对每个选项分别打"价值一致性 0–10"与"事实依据强度 0–10"，并标出两者差距最大的选项。
5. 禁止用情绪改善作为判断改善的证据；每条状态结论必须标注为：主观感受 / 短期 / 行为或结果指标。

### 可自行验证的检索式

1. `("after-action review" OR debrief) AND ("free reflection" OR unstructured reflection) AND meta-analysis AND performance`
2. `"expressive writing" AND ("failed replication" OR "null effect") AND (moderator OR engagement) AND randomized`
3. `("self-distancing" OR "distanced self-talk") AND (preregistered replication OR boundary condition) AND "emotion regulation"`
4. `"metacognitive prompt" AND "calibration" AND feedback AND randomized controlled trial`

### 未找到证据

- 无反馈条件下，元认知提示能长期改善真实生活决策质量
- 价值澄清对心理健康结局的独立、长期效应


### 流域 5：源文件 `research/05-knowledge-organization.md`

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


### 流域 6：源文件 `research/06-ai-dialogue-effects.md`

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


### 流域 7：源文件 `research/07-debunked-practices.md`

## 流域 7：伪科学黑名单（跨域核查）

> 调研工具：[`prompts/50-design-research.md`](../prompts/50-design-research.md)　状态：已完成（2026）

分级四档：① 已被否定 ② 证据不足 ③ 部分有效但被夸大 ④ 有较好支持。类型标注：meta = 元分析，RCT = 随机实验，综述 = 系统 / 叙述综述，科普 = 权威机构科普。

| 说法 | 分级 | 证据支持的部分 | 被夸大 / 错误的部分 | 关键来源 | 提示词中应如何表述 |
| --- | --- | --- | --- | --- | --- |
| 1 学习风格（VAK）匹配 | ① 已被否定 | 人有多通道偏好；多样化呈现能提升参与度 | "视觉型 / 听觉型"不是稳定类型；**匹配风格不能提高成绩** | 综述 + meta：Pashler《Learning Styles: Concepts and Evidence》<https://journals.sagepub.com/doi/full/10.1111/j.1539-6053.2009.01038.x>；[2025 复评](https://link.springer.com/article/10.1007/s10648-025-10002-w) | 写"用多种表征方式讲解"，不写"按你的学习类型匹配" |
| 2 脑力训练游戏 | ① 已被否定（远迁移） | 训练任务本身变快（近迁移） | "提升智力 / 记忆力"——对智力与工作记忆能力无迁移 | meta：Simons《Do "Brain-Training" Programs Work?》<https://www.vumc.org/psychiatry/sites/default/files/GRED%20pdfs/GRED%20Nov%2020%20Do%20%E2%80%9CBrain-Training%E2%80%9D%20Programs%20Work.pdf>；[Melby-Lervåg 2016](https://pmc.ncbi.nlm.nih.gov/articles/PMC4968033/) | 只作娱乐或专注练习，不作能力提升承诺 |
| 3 成长型思维 | ③ 部分有效但被夸大 | 信念可塑、环境可变；对低成就 / 资源薄弱学生有小效应 | "人人提分、大效应稳定复现"——统计校正后效应≈0 | RCT：[Yeager 2019 Nature](https://www.nature.com/articles/s41586-019-1466-y)；meta：[Sisk 2018](https://journals.sagepub.com/doi/abs/10.1177/0956797617739704)、[Macnamara & Burgoyne 2023](https://doi.org/10.1037/bul0000352) | 讲"策略 + 过程反馈 + 归属感"，不承诺提分 |
| 4 左右脑人格 | ① 已被否定 | 语言 / 视空间功能确有偏侧化 | "左脑理性、右脑创意"的人格分类：个体层面无一致性网络偏侧 | 研究：[Nielsen 2013 PLOS ONE](https://journals.plos.org/plosone/article?id=10.1371%2Fjournal.pone.0071275) | 直接删除该说法 |
| 5 一万小时定律 | ③ 部分有效但被夸大 | 刻意练习是重要因素，反馈与任务质量关键 | "练满一万小时即成专家"；练习量解释的绩效方差有限（音乐 21%、体育 18% 等） | meta：[Macnamara 2014](https://doi.org/10.1177/0956797614535810)；[Ericsson 回应](https://journals.sagepub.com/doi/abs/10.1177/1745691616635600) | 改写为"有反馈的针对性练习 + 时间 + 方法" |
| 6 MBTI 用于自我认知 / 择业 | ② 证据不足 | 能提供描述偏好的词汇，可作自我反思起点 | "真实类型"二分为伪；重测信度差、双峰性不成立、对职业绩效无预测力 | 综述：[Stein & Swan 2019](https://compass.onlinelibrary.wiley.com/doi/10.1111/spc3.12434)；[Pittenger 1993](https://web.archive.org/web/20230902055656/https:/journals.sagepub.com/doi/10.3102/00346543063004467) | 只当社交话题，不用于选专业 / 选岗 |
| 7 记忆术 / 记忆宫殿 | ③ 部分有效但被夸大 | 对词表、外语配对等记忆任务有效，可训练 | "提升思考能力 / 变聪明"：对理解与迁移无证据 | 综述：[Dunlosky 2013](https://pubmed.ncbi.nlm.nih.gov/26173288/)；实验：[Dresler 2017](https://doi.org/10.1016/j.neuron.2017.02.003) | 定位为"记住事实"的技巧，非思维训练 |
| 8 多巴胺戒断 | ① 已被否定 | 减少刷短视频等高刺激行为本身有益 | "给多巴胺排毒、重置奖赏系统"：无研究支持，概念本身错误 | 科普：[Harvard Health](https://www.health.harvard.edu/blog/dopamine-fasting-misunderstanding-science-spawns-a-maladaptive-fad-2020022618917)、[Cleveland Clinic](https://health.clevelandclinic.org/dopamine-detox) | 改成"减少刺激源 + 做环境设计" |
| 9 批判性思维培训提升智力 | ③ 部分有效但被夸大 | 专门教学可在 CT 测评上小幅提升（g≈0.3） | "提升一般智力""跨领域自动迁移"：远迁移证据薄弱，依赖领域知识 | meta：[Abrami 2008/2015](https://eric.ed.gov/?id=EJ896709) | 说"在具体学科内练 CT"，不承诺变聪明 |
| 10 速读 / 照相记忆 | ① 已被否定 | 按目的跳读、预览可省时间；略提速在宽松条件下可行 | "高速阅读仍完整理解""一眼成相"：与眼动 / 知觉瓶颈冲突 | 综述：[Rayner 2016 PSPI](https://doi.org/10.1177/1529100615623267) | 写"按目的选择阅读策略"，不承诺提速 |
| 11 必须排除情绪才理性 | ① 已被否定 | 情绪是决策信息；腹内侧损伤患者情感缺失后决策反而崩坏 | "情绪＝理性敌人""完全无情绪才理性"：二分不成立 | 研究：[Maia & McClelland 2004](https://doi.org/10.1073/pnas.0406666101)；综述：[Lerner 2015](https://www.annualreviews.org/content/journals/10.1146/annurev-psych-010213-115043) | 写"识别情绪信号、校准偏差"，而非压制情绪 |
| 12 必须手写笔记 | ③ 部分有效但被夸大 | 笔记的生成性加工与复习方式才关键 | "手写优于打字提分"：直接复现失败，meta 效应 g≈−0.008（≈0） | 原研究：[Mueller & Oppenheimer 2014](https://doi.org/10.1177/0956797614524581)；复现：[Morehead 2019](https://doi.org/10.1007/s10648-019-09468-2)、[Urry 2021](https://doi.org/10.1177/0956797620965541)；[meta](https://www.sciencedirect.com/science/article/abs/pii/S0361476X21000849) | 写"加工深度 > 媒介"，媒介自由 |

### 三条最容易被当真理、最需警惕的说法

1. **左右脑人格 / MBTI 类型**：把模糊标签变成身份认同，自我确认偏误让人"越看越像"；几乎零成本、可随时复述。
2. **一万小时定律 / 成长型思维**：嫁接"努力即可成功"的道德直觉，把失败归因于个人努力不足，因此难以被反驳。
3. **脑力游戏、速读、多巴胺戒断**：有产品、有即时进度条与爽感，商业动机强；伪科学外壳裹着一点真成分（近迁移、跳读、少刷手机），最难识破。

### 直觉不可靠、需要查证时用的检索式

1. `"[说法] meta-analysis 2020..2025 effect size publication bias"`（先找元分析，看效应量与被试量）
2. `"[说法] replication failure OR direct replication OR failed to replicate"`（判断是否可复现）
3. `"[说法] neuromyth OR systematic review -site:pinterest.com -site:medium.com"`（区分同行评议与自媒体）

### 核查备注

- 第 1 项：2024 年 Frontiers 的元分析曾报告"匹配有小幅获益"，但 2025 年 *Educational Psychology Review* 复评指出其纳入研究未满足匹配假设的设计要求，故维持"已被否定"。
- 第 11 项：躯体标记假说本身仍有争论，但"情绪必须完全排除"的二分说法可明确否定。

### 对本工具箱的直接含义

- `docs/evidence-standards.md` 的"话术识别"一节可以引用本表：**判断一个说法可靠不可靠，先看有没有元分析与复现**
- 人生规划模块禁止出现"排除情绪做理性决策""意志力不足""改变思维方式就能改变结果"这类表述
- 知识地图模块禁止把记忆术、速读、学习风格匹配当作学习方法推荐


---

## 5. 汇总裁决（阶段 2 输入，原文）

> 源文件：`docs/clause-decisions.md`

## 条款裁决（阶段 1 → 阶段 2）

把 `research/` 里七个流域的证据，逐条对照到 `prompts/` 的现有条款与候选条款上。**结论：现有设计需要一次范式调整，不是补几条。**

简称：R1 提问技术｜R2 论证与系统｜R3 决策与校准｜R4 反思与元认知｜R5 知识组织｜R6 AI 对话行为｜R7 伪科学核查（见 [`../research/`](../research/)）。

### 总原则：从"输出更漂亮的分析"转向"逼出产出物 + 事后对账"

跨流域证据里唯一稳定复现的机制有两个：

1. **强制生成 + 紧跟具体反馈**：自我解释 g=0.55（R1）、反驳文本 g=0.41（R1）、先答后纠 g=0.36（R1）、结构化复盘 d≈0.67（R3/R4）、检索练习与间隔练习（强，R5）
2. **把判断外置成可计分、可复核的物件**：参考类预测（中—强，R3）、自然频数（中，R5）、校准训练必须闭环到反馈（中，R3/R4）

而**"讲授方法论"被反复证明无效**（只讲"偏差存在"无效，Abrami g+≈0.30 且需结合学科内容，R2/R5）；**以形式命名的方法**（苏格拉底式、Bloom 层级、Toulmin、竞争假设矩阵）要么证据弱，要么需要数小时级练习才有迁移（R1/R2）。

→ **判据**：一条条款若不能迫使用户产出具体物件、或不能留下可对账的痕迹，就应当删除或降级为"待验证"。

### 一、现有条款逐项裁决

| # | 现有条款 | 出处 | 证据 | 裁决 | 怎么改 |
| --- | --- | --- | --- | --- | --- |
| 1 | 事实 / 推论 / 价值三分 | 00、10、20 | **无直接实验**（待验证）；间接：语言化不确定改善单次校准（中，R6）；它本身是"可检查产出物" | **保留**（标注待验证） | 加强：每条推论写出"其成立所需前提"；来源等级 meta > 单一 RCT > 个案 > 无源 |
| 2 | 最强反方 | 00、10 | consider-the-opposite 中（R2/R3/R1）；**take perspective 弱、常失败**（R2）；迁移有限（R1/R2） | **修正** | 改为"写出 ≥2 条**可为真**的反方证据 + 若其为真，结论改到哪一步"；删掉"设身处地/重建到对方认可"这类表述 |
| 3 | L1–L3 深度分档 | 00 | 无直接实验；引导式探究 d=0.50、"新手必须配结构化支架"（强，R1）为其提供**间接支持** | **保留**（标注待验证） | 说明它是认知负荷 / 支架设计的应用，**不是"思维深度阶梯"**（Bloom 式层级已被否定，R1） |
| 4 | 收尾 30 条追问清单 | 00、docs | 苏格拉底式提问弱—中、无可分离因果证据（R1）；生成 + 反馈才是有效机制 | **修正** | 每轮最多问 **1 个**问题，且声明"此问题检验的是哪条隐含前提"；高情绪议题走"先答后纠"或降级为陈述式 |
| 5 | 禁止鸡汤 / 迎合 | 00、20 | sycophancy 中（R6）；**加警示标签只改变感知、不改变影响**（R6） | **保留 + 增强** | 不靠"提醒我警惕谄媚"，靠流程：AI 必须先复述我方主张的最强版本并得到确认，再反驳；禁止以"你的感受完全合理"开头 |
| 6 | 缺信息先问再答 / 信息不足不下结论 | 00、40 | **与"先答后纠"冲突**：先让用户生成（即使错误）再给答案有中—强证据（R1，PS-I g=0.36，校正后 0.87） | **冲突，待决策** | 见第四节问题 1 |
| 7 | 边界声明（专业领域交持证者） | 00 | 无直接实验；属风险控制 | **保留** | 无需改 |
| 8 | 计划加入的 premortem / 可逆性分类 / 决策日志 | 未落地 | premortem 弱—中且只测信心（R3）；"单向门/双向门"无同行评议证据（R3）；决策日志无任何直接证据（R3） | **不进默认流程** | premortem 可作可选项；另两个删除 |
| 9 | 置信度打分（校准） | 00 草案 | g=0.26 小、偏倚风险高、**必须闭环到反馈**（R3/R4） | **保留但绑定条件** | 没有"事后对账"就不许使用"校准"一词；预测登记 + 到期回看 |
| 10 | 知识地图"建立知识体系 / 跨学科思维" | 30 | 远迁移弱—近否定（R5）；跨学科整合正向证据最弱（R5）；概念地图 g=0.58 但结局是学科成绩 | **改承诺** | 删除"建立体系"类承诺；加"1 天 / 7 天无提示默写""每个节点必须写它排除了什么"；结论必标证据类型与情境 |
| 11 | 论证图 / 因果回路图 / Toulmin | 10 草案 | 论证图需数小时练习、单次短练无效（R2）；Toulmin 弱（R2）；CLD 弱—中（R2） | **降级为可选产出物** | 只在需要时用，且必须由**用户自己填**；不写"AI 帮你画一张论证图" |
| 12 | 人生规划里的"状态 / 意志力" | 20 | "意志力耗竭"已被多实验室 RRR 否定（d=0.06，R4）；"状态会污染判断"中但幅度小（R4） | **修正** | 删除意志力解释；保留"高唤醒/压力下判断不可靠"，并要求标注是主观感受还是结果指标 |
| 13 | 情绪处理方式 | 20 | "必须排除情绪才理性"已被否定（R7） | **修正** | 写"识别情绪信号、校准偏差"，不写"先排除情绪" |

### 二、新增条款候选（按证据强度排序）

| 条款 | 证据 | 强度 | 落地位置 |
| --- | --- | --- | --- |
| **AI 不给成品答案，只给分步提示 / 反问前先要求用户产出** | PNAS 2025 现场 RCT，近千名高中生；加护栏组无损害（R6） | **强** | 00-master（护栏总开关） |
| **强制产出物**：用户自己填表、先写自己的答案，再让 AI 对照 | 生成类干预 g=0.36–0.55（R1/R2） | **强** | 00 / 10 / 20 / 30 |
| **1 天 / 7 天无提示默写**，只保留两次都通过的内容 | 检索练习（222 研究）+ 间隔练习（317 实验）（R5） | **强** | 30 知识地图 |
| **if-then 动作**（何时 / 何处 / 做什么） | d≈0.65，642 个独立检验（R4） | **强** | 20 人生规划 |
| **预测登记 + 到期对账**（复盘三件套：可核验事实 / 预测与实际差值 / if-then） | AAR d≈0.67（R3/R4） | **中—强** | 新模块或 20 |
| **先写同类事件的历史分布，再写本次预测** | 参考类预测（R3） | **中—强** | 10 社会议题 |
| **自然频数**（x/1000）+ 基准率，禁止只给百分比 | 自然频数 meta（R5） | **中** | 10 / 30 |
| **第三人称自我距离**（把"我"写成"他/她"或自己的名字再推理） | 三项 RCT，N=693（R3） | **中** | 20 人生规划 |
| **因果链接标注**：必要 / 充分 / 仅相关 + 一条可证伪观察 | 反事实干预中—大效应但窄（R2） | **中（窄）** | 10 社会议题 |
| **结尾 ≥2 条"证据不足 / 我不知道"**，不得留空 | 反驳文本 + 校准机制（R1/R3） | **中** | 10 / 30 |
| AI 语言化表达不确定（"我不确定，但…"） | FAccT 2024 预注册 N=404（R6） | **中** | 00-master |
| 反例必须标注"证伪所需条件" | 反驳文本 g=0.41（R1） | **中—强（短期）** | 10 |

### 三、明确排除清单（不写进提示词）

| 做法 | 排除理由 |
| --- | --- |
| 竞争假设矩阵（ACH / 情报界 SATs） | 批判性综述称几乎无收益甚至有害（R2） |
| Toulmin 模型当"提升思维"的干预 | 仅 1 项准实验、无显著差异；只可当拆解清单（R2） |
| Bloom 层级当"思维深度阶梯" | 层级性缺实证支持（R1） |
| premortem 作为主打机制 | 只有几个实验，且测的是信心而非决策质量（R3） |
| 决策日志单独宣传 | 找不到任何 RCT 或 meta（R3） |
| "单向门 / 双向门" | 无同行评议证据，只有期权理论（R3） |
| 概念地图 / 知识图谱 = 建立知识体系 | 结局全是学科成绩，无跨领域判断证据（R5） |
| 跨学科整合本身的效果承诺 | 综述：少有证据表明跨学科课程优于学科课程（R5） |
| 表达性写作（情绪疗愈机制） | 全量 meta r≈.075，原始效应未复现（R4） |
| 记忆术 / 速读 / 学习风格匹配 | 已被否定（R7） |
| "先排除情绪才能理性" | 已被否定（R7） |
| "意志力耗竭"解释 | 多实验室 RRR d=0.06 不显著（R4） |
| "AI 正在削弱你的思考能力"作为立论依据 | MIT 研究仍为预印本、n=54，被过度解读（R6） |
| 给用户加"当心 AI 谄媚"的警示标签 | 只改变感知、不改变影响（R6） |

### 四、需要你决策的冲突点

1. **条款 6 冲突**：现有"信息不足不下结论"与有中—强证据的"先答后纠"（先让用户生成、再给答案）方向相反
2. **苏格拉底式追问的去留**：它是 R1 里证据最弱的一类，且可能抑制高焦虑者表达；但对"逼出隐含前提"仍有直觉吸引力
3. **是否新增校准 / 复盘模块**：这是跨流域最强的证据，但要求你真的回来对账，成本在你身上
4. **"强制产出物"的强度**：越强的产出物要求越能促进思考（证据），但会牺牲"直接给我一份分析"的便利



---

## 6. 引用核实状态

子代理受代理与 SSRF 限制无法抓取全文，下列关键引用由主导做了二次核实：

| 引用 | 核实结果 |
| --- | --- |
| Bastani et al., *Generative AI without guardrails can harm learning*, PNAS 122(26), 2025-06-25 | ✅ 存在；有公开数据与代码仓库 |
| *Systematic review and meta-analysis of educational approaches to reduce cognitive biases among students*, Nat Hum Behav 9(12):2510–2538, 2025-08-26 | ✅ 存在；54 项 RCT / 383 个效应量 / 10,941 人 与摘要一致 |
| Gollwitzer & Sheeran 2006, *Implementation Intentions and Goal Achievement*, Adv. Exp. Soc. Psychol. 38:69–119 | ✅ 存在（d≈0.65 为原文报告值） |

**尚未核实**（引用时必须标注预印本 / 技术报告）：

- arXiv 2606.21317、arXiv 2607.28133（2026）：仅经多次检索交叉确认存在，未见同行评议记录
- arXiv 2601.20245：Anthropic 技术报告，未同行评议
- arXiv 2506.08872（MIT "Your Brain on ChatGPT"）：仍为预印本，n=54，结论被广泛过度解读

**分级来源单一、需重点抽查的条目**：所有标"弱"的项；所有只有单一来源支撑的项（在各流域表中已标注）；概念地图 / 跨学科整合 / ACH 相关条目（这几项结论方向鲜明，但依据综述的纳入标准可能不同）。

---

## 7. 文件清单（在仓库中的对应位置）

| 本包章节 | 仓库文件 |
| --- | --- |
| 第 2 节 方法提示词 | `prompts/50-design-research.md` |
| 第 3 节 子代理提示词与检索日志 | 由子代理会话记录解析生成（本包独有） |
| 第 4 节 流域 1–7 | `research/01-questioning-techniques.md` … `research/07-debunked-practices.md` |
| 第 5 节 汇总裁决 | `docs/clause-decisions.md` |
| 索引与主线 | `research/README.md` |
| 最终提示词 | `prompts/00-master.md`、`10-social-event-analysis.md`、`20-life-planning.md`、`30-knowledge-map.md`、`40-deep-research.md` |

> 注意：第 4、5 节反映的是**尚未按裁决修改**的现行提示词所对应的分析；验证意见回收后才会改动 `prompts/` 下的文件。

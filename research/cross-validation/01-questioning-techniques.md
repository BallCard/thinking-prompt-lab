# 交叉验证单 1/7：提问技术

> 本单是一份**独立可验证**的证据交接件：由另一个 AI 单独核查这一个流域，不需要看其他 6 份。七份共用同一套核查清单与分级定义。

## 0. 背景

我们在设计一组提示词，让 AI 陪用户（大学生 / 非专业成年人）就**社会议题**与**人生选择**做深度思考。做法是：先检索「哪些方法真能提升思考质量」，再把证据为强 / 中的机制翻译成可执行、可检查的提示词条款。全部证据分为 7 个流域，本单是第 1 个：**提问技术**。

本流域覆盖范围：苏格拉底式提问、认知冲突与概念转变、脚手架式追问、Bloom 层级、自我解释、自我提问、先答后纠

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

1. 「苏格拉底式提问：弱—中，无独立 meta 分析」——请确认是「确实不存在 meta」还是「检索不到」，两者含义不同
2. Bloom 层级「缺实证」的判定依据（Kunen 1981 是否足以支撑）
3. 先答后纠（PS-I）校正发表偏差后 g=0.87、区间极宽的解读是否保守
4. 「引导式探究 d=0.50」是否被用来支持「必须给结构化支架」过度外推
5. 自我解释的「先验知识阈值」是否意味着对低基础用户该条款会失效

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

- 条款 4「收尾 30 条追问清单」→ 修正为每轮最多 1 问并声明检验哪条隐含前提
- 条款 6「信息不足不下结论」→ 与「先答后纠」冲突，列为待决策项
- 新增候选「强制产出物」（生成类干预）
- 排除清单：Bloom 层级当「思维深度阶梯」、按学习风格匹配提问

> 条款编号对应 `docs/clause-decisions.md`：00 总控、10 社会议题、20 人生规划、30 知识地图、40 深度检索。

## 3. 子代理原始提示词与检索日志（未人工改写）

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


## 4. 证据表（原文）

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


## 5. 引用核实状态

主导已二次核实 3 条：Bastani et al. PNAS 122(26) 2025-06-25 ✅；Nat Hum Behav 9(12):2510–2538 2025-08-26 ✅；Gollwitzer & Sheeran 2006, Adv. Exp. Soc. Psychol. 38:69–119 ✅。

**未核实、引用时必须标注**：arXiv 2606.21317、arXiv 2607.28133、arXiv 2601.20245（Anthropic 技术报告）、arXiv 2506.08872（MIT “Your Brain on ChatGPT”，预印本）。

本单内的其他引用**均未经人工核实**，请按第 1 节第 1 项抽查。

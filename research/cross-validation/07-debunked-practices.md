# 交叉验证单 7/7：伪科学黑名单（跨域核查）

> 本单是一份**独立可验证**的证据交接件：由另一个 AI 单独核查这一个流域，不需要看其他 6 份。七份共用同一套核查清单与分级定义。

## 0. 背景

我们在设计一组提示词，让 AI 陪用户（大学生 / 非专业成年人）就**社会议题**与**人生选择**做深度思考。做法是：先检索「哪些方法真能提升思考质量」，再把证据为强 / 中的机制翻译成可执行、可检查的提示词条款。全部证据分为 7 个流域，本单是第 7 个：**伪科学黑名单（跨域核查）**。

本流域覆盖范围：学习风格匹配、脑力训练、成长型思维、左右脑人格、一万小时定律、MBTI、记忆术、多巴胺戒断、批判性思维培训提升智力、速读、情绪与理性二分、手写笔记

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

1. 学习风格判「已被否定」：2024 年 Frontiers meta 与 2025 年复评之争，请独立判断哪一方更可靠
2. 成长型思维判「部分有效但被夸大」的措辞是否公允（Sisk 2018 与 Yeager 2019 的张力）
3. 「手写笔记 meta g≈−0.008」的引用是否准确
4. 一万小时定律中「练习解释的方差比例」（21% / 18%）是否被正确转述
5. 第 11 项（情绪必须排除才理性）：躯体标记假说本身有争议，用它否定该说法是否合法

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

- 条款 13「情绪处理」→ 改为「识别情绪信号」，删掉「先排除情绪」
- 排除清单主体（学习风格、记忆术、速读、多巴胺戒断、MBTI 等）
- `docs/evidence-standards.md` 增加「查元分析 → 查复现失败 → 用 neuromyth 锁定综述」的检索式

> 条款编号对应 `docs/clause-decisions.md`：00 总控、10 社会议题、20 人生规划、30 知识地图、40 深度检索。

## 3. 子代理原始提示词与检索日志（未人工改写）

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


## 4. 证据表（原文）

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


## 5. 引用核实状态

主导已二次核实 3 条：Bastani et al. PNAS 122(26) 2025-06-25 ✅；Nat Hum Behav 9(12):2510–2538 2025-08-26 ✅；Gollwitzer & Sheeran 2006, Adv. Exp. Soc. Psychol. 38:69–119 ✅。

**未核实、引用时必须标注**：arXiv 2606.21317、arXiv 2607.28133、arXiv 2601.20245（Anthropic 技术报告）、arXiv 2506.08872（MIT “Your Brain on ChatGPT”，预印本）。

本单内的其他引用**均未经人工核实**，请按第 1 节第 1 项抽查。

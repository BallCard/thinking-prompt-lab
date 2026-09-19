# 流域 7：伪科学黑名单（跨域核查）

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

## 三条最容易被当真理、最需警惕的说法

1. **左右脑人格 / MBTI 类型**：把模糊标签变成身份认同，自我确认偏误让人"越看越像"；几乎零成本、可随时复述。
2. **一万小时定律 / 成长型思维**：嫁接"努力即可成功"的道德直觉，把失败归因于个人努力不足，因此难以被反驳。
3. **脑力游戏、速读、多巴胺戒断**：有产品、有即时进度条与爽感，商业动机强；伪科学外壳裹着一点真成分（近迁移、跳读、少刷手机），最难识破。

## 直觉不可靠、需要查证时用的检索式

1. `"[说法] meta-analysis 2020..2025 effect size publication bias"`（先找元分析，看效应量与被试量）
2. `"[说法] replication failure OR direct replication OR failed to replicate"`（判断是否可复现）
3. `"[说法] neuromyth OR systematic review -site:pinterest.com -site:medium.com"`（区分同行评议与自媒体）

## 核查备注

- 第 1 项：2024 年 Frontiers 的元分析曾报告"匹配有小幅获益"，但 2025 年 *Educational Psychology Review* 复评指出其纳入研究未满足匹配假设的设计要求，故维持"已被否定"。
- 第 11 项：躯体标记假说本身仍有争论，但"情绪必须完全排除"的二分说法可明确否定。

## 对本工具箱的直接含义

- `docs/evidence-standards.md` 的"话术识别"一节可以引用本表：**判断一个说法可靠不可靠，先看有没有元分析与复现**
- 人生规划模块禁止出现"排除情绪做理性决策""意志力不足""改变思维方式就能改变结果"这类表述
- 知识地图模块禁止把记忆术、速读、学习风格匹配当作学习方法推荐

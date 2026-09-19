# Thinking Prompt Lab

> Status: `active`
> Purpose: 用于社会议题分析、人生规划与跨学科补课的提示词工具箱
> Entrypoint: [`prompts/00-master.md`](./prompts/00-master.md)
> Validation: 见 [AGENTS.md](./AGENTS.md) 的自检清单
> GitHub: <https://github.com/BallCard/thinking-prompt-lab>
> Next: 用 2–3 个真实问题跑一遍四个模块，记录哪些约束实际起作用

这套提示词解决的问题不是"让 AI 说得更多"，而是让它的输出**可判断、可验证、可复用**：把事实、推论和价值判断分开，把自我怀疑拆成可验证的命题，把外部信息压到能用于决策的最小程度。

## 项目工作流

本项目的产出不是“一个万能提示词”，而是经过证据筛选的提示词集合。顺序不能倒：

| 阶段 | 做什么 | 工具 / 产出 |
| --- | --- | --- |
| **1 调研** | 检索“哪些方法真能提升思考质量”，并区分证据强度与流行说法 | 用 [`prompts/50-design-research.md`](./prompts/50-design-research.md) 执行 → 产出 [`research/`](./research/) 下的证据表 |
| **2 设计** | 把证据为“强/中”的机制翻译成可执行、可检查的提示词条款 | `prompts/00–40` 各模块；保留哪些条款必须能追溯到证据 |
| **3 验证** | 用真实问题跑一遍，看条款是否真的改变了输出（而不是只让输出变长） | 洞察卡片 + `docs/design-notes.md` 的改动记录 |

`prompts/50-design-research.md` 是**手段**：它负责第 1 阶段，本身不是最终交付物。想改任何一条提示词条款，先到 `research/` 里找它对应的证据。

## 快速导航

| 文件 | 用途 | 什么时候用 |
| --- | --- | --- |
| [`prompts/00-master.md`](./prompts/00-master.md) | 总控提示词：路由 + 深度分档 + 通用输出规范 | 长期挂载，或每次对话开头粘贴 |
| [`prompts/10-social-event-analysis.md`](./prompts/10-social-event-analysis.md) | 社会事件分析：六层结构 + 利益结构 + 反方论证 | 看新闻、遇到公共议题、理解政策 |
| [`prompts/20-life-planning.md`](./prompts/20-life-planning.md) | 人生规划：约束条件 → 命题化 → 可逆实验 | 方向选择、取舍、自我怀疑卡住时 |
| [`prompts/30-knowledge-map.md`](./prompts/30-knowledge-map.md) | 知识地图：把陌生领域压成能用于判断的最小集 | 遇到不懂的概念、需要跨学科背景 |
| [`prompts/40-deep-research.md`](./prompts/40-deep-research.md) | 深度检索：检索式生成 + 来源分级 + 证据表（AI 搜索提示词） | 需要外部事实与数据，且要求可核查 |
| [`prompts/50-design-research.md`](./prompts/50-design-research.md) | **调研工具（阶段 1）**：检索“怎样设计促进思考的流程”，输出方法→证据→条款映射 | 设计或修改任何提示词之前先跑它 |
| [`docs/methodology-catalog.md`](./docs/methodology-catalog.md) | 十种分析方法：各自回答什么问题、局限在哪 | 分析卡住时换视角 |
| [`docs/depth-boundary.md`](./docs/depth-boundary.md) | 认知深度分档、时间盒、危险信号 | 判断"想到什么程度就够了" |
| [`docs/evidence-standards.md`](./docs/evidence-standards.md) | 来源分级、数据陷阱、话术识别 | 核查证据、识别可疑说法 |
| [`docs/question-bank.md`](./docs/question-bank.md) | 30 条追问清单 | 让 AI 追问自己，或自查 |
| [`docs/design-notes.md`](./docs/design-notes.md) | 设计原则、已知局限、迭代方式 | 修改提示词之前先读 |
| [`templates/insight-card.md`](./templates/insight-card.md) | 洞察卡片：把一次思考沉淀成可复用判断 | 每次分析结束后 |

## 三种用法

**1. 单轮问答（最省事）**
直接粘贴对应模块的全文，把开头带 **【】** 的占位符替换成你的问题。模块自带输出规范，不挂总控也能用。

**2. 长期对话（推荐）**
先粘贴 `00-master.md`，再抛出问题。总控会自动判断走哪条线、选深度档位，并按统一格式收尾。

**3. 需要外部证据时**
先用 `40-deep-research.md` 取证，拿到证据表后回到社会议题或人生规划模块做分析。不要跳过取证直接用 A/B 模块谈事实。

**4. 设计或修改提示词时（阶段 1 → 2）**
先跑 `prompts/50-design-research.md`，把结果存进 `research/`，再决定加什么条款、删什么条款。**每条条款都应该能指向一条证据**；指不上的条款要么删掉，要么标记为“待验证”。

## 使用顺序建议

1. 拿到一个问题 → 判断类型（社会 / 人生 / 知识 / 需要取证）
2. 定深度档位（L1 一小时，L2 半天，L3 才长期跟踪）
3. 跑模块，产出结构与证据
4. 填一张洞察卡片，写下待验证假设与检查时间
5. 到期复盘，只在新证据与假设冲突时才延长投入

## 设计要点

- **强制分类**：【事实】/【推论】/【价值】三分，分歧落在哪一层一目了然
- **可检验性优先**：来源分级、原文片段、交叉验证、"未找到证据"是合法输出
- **最强反方**：重建对立立场到其支持者认可的程度，再说明分歧性质
- **深度分档**：L1/L2/L3 各有时限，到点必须收敛成结论或"证据不足"
- **反迎合**：禁止鸡汤、伪精确、和稀泥结论，不用安慰替代分析

## 边界

- 提示词只能约束输出形式，不能保证内容为真；**关键事实请自行抽查来源**
- 涉及医疗、心理、法律、财务、工程安全的判断，AI 输出只能作为准备材料
- 本仓库只包含通用提示词与文档；个人分析记录与洞察卡片保存在本地，不入库

## 迭代计划

- [ ] 用 3 个真实问题检验各模块，记录哪些约束真正改变了输出
- [x] 跑一次 `prompts/50-design-research.md`，把证据强弱结论回写到各模块条款（已完成检索与七份流域交叉验证，修正记录见 [`docs/clause-decisions.md`](./docs/clause-decisions.md) 第五节）
- [ ] 补 1–2 个示例（脱敏后），展示同一问题的 L1 与 L2 输出差异
- [ ] 观察长对话中的约束衰减，必要时增加"每 5 轮重申纪律"的机制

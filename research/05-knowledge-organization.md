# 流域 5：知识组织、理解与迁移

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

## 一条最重要的结论

证据最强的是"**让知识被反复取出、且跨时间取出**"（检索练习 + 间隔练习）；而"整理形式"（概念地图、知识图谱，以及"费曼技巧"这个名号本身）效应中等且高度依赖使用方式；**跨学科整合与远迁移的正向证据最弱**。

因此：提示词应把"判断力"写成**可检查的提取、反例与近迁移任务**，不能承诺"帮助你建立知识体系"或"形成跨学科思维"。

## 可直接写进提示词的条款草案

1. 每个新领域先写"必须能回答的 5 个问题"，每个问题配一个**可判错的具体案例**；没有案例的概念不进地图。
2. 地图最多 12 个节点，每个节点必须写"它排除了什么"（失效条件 / 反例）；缺此字段视为未完成。
3. 每条结论必须标注证据类型（meta / RCT / 综述 / 无）与情境（实验室 / 真实）；无标注的按"未验证"处理，不得用于决策。
4. 输出后隔 1 天与 7 天各做一次**无提示默写**，只保留两次都通过的内容。
5. 涉及量级或风险判断时，一律写成自然频数（x/1000）并给出基准率，禁止只给百分比。

## 可自行验证的检索式

1. `("concept map" OR "knowledge map") AND ("far transfer" OR "transfer of learning")`
2. `"learning by teaching" AND ("meta-analysis" OR "randomized") AND (retention OR transfer)`
3. `"interdisciplinary" AND ("learning outcomes" OR "critical thinking") AND ("systematic review" OR "meta-analysis") AND "effect size"`

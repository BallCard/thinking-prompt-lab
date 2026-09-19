# 流域 3：判断偏差干预与决策辅助

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

## 一条最重要的结论

本流域最强、最可迁移的效应来自**把判断外置成可计分、可反馈的流程**（复盘 d=0.67、校准训练、参考类预测）；而最响亮的流行说法——**事前验尸、单向门 / 双向门、决策日志**——证据最薄。去偏训练在受控任务上的平均效应只有 g≈0.26，且能否迁移到真实决策**仍未被证明**。

## 可直接写进提示词的条款草案

1. 每条关键判断必须给出 0–100 的概率，并注明"什么证据会让我把它下调 20 点以上"。
2. 先写出本议题同类事件的历史分布（发生频率或典型区间），再写本次预测；两者冲突时必须说明为何本次不同。
3. 强制生成至少 3 条反驳当前结论的具体证据来源，其中至少 1 条必须是持真实不同立场者会引用的（不是稻草人）。
4. 输出末尾固定给出：本次判断的可逆性、最小可逆验证动作、以及"何时回头复核"的时间点。
5. 复盘时只对照事前写下的预期与实际结果，逐条标出是哪一步推理出错；**不接受**"结果不好但过程没错"这种自评。

## 可继续验证的检索式

1. `premortem randomized controlled trial decision quality outcome (not confidence)`
2. `debiasing training transfer field setting follow-up effect size meta-analysis site:ssrn.com OR site:osf.io`
3. `checklist expertise reversal complex dynamic task performance decrement experiment`

## 未找到证据

- 决策日志的独立效果
- "单向门 / 双向门"分类的对照实验证据（只有期权理论 + 经济计量支持）

## 与流域 2、4 的交叉

- 流域 4 与本文都指向同一结论：**没有反馈就没有校准**，所以"置信度打分"必须绑定"事后回来对账"，否则只是形式。
- 校准效应（g≈0.26）比复盘（d≈0.67）小得多 → 提示词里"预测 + 对账"应作为复盘流程的一部分，而不是独立卖点。

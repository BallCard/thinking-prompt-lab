# 调研证据（阶段 1）

这里存放执行 [`prompts/50-design-research.md`](../prompts/50-design-research.md) 得到的证据表。**`prompts/` 下的每条条款都应该能追溯到这里的某一行**；追溯不到的条款要么删掉，要么标记为"待验证"。

## 流域与状态

| # | 流域 | 文件 | 状态 |
| --- | --- | --- | --- |
| 1 | 提问技术（苏格拉底式提问、认知冲突、脚手架式追问） | `01-questioning-techniques.md` | 进行中 |
| 2 | 论证结构与系统视角（argument mapping、Toulmin、因果回路） | [`02-argument-and-systems.md`](./02-argument-and-systems.md) | 已完成 |
| 3 | 判断偏差干预与决策辅助（premortem、校准、参考类预测） | [`03-decision-and-calibration.md`](./03-decision-and-calibration.md) | 已完成 |
| 4 | 自我反思与元认知 | [`04-reflection-and-metacognition.md`](./04-reflection-and-metacognition.md) | 已完成 |
| 5 | 知识组织、理解与迁移 | [`05-knowledge-organization.md`](./05-knowledge-organization.md) | 已完成 |
| 6 | AI 对话行为与使用者认知（迎合、认知卸载） | [`06-ai-dialogue-effects.md`](./06-ai-dialogue-effects.md) | 已完成 |
| 7 | 伪科学黑名单（跨域核查） | [`07-debunked-practices.md`](./07-debunked-practices.md) | 已完成 |

## 跨流域三条主线（初判，待 1、2 流域完成后定稿）

1. **最强证据全部指向"把判断外置成可计分、可反馈、可复核的流程"**：复盘 d≈0.67、检索练习与间隔练习（强）、参考类预测（中—强）。
2. **最弱的恰恰是最响亮的流行做法**：premortem、决策日志、单向门/双向门、概念地图式"建立知识体系"、跨学科整合、远迁移——这些不能当主卖点。
3. **唯一同时具备因果证据的 AI 交互条款有两条**：不直接给答案/只给分步提示（强，PNAS 2025），以及语言化表达不确定（中）。其余条款（三分法、最强反方、信息不足不下结论）应标为**待验证**，而不是写成硬约束。

## 交叉验证包（交接给另一个 AI）

**[`cross-validation-package.md`](./cross-validation-package.md)**（~90 KB，单一文件）把下面四类内容拼在一起，可直接整份交给另一个 AI 做独立核查：

1. 给验证者的任务清单（8 项核查 + 输出格式 + 本包已知弱点自陈）
2. 方法提示词原文（`prompts/50-design-research.md`）
3. **7 个子代理的完整原始提示词 + 按时间顺序的全部检索式与抓取 URL**（由子代理会话记录离线解析，未人工改写；共 166 次工具调用、**283 条检索式**、19 个抓取 URL）
4. 七份证据表原文 + 汇总裁决原文 + 引用核实状态

> 本文件是生成物：改内容请改源文件后重新拼接，不要直接编辑。

## 引用抽查（人工二次核实）

子代理受代理与 SSRF 限制无法抓取全文，下列关键引用由主导查重：

| 引用 | 核实结果 |
| --- | --- |
| Bastani et al., *Generative AI without guardrails can harm learning*, PNAS 122(26), 2025-06-25 | ✅ 存在；有公开数据与代码仓库 |
| *Systematic review and meta-analysis of educational approaches to reduce cognitive biases among students*, Nat Hum Behav 9(12):2510–2538, 2025-08-26 | ✅ 存在；54 项 RCT / 383 个效应量 / 10,941 人与摘要一致 |
| Gollwitzer & Sheeran 2006, *Implementation Intentions and Goal Achievement*, Adv. Exp. Soc. Psychol. 38:69–119 | ✅ 存在（d≈0.65 为原文报告值） |

**尚未核实**（引用时必须标预印本 / 技术报告）：arXiv 2606.21317、2607.28133、2601.20245；MIT"Your Brain on ChatGPT"（arXiv 2506.08872）仍为预印本。

## 阅读方式

- 证据强度只有四档：`强`（多项 RCT 或系统综述结论一致）、`中`（单项实验或结果混杂）、`弱`（理论推导、专家意见、实践共识）、`已否定`
- **"弱"不等于无用**，但写进提示词时必须标为待验证，不能作为主要机制
- 每份文件末尾的"条款草案"是阶段 2 的输入，不是最终条款；汇总裁决见 `../docs/clause-decisions.md`（整理中）

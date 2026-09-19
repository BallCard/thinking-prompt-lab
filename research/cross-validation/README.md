# 交叉验证单（按流域拆成 7 份，可分别独立送检）

把完整包 [`../cross-validation-package.md`](../cross-validation-package.md) 拆成 7 份：每份自带背景、核查清单、分级定义、子代理原始提示词、完整检索日志、证据表、裁决去向与重点抽查项，**可以单独交给一个 AI 核查**。

要更干净的交叉验证，建议 7 份分别交给 7 个互不相关的会话 / 模型，避免同一上下文互相锚定。

| # | 流域 | 文件 | 大小 |
| --- | --- | --- | --- |
| 1 | 提问技术 | [`01-questioning-techniques.md`](./01-questioning-techniques.md) | 16.1 KB |
| 2 | 论证结构与系统视角 | [`02-argument-and-systems.md`](./02-argument-and-systems.md) | 14.3 KB |
| 3 | 判断偏差干预与决策辅助 | [`03-decision-and-calibration.md`](./03-decision-and-calibration.md) | 14.3 KB |
| 4 | 自我反思与元认知干预 | [`04-reflection-and-metacognition.md`](./04-reflection-and-metacognition.md) | 11.4 KB |
| 5 | 知识组织、理解与迁移 | [`05-knowledge-organization.md`](./05-knowledge-organization.md) | 13.6 KB |
| 6 | AI 对话行为与使用者认知 | [`06-ai-dialogue-effects.md`](./06-ai-dialogue-effects.md) | 11.7 KB |
| 7 | 伪科学黑名单（跨域核查） | [`07-debunked-practices.md`](./07-debunked-practices.md) | 12.6 KB |

## 送检结果

| 文件 | 内容 |
| --- | --- |
| [`result.md`](./result.md) | 七份核查报告的返回结果，按流域顺序拼接；已剔除会过期的第三方附件签名链接，其余来源链接保留 |

据此产生的条款修正见 [`../../docs/clause-decisions.md`](../../docs/clause-decisions.md) 第五节，逐条改动理由见 [`../../docs/design-notes.md`](../../docs/design-notes.md) 的迭代记录。

> 上面 7 份是生成物：修改请改 `prompts/50-design-research.md`、`research/0*.md`、`docs/clause-decisions.md` 后重新生成。

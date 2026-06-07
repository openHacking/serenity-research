# Serenity Research Skill

[English](README.md) | [中文](README.zh-CN.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [Español](README.es.md)

Serenity Research 是一个开源 AI skill，用于把市场叙事转化为结构化投资研究。

它受到公开的 Serenity 风格研究方法启发，但这是一个原创框架。这个 skill 关注如何把趋势拆解为需求冲击、价值链层级、稀缺约束、二阶和三阶受益者、证据质量、错误定价假设和证伪测试。

```text
趋势 -> 需求冲击 -> 价值链 -> 稀缺层 -> 二阶/三阶受益者 -> 证据 -> 错误定价假设 -> 证伪
```

仅用于研究支持。本 skill 不提供个性化财务建议、交易执行、收益保证或买卖指令。

## 30 秒开始

`skills` CLI 不要求选择特定 AI 客户端。如果你的环境支持，可以这样安装：

```bash
npx skills add https://github.com/openHacking/serenity-research --skill serenity-research
```

如果你更希望让 AI agent 帮你安装，可以使用与你的客户端匹配的提示词。

**Codex**

```text
请安装 serenity-research Codex skill。把 https://github.com/openHacking/serenity-research 克隆到 ${CODEX_HOME:-$HOME/.codex}/skills/serenity-research，然后确认 SKILL.md、README.md 和 agents/openai.yaml 都存在。
```

如果是项目级 Codex 安装，请把仓库放在 `.codex/skills/serenity-research`。

**Claude Code 或其他带有 `skills` CLI 的客户端**

```text
请使用 skills CLI 从 https://github.com/openHacking/serenity-research 安装 serenity-research skill。安装后，确认这个 skill 可以用 serenity-research 调用。
```

**其他可运行 shell 的 agent**

```text
请把 https://github.com/openHacking/serenity-research 安装为本地 AI skill。若可用，优先使用 skills CLI；否则使用当前客户端要求的 skill 目录，并确认客户端可以发现 SKILL.md。
```

更新已有 Codex 安装：

```text
请更新 serenity-research。进入 ${CODEX_HOME:-$HOME/.codex}/skills/serenity-research，运行 git pull，并报告最新 commit。
```

安装后，可以这样问你的 agent：

```text
请使用 serenity-research 梳理 AI 数据中心电力链，并按研究优先级排序最值得关注的二阶受益者。
```

## 它能帮助什么

- 把市场主题转化为研究地图。
- 找到产业链瓶颈和稀缺层。
- 越过显而易见的赢家，寻找供应商和基础设施受益者。
- 挑战某家公司是否真的受益于某个趋势。
- 按研究优先级排序候选对象。
- 为市场主题和产业链生成深度研究提示词。
- 建立证据清单和证伪条件。

## 仓库结构

```text
serenity-research/
|-- SKILL.md
|-- README.md
|-- README.zh-CN.md
|-- README.ja.md
|-- README.ko.md
|-- README.es.md
|-- LICENSE
|-- agents/
|   `-- openai.yaml
|-- examples/
|   |-- theme-scan.md
`-- evals/
    `-- test-cases.md
```

## 示例提示词

可以直接要求使用 `serenity-research`，也可以用 Serenity 风格描述研究任务：

```text
请为 AI 基础设施供应链生成一个 Serenity 风格的研究提示词。
```

```text
请验证 Company X 是否真的是机器人供应链中的瓶颈环节。
```

```text
请使用 serenity-research，一次问我一个问题，教我掌握这个研究方法。
```

## 默认输出

skill 通常会返回：

```text
1. 先给判断
2. 需求冲击
3. 价值链地图
4. 稀缺层
5. 受益者层级
6. 候选研究清单
7. 证据清单
8. 市场可能忽略了什么
9. 证伪条件
10. 下一步验证
```

## 评分框架

对候选对象排序时，skill 使用 100 分研究优先级评分：

| 维度 | 分值 |
| --- | ---: |
| 主题相关性 | 20 |
| 盈利弹性 | 20 |
| 稀缺性 / 瓶颈控制力 | 20 |
| 证据强度 | 20 |
| 市场认知差 | 20 |

分数代表研究优先级，不是收益预测。

## 示例：主题扫描

skill 不会只问哪家热门公司最受关注，而会问：

- 哪个需求冲击是可观察的？
- 哪些价值链层级必须扩张？
- 哪些层级难以快速扩张？
- 哪些二阶和三阶供应商可能有更高盈利弹性？
- 哪些证据会确认或削弱这个 thesis？

可复用提示词见 [examples/theme-scan.md](examples/theme-scan.md)。

## 证据标准

优先使用一手、可验证来源：

- 公司公告和披露
- 年报和中报
- 业绩会文字稿
- 投资者演示材料
- 交易所文件
- 官方公告
- 采购记录
- 监管记录
- 专利和标准
- 已确认合同

社交媒体和无来源评论只能作为线索。当前市场主张在证券排序前应使用最新数据验证。

## 研究边界

本 skill 用于研究、排序和 thesis 测试。它不应该：

- 承诺收益
- 告诉用户买入或卖出什么
- 编造市场数据
- 把传闻当作证据
- 把社交媒体当作最终证据
- 忽略流动性、估值、监管或治理风险

最终投资决策仍由用户自行负责。

## License

MIT. See [LICENSE](LICENSE).

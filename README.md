# Serenity Research Skill

Serenity Research is an open-source AI skill for turning market narratives into structured investment research.

It is inspired by public Serenity-style research patterns, but it is an original framework. The skill focuses on mapping a trend into demand shocks, value-chain layers, scarce constraints, second- and third-order beneficiaries, evidence quality, mispricing hypotheses, and falsification tests.

```text
trend -> demand shock -> value chain -> scarce layer -> second/third-order beneficiaries -> evidence -> mispricing hypothesis -> falsification
```

Research support only. This skill does not provide personalized financial advice, trade execution, guaranteed returns, or buy/sell instructions.

## 30-Second Start

The `skills` CLI does not require choosing a specific AI client. If your environment supports it, install with:

```bash
npx skills add https://github.com/openHacking/serenity-research --skill serenity-research
```

If you prefer to let an AI agent install it for you, use the prompt that matches your client.

**Codex**

```text
Install the serenity-research Codex skill. Clone https://github.com/openHacking/serenity-research into ${CODEX_HOME:-$HOME/.codex}/skills/serenity-research, then verify that SKILL.md, README.md, and agents/openai.yaml exist.
```

For a project-level Codex install, place the repository in `.codex/skills/serenity-research` instead.

**Claude Code or another client with the `skills` CLI**

```text
Install the serenity-research skill from https://github.com/openHacking/serenity-research using the skills CLI. After installation, verify that the skill is available as serenity-research.
```

**Other shell-capable agents**

```text
Install serenity-research from https://github.com/openHacking/serenity-research as a local AI skill. Prefer the skills CLI if available. If not, use the skill directory required by this client and verify that SKILL.md is discoverable by the client.
```

To update an existing Codex install:

```text
Update serenity-research. Go to ${CODEX_HOME:-$HOME/.codex}/skills/serenity-research, run git pull, and report the latest commit.
```

After installation, ask your agent:

```text
Use serenity-research to map the AI data-center power chain and rank the most interesting second-order beneficiaries.
```

## What It Helps With

- Convert a market theme into a research map.
- Find industry-chain bottlenecks and scarce layers.
- Look past obvious winners toward suppliers and enabling infrastructure.
- Challenge whether a company truly benefits from a trend.
- Rank candidates by research priority.
- Generate deep-research prompts for market themes and industry chains.
- Build evidence checklists and falsification conditions.

## Repository Structure

```text
serenity-research/
|-- SKILL.md
|-- README.md
|-- LICENSE
|-- agents/
|   `-- openai.yaml
|-- examples/
|   |-- theme-scan.md
`-- evals/
    `-- test-cases.md
```

## Example Prompts

Ask for `serenity-research` directly, or describe the research task in Serenity-style language:

```text
Build me a Serenity-style research prompt for the AI infrastructure supply chain.
```

```text
Challenge whether Company X is a real bottleneck in the robotics supply chain.
```

```text
Use serenity-research to teach me the method one question at a time.
```

## Default Output

The skill normally returns:

```text
1. Judgment first
2. Demand shock
3. Value-chain map
4. Scarce layers
5. Beneficiary layers
6. Candidate research list
7. Evidence checklist
8. What the market may be missing
9. Falsification conditions
10. Next verification steps
```

## Scoring Framework

When ranking candidates, the skill uses a 100-point research-priority score:

| Dimension | Points |
| --- | ---: |
| Theme relevance | 20 |
| Earnings elasticity | 20 |
| Scarcity / bottleneck control | 20 |
| Evidence strength | 20 |
| Market recognition gap | 20 |

Scores are research priorities, not return forecasts.

## Example: Theme Scan

Instead of asking which headline company is popular, the skill asks:

- What demand shock is actually observable?
- Which value-chain layers must scale?
- Which layers are hard to expand quickly?
- Which second- and third-order suppliers may have higher earnings elasticity?
- What evidence would confirm or weaken the thesis?

See [examples/theme-scan.md](examples/theme-scan.md) for a reusable prompt.

## Evidence Standards

Prefer primary and verifiable sources:

- company filings
- annual and interim reports
- earnings transcripts
- investor presentations
- exchange filings
- official announcements
- procurement records
- regulatory records
- patents and standards
- confirmed contracts

Use social media and unsourced commentary only as idea leads. Current market claims should be verified with current data before ranking securities.

## Research Boundaries

This skill is designed for research, prioritization, and thesis testing. It should not:

- promise returns
- tell a user what to buy or sell
- invent market data
- rely on rumors as proof
- treat social media as final evidence
- ignore liquidity, valuation, regulation, or governance risks

Final investment decisions remain with the user.

## License

MIT. See [LICENSE](LICENSE).

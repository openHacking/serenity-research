# Serenity Research Skill

[English](README.md) | [中文](README.zh-CN.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [Español](README.es.md)

Serenity Research は、市場のナラティブを構造化された投資リサーチへ変換するためのオープンソース AI skill です。

公開されている Serenity 風のリサーチパターンに着想を得ていますが、これは独自のフレームワークです。トレンドを需要ショック、バリューチェーンの階層、希少な制約、二次・三次の受益者、証拠の質、ミスプライシング仮説、反証テストへ分解します。

```text
trend -> demand shock -> value chain -> scarce layer -> second/third-order beneficiaries -> evidence -> mispricing hypothesis -> falsification
```

リサーチ支援のみを目的としています。個別の金融アドバイス、取引執行、利益保証、売買指示は提供しません。

## 30 秒で開始

`skills` CLI は特定の AI クライアントを選ぶ必要がありません。環境が対応していれば、次のようにインストールできます。

```bash
npx skills add https://github.com/openHacking/serenity-research --skill serenity-research
```

AI agent にインストールさせたい場合は、利用中のクライアントに合うプロンプトを使ってください。

**Codex**

```text
serenity-research Codex skill をインストールしてください。https://github.com/openHacking/serenity-research を ${CODEX_HOME:-$HOME/.codex}/skills/serenity-research にクローンし、SKILL.md、README.md、agents/openai.yaml が存在することを確認してください。
```

プロジェクト単位で Codex に導入する場合は、リポジトリを `.codex/skills/serenity-research` に置きます。

**Claude Code または `skills` CLI 対応クライアント**

```text
skills CLI を使って https://github.com/openHacking/serenity-research から serenity-research skill をインストールしてください。インストール後、serenity-research として利用できることを確認してください。
```

**その他の shell 対応 agent**

```text
https://github.com/openHacking/serenity-research から serenity-research をローカル AI skill としてインストールしてください。skills CLI が使える場合は優先してください。使えない場合は、このクライアントが要求する skill ディレクトリを使い、SKILL.md をクライアントが検出できることを確認してください。
```

既存の Codex インストールを更新するには：

```text
serenity-research を更新してください。${CODEX_HOME:-$HOME/.codex}/skills/serenity-research に移動し、git pull を実行して、最新の commit を報告してください。
```

インストール後、agent に次のように依頼できます。

```text
serenity-research を使って AI データセンターの電力チェーンを整理し、注目すべき二次受益者をリサーチ優先度でランク付けしてください。
```

## できること

- 市場テーマをリサーチマップに変換する。
- 産業チェーンのボトルネックと希少レイヤーを見つける。
- 明白な勝者の先にある供給企業やインフラを探す。
- 企業が本当にトレンドの恩恵を受けるか検証する。
- 候補をリサーチ優先度でランク付けする。
- 市場テーマや産業チェーン向けの深掘りリサーチプロンプトを作る。
- 証拠チェックリストと反証条件を作る。

## リポジトリ構成

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

## プロンプト例

`serenity-research` を直接指定するか、Serenity 風の言葉でリサーチ課題を説明します。

```text
AI インフラ供給チェーン向けの Serenity スタイルのリサーチプロンプトを作成してください。
```

```text
Company X がロボティクス供給チェーンにおける本当のボトルネックなのかを検証してください。
```

```text
serenity-research を使って、この方法を一度に一つの質問で教えてください。
```

## デフォルト出力

通常、skill は次の形式で返します。

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

## スコアリング

候補をランク付けする際、skill は 100 点のリサーチ優先度スコアを使います。

| Dimension | Points |
| --- | ---: |
| Theme relevance | 20 |
| Earnings elasticity | 20 |
| Scarcity / bottleneck control | 20 |
| Evidence strength | 20 |
| Market recognition gap | 20 |

スコアはリサーチ優先度であり、リターン予測ではありません。

## 例：テーマスキャン

この skill は、話題の会社を追うだけでなく、次を問いかけます。

- 観察可能な需要ショックは何か？
- どのバリューチェーン階層が拡大する必要があるか？
- どの階層は短期間で拡大しにくいか？
- どの二次・三次サプライヤーに高い利益感応度があるか？
- どの証拠が仮説を強め、または弱めるか？

再利用可能なプロンプトは [examples/theme-scan.md](examples/theme-scan.md) を参照してください。

## 証拠基準

一次情報と検証可能な情報を優先します。

- 企業開示
- 年次・中間報告書
- 決算説明会の書き起こし
- 投資家向け資料
- 取引所提出書類
- 公式発表
- 調達記録
- 規制関連記録
- 特許と標準
- 確認済み契約

ソーシャルメディアや出典不明のコメントは、アイデアの手がかりとしてのみ扱います。現在の市場主張は、証券をランク付けする前に最新データで確認する必要があります。

## リサーチの境界

この skill はリサーチ、優先順位付け、仮説検証のためのものです。次のことは行いません。

- 利益を約束する
- 売買対象を指示する
- 市場データを作り上げる
- 噂を証拠として扱う
- ソーシャルメディアを最終証拠として扱う
- 流動性、バリュエーション、規制、ガバナンスリスクを無視する

最終的な投資判断はユーザー自身にあります。

## License

MIT. See [LICENSE](LICENSE).

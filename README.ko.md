# Serenity Research Skill

[English](README.md) | [中文](README.zh-CN.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [Español](README.es.md)

Serenity Research는 시장 내러티브를 구조화된 투자 리서치로 바꾸는 오픈소스 AI skill입니다.

공개된 Serenity 스타일 리서치 패턴에서 영감을 받았지만, 이 skill은 독자적인 프레임워크입니다. 트렌드를 수요 충격, 가치사슬 레이어, 희소한 제약, 2차 및 3차 수혜자, 증거 품질, 미스프라이싱 가설, 반증 테스트로 분해하는 데 초점을 둡니다.

```text
trend -> demand shock -> value chain -> scarce layer -> second/third-order beneficiaries -> evidence -> mispricing hypothesis -> falsification
```

리서치 지원 전용입니다. 이 skill은 개인화된 금융 조언, 거래 실행, 수익 보장, 매수/매도 지시를 제공하지 않습니다.

## 30초 시작

`skills` CLI는 특정 AI 클라이언트를 선택할 필요가 없습니다. 환경이 지원한다면 다음 명령으로 설치할 수 있습니다.

```bash
npx skills add https://github.com/openHacking/serenity-research --skill serenity-research
```

AI agent가 대신 설치하게 하려면 사용하는 클라이언트에 맞는 프롬프트를 사용하세요.

**Codex**

```text
serenity-research Codex skill을 설치해 주세요. https://github.com/openHacking/serenity-research 를 ${CODEX_HOME:-$HOME/.codex}/skills/serenity-research 에 클론한 뒤, SKILL.md, README.md, agents/openai.yaml 이 존재하는지 확인해 주세요.
```

프로젝트 단위 Codex 설치의 경우 저장소를 `.codex/skills/serenity-research`에 두세요.

**Claude Code 또는 `skills` CLI가 있는 다른 클라이언트**

```text
skills CLI를 사용해 https://github.com/openHacking/serenity-research 에서 serenity-research skill을 설치해 주세요. 설치 후 serenity-research 로 사용할 수 있는지 확인해 주세요.
```

**기타 shell 실행 가능 agent**

```text
https://github.com/openHacking/serenity-research 에서 serenity-research 를 로컬 AI skill로 설치해 주세요. 가능하면 skills CLI를 우선 사용하세요. 그렇지 않다면 이 클라이언트가 요구하는 skill 디렉터리를 사용하고, 클라이언트가 SKILL.md 를 발견할 수 있는지 확인해 주세요.
```

기존 Codex 설치를 업데이트하려면:

```text
serenity-research 를 업데이트해 주세요. ${CODEX_HOME:-$HOME/.codex}/skills/serenity-research 로 이동해 git pull 을 실행하고, 최신 commit 을 보고해 주세요.
```

설치 후 agent에게 이렇게 요청할 수 있습니다.

```text
serenity-research 를 사용해 AI 데이터센터 전력 체인을 매핑하고, 가장 흥미로운 2차 수혜자를 리서치 우선순위로 순위화해 주세요.
```

## 활용 분야

- 시장 테마를 리서치 맵으로 전환합니다.
- 산업 가치사슬의 병목과 희소 레이어를 찾습니다.
- 명백한 승자 너머의 공급업체와 인프라 수혜자를 탐색합니다.
- 한 기업이 실제로 트렌드의 수혜를 받는지 검증합니다.
- 후보를 리서치 우선순위로 정렬합니다.
- 시장 테마와 산업 체인을 위한 심층 리서치 프롬프트를 만듭니다.
- 증거 체크리스트와 반증 조건을 만듭니다.

## 저장소 구조

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

## 예시 프롬프트

`serenity-research`를 직접 요청하거나 Serenity 스타일 언어로 리서치 작업을 설명하세요.

```text
AI 인프라 공급망을 위한 Serenity 스타일 리서치 프롬프트를 만들어 주세요.
```

```text
Company X 가 로보틱스 공급망의 실제 병목인지 검증해 주세요.
```

```text
serenity-research 를 사용해 한 번에 한 질문씩 이 방법을 가르쳐 주세요.
```

## 기본 출력

skill은 일반적으로 다음을 반환합니다.

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

## 점수 프레임워크

후보를 순위화할 때 skill은 100점 만점의 리서치 우선순위 점수를 사용합니다.

| Dimension | Points |
| --- | ---: |
| Theme relevance | 20 |
| Earnings elasticity | 20 |
| Scarcity / bottleneck control | 20 |
| Evidence strength | 20 |
| Market recognition gap | 20 |

점수는 리서치 우선순위이지 수익률 전망이 아닙니다.

## 예시: 테마 스캔

이 skill은 어떤 인기 기업이 주목받는지만 묻지 않고 다음을 질문합니다.

- 관찰 가능한 수요 충격은 무엇인가?
- 어떤 가치사슬 레이어가 확장되어야 하는가?
- 어떤 레이어가 빠르게 확장되기 어려운가?
- 어떤 2차 및 3차 공급업체가 더 높은 이익 민감도를 가질 수 있는가?
- 어떤 증거가 가설을 확인하거나 약화하는가?

재사용 가능한 프롬프트는 [examples/theme-scan.md](examples/theme-scan.md)를 참고하세요.

## 증거 기준

1차 자료와 검증 가능한 출처를 우선합니다.

- 회사 공시
- 연간 및 중간 보고서
- 실적 발표 transcript
- 투자자 프레젠테이션
- 거래소 제출 자료
- 공식 발표
- 조달 기록
- 규제 기록
- 특허와 표준
- 확인된 계약

소셜 미디어와 출처 없는 코멘트는 아이디어 단서로만 사용합니다. 현재 시장 주장에 대해서는 증권 순위화 전에 최신 데이터로 검증해야 합니다.

## 리서치 경계

이 skill은 리서치, 우선순위화, thesis 테스트를 위해 설계되었습니다. 다음을 해서는 안 됩니다.

- 수익을 약속하기
- 사용자에게 무엇을 사고팔지 지시하기
- 시장 데이터를 만들어내기
- 루머를 증거로 사용하기
- 소셜 미디어를 최종 증거로 취급하기
- 유동성, 밸류에이션, 규제, 지배구조 리스크를 무시하기

최종 투자 결정은 사용자에게 있습니다.

## License

MIT. See [LICENSE](LICENSE).

# Harness Engineering 서베이 2026

> **에이전트 성능의 병목은 대체로 모델 크기가 아니라 하네스 설계에 있다.**

2026년 5~7월 하네스 엔지니어링(에이전트 하네스·스캐폴딩·컨텍스트 엔지니어링·툴 오케스트레이션·평가 하네스) 분야의 최신 연구를 라이브 검색으로 발굴하고, **raw arXiv API로 실존을 적대적으로 검증**하여(환각 인용 0건), 검증된 논문만으로 작성한 서베이입니다.

## 🔗 바로 보기

- **인터랙티브 웹페이지:** https://revfactory.github.io/harness-paper/
- **전체 리포트(웹 뷰어):** https://revfactory.github.io/harness-paper/report.html

## 규모

| 항목 | 수치 |
|------|------|
| arXiv 논문 실존 검증 | 95편 (95/95 확인) |
| 범위 내(2026-05~07) 인용 | 86편 |
| 환각 인용(REJECTED) | **0건** |
| 산업 1차 자료 HTTP 확인 | 18건 |
| 연구 테마 | T1–T10 |

## 구성

```
index.html                                  인터랙티브 요약 웹페이지 (자기완결 단일 파일)
report.html                                 전체 리포트 웹 뷰어
harness-engineering-survey-2026-readable.md 전체 리포트 (가독성 개선판)
harness-engineering-survey-2026.md          전체 리포트 (원본)
_workspace/                                 발굴·분석·검증 중간 산출물 (감사 추적용)
  └─ 03_verification/                       raw arXiv API 검증 원장
.claude/                                    서베이를 생성한 에이전트 하네스 정의 (agents 4종 + skills 5종)
```

## 방법론

이 서베이 자체가 하나의 **에이전트 하네스**로 만들어졌습니다:

```
paper-scout ×3 (라이브 발굴) → paper-analyst (초록 기반 분석)
  → citation-verifier (적대적 검증 게이트 — raw arXiv API 배치 대조) ★
  → survey-synthesizer (CONFIRMED만 인용하여 종합)
```

대상 논문 전부가 AI 지식 컷오프 이후 발표됐기 때문에 환각 인용이 최대 위험이며, 검증 게이트를 통과한(CONFIRMED) 논문만 본문에 인용합니다. 커버리지 한계(arXiv 편중, 동료심사 미확인 등)는 리포트 §2와 부록 A에 투명하게 기록되어 있습니다.

---
name: harness-survey-orchestrator
description: "하네스 엔지니어링(에이전트 하네스·스캐폴딩·컨텍스트 엔지니어링·툴 오케스트레이션·평가 하네스) 분야의 최신 논문을 조사·분석·검증하여 인용 포함 서베이 리포트를 생성하는 에이전트 팀 오케스트레이터. '하네스 엔지니어링 논문 조사', '최신 논문 서베이', '문헌 조사', '연구 동향 정리', '트렌드 분석' 요청 시 사용. 후속 작업: 서베이 다시 실행, 재실행, 업데이트, 수정, 보완, 기간 변경, 논문 추가, 이전 결과 개선, 특정 주제만 다시 조사 요청 시에도 반드시 이 스킬을 사용."
---

# Harness Survey Orchestrator

하네스 엔지니어링 논문 서베이를 위한 에이전트 팀을 조율하여, 라이브 검색으로 발굴·분석·**적대적 검증**된 논문만으로 인용 포함 서베이 리포트를 생성하는 통합 스킬.

## 실행 모드: 에이전트 팀 (하이브리드)

- 탐색·분석·검증: 팬아웃/팬인 + 생성-검증 (백그라운드 named Agent + 공유 TaskList + SendMessage 크로스토크)
- 종합: 단일 synthesizer (검증 완료 후 배리어, 크로스토크 불필요)

> 이 환경에는 `TeamCreate`가 없으므로 "에이전트 팀"은 `Agent(run_in_background:true)` + 이름 기반 `SendMessage` + 공유 `TaskCreate/Update` + `_workspace/` 파일 아티팩트로 실현한다. 모든 Agent 호출은 `model:"fable"`.

## 핵심 설계 원칙 — 왜 이 하네스가 이렇게 생겼는가

대상 논문이 지식 컷오프 이후에 나왔기 때문에 **환각 인용이 최대 실패 모드**다. 그래서 이 하네스의 심장은 **citation-verifier의 적대적 검증 게이트**다. 발굴·분석은 넓게 하되, **독립 검증을 통과한 논문만 리포트 본문에 들어간다.** 이 게이트가 서베이의 신뢰성을 지킨다.

## 에이전트 구성

| 팀원 | 에이전트 타입 | 역할 | 스킬 | 출력 |
|------|-------------|------|------|------|
| paper-scout (×2~3) | general-purpose | 동의어 확장 라이브 검색으로 후보 발굴 | paper-discovery | `01_scout/candidates_{axis}.md` |
| paper-analyst (×N) | general-purpose | 논문 세부 분석 | paper-analysis | `02_analysis/{id}.md` |
| citation-verifier | general-purpose | 적대적 실존·날짜·인용 검증 | citation-verification | `03_verification/verdicts.md` |
| survey-synthesizer | general-purpose | 최종 리포트 종합 | survey-synthesis | 최종 리포트 + `04_synthesis/notes.md` |
| (리더 = 오케스트레이터) | — | 조율·dedup·통합·보고 | 이 스킬 | — |

## 워크플로우

### Phase 0: 컨텍스트 확인 (후속 작업 지원)

`_workspace/` 존재 여부로 실행 모드를 결정한다:
- **미존재** → 초기 실행. Phase 1로.
- **존재 + 부분 수정 요청**(예: "검증만 다시", "종합만 갱신", "특정 주제만 추가 조사") → 부분 재실행. 해당 Phase의 에이전트만 재호출하고 이전 산출물을 프롬프트에 전달해 개선 반영.
- **존재 + 새 입력**(예: 기간 변경, 도메인 변경) → 새 실행. 기존 `_workspace/`를 `_workspace_{YYYYMMDD_HHMMSS}/`로 이동 후 Phase 1.

### Phase 1: 준비
1. 사용자 입력 분석 — 도메인 범위, 기간(기본 2026-05~07), 산출물 형태 파악
2. `_workspace/` 및 하위 디렉토리 생성 (00_input, 01_scout, 02_analysis, 03_verification, 04_synthesis)
3. `_workspace/00_input/scope.md`에 범위·동의어 클러스터·기간·소스 목록 기록

### Phase 2: 탐색 (팬아웃, 병렬)
**실행 모드:** 에이전트 팀 (병렬 named 백그라운드 Agent)

1. paper-scout를 검색 축별로 병렬 스폰 (단일 메시지, 복수 Agent 호출, `run_in_background:true`, `model:"fable"`):
   - scout-academic: arXiv/OpenReview/Semantic Scholar/ACL 학술 축
   - scout-industry: 기업 랩 블로그·기술 리포트·벤치마크(SWE-bench/Terminal-Bench) 축
   - (문헌이 넓으면 scout-adjacent: 컨텍스트 엔지니어링·메모리·멀티에이전트 인접 축 추가)
2. 각 scout는 `paper-discovery` 스킬을 읽고 담당 축을 소진할 때까지 검색
3. scout 간 SendMessage로 중복 후보 공유
4. 완료 후 리더가 모든 `candidates_*.md`를 Read → **dedup**하여 `01_scout/candidates.md` 통합본 작성

### Phase 3: 분석 (팬아웃, 병렬)
**실행 모드:** 에이전트 팀 (병렬 named 백그라운드 Agent)

1. 통합 후보를 배치로 분할 (analyst당 3~6편)
2. paper-analyst를 배치 수만큼 병렬 스폰 (`model:"fable"`)
3. 각 analyst는 `paper-analysis` 스킬을 읽고 담당 논문을 실제로 열어 분석 → `02_analysis/{id}.md`
4. analyst 간 논문 연결 발견 시 SendMessage 공유

### Phase 4: 적대적 검증 (생성-검증)
**실행 모드:** 서브/팀 — citation-verifier 1인 (문헌 많으면 축별 병렬)

1. citation-verifier 스폰 (`model:"fable"`). `citation-verification` 스킬 사용
2. 후보 + 분석의 "인용용 핵심 사실"을 독립 검색으로 재확인
3. CONFIRMED / OUT-OF-RANGE / REJECTED / UNVERIFIED 판정 → `03_verification/verdicts.md`
4. 환각·오류 발견 시 scout/analyst에게 SendMessage로 전파
5. **게이트: CONFIRMED만 다음 Phase 본문 대상**

### Phase 5: 종합 (단일)
**실행 모드:** 서브 에이전트 (단일 synthesizer, 크로스토크 불필요)

1. survey-synthesizer 스폰 (`model:"fable"`). `survey-synthesis` 스킬 사용
2. verdicts.md(게이트) + 분석 + 후보 메타를 종합 → 최종 리포트
3. 출력: `/Users/robin/Downloads/harness-paper/harness-engineering-survey-2026.md`
4. 부록에 REJECTED/OUT-OF-RANGE/UNVERIFIED 투명 기록

### Phase 6: 검증 및 보고
1. 리포트 구조·인용 링크 유효성 확인
2. **본문 모든 인용이 verdicts.md에서 CONFIRMED인지 대조** (게이트 준수 확인)
3. `_workspace/` 보존, 사용자에게 요약 보고 + 피드백 요청

## 데이터 흐름

```
[리더] Phase1 scope.md
  → [scout-academic] ─┐
  → [scout-industry] ─┼→ candidates_*.md ─(dedup)→ candidates.md
  → [scout-adjacent] ─┘
  → [analyst×N] → 02_analysis/{id}.md
  → [citation-verifier] → verdicts.md  ★게이트 (CONFIRMED만 통과)
  → [survey-synthesizer] → harness-engineering-survey-2026.md
  → [리더: 게이트 대조 + 보고]
```

## 에러 핸들링

| 상황 | 전략 |
|------|------|
| scout가 후보 0건 | 다른 동의어/소스로 재시도. 그래도 희소하면 "문헌 희소"를 정직하게 보고 |
| analyst 논문 접근 불가 | 확인수준 "접근불가" 표기, 확인 가능 범위만 분석 |
| 검증에서 다수 REJECTED | 정상 — 게이트가 작동한 것. CONFIRMED 규모를 정직하게 보고 |
| CONFIRMED 매우 적음 | 부풀리지 않음. 규모 명시 + OUT-OF-RANGE로 맥락 보강 |
| 에이전트 1인 실패 | 1회 재시도. 재실패 시 누락 명시하고 진행 |
| 데이터 충돌 | 삭제하지 않고 출처 병기 |

## 테스트 시나리오

### 정상 흐름
1. 사용자가 "2026년 5~7월 하네스 엔지니어링 논문 서베이" 요청
2. Phase 1에서 scope.md 작성
3. Phase 2에서 scout 2~3인 병렬 검색 → 후보 dedup
4. Phase 3에서 analyst 병렬 분석
5. Phase 4에서 verifier가 적대적 검증 → CONFIRMED 게이트
6. Phase 5에서 synthesizer가 리포트 생성
7. 예상 결과: `harness-engineering-survey-2026.md` 생성, 본문 인용 전부 CONFIRMED

### 에러 흐름
1. Phase 4에서 후보 다수가 실존 미확인 → REJECTED
2. verifier가 scout에게 SendMessage로 전파
3. synthesizer가 CONFIRMED만으로 리포트 작성, 부록에 REJECTED 사유 기록
4. 리더가 "확인 문헌 N편(범위 내 M편)"으로 규모를 정직하게 보고
```

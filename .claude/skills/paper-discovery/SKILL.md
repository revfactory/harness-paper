---
name: paper-discovery
description: "하네스 엔지니어링(에이전트 하네스·스캐폴딩·컨텍스트 엔지니어링·툴 오케스트레이션·평가 하네스) 관련 논문·프리프린트·기술 리포트를 라이브 웹 검색으로 발굴할 때 사용. 동의어 확장 검색 전략, 소스 목록, 중복 제거, 후보 스키마를 제공한다. 논문 조사·문헌 수집·서베이 대상 발굴 요청 시 사용."
---

# Paper Discovery — 하네스 엔지니어링 논문 발굴 절차

신생 용어를 다루는 문헌 정찰의 핵심은 **동의어 확장**과 **소스 다각화**다. 하나의 검색어·하나의 소스로는 반드시 놓친다.

## 왜 동의어 확장이 필수인가

"Harness Engineering"은 아직 학술 표준 용어가 아니다. 같은 개념이 여러 이름으로 발표된다. 좁은 검색은 문헌의 대부분을 보이지 않게 만든다. 아래 클러스터를 모두 검색어로 순회한다.

### 검색어 클러스터

| 클러스터 | 검색어 예 |
|---------|----------|
| 하네스/스캐폴딩 | `agent harness`, `agentic harness`, `agent scaffolding`, `LLM scaffolding`, `test-time scaffolding` |
| 컨텍스트 엔지니어링 | `context engineering`, `context management LLM agents`, `long-context agent` |
| 툴 오케스트레이션 | `tool orchestration LLM`, `tool-use agent`, `function calling orchestration` |
| 에이전트 프레임워크 | `agentic framework`, `LLM agent framework`, `agent runtime` |
| 코딩 에이전트 | `coding agent`, `SWE agent`, `agentic coding`, `software engineering agent` |
| 메모리/장기과제 | `agent memory`, `long-horizon agent`, `agentic memory` |
| 멀티에이전트 | `multi-agent orchestration`, `agent team`, `multi-agent LLM system` |
| 평가 하네스 | `evaluation harness`, `agent benchmark`, `SWE-bench`, `Terminal-Bench` |

각 클러스터를 기간 한정어(`2026`, `May 2026`, `June 2026`, `July 2026`)와 조합한다.

## 소스 다각화

이 분야는 **산업 리포트가 학술 논문만큼 중요**하다. 다음을 모두 순회한다:

- **학술**: arXiv (cs.AI/cs.SE/cs.CL/cs.LG listing 및 검색), Semantic Scholar, OpenReview, ACL Anthology, Papers with Code
- **산업 랩·기업**: Anthropic·OpenAI·Google DeepMind·Meta AI·Cognition 등의 리서치 블로그·기술 리포트
- **벤치마크/리더보드**: SWE-bench, Terminal-Bench, 관련 리더보드에 연결된 논문

WebSearch로 후보를 찾고, **반드시 WebFetch로 실제 페이지를 열어** 제목·날짜·저자·초록을 확인한다. 스니펫만 보고 기록하면 환각·오정보가 섞인다.

## 검색 절차

1. 담당 축(리더 배정)의 클러스터×기간 조합으로 최소 15개 쿼리 실행
2. 각 히트를 WebFetch로 열어 메타데이터 확인 (날짜가 핵심)
3. 날짜 범위 판정: IN(2026-05~07) / OUT / UNKNOWN — 폐기하지 말고 표기
4. 후보 스키마로 `_workspace/01_scout/candidates_{axis}.md`에 기록
5. 새 후보가 안 나올 때까지(고갈) 동의어를 바꿔 반복
6. 다른 scout와 중복 가능성 있는 후보는 SendMessage로 공유

## 후보 스키마

```markdown
### C{n}. {제목}
- 저자: {저자/기관 또는 "미확인"}
- 날짜: {YYYY-MM-DD} | 범위판정: {IN | OUT | UNKNOWN}
- 소스: {arXiv | OpenReview | 기업블로그 | 벤치마크 | 기타}
- URL: {실제 접근 URL}
- ID: {arXiv ID 등 또는 "-"}
- 한줄요약: {무엇에 관한 것인지}
- 검색어: {찾은 쿼리}
- 하네스관련성: {high | medium | low} — {이유}
- 확인방법: {스니펫만 | WebFetch로 페이지 확인}
```

## 중복 제거 (dedup)

같은 논문이 여러 축·검색어로 잡힌다. 리더가 통합 시 다음 기준으로 병합:
- arXiv ID 동일 → 같은 논문
- 제목 정규화(소문자·공백·구두점 제거) 후 동일/근사 → 같은 논문
- 버전 차이(v1/v2)는 최신 버전으로 통합, 날짜는 최초 submission 기준

## 정직성

- 억지로 개수를 채우지 않는다. 관련 없는 논문을 관련성 high로 표기하지 않는다.
- 범위 밖이어도 매우 관련성 높은 기반 논문은 OUT으로 표기해 남긴다(맥락 제공용).
- 애매한 날짜·접근 불가는 UNKNOWN/접근불가로 표기 — 최종 판정은 검증 단계에 위임한다.

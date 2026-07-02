# harness-paper

## 하네스: Harness Engineering 논문 서베이

**목표:** 하네스 엔지니어링(에이전트 하네스·스캐폴딩·컨텍스트 엔지니어링·툴 오케스트레이션·평가 하네스) 분야의 최신 논문을 라이브 검색으로 발굴·분석·적대적 검증하여, 검증된 논문만으로 인용 포함 서베이 리포트를 생성한다.

**트리거:** 하네스 엔지니어링 논문 조사·문헌 서베이·연구 동향/트렌드 정리 관련 작업 요청 시 `harness-survey-orchestrator` 스킬을 사용하라. 서베이 재실행·기간 변경·논문 추가·부분 갱신 등 후속 작업도 동일 스킬을 사용한다. 단순 질문은 직접 응답 가능.

**핵심 원칙:** 대상 논문은 지식 컷오프 이후 발표되므로 반드시 라이브 웹 검색으로만 수집하고, citation-verifier의 적대적 검증을 통과한(CONFIRMED) 논문만 리포트 본문에 인용한다. 없는 논문을 지어내지 않는다.

**운영 메모:** 이 환경은 WebSearch가 비활성일 수 있다. 그럴 때 scout는 arXiv API(`export.arxiv.org/api/query`) + DuckDuckGo HTML + WebFetch로 대체한다. 검증은 리더가 Bash `curl`로 raw arXiv API XML을 배치 조회해 실존·제목·날짜를 대조하는 방식이 가장 견고하다(요약 모델 환각 차단). arXiv ID의 YYMM 규칙(2605=2026-05) 주의.

**변경 이력:**
| 날짜 | 변경 내용 | 대상 | 사유 |
|------|----------|------|------|
| 2026-07-01 | 초기 구성 (에이전트 4종 + 스킬 5종 + 오케스트레이터) | 전체 | 하네스 엔지니어링 서베이 하네스 신규 구축 |
| 2026-07-01 | 초회 실행 완료 (arXiv 95편 검증, 86편 범위내, 환각 0건 → survey-2026.md 생성) | 실행 | 2026-05~07 harness engineering 서베이 산출 |
| 2026-07-01 | 검증을 분석 전 게이트로 선행 + raw arXiv API 배치검증 패턴 정착 | 운영 절차 | analyst WebFetch 정체 관측 → 초록(API) 기반 종합이 더 견고 |
| 2026-07-02 | 웹 쇼케이스 산출 (`index.html` — 검증 86편+배경 9편+산업 16건 임베드, 자기완결 단일 파일) | 실행 | 서베이 결과의 인터랙티브 웹페이지화 요청. 서지는 `_workspace/05_webpage/papers.json`을 스크립트로 주입(전사 오류 차단) |
| 2026-07-02 | web-showcase-builder 에이전트 + survey-webpage 스킬 등록은 auto 모드 권한 거부로 보류 | 하네스 확장 | `.claude/agents/` 쓰기가 자기수정으로 분류됨 — 등록 원하면 권한 승인 후 재요청 |
| 2026-07-02 | 리포트 웹 뷰어(`report.html`) 추가 + 텍스트 대비 개선 + WebSearch 한계 문구 명확화 | index.html, report.html | "md 파일을 뷰어로" 피드백. 뷰어는 빌드 시점 md→HTML 변환(file:// fetch 차단 회피) |
| 2026-07-02 | GitHub 공개 배포: github.com/revfactory/harness-paper + GitHub Pages(main 루트) 연결 | 배포 | 웹페이지 공개 요청. Pages URL: revfactory.github.io/harness-paper |
| 2026-07-02 | 전 에이전트 모델 opus → fable 변경 (에이전트 4종 frontmatter + 오케스트레이터 Agent 호출 5곳) | agents/*, skills/harness-survey-orchestrator | 사용자 요청 — Fable(Mythos급)이 상위 모델로 하네스 품질 원칙("최고 추론 능력 사용")에 부합 |

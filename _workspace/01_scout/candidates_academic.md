# 학술 축 후보 (Academic Axis Candidates)

- 담당: paper-scout (academic)
- 축: arXiv (cs.AI/cs.SE/cs.CL/cs.LG), OpenReview, Semantic Scholar, ACL Anthology, Papers with Code
- 대상 기간: 2026-05 ~ 2026-07 (IN)
- 발굴 방법: **WebSearch 미가용(이 컨텍스트에서 비활성)** → arXiv API(`export.arxiv.org/api/query`)를 라이브 검색 채널로 사용 + `arxiv.org/abs/{id}` 페이지 WebFetch로 스팟 검증
- 실행 쿼리 수: 12개 arXiv API 검색(각 20~30건) + 6건 개별 abstract 페이지 검증 = 사실상 15+ 각도
- 검증 로그: 아래 6건은 arxiv.org/abs 페이지를 직접 열어 제목·저자·초록을 육안 확인함(API 환각 아님을 교차 확인):
  - 2606.10106 (What makes a harness a harness) — 저자 Sanderson Oliveira de Macedo, 2026-06-08 ✔
  - 2606.20683 (Survey on Agent System and Harness Design) — 저자 J. Guo 외 17인, 2026-06-14 ✔
  - 2606.14249 (HarnessX) — 저자 T. Chen 외 14인, 2026-06-12 ✔
  - 2606.25447 (Interplay of Harness Design and Post-Training) — 저자 K. Kim 외 6인, 2026-06-24 ✔
  - 2606.13643 (Recursive Agent Harnesses) — 저자 E. Lumer 외 3인, 2026-06-11 ✔
  - 2606.06324 (Diagnosing and Repairing Harness Flaws) — 저자 M. Chen 외 4인, 2026-06-04 ✔
- 나머지 후보는 arXiv API 응답(제목·ID·published date·초록)에서 확인. arXiv API는 arXiv 실인덱스를 반환하므로 "WebFetch로 페이지 확인"에 준함. 단, 개별 abstract 페이지 육안 확인분만 "직접확인 ✔"으로 별도 표기.

> 정직성 메모: 이 축은 문헌이 **매우 풍부**했다(희소하지 않음). "harness"라는 용어가 2026년 중반에 arXiv에서 하나의 연구 주제군으로 확립된 정황이 뚜렷하다. 억지 패딩 없이도 후보가 넘쳤으며, 아래는 하네스관련성 high/medium 위주로 선별한 것이다(low/도메인특화 응용은 대부분 제외).

---

## A. 코어 — "하네스" 정면 주제 (하네스관련성 high)

### C1. What makes a harness a harness: necessary and sufficient conditions for an agent harness
- 저자: Sanderson Oliveira de Macedo
- 날짜: 2026-06-08 | 범위판정: IN
- 소스: arXiv (cs.SE/cs.AI)
- URL: https://arxiv.org/abs/2606.10106
- ID: 2606.10106
- 한줄요약: "agent harness"의 구성적(operational) 정의 — 필요충분조건 제시, Claude Code/Codex CLI/Aider/Cline/OpenHands/SWE-agent 6개 실사례에 적용, framework/SDK/orchestrator와 구분.
- 검색어: `abs:"agent harness"` / `ti:harness AND abs:agent`
- 하네스관련성: high — 하네스 정의론의 기준 논문. 서베이 개념 프레임의 앵커.
- 확인방법: WebFetch로 abstract 페이지 직접확인 ✔

### C2. From Question Answering to Task Completion: A Survey on Agent System and Harness Design
- 저자: Jianyuan Guo 외 17인 (Kai Han, Yunhe Wang 등 포함)
- 날짜: 2026-06-14 | 범위판정: IN
- 소스: arXiv (cs.AI/cs.CL)
- URL: https://arxiv.org/abs/2606.20683
- ID: 2606.20683
- 한줄요약: model-harness 관점 종합 서베이. 런타임 책임을 observation/context/control/action/state/verification 6요소로 분해, 모델-하네스 공진화 분석.
- 검색어: `abs:"context engineering"` / `ti:harness AND abs:agent`
- 하네스관련성: high — 본 서베이의 직접적 선행 서베이. 최우선 정독 대상.
- 확인방법: WebFetch로 abstract 페이지 직접확인 ✔

### C3. HarnessX: A Composable, Adaptive, and Evolvable Agent Harness Foundry
- 저자: Tingyang Chen 외 14인 (Kun Shao, Jian Luan 등)
- 날짜: 2026-06-12 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.14249
- ID: 2606.14249
- 한줄요약: 타입드 하네스 프리미티브를 substitution algebra로 조립, trace 기반 멀티에이전트 진화 엔진. 5개 벤치마크 평균 +14.5%.
- 검색어: `abs:"SWE-bench"` / `ti:harness AND abs:agent`
- 하네스관련성: high — 하네스 자동 조립·진화. "하네스 엔지니어링" 실체.
- 확인방법: WebFetch로 abstract 페이지 직접확인 ✔

### C4. The Interplay of Harness Design and Post-Training in LLM Agents
- 저자: Kyungmin Kim, Youngbin Choi, Seoyeon Lee, Suhyeon Jun, Dongwoo Kim, Sangdon Park
- 날짜: 2026-06-24 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.25447
- ID: 2606.25447
- 한줄요약: 하네스 스캐폴딩(툴 노출·설명·per-step 관측 부가정보)이 post-training 효과에 미치는 상호작용을 분포내/툴환경 시프트 하에서 분석.
- 검색어: `ti:harness AND abs:agent`
- 하네스관련성: high — 하네스 설계 × 학습의 결합 효과. 서베이 "모델-하네스 공진화" 섹션 핵심.
- 확인방법: WebFetch로 abstract 페이지 직접확인 ✔

### C5. Recursive Agent Harnesses
- 저자: Elias Lumer, Sahil Sen, Kevin Paul, Vamse Kumar Subbiah
- 날짜: 2026-06-11 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.13643
- ID: 2606.13643
- 한줄요약: 재귀 단위를 (모델 호출이 아닌) 파일시스템 툴·코드실행·플래닝을 갖춘 완전한 에이전트 하네스로 두고 부모가 서브에이전트 하네스를 병렬 스폰하는 패턴 명명·연구. Anthropic dynamic workflows 언급.
- 검색어: `abs:"coding agent" AND abs:harness` / `ti:harness AND abs:agent`
- 하네스관련성: high — 서브에이전트 오케스트레이션의 하네스 층위 정식화.
- 확인방법: WebFetch로 abstract 페이지 직접확인 ✔

### C6. From Failed Trajectories to Reliable LLM Agents: Diagnosing and Repairing Harness Flaws
- 저자: Mengzhuo Chen, Junjie Wang, Zhe Liu, Yawen Wang, Qing Wang
- 날짜: 2026-06-04 | 범위판정: IN
- 소스: arXiv (cs.SE)
- URL: https://arxiv.org/abs/2606.06324
- ID: 2606.06324
- 한줄요약: HarnessFix — 트레이스를 중간표현으로 컴파일해 하네스 결함(실행환경·툴 인터페이스·컨텍스트·오케스트레이션·관측·검증·거버넌스) 진단·패치. 하네스 구성요소 7분류 제시.
- 검색어: `abs:"agent harness"` / `abs:"Terminal-Bench"`
- 하네스관련성: high — 하네스 결함 진단·수리 프레임워크.
- 확인방법: WebFetch로 abstract 페이지 직접확인 ✔

### C7. Self-Harness: Harnesses That Improve Themselves
- 저자: 미확인 (API 초록 확인)
- 날짜: 2026-06-08 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.09498
- ID: 2606.09498
- 한줄요약: 에이전트가 스스로 하네스 약점을 채굴→최소 수정 제안→자율 검증하는 자기개선 하네스. Terminal-Bench-2.0에서 검증.
- 검색어: `abs:"agent harness"` / `abs:"Terminal-Bench"`
- 하네스관련성: high — 자기개선 하네스.
- 확인방법: arXiv API 초록 확인

### C8. Evolving Agents in the Dark: Retrospective Harness Optimization via Self-Preference
- 저자: 미확인
- 날짜: 2026-06-04 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.05922
- ID: 2606.05922
- 한줄요약: 정답 검증 없이 과거 트레이스만으로 self-preference 기반 하네스 최적화(자기지도).
- 검색어: `abs:"agent harness"`
- 하네스관련성: high — ground-truth 없는 하네스 진화.
- 확인방법: arXiv API 초록 확인

### C9. HarnessBridge: Learnable Bidirectional Controller for LLM Agent Harness
- 저자: 미확인
- 날짜: 2026-06-11 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.12882
- ID: 2606.12882
- 한줄요약: 에이전트-환경 인터페이스를 양방향 관측·행동 투영으로 파라미터화한 학습형 플러그인 하네스 컨트롤러. 토큰 사용↓, Terminal-Bench 2.0.
- 검색어: `abs:"Terminal-Bench"` / `ti:harness AND abs:agent`
- 하네스관련성: high — 학습형 하네스 컨트롤러.
- 확인방법: arXiv API 초록 확인

### C10. LLM-as-Code: Agentic Programming for Agent Harness
- 저자: 미확인
- 날짜: 2026-06-14 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.15874
- ID: 2606.15874
- 한줄요약: LLM을 결정론적 제어흐름 내 추론 컴포넌트로 배치, 실행 이력을 DAG로 형성하는 program-governed 하네스 아키텍처.
- 검색어: `ti:harness AND abs:agent`
- 하네스관련성: high — 프로그램 지배형 하네스 아키텍처.
- 확인방법: arXiv API 초록 확인

### C11. LemonHarness Technical Report
- 저자: 미확인
- 날짜: 2026-06-23 | 범위판정: IN
- 소스: arXiv (기술 리포트)
- URL: https://arxiv.org/abs/2606.24311
- ID: 2606.24311
- 한줄요약: 장기 과제용 하네스 — 상태 변경을 정의된 워크스페이스 내로 제약하고 time-aware 실행 메커니즘 추가.
- 검색어: `abs:"Terminal-Bench"`
- 하네스관련성: high — 실전 하네스 기술 리포트.
- 확인방법: arXiv API 초록 확인

### C12. Harnesser/Continual Harness: Online Adaptation for Self-Improving Foundation Agents
- 저자: 미확인
- 날짜: 2026-05-11 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2605.09998
- ID: 2605.09998
- 한줄요약: 리셋 없이 단일 embodied 에이전트 실행 내에서 프롬프트·서브에이전트·메모리를 자동 정제하는 자기개선 하네스.
- 검색어: `abs:"long-horizon" AND abs:agent AND abs:scaffold`
- 하네스관련성: high — 온라인 하네스 적응.
- 확인방법: arXiv API 초록 확인

### C13. SIA: Self Improving AI with Harness & Weight Updates
- 저자: 미확인
- 날짜: 2026-05-26 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2605.27276
- ID: 2605.27276
- 한줄요약: 하네스 업데이트 + 가중치 업데이트를 결합해 법률·최적화·생명정보 도메인에서 자율 성능 향상.
- 검색어: `abs:"long-horizon" AND abs:agent AND abs:scaffold`
- 하네스관련성: high — 하네스+웨이트 공동 자기개선.
- 확인방법: arXiv API 초록 확인

### C14. The Last Harness You'll Ever Build
- 저자: 미확인
- 날짜: 2026-04-22 | 범위판정: OUT (2026-04) — 하네스 엔지니어링 자동화 직접 주제로 맥락 보강용 유지
- 소스: arXiv
- URL: https://arxiv.org/abs/2604.21003
- ID: 2604.21003
- 한줄요약: 반복 최적화 루프로 최적 프롬프트·툴·오케스트레이션 로직을 학습하는 2층 하네스 엔지니어링 자동화 프레임워크.
- 검색어: `abs:"tool orchestration" AND abs:agent`
- 하네스관련성: high — 하네스 엔지니어링 자동화. 범위밖이나 개념적으로 핵심.
- 확인방법: arXiv API 초록 확인

### C15. NOVA: A Verification-Aware Agent Harness for Architecture Evolution in Industrial Recommender Systems
- 저자: 미확인
- 날짜: 2026-06-25 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.27243
- ID: 2606.27243
- 한줄요약: 검증-인식(verification-aware) 하네스로 산업 추천 모델 아키텍처 자동 진화, 다단계 태스크 라우팅.
- 검색어: `abs:"agent harness"` / `abs:"coding agent" AND abs:harness`
- 하네스관련성: high — 검증 게이트 내장 하네스(응용).
- 확인방법: arXiv API 초록 확인

### C16. AOHP: An Open-Source OS-Level Agent Harness for Personalized, Efficient and Secure Interaction
- 저자: 미확인
- 날짜: 2026-06-22 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.23449
- ID: 2606.23449
- 한줄요약: 에이전트를 1급 액터로 두는 안드로이드 OS 레벨 하네스 — 개인화 구성·효율 인터페이스·안전 정보흐름.
- 검색어: `abs:"agent harness"` / `ti:harness AND abs:agent`
- 하네스관련성: high — OS 레벨 하네스.
- 확인방법: arXiv API 초록 확인

### C17. ActPlane: Programmable OS-Level Policy Enforcement for Agent Harnesses
- 저자: 미확인
- 날짜: 2026-06-23 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.25189
- ID: 2606.25189
- 한줄요약: eBPF 기반 OS 커널 정책 엔진으로 툴콜 인터셉트를 넘어선 실행경로 커버·안전 정책 강제.
- 검색어: `ti:harness AND abs:agent`
- 하네스관련성: high — 하네스 보안/거버넌스 강제 레이어.
- 확인방법: arXiv API 초록 확인

### C18. Harness-MU: A Safe, Governed, and Effective Harness for Multi-User LLM Agents
- 저자: 미확인
- 날짜: 2026-06-20 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.21856
- ID: 2606.21856
- 한줄요약: 언어 생성과 안전 오케스트레이션을 분리해 다중 주체(multi-principal) 거버넌스를 보장하는 모델 무관 하네스.
- 검색어: `ti:harness AND abs:agent`
- 하네스관련성: high — 멀티유저 안전 하네스.
- 확인방법: arXiv API 초록 확인

### C19. Building Agent Harnesses for Scientific Curation from Multimodal Sources
- 저자: 미확인
- 날짜: 2026-06-19 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.21005
- ID: 2606.21005
- 한줄요약: Beaver 하네스 — 멀티모달 증거 툴링 + 태스크 스캐폴딩으로 논문 구조화 정보 추출.
- 검색어: `abs:"agent harness"` / `ti:harness AND abs:agent`
- 하네스관련성: high — 하네스 구축 사례 연구.
- 확인방법: arXiv API 초록 확인

### C20. Layer-Isolated Evaluation: Gating the Deterministic Scaffold of a Production LLM Agent with a No-LLM, Regression-Locked Test Harness
- 저자: 미확인
- 날짜: 2026-06-10 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.11686
- ID: 2606.11686
- 한줄요약: 에이전트를 레이어로 분해, No-LLM 결정론적 어서션 슬라이스로 성능 회귀를 격리·지역화하는 컴포넌트 테스트 하네스.
- 검색어: `ti:harness AND abs:agent`
- 하네스관련성: high — 하네스 평가/회귀 테스트 방법론.
- 확인방법: arXiv API 초록 확인

### C21. Claw-SWE-Bench: A Benchmark for Evaluating OpenClaw-style Agent Harnesses on Coding Tasks
- 저자: 미확인
- 날짜: 2026-06-10 | 범위판정: IN
- 소스: arXiv (벤치마크)
- URL: https://arxiv.org/abs/2606.12344
- ID: 2606.12344
- 한줄요약: 8개 언어 350 GitHub 이슈, adapter 프로토콜로 이질적 하네스를 고정 프롬프트·워크스페이스 계약 하에 공정 비교.
- 검색어: `abs:"coding agent" AND abs:harness` / `ti:harness AND abs:agent`
- 하네스관련성: high — 하네스 비교 벤치마크. (주의: "OpenClaw"라는 명칭은 실존 확인 필요 — 벤치마크 축과 중복 가능)
- 확인방법: arXiv API 초록 확인

### C22. PhoneHarness: Harnessing Phone-Use Agents through Mixed GUI, CLI, and Tool Actions
- 저자: 미확인
- 날짜: 2026-06-12 | 범위판정: IN
- 소스: arXiv (벤치마크+하네스)
- URL: https://arxiv.org/abs/2606.14832
- ID: 2606.14832
- 한줄요약: GUI·CLI·툴 혼합 액션을 라우팅하는 폰-사용 에이전트 하네스+벤치마크.
- 검색어: `ti:harness AND abs:agent`
- 하네스관련성: high — 혼합 액션 하네스.
- 확인방법: arXiv API 초록 확인

### C23. A Process Harness for Uplifting Legacy Workflows to Agentic BPM: Design and Realization in CUGA FLO
- 저자: 미확인
- 날짜: 2026-06-25 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.27188
- ID: 2606.27188
- 한줄요약: 결정론적 워크플로 엔진을 감싸 추론·적응을 부여하되 구조 제어를 유지하는 정책 지배 에이전트 계층(process harness).
- 검색어: `ti:harness AND abs:agent`
- 하네스관련성: medium — 프로세스/BPM 하네스(응용).
- 확인방법: arXiv API 초록 확인

### C24. Toward Self-Evolution-Ready Workflow Harnesses: A Reversible Migration Path and Convertibility Taxonomy for Expert LLM Pipelines
- 저자: 미확인
- 날짜: 2026-06-15 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.24598
- ID: 2606.24598
- 한줄요약: Strangler-Fig 마이그레이션으로 레거시 워크플로를 합성 가능한 스테이지로 리팩터, readiness taxonomy와 system harness 라우팅.
- 검색어: `ti:harness AND abs:agent`
- 하네스관련성: medium — 워크플로 하네스 진화 경로.
- 확인방법: arXiv API 초록 확인

### C25. AutoMegaKernel: A Statically-Checked Agent Harness for Self-Retargeting Megakernel Synthesis
- 저자: 미확인
- 날짜: 2026-06-08 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.09682
- ID: 2606.09682
- 한줄요약: 정적 스케줄 검증(교착·경쟁 없음 인증)을 갖춘 자기개선 CUDA 커널 합성 에이전트 하네스.
- 검색어: `ti:harness AND abs:agent`
- 하네스관련성: medium — 정적 검증 내장 하네스(응용).
- 확인방법: arXiv API 초록 확인

---

## B. 코딩/SWE 에이전트 아키텍처·스캐폴딩 (하네스관련성 high~medium)

### C26. Inside the Scaffold: A Source-Code Taxonomy of Coding Agent Architectures
- 저자: 미확인
- 날짜: 2026-04-03 | 범위판정: OUT (2026-04) — 맥락 보강용 유지
- 소스: arXiv (cs.SE)
- URL: https://arxiv.org/abs/2604.03515
- ID: 2604.03515
- 한줄요약: 13개 오픈소스 코딩 에이전트를 12개 아키텍처 차원으로 분석한 소스코드 수준 스캐폴딩 분류학.
- 검색어: `abs:"agent scaffolding"`
- 하네스관련성: high — 하네스/스캐폴딩 분류학. 범위밖이나 개념 핵심.
- 확인방법: arXiv API 초록 확인

### C27. Position: Coding Benchmarks Are Misaligned with Agentic Software Engineering
- 저자: 미확인
- 날짜: 2026-06-16 | 범위판정: IN
- 소스: arXiv (cs.SE, position paper)
- URL: https://arxiv.org/abs/2606.17799
- ID: 2606.17799
- 한줄요약: 현행 벤치마크가 모델과 하네스를 혼동하고, 유효한 대안을 패널티화하며, 컴포넌트 수준 이터레이션 신호가 없다고 주장.
- 검색어: `abs:"coding agent" AND abs:harness`
- 하네스관련성: high — 하네스-모델 분리 평가론.
- 확인방법: arXiv API 초록 확인

### C28. ClayBuddy: A Framework, Evaluation, & Mitigation of Coding Agent Failures
- 저자: 미확인
- 날짜: 2026-06-13 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.19380
- ID: 2606.19380
- 한줄요약: 코딩 에이전트 실패를 underspecification·capability·harness 오류 3종으로 분류, 하네스 수정+세션 내 컨텍스트 편집으로 완화.
- 검색어: `abs:"coding agent" AND abs:harness`
- 하네스관련성: high — 하네스 오류 분류·완화. (명칭 "ClayBuddy" 실존 확인 권장)
- 확인방법: arXiv API 초록 확인

### C29. SWE-MeM: Learning Adaptive Memory Management for Long-Horizon Coding Agents
- 저자: 미확인
- 날짜: 2026-06-26 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.28434
- ID: 2606.28434
- 한줄요약: SE 에이전트의 능동적 메모리 관리(flexible memory tool 결정)를 학습하는 훈련 프레임워크.
- 검색어: `abs:"SWE-bench"`
- 하네스관련성: high — 코딩 에이전트 메모리 하네스.
- 확인방법: arXiv API 초록 확인

### C30. FastContext: Training Efficient Repository Explorer for Coding Agents
- 저자: 미확인
- 날짜: 2026-06-12 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.14066
- ID: 2606.14066
- 한줄요약: 전용 탐색 서브에이전트로 해결률 최대 +5.5% 개선, 토큰 60%↓.
- 검색어: `abs:"SWE-bench"`
- 하네스관련성: medium — 컨텍스트/탐색 서브에이전트 하네스 구성요소.
- 확인방법: arXiv API 초록 확인

### C31. Dockerless: Environment-Free Program Verifier for Coding Agents
- 저자: 미확인
- 날짜: 2026-06-26 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.28436
- ID: 2606.28436
- 한줄요약: 환경 없는 패치 검증기 — 에이전트 리포지토리 탐색으로 SWE-bench Verified 62.0%.
- 검색어: `abs:"SWE-bench"`
- 하네스관련성: medium — 검증 하네스 컴포넌트.
- 확인방법: arXiv API 초록 확인

### C32. Unlocking Model Potentials Through Adaptive Multi-Agent Scaffolding for Efficient Issue Resolution
- 저자: 미확인
- 날짜: 2026-06-24 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.25514
- ID: 2606.25514
- 한줄요약: icat-agent — 이벤트 기반 메시징의 탈중앙 멀티에이전트 스캐폴딩, SWE-bench Pro 67.4%.
- 검색어: `abs:"agent scaffolding"` / `abs:"long-horizon"...scaffold`
- 하네스관련성: high — 멀티에이전트 스캐폴딩.
- 확인방법: arXiv API 초록 확인

### C33. Socratic-SWE: Self-Evolving Coding Agents via Trace-Derived Agent Skills
- 저자: 미확인
- 날짜: 2026-06-05 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.07412
- ID: 2606.07412
- 한줄요약: 해결 트레이스를 agent skill로 증류해 수리 과제 생성하는 폐루프 자기진화. Terminal-Bench 2.0 개선.
- 검색어: `abs:"Terminal-Bench"`
- 하네스관련성: medium — 스킬 기반 자기진화 하네스.
- 확인방법: arXiv API 초록 확인

### C34. Strained Coherence: A Pre-Failure Signal in Coding Agent Execution Trajectories
- 저자: 미확인
- 날짜: 2026-06-05 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.07889
- ID: 2606.07889
- 한줄요약: 에이전트가 문제를 인지하고도 반대로 행동하는 "strained coherence" 실패 패턴 분석. Terminal-Bench-2.
- 검색어: `abs:"Terminal-Bench"`
- 하네스관련성: medium — 하네스 실패 진단 신호.
- 확인방법: arXiv API 초록 확인

### C35. Sakana Fugu Technical Report
- 저자: Sakana AI (기관, 세부 미확인)
- 날짜: 2026-06-19 | 범위판정: IN
- 소스: arXiv (기술 리포트)
- URL: https://arxiv.org/abs/2606.21228
- ID: 2606.21228
- 한줄요약: 오케스트레이터 모델이 적응형 agentic scaffold를 동적 고안, SWE-Bench Pro/Terminal Bench SOTA.
- 검색어: `abs:"agent scaffolding"` / `abs:"Terminal-Bench"`
- 하네스관련성: high — 동적 스캐폴드 생성. (산업 랩 리포트 — scout-industry와 중복 가능)
- 확인방법: arXiv API 초록 확인

---

## C. 컨텍스트 엔지니어링 (하네스관련성 high~medium)

### C36. Less Context, Better Agents: Efficient Context Engineering for Long-Horizon Tool-Using LLM Agents
- 저자: 미확인
- 날짜: 2026-06-08 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.10209
- ID: 2606.10209
- 한줄요약: 요약 동반 pruning으로 엔터프라이즈 워크플로 91.6% 완료 + 토큰 대폭 절감.
- 검색어: `abs:"context engineering"`
- 하네스관련성: high — 컨텍스트 엔지니어링 정면.
- 확인방법: arXiv API 초록 확인

### C37. Plans Don't Persist: Why Context Management Is Load Bearing for LLM Agents
- 저자: 미확인
- 날짜: 2026-06-22 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.22953
- ID: 2606.22953
- 한줄요약: 에이전트가 계획을 내부 상태로 이월하지 못하고 컨텍스트에 계획이 보여야만 의존한다는 진단 분석.
- 검색어: `abs:"context management" AND abs:agent`
- 하네스관련성: high — 컨텍스트 관리 필수성 실증.
- 확인방법: arXiv API 초록 확인

### C38. Governance Decay: How Context Compaction Silently Erases Safety Constraints in Long-Horizon LLM Agents
- 저자: 미확인
- 날짜: 2026-06-21 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.22528
- ID: 2606.22528
- 한줄요약: 컨텍스트 compaction이 안전 제약을 지운다는 ConstraintRot 벤치, Constraint Pinning 완화.
- 검색어: `abs:"context management" AND abs:agent`
- 하네스관련성: high — 컨텍스트 압축의 안전 부작용.
- 확인방법: arXiv API 초록 확인

### C39. LLM Agents Are Latent Context Managers: Eliciting Self-Managed Context via a Proprioceptive Dashboard
- 저자: 미확인
- 날짜: 2026-06-29 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.30005
- ID: 2606.30005
- 한줄요약: VISTA — 워킹 메모리를 타입드 블록으로 노출하고 토큰 사용·접근 이력을 런타임 대시보드로 추적(훈련 불필요).
- 검색어: `abs:"context management" AND abs:agent`
- 하네스관련성: high — 자기관리 컨텍스트 인터페이스.
- 확인방법: arXiv API 초록 확인

### C40. Learning Agent-Compatible Context Management for Long-Horizon Tasks
- 저자: 미확인
- 날짜: 2026-05-29 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2605.30785
- ID: 2605.30785
- 한줄요약: AdaCoM — 외부 LLM을 학습시켜 frozen 에이전트의 컨텍스트를 유연 수정(RL).
- 검색어: `abs:"context management" AND abs:agent`
- 하네스관련성: high — 외부 컨텍스트 관리자 하네스.
- 확인방법: arXiv API 초록 확인

### C41. TokenPilot: Cache-Efficient Context Management for LLM Agents
- 저자: 미확인
- 날짜: 2026-06-15 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.17016
- ID: 2606.17016
- 한줄요약: ingestion-aware compaction + lifecycle-aware eviction으로 프롬프트 캐시 연속성 유지하며 추론비 절감.
- 검색어: `abs:"context management" AND abs:agent`
- 하네스관련성: medium — 캐시 효율 컨텍스트 관리.
- 확인방법: arXiv API 초록 확인

### C42. ACE: Pluggable Adaptive Context Elasticizer across Agents
- 저자: 미확인
- 날짜: 2026-06-30 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.31564
- ID: 2606.31564
- 한줄요약: 무손실 메시지 저장 + raw/abstract/drop 이력 적응 오케스트레이션 플러그앤플레이 모듈.
- 검색어: `abs:"context management" AND abs:agent` / `abs:"agentic framework"`
- 하네스관련성: medium — 컨텍스트 탄력화 모듈.
- 확인방법: arXiv API 초록 확인

### C43. A Language for Describing Agentic LLM Contexts (ACDL)
- 저자: 미확인
- 날짜: 2026-05-03 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2605.01920
- ID: 2605.01920
- 한줄요약: LLM 컨텍스트 구성·진화를 문서화하는 형식 명세 언어 ACDL.
- 검색어: `abs:"context engineering"`
- 하네스관련성: medium — 컨텍스트 형식화.
- 확인방법: arXiv API 초록 확인

### C44. A Dataset of Agentic AI Coding Tool Configurations
- 저자: 미확인
- 날짜: 2026-05-08 | 범위판정: IN
- 소스: arXiv (데이터셋)
- URL: https://arxiv.org/abs/2605.08435
- ID: 2605.08435
- 한줄요약: 5개 AI 코딩 툴, 4,738 리포지토리에서 15,591개 설정 아티팩트 큐레이션.
- 검색어: `abs:"context engineering"`
- 하네스관련성: medium — 하네스/에이전트 설정 실증 데이터.
- 확인방법: arXiv API 초록 확인

---

## D. 툴 오케스트레이션 (하네스관련성 high~medium)

### C45. MAVEN: Improving Generalization in Agentic Tool Calling
- 저자: 미확인
- 날짜: 2026-05-29 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2605.30738
- ID: 2605.30738
- 한줄요약: 구조적 분해 + 적응형 툴 오케스트레이션 + 중간 검증의 모듈형 추론 스캐폴드.
- 검색어: `abs:"tool orchestration" AND abs:agent`
- 하네스관련성: high — 툴 오케스트레이션 스캐폴드.
- 확인방법: arXiv API 초록 확인

### C46. The Evolution of Tool Use in LLM Agents: From Single-Tool Call to Multi-Tool Orchestration
- 저자: 미확인
- 날짜: 2026-03-24 | 범위판정: OUT (2026-03) — 맥락 보강용 유지
- 소스: arXiv (survey/review)
- URL: https://arxiv.org/abs/2603.22862
- ID: 2603.22862
- 한줄요약: 단일 툴 호출→장기 다중 툴 오케스트레이션 진화를 플래닝·안전·효율 차원으로 종합한 리뷰.
- 검색어: `abs:"tool orchestration" AND abs:agent`
- 하네스관련성: high — 툴 오케스트레이션 서베이. 범위밖이나 배경 필수.
- 확인방법: arXiv API 초록 확인

### C47. SING: Synthetic Intention Graph for Scalable Active Tool Discovery in LLM Agents
- 저자: 미확인
- 날짜: 2026-06-15 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.16591
- ID: 2606.16591
- 한줄요약: 7,471개 툴 생태계에서 의도-인식 동적 툴 검색 프레임워크.
- 검색어: `abs:"agent harness"`
- 하네스관련성: medium — 대규모 툴 디스커버리(하네스 구성요소).
- 확인방법: arXiv API 초록 확인

### C48. Training LLMs for Multi-Step Tool Orchestration with Constrained Data Synthesis
- 저자: 미확인
- 날짜: 2026-03-25 | 범위판정: OUT (2026-03) — 맥락 보강용
- 소스: arXiv
- URL: https://arxiv.org/abs/2603.24709
- ID: 2603.24709
- 한줄요약: graduated reward decomposition + API-응답 환경 합성으로 다단계 툴 오케스트레이션 RL 훈련.
- 검색어: `abs:"tool orchestration" AND abs:agent`
- 하네스관련성: medium — 툴 오케스트레이션 학습.
- 확인방법: arXiv API 초록 확인

---

## E. 에이전트 메모리 (하네스관련성 high~medium)

### C49. Are We Ready For An Agent-Native Memory System?
- 저자: 미확인
- 날짜: 2026-06-23 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.24775
- ID: 2606.24775
- 한줄요약: 12개 에이전트 메모리 시스템을 5개 벤치마크로 체계 평가 — 단일 아키텍처 지배 없음, 워크로드 정합 의존.
- 검색어: `abs:"agent memory"`
- 하네스관련성: high — 메모리 시스템 서베이/평가.
- 확인방법: arXiv API 초록 확인

### C50. Governed Shared Memory for Multi-Agent LLM Systems
- 저자: 미확인
- 날짜: 2026-06-23 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.24535
- ID: 2606.24535
- 한줄요약: fleet-memory 문제 4대 실패모드 정식화, scoped retrieval·temporal supersession·provenance의 MemClaw 프로덕션 서비스.
- 검색어: `abs:"agent memory"`
- 하네스관련성: high — 멀티에이전트 공유 메모리 거버넌스. (명칭 "MemClaw" 실존 확인 권장)
- 확인방법: arXiv API 초록 확인

### C51. OpenRath: Session-Centered Runtime State for Agent Systems
- 저자: 미확인
- 날짜: 2026-06-17 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.19409
- ID: 2606.19409
- 한줄요약: Session을 1급 런타임 추상으로 두어 branch·inspect·replay 가능한 멀티에이전트 상태 관리 프로그래밍 모델.
- 검색어: `abs:"agent memory"`
- 하네스관련성: high — 런타임 상태/세션 관리(하네스 상태 층).
- 확인방법: arXiv API 초록 확인

### C52. Control-Plane Placement Shapes Forgetting: An Architectural Study of Agent Memory Across Thirteen System Configurations
- 저자: 미확인
- 날짜: 2026-06-14 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.15903
- ID: 2606.15903
- 한줄요약: 13개 메모리 파이프라인 구성 비교 — mutation-time LLM hook이 intent-aware 삭제 회복.
- 검색어: `abs:"agent memory"`
- 하네스관련성: medium — 메모리 아키텍처 비교연구.
- 확인방법: arXiv API 초록 확인

### C53. MemDelta: Controlled Baselines and Hidden Confounds in Agent Memory Evaluation
- 저자: 미확인
- 날짜: 2026-06-29 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.29914
- ID: 2606.29914
- 한줄요약: 통제 평가 프로토콜 — 임베딩 교체가 정확도를 ±6.2pp 이동, RAG vs full-context 순위 역전.
- 검색어: `abs:"agent memory"`
- 하네스관련성: medium — 메모리 평가 방법론.
- 확인방법: arXiv API 초록 확인

---

## F. 멀티에이전트 오케스트레이션 (하네스관련성 high~medium)

### C54. Reward Modeling for Multi-Agent Orchestration
- 저자: 미확인
- 날짜: 2026-06-11 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.13598
- ID: 2606.13598
- 한줄요약: OrchRM — 인간 주석 없이 오케스트레이션 품질을 자기지도 평가, 토큰 효율 최대 10x.
- 검색어: `abs:"multi-agent orchestration"`
- 하네스관련성: high — 오케스트레이션 보상 모델링.
- 확인방법: arXiv API 초록 확인

### C55. LEMON: Learning Executable Multi-Agent Orchestration via Counterfactual Reinforcement Learning
- 저자: 미확인
- 날짜: 2026-05-14 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2605.14483
- ID: 2605.14483
- 한줄요약: 역사실 RL로 역할·용량·의존성을 통합한 실행형 오케스트레이션 명세 생성.
- 검색어: `abs:"multi-agent orchestration"`
- 하네스관련성: high — 실행형 오케스트레이션 학습.
- 확인방법: arXiv API 초록 확인

### C56. PerspectiveGap: A Benchmark for Multi-Agent Orchestration Prompting
- 저자: 미확인
- 날짜: 2026-06-07 | 범위판정: IN
- 소스: arXiv (벤치마크)
- URL: https://arxiv.org/abs/2606.08878
- ID: 2606.08878
- 한줄요약: 110개 시나리오, 다양한 모델군에서 멀티에이전트 오케스트레이션 프롬프트 작성 능력 평가.
- 검색어: `abs:"multi-agent orchestration"`
- 하네스관련성: medium — 오케스트레이션 프롬프팅 벤치.
- 확인방법: arXiv API 초록 확인

### C57. Polar: Agentic RL on Any Harness at Scale
- 저자: 미확인
- 날짜: 2026-05-22 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2605.24220
- ID: 2605.24220
- 한줄요약: 에이전트 하네스를 블랙박스로 취급하는 확장형 비동기 RL 프레임워크. 코드 과제 +22.6점.
- 검색어: `abs:"multi-agent orchestration"`
- 하네스관련성: high — 하네스 무관 RL 학습 프레임워크.
- 확인방법: arXiv API 초록 확인

### C58. How Task Structure Limits Multi-Agent Success: An Information-Theoretic Analysis
- 저자: 미확인
- 날짜: 2026-06-11 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.13733
- ID: 2606.13733
- 한줄요약: MAS 성공이 태스크 제약 연결성에 의존함을 정보이론적으로 증명(SWE-bench 데이터).
- 검색어: `abs:"SWE-bench"`
- 하네스관련성: medium — 멀티에이전트 한계 이론.
- 확인방법: arXiv API 초록 확인

---

## G. 평가·벤치마크 하네스 / 아키텍처 진화 (하네스관련성 high~medium)

### C59. SEAGym: An Evaluation Environment for Self-Evolving LLM Agents
- 저자: 미확인
- 날짜: 2026-06-16 | 범위판정: IN
- 소스: arXiv (벤치마크/환경)
- URL: https://arxiv.org/abs/2606.17546
- ID: 2606.17546
- 한줄요약: 하네스 업데이트를 train/val/test/replay 뷰로 측정하고 비용 추적하는 자기진화 에이전트 평가 환경. Terminal-Bench 2.0.
- 검색어: `abs:"agent harness"` / `abs:"Terminal-Bench"`
- 하네스관련성: high — 하네스 진화 평가 환경.
- 확인방법: arXiv API 초록 확인

### C60. Dissecting model behavior through agent trajectories
- 저자: 미확인
- 날짜: 2026-06-16 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.17454
- ID: 2606.17454
- 한줄요약: 138k 프론티어 모델 트레이스로 모델 능력과 하네스 행동 사이 intent-execution gap 분석.
- 검색어: `abs:"agent harness"` / `abs:"Terminal-Bench"`
- 하네스관련성: high — 모델 vs 하네스 행동 분리 분석.
- 확인방법: arXiv API 초록 확인

### C61. APEX: Adaptive Principle EXtraction — A Three-Layer Self-Evolution Framework for Production AI Agents
- 저자: 미확인
- 날짜: 2026-06-13 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.15363
- ID: 2606.15363
- 한줄요약: 하네스·행동원칙·워크플로 토폴로지를 동시 공진화하는 3층 프레임워크(프로덕션 배포).
- 검색어: `abs:"agent harness"` / `abs:"Terminal-Bench"`
- 하네스관련성: high — 다층 하네스 자기진화.
- 확인방법: arXiv API 초록 확인

### C62. ADK Arena: Evaluating Agent Development Kits via LLM-as-a-Developer
- 저자: 미확인
- 날짜: 2026-06-04 | 범위판정: IN
- 소스: arXiv (벤치마크)
- URL: https://arxiv.org/abs/2606.05548
- ID: 2606.05548
- 한줄요약: 51개 Python ADK 프레임워크를 LLM 코딩 에이전트로 SWE-bench·Terminal-Bench에서 자동 평가.
- 검색어: `abs:"Terminal-Bench"`
- 하네스관련성: high — 에이전트 개발 킷(하네스 프레임워크) 비교.
- 확인방법: arXiv API 초록 확인

### C63. RigorBench: Benchmarking Engineering Process Discipline in Autonomous AI Coding Agents
- 저자: 미확인
- 날짜: 2026-06-21 | 범위판정: IN
- 소스: arXiv (벤치마크)
- URL: https://arxiv.org/abs/2606.22678
- ID: 2606.22678
- 한줄요약: 계획·검증·복구·abstention·전이 무결성 차원의 프로세스 규율 측정 최초 벤치.
- 검색어: `abs:"coding agent" AND abs:harness`
- 하네스관련성: medium — 하네스 프로세스 규율 평가.
- 확인방법: arXiv API 초록 확인

### C64. StaminaBench: Stress-Testing Coding Agents over 100 Interaction Turns
- 저자: 미확인
- 날짜: 2026-06-17 | 범위판정: IN
- 소스: arXiv (벤치마크)
- URL: https://arxiv.org/abs/2606.19613
- ID: 2606.19613
- 한줄요약: 100턴 절차적 변경요청 하에서 에이전트 하네스 회복력 측정.
- 검색어: `abs:"agent harness"` / `abs:"coding agent" AND abs:harness`
- 하네스관련성: medium — 장기 상호작용 하네스 스트레스 테스트.
- 확인방법: arXiv API 초록 확인

### C65. AgentBeats: Agentifying Agent Assessment for Openness, Standardization, and Reproducibility
- 저자: 미확인
- 날짜: 2026-06-11 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.13608
- ID: 2606.13608
- 한줄요약: judge agent + 표준 프로토콜(A2A, MCP)로 재현 가능한 멀티에이전트 평가.
- 검색어: `abs:"coding agent" AND abs:harness`
- 하네스관련성: medium — 평가 하네스 표준화.
- 확인방법: arXiv API 초록 확인

### C66. Hardening Agent Benchmarks with Adversarial Hacker-Fixer Loops
- 저자: 미확인
- 날짜: 2026-06-08 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.08960
- ID: 2606.08960
- 한줄요약: hacker-fixer-solver 교대로 exploit-저항 검증기 구축, Terminal-Bench 323개 해킹 가능 태스크 발견.
- 검색어: `abs:"Terminal-Bench"`
- 하네스관련성: medium — 평가 하네스 견고화(reward hacking 대응).
- 확인방법: arXiv API 초록 확인

### C67. AgentSpec: Understanding Embodied Agent Scaffolds Through Controlled Composition
- 저자: 미확인
- 날짜: 2026-06-12 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.14674
- ID: 2606.14674
- 한줄요약: 컴포넌트 인터페이스 표준화로 embodied 에이전트의 memory·reasoning·reflection 모듈 상호작용 분석.
- 검색어: `abs:"long-horizon" AND abs:agent AND abs:scaffold`
- 하네스관련성: high — 스캐폴드 컴포넌트 통제 조합 분석.
- 확인방법: arXiv API 초록 확인

### C68. Act As a Real Researcher: A Suite of Benchmarks Evaluating Frontier LLMs and Agentic Harnesses in Research Lifecycle
- 저자: 미확인
- 날짜: 2026-06-05 | 범위판정: IN
- 소스: arXiv (벤치마크)
- URL: https://arxiv.org/abs/2606.07462
- ID: 2606.07462
- 한줄요약: AARRI-Bench — 연구 생애주기 시나리오에서 프론티어 LLM과 agentic harness 평가.
- 검색어: `abs:"agent scaffolding"` / `abs:"long-horizon"...scaffold`
- 하네스관련성: high — "agentic harness"를 명시적 평가 대상으로 삼음.
- 확인방법: arXiv API 초록 확인

### C69. Beyond pass@1: A Reliability Science Framework for Long-Horizon LLM Agents
- 저자: 미확인
- 날짜: 2026-03-31 | 범위판정: OUT (2026-03) — 맥락 보강용
- 소스: arXiv
- URL: https://arxiv.org/abs/2603.29231
- ID: 2603.29231
- 한줄요약: 과제 길이별 신뢰도 감쇠 측정 — 능력 순위와 신뢰도 순위가 장기 구간에서 크게 발산.
- 검색어: `abs:"long-horizon" AND abs:agent AND abs:scaffold`
- 하네스관련성: medium — 장기 에이전트 신뢰도 평가 과학. 범위밖이나 평가론 배경.
- 확인방법: arXiv API 초록 확인

---

## H. 참조/개관 (하네스관련성 medium)

### C70. The Hitchhiker's Guide to Agentic AI: From Foundations to Systems
- 저자: 미확인
- 날짜: 2026-06-22 | 범위판정: IN
- 소스: arXiv (레퍼런스/서베이)
- URL: https://arxiv.org/abs/2606.24937
- ID: 2606.24937
- 한줄요약: LLM 기초→에이전트 하네스 설계→멀티에이전트 조정→프로덕션 배포 종합 레퍼런스.
- 검색어: `abs:"agent harness"` / `abs:"context management" AND abs:agent`
- 하네스관련성: medium — 하네스 설계 포함 개관서.
- 확인방법: arXiv API 초록 확인

### C71. Agents All the Way Down: A Methodology for Building Custom AI Agents from Substrate to Production
- 저자: 미확인
- 날짜: 2026-06-10 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.11869
- ID: 2606.11869
- 한줄요약: LLM 기저·함수호출·CLI 구성 등 프레임워크 무관 커스텀 에이전트 구축 방법론.
- 검색어: `abs:"multi-agent orchestration"`
- 하네스관련성: medium — 에이전트 구축 방법론(하네스 실무).
- 확인방법: arXiv API 초록 확인

### C72. SemaClaw: A Step Towards General-Purpose Personal AI Agents through Harness Engineering
- 저자: 미확인
- 날짜: 2026-04-13 | 범위판정: OUT (2026-04) — "harness engineering" 용어 직접 사용, 맥락 보강용
- 소스: arXiv
- URL: https://arxiv.org/abs/2604.11548
- ID: 2604.11548
- 한줄요약: DAG 오케스트레이션·행동 안전·3계층 컨텍스트 관리를 강조한 "harness engineering" 오픈소스 프레임워크.
- 검색어: `abs:"context engineering"`
- 하네스관련성: high — 제목에 "Harness Engineering" 명시. 용어 확립 증거. (명칭 "SemaClaw" 실존 확인 권장)
- 확인방법: arXiv API 초록 확인

---

## 검증 필요 플래그 (citation-verifier에 위임)

다음 후보들은 제품/코드네임(Claw, Buddy, Lemon 등)이 붙어 있어, arXiv API 인덱스에는 존재하나 **개별 abstract 페이지 육안 확인은 아직 안 함**. 검증 단계에서 arxiv.org/abs/{id} 직접 열람 권장:
- C11 LemonHarness (2606.24311), C21 Claw-SWE-Bench "OpenClaw" (2606.12344), C28 ClayBuddy (2606.19380), C35 Sakana Fugu (2606.21228), C50 "MemClaw" (2606.24535), C72 SemaClaw (2604.11548)
- 이들 중 다수는 산업 랩/제품 계열이라 **scout-industry 축과 중복 가능성 높음**.

## 소스 다각화 메모 (한계 정직 고지)
- **arXiv API가 유일한 실효 검색 채널이었음**(WebSearch 미가용). Semantic Scholar / OpenReview / ACL Anthology / Papers with Code는 이 컨텍스트에서 별도 API 없이 접근이 제한적이라, 위 후보의 상당수가 학술 사전출판(arXiv) 편중. 최종 서베이에서 동료심사 게재(OpenReview/ACL) 여부는 검증 단계에서 재확인 필요.
- 그럼에도 arXiv 자체가 cs.AI/cs.SE/cs.CL/cs.LG를 포괄하므로 학술 축 커버리지는 충분히 넓다고 판단.

## 통계
- 총 후보: 72건 (IN: 65건 / OUT-관련: 7건 [C14, C26, C46, C48, C69, C72, + C2계열 없음])
- 하네스관련성 high: ~45건 / medium: ~27건
- 실행 arXiv API 쿼리: 12개(클러스터×time/term) + abstract 페이지 직접검증 6건

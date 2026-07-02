# Scout Candidates — Adjacent Axis (context engineering / memory / multi-agent / eval / self-improving / RL for agents)

Scout: paper-scout (adjacent axis). Live WebFetch against arXiv API + abstract pages + web sources.
Target window: 2026-05 ~ 2026-07 (IN). OUT-but-relevant kept for context.
Honesty: only entries with 확인방법 = "WebFetch로 페이지 확인" are directly verified by me.

---

### C1. From Question Answering to Task Completion: A Survey on Agent System and Harness Design
- 저자: Jianyuan Guo, Zhiwei Hao, Chengcheng Wang, Cheng Fan, ... Kai Han, Chang Xu, Yunhe Wang (Huawei/HKU 계열)
- 날짜: 2026-06-14 | 범위판정: IN
- 소스: arXiv (cs.AI/cs.SE)
- URL: https://arxiv.org/abs/2606.20683
- ID: 2606.20683
- 한줄요약: LLM 에이전트를 "model-harness" 관점으로 분해하는 서베이. 실행 하네스를 observation·context·control·action·state·verification 6개 런타임 책임으로 정식화. 하네스 엔지니어링 서베이의 직접 선행/경쟁작.
- 검색어: arXiv API "context engineering" AND agent, sortBy submittedDate
- 하네스관련성: high — 제목·본문이 harness design 그 자체. 우리 서베이의 핵심 비교 대상.
- 확인방법: WebFetch로 페이지 확인

### C2. Less Context, Better Agents: Efficient Context Engineering for Long-Horizon Tool-Using LLM Agents
- 저자: Abhilasha Lodha, Mahsa Pahlavikhah Varnosfaderani, Abir Chakraborty, Abhinav Mithal (Microsoft 계열)
- 날짜: 2026-06-08 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.10209
- ID: 2606.10209
- 한줄요약: 장기·툴사용 에이전트에서 컨텍스트 프루닝(최근 5개 tool call 유지)+요약이 완주율↑·토큰↓·런타임↓. Dynamics 365 expense itemization 실증(GPT-5).
- 검색어: arXiv API "context engineering" AND agent
- 하네스관련성: high — 컨텍스트 관리(하네스의 핵심 축) 실증 연구, long-horizon tool use.
- 확인방법: WebFetch로 페이지 확인

### C3. A Language for Describing Agentic LLM Contexts (ACDL)
- 저자: Noga Peleg Pelc, Gal A. Kaminka, Yoav Goldberg (Bar-Ilan)
- 날짜: 2026-05-03 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2605.01920
- ID: 2605.01920
- 한줄요약: 에이전트 컨텍스트 구조·동태를 형식적으로 기술하는 언어 ACDL 제안. role message·dynamic content·conditional structure 구성자. acdlang.org 도구 제공.
- 검색어: arXiv API "context engineering" AND agent
- 하네스관련성: high — 컨텍스트 엔지니어링의 형식화/명세 언어. 하네스 설계 문서화에 직접 관련.
- 확인방법: WebFetch로 페이지 확인

### C4. Swarm Skills: A Portable, Self-Evolving Multi-Agent System Specification for Coordination Engineering
- 저자: Xinyu Zhang, Zhicheng Dou, Deyang Li, ... Zhangchun Zhao
- 날짜: 2026-05-11 (v1), 2026-05-15 (v2) | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2605.10052
- ID: 2605.10052
- 한줄요약: Anthropic Skills를 멀티에이전트로 확장한 이식성 명세 + 성공 trajectory를 새 Skill로 자동 증류/패치하는 self-evolution 알고리즘. 자기개선 멀티에이전트 하네스.
- 검색어: arXiv API "context engineering" AND agent
- 하네스관련성: high — Skills(하네스 컴포넌트) + 멀티에이전트 오케스트레이션 + 자기개선 결합.
- 확인방법: WebFetch로 페이지 확인

### C5. Mise en Place for Agentic Coding: Deliberate Preparation as Context Engineering Methodology
- 저자: Andrew Zigler
- 날짜: 2026-05-06 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2605.05400
- ID: 2605.05400
- 한줄요약: 에이전틱 코딩 전 "준비(mise en place)"를 컨텍스트 엔지니어링 방법론으로 정식화 — contextual grounding·collaborative specification·task decomposition 3단계. "context fluency"를 개발자 역량으로 제시.
- 검색어: arXiv API "context engineering" AND agent
- 하네스관련성: high — 컨텍스트 엔지니어링 실무 방법론, 병렬 에이전트 준비.
- 확인방법: WebFetch로 페이지 확인

### C6. Are We Ready For An Agent-Native Memory System?
- 저자: Wei Zhou, Xuanhe Zhou, Shaokun Han, Hongming Xu, Guoliang Li, Zhiyu Li, Feiyu Xiong, Fan Wu (Tsinghua 계열)
- 날짜: 2026-06-23 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.24775
- ID: 2606.24775
- 한줄요약: 에이전트 메모리를 데이터관리 관점(representation/extraction/retrieval/maintenance 4모듈)으로 12개 아키텍처×5 워크로드 체계 평가. "단일 최적 아키텍처 없음, 워크로드 병목 정렬이 관건."
- 검색어: arXiv API "agent memory" AND LLM
- 하네스관련성: high — 하네스의 메모리 서브시스템 설계 근거. 벤치마크·평가 방법론 겸함.
- 확인방법: WebFetch로 페이지 확인

### C7. Agent Memory: Characterization and System Implications of Stateful Long-Horizon Workloads
- 저자: Yasmine Omri, Ziyu Gan, Zachary Broveak, Robin Geens, Zexue He, Alex Pentland, Marian Verhelst, Tsachy Weissman, Thierry Tambe (Stanford/MIT/KU Leuven 계열)
- 날짜: 2026-06-04 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.06448
- ID: 2606.06448
- 한줄요약: 에이전트 메모리의 첫 시스템 레벨 특성화. 4차원 분류 taxonomy + 프로파일링 툴 + 10개 시스템 특성화 + scheduling·capability floor·fleet-scale 등 10개 실무 권고.
- 검색어: arXiv API "agent memory" AND LLM
- 하네스관련성: high — long-horizon stateful 워크로드의 시스템 함의. 하네스 인프라 설계 직결.
- 확인방법: WebFetch로 페이지 확인

### C8. Sakana Fugu Technical Report
- 저자: Yujin Tang, Edoardo Cetin, Jinglue Xu, ... Tarin Clanuwat (Sakana AI)
- 날짜: 2026-06-19 (v1), 2026-06-23 (v2) | 범위판정: IN
- 소스: arXiv (산업 랩 기술 리포트)
- URL: https://arxiv.org/abs/2606.21228
- ID: 2606.21228
- 한줄요약: orchestrator 모델이 LLM 에이전트 팀을 harness/amplify하는 "dynamic, query-adaptive agentic scaffolds" 제안. SWE-Bench Pro·Terminal Bench·LiveCodeBench·GPQA-Diamond·HLE·CharXiv에서 SOTA.
- 검색어: arXiv API "multi-agent" AND orchestration AND LLM
- 하네스관련성: high — "agentic scaffold"를 명시적으로 다루는 산업 리포트. 오케스트레이터 하네스의 핵심 사례.
- 확인방법: WebFetch로 페이지 확인

### C9. ClawArena-Team: Benchmarking Subagent Orchestration and Dynamic Workflows in Language-Model Agents
- 저자: Kaiwen Xiong, Haonian Ji, Shi Qiu, Zeyu Zheng, Cihang Xie, Xinyu Ye, Huaxiu Yao
- 날짜: 2026-06-30 | 범위판정: IN
- 소스: arXiv (벤치마크)
- URL: https://arxiv.org/abs/2606.31174
- ID: 2606.31174
- 한줄요약: 리더 LLM이 특화 서브에이전트를 병렬·비동기로 관리하는 능력을 측정하는 벤치마크(41개 멀티턴·멀티모달·멀티디렉토리 시나리오). Subagent-Management Score(SMS) 제안.
- 검색어: arXiv API "multi-agent" AND orchestration AND LLM
- 하네스관련성: high — 서브에이전트 오케스트레이션(하네스 핵심 기능) 전용 평가 하네스.
- 확인방법: WebFetch로 페이지 확인

### C10. From Failed Trajectories to Reliable LLM Agents: Diagnosing and Repairing Harness Flaws (HarnessFix)
- 저자: Mengzhuo Chen, Junjie Wang, Zhe Liu, Yawen Wang, Qing Wang (ISCAS 계열)
- 날짜: 2026-06-04 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.06324
- ID: 2606.06324
- 한줄요약: 실패 trajectory를 harness layer(ETCLOVG)에 귀속시켜 flaw-specific repair spec으로 harness patch를 생성·검증하는 HarnessFix. SWE-Bench Verified·Terminal-Bench 2.0·GAIA·AppWorld에서 15.2~50.0%↑.
- 검색어: arXiv API "self-improving" AND agent
- 하네스관련성: high — 제목·본문이 "harness flaws"·"harness patch". 하네스 신뢰성/수리의 직접 연구.
- 확인방법: WebFetch로 페이지 확인

### C11. AutoMegaKernel: A Statically-Checked Agent Harness for Self-Retargeting Megakernel Synthesis
- 저자: Jaber Jaber, Osama Jaber
- 날짜: 2026-06-08 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.09682
- ID: 2606.09682
- 한줄요약: 스케줄을 실행 전 정적 검증하는 "statically-checked agent harness" + 무인 autoresearch 루프가 megakernel을 자기개선(1.25~1.72x). frozen schedule-IR validator로 deadlock-freedom 정적 인증.
- 검색어: arXiv API "self-improving" AND agent
- 하네스관련성: high — 제목이 "Agent Harness". 정적 검증 하네스 + 자기개선 루프 결합.
- 확인방법: WebFetch로 페이지 확인

### C12. APEX: Adaptive Principle EXtraction — A Three-Layer Self-Evolution Framework for Production AI Agents
- 저자: Ya-Chuan Chen, Tien-Jen Lai, Hsiang-Wei Hu
- 날짜: 2026-06-13 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.15363
- ID: 2606.15363
- 한줄요약: L1 하네스 최적화(failure-mode patching)·L2 행동원칙(success-trace distillation)·L3 워크플로 토폴로지를 동시 진화. 단일축 harness 최적화(Self-Harness) 대비 우수, 4 LLM call로 Health Score 90%↑.
- 검색어: arXiv API "self-improving" AND agent
- 하네스관련성: high — "harness optimization"을 3계층 자기진화의 한 축으로 명시. "Self-Harness" 선행 프레임워크 언급.
- 확인방법: WebFetch로 페이지 확인

### C13. QueenBee Planner: Skill-Evolving Communication Topologies for Token-Efficient LLM Multi-Agent Systems
- 저자: Congjia Tian, Yuhang Yao, Jiaming Cui
- 날짜: 2026-06-25 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.27492
- ID: 2606.27492
- 한줄요약: 에이전트 간 통신 토폴로지를 학습가능한 design skill로 보고 router-prompt co-evolution으로 자기개선. 메시지·토큰 비용↓.
- 검색어: arXiv API "self-improving" AND agent
- 하네스관련성: medium — 멀티에이전트 통신 토폴로지(오케스트레이션 하네스) 최적화. 스니펫 기반, 미검증.
- 확인방법: WebSearch 스니펫만 봄 (arXiv API 요약)

### C14. AgentX: Towards Agent-Driven Self-Iteration of Industrial Recommender Systems
- 저자: Changxin Lao, Fei Pan, Guozhuang Ma 외 (74인)
- 날짜: 2026-06-25 (v2) | 범위판정: IN
- 소스: arXiv (산업 배포)
- URL: https://arxiv.org/abs/2606.26859
- ID: 2606.26859
- 한줄요약: 프로덕션 멀티에이전트가 추천 실험을 자율 생성·구현·평가. "Harness Evolution" 레이어가 SGPO로 trajectory를 semantic-gradient 업데이트로 증류하여 지속 자기개선.
- 검색어: arXiv API "self-improving" AND agent
- 하네스관련성: medium — "Harness Evolution" 레이어 명시. 다만 추천시스템 특화. 미검증.
- 확인방법: WebSearch 스니펫만 봄 (arXiv API 요약)

---
## "agent harness" 명시 클러스터 (핵심 온토픽 — scout-academic 축과 중복 가능성 높음, dedup 필요)

### C15. What makes a harness a harness: necessary and sufficient conditions for an agent harness
- 저자: Sanderson Oliveira de Macedo
- 날짜: 2026-06-08 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.10106
- ID: 2606.10106
- 한줄요약: "agent harness"의 필요·충분조건을 정의하는 개념 논문. framework·SDK·IDE plugin·eval harness·orchestrator와 경계를 긋는 inclusion/exclusion test. Claude Code·Codex CLI·Aider·Cline·OpenHands·SWE-agent 6개 시스템에 적용.
- 검색어: arXiv API all:"agent harness"
- 하네스관련성: high — 하네스의 정의 그 자체. 서베이 개념 정의 챕터의 근간.
- 확인방법: WebFetch로 페이지 확인

### C16. Self-Harness: Harnesses That Improve Themselves
- 저자: Hangfan Zhang, Shao Zhang, Kangcong Li, Chen Zhang, Yang Chen, Yiqun Zhang, Lei Bai, Shuyue Hu (Shanghai AI Lab 계열)
- 날짜: 2026-06-08 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.09498
- ID: 2606.09498
- 한줄요약: LLM 에이전트가 인간 개입 없이 자기 자신의 하네스를 개선. weakness mining → harness proposal → regression validation 3단계. pass rate 40.5%→61.9%. (APEX가 인용한 선행작)
- 검색어: arXiv API all:"agent harness"
- 하네스관련성: high — 자기개선 하네스의 원형. C12(APEX)의 baseline.
- 확인방법: WebFetch로 페이지 확인

### C17. HarnessX: A Composable, Adaptive, and Evolvable Agent Harness Foundry
- 저자: Tingyang Chen, Shuo Lu, Kang Zhao, Weicheng Meng 외 (Kun Shao, Jian Luan 등)
- 날짜: 2026-06-12 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.14249
- ID: 2606.14249
- 한줄요약: 타입화된 harness primitive를 substitution algebra로 조합하고 AEGIS 멀티에이전트 진화엔진(trace-driven)으로 적응·진화. prompts·tools·memory·control flow를 런타임 인프라로 최적화. 5개 벤치 평균 +14.5%(최대 +44.0%).
- 검색어: arXiv API all:"agent harness"
- 하네스관련성: high — 하네스를 조합/적응/진화 가능한 파운드리로 정식화. 하네스 아키텍처의 핵심.
- 확인방법: WebFetch로 페이지 확인

### C18. Recursive Agent Harnesses (RAH)
- 저자: Elias Lumer, Sahil Sen, Kevin Paul, Vamse Kumar Subbiah
- 날짜: 2026-06-11 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.13643
- ID: 2606.13643
- 한줄요약: 재귀 단위를 "model call"이 아닌 "full agent harness(파일시스템·코드실행·계획 포함)"로. 부모 에이전트가 스크립트로 서브에이전트 하네스를 병렬 spawn. 4M-token 벤치 71.75%→81.36%(강모델 89.77%).
- 검색어: arXiv API all:"agent harness"
- 하네스관련성: high — 재귀·병렬 서브에이전트 하네스 orchestration. C9(ClawArena)·C18 subagent 주제 연결.
- 확인방법: WebFetch로 페이지 확인

### C19. HarnessBridge: Learnable Bidirectional Controller for LLM Agent Harness
- 저자: Xiaoxuan Wang, Haixin Wang, Alexander Taylor, Jason Cong, Yizhou Sun, Wei Wang (UCLA 계열)
- 날짜: 2026-06-11 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.12882
- ID: 2606.12882
- 한줄요약: observation↔action 양방향 projection을 파라미터화하는 경량 학습형 컨트롤러. 전용 하네스에 필적하며 토큰 사용 절감. Terminal-Bench 2.0·SWE-bench.
- 검색어: arXiv API all:"agent harness"
- 하네스관련성: high — 학습형 하네스 컨트롤러. 미검증(스니펫).
- 확인방법: WebSearch 스니펫만 봄 (arXiv API 요약)

### C20. Claw-SWE-Bench: A Benchmark for Evaluating OpenClaw-style Agent Harnesses on Coding Tasks
- 저자: Mengyu Zheng, Kai Han, Boxun Li, ... Yunhe Wang, Yu Wang (Huawei 계열; C1 저자와 겹침)
- 날짜: 2026-06-10 | 범위판정: IN
- 소스: arXiv (벤치마크)
- URL: https://arxiv.org/abs/2606.12344
- ID: 2606.12344
- 한줄요약: OpenClaw-style 하네스 평가 벤치(350 GitHub 이슈, 8개 언어, 43 repo). "adapter design이 핵심": 동일 GLM 5.1이 minimal direct-diff adapter 19.1% vs full adapter 73.4%.
- 검색어: arXiv API all:"agent harness"
- 하네스관련성: high — 하네스(adapter) 설계가 성능을 좌우함을 정량 입증. 평가 하네스.
- 확인방법: WebFetch로 페이지 확인

### C21. StaminaBench: Stress-Testing Coding Agents over 100 Interaction Turns
- 저자: Vlad Sobal, Shuo Yang, Yuting Zhang, Wei Xia, Stefano Soatto (AWS 계열)
- 날짜: 2026-06-17 | 범위판정: IN
- 소스: arXiv (벤치마크)
- URL: https://arxiv.org/abs/2606.19613
- ID: 2606.19613
- 한줄요약: 100턴 장기 세션에서 코딩 에이전트 하네스 강건성 스트레스 테스트. "강한 모델일수록 best/worst harness 간 최대 6x 격차; 약한 모델은 하네스 무관하게 고전."
- 검색어: arXiv API all:"agent harness"
- 하네스관련성: high — 하네스 품질이 성능 병목/증폭기임을 장기 세션에서 실증. 핵심 논거.
- 확인방법: WebFetch로 페이지 확인

### C22. SEAGym: An Evaluation Environment for Self-Evolving LLM Agents
- 저자: Congjie Zheng, Chuanyi Xue, Bin Liang, Jun Yang, Changshui Zhang
- 날짜: 2026-06-16 | 범위판정: IN
- 소스: arXiv (벤치마크/환경)
- URL: https://arxiv.org/abs/2606.17546
- ID: 2606.17546
- 한줄요약: 자기진화 에이전트 평가 환경. "agent harness updates가 training/validation/test/replay/cost 기록에 걸쳐" 시스템에 미치는 영향 측정.
- 검색어: arXiv API all:"agent harness"
- 하네스관련성: medium-high — 자기진화+하네스 업데이트 평가. 미검증(스니펫).
- 확인방법: WebSearch 스니펫만 봄 (arXiv API 요약)

### C23. ActPlane: Programmable OS-Level Policy Enforcement for Agent Harnesses
- 저자: Yusheng Zheng, Tianyuan Wu, Quanzhi Fu, Tong Yu, Wenan Mao, Wei Wang, Dan Williams, Andi Quinn
- 날짜: 2026-06-23 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.25189
- ID: 2606.25189
- 한줄요약: eBPF 기반 OS 커널 레벨 정책 엔진이 에이전트 실행 경로 전반에 안전 정책 강제. indirect path 컴플라이언스↑, 오버헤드 1.9~8.4%.
- 검색어: arXiv API all:"agent harness"
- 하네스관련성: medium-high — 하네스의 안전/정책 강제 레이어. 미검증(스니펫).
- 확인방법: WebSearch 스니펫만 봄 (arXiv API 요약)

### C24. LLM-as-Code: Agentic Programming for Agent Harness
- 저자: Junjia Qi, Zichuan Fu, Jingtong Gao, Wenlin Zhang, Hanyu Yan, Xian Wu, Xiangyu Zhao
- 날짜: 2026-06-14 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.15874
- ID: 2606.15874
- 한줄요약: 모델 오케스트레이션이 아니라 "프로그램이 모든 control flow를 지배"하는 패러다임. computer-use 에이전트의 long visual operation sequence 안정성↑.
- 검색어: arXiv API all:"agent harness"
- 하네스관련성: medium-high — control flow 주도권(하네스 vs 모델) 논쟁의 한 축. 미검증(스니펫).
- 확인방법: WebSearch 스니펫만 봄 (arXiv API 요약)

### C25. Building Agent Harnesses for Scientific Curation from Multimodal Sources (Beaver)
- 저자: Sheng Zhang, Qin Liu, Renqian Luo, Shufang Xie, Reuben Tan 외 (Microsoft 계열 추정)
- 날짜: 2026-06-19 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.21005
- ID: 2606.21005
- 한줄요약: multimodal evidence tooling + task scaffolding + artifact-grounded autoresearch를 결합한 Beaver 하네스로 과학 논문에서 구조화 정보 추출(provenance 추적).
- 검색어: arXiv API all:"agent harness"
- 하네스관련성: medium-high — 도메인 하네스 구축 사례(스캐폴딩+툴링). 미검증(스니펫).
- 확인방법: WebSearch 스니펫만 봄 (arXiv API 요약)

### C26. ClayBuddy: A Framework, Evaluation, & Mitigation of Coding Agent Failures
- 저자: Kenneth Ge, Andre Assis
- 날짜: 2026-06-13 (v3) | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.19380
- ID: 2606.19380
- 한줄요약: 코딩 에이전트 하네스 3대 실패 메커니즘(underspecification·capability error·execution failure)과 완화(deterministic guardrails) 제시.
- 검색어: arXiv API all:"agent harness"
- 하네스관련성: medium-high — 하네스 실패 분류/완화. C10(HarnessFix)과 주제 인접. 미검증(스니펫).
- 확인방법: WebSearch 스니펫만 봄 (arXiv API 요약)

### C27. The Hitchhiker's Guide to Agentic AI: From Foundations to Systems
- 저자: Haggai Roitman
- 날짜: 2026-06-22 | 범위판정: IN
- 소스: arXiv (서베이/레퍼런스)
- URL: https://arxiv.org/abs/2606.24937
- ID: 2606.24937
- 한줄요약: 에이전틱 스택 전반 레퍼런스 — "agent harness design and context management" + 메모리·조정 프로토콜·배포 포함.
- 검색어: arXiv API all:"agent harness"
- 하네스관련성: medium — 서베이류(맥락 정리에 유용). 미검증(스니펫).
- 확인방법: WebSearch 스니펫만 봄 (arXiv API 요약)

---
## 신뢰성/멀티에이전트 검증 + 툴 오케스트레이션 (인접 축)

### C28. MAS-Lab: A Specification-Driven Validation Framework for Reliable Multi-Agent Systems
- 저자: Jordan Augé, Giovanna Carofiglio, Giulio Grassi, Jacques Samain (Cisco 계열 추정)
- 날짜: 2026-06-29 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.30546
- ID: 2606.30546
- 한줄요약: Spec(선언적·프레임워크 무관 명세) + MAS-OS(stateful 실행/제어) + Lab overlay(관측·평가) 3계층으로 MAS를 "스크립트 모음"에서 "엔지니어링된 분산 시스템"으로. intent와 운영을 분리.
- 검색어: arXiv API agent AND reliability AND LLM
- 하네스관련성: high — 멀티에이전트 하네스의 명세·검증·관측 계층. 하네스 신뢰성 엔지니어링.
- 확인방법: WebFetch로 페이지 확인

### C29. MCP Server Architecture Patterns for LLM-Integrated Applications
- 저자: Carson Rodrigues, Oysturn Vas
- 날짜: 2026-06-29 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.30317
- ID: 2606.30317
- 한줄요약: MCP 서버 15개 분석 → 5개 아키텍처 패턴(Resource Gateway·Tool Orchestrator·Stateful Session Server·Proxy Aggregator·Domain-Specific Adapter). 툴 개수↑ 시 tool-selection 정확도 저하(Haiku 4.5는 10~15개, Sonnet 4는 20~30개에서 90% 붕괴).
- 검색어: arXiv API "tool orchestration"/"tool-use" AND agent
- 하네스관련성: high — 툴 오케스트레이션(하네스 핵심 축) 아키텍처 패턴 + 정량 한계. MCP 실무 직결.
- 확인방법: WebFetch로 페이지 확인

### C30. Characterizing Large Language Model Agentic Workflows: A Study on N8n Ecosystem
- 저자: Yutian Tang, Yuming Zhou, Huaming Chen
- 날짜: 2026-06-27 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.29116
- ID: 2606.29116
- 한줄요약: 6,000+ n8n 워크플로 실증 분석. "structured fallback path·repair loop·failure-specific alert 같은 명시적 신뢰성 메커니즘이 여전히 드물다" — 배포와 엔지니어링 지원 간 격차 노출.
- 검색어: arXiv API "tool orchestration"/"tool-use" AND agent
- 하네스관련성: medium — 실제 에이전틱 워크플로의 신뢰성 하네스 부재 실증. 미검증(스니펫).
- 확인방법: WebSearch 스니펫만 봄 (arXiv API 요약)

### C31. Capability Gates Are Not Authorization: Confused-Deputy Failures in LLM Agent Frameworks
- 저자: David Mellafe Zuvic
- 날짜: 2026-06-27 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.28679
- ID: 2606.28679
- 한줄요약: LangChain/LangGraph·LlamaIndex의 권한 갭 감사 — 기본값으로 "deterministic fail-closed per-call value authorization gate"를 제공하는 프레임워크 없음. ScopeGate 완화책 제안.
- 검색어: arXiv API "tool orchestration"/"tool-use" AND agent
- 하네스관련성: medium — 에이전트 프레임워크(하네스)의 권한/안전 결함. 미검증(스니펫).
- 확인방법: WebSearch 스니펫만 봄 (arXiv API 요약)

---
## "harness engineering" 정확 문구 클러스터 (서베이 핵심 스파인 — scout-academic/industry 축과 중복 강력 예상, DEDUP 최우선)

### C32. AI Harness Engineering: A Runtime Substrate for Foundation-Model Software Agents
- 저자: Hailin Zhong, Shengxin Zhu
- 날짜: 2026-05-13 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2605.13357
- ID: 2605.13357
- 한줄요약: "AI Harness Engineering"을 정식화 — 11개 컴포넌트 책임(task spec·context selection·tool access·project memory·task state·observability·failure attribution·verification·permissions·entropy auditing·intervention recording) + H0~H3 4단계 사다리. model-harness-environment 시스템 관점.
- 검색어: arXiv API all:"harness engineering"
- 하네스관련성: high — 제목·주제가 하네스 엔지니어링 그 자체. 서베이 분류체계의 핵심 골격.
- 확인방법: WebFetch로 페이지 확인

### C33. Code as Agent Harness (survey)
- 저자: Xuying Ning, Katherine Tieu, Dongqi Fu, Tianxin Wei, Zihao Li 외 (총 42인)
- 날짜: 2026-05-18 | 범위판정: IN
- 소스: arXiv (서베이)
- URL: https://arxiv.org/abs/2605.18747
- ID: 2605.18747
- 한줄요약: 코드를 에이전트 인프라의 기반으로 보는 통합 서베이. Harness Interface·Harness Mechanisms(planning/memory/tool use + feedback control)·Scaling(단일→멀티에이전트) 3계층. 코딩·GUI/OS·embodied·과학·엔터프라이즈 망라.
- 검색어: arXiv API all:"harness engineering"
- 하네스관련성: high — 하네스 서베이. 우리 서베이의 직접 선행/비교 대상. C1과 함께 핵심.
- 확인방법: WebFetch로 페이지 확인

### C34. Agentic Harness Engineering: Observability-Driven Automatic Evolution of Coding-Agent Harnesses
- 저자: Jiahang Lin, Shichun Liu, Chengjun Pan, ... Tao Gui, Yu-Gang Jiang (Fudan 계열)
- 날짜: 2026-04-28 (v1), 2026-05-18 (v4) | 범위판정: IN (v4 갱신이 범위 내; 최초는 OUT 경계)
- 소스: arXiv
- URL: https://arxiv.org/abs/2604.25850
- ID: 2604.25850
- 한줄요약: 관측성 3기둥(component·experience·decision observability)으로 코딩 에이전트 하네스를 폐루프 자동 진화. 10회 반복으로 Terminal-Bench 2 pass@1 69.7%→77.0% (Codex-CLI 71.9%·ACE·TF-GRPO 상회). 모델군 간 전이.
- 검색어: arXiv API all:"harness engineering"
- 하네스관련성: high — 하네스 자동 진화의 대표작. C16(Self-Harness)·C17(HarnessX)·C34 자기개선 하네스 클러스터.
- 확인방법: WebFetch로 페이지 확인

### C35. Harness Engineering as Categorical Architecture
- 저자: Bogdan Banu
- 날짜: 2026-05-12 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2605.12239
- ID: 2605.12239
- 한줄요약: 하네스 엔지니어링의 형식적 범주론(categorical) 프레임워크. 에이전트 외재화 4기둥(Memory·Skills·Protocols·Harness)을 아키텍처 triple에 매핑, compiler functor로 여러 프레임워크 타겟팅.
- 검색어: arXiv API all:"harness engineering"
- 하네스관련성: high — 하네스 이론화(형식적 정의). C15(정의 논문)와 이론 축.
- 확인방법: WebSearch 스니펫만 봄 (arXiv API 요약)

### C36. It's Not the Size: Harness Design Determines Operational Stability in Small Language Models
- 저자: Yong-eun Cho
- 날짜: 2026-05-12 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2605.12129
- ID: 2605.12129
- 한줄요약: 2~3B 모델에서 하네스 설계 효과 실증. plan-execute-verify-recover 4단계 파이프라인이 near-perfect, raw 모델은 scaffold collapse. planning·recovery 각각 ~25% 기여.
- 검색어: arXiv API all:"harness engineering"
- 하네스관련성: high — 하네스 설계가 소형 모델 안정성을 좌우함을 실증. C21(StaminaBench)·C20(Claw-SWE) "하네스가 성능 좌우" 논거군.
- 확인방법: WebSearch 스니펫만 봄 (arXiv API 요약)

### C37. Effective Harness Engineering for Algorithm Discovery with Coding Agents
- 저자: Yoichi Ishibashi, Taro Yano, Masafumi Oyamada (NEC 계열 추정)
- 날짜: 2026-05-13 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2605.15221
- ID: 2605.15221
- 한줄요약: 고정 토큰 예산 하 알고리즘 발견용 하네스 설계. depth-over-breadth(적은 알고리즘·깊은 추론이 다수 빠른 생성 상회). 모델 역량에 스케일하는 evaluation-hack 탐지.
- 검색어: arXiv API all:"harness engineering"
- 하네스관련성: high — 하네스 설계 선택(깊이 vs 폭)의 실증. 미검증(스니펫).
- 확인방법: WebSearch 스니펫만 봄 (arXiv API 요약)

### C38. Harness-MU: A Safe, Governed, and Effective Harness for Multi-User LLM Agents
- 저자: Wangxuan Fan, Xiaoyu Nie, Zhongxiang Dai
- 날짜: 2026-06-20 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.21856
- ID: 2606.21856
- 한줄요약: 멀티유저 LLM 에이전트 거버넌스 하네스. "거버넌스 제약은 execution hook으로 강제해야 한다"(확률적 안전장치 아님). Muses-Bench에서 access-control 공격 대비 permission preservation↑.
- 검색어: arXiv API all:"harness engineering"
- 하네스관련성: high — 하네스의 거버넌스/안전 강제(execution hook). C23(ActPlane)·C31 안전 하네스 클러스터. 미검증(스니펫).
- 확인방법: WebSearch 스니펫만 봄 (arXiv API 요약)

### C39. Harnesses for Inference-Time Alignment over Execution Trajectories
- 저자: Boyuan Wang, Bochao Li, Minghan Wang, Yuxin Tao, Fang Kong
- 날짜: 2026-05-15 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2605.21516
- ID: 2605.21516
- 한줄요약: trajectory alignment 관점의 하네스 설계. task decomposition과 guided execution 분리, workflow granularity·retry budget 효과 정량화. "partial harness가 fully structured workflow 상회 가능."
- 검색어: arXiv API all:"harness engineering"
- 하네스관련성: high — 하네스 구조 granularity·retry의 정량 분석. 미검증(스니펫).
- 확인방법: WebSearch 스니펫만 봄 (arXiv API 요약)

### C40. What Makes Interaction Trajectories Effective for Training Terminal Agents?
- 저자: Sidi Yang 외 (14인)
- 날짜: 2026-06-02 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.03461
- ID: 2606.03461
- 한줄요약: Environment-Grounded Supervision 관점의 터미널 에이전트 학습. "낮은 점수 에이전트가 더 나은 학습 trajectory 생성"이라는 pedagogical paradox. "Harness Engineering을 재현가능 에이전틱 지능의 1차 촉매"로 강조.
- 검색어: arXiv API all:"harness engineering"
- 하네스관련성: high — 하네스가 학습 데이터 품질을 좌우(RL/훈련 접점). 미검증(스니펫).
- 확인방법: WebSearch 스니펫만 봄 (arXiv API 요약)

### C41. NORA: A Harness-Engineered Autonomous Research Agent for End-to-End Spatial Data Science
- 저자: Bing Zhou 외 (6인)
- 날짜: 2026-05-03 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2605.02092
- ID: 2605.02092
- 한줄요약: 지리공간 과학 특화 연구 에이전트. lifecycle hook·safety gate·state persistence로 하네스 엔지니어링 정식화. NeuroBench(executability·artifact validity·reproducibility) 도입.
- 검색어: arXiv API all:"harness engineering"
- 하네스관련성: medium-high — 도메인 하네스 + lifecycle hook/safety gate. 미검증(스니펫).
- 확인방법: WebSearch 스니펫만 봄 (arXiv API 요약)

### C42. HARBOR: A Harness Framework for Agentic Robot Reinforcement Learning
- 저자: Zechu Li 외 (7인)
- 날짜: 2026-06-07 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.08610
- ID: 2606.08610
- 한줄요약: 로봇 RL 자동화를 harness-engineering 과제로. 목표를 bounded stage로 분해 + 특화 에이전트 + 자동 reward 설계 + 하이퍼파라미터 튜닝. manipulation·locomotion·dexterous.
- 검색어: arXiv API all:"harness engineering"
- 하네스관련성: medium — RL for agents × 하네스 접점(embodied 도메인). 미검증(스니펫).
- 확인방법: WebSearch 스니펫만 봄 (arXiv API 요약)

---
## 하네스 × 훈련/RL 접점 + 스캐폴드 조합 (인접 축 핵심)

### C43. The Interplay of Harness Design and Post-Training in LLM Agents
- 저자: Kyungmin Kim, Youngbin Choi, Seoyeon Lee, Suhyeon Jun, Dongwoo Kim, Sangdon Park (POSTECH 계열 추정)
- 날짜: 2026-06-24 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.25447
- ID: 2606.25447
- 한줄요약: 하네스 설계(어떤 툴을 노출/기술하는가)가 post-training 성능·OOD 강건성에 미치는 영향. "harness-aware post-training"이 in-distribution + OOD 적응 모두 개선; minimal harness는 툴환경 변화 시 급락. 하네스를 훈련의 제어 가능 차원으로.
- 검색어: arXiv API agent AND scaffolding AND LLM
- 하네스관련성: high — 하네스 설계 × RL/post-training의 직접 상호작용. 인접 축(RL for agent scaffolding)의 핵심 논문.
- 확인방법: WebFetch로 페이지 확인

### C44. AgentSpec: Understanding Embodied Agent Scaffolds Through Controlled Composition
- 저자: Jixuan Chen, Jianzhi Shen, Haoqiang Kang, ... Kun Zhou, Lianhui Qin
- 날짜: 2026-06-12 | 범위판정: IN
- 소스: arXiv
- URL: https://arxiv.org/abs/2606.14674
- ID: 2606.14674
- 한줄요약: 에이전트를 "typed compositions of reusable policy components"로 표현하는 모듈 명세 프레임워크. perception·memory·reasoning·reflection·action·learning 표준 인터페이스. "성능은 개별 모듈 강도보다 scaffold 호환성·상호작용이 좌우." RL 정책은 배포시 scaffold와 정렬될 때 최적.
- 검색어: arXiv API agent AND scaffolding AND LLM
- 하네스관련성: high — 스캐폴드(하네스) 조합의 통제 실험. C43과 함께 scaffold×RL 축.
- 확인방법: WebFetch로 페이지 확인

---
## OUT-but-relevant (범위 밖 기반 앵커 — 맥락용)

### C45. A Survey of Context Engineering for Large Language Models
- 저자: Lingrui Mei, Jiayu Yao, Yuyao Ge, ... Jiafeng Guo, Shenghua Liu
- 날짜: 2025-07-17 (v1), 2025-07-21 (v2) | 범위판정: OUT (2025-07, 대상창 밖)
- 소스: arXiv (서베이)
- URL: https://arxiv.org/abs/2507.13334
- ID: 2507.13334
- 한줄요약: "context engineering"을 형식적 분야로 정립한 대규모 서베이(1,400+ 논문). retrieval·generation·processing·management 기초 구성 + RAG·메모리·툴통합·멀티에이전트. "복잡 컨텍스트 이해는 잘하나 정교한 장문 생성은 약함"의 비대칭 지적.
- 검색어: arXiv API abs:"context engineering" AND abs:survey
- 하네스관련성: high(맥락) — 컨텍스트 엔지니어링(하네스의 핵심 축)의 표준 기반 서베이. 2026 논문들의 공통 인용 앵커로 부록/도입부에 유용.
- 확인방법: WebFetch로 페이지 확인 (날짜 2025-07 = 대상 범위 밖)

---
## 정찰 요약 (Scout Summary — Adjacent Axis)

- **총 후보: 45건** (IN 44, OUT-relevant 1). 모두 arXiv 라이브 WebFetch 기반.
- **직접 페이지 확인(WebFetch): 21건** — C1~C12(일부), C15~C18, C20~C21, C28~C29, C32~C34, C43~C45. 나머지는 arXiv API 요약(스니펫) 기반이며 검증 단계에서 재확인 필요로 정직히 표기.
- **날짜 분포: 대부분 2026-05·2026-06.** 2026-07(2607) 논문은 현재 시점(2026-07-01) 기준 arXiv에 아직 거의 없음 — 정직히 "7월분 희소"로 보고. 억지 패딩 없음.
- **arXiv ID 포맷 주의:** 2026년 논문은 `2605.*`(5월)·`2606.*`(6월) 형식(YYMM). 검증자가 헷갈리지 않도록 명시.

### DEDUP 경고 (다른 scout 축과 중복 강력 예상)
- **scout-academic 축과 중복 유력:** C1(harness survey), C15(정의), C32(AI Harness Engineering), C33(Code as Agent Harness), C34(관측성 진화), C35(categorical), C16(Self-Harness), C17(HarnessX) — "harness engineering"/"agent harness" 정확 문구 클러스터 전반은 학술 축에서도 필연적으로 잡힘.
- **scout-industry 축과 중복 유력:** C8(Sakana Fugu 기술 리포트), C20/C9/C21(Claw-SWE/ClawArena/StaminaBench 벤치마크), C29(MCP 패턴).
- **인접 축 고유(다른 scout가 놓칠 가능성 높음):** 메모리 시스템 클러스터(C6·C7 및 arXiv 메모리 대량 히트), C43(하네스×post-training), C44(AgentSpec), C28(MAS-Lab), C3(ACDL 컨텍스트 언어), C5(Mise en Place), C36·C37·C39·C40(하네스 설계 실증/RL 접점).

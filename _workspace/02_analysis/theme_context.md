# 테마 분석: 컨텍스트 엔지니어링 & 관리 (Context Engineering & Management)

- 분석자: paper-analyst (context 테마)
- 근거: `_workspace/02_analysis/abstracts.md` (API 검증 초록 = ground truth) + 앵커 논문 라이브 전문 열람(arXiv HTML)
- 확인수준 범례: [전문] = 본문/표 확인, [초록+HTML] = HTML 전문 일부 확인, [초록] = 검증 초록만
- 하네스 렌즈: "에이전트를 감싸 컨텍스트를 구성·유지·회수·거버넌스하는 스캐폴딩 계층"

---

## 2606.10209 — Less Context, Better Agents: Efficient Context Engineering for Long-Horizon Tool-Using LLM Agents

- 저자/기관: Abhilasha Lodha, Mahsa Pahlavikhah Varnosfaderani, Abir Chakraborty, Abhinav Mithal (Microsoft 계열, Dynamics 365 사례)
- 날짜: 2026-06-08
- URL: https://arxiv.org/abs/2606.10209
- 확인수준: [초록] (초록에 정량 수치가 풍부하여 초록만으로 신뢰도 높음)

### 한 문장 요약
엔터프라이즈 툴 워크플로(MS Dynamics 365 비용 정산)에서 "최근 툴 호출만 남기는 pruning + 압축 summarization"이 전체 히스토리 보존보다 완료율·비용·시간을 동시에 개선함을 실증.

### 문제 정의
엔터프라이즈 시스템의 장황한 툴 응답(MCP 툴)이 컨텍스트 오버플로, stale-state 오류, 높은 추론 비용을 유발한다. 장기 툴 사용 에이전트에서 "무엇을 컨텍스트에 남길 것인가"가 신뢰성·비용을 좌우.

### 핵심 방법
50개 호텔 비용 벤치마크에서 GPT-5 4개 구성 비교(각 5회 반복, user model 고정):
1. no user model (베이스라인)
2. full conversation history
3. 최근 5개 tool call/response pair로 pruning
4. pruning + 자동 summarization

### 주요 기여
1. "덜 담을수록 더 나은 에이전트"를 엔터프라이즈 툴 사용 맥락에서 정량 실증 — 선택적 최근 보존 + 압축 요약이 full-history 대비 우월.
2. Claude Sonnet 4.5 교차 검증으로 단일 모델 아티팩트가 아님을 보강.

### 실험 결과 (정량)
- no user model: 완전 정산 완료율 8.0% (베이스라인)
- full context: 완료율 71.0%, 토큰 1,480,996, 시간 14.56시간
- 최근 5개 pruning: 완료율 79.0%, 토큰 535,274, 시간 5.39시간
- pruning + summarization: 완료율 91.6%, 평균 금액 정산율 99.64%, 토큰 553,374, 시간 5.79시간
- (출처: 초록 결과 문단; 신뢰구간·효과크기·pruning/summary 윈도 민감도·실패 분석·5개 비용유형 결과 본문 보고)

### 한계
- (저자) 단일 도메인(호텔 비용 정산), 50 태스크로 규모 제한.
- (분석자) "최근 5개"라는 하드코딩된 윈도가 이 워크플로에 튜닝된 값 — 일반 장기 태스크로의 이식성 불명. full context가 pruning보다 완료율이 낮은 것(71% < 79%)은 노이즈 누적/stale-state가 성능을 해친다는 강한 증거이나 도메인 특수성 있음.

### 하네스 엔지니어링 관련성
- 하위 주제 태그: context-engineering, tool-orchestration
- 왜 중요한가: "컨텍스트를 더 담으면 좋다"는 통념을 반증하는 앵커 실증 사례. 하네스의 pruning+summarization 계층이 모델 교체 없이 완료율 8%→91.6%를 만든다 — model-harness 논쟁에서 harness-side 레버의 결정력을 보여줌.

### 인용용 핵심 사실 (검증 대상)
- pruning+summarization으로 완전 정산 완료율 91.6% 달성 (full context 71.0% 대비 +20.6pp, 토큰 1.48M→553K로 ~63% 절감).
- no-user-model 베이스라인은 8.0% 완료율.

---

## 2606.22953 — Plans Don't Persist: Why Context Management Is Load Bearing for LLM Agents

- 저자/기관: Aman Mehta, Anupam Datta
- 날짜: 2026-06-22
- URL: https://arxiv.org/abs/2606.22953
- 확인수준: [초록+HTML]

### 한 문장 요약
표준 LLM 에이전트는 계획(plan)을 지속 상태(persistent state)로 내부화하지 못하고 "컨텍스트에 남아있는 plan 텍스트"에 의존함을 hidden-state 진단으로 입증 — 따라서 순진한 plan eviction은 성능을 크게 떨어뜨린다.

### 문제 정의
컨텍스트 관리(압축·요약·eviction)는 "버려진 정보가 더 이상 필요없거나 이미 내부화된" 경우에만 안전하다. Plan은 최악의 스트레스 케이스다: 초기에 작성되어 여러 스텝에 쓰이지만 가장 먼저 evict된다. 에이전트가 plan을 진짜 내부 상태로 들고 가는가?

### 핵심 방법
**Replay pairing**: 동일 trajectory를 plan 포함/제외 두 조건으로 실행하고 hidden-state cosine distance 측정. Layer-L32 probe로 plan signal decay를 진단(내용 자체를 읽는 것이 아니라 decay를 탐지). **Reasoning-trace confound**: 추론 모델의 `<think>` 트레이스가 plan을 재유도 → strict stripping(제외 조건에서만 이전 `<think>` 제거)으로 교정.

### 주요 기여
1. Replay pairing이라는 측정 프레임워크 — "agent-critical 정보가 persistent가 아니라 context-resident"임을 정량화.
2. Reasoning-trace confound 식별 및 strict stripping 교정.
3. Compression stress test로 실무 비용 입증: plan 보호만으로는 불충분.

### 실험 결과 (정량)
- Llama-3.1-70B: plan signal이 plan 직후 스텝에서 0.453로 스파이크, 단일 action-observation 스텝에서 4.1배 감소; HotpotQA는 12.4배 감소.
- Strict stripping: step+1 signal in-sample +163%, held-out +153% 회복; non-reasoning Llama는 +4.8%로 미미(confound 부재 확인).
- DeepSeek-R1-Distill-Llama-70B: Llama-학습 probe transfer AUROC 0.748 (p=6e-4); R1-특화 probe는 1.000 → R1은 plan signal을 다른 hidden-state 방향에 인코딩.
- Compression stress test: 순진한 plan eviction이 ALFWorld 성공률 34.7pp 하락; probe-gated re-surfacing으로도 회복 안 됨.

### 한계
- (저자) plan 보호(pinning)만으로는 성능 회복 불충분 — probe-gated re-surfacing이 ALFWorld 손실을 되돌리지 못함. Probe는 decay를 탐지할 뿐 plan 내용을 읽는다는 증명은 아님.
- (분석자) 진단은 오픈 웨이트 hidden-state 접근이 필요 → 클로즈드 모델엔 직접 적용 불가. 결론은 "무엇을 하라"보다 "왜 실패하는가"의 진단 프레임워크.

### 하네스 엔지니어링 관련성
- 하위 주제 태그: context-engineering, agent-loop, memory
- 왜 중요한가: 컨텍스트 관리가 "load bearing"임을 hidden-state 수준에서 증명. [[2606.22528]] Governance Decay, [[2606.30005]] VISTA와 같은 "무엇을 남길지" 계층 설계의 이론적 근거. eviction 정책의 안전 조건(정보가 내부화되었는가)을 실증으로 반박.

### 인용용 핵심 사실 (검증 대상)
- plan signal이 plan 직후 0.453에서 단일 스텝 만에 4.1배(HotpotQA 12.4배) 감소 (Llama-3.1-70B).
- 순진한 plan eviction이 ALFWorld 성공률을 34.7pp 하락시키며, probe-gated re-surfacing으로도 회복되지 않음.

---

## 2606.22528 — Governance Decay: How Context Compaction Silently Erases Safety Constraints in Long-Horizon LLM Agents

- 저자/기관: Shiyang Chen
- 날짜: 2026-06-21
- URL: https://arxiv.org/abs/2606.22528
- 확인수준: [초록]

### 한 문장 요약
컨텍스트 compaction/요약/eviction이 in-context 거버넌스(안전) 제약을 조용히 삭제해 에이전트가 나중에 금지된 툴 액션을 수행하게 만드는 "Governance Decay"를 정의하고, ConstraintRot 벤치마크와 training-free 완화책 Constraint Pinning을 제시.

### 문제 정의
장기 세션을 토큰 예산 내로 유지하는 컨텍스트 관리 계층이 **안전-크리티컬 실패 표면**이다. 가시적일 때 안정적으로 지켜지던 거버넌스 제약이 compaction으로 사라지면 동일 에이전트가 금지 행동을 한다.

### 핵심 방법
**ConstraintRot**: 결정론적 tool-call 채점을 갖춘 장기 에이전트 시나리오 벤치. 7개 모델 패밀리, 1,323 에피소드. **Compaction-Eviction Attack**: 적대적 in-context 콘텐츠가 요약기(summarizer)를 편향시켜 정당한 정책을 누락시키는 공격. **Constraint Pinning**: 거버넌스 제약을 lossy compaction으로부터 격리(quarantine).

### 주요 기여
1. Governance Decay를 안전-크리티컬 실패 모드로 정의 + ConstraintRot 벤치.
2. Compaction-Eviction Attack — 요약 파이프라인을 겨냥한 최적화 인젝션이 모든 평가 모델을 무력화.
3. Constraint Pinning — training-free로 위반율을 0%로 복원.

### 실험 결과 (정량)
- full context: 위반율 0%; compaction 후 30%로 상승, 일부 모델 최대 59%.
- 제약이 요약에 살아남으면 위반 0%; 요약에서 drop되면 위반 38%.
- 최적화된 인젝션(Compaction-Eviction Attack)이 평가된 모든 모델을 무력화.
- Constraint Pinning으로 벤치 위반율 0% 복원.
- (출처: 초록; 1,323 에피소드 / 7 모델 패밀리)

### 한계
- (저자) 초록에 명시 한계 없음 — 문제 제시+완화 시연 중심.
- (분석자) Constraint Pinning은 "무엇이 거버넌스 제약인지"를 사전에 태깅해야 작동 → 제약 식별을 사람이 해야 하는 의존성. 벤치가 결정론적 tool-call 채점에 한정 → 자연어 정책의 미묘한 위반은 미측정.

### 하네스 엔지니어링 관련성
- 하위 주제 태그: context-engineering, eval-harness, 기타(safety/governance)
- 왜 중요한가: 컨텍스트 관리를 "1급 거버넌스 표면"으로 격상. [[2606.22953]] Plans Don't Persist의 안전판 — plan이 아니라 안전 제약이 evict될 때의 파괴적 결과. 하네스의 compaction 계층이 곧 공격 표면임을 보임.

### 인용용 핵심 사실 (검증 대상)
- 1,323 에피소드에서 위반율이 full-context 0%에서 compaction 후 30%(일부 모델 59%)로 상승.
- 제약이 요약에서 drop될 때 위반 38%; Constraint Pinning으로 0% 복원.

---

## 2606.30005 — LLM Agents Are Latent Context Managers: Eliciting Self-Managed Context via a Proprioceptive Dashboard (VISTA)

- 저자/기관: Binyan Xu, Haitao Li, Kehuan Zhang
- 날짜: 2026-06-29
- URL: https://arxiv.org/abs/2606.30005
- 확인수준: [초록+HTML(초록 페이지 수준)]

### 한 문장 요약
모델은 자기 컨텍스트에 "고유수용감각적으로 눈이 멀어(proprioceptively blind)" 있다 — 학습된 압축 정책이 아니라 컨텍스트 상태를 노출하는 인터페이스(VISTA)만 주면 유능한 컨텍스트 관리가 이미 잠재되어 있음을 발현시킬 수 있다.

### 문제 정의
장기 툴 에이전트는 컨텍스트가 윈도 한계로 자라며 병목. 기존 시스템은 (a) 증거를 버리는 압축 정책을 학습하거나 (b) 에이전트가 못 보는 계층에서 관리한다. 더 근본적 공백: 모델은 프롬프트만으로 각 블록이 얼마나 크고/오래됐고/얼마나 쓰였는지 볼 수 없다 — keep/drop 결정에 필요한 신호가 없다.

### 핵심 방법
**VISTA (Visible Internal State for Tool Agents)**: training-free, model-agnostic 계층.
1. 작업 기억을 typed·addressable 블록으로 표현.
2. 블록별 token usage·recency·access history를 노출하는 runtime dashboard.
3. 블록을 recoverable full-fidelity payload로 archive.

### 주요 기여
1. "모델은 컨텍스트에 대해 proprioceptively blind" 논제 — 부족한 것은 정책이 아니라 인터페이스.
2. 학습·아키텍처 수정 없이 여러 백본에 이식되는 대시보드 인터페이스.
3. 대시보드가 archive/recovery 툴을 넘어서는 독립적 기여를 함을 ablation으로 확인.

### 실험 결과 (정량)
- LOCA-Bench에서 Gemini-3-Flash를 22.7%→50.7%로 상승.
- 동일 미학습 인터페이스가 million-/100K-/10K-scale trajectory(LOCA-Bench, BrowseComp-Plus, GAIA)에 전이, 4개 백본 개선.
- lift가 컨텍스트 압력에 비례해 증가하고 백본 간 전이.
- Ablation: 대시보드가 archive/recovery를 넘어 기여.
- (출처: 초록; 백본별·벤치별 세부 수치는 본문)

### 한계
- (저자) 초록에 명시 한계 없음.
- (분석자) 대시보드가 컨텍스트 자체 토큰을 소비 → 대시보드 오버헤드 대비 순이익의 세부 회계 불명. 관리 품질이 모델의 "잠재 능력"에 의존 → 약한 모델에선 인터페이스가 있어도 관리가 부실할 수 있음(초록의 "capable models" 전제).

### 하네스 엔지니어링 관련성
- 하위 주제 태그: context-engineering, memory, agent-loop
- 왜 중요한가: "학습된 정책 vs 인터페이스 노출"이라는 설계 축을 명확히. [[2605.30785]] AdaCoM(외부 학습 관리자)과 정반대 철학 — training-free 자기관리. [[2606.22953]]의 진단(모델이 컨텍스트 상태를 못 봄)에 대한 처방적 대응.

### 인용용 핵심 사실 (검증 대상)
- VISTA(training-free 대시보드)가 LOCA-Bench에서 Gemini-3-Flash를 22.7%→50.7%로 상승.
- 동일 미학습 인터페이스가 4개 백본, 세 벤치(10K~1M 토큰 스케일)에 전이하며 lift가 컨텍스트 압력에 비례.

---

## 2605.30785 — Learning Agent-Compatible Context Management for Long-Horizon Tasks (AdaCoM)

- 저자/기관: Lu Yi, Runlin Lei, Liuyi Yao, Yuexiang Xie, Yuyang Li, Wenhao Zhang (+3)
- 날짜: 2026-05-29
- URL: https://arxiv.org/abs/2605.30785
- 확인수준: [전문] (HTML 본문에서 액션·리워드·수치 확인)

### 한 문장 요약
**frozen(동결) 에이전트**의 컨텍스트를 외부 LLM 관리자가 RL로 관리(AdaCoM) — 클로즈드 에이전트에도 적용 가능하며, 에이전트 능력에 따라 최적 전략이 달라지는 Fidelity-Reliability Trade-off를 발견.

### 문제 정의
장기 태스크(웹 검색·딥리서치)에서 누적 컨텍스트가 long-context degradation을 유발. 기존 완화책은 에이전트 자체를 학습해야 해서 클로즈드 에이전트에 부적합하고, 에이전트마다 다른 전략이 필요함을 무시.

### 핵심 방법
외부 관리자 LLM(Qwen3-4B-Instruct 초기화)이 동결 에이전트 컨텍스트에 구조화 JSON 액션 수행:
- **Rewrite**(내용 수정), **Delete**(빈 내용으로 제거), **Merge**(병합), **Preserve**(유지).
- **GRPO** + PPO식 token-level clipping. 2단계 advantage:
  - Task-level: LLM judge의 이진 결과 리워드.
  - Step-level process 리워드: 길이초과 -0.8, 중복 action -0.4, 잘못된 JSON -0.5, gold 문서 발견 +0.6 / key 문서 +0.3.
- SFT warm-up 후 RL (batch G=8, process reward weight α=0.1).

### 주요 기여
1. 동결 에이전트를 위한 외부 학습형 컨텍스트 관리자 — 에이전트 재학습 불필요.
2. Fidelity-Reliability Trade-off 발견 및 정량화.
3. 능력 근접성(vanilla ReAct 성능)이 관리자 전이를 좌우함을 실증.

### 실험 결과 (정량)
- BrowseComp-Plus(웹 검색): 평균 24.17%→33.60% (+39.0%). 개별: Qwen3-Max 27.78%→36.67%, Kimi-K2 18.56%→36.20%(+95%), GLM-4.5-Air 32.56%→35.33%, DeepSeek-V3 17.78%→26.19%.
- MCP-Bench-Wiki(딥리서치): 평균 51.28%→59.05% (+15.2%).
- Fidelity-Reliability: 강한 에이전트(GLM, 베이스 32.56%)는 관리 후 7.0K 토큰 raw 보존, 약한 에이전트(DeepSeek 17.78%)는 1.9K로 aggressive 압축.
- 전이: 28개 cross-agent pair 중 23개가 ReAct 베이스라인 개선(평균 cross-agent +22.1%), 최대 +79.6%(DeepSeek-학습 관리자가 Kimi에).
- (출처: HTML 본문 Table/Section)

### 한계
- (저자) 능력 격차가 큰 에이전트 간 전이는 약함; DeepSeek/Kimi는 다른 메모리 스타일 선호, GLM은 aggressive 압축에 민감, Gemini는 report-style 포맷과 비호환.
- (분석자) 외부 관리자 학습에 RL 파이프라인+리워드 설계 비용이 큼(VISTA의 training-free와 대비). 리워드가 태스크별 gold/key 문서 라벨에 의존 → 라벨 없는 도메인엔 적용 난이도.

### 하네스 엔지니어링 관련성
- 하위 주제 태그: context-engineering, agent-loop, memory
- 왜 중요한가: "컨텍스트 관리자를 에이전트 외부에 두고 RL로 학습" 축의 대표작. [[2606.30005]] VISTA(training-free 인터페이스)와 정반대 접근으로, 종합 시 "학습 vs 무학습 × 내부 vs 외부" 2×2 설계 공간을 형성. Fidelity-Reliability Trade-off는 [[2605.23296]]의 요약 볼륨 제어 논의와 연결.

### 인용용 핵심 사실 (검증 대상)
- AdaCoM이 BrowseComp-Plus에서 평균 24.17%→33.60%(+39.0%), MCP-Bench-Wiki에서 51.28%→59.05%(+15.2%) 개선.
- Fidelity-Reliability Trade-off: 강한 에이전트는 raw 보존(고fidelity), 약한 에이전트는 aggressive 압축(신뢰성 유지); 28 cross-agent pair 중 23개 개선.

---

## 2606.17016 — TokenPilot: Cache-Efficient Context Management for LLM Agents

- 저자/기관: Buqiang Xu, Zirui Xue, Dianmou Chen, Chenyang Fu, Chiyu Wu, Caiying Huang (+9) — ZJUNLP (LightMem2 통합)
- 날짜: 2026-06-15
- URL: https://arxiv.org/abs/2606.17016
- 확인수준: [초록+HTML(초록 페이지 수준)]

### 한 문장 요약
텍스트 pruning/eviction이 prefix를 어긋나게 해 prompt cache를 무효화하는 "text sparsity vs cache continuity" 트레이드오프를 지적하고, ingestion 단계에서 prefix를 안정화 + lifecycle 기반 eviction으로 캐시를 보존하는 dual-granularity 관리 프레임워크.

### 문제 정의
장기 세션에서 컨텍스트 누적이 비용을 키운다. 기존 pruning/eviction은 무제약 sequence mutation으로 레이아웃을 바꿔 **prefix mismatch → cache invalidation**을 유발. 텍스트를 줄이면 캐시를 잃는 근본 트레이드오프.

### 핵심 방법
Dual-granularity:
- **전역: Ingestion-Aware Compaction** — framework harness로서 ingestion gate에서 prompt prefix를 안정화하고 open-world 환경 노이즈 제거.
- **국소: Lifecycle-Aware Eviction** — 컨텍스트 세그먼트의 residual utility를 모니터링, 태스크 관련성이 만료될 때만 conservative batch-turn 스케줄로 offload.

### 주요 기여
1. text sparsity와 prompt cache continuity 간 트레이드오프를 명시적으로 정식화 — 토큰 삭감이 캐시 재계산을 강제함을 지적.
2. ingestion gate에서 prefix 안정화(전역) + 만료 기반 eviction(국소)의 이중 계층.
3. LightMem2에 통합(오픈소스).

### 실험 결과 (정량)
- PinchBench / Claw-Eval, isolated 모드: 비용 61% / 56% 절감.
- continuous 모드: 비용 61% / 87% 절감.
- 성능은 기존 시스템 대비 경쟁력 유지.
- (출처: 초록)

### 한계
- (저자) sparsity vs cache continuity는 내재적 최적화 과제로 남음(완전 해결 아님).
- (분석자) batch-turn 스케줄의 conservative offload가 늦은 eviction으로 이어져 일부 상황에서 토큰 절감이 제한될 수 있음. 두 벤치(PinchBench, Claw-Eval)에 한정.

### 하네스 엔지니어링 관련성
- 하위 주제 태그: context-engineering, tool-orchestration, 기타(serving/cost)
- 왜 중요한가: 컨텍스트 관리를 **KV-cache 인프라 관점**에서 재정의 — 대부분의 pruning 논문이 무시하는 캐시 무효화 비용을 1급 제약으로. [[2605.23296]] Parallel Compaction(서빙 관점)과 함께 "컨텍스트 관리 = 시스템/서빙 문제" 계열.

### 인용용 핵심 사실 (검증 대상)
- TokenPilot이 PinchBench/Claw-Eval에서 isolated 모드 비용 61%/56%, continuous 모드 61%/87% 절감하며 성능 경쟁력 유지.
- 핵심 통찰: 무제약 텍스트 mutation이 prefix mismatch를 일으켜 prompt cache를 무효화.

---

## 2606.31564 — ACE: Pluggable Adaptive Context Elasticizer across Agents

- 저자/기관: Ning Liao, Zihao Long, Xiaoxing Wang, Xue Yang, Yaoming Wang, Ziyuan Zhuang (+3)
- 날짜: 2026-06-30
- URL: https://arxiv.org/abs/2606.31564
- 확인수준: [전문] (HTML 본문에서 벤치·수치·메커니즘 확인)

### 한 문장 요약
각 히스토리 스텝을 매 결정 스텝마다 raw/abstract/drop 중 하나로 **가역적(reversible)** 재배정하는 plug-and-play 모듈 — 학습·아키텍처 수정 없이 4개 에이전트 프레임워크에 적용되어 truncation·summarization을 일관 상회.

### 문제 정의
에이전트 태스크 복잡화로 trajectory가 급격히 길어진다. truncation/summarization은 **비가역적**: 버리거나 압축한 정보를 나중에 크리티컬해도 복구 불가.

### 핵심 방법
- **Lossless message maintenance layer**: 각 히스토리 스텝의 raw 메시지 + 압축 abstraction 둘 다 저장.
- **Context orchestration layer**: 현재 태스크 상태 기반으로 매 결정 스텝마다 각 스텝에 elastic type(raw/abstract/drop) 배정. 한 스텝에서 압축된 것을 이후 스텝에서 raw로 복원 가능(가역).
- 결정 함수는 태스크 설명 + 모든 스텝 abstraction을 입력으로 받음(Eq. 3). 학습·구조 변경 없음.

### 주요 기여
1. 가역적 elastic context 관리 — truncation/summarization의 비가역성 극복.
2. 학습 없이 ReAct·DeepAgent·WebThinker·MiroFlow 4개 프레임워크에 plug-in.
3. 토큰 길이를 ReAct 대비 낮게 유지하면서 정보 복원 능력 확보.

### 실험 결과 (정량)
- 벤치: GAIA, HLE, WebShop (+ WebWalkerQA, xBench-DS, BrowseComp-ZH).
- ReAct(GPT-4.1) GAIA All: vanilla 38.8 → ACE 42.4 (+3.6); truncation 37.0, summarization 40.0.
- ReAct(Gemini-3.1-flash-lite-preview) GAIA All: 46.1 → 52.7 (+6.6).
- DeepAgent GAIA: +1.8(GPT-4.1)/+4.8(Gemini); WebThinker: +10.7/+8.8; MiroFlow: +10.3/+1.9.
- 토큰: per-step 입력 길이가 ReAct보다 유의하게 낮고, 선형 증가 대신 완만·변동 추세(Fig. 2).
- (출처: HTML 본문 Table 1-4, Section 3.2/4.4)

### 한계
- (저자) 초록에 명시 한계 적음.
- (분석자) lossless 저장(raw+abstract 이중 보관)이 메모리 오버헤드 유발 — 초장기 trajectory에서 저장 비용 스케일 불명. orchestration 결정 자체의 LLM 호출 비용/지연 회계가 초록 수준에서 불투명. 프레임워크별 gain 편차가 큼(+1.8~+10.7).

### 하네스 엔지니어링 관련성
- 하위 주제 태그: context-engineering, agent-loop
- 왜 중요한가: **가역성(reversibility)**을 컨텍스트 관리의 핵심 설계 원리로 격상. [[2606.30005]] VISTA의 archive/recovery와 개념 공유하나, ACE는 매 스텝 자동 재배정. 크로스-프레임워크 이식성 실증은 [[2605.30785]] AdaCoM의 크로스-에이전트 전이와 대비되는 "무학습 이식" 증거.

### 인용용 핵심 사실 (검증 대상)
- ACE(training-free)가 ReAct GAIA All에서 vanilla 38.8→42.4(GPT-4.1), 46.1→52.7(Gemini)로 개선하며 truncation/summarization 상회.
- 각 히스토리 스텝을 raw/abstract/drop으로 매 결정 스텝마다 가역적으로 재배정(한 번 압축한 스텝도 raw 복원 가능).

---

## 2605.01920 — A Language for Describing Agentic LLM Contexts (ACDL)

- 저자/기관: Noga Peleg Pelc, Gal A. Kaminka, Yoav Goldberg (Bar-Ilan / AI2 계열)
- 날짜: 2026-05-03
- URL: https://arxiv.org/abs/2605.01920
- 확인수준: [전문] (HTML 본문에서 구문·예제·한계 확인)

### 한 문장 요약
프롬프트가 상호작용 스텝에 따라 어떻게 진화하는지를 정밀·가독·표준적으로 기술하는 언어 ACDL — 화이트보드에 손으로 그리거나 형식 언어로 렌더링 가능한, 컨텍스트 엔지니어링의 "공통 표기법".

### 문제 정의
LLM 컨텍스트 구성은 산문·임시 다이어그램·코드 직접 검사로 전달되어, 프롬프트가 스텝별로 어떻게 진화하는지 또는 두 컨텍스트 전략이 어떻게 다른지를 정밀히 담지 못함. 표준 부재.

### 핵심 방법
ACDL 구문(Section 4):
- **Role messages**: System/User/Assistant/Tool(+legacy None).
- **Dynamic content**: constant 템플릿, system state, environment state, prior LLM response, computed function 5종.
- **Time-indexed references**: @T(현재), @T.I(substep) — 컨텍스트를 시간의 함수로 모델링.
- **Control flow**: ForEach, If/ElseIf/Else, Switch/Case (프롬프트/메시지 양 수준).
- **Fragments**: 재사용 가능한 string/role 조각.

### 주요 기여
1. 컨텍스트 구조·동역학의 표준 기술 언어 — 프롬프트를 시간의 함수로 표현.
2. 화이트보드-드로잉 가능 + 형식 렌더링 가능한 이중 표현, 시각화 툴링(웹 에디터, VS Code 확장, Claude Code skill).
3. 기존 시스템(OpenCode, OpenClaw, Gemini Plays Pokémon, DeepSeek-V4, 3종 ReAct 변형) 문서화로 유용성 시연.

### 실험 결과 (정량)
- 언어 제안 논문 — 정량 평가는 제한적. MINT 벤치(Appendix A)에서 7개 컨텍스트 구성 비교, best/worst 구성 간 격차 ~5pp(GPT-4-Turbo).
- 단, "GPT-5 등 강한 모델은 MINT의 짧은 프롬프트·단순 태스크에서 이 구분에 대체로 둔감"이라 명시(Appendix A).
- (출처: HTML 본문 Section 4-5, Appendix A)

### 한계
- (저자) (1) 구성 중 state가 immutable하다고 가정 → 컨텍스트 구성 중 state mutation 있는 시스템은 번역이 번거로움(Section 7). (2) 별도 clock + shared mutable state를 갖는 멀티에이전트 시스템은 깔끔히 기술 불가(명시적 clock sync가 필요해 비우아함).
- (분석자) 정량적 이점보다 "커뮤니케이션/형식화" 이점 중심 → 채택은 커뮤니티 합의에 의존. 강한 모델이 컨텍스트 구분에 둔감하다는 점이 ACDL의 실무 필요성을 약화시킬 소지.

### 하네스 엔지니어링 관련성
- 하위 주제 태그: context-engineering, 기타(specification/formalism)
- 왜 중요한가: 컨텍스트 엔지니어링의 **기술(description) 표준** 후보. 이 서베이가 여러 컨텍스트 전략(truncation/summarization/elastic/pinning)을 비교할 때 공통 표기 어휘를 제공. [[2605.05400]] Mise en Place(방법론), [[2605.08435]] 설정 데이터셋(실측)과 함께 "컨텍스트를 어떻게 명세·기록하는가" 축.

### 인용용 핵심 사실 (검증 대상)
- ACDL은 role message 시퀀스, 시간 인덱스 참조(@T), 조건/반복 구조로 프롬프트가 스텝별로 진화하는 전체 구조를 구현 독립적으로 명세.
- 언어 제안 논문으로, MINT 평가에서 컨텍스트 구성 간 최대 ~5pp 격차를 보이나 강한 모델은 둔감(Appendix A).

---

## 2605.23296 — Parallel Context Compaction for Long-Horizon LLM Agent Serving

- 저자/기관: Musa Cim, Burak Topcu, Chita Das, Mahmut Taylan Kandemir (Penn State 계열, 시스템)
- 날짜: 2026-05-22
- URL: https://arxiv.org/abs/2605.23296
- 확인수준: [전문] (HTML 본문에서 표·수치 확인)

### 한 문장 요약
LLM 요약 기반 컨텍스트 compaction의 blocking 호출이 추론을 수십 초 정지시키는 문제를, 대화를 블록으로 분할해 병렬 요약(parallel compaction)함으로써 wall-time·throughput·요약 볼륨 제어 가능성을 개선하는 **서빙 관점** 연구.

### 문제 정의
장기 에이전트는 히스토리가 윈도를 초과. LLM 요약 compaction은 (1) 본질적으로 lossy, (2) blocking 호출로 수십 초 stall, (3) operator가 요약 볼륨을 세밀 제어 불가(프롬프트 지시 대부분 무시), (4) run 간 유지 정보가 크게 요동쳐 예측 불가.

### 핵심 방법
3단계 parallel compaction(Section 4): 대화를 고정 크기 블록으로 snapshot·분할 → prefix-aware 레이아웃으로 모든 블록을 워커에 동시 dispatch(각 워커는 자기 블록까지의 전체 히스토리 수신, cross-block context 보존 + prefix cache 재사용) → 순서대로 per-block 요약 병합. XML 마커로 타깃 블록 delimit.

### 주요 기여
1. 장기 에이전트 흐름을 위한 parallel compaction 정식화 및 sequential 동기 베이스라인과 특성화.
2. operator에게 요약 볼륨의 세밀·예측 가능 제어 + 블록별 타깃 프롬프트 엔지니어링 부여.
3. compaction의 run 간 비재현성(semantic drift) 정량화.

### 실험 결과 (정량)
- 4개 백본(Llama-3.1-8B dense/non-reasoning, gpt-oss-20B MoE/reasoning, Llama-3.3-70B dense, gpt-oss-120B MoE), HotpotQA·LoCoMo.
- Sequential compaction이 wall-time의 최대 62.4% 소비(Table 2).
- Wall-time: Llama-3.3-70B HotpotQA 1.40× speedup(4k 블록); gpt-oss-120B LoCoMo 1.49-1.60×(8-16k). Compaction throughput 최대 2.52× 개선(matched decode volume).
- 요약 볼륨 제어(96k 입력, gpt-oss-120B, Table 10): sequential 0.79-4.16% 유지 vs 4k 블록 12.37-34.13%, 2k 블록 28.16-50.98%.
- 비재현성: 출력 길이 변동계수 42.9-84.5%(Table 5); 최장 컨텍스트에서 run 간 cosine similarity 0.472-0.624.
- (출처: HTML 본문 Table 2/5/7/10)

### 한계
- (저자) prefill 비용이 큰 블록에서 병렬 이득 제한; 작은 블록은 uncached per-worker prefill 오버헤드 증가. 향후: 동적 블록 크기, marker-awareness 파인튜닝, 완전 asynchronous compaction.
- (분석자) 이득이 wall-time·throughput 위주 — 요약 품질/downstream 정확도 개선은 부차적(요약은 여전히 lossy). 비재현성 문제 자체를 해결하기보다 "제어 가능성"을 부여.

### 하네스 엔지니어링 관련성
- 하위 주제 태그: context-engineering, 기타(serving/systems)
- 왜 중요한가: 컨텍스트 관리를 **서빙 인프라·지연 시간** 문제로 다룸. [[2606.17016]] TokenPilot(캐시 효율)과 함께 "컨텍스트 관리 = 시스템 문제" 축을 형성. 비재현성(run 간 semantic drift) 정량화는 [[2605.30785]] AdaCoM의 요약 볼륨 논의와 [[2606.22528]]의 "요약이 정책을 drop"과 연결.

### 인용용 핵심 사실 (검증 대상)
- Sequential 동기 compaction이 end-to-end wall-time의 최대 62.4%를 소비; parallel compaction으로 최대 1.60× wall-time speedup, 2.52× throughput(matched decode).
- compaction 요약이 run 간 크게 요동(출력 길이 변동계수 42.9-84.5%, 장기 컨텍스트 run 간 cosine similarity 0.472-0.624)해 성능 비재현성 유발.

---

## 2605.05400 — Mise en Place for Agentic Coding: Deliberate Preparation as Context Engineering Methodology

- 저자/기관: Andrew Zigler
- 날짜: 2026-05-06
- URL: https://arxiv.org/abs/2605.05400
- 확인수준: [전문] (HTML 본문에서 3단계·케이스스터디·자기명시 한계 확인)

### 한 문장 요약
"vibe coding"의 준비 부족을 정렬 문제로 규정하고, 요리의 mise en place(모든 것을 제자리에)를 빌려 (1)맥락 접지 (2)협업 명세 (3)태스크 분해의 3단계 준비 방법론과 "context fluency" 개념을 제안하는 **방법론/포지션 논문**.

### 문제 정의
AI 코딩 에이전트의 지배적 워크플로 "vibe coding"이 구현 속도를 준비보다 우선 → 맥락 부족 에이전트가 광범위한 디버깅·리팩터링이 필요한 코드를 산출하는 체계적 정렬 문제.

### 핵심 방법
3단계 MEP:
1. **Contextual grounding**: 도메인 전문성·암묵지를 구조화 문서로 외부화(markdown — 도메인 지식, 경쟁 분석, 설계 철학).
2. **Collaborative specification**: 인간-에이전트 대화로 설계 산출물(화면·상호작용·데이터 흐름·품질 기준, "what"뿐 아니라 "why").
3. **Task decomposition**: 명세를 의존성 인식 태스크 레코드(Beads 포맷)로 변환.
- **Context fluency**: "에이전트가 행동할 수 있는 풍부·구조화된 맥락을 만드는 능력" — decomposition/specification/constraint definition/domain encoding 4요소, 프롬프팅보다 상위(informational architecture).
- 이론적 근거: backward design(Wiggins & McTighe), Polanyi 암묵지, Nonaka-Takeuchi SECI externalization.

### 주요 기여
1. 준비(preparation)를 컨텍스트 엔지니어링 방법론으로 정식화.
2. "context fluency"를 신흥 개발자 역량으로 개념화.
3. 준비-단계 방법론 검증을 위한 연구 어젠다(RQ1-RQ5).

### 실험 결과 (정량)
- 단일 해커톤 사례: ~2시간 준비(9,386단어 계획 문서, 64 task beads) → 184분 구현(4개 병렬 서브에이전트), 8,496줄 코드, 43 beads 종료(중앙값 5.9분/태스크), 준비:실행 ~5.7:1, "near-zero architectural rework".
- (출처: HTML 본문 케이스스터디 절)

### 한계
- (저자) 명시적: "경험적 주장이 단일 해커톤·단일 실무자·무통제군에 의존" — 일반화 불가, MEP는 "출발 프레임워크"(Section 6.2에 비교연구·복제·종단 연구 필요 명시).
- (분석자) 정량 지표가 사례 서술 수준 — 통제된 A/B 부재. 성과가 준비 때문인지 실무자 숙련 때문인지 분리 안 됨.

### 하네스 엔지니어링 관련성
- 하위 주제 태그: context-engineering, 기타(methodology/practice)
- 왜 중요한가: 컨텍스트 엔지니어링을 **런타임 관리(pruning/compaction)가 아니라 사전 준비**로 보는 상보적 관점. [[2605.08435]] 설정 데이터셋(실측된 준비 산출물: Context Files/Skills)의 방법론적 짝. 서베이의 "human-side context engineering" 축을 대표하나, 증거 수준은 사례 1건으로 약함(발전 방향 후보).

### 인용용 핵심 사실 (검증 대상)
- MEP는 contextual grounding → collaborative specification → task decomposition의 3단계 준비 방법론이며 "context fluency"를 신흥 개발자 역량으로 제안.
- 단일 해커톤 사례(약 2시간 준비 → 184분 병렬 구현); 저자 스스로 단일 실무자·무통제군의 비일반화 한계를 명시.

---

## 2605.08435 — A Dataset of Agentic AI Coding Tool Configurations

- 저자/기관: Matthias Galster, Seyedmoein Mohsenimofidi, Levi Böhme, Jai Lal Lulla, Muhammad Auwal Abubakar, Christoph Treude (+1)
- 날짜: 2026-05-08
- URL: https://arxiv.org/abs/2605.08435
- 확인수준: [전문] (HTML 본문에서 데이터 구성·8 메커니즘·통계 확인)

### 한 문장 요약
Claude Code·Codex 등 5개 도구의 리포지토리-레벨 설정 아티팩트(Context Files·Skills·Rules·Hooks 등 8종)를 4,738개 GitHub 리포에서 대규모 수집한, 컨텍스트 엔지니어링 실증 연구용 공개 데이터셋(CC BY 4.0).

### 문제 정의
Agentic 코딩 도구를 조종하기 위해 개발자가 만드는 리포지토리-레벨 설정 아티팩트가 대규모로 큐레이션된 데이터셋이 없음.

### 핵심 방법
파이프라인: SEART 187,304 리포 → 메타데이터 필터로 40,585 활성 리포 → GPT-5.2 분류로 36,710 engineered project → 설정 아티팩트 탐지로 최종 4,738 리포.
8개 설정 메커니즘: **Context Files, Skills, Subagents, Commands, Rules, Settings, Hooks, MCP Configurations**.

### 주요 기여
1. 5개 도구 × 8개 메커니즘의 대규모 설정 아티팩트 코퍼스(공개, 재현 가능 파이프라인).
2. 설정 파일 전문 + AI-co-authored 커밋 포함으로 채택·거버넌스·인간-AI 협업 연구 지원.

### 실험 결과 (정량)
- 4,738 리포, 설정 아티팩트 15,591개, 설정 파일 전문 18,167개, AI-co-authored 커밋 148,519개.
- 메커니즘별 분포: Context Files 9,470파일/4,463리포(최다), Skills 2,430/547, Commands 1,098/284, Rules 997/298, Subagents 884/273, Settings 472/447, MCP 138/124, Hooks 102/101.
- 도구별: Claude Code 2,525리포(최다), Copilot 1,397, Cursor 466. Cursor 리포의 63.5%가 Rules 채택(타 도구 최대 17.0% 대비 두드러짐).
- (출처: HTML 본문 데이터 구성/분포 절)

### 한계
- (저자) 초록에 방법론 한계 명시 적음(데이터셋 논문).
- (분석자) GitHub 공개 리포 편향(사적/사내 설정 미포함), 특정 시점 스냅샷(급변하는 도구 생태계). GPT-5.2 분류 기반 필터링의 오분류 가능성.

### 하네스 엔지니어링 관련성
- 하위 주제 태그: context-engineering, tool-orchestration, 기타(dataset/empirical)
- 왜 중요한가: **실무에서 실제로 쓰이는 컨텍스트 엔지니어링 메커니즘의 실측 근거**. Context Files가 압도적 다수라는 통계는 "가장 널리 쓰이는 컨텍스트 관리 = 정적 컨텍스트 파일"임을 시사 — [[2605.05400]] Mise en Place의 externalization 주장을 데이터로 뒷받침. [[2605.01920]] ACDL이 기술하려는 대상의 실물 코퍼스.

### 인용용 핵심 사실 (검증 대상)
- 4,738 리포에서 15,591 설정 아티팩트·18,167 설정 파일·148,519 AI-co-authored 커밋 수집; 5개 도구 × 8개 설정 메커니즘.
- Context Files가 최다 채택(9,470파일/4,463리포); Cursor 리포의 63.5%가 Rules 사용(타 도구 대비 두드러짐).

---

## 2507.13334 — A Survey of Context Engineering for Large Language Models  ⚠️ [배경/컷오프 이전, OUT]

- 저자/기관: Lingrui Mei, Jiayu Yao, Yuyao Ge, Yiwei Wang, Baolong Bi, Yujun Cai (+9)
- 날짜: 2025-07-17 (지식 컷오프 이전 — **배경 문헌**, 본 서베이의 신규 기여 대상 아님)
- URL: https://arxiv.org/abs/2507.13334
- 확인수준: [전문] (HTML 목차/택소노미 확인)

### 한 문장 요약
Context Engineering을 단순 프롬프트 설계를 넘어선 정식 분과로 정의하고, 1400+ 논문을 (context retrieval/generation · processing · management) 3대 기초 컴포넌트와 (RAG · memory · tool-integrated reasoning · multi-agent) 시스템 구현으로 체계화한 배경 서베이.

### 문제 정의 / 택소노미 (본 테마 정리에 유용한 뼈대)
- 기초 컴포넌트: **Context Retrieval & Generation**(§4.1), **Context Processing**(§4.2: long-context, self-refinement, multimodal, structured), **Context Management**(§4.3: fundamental constraints, memory hierarchies & storage, context compression, applications).
- 시스템 구현: RAG(§5.1), Memory Systems(§5.2), Tool-Integrated Reasoning(§5.3), Multi-Agent Systems(§5.4).

### 주요 기여 / 핵심 사실
- Context Engineering의 정식 분과화 + 통합 택소노미(1400+ 논문 분석).
- 핵심 연구 공백: **capability asymmetry** — 모델은 복잡한 컨텍스트 "이해"엔 능하나 동등하게 정교한 "장문 생성"엔 뚜렷한 한계.

### 하네스 엔지니어링 관련성 및 위상
- 하위 주제 태그: context-engineering (배경/OUT)
- 왜 중요한가: 본 서베이(harness engineering)의 **컨텍스트 관리 하위 택소노미를 귀납할 때 기준 골격** 제공. 단, 컷오프 이전 문헌이므로 "선행 배경"으로만 인용하고, 위 11개 신규 논문이 이 골격의 "compression/management" 칸을 어떻게 채우고 확장하는지를 대비시키는 용도로 사용해야 함.

### 인용용 핵심 사실 (검증 대상)
- 1400+ 논문을 3대 기초 컴포넌트(retrieval/generation, processing, management) + 4대 시스템 구현(RAG, memory, tool-integrated reasoning, multi-agent)으로 체계화.
- 핵심 공백: 컨텍스트 "이해"와 정교한 "장문 생성" 능력 간 비대칭. (2025-07 배경 문헌)

---

## 공통 관점 (Cross-cutting Synthesis)

이 테마의 11편(+배경 서베이 1편)은 "에이전트 컨텍스트를 어떻게 구성·유지·회수·거버넌스하는가"를 서로 다른 계층에서 공략한다. 하네스 렌즈에서 다음 축들이 반복 등장한다.

**1. "덜 담을수록 낫다"는 반직관 — 그러나 무엇을 남기느냐가 관건**
- Less Context([[2606.10209]])는 full-history(71%)보다 pruning+summary(91.6%)가 낫다는 직접 증거. Plans Don't Persist([[2606.22953]])는 그 이유를 hidden-state로 설명: 정보는 종종 persistent가 아니라 context-resident라, 잘못 버리면(plan eviction) ALFWorld -34.7pp. 즉 pruning의 이득과 위험이 동전의 양면.

**2. 비가역성 vs 가역성 — 회수 가능성이 새 설계 원리**
- truncation/summarization의 비가역성을 문제로 지목하고 회수를 설계에 넣는 흐름: ACE([[2606.31564]], raw/abstract/drop 매 스텝 재배정), VISTA([[2606.30005]], full-fidelity archive + 복구). "한 번 버리면 끝"에서 "필요하면 되살린다"로.

**3. 학습 정책 vs 인터페이스 노출 (× 내부 vs 외부) — 2×2 설계 공간**
- AdaCoM([[2605.30785]])은 **외부 학습(RL) 관리자**로 동결 에이전트 컨텍스트 관리(+39% BrowseComp-Plus). VISTA([[2606.30005]])는 정반대 — **training-free 인터페이스**만 주면 "잠재된" 관리 능력 발현(Gemini-3-Flash 22.7→50.7%). ACE는 무학습 외부 모듈. 이 세 편이 "학습/무학습 × 내부/외부" 공간을 채운다.

**4. 컨텍스트 관리 = 시스템/서빙/캐시 문제**
- TokenPilot([[2606.17016]])은 pruning이 KV-cache를 무효화하는 비용을 1급 제약으로(비용 최대 87% 절감). Parallel Compaction([[2605.23296]])은 요약 blocking이 wall-time 62.4%를 먹는 서빙 병목을 병렬화(최대 2.52× throughput). 알고리즘 논문들이 놓치는 인프라 비용을 드러냄.

**5. 컨텍스트 관리 = 안전·거버넌스 표면 (새롭고 중요)**
- Governance Decay([[2606.22528]])는 compaction이 안전 제약을 조용히 삭제해 위반율 0→30%(최대 59%), 요약을 겨냥한 인젝션 공격까지 성립함을 보임. 컨텍스트 관리 계층이 곧 공격 표면. Constraint Pinning으로 완화. [[2606.22953]]의 "load bearing" 주장의 안전판.

**6. 명세·준비·실측 — 인간/기술(description) 측면**
- ACDL([[2605.01920]])은 컨텍스트 전략을 기술하는 표준 언어, Mise en Place([[2605.05400]])는 사전 준비 방법론, 설정 데이터셋([[2605.08435]])은 실무 실측(Context Files가 압도적). 런타임 알고리즘과 대비되는 "컨텍스트를 어떻게 명세·준비·기록하는가" 축.

**측정·근거 성숙도 편차 (검증자·synthesizer 주의)**
- 강한 정량 앵커: Less Context, AdaCoM, ACE, Parallel Compaction, Governance Decay, VISTA(하나의 대표 수치 22.7→50.7), TokenPilot.
- 약한 근거/포지션·언어·데이터셋 성격: Mise en Place(사례 1건, 저자가 비일반화 명시), ACDL(언어 제안, 정량 최소), 설정 데이터셋(기술적 통계).
- **배경/OUT**: 2507.13334(2025-07 컷오프 이전) — 신규 기여로 인용 금지, 택소노미 골격·선행 배경으로만.

**서베이 발전 방향 후보 (한계에서 도출)**
- (a) pruning 윈도·요약 볼륨의 도메인 일반화(Less Context, Parallel Compaction의 도메인 특수성).
- (b) 회수(recovery) 계층의 저장/지연 비용 회계(ACE의 lossless 이중저장, VISTA의 대시보드 오버헤드).
- (c) 거버넌스 제약 자동 식별(Constraint Pinning이 태깅에 의존).
- (d) 클로즈드 모델 적용성(Plans Don't Persist 진단이 hidden-state 접근 필요; AdaCoM은 외부 관리로 우회).
- (e) 요약의 run 간 비재현성(Parallel Compaction) — 아직 "제어"만, 근본 해결 미해결.

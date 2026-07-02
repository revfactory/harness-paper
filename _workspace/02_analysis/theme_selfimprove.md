# 테마 분석: 자기개선 / 진화형 하네스 (Self-improving / Evolving Harnesses)

> 분석자: paper-analyst (self-improve 테마)
> 근거: `_workspace/02_analysis/abstracts.md`의 API 검증 초록 전문 + 앵커 4편(Self-Harness, HarnessX, APEX, HarnessFix) arXiv 초록 페이지 WebFetch 확인.
> 확인수준 주의: arXiv 초록 페이지는 초록만 노출 → 본문 세부(알고리즘 의사코드·per-benchmark 분해표 등)는 초록에 명시된 것만 인용. 초록에 없는 수치는 기록하지 않음.

---

# 2606.09498 — Self-Harness: Harnesses That Improve Themselves

- 저자/기관: Hangfan Zhang, Shao Zhang, Kangcong Li, Chen Zhang, Yang Chen, Yiqun Zhang (+2)
- 날짜: 2026-06-08
- URL: https://arxiv.org/abs/2606.09498
- 확인수준: 초록+앵커 WebFetch (초록 재확인, 본문 미열람)

## 한 문장 요약
LLM 에이전트가 인간 엔지니어나 더 강한 외부 에이전트 없이 자기 자신의 운영 하네스를 반복적으로 개선하는 3단계 루프(약점 채굴 → 하네스 제안 → 회귀검증) 패러다임을 제안한다.

## 문제 정의
효과적인 하네스 설계는 본질적으로 모델별(model-specific)이다. 모델마다 행동이 다르므로 하네스도 달라야 하는데, 현재 하네스는 여전히 인간 전문가가 수작업으로 만든다. 모델이 다양해지고 빠르게 바뀌는 상황에서 이 방식은 확장성이 없다.

## 핵심 방법
3단계 반복 루프:
1. **Weakness Mining(약점 채굴):** 실행 트레이스에서 모델 고유의 실패 패턴을 식별.
2. **Harness Proposal(하네스 제안):** 그 실패에 직접 연결된, 다양하지만 최소한의(minimal) 하네스 수정안 생성.
3. **Proposal Validation(제안 검증):** 회귀 테스트(regression testing)를 통과한 후보 편집만 수용.
최소 초기 하네스(minimal initial harness)에서 시작하여 위 루프를 반복.

## 주요 기여
1. "에이전트가 자기 하네스를 스스로 재설계"하는 자기개선 패러다임의 정식화 및 명명(Self-Harness).
2. 회귀검증 게이트로 안전하게 하네스를 진화시키는 구체적 3단계 알고리즘.
3. 정성 분석으로 "일반적 지시문을 덧붙이는 게 아니라 모델별 약점을 구체적·실행가능한 하네스 변경으로 전환함"을 입증.

## 실험 결과 (정량)
- Terminal-Bench-2.0, 세 계열 베이스 모델 held-out pass rate (출처: 초록):
  - **MiniMax M2.5: 40.5% → 61.9%**
  - **Qwen3.5-35B-A3B: 23.8% → 38.1%**
  - **GLM-5: 42.9% → 57.1%**
- 세 모델 모두에서 일관된 개선.

## 한계
- (저자 명시 범위) 단일 벤치마크(Terminal-Bench-2.0)에서만 검증. 일반화 주장은 제한적.
- (분석자 판단) 최적화 축이 **프롬프트 하네스 단일 차원**에 국한 — 행동 원칙·워크플로 토폴로지는 변경하지 않음(이 한계는 APEX가 명시적으로 지적하며 확장의 출발점으로 삼음).
- 회귀검증이 held-out 셋에 의존 → 라벨/검증셋 확보가 어려운 배포 환경 적용성 문제(이 지점을 RHO 2606.05922가 self-preference로 우회).
- 개선폭이 초기 하네스가 얼마나 "최소"였는지에 의존할 수 있음(낮은 베이스라인에서 큰 상승).

## 하네스 엔지니어링 관련성
- 하위 주제 태그: agent-loop, context-engineering, eval-harness, self-improvement(기타)
- 왜 중요한가: **이 테마의 baseline이자 앵커.** "하네스를 사람이 만드는 정적 산출물"에서 "에이전트가 실행 트레이스로 스스로 진화시키는 대상"으로 전환하는 원형. APEX·HarnessX·HarnessFix·AHE 등이 모두 이 루프(진단→제안→검증)를 계승·확장한다.

## 인용용 핵심 사실 (검증 대상)
- Self-Harness는 3단계(Weakness Mining, Harness Proposal, Proposal Validation) 루프다.
- Terminal-Bench-2.0에서 MiniMax M2.5 40.5%→61.9%, Qwen3.5-35B-A3B 23.8%→38.1%, GLM-5 42.9%→57.1% (held-out pass rate).
- 인간 엔지니어나 더 강한 외부 에이전트에 의존하지 않고 자기 하네스를 개선한다.

---

# 2606.14249 — HarnessX: A Composable, Adaptive, and Evolvable Agent Harness Foundry

- 저자/기관: Tingyang Chen, Shuo Lu, Kang Zhao, Weicheng Meng, Hanlin Teng, Tianhao Li (+8)
- 날짜: 2026-06-12
- URL: https://arxiv.org/abs/2606.14249
- 확인수준: 초록+앵커 WebFetch (초록 재확인. 본문 미공개 — 코드도 "future release" 예정)

## 한 문장 요약
프롬프트·툴·메모리·제어흐름을 타입화된 하네스 프리미티브로 보고, 치환 대수(substitution algebra)로 조립하고 AEGIS 진화엔진으로 트레이스 기반 진화시키는 "하네스 파운드리(foundry)"를 제안한다.

## 문제 정의
하네스가 여전히 대부분 수작업·정적(hand-crafted and static)이다. 새 모델/태스크마다 맞춤 스캐폴딩이 필요하고, 실행 중 생성되는 풍부한 트레이스가 체계적 개선으로 환류되지 않는다.

## 핵심 방법
- **타입화된 하네스 프리미티브 + 치환 대수(substitution algebra):** 하네스를 조합 가능한(composable) 단위들의 대수적 치환으로 조립. (초록은 대수의 구체 연산·프리미티브 목록을 명시하지 않음 — 본문 필요)
- **AEGIS(진화 엔진):** 트레이스 구동(trace-driven) 멀티에이전트 진화 엔진. "심볼릭 적응(symbolic adaptation)과 강화학습(RL) 사이의 operational mirror(작동적 대응)"에 기반. (이 대응의 기계적 정의는 초록에 없음)
- **하네스-모델 루프 폐쇄:** 트레이스를 (a) 하네스 업데이트와 (b) 모델 학습 신호 양쪽으로 동시에 전환 — 양방향 피드백.

## 주요 기여
1. Composable·Adaptive·Evolvable 세 성질을 갖춘 하네스 파운드리 아키텍처.
2. 심볼릭 적응↔RL의 operational mirror 위에 세운 트레이스 구동 진화 엔진 AEGIS.
3. 하네스 업데이트와 모델 학습 신호를 동시에 뽑는 harness-model 공진화 루프.

## 실험 결과 (정량)
- 5개 벤치마크(ALFWorld, GAIA, WebShop, tau^3-Bench, SWE-bench Verified) 평균 **+14.5% (최대 +44.0%)** (출처: 초록).
- "gains largest where baselines are lowest" — 베이스라인이 낮을수록 이득이 큼.
- (주의) per-benchmark 분해 수치는 초록에 미제시.

## 한계
- (분석자 판단) 초록/코드 미공개("open-sourced in a future release") → 재현·독립검증 불가. 치환 대수·AEGIS·operational mirror의 기계적 정의가 초록만으로는 불명확.
- "베이스라인이 낮을수록 이득 큼"은 저성능 시작점에서의 개선 편향 가능성(headroom effect).
- 5개 벤치마크가 이질적이라 평균 +14.5%의 분산이 클 수 있음(per-benchmark 미공개).

## 하네스 엔지니어링 관련성
- 하위 주제 태그: tool-orchestration, context-engineering, memory, agent-loop, self-improvement(기타)
- 왜 중요한가: Self-Harness가 "단일 하네스를 진화"시키는 데 비해, HarnessX는 **하네스를 타입화된 프리미티브의 조합(대수)으로 형식화**하고 그 위에서 진화 + 모델 공학습까지 결합한 "파운드리"로 격상. 하네스를 재사용 가능한 구성요소 대수로 다루는 방향의 대표.

## 인용용 핵심 사실 (검증 대상)
- HarnessX = 치환 대수(substitution algebra) + AEGIS(트레이스 구동 멀티에이전트 진화 엔진).
- 5개 벤치마크(ALFWorld, GAIA, WebShop, tau^3-Bench, SWE-bench Verified) 평균 +14.5%, 최대 +44.0%.
- 트레이스를 하네스 업데이트와 모델 학습 신호 양쪽으로 전환(harness-model loop).

---

# 2606.15363 — APEX: Adaptive Principle EXtraction — 3계층 자기진화 프레임워크

- 저자/기관: Ya-Chuan Chen, Tien-Jen Lai, Hsiang-Wei Hu
- 날짜: 2026-06-13
- URL: https://arxiv.org/abs/2606.15363
- 확인수준: 초록+앵커 WebFetch (초록 재확인)

## 한 문장 요약
Self-Harness가 프롬프트 하네스 단일 축만 진화시키는 한계를 지적하며, 하네스(L1)·행동원칙(L2)·워크플로 토폴로지(L3) 세 계층을 동시에 공진화시키는 프레임워크를 제안한다.

## 문제 정의
SOTA인 Self-Harness는 실패 클러스터를 채굴해 하네스를 패칭하지만 **오직 프롬프트 하네스 한 차원만** 최적화하고, 행동 원칙과 워크플로 토폴로지는 그대로 둔다. 다차원 공진화가 필요하다.

## 핵심 방법
3계층 공진화:
- **L1 (Harness):** 실패 모드 패칭(failure-mode patching)으로 하네스 진화. (Self-Harness 계승)
- **L2 (Behavioural Principles):** 성공 트레이스 증류(success-trace distillation)로 재사용 가능한 행동 원칙 추출.
- **L3 (Workflow Topology):** 구조적 적합도 기반 선택(structural fitness-based selection)으로 에이전트 워크플로 토폴로지 진화.
- 실제 프로덕션 에이전트 **Joe**(NVIDIA Nemotron 기반, Edge AI Agent Factory)에 구현, 15노드 컴퓨트 fleet 관리, 18일간 수집한 114개 실제 태스크 트레이스로 평가.

## 주요 기여
1. Self-Harness의 단일축 한계를 명시적으로 지적하고 3계층 공진화(L1/L2/L3)로 확장.
2. 성공 트레이스 증류로 재사용 가능한 행동 원칙을 추출하는 L2 도입.
3. 극저비용(4 LLM 호출)으로 프로덕션 에이전트에서 실증.

## 실험 결과 (정량)
- **APEX Health Score 0.570 (+90% vs. baseline 0.300)** — 단일 진화 런 (출처: 초록).
- 재사용 가능한 신규 원칙 **6개** 증류.
- research-first 워크플로 토폴로지 선택, **토폴로지 점수 0.900 (+20%)**.
- 비용: **4 LLM 호출(~270초)**, 로컬 qwen2.5-coder:32b 인스턴스.

## 한계
- (분석자 판단) 평가 지표가 "APEX Health Score"라는 자체 정의 복합 지표 + 단일 진화 런 + 단일 프로덕션 시스템(Joe, n=114 트레이스). 표준 벤치마크(Terminal-Bench 등) 직접 비교가 초록에 없어 Self-Harness 대비 우위가 **동일 척도상 비교가 아님**.
- 표본이 작음(114 트레이스, 15노드, 1회 런) → 통계적 견고성 제한.
- "+90%"는 baseline 0.300이라는 낮은 기준에서의 상대 개선.

## 하네스 엔지니어링 관련성
- 하위 주제 태그: agent-loop, multi-agent(토폴로지), context-engineering, self-improvement(기타)
- 왜 중요한가: **Self-Harness → APEX는 이 테마의 핵심 계보.** "하네스만 진화"에서 "하네스+원칙+토폴로지 다차원 공진화"로 확장하는 명시적 후속. 자기개선의 최적화 대상 공간(action space)을 프롬프트 너머로 넓히는 방향을 대표.

## 인용용 핵심 사실 (검증 대상)
- APEX는 Self-Harness가 "프롬프트 하네스 단일 차원만 최적화"한다고 명시적으로 비판하며 L1/L2/L3 3계층으로 확장.
- Self-Harness가 Terminal-Bench-2.0에서 14–21% 개선했다고 APEX가 인용(APEX 초록 기재 수치).
- APEX Health Score 0.570(+90% vs 0.300), 원칙 6개, 토폴로지 0.900(+20%), 4 LLM 호출(~270s).
- 프로덕션 에이전트 Joe(NVIDIA Nemotron), 15노드, 114 트레이스/18일.

---

# 2606.06324 — HarnessFix: 실패 트레이스로부터 신뢰가능 에이전트로 — 하네스 결함 진단·수리

- 저자/기관: Mengzhuo Chen, Junjie Wang, Zhe Liu, Yawen Wang, Qing Wang
- 날짜: 2026-06-04
- URL: https://arxiv.org/abs/2606.06324
- 확인수준: 초록+앵커 WebFetch (초록 재확인)

## 한 문장 요약
실행 트레이스와 하네스 코드를 하네스-인지 트레이스 IR(HTIR)로 컴파일해, 실패를 책임 있는 트레이스 스텝과 하네스 계층에 귀속(attribution)시키고 범위 한정(scoped) 수리 연산자로 패치하는 진단·수리 프레임워크.

## 문제 정의
기존 자기개선/하네스 진화 방법은 런타임 감독·프롬프트 최적화·워크플로 탐색·최종결과 기반 하네스 수정으로 개선하지만, **어느 트레이스 증거가 책임인지·어느 하네스 계층이 원인인지 진단하지 못해** 넓고 간접적이며 범위가 불분명한(broad, indirect, poorly scoped) 변경을 낳는다.

## 핵심 방법
- **HTIR (Harness-aware Trace Intermediate Representation):** 원시 실행 트레이스 + 하네스 코드를 컴파일. 파편화된 궤적 증거를 정규화하고 스텝별 provenance와 제어흐름 관계를 포착.
- **귀속(attribution):** 실패를 (a) 책임 트레이스 스텝과 (b) 책임 하네스 계층에 귀속.
- **결함 레코드 → 범위 한정 수리 연산자(scoped repair operators):** 반복 진단을 실행가능한 flaw record로 통합하고 수리 연산자에 매핑.
- **flaw-specific repair specification 하에 패치 생성·검증:** 목표 결함을 줄이되 허용불가 회귀는 도입하지 않도록 검증.

## 주요 기여
1. 실패의 **위치(where)** 를 짚는 하네스-인지 IR(HTIR) — 스텝·계층 이중 귀속.
2. 넓은/간접 수정 대신 범위 한정 수리 연산자로의 매핑.
3. ETCLOVG 계층에 걸친 반복적 하네스 결함 패턴 발견.

## 실험 결과 (정량)
- SWE-Bench Verified, Terminal-Bench 2.0 Verified, GAIA, AppWorld에서 초기 하네스 대비 held-out 성능 **+15.2% ~ +50.0%** (출처: 초록).
- 인간 설계 baseline 및 자기진화 baseline을 상회.

## 한계
- (분석자 판단) 초록에 **ETCLOVG 약어가 정의되지 않음.** 초록 열거("execution environments, tool interfaces, context, lifecycle orchestration, observability, verification, and governance")로 미루어 E-T-C-L-O-V-G로 추정되나 저자 명시 정의는 미확인 → 인용 시 "추정" 표기 필요.
- "허용불가 회귀는 도입하지 않는다"의 판정 기준(회귀 임계)이 초록만으로는 불명확.
- 개선폭 범위(15.2~50%)가 넓어 벤치마크·결함 유형별 편차가 클 것으로 보임(분해 미제시).

## 하네스 엔지니어링 관련성
- 하위 주제 태그: eval-harness, agent-loop, tool-orchestration, context-engineering, self-improvement(기타)
- 왜 중요한가: 자기개선 계열의 공통 약점인 **"진단 부재(어디를 왜 고쳐야 하는지 모름)"** 를 정면으로 다룸. Self-Harness/APEX가 "무엇을 진화시킬지"를 넓혔다면 HarnessFix는 "실패를 계층·스텝에 귀속시켜 정밀하게 고치는" 진단 인프라를 제공. AHE(2604.25850)의 관측가능성(observability) 3필러와 짝을 이루는 진단 계보.

## 인용용 핵심 사실 (검증 대상)
- HarnessFix는 트레이스+하네스코드를 HTIR로 컴파일해 실패를 트레이스 스텝과 하네스 계층에 이중 귀속.
- SWE-Bench Verified, Terminal-Bench 2.0 Verified, GAIA, AppWorld에서 +15.2%~50.0% 개선.
- 인간 설계 및 자기진화 baseline을 상회, ETCLOVG 계층 걸친 반복 결함 패턴 발견.
- (주의) ETCLOVG 약어의 저자 정의는 초록에 없음 — 인용 시 확인 필요.

---

# 2605.09998 — Continual Harness: 자기개선 파운데이션 에이전트를 위한 온라인 적응

- 저자/기관: Seth Karten, Joel Zhang, Tersoo Upaa, Ruirong Feng, Wenzhe Li, Chengshuai Shi (+2)
- 날짜: 2026-05-11
- URL: https://arxiv.org/abs/2605.09998
- 확인수준: 초록 (전문 미열람)

## 한 문장 요약
코딩 하네스(Claude Code/OpenHands)에 상응하는 것이 임베디드(신체화) 에이전트에는 없다는 관찰에서 출발해, 리셋 없이(reset-free) 단일 런 안에서 프롬프트·서브에이전트·스킬·메모리를 온라인 자기개선하는 하네스를 제안한다.

## 문제 정의
코딩 하네스는 모델을 툴·메모리·플래닝으로 감싸지만, 임베디드 에이전트의 장기·부분관측(long-horizon partial-observability) 의사결정에는 대응물이 없다. 기존 프롬프트 최적화는 에피소드 리셋을 요구하는데 실환경은 리셋이 불가.

## 핵심 방법
- **관찰(GPP):** Gemini Plays Pokemon — 인간 개입 하네스 정제(human-in-the-loop)로 Pokemon Blue, Yellow Legacy hard mode, Crystal를 무패로 클리어(최초). 어려운 구간에서 에이전트가 장기 컨텍스트 메모리로 스스로 전략을 반복 개선하는 창발적 자기개선 신호 관찰.
- **Continual Harness:** 인간을 루프에서 완전 제거. 최소 환경 인터페이스만으로 시작, 행동(acting)과 자기정제(refining)를 번갈아 — 자신의 프롬프트·서브에이전트·스킬·메모리를 과거 궤적 데이터로 개선. **에피소드 리셋 없이 단일 런 내 온라인 적응.**
- **모델 공학습 루프:** 오픈소스 에이전트의 롤아웃을 frontier teacher가 relabel → 모델 가중치 업데이트(온라인 process-reward co-learning). 환경 리셋 없이 인게임 마일스톤 지속 진전.

## 주요 기여
1. 임베디드/장기 의사결정용 리셋-프리 자기개선 하네스 정식화(코딩 하네스의 임베디드판).
2. 최소 인터페이스에서 시작해 수작업 도구·도메인 스캐폴딩 없이 전문가 하네스 격차의 다수를 회복.
3. 하네스 정제 + 모델 가중치 공학습을 온라인으로 결합(SIA와 문제의식 공유).

## 실험 결과 (정량)
- Pokemon Red·Emerald, frontier 모델들: 미니멀 baseline 대비 **버튼 입력(button-press) 비용을 상당히 감소**, 수작업 전문가 하네스와의 격차의 다수(majority)를 회복(capability-dependent).
- (주의) 초록은 구체적 %/절대수치를 제시하지 않고 정성적 서술 위주.

## 한계
- (저자 명시) 이득이 capability-dependent — 약한 모델에서는 회복폭이 작을 수 있음.
- (분석자 판단) 도메인이 게임(Pokemon)에 국한, 정량 지표(button-press cost)가 표준 벤치마크가 아니어서 타 연구와 직접 비교 어려움.
- 초록에 구체 수치 부재 → 개선폭 크기 인용 불가.

## 하네스 엔지니어링 관련성
- 하위 주제 태그: agent-loop, memory, self-improvement(기타), embodied
- 왜 중요한가: 자기개선 하네스를 **코딩 도메인 밖(임베디드·부분관측)으로 확장**하고, 특히 "에피소드 리셋 없는 온라인 적응"이라는 제약을 정면으로 다룸. 대부분의 프롬프트 최적화가 리셋을 전제하는 것과 대비. 하네스 진화 + 모델 가중치 공학습을 온라인 결합(→ SIA와 연결).

## 인용용 핵심 사실 (검증 대상)
- Continual Harness는 리셋-프리, 단일 런 내 온라인으로 프롬프트·서브에이전트·스킬·메모리를 자기개선.
- GPP는 Pokemon Blue/Yellow Legacy(hard)/Crystal를 무패 클리어한 최초 AI 시스템(초록 주장).
- 온라인 process-reward co-learning으로 오픈소스 에이전트 롤아웃을 frontier teacher가 relabel해 모델 가중치 업데이트.

---

# 2605.27276 — SIA: Self Improving AI with Harness & Weight Updates

- 저자/기관: Prannay Hebbar, Yogendra Manawat, Samuel Verboomen, Alesia Ivanova, Selvam Palanimalai, Kunal Bhatia (+1)
- 날짜: 2026-05-26
- URL: https://arxiv.org/abs/2605.27276
- 확인수준: 초록 (전문 미열람)

## 한 문장 요약
하네스만 고치는 "harness-update 학파"와 가중치만 고치는 "test-time training 학파"를 통합해, Feedback-Agent가 하네스와 가중치를 **둘 다** 업데이트하는 자기개선 루프를 제안한다.

## 문제 정의
AI 개선의 병목은 인간. 두 연구 라인이 고립돼 있다: (1) harness-update 학파 — 메타에이전트가 스캐폴드(툴·프롬프트·재시도·탐색)를 재작성, 가중치는 고정. (2) test-time training 학파 — 수작업 RL 파이프라인으로 가중치 업데이트, 하네스는 고정. 두 축을 함께 돌린 적이 없다.

## 핵심 방법
- **SIA (Self-Improving loop):** LM 에이전트인 **Feedback-Agent**가 태스크별 에이전트의 **하네스와 가중치 둘 다** 업데이트.
- 두 레버의 역할 분담: 하네스 업데이트는 모델을 "에이전트답게" 만듦(탐색·행동 방식 조형), 가중치 업데이트는 프롬프트/스캐폴드로 주입 못하는 도메인 직관을 형성.

## 주요 기여
1. harness-update와 weight-update 두 고립 학파를 하나의 루프로 통합(SIA-W+H).
2. 세 대조적 도메인에서 두 레버 결합이 스캐폴드 단독 반복을 능가함을 실증.

## 실험 결과 (정량)
- **SIA-W+H가 세 벤치마크 모두에서 스캐폴드 반복 단독을 능가** (출처: 초록):
  - LawBench(중국 법률 죄목 분류): 선행 SOTA 대비 **+25.1%**
  - 저수준 GPU 커널 최적화: 선행 SOTA 대비 **12.4% 더 빠름 (1,017 vs 1,161 μs)**
  - 단일세포 RNA 디노이징: 선행 SOTA 대비 **+20.4%**

## 한계
- (분석자 판단) 세 도메인이 매우 이질적(법률/GPU/생명정보) → 방법의 일반 프로토콜성보다 도메인별 튜닝 여지. 각 도메인의 "선행 SOTA" 정의·측정 조건이 초록만으로는 불명확.
- 가중치 업데이트가 필요 → Continual Harness/Self-Harness 같은 순수 하네스 진화보다 인프라·비용 부담 큼.
- Feedback-Agent 자체의 신뢰성/발산 방지 메커니즘이 초록에 미기술.

## 하네스 엔지니어링 관련성
- 하위 주제 태그: agent-loop, self-improvement(기타), model-harness co-evolution
- 왜 중요한가: 이 테마의 **model-harness 공진화 극단**. HarnessX가 트레이스를 "하네스+모델 신호"로 나눈 것을, SIA는 명시적으로 "하네스 업데이트 vs 가중치 업데이트" 두 레버로 정식화하고 결합 우위를 실증. "하네스가 모델을 에이전트답게 만들고, 가중치가 도메인 직관을 준다"는 분업 명제가 인용 가치 높음.

## 인용용 핵심 사실 (검증 대상)
- SIA는 Feedback-Agent가 하네스와 가중치를 둘 다 업데이트(harness-update ∪ weight-update 통합).
- SIA-W+H: LawBench +25.1%, GPU 커널 12.4% 빠름(1,017 vs 1,161μs), RNA 디노이징 +20.4% (모두 선행 SOTA 대비).
- "하네스 업데이트는 모델을 agentic하게, 가중치 업데이트는 도메인 직관을 형성"이라는 분업 명제.

---

# 2606.05922 — Evolving Agents in the Dark: Retrospective Harness Optimization via Self-Preference (RHO)

- 저자/기관: Wenbo Pan, Shujie Liu, Chin-Yew Lin, Jingying Zeng, Xianfeng Tang, Xiangyang Zhou (+2)
- 날짜: 2026-06-04
- URL: https://arxiv.org/abs/2606.05922
- 확인수준: 초록 (전문 미열람)

## 한 문장 요약
정답 검증셋 없이(self-supervised) 과거 궤적만으로 하네스를 최적화하는 RHO — 어려운 태스크 코어셋을 재풀이하고, 자기검증·자기일관성으로 후보 하네스 업데이트를 만들어 pairwise self-preference로 최선안을 선택.

## 문제 정의
기존 하네스 최적화는 대개 **ground-truth 검증셋**을 요구하지만, 실배포에서 라벨 데이터 확보는 어렵다("in the dark" — 정답 없이 진화해야 함).

## 핵심 방법
- **RHO (Retrospective Harness Optimization):** 과거 궤적만 사용하는 self-supervised 방법.
- 과거 궤적에서 다양하고 어려운 태스크의 코어셋(coreset)을 선택 → 병렬로 재풀이(re-solve).
- 롤아웃을 self-validation + self-consistency로 분석 → 후보 하네스 업데이트 생성 → **pairwise self-preference**로 가장 효과적인 것 선택.

## 주요 기여
1. 외부 채점/라벨 없이 하네스를 최적화하는 self-supervised 프레임워크(Self-Harness의 회귀검증셋 의존을 우회).
2. self-validation·self-consistency·self-preference 삼중 자기신호로 후보 선택.
3. 최적화가 과거 실패 모드를 실제로 겨냥함을 분석으로 입증.

## 실험 결과 (정량)
- 세 도메인(software engineering, technical work, knowledge work).
- **SWE-Bench Pro pass rate: 59% → 78% (단일 최적화 라운드, 외부 채점 없음)** (출처: 초록).
- 최적화된 하네스가 에이전트 행동 패턴을 바꾸고 장기 세션에서 더 높은 정확도 유지.

## 한계
- (분석자 판단) self-preference는 모델 자신의 선호에 의존 → 잘못된 선호가 정책으로 굳을 위험(QueenBee 2606.27492가 지적하는 "lucky run/plausible-but-false"). 초록은 이 위험의 방어 장치를 명시하지 않음.
- 단일 라운드 결과 위주 — 다중 라운드 안정성/발산 여부 미제시.
- 어려운 코어셋 선택 기준의 구체 알고리즘이 초록에 없음.

## 하네스 엔지니어링 관련성
- 하위 주제 태그: eval-harness, self-improvement(기타), agent-loop
- 왜 중요한가: Self-Harness의 최대 실용 장벽인 **"회귀검증에 라벨/검증셋이 필요하다"** 를 정면으로 제거. 배포 환경 자기개선의 핵심 난제(정답 없는 진화)를 self-preference로 푸는 대표 접근. SEAGym이 경계하는 "self-preference가 lucky run을 정책화" 문제의 반대편 사례.

## 인용용 핵심 사실 (검증 대상)
- RHO는 정답 검증셋 없이 과거 궤적만으로 하네스를 최적화(self-supervised).
- 단일 최적화 라운드로 SWE-Bench Pro pass rate 59%→78%, 외부 채점 전혀 없음.
- self-validation + self-consistency로 후보 생성, pairwise self-preference로 선택.

---

# 2606.13643 — Recursive Agent Harnesses (RAH)

- 저자/기관: Elias Lumer, Sahil Sen, Kevin Paul, Vamse Kumar Subbiah
- 날짜: 2026-06-11
- URL: https://arxiv.org/abs/2606.13643
- 확인수준: 초록 (전문 미열람)

## 한 문장 요약
재귀의 단위를 "툴 없는 모델 호출"이 아니라 "파일시스템·코드실행·플래닝을 갖춘 완전한 에이전트 하네스"로 놓는 패턴(RAH)을 명명·연구 — 부모 에이전트가 실행 스크립트를 생성해 서브에이전트 하네스를 병렬 스폰.

## 문제 정의
RLM(재귀 언어모델)은 모델 호출의 재귀로 긴 컨텍스트 추론을 개선했고, 프로덕션 코딩 에이전트는 대규모로 서브에이전트를 스폰하기 시작했다(Anthropic dynamic workflows). 이 둘 사이의 패턴 — 재귀 단위가 "완전한 하네스"인 경우 — 이 명명·연구되지 않았다.

## 핵심 방법
- **RAH (Recursive Agent Harness):** RLM의 "모델 재귀"에 대한 code-first 확장인 "하네스 재귀(harness recursion)".
- 부모 에이전트가 실행가능 스크립트를 생성·실행 → 세밀한 워크로드에 대해 서브에이전트 하네스를 **병렬 스폰**, 작은 서브태스크엔 구조화된 함수 호출 사용.
- 백본 고정 통제 평가(Codex/RLM baseline과 매칭).

## 주요 기여
1. "하네스 재귀"라는 패턴의 명명·정식화(모델 재귀 RLM의 code-first 확장).
2. 백본 고정 통제 실험으로 개선이 **모델이 아니라 하네스에 기인**함을 분리 입증.

## 실험 결과 (정량)
- 백본 GPT-5 고정, Oolong-Synthetic(199 샘플, 최대 4M 토큰 13개 컨텍스트 버킷):
  - **Codex 코딩에이전트 baseline 71.75% → RAH 81.36%** — 모델이 아닌 하네스에 기인.
- 더 강한 백본 Claude Sonnet 4.5: 동일 설계로 **89.77%** 도달.

## 한계
- (분석자 판단) 자기개선/진화 루프 자체는 아님 — RAH는 "재귀적 구조로 하네스를 조직"하는 설계 패턴. 이 테마 내에서는 "진화"보다 "구조적 스캐폴딩"에 가까움(테마 경계 사례).
- 평가가 장기 컨텍스트 추론(Oolong-Synthetic) 중심 — 일반 SWE/터미널 태스크 일반화는 미검증.

## 하네스 엔지니어링 관련성
- 하위 주제 태그: agent-loop, multi-agent, context-engineering, tool-orchestration
- 왜 중요한가: 개선폭이 "모델이 아닌 하네스에 기인"함을 백본 고정으로 깔끔히 분리 입증 → **하네스 엔지니어링의 인과 기여를 정량화**한 강한 증거. 서브에이전트 병렬 스폰(dynamic workflows)을 "재귀 하네스"로 정식화. ClawArena-Team·Recursive 계열과 연결.

## 인용용 핵심 사실 (검증 대상)
- RAH는 재귀 단위가 "완전한 에이전트 하네스"(파일시스템·코드실행·플래닝)이며 서브에이전트를 병렬 스폰.
- GPT-5 고정: Oolong-Synthetic에서 Codex 71.75% → RAH 81.36% (개선은 모델 아닌 하네스 기인).
- Claude Sonnet 4.5 백본: 동일 설계 89.77%.

---

# 2606.17546 — SEAGym: 자기진화 LLM 에이전트를 위한 평가 환경

- 저자/기관: Congjie Zheng, Chuanyi Xue, Bin Liang, Jun Yang, Changshui Zhang
- 날짜: 2026-06-16
- URL: https://arxiv.org/abs/2606.17546
- 확인수준: 초록 (전문 미열람)

## 한 문장 요약
자기진화 에이전트의 하네스 업데이트를 train/validation/test/replay/cost 다중 뷰로 측정하는 평가 환경 — "업데이트가 재사용 가능한 개선인가, 최근 태스크에 과적합했나, 비용이 늘었나, 과거 행동을 해쳤나"를 분리.

## 문제 정의
자기진화 에이전트는 주로 하네스(프롬프트·메모리·툴·미들웨어·런타임 상태·모델-툴 루프)를 바꿔 개선한다. 그러나 기존 평가는 이를 고립 태스크 점수나 단일 순차 곡선으로 환원해, 업데이트가 재사용 가능 개선인지/과적합인지/비용 증가인지/과거 행동 손상인지를 구분 못 한다.

## 핵심 방법
- **SEAGym:** Harbor-호환 벤치마크를 동적 자기진화 태스크 소스로 변환. train 배치, frozen update-validation, held-out ID/OOD transfer 뷰, replay diagnostics, snapshot·metric 기록 저장.
- Terminal-Bench 2.0·HLE에 인스턴스화, 공유 epoch/batch 프로토콜로 **ACE·TF-GRPO·AHE** 비교.

## 주요 기여
1. 자기진화 하네스 업데이트를 5개 뷰(training/validation/test/replay/cost)로 측정하는 표준 평가 환경.
2. held-out ID/OOD transfer, replay diagnostics로 과적합·붕괴·비용 증가를 드러냄.
3. 세 자기진화 방법(ACE/TF-GRPO/AHE) 공정 비교 프로토콜.

## 실험 결과 (정량)
- 초록은 구체 점수보다 **정성 발견**을 강조 (출처: 초록):
  - 잦은 업데이트가 held-out 성능 개선에 실패할 수 있음.
  - 유용해 보이던 중간 스냅샷이 나중에 붕괴(collapse)할 수 있음.
  - 소스 다양성·모델 백엔드가 하네스 신뢰성에 영향.
- (주의) 수치 벤치마크 비교표는 초록 미제시.

## 한계
- (분석자 판단) 정량 리더보드가 아니라 "평가 방법론/뷰" 제안 — 절대 성능 주장 부재. 어떤 방법이 이기는지의 결론보다 "평가가 놓치는 것"을 드러내는 데 초점.
- Harbor 호환/Terminal-Bench·HLE 두 벤치에 국한.

## 하네스 엔지니어링 관련성
- 하위 주제 태그: eval-harness, self-improvement(기타)
- 왜 중요한가: 이 테마의 **메타-평가 인프라.** Self-Harness/APEX/RHO 등이 "개선했다"고 주장하는 것을 **어떻게 신뢰성 있게 측정하나**를 다룸. 특히 "중간 스냅샷 붕괴", "잦은 업데이트가 held-out 개선 실패", "self-preference의 과적합 위험"을 노출 — RHO의 self-preference·Self-Harness의 회귀검증이 놓칠 수 있는 실패를 드러내는 대응물. AHE를 비교 대상에 포함.

## 인용용 핵심 사실 (검증 대상)
- SEAGym은 하네스 업데이트를 train/validation/test/replay/cost 다중 뷰로 측정, held-out ID/OOD transfer 포함.
- Terminal-Bench 2.0·HLE에서 ACE·TF-GRPO·AHE를 공유 프로토콜로 비교.
- 발견: 잦은 업데이트가 held-out 개선에 실패 가능, 중간 스냅샷이 나중에 붕괴 가능.

---

# 2606.26859 — AgentX: 산업용 추천시스템의 에이전트 주도 자기반복

- 저자/기관: Changxin Lao, Fei Pan, Guozhuang Ma, Han Li, Huihuang Lin, Jijun Shi (+56)
- 날짜: 2026-06-25
- URL: https://arxiv.org/abs/2606.26859
- 확인수준: 초록 (전문 미열람)

## 한 문장 요약
추천 알고리즘 반복의 idea→launch 사이클을 자율화하는 프로덕션 멀티에이전트 시스템 — 4단계 폐루프(Brainstorm/Developing/Evaluation Agent) 위에 "Harness Evolution 레이어(SGPO)"가 실행 궤적을 semantic-gradient 업데이트로 증류해 에이전트 자신을 지속 개선.

## 문제 정의
추천 알고리즘 반복이 산업화 연구 루프로 이행 중이나, idea-to-launch 사이클이 여전히 인간 엔지니어(가설 생성·프로덕션 코드 수정·A/B 실행·결과 귀속)에 의존 → 혁신이 인력에 선형 비례, 증거·컴퓨트·누적경험으로 복리 성장하지 못함.

## 핵심 방법
- 4단계 폐루프:
  - **Brainstorm Agent:** 과거 실험·아키텍처·데이터 분석·외부 연구를 종합해 순위화된 실행가능 제안.
  - **Developing Agent:** 제안을 repo-grounded 생성 + 다차원 신뢰성 검증으로 프로덕션 코드로 번역.
  - **Evaluation Agent:** guardrail-vetoed A/B 판정으로 안전 온라인 롤아웃, 성공·실패를 구조화 지식 자산으로 전환.
- **Harness Evolution 레이어 (SGPO):** 실행 궤적을 semantic-gradient 업데이트로 증류해 에이전트 자신을 지속적으로 sharpen — "자동화를 넘어 자기개선."

## 주요 기여
1. 추천 반복 전 과정(가설→구현→평가→학습)을 자율화한 프로덕션 self-evolving 개발 엔진.
2. 성공/실패를 모두 구조화 지식 자산으로 전환하는 폐루프.
3. 실행 궤적→semantic-gradient(SGPO)로 에이전트를 지속 개선하는 Harness Evolution 레이어.

## 실험 결과 (정량)
- (주의) 이 초록은 정량 결과 수치를 명시하지 않음(시스템 아키텍처·능력 서술 중심). 정량 인용 불가.

## 한계
- (분석자 판단) 초록에 벤치마크 점수/A/B 개선폭 부재 → 효과 크기 검증 불가. 프로덕션 시스템 특성상 재현·독립검증 어려움.
- SGPO의 semantic-gradient 정의가 초록만으로는 불명확.
- 저자 60여 명 대규모 산업 리포트 → 방법 일반화보다 특정 배포 최적화 가능성.

## 하네스 엔지니어링 관련성
- 하위 주제 태그: multi-agent, self-improvement(기타), tool-orchestration
- 왜 중요한가: 자기개선 하네스를 **산업 추천시스템이라는 실배포 도메인**에 적용, "Harness Evolution 레이어"를 명시적 아키텍처 구성요소로 둠. NOVA(2606.27243, verification-aware architecture evolution)와 함께 산업 추천 도메인의 자기진화 하네스 계보. AgentX의 SGPO는 semantic-gradient라는 점에서 NOVA의 "architecture gradient"와 개념 대응.

## 인용용 핵심 사실 (검증 대상)
- AgentX는 Brainstorm/Developing/Evaluation 3에이전트 폐루프 + Harness Evolution 레이어(SGPO).
- SGPO는 실행 궤적을 semantic-gradient 업데이트로 증류해 에이전트를 지속 개선.
- (주의) 초록에 정량 성능 수치 없음 — 효과 크기 인용 시 본문 확인 필요.

---

# 2606.07412 — Socratic-SWE: 트레이스 유도 에이전트 스킬로 자기진화하는 코딩 에이전트

- 저자/기관: Chuan Xiao, Zhengbo Jiao, Shaobo Wang, Wei Wang, Bing Zhao, Hu Wei (+2)
- 날짜: 2026-06-05
- URL: https://arxiv.org/abs/2606.07412
- 확인수준: 초록 (전문 미열람)

## 한 문장 요약
에이전트의 과거 풀이 트레이스를 구조화된 "에이전트 스킬"(반복 실패·효과적 수리 패턴 요약)로 증류하고, 이 스킬로 실제 레포에서 타깃 수리 태스크를 생성해 커리큘럼을 자기진화시키는 폐루프.

## 문제 정의
SWE 에이전트 학습은 고품질 SWE 태스크 부족에 제약된다. 기존 합성데이터는 고정 mutation/bug-injection이라 에이전트 자신의 약점·학습 진행과 독립적인 분포를 만든다.

## 핵심 방법
- **Socratic-SWE (폐루프 자기진화):** 과거 풀이 트레이스를 보상 계산 증거로만 쓰지 않고, **구조화된 agent skills**(반복 실패 + 효과적 수리 패턴 요약)로 증류.
- 이 스킬이 실제 레포에서 타깃 수리 태스크 생성을 유도.
- 후보 태스크를 execution-based validation으로 검증 + solver-gradient alignment reward로 채점 → 검증가능하고 유용한 태스크만 유지.
- 업데이트된 Solver가 새 트레이스 생성 → 커리큘럼이 라운드마다 적응.

## 주요 기여
1. 풀이 트레이스를 "에이전트 스킬"로 증류해 태스크 커리큘럼을 에이전트 약점에 맞춰 진화(Self-Harness의 weakness-mining을 학습데이터 생성으로 확장).
2. execution 검증 + solver-gradient alignment로 유용·검증가능 태스크만 유지.
3. 동일 컴퓨트 예산에서 자기진화 baseline을 일관 상회.

## 실험 결과 (정량)
- SWE-bench Verified/Lite/Pro, Terminal-Bench 2.0에서 동일 컴퓨트 예산 하 자기진화 baseline 일관 상회 (출처: 초록).
- **SWE-bench Verified: 3회 반복 후 50.40%** 도달.

## 한계
- (저자 함의) 개선이 커리큘럼 생성 품질 및 execution-based validation의 커버리지에 의존.
- (분석자 판단) SWE-bench Verified 50.40%는 프론티어 에이전트(예: icat-agent 67.4% on Pro 등) 대비 절대 성능은 중간대 — "동일 컴퓨트 예산 baseline 대비" 상대 우위 주장.
- solver-gradient alignment reward의 구체 정의가 초록에 없음.

## 하네스 엔지니어링 관련성
- 하위 주제 태그: self-improvement(기타), eval-harness, agent-loop
- 왜 중요한가: 자기개선의 대상을 "하네스" 자체가 아니라 **학습 커리큘럼(태스크 분포)** 으로 옮긴 사례 — 트레이스에서 "에이전트 스킬"을 증류한다는 점은 APEX의 L2(성공-트레이스 증류)·Swarm Skills의 스킬 진화와 개념 공유. "트레이스가 자기진화의 확장가능한 substrate"라는 명제.

## 인용용 핵심 사실 (검증 대상)
- Socratic-SWE는 과거 풀이 트레이스를 구조화된 agent skills로 증류해 타깃 수리 태스크를 생성.
- execution-based validation + solver-gradient alignment reward로 태스크 유지 여부 결정.
- SWE-bench Verified에서 3회 반복 후 50.40% 도달, 동일 컴퓨트 예산 자기진화 baseline 일관 상회.

---

# 공통 관점 (Cross-cutting Synthesis)

## 1. 계보: Self-Harness가 뿌리, 나머지는 축의 확장
- **2606.09498 Self-Harness가 이 테마의 baseline/앵커.** 3단계 루프(진단→제안→검증)가 원형.
- **최적화 대상(action space) 확장:**
  - APEX(2606.15363)는 Self-Harness가 "프롬프트 하네스 단일축"만 본다고 **명시적으로 비판**하고 L1(하네스)+L2(원칙)+L3(토폴로지) 3계층으로 확장. (Self-Harness→APEX가 가장 직접적인 계승 관계)
  - HarnessX(2606.14249)는 하네스를 타입화 프리미티브의 **치환 대수**로 형식화하고 진화 엔진(AEGIS)+모델 공학습을 결합한 "파운드리"로 격상.
  - Socratic-SWE(2606.07412)는 대상을 하네스가 아닌 **학습 커리큘럼**으로 이동(트레이스→스킬→태스크).

## 2. "검증셋 없이 진화"라는 실용 병목과 두 갈래 해법
- Self-Harness는 회귀검증에 **held-out/라벨**을 요구 → 배포 적용 병목.
- **RHO(2606.05922)** 는 라벨 없이 과거 궤적 + self-validation/self-consistency/**self-preference**로 우회(SWE-Bench Pro 59→78%, 외부 채점 0).
- 그러나 **SEAGym(2606.17546)** 은 정확히 이런 self-* 신호가 "lucky run 과적합·중간 스냅샷 붕괴"를 낳을 수 있음을 메타-평가로 노출 → RHO류의 낙관에 대한 견제. (이 테마 밖 QueenBee 2606.27492도 같은 우려를 acceptance gate로 방어)

## 3. 진단(어디를 왜)의 부상
- 초기 자기개선은 "최종 결과 기반"이라 **넓고 범위 불분명한 수정**을 낳음.
- **HarnessFix(2606.06324)** 는 HTIR로 실패를 **트레이스 스텝 × 하네스 계층(ETCLOVG 추정)** 에 이중 귀속시켜 범위 한정 수리로 전환 — 자기개선 계열의 "진단 인프라". (테마 밖 AHE 2604.25850의 observability 3필러와 짝)

## 4. 하네스 vs 가중치: 공진화의 스펙트럼
- **순수 하네스 진화:** Self-Harness, APEX, RHO, HarnessFix, Socratic-SWE(커리큘럼).
- **하네스 + 모델 공학습:** HarnessX(트레이스→하네스+모델 신호), Continual Harness(온라인 process-reward co-learning), **SIA(2605.27276)** — 하네스와 가중치를 **둘 다** Feedback-Agent가 업데이트(결합이 스캐폴드 단독 능가). SIA의 분업 명제("하네스=agentic하게, 가중치=도메인 직관")가 이 스펙트럼의 정식화.

## 5. 온라인/리셋-프리 vs 오프라인 라운드
- 대부분(Self-Harness/APEX/RHO/Socratic-SWE)은 **오프라인 라운드**(재풀이·회귀검증·반복).
- **Continual Harness(2605.09998)** 는 에피소드 **리셋 없이 단일 런 내 온라인 적응** — 임베디드/부분관측 도메인(Pokemon)으로 확장. 프롬프트 최적화의 리셋 전제를 깬다.

## 6. 도메인 확장
- 코딩/터미널(Self-Harness, HarnessFix, Socratic-SWE, RHO) → 임베디드 게임(Continual Harness) → 산업 추천시스템(**AgentX 2606.26859**, "Harness Evolution 레이어" SGPO; 테마 밖 NOVA 2606.27243의 "architecture gradient"와 대응) → 이질 과학 도메인(SIA: 법률/GPU/RNA).

## 7. 인과 분리 증거
- **RAH(2606.13643)** 는 백본 고정 통제로 개선이 "모델이 아니라 하네스에 기인"(Codex 71.75→81.36%)함을 깔끔히 분리 — 이 테마 전체가 기대는 "하네스가 성능의 독립 레버"라는 명제의 강한 증거. (단 RAH 자체는 진화 루프라기보다 재귀적 구조 설계 → 테마 경계 사례로 표기)

## 8. 정직성 메모 (검증자용)
- **초록에 정량 없음:** AgentX(2606.26859)는 초록에 성능 수치 부재 → 효과 크기 인용 금지.
- **정성 위주:** Continual Harness·SEAGym은 초록에 %/절대수 대신 정성 서술 → 구체 수치 인용 주의.
- **자체 정의 지표:** APEX "Health Score", SEAGym 다중 뷰는 표준 벤치마크 점수가 아님 → 타 논문과 직접 비교 불가.
- **미정의 약어:** HarnessFix의 ETCLOVG는 초록에 정의 없음(E-T-C-L-O-V-G 추정) → 인용 시 "추정" 표기.
- **미공개:** HarnessX 코드 "future release", 앵커 4편 본문은 arXiv 초록페이지에서 미열람.

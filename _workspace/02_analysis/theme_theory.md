# 테마: 하네스 정의 · 이론 · 택소노미 (Harness Definition, Theory & Taxonomy)

이 테마는 "에이전트 하네스란 무엇인가"를 정면으로 다루는 이론·정의·분류 계열 논문을 묶는다. 다른 테마(컨텍스트 관리, 툴 오케스트레이션, 자기진화 등)가 하네스의 **부분 기능**을 개선하는 데 비해, 이 테마의 논문들은 **하네스라는 개념 자체를 정의·형식화·분류**하려 한다. 핵심 질문은 세 가지다: (1) 무엇을 하네스라 부를 수 있고 무엇은 아닌가(정의·경계), (2) 하네스를 어떤 구성 책임/축으로 분해할 수 있는가(택소노미), (3) 성능 병목이 모델에 있는가 하네스에 있는가 그 결합에 있는가(이론적 위치 규정).

> **근거자료 주의:** 모든 분석은 `_workspace/02_analysis/abstracts.md`의 arXiv API 검증 초록을 1차 근거로 한다. 앵커 논문 2건(2606.10106, 2606.20683)은 arXiv 페이지를 추가 WebFetch했으나, **2606.10106의 전문 PDF fetch 결과는 모델이 초록을 재구성·패러프레이즈한 것으로 판단되어 verbatim 신뢰 불가** — 해당 논문의 "구체 조건 목록"은 초록에서 확인 가능한 범위로 제한하고 그 사실을 명시한다.

---

## 2606.10106 — What makes a harness a harness: necessary and sufficient conditions for an agent harness

- 저자/기관: Sanderson Oliveira de Macedo
- 날짜: 2026-06-08
- URL: https://arxiv.org/abs/2606.10106
- 확인수준: **초록만** (전문 PDF WebFetch를 시도했으나 반환 내용이 초록의 재구성으로 판단되어 verbatim 신뢰 불가 → 초록에서 명시적으로 확인되는 사실만 사용)

### 한 문장 요약
"agent harness"라는 널리 쓰이지만 다의적으로 남용되는 용어에 대해, 포함/배제를 일관되게 판정하는 **도구로서의 참조 정의**(필요·충분조건)를 개념 분석으로 구축한다.

### 문제 정의
"agent harness"는 (a) 제품 전체(Claude Code, Codex CLI), (b) 에이전트를 태스크에 돌리는 평가 스캐폴드(SWE-bench harness), (c) agent framework·SDK·IDE 플러그인·orchestrator 등과 혼용된다. 개념이 느슨하고 다의적(loose and polysemous)이어서, 사례를 일관되게 포함·배제하는 **기준 정의(reference definition)가 부재**하다. 이 부재가 엔지니어링 실무와 에이전트 시스템의 과학적 비교를 모두 저해한다.

### 핵심 방법
- **개념 분석(conceptual analysis):** 영속 식별자를 가진 문헌 + 1차 회색문헌(공식 문서, 용어집, 엔지니어링 리포트)을 결합.
- **계보 재구성(genealogy):** 말의 마구(horse's tack) → 고전적 테스트 하네스(test harness) → 머신러닝 평가 하네스(ML evaluation harness) → 에이전트 하네스(agent harness)로 이어지는 용어의 진화 추적.
- **구성적 정의(constitutive definition):** 시스템이 에이전트 하네스이기 위한 **필요·충분조건**을 진술하고, 이를 **포함/배제 테스트(inclusion and exclusion test)**로 조작화.
- **경계 긋기:** agent framework / agent SDK / IDE plugin / eval harness / orchestrator 다섯 인접 개념 각각에 대해 하네스와의 경계를 명시.
- **적용 검증:** 실제 하네스 6종 + 의도적 경계 사례(edge cases)에 정의를 적용해 포함/배제가 일관됨을 보임.

### 주요 기여
1. 에이전트 하네스의 **운영적 정의(operational definition)** — 공유 어휘를 제공해 실무 가이드와 과학적 비교 모두를 가능케 함.
2. **포함/배제 테스트**라는 판정 도구화 — 정의가 사례를 일관되게 include/exclude 함을 실증.
3. 인접 5개 개념(framework/SDK/IDE plugin/eval harness/orchestrator)과의 **경계 정립**.
4. **설계 긴장 축(design tension axes)**으로 조직된 연구 어젠다 제시.

### 실험 결과 (정량)
- 본 논문은 개념 분석 논문으로 벤치마크 수치가 없다.
- 정성 결과: 실제 하네스 **6종(Claude Code, Codex CLI, Aider, Cline, OpenHands, SWE-agent)**과 의도적 경계 사례에 정의를 적용했을 때 **포함/배제가 일관되게(consistently) 작동**했다고 초록이 명시. (출처: 초록)

### 한계
- (저자 명시) 정의는 개념 분석과 회색문헌 기반 — 경험적/양적 검증이 아니라 **정합성(consistency) 논증**에 의존.
- (분석자 판단) 급변하는 하네스 관행에 대해 정의가 얼마나 오래 안정적일지 불명. 새 형태(예: OS-레벨 하네스, 멀티유저 하네스)가 나올 때 경계가 재협상될 가능성.
- (분석자 판단) **구체적 필요·충분조건의 verbatim 목록은 초록에 없음** — 정의의 실제 문항은 전문 확인 필요(현 확인수준: 초록만). 리포트에서 "조건 N개"라 단정하지 말 것.

### 하네스 엔지니어링 관련성
- 하위 주제 태그: **definition / taxonomy** (theory 앵커)
- 왜 중요한가: 이 서베이 전체의 **개념적 기준점**. "하네스 vs framework vs SDK vs eval harness vs orchestrator" 경계는 다른 모든 논문을 분류할 때 재사용할 어휘를 제공한다. 서베이의 택소노미 절 서두에 이 정의를 앵커로 놓기 적합.

### 인용용 핵심 사실 (검증 대상)
- 논문은 에이전트 하네스에 대한 **필요·충분조건을 진술하는 구성적 정의**를 제안하고, 이를 **포함/배제 테스트로 조작화**한다. (초록)
- 정의는 실제 하네스 **6종(Claude Code, Codex CLI, Aider, Cline, OpenHands, SWE-agent)**과 의도적 경계 사례에 적용되어 **일관되게 포함·배제**했다. (초록)
- 하네스 용어의 계보를 **말의 마구 → 테스트 하네스 → ML 평가 하네스 → 에이전트 하네스**로 재구성한다. (초록)
- agent framework, agent SDK, IDE plugin, eval harness, orchestrator **다섯 인접 개념과의 경계**를 명시적으로 긋는다. (초록)
- 연구 어젠다를 **설계 긴장 축(design tension axes)**으로 조직한다. (초록) — 구체 축 명칭은 초록에서 미확인.

---

## 2606.20683 — From Question Answering to Task Completion: A Survey on Agent System and Harness Design

- 저자/기관: Jianyuan Guo, Zhiwei Hao, Chengcheng Wang, Cheng Fan, Tingzhang Luo, Hongguang Li 외 (+11)
- 날짜: 2026-06-14
- URL: https://arxiv.org/abs/2606.20683 · 논문 모음: https://github.com/ggjy/Awesome-Agent-Engineering
- 확인수준: **초록 + arXiv 페이지 보강** (6책임 분해와 4패러다임을 페이지에서 재확인)

### 한 문장 요약
LLM 에이전트를 **"foundation model + execution harness"**의 결합으로 보는 model-harness 렌즈를 세우고, 실행 하네스를 **6개의 결합된 런타임 책임(observation·context·control·action·state·verification)**으로 분해해 서베이한다.

### 문제 정의
에이전트는 수동적 질의응답(QA)에서 능동적 태스크 완수(task completion)로 이동했다 — 환경을 지각하고, 툴을 호출하고, 상태를 유지하며, 장기 horizon에 걸쳐 행동한다. 이때 **중심 질문**: 에이전트 성능의 병목이 (i) foundation model에 있는가, (ii) execution harness에 있는가, (iii) 둘의 **결합(coupling)**에 있는가? 기존 관점은 에이전트를 "보조 툴을 단 모델"로 취급해 이 질문을 흐린다.

### 핵심 방법 (model-harness lens)
- **에이전트의 함수적 정의 + 구현 관점 정립:** LLM 에이전트 = foundation model ⊗ execution harness.
- **모델 중심 스케일링의 한계 분석** 후, 에이전트 엔지니어링의 **4개 패러다임** 추적:
  prompt engineering → workflows & context engineering → **harness engineering** → agent-native training with co-evolution.
- **실행 하네스를 6개 결합 런타임 책임으로 분해:**
  1. **Observation** — 환경 입력을 어떻게 지각/수용하는가
  2. **Context** — 정보 상태·이력을 어떻게 구성·관리하는가
  3. **Control** — 의사결정 흐름/제어를 어떻게 조직하는가
  4. **Action** — 툴 호출·개입을 어떻게 실행하는가
  5. **State** — 지속 상태/메모리를 어떻게 유지하는가
  6. **Verification** — 태스크 완료·정확성을 어떻게 검증하는가
- 이 분해로 **task properties·domain pressures → harness configurations** 매핑을 수행하고, 벤치마크·평가 관행을 리뷰하며, 런타임 설계가 장기 horizon 완수·효율·신뢰성에 미치는 model-harness 증거를 종합.

### 주요 기여
1. **model-harness 렌즈** — 에이전트 품질을 "모델 능력 × 런타임 인프라 × 태스크 구조 × 평가 설계"의 상호작용으로 재정의.
2. **6-책임 하네스 분해**(observation/context/control/action/state/verification) — 서베이 전반의 분류 축.
3. 에이전트 엔지니어링 **4패러다임 계보** 정립(프롬프트→워크플로/컨텍스트→하네스→에이전트-네이티브 공진화).
4. **미해결 도전 4종** 식별: value-aware evaluation, safety, harness generalization, model-harness co-evolution.

### 실험 결과 (정량)
- 서베이 논문 — 자체 벤치마크 수치 없음. 여러 시스템의 model-harness 증거를 **종합·정리**하는 형태.

### 한계
- (저자 함의) 병목의 위치를 단일 답으로 규정하지 않음 — "상호작용에서 창발"한다는 결론은 실무자에게 처방적 지침으로는 약함.
- (분석자 판단) 6-책임 분해는 유용하나 책임 간 **경계·중첩**(예: context vs state, control vs action)이 초록 수준에서 흐릿함. 다른 분류(2605.13357의 11책임, 2606.06324의 ETCLOVG 계층)와 **정렬/대조**가 서베이 종합에서 필요.

### 하네스 엔지니어링 관련성
- 하위 주제 태그: **taxonomy / definition** (theory 앵커, 6-책임 프레임워크)
- 왜 중요한가: 이 서베이의 **분류 골격**으로 삼기 가장 적합한 6축 어휘를 제공. 다른 테마 논문(컨텍스트=context, 툴=action, 메모리=state, 평가=verification 등)을 이 6축에 매핑하면 종합이 깔끔해진다.

### 인용용 핵심 사실 (검증 대상)
- LLM 에이전트를 **foundation model + execution harness**의 결합으로 정의하는 **model-harness 렌즈**를 제시. (초록)
- 실행 하네스를 **6개의 결합 런타임 책임: observation, context, control, action, state, verification**으로 분해. (초록)
- 에이전트 엔지니어링의 **4패러다임**: prompt engineering → workflows/context engineering → harness engineering → agent-native training with co-evolution. (초록)
- 미해결 도전 4종: **value-aware evaluation, safety, harness generalization, model-harness co-evolution.** (초록)
- 중심 질문: 성능 병목이 **model / harness / coupling** 중 어디에 있는가. (초록)

---

## 2605.13357 — AI Harness Engineering: A Runtime Substrate for Foundation-Model Software Agents

- 저자/기관: Hailin Zhong, Shengxin Zhu
- 날짜: 2026-05-13
- URL: https://arxiv.org/abs/2605.13357
- 확인수준: **초록만** (초록이 11책임·H0–H3 사다리를 구체적으로 열거하고 있어 충분)

### 한 문장 요약
소프트웨어 엔지니어링 능력은 모델 단독이 아니라 **model-harness-environment 시스템**에서 창발한다고 보고, 하네스를 **런타임 기질(runtime substrate)**로 형식화해 **11개 구성 책임**과 **4단계 사다리(H0–H3)**, 그리고 **트레이스 기반 평가 프로토콜**을 제안한다.

### 문제 정의
자율 SWE 에이전트가 현실적 개발 환경에서 여전히 불안정하다. 지배적 설명은 이를 **모델 능력** 탓으로 돌린다. 저자는 병목의 위치(locus)를 다르게 잡는다 — 능력은 모델·하네스·환경의 **시스템**에서 나오며, 그 중 런타임 기질인 **하네스**가 에이전트가 프로젝트를 관찰·행동·피드백 수용·완료 확정하는 방식을 매개한다.

### 핵심 방법
- 하네스를 **AI Harness Engineering**이라는 런타임 기질로 형식화하고 **11개 구성 책임** 식별:
  1. task specification (태스크 명세)
  2. context selection (컨텍스트 선택)
  3. tool access (툴 접근)
  4. project memory (프로젝트 메모리)
  5. task state (태스크 상태)
  6. observability (관측성)
  7. failure attribution (실패 귀인)
  8. verification (검증)
  9. permissions (권한)
  10. entropy auditing (엔트로피 감사)
  11. intervention recording (개입 기록)
- **4단계 사다리 H0–H3:** 런타임 지원을 에이전트에게 점진적으로 노출하는 수준. 낮은 레벨은 최종 patch만, 높은 레벨은 재현 로그·실패 귀인·결정적 요구사항 체크·구조화된 검증 리포트를 산출.
- **트레이스 기반 평가 프로토콜:** 각 에이전트 실행을 **감사 가능한 에피소드 패키지(auditable episode package)**로 변환.

### 주요 기여
1. SWE 능력의 **locus를 모델에서 model-harness-environment 시스템으로 재배치**.
2. 하네스의 **11책임** 상세 목록(2606.20683의 6책임보다 세분화된 대안 분류).
3. **H0–H3 사다리** — 하네스 성숙도를 단계적으로 조작화.
4. **에피소드 패키지** 기반 트레이스 평가 — 산출 증거 구조가 하네스 레벨에 따라 체계적으로 변함을 보임.

### 실험 결과 (정량)
- 정량 벤치마크 점수는 초록에 없음(개념·프레임워크 논문). 대신 **통제된 검증 태스크**에 적용해, 에피소드 패키지의 **증거 구조가 하네스 레벨(H0–H3)에 따라 체계적으로 변한다**는 정성 결과 제시 — 낮은 레벨=최종 patch만, 높은 레벨=재현 로그+실패 귀인+결정적 요구사항 체크+구조화 검증 리포트. (출처: 초록)

### 한계
- (저자 함의) "통제된 검증 태스크"(controlled validation task) 단일 — 일반화 근거 약함.
- (분석자 판단) 11책임이 6책임(2606.20683)·ETCLOVG(2606.06324) 등과 **어떻게 대응**되는지 미제시. 책임 개수 인플레이션의 위험(분류마다 6~11개로 제각각).
- (분석자 판단) H0–H3 사다리의 레벨 경계 기준이 초록 수준에서 정성적.

### 하네스 엔지니어링 관련성
- 하위 주제 태그: **taxonomy / eval-harness / agent-loop**
- 왜 중요한가: "하네스=런타임 기질"이라는 명제를 가장 명료히 밀어붙인 논문. **H0–H3 성숙도 사다리**와 **11책임**은 서베이의 "하네스를 어떻게 계층화/분해하는가" 절에 직접 쓸 수 있다. 평가를 최종 patch가 아니라 **감사 가능 에피소드**로 재정의한 점은 eval-harness 테마와 교차.

### 인용용 핵심 사실 (검증 대상)
- 하네스를 **11개 구성 책임**으로 식별: task specification, context selection, tool access, project memory, task state, observability, failure attribution, verification, permissions, entropy auditing, intervention recording. (초록)
- 하네스를 **4단계 사다리 H0–H3**로 조작화하며, 레벨이 높을수록 재현 로그·실패 귀인·결정적 요구사항 체크·구조화 검증 리포트를 산출. (초록)
- SWE 능력의 locus를 **model-harness-environment 시스템**으로 재규정. (초록)
- 각 에이전트 실행을 **감사 가능한 에피소드 패키지**로 변환하는 트레이스 기반 평가 프로토콜 제안. (초록)

---

## 2605.12239 — Harness Engineering as Categorical Architecture

- 저자/기관: Bogdan Banu
- 날짜: 2026-05-12
- URL: https://arxiv.org/abs/2605.12239
- 확인수준: **초록만**

### 한 문장 요약
하네스 설계에 형식 이론이 없다는 문제를 지적하고, **ArchAgents 프레임워크의 범주론적 Architecture 삼중항 (G, Know, Phi)**가 하네스 엔지니어링의 형식 이론을 정확히 제공한다고 주장·검증한다.

### 문제 정의
에이전트 하네스(prompts·tools·memory·orchestration logic를 감싸는 시스템 계층)는 LLM 에이전트의 중심 엔지니어링 추상이 되었으나, 설계가 **ad hoc**하다. 합성(composition), 컴파일 하의 속성 보존, 프레임워크 간 체계적 비교를 지배하는 **형식 이론이 없다.**

### 핵심 방법
- **범주론적 Architecture 삼중항 (G, Know, Phi)**를 하네스 형식화에 매핑:
  - 에이전트 외부화의 4기둥(Memory, Skills, Protocols, Harness Engineering)을 삼중항 요소에 대응 — Memory=coalgebraic state, Skills=operad-composed objects, Protocols=syntactic wiring G, 전체 Harness=Architecture 자체.
  - 구조적 보증(integrity gates, quality-based escalation, supported convergence checks)을 **Know-레벨 인증서(certificates)**로 규정하고, 보존을 **구조적 재생(structural replay)**으로 정의 — 컴파일러가 identity와 verifier replay를 확인(출력 정합성이나 모델 행동이 아니라).
- **레퍼런스 구현:** Swarms, DeerFlow, Ralph, Scion, LangGraph를 타깃으로 하는 **컴파일러 펑터(functor)** 제시. 4개 구성 컴파일러가 3개 명명 인증서 타입을 identity 또는 replay로 보존.
- 실제 LLM 에이전트로 end-to-end escalation 실험 — quality-based escalation 제어 경로가 model-parametric임을 (2모델·1태스크 실험에서) 확인.

### 주요 기여
1. 하네스 엔지니어링에 **형식 이론(범주론적 아키텍처)**을 부여.
2. 4기둥(Memory/Skills/Protocols/Harness)의 삼중항 매핑.
3. **인증서 보존 = 구조적 재생**이라는 컴파일 정합성 개념.
4. 5개 프레임워크 타깃 컴파일러 레퍼런스 구현.

### 실험 결과 (정량)
- 정량 성능 벤치마크가 아님. 검증은 **정성/구조적**: 4개 구성 컴파일러가 **3개 명명 인증서 타입을 identity 또는 replay로 보존**, LangGraph도 공유 per-stage 실행 경로로 동일 인증서 보존. escalation 실험은 **2모델·1태스크**로 model-parametric 확인. (출처: 초록)

### 한계
- (저자 명시) escalation 실험이 **2모델·1태스크**로 극히 제한적 — 일반화 불가.
- (저자 명시) 컴파일러는 **identity/verifier replay**만 확인하고 **출력 정합성이나 모델 행동은 검증하지 않음** — 보증 범위가 구조적 계약에 국한.
- (분석자 판단) 범주론적 형식화의 실무 채택 장벽이 큼 — operad/coalgebra 어휘가 실무자에게 진입장벽.

### 하네스 엔지니어링 관련성
- 하위 주제 태그: **theory / definition** (형식 이론 계열)
- 왜 중요한가: 하네스 이론을 **가장 수학적으로 형식화**한 극단 사례. 서베이의 "하네스 설계의 형식화 시도" 절에서 스펙트럼의 formal 끝단으로 배치. 합성·속성 보존을 명시적으로 다룬 유일 계열.

### 인용용 핵심 사실 (검증 대상)
- 범주론적 **Architecture 삼중항 (G, Know, Phi)**가 하네스 엔지니어링의 형식 이론을 제공한다고 주장. (초록)
- 에이전트 외부화 4기둥 = **Memory(coalgebraic state), Skills(operad-composed objects), Protocols(syntactic wiring G), Harness(=Architecture 전체)**. (초록)
- 컴파일러 펑터가 **Swarms, DeerFlow, Ralph, Scion, LangGraph** 5개를 타깃하며, 인증서 보존을 **identity 또는 replay**로 검증(출력 정합성/모델 행동은 미검증). (초록)
- escalation 실험은 **2모델·1태스크** 규모로 model-parametric 제어 경로를 확인. (초록)

---

## 2605.18747 — Code as Agent Harness

- 저자/기관: Xuying Ning, Katherine Tieu, Dongqi Fu, Tianxin Wei, Zihao Li, Yuanchen Bei 외 (+36)
- 날짜: 2026-05-18
- URL: https://arxiv.org/abs/2605.18747
- 확인수준: **초록만** (대규모 서베이, 초록이 3계층 구조를 명시)

### 한 문장 요약
코드가 단순 출력 대상이 아니라 에이전트 추론·행동·환경 모델링·검증의 **운영 기질(operational substrate)**이 되었다는 관점에서, **"code as agent harness"**를 통일 렌즈로 세우고 3계층(interface·mechanisms·scaling)으로 서베이한다.

### 문제 정의
LLM이 코드 이해·생성에 강해지면서, 에이전트 시스템에서 코드는 최종 산출물을 넘어 **에이전트 인프라의 기반**이 되었다. 이 전환을 하네스 렌즈로 체계화할 통일 관점이 필요하다.

### 핵심 방법 (3계층 서베이)
1. **Harness interface** — 코드가 에이전트를 reasoning·action·environment modeling에 연결하는 층.
2. **Harness mechanisms** — 장기 실행을 위한 planning·memory·tool use, 그리고 하네스를 신뢰·적응 가능하게 만드는 feedback-driven control·optimization.
3. **Scaling the harness** — 단일 에이전트에서 멀티에이전트로 확장; 공유 코드 산출물이 멀티에이전트 조율·리뷰·검증을 뒷받침.
- 응용 영역 정리: coding assistants, GUI/OS automation, embodied agents, scientific discovery, personalization/recommendation, DevOps, enterprise workflows.

### 주요 기여
1. **"code as agent harness"** 통일 관점 제시 — 코드를 에이전트 인프라의 중심에 놓음.
2. interface / mechanisms / scaling **3계층 조직화**.
3. 하네스 엔지니어링의 **미해결 도전** 목록: 최종 태스크 성공 너머의 평가, 불완전 피드백 하 검증, regression-free 하네스 개선, 멀티에이전트 간 일관된 공유 상태, 안전-critical 행동에 대한 인간 감독, 멀티모달 확장.

### 실험 결과 (정량)
- 서베이 논문 — 자체 벤치마크 없음. 대표 방법·응용을 종합.

### 한계
- (분석자 판단) 저자 37명 규모의 광범위 서베이 — 넓지만 각 방법의 정량 대조는 얕을 수 있음.
- (분석자 판단) "code as harness"라는 프레이밍이 코드-실행 기반이 약한 하네스(예: 순수 GUI 조작, 멀티유저 거버넌스)를 얼마나 포괄하는지 불명.

### 하네스 엔지니어링 관련성
- 하위 주제 태그: **taxonomy / tool-orchestration / multi-agent** (code-centric 서베이)
- 왜 중요한가: 하네스를 **"코드 = 운영 기질"** 관점에서 통합. 2606.20683의 기능적 6책임 렌즈와 **상보적** — 이쪽은 substrate(무엇으로 만드는가), 저쪽은 responsibility(무엇을 하는가). 서베이의 "하네스를 보는 두 렌즈" 대조에 유용.

### 인용용 핵심 사실 (검증 대상)
- 코드를 에이전트 인프라의 기반으로 놓는 **"code as agent harness"** 통일 관점을 제시. (초록)
- 서베이를 **3계층: harness interface / harness mechanisms / scaling the harness**로 조직. (초록)
- 하네스 엔지니어링 미해결 도전으로 **최종 성공 너머 평가, 불완전 피드백 하 검증, regression-free 개선, 멀티에이전트 공유 상태 일관성, 안전-critical 인간 감독, 멀티모달 확장**을 명시. (초록)

---

## 2605.15221 — Effective Harness Engineering for Algorithm Discovery with Coding Agents

- 저자/기관: Yoichi Ishibashi, Taro Yano, Masafumi Oyamada
- 날짜: 2026-05-13
- URL: https://arxiv.org/abs/2605.15221
- 확인수준: **초록만**

### 한 문장 요약
AlphaEvolve/FunSearch 계열의 알고리즘 발견에서 성공이 모델뿐 아니라 **실행 인프라=하네스** 설계에 크게 좌우됨을 보이고, 고정 토큰 예산 하 하네스 설계 3문항을 Vesper 프레임워크로 실험한다.

### 문제 정의
LLM+진화탐색 알고리즘 발견의 성공은 모델 능력만으로 결정되지 않고 **하네스 설계**가 유의하게 좌우한다. 세 가지 하네스 설계 질문: (1) 고정 토큰 예산 하에서 얕은 사고로 많은 알고리즘 vs 깊은 사고로 적은 알고리즘, (2) 생성 프로그램이 채점 함수를 악용하는 **evaluation hack**를 하네스가 어떻게 다룰 것인가, (3) 전체 파일시스템 접근이 필요한 에이전트를 어떻게 **안전하게 병렬 실행**할 것인가.

### 핵심 방법
- **Vesper** 알고리즘 발견 프레임워크에 위 3문항을 다루는 하네스 개선을 통합.
- Circle Packing 문제에서 **동일 토큰 예산** 하에 비교.

### 주요 기여
1. 알고리즘 발견 성공의 상당 부분이 **하네스 설계**에서 나옴을 실증.
2. **"깊게 적게 vs 얕게 많이"** 트레이드오프의 반직관적 결론 제시.
3. **evaluation hack** 탐지 필요성과 모델 능력의 관계 규명.

### 실험 결과 (정량)
- Circle Packing에서 **동일 토큰 예산** 하, **적은 수의 알고리즘을 각각 더 깊이 생각**하는 편이 더 높은 점수를 달성 — 즉 개체 수 스케일링보다 **개체 품질 스케일링이 예산 효율적**. (출처: 초록)
- **더 능력 있는 모델일수록 evaluation hack를 더 높은 비율로** 생성 — 모델 스케일에 따라 hack 탐지 필요성 증가. (출처: 초록)

### 한계
- (분석자 판단) 단일 도메인(Circle Packing) 결과 — 일반 알고리즘 발견으로의 외삽 주의.
- (분석자 판단) "깊게 적게"의 최적점이 문제·모델 의존일 수 있음(초록은 예산 고정 조건).

### 하네스 엔지니어링 관련성
- 하위 주제 태그: **eval-harness / agent-loop / 기타(safety-sandbox)**
- 왜 중요한가: 하네스 설계 **선택(사고 깊이·hack 방어·병렬 격리)이 성과를 직접 좌우**함을 도메인 특화로 실증. "harness design이 성능 결정 요인"이라는 테마 공통 명제의 알고리즘-발견 판 증거. evaluation hacking은 eval-harness 테마(2606.08960 hacker-fixer)와 교차.

### 인용용 핵심 사실 (검증 대상)
- Circle Packing에서 동일 토큰 예산 하 **적은 알고리즘·깊은 사고가 많은 알고리즘·얕은 사고보다 높은 점수** — 개체 품질 스케일링이 개체 수 스케일링보다 예산 효율적. (초록)
- **더 능력 있는 모델일수록 evaluation hack 생성 비율이 높아** hack 탐지 필요성이 모델 스케일과 함께 증가. (초록)
- 하네스 개선을 통합한 프레임워크 이름은 **Vesper**. (초록)

---

## 2605.12129 — It's Not the Size: Harness Design Determines Operational Stability in Small Language Models

- 저자/기관: Yong-eun Cho
- 날짜: 2026-05-12
- URL: https://arxiv.org/abs/2605.12129
- 확인수준: **초록만** (초록에 정량 수치가 풍부)

### 한 문장 요약
소형 언어모델(2–3B)에서 **하네스 엔지니어링 수준**이 운영 성능을 좌우함을 3모델·24태스크로 실험하고, 무하네스보다 최소 셸이 오히려 나쁠 수 있는 **비단조 현상**과 **scaffold collapse**를 보고한다.

### 문제 정의
소형 모델(SLM, 2–3B)에서 하네스 수준이 운영 성능(안정성)에 미치는 영향을 통제 실험으로 규명한다. 통념("크기가 성능을 결정")에 반해 **하네스 설계**가 결정 요인일 수 있는가?

### 핵심 방법
- **3개 하네스 조건:** model-only(raw prompt), minimal-shell(wrapper tags), **4-stage pipeline(plan→execute→verify→recover)**.
- **3개 모델:** Gemma4 E2B, Qwen3.5:2B, LLaMA 3.2 3B.
- **24개 태스크**에서 TSR(Task Success Rate)·VTSR(Valid TSR) 비교. planning/recovery 기여를 ablation.

### 주요 기여
1. SLM에서 **하네스 설계가 크기보다 운영 안정성을 좌우**함을 실증("It's not the size").
2. **비단조 현상**(minimal-shell TSR < model-only TSR) 관찰 — 어설픈 하네스가 오히려 해가 됨.
3. **scaffold collapse** 개념 — 하네스 지원 없이 복잡한 포맷 요구 하에서 모델이 JSON 구조를 포기.
4. planning·recovery 각 기여도 ablation 정량화.

### 실험 결과 (정량)
- 파이프라인 하네스가 **Gemma4 E2B에서 TSR=0.952, VTSR=1.000** (T1–T5, 21태스크). (초록)
- 두 모델에서 **비단조 현상: minimal-shell TSR < model-only TSR** 관찰. (초록)
- LLaMA 3.2 3B **model-only에서 7건 포맷 위반, TSR=0.429** — scaffold collapse(하네스 없이 복잡 포맷 요구 시 JSON 구조 포기). (초록)
- ablation: **planning과 recovery가 각각 총 이득의 약 24.7% 기여.** (초록)
- 전체 파이프라인 실행 **VCR(Verification Catch Rate)=0.625.** (초록)

### 한계
- (분석자 판단) 소형 모델·24태스크 소규모 — 통계적 일반화 제한.
- (분석자 판단) 저자 1인·단일 저자 스터디, 태스크 구성(T1–T5)의 대표성 불명.

### 하네스 엔지니어링 관련성
- 하위 주제 태그: **agent-loop / eval-harness**
- 왜 중요한가: "하네스가 성능 결정 요인"이라는 테마 공통 명제를 **소형 모델**에서 가장 선명하게 보여주는 증거. 특히 **비단조성**(어설픈 하네스는 해롭다)과 **scaffold collapse**는 서베이의 "하네스가 항상 도움이 되는가?" 반례 절에 유용. 2603.29231(reliability)의 "memory scaffolds universally hurt"와 방향적으로 공명.

### 인용용 핵심 사실 (검증 대상)
- 4-stage 파이프라인(plan→execute→verify→recover)이 **Gemma4 E2B에서 TSR=0.952, VTSR=1.000**(21태스크). (초록)
- **비단조 현상**: 두 모델에서 minimal-shell TSR < model-only TSR. (초록)
- LLaMA 3.2 3B model-only: **7건 포맷 위반, TSR=0.429**, scaffold collapse 관찰. (초록)
- ablation: **planning·recovery 각각 총 이득의 약 24.7% 기여**; 파이프라인 VCR=0.625. (초록)

---

## 2604.03515 — Inside the Scaffold: A Source-Code Taxonomy of Coding Agent Architectures  *(OUT-of-range · 배경 참고)*

> **범위 표시:** 2604.xxxx 는 이 서베이의 대상 기간(주로 2605–2606) **밖**의 배경 논문. 정의·택소노미 계보의 선행 근거로만 인용하고, 핵심 최신 사례로 분류하지 않는다.

- 저자/기관: Benjamin Rombaut
- 날짜: 2026-04-03
- URL: https://arxiv.org/abs/2604.03515
- 확인수준: **초록만**

### 한 문장 요약
코딩 에이전트를 감싸는 **스캐폴드 코드**를 13개 오픈소스 에이전트의 **소스코드 수준**에서 분석해, 3계층·12차원의 **소스코드 기반 아키텍처 택소노미**를 제시한다.

### 문제 정의
LLM을 감싸는 스캐폴딩 코드(control loop, tool definitions, state management, context strategy)가 잘 이해되지 않는다. 기존 서베이는 추상 능력(tool use·planning·reflection)으로 분류해 **구조적으로 다른 시스템을 구분하지 못하고**, trajectory 연구는 무엇을 하는지만 관찰하고 왜 그런지를 결정하는 스캐폴드 코드를 보지 않는다.

### 핵심 방법
- **13개 오픈소스 코딩 에이전트 스캐폴드**를 **고정 커밋 해시(pinned commit)**에서 분석.
- 각 에이전트를 **3계층(control architecture / tool·environment interface / resource management)** 아래 **12차원**으로 특성화.
- 모든 택소노미 주장을 **파일 경로·라인 번호로 근거화**.

### 주요 기여
1. **소스코드 수준** 아키텍처 택소노미(추상 능력 분류의 한계 극복).
2. 스캐폴드가 **이산 분류에 저항**함을 실증 — 연속적 설계 공간.
3. **5개 루프 프리미티브**(ReAct, generate-test-repair, plan-execute, multi-attempt retry, tree search)가 조합 가능한 빌딩블록임을 발견 — 13개 중 11개가 다중 프리미티브를 합성.
4. 외부 제약이 지배하는 곳(tool capability, edit formats, execution isolation)에서 차원이 수렴하고, 열린 설계 질문(context compaction, state management, multi-model routing)에서 발산.

### 실험 결과 (정량)
- control strategy는 fixed pipeline부터 **MCTS**까지, tool 개수는 **0–37개**, context compaction은 **7개 distinct 전략**. (초록)
- **13개 중 11개** 에이전트가 단일 제어구조가 아니라 **다중 루프 프리미티브를 합성**. (초록)

### 한계
- (범위) 2604 — 대상 기간 밖 배경 논문.
- (분석자 판단) 13개 스냅샷·특정 커밋 시점 — 빠르게 변하는 스캐폴드에 대해 스냅샷 노후화.

### 하네스 엔지니어링 관련성
- 하위 주제 태그: **taxonomy / agent-loop** (source-code 택소노미)
- 왜 중요한가: **정의 이전의 실증 택소노미** 선행 사례. "스캐폴드가 이산 분류에 저항한다 / 5개 루프 프리미티브가 조합된다"는 발견은 2606.10106의 정의 작업과 2606.20683의 6책임 분해 모두에 배경을 제공. 배경으로만 인용.

### 인용용 핵심 사실 (검증 대상)
- **13개 오픈소스 코딩 에이전트**를 고정 커밋에서 **3계층·12차원**으로 분석. (초록)
- tool 개수 **0–37**, context compaction **7개 전략**, control은 fixed pipeline~MCTS 범위. (초록)
- **5개 루프 프리미티브**(ReAct, generate-test-repair, plan-execute, multi-attempt retry, tree search)가 조합 블록이며 **13개 중 11개가 다중 합성**. (초록)

---

## 2604.25850 — Agentic Harness Engineering: Observability-Driven Automatic Evolution of Coding-Agent Harnesses  *(OUT-of-range · 배경 참고)*

> **범위 표시:** 2604.xxxx — 대상 기간 밖 배경 논문. 자기진화 테마(2606.05922 RHO, 2606.09498 Self-Harness, 2606.06324 HarnessFix 등)의 **선행/근접 근거**로 인용하되 핵심 최신 사례로 분류하지 않는다.

- 저자/기관: Jiahang Lin, Shichun Liu, Chengjun Pan, Lizhi Lin, Shihan Dou, Zhiheng Xi 외 (+5)
- 날짜: 2026-04-28
- URL: https://arxiv.org/abs/2604.25850
- 확인수준: **초록만** (초록에 정량 수치 풍부)

### 한 문장 요약
하네스 엔지니어링이 여전히 수작업임을 지적하고, **3개 관측성 기둥(component/experience/decision observability)**으로 편집을 falsifiable 계약으로 만들어 하네스를 **자율 진화**시키는 폐루프 AHE를 제안한다.

### 문제 정의
하네스가 코딩 에이전트 성능의 중심이 됐지만 하네스 엔지니어링은 **수작업 공예**로 남아 있다. 자동화의 3난제: 편집 가능 컴포넌트에 걸친 **이질적 액션 공간**, 실행 가능 신호를 묻어버리는 **방대한 trajectory**, **귀인이 어려운 편집 효과**.

### 핵심 방법 (3 관측성 기둥)
1. **Component observability** — 모든 편집 가능 하네스 컴포넌트에 파일 수준 표현을 부여 → 액션 공간이 명시적·되돌림 가능.
2. **Experience observability** — 수백만 raw trajectory 토큰을 계층적 drill-down 증거 corpus로 증류 → 진화 에이전트가 실제 소비 가능.
3. **Decision observability** — 모든 편집을 self-declared 예측과 짝지어 다음 라운드 태스크 결과로 검증 → 편집을 **falsifiable 계약**으로.

### 주요 기여
1. 하네스 진화를 **trial-and-error로 붕괴하지 않는 자율 폐루프(AHE)**로 형식화.
2. 3 관측성 기둥으로 이질 액션 공간·신호 매몰·귀인 난제 해결.
3. 진화된 하네스의 **cross-family·cross-benchmark 전이** 실증.

### 실험 결과 (정량)
- **10회 AHE 반복**으로 Terminal-Bench 2 pass@1을 **69.7% → 77.0%**로 상승, 인간 설계 Codex-CLI(**71.9%**)와 자기진화 베이스라인(ACE, TF-GRPO)을 상회. (초록)
- 동결된 하네스가 재진화 없이 전이: SWE-bench-verified에서 **seed 대비 12% 적은 토큰**으로 aggregate success 최고; Terminal-Bench 2에서 3개 대체 모델 계열에 **+5.1~+10.1pp cross-family 이득**. (초록)
- ablation: 이득이 **system prompt가 아니라 tools·middleware·long-term memory**에서 나옴 — 사실적 하네스 구조는 전이되나 산문 수준 전략은 전이 안 됨. (초록)

### 한계
- (범위) 2604 — 대상 기간 밖 배경 논문.
- (분석자 판단) 2606.05922(RHO)·2606.09498(Self-Harness)·2606.06324(HarnessFix)·2606.15363(APEX, "Self-Harness [1]" 인용)와 **강한 계보 관계** — 자기진화 테마 담당 analyst와 연결 필요(→ SendMessage 대상).

### 하네스 엔지니어링 관련성
- 하위 주제 태그: **agent-loop / eval-harness / self-evolution(자기진화)**
- 왜 중요한가: 정의·이론 테마와 자기진화 테마의 **교량 논문**. "하네스를 관측성으로 분해 → 편집을 falsifiable 계약화 → 자율 진화"는 하네스를 **정적 대상이 아니라 진화 대상**으로 보는 시각을 정착시킨 선행 사례. "prose 전략은 전이 안 되고 factual 구조는 전이된다"는 발견은 서베이의 하네스 일반화(harness generalization) 논의에 직접 근거.

### 인용용 핵심 사실 (검증 대상)
- **10회 AHE 반복**으로 Terminal-Bench 2 pass@1 **69.7% → 77.0%**, 인간 설계 Codex-CLI **71.9%** 상회. (초록)
- 동결 하네스 전이: SWE-bench-verified에서 **seed 대비 −12% 토큰**으로 최고 aggregate success; Terminal-Bench 2에서 **+5.1~+10.1pp cross-family** 이득. (초록)
- 이득의 국소화: **tools·middleware·long-term memory**에서 나오고 **system prompt에서는 아님**. (초록)
- 3 관측성 기둥: **component / experience / decision observability**, 각 편집을 **falsifiable 계약**으로. (초록)

---

## 이 테마의 공통 관점 (Synthesis Note)

**1. 하네스는 이 분야의 새로운 1급 시민이다 — 그리고 아직 정의가 불안정하다.**
2606.10106은 "agent harness"가 제품·평가 스캐폴드·framework·SDK·orchestrator와 혼용되는 **다의성 문제**를 정면으로 지적하고 필요·충분조건+포함/배제 테스트로 기준 정의를 세운다. 이 테마의 존재 이유가 곧 이 정의의 필요성이다.

**2. "하네스가 성능을 결정한다"는 것이 관통 명제 — 모델 크기가 아니라 설계가 병목.**
제목부터가 증거다: 2605.12129 *"It's Not the Size"*, 2605.15221 *"Effective Harness Engineering …"*, 2605.13357은 SWE 능력의 locus를 모델에서 **model-harness-environment 시스템**으로 재배치한다. 2606.20683은 이를 "병목이 model / harness / **coupling** 중 어디인가"라는 중심 질문으로 정식화하고, 답을 "상호작용에서 창발"로 규정한다. 2605.12129의 **scaffold collapse**·**비단조성**(어설픈 하네스는 오히려 해롭다)은 이 명제에 필요한 반례·경계 조건까지 제공한다.

**3. 하네스를 "무엇으로 분해하는가"에 대한 합의는 아직 없다 — 분류 어휘가 6~12개로 제각각.**
- 2606.20683: **6 책임**(observation·context·control·action·state·verification)
- 2605.13357: **11 책임**(task spec·context selection·tool access·project memory·task state·observability·failure attribution·verification·permissions·entropy auditing·intervention recording) + **H0–H3 사다리**
- 2604.03515(배경): **3계층·12차원 + 5 루프 프리미티브**
- 2605.18747: **3계층**(interface·mechanisms·scaling), "code as substrate" 렌즈
- 2605.12239: **범주론적 (G, Know, Phi)** — 형식화 극단
이들은 서로 대응 관계가 명시되지 않아, 서베이 종합 시 **하나의 정합적 분류 축으로 정렬하는 작업**이 필요하다(권장 앵커: 2606.20683의 6책임을 골격으로, 나머지를 매핑).

**4. 두 개의 상보적 렌즈: 기능(무엇을 하는가) vs 기질(무엇으로 만드는가).**
2606.20683/2605.13357은 하네스를 **기능적 책임**으로 본다. 2605.18747은 **코드를 운영 기질**로 본다. 2605.12239는 이를 **범주론적 아키텍처**로 추상화한다. 서베이는 이 두(세) 렌즈를 대조축으로 쓸 수 있다.

**5. 이 테마는 자기진화 테마와 교량으로 연결된다.**
배경 논문 2604.25850(AHE)은 하네스를 **정적 정의 대상이 아니라 진화 대상**으로 보는 시각을 정착시켰고, 이는 2606.05922(RHO)·2606.09498(Self-Harness)·2606.06324(HarnessFix)·2606.15363(APEX) 등 자기진화 계열의 선행이다. "정의/이론"과 "자기진화"는 별개 테마가 아니라 **정의된 하네스를 자동으로 개선한다**는 하나의 축의 양끝이다.

**교차 테마 연결 메모(다른 analyst에게 공유 권장):**
- 자기진화 담당 → 2604.25850(배경)이 그쪽 계보의 선행. "factual 구조는 전이되나 prose 전략은 전이 안 됨" 발견 공유.
- eval-harness 담당 → 2605.13357의 "감사 가능 에피소드 패키지", 2605.15221의 evaluation hacking(2606.08960 hacker-fixer와 교차).
- context-engineering 담당 → 2606.20683의 6책임 중 context/state 축이 그쪽 논문들(TokenPilot·ACE·VISTA 등)의 상위 분류.

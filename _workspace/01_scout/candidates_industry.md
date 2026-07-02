# Scout 후보 — 산업/벤치마크 축 (candidates_industry)

**축 담당:** scout-industry — 기업 랩 리서치 블로그·기술 리포트·벤치마크
**수집 기간:** 2026-05 ~ 2026-07 (IN), 맥락용 기반 리포트는 OUT으로 표기
**수집 방법:** WebSearch 사용 불가(도구 미제공) → DuckDuckGo HTML 엔드포인트를 WebFetch로 검색 발견 + 각 1차 페이지를 WebFetch로 직접 열어 제목·저자·날짜·내용 확인
**정직성 주의:** DuckDuckGo 스니펫 요약은 환각 위험이 있어, "WebFetch로 페이지 실제 확인"으로 표기된 항목만 1차 페이지를 실제로 열어 검증했다. OpenAI 도메인은 WebFetch에 403을 반환하여 접근 불가 → 2차 출처(InfoQ)로 교차 확인.

---

## IN (2026-05 ~ 2026-07) — 범위 내

### C1. How we contain Claude across products
- 저자: Max McGuinness, Mikaela Grace, Jiri De Jonghe, Jake Eaton, Abel Ribbink (Anthropic)
- 날짜: 2026-05-25 | 범위판정: IN
- 소스: 기업블로그 (Anthropic Engineering)
- URL: https://www.anthropic.com/engineering/how-we-contain-claude
- ID: -
- 한줄요약: 에이전트 하네스의 실행 격리·안전 계층(claude.ai gVisor 컨테이너, Claude Code OS 샌드박스 Seatbelt/bubblewrap, Cowork 봉인 VM)과 환경·모델·외부콘텐츠 3계층 방어, 프롬프트 인젝션/자격증명 유출 취약점 사례.
- 검색어: Anthropic engineering blog May 2026 agent
- 하네스관련성: high — 하네스의 실행환경 격리·권한·안전 훅은 harness engineering의 핵심 축. "직접 만든 계층이 가장 약하다" 등 실전 하네스 설계 교훈.
- 확인방법: WebFetch로 페이지 실제 확인

### C2. New in Claude Managed Agents: dreaming, outcomes, and multiagent orchestration
- 저자: Anthropic (개별 저자 미표기)
- 날짜: 2026-05-19 | 범위판정: IN
- 소스: 기업블로그 (claude.com/blog)
- URL: https://claude.com/blog/new-in-claude-managed-agents
- ID: -
- 한줄요약: Managed Agents에 dreaming(세션·메모리 검토로 패턴 추출·메모리 큐레이션), outcomes(루브릭 기반 grader 채점, 최대 +10%p), multiagent orchestration(리드 에이전트가 공유 파일시스템에서 병렬 서브에이전트에 위임) 추가. Netflix 빌드로그 분석 사례.
- 검색어: claude.com/blog managed agents multiagent orchestration dreaming 2026
- 하네스관련성: high — 멀티에이전트 오케스트레이션·에이전트 메모리·평가(outcomes)가 모두 하네스 구성요소.
- 확인방법: WebFetch로 페이지 실제 확인

### C3. New in Claude Managed Agents: self-hosted sandboxes and MCP tunnels
- 저자: Anthropic (개별 저자 미표기)
- 날짜: 2026-05-19 | 범위판정: IN
- 소스: 기업블로그 (claude.com/blog)
- URL: https://claude.com/blog/claude-managed-agents-updates
- ID: -
- 한줄요약: 오케스트레이션 루프는 Anthropic 서버에 두고 툴 실행만 사용자 인프라(Cloudflare/Daytona/Modal/Vercel)로 이동하는 self-hosted 샌드박스, 사설망 MCP 서버 접근용 MCP tunnels(아웃바운드 단일 연결·E2E 암호화).
- 검색어: OpenAI/Anthropic Codex tool use 2026 (Claude blog index에서 발견)
- 하네스관련성: high — 하네스의 툴 실행 격리·MCP 툴 연결 인프라 설계.
- 확인방법: WebFetch로 페이지 실제 확인

### C4. New in Claude Managed Agents: run agents on a schedule and store environment variables in vaults
- 저자: Anthropic (개별 저자 미표기)
- 날짜: 2026-06-09 | 범위판정: IN
- 소스: 기업블로그 (claude.com/blog)
- URL: https://claude.com/blog/whats-new-in-claude-managed-agents
- ID: -
- 한줄요약: Managed Agents의 스케줄 실행과 환경변수 vault 저장 기능 추가(하네스 운영·비밀관리).
- 검색어: claude.com/blog managed agents 2026 (blog index)
- 하네스관련성: medium — 하네스 운영(스케줄링·시크릿 관리) 측면. 제품 업데이트 성격.
- 확인방법: 스니펫만 (blog index에서 제목·날짜 확인, 개별 페이지 미개봉)

### C5. The evolution of agentic surfaces: building with Claude Managed Agents
- 저자: Gagan Bhat, Isabella He (Anthropic Applied AI team)
- 날짜: 2026-06-10 | 범위판정: IN
- 소스: 기업블로그 (claude.com/blog)
- URL: https://claude.com/blog/building-with-claude-managed-agents
- ID: -
- 한줄요약: 에이전트 인프라 3단계 진화 — Messages API(2023, 직접 에이전트 루프 구현) → Claude Agent SDK(2025, Claude Code의 하네스 기계장치 제공) → Managed Agents(2026, brain/hands 분리 관리형). append-only 세션 로그, 시크릿 vault, TTFT 60% 단축.
- 검색어: agentic coding report 2026 / claude blog index
- 하네스관련성: high — "하네스(harness) machinery" 개념의 진화를 명시적으로 서술. harness engineering 서사의 핵심 1차 자료.
- 확인방법: WebFetch로 페이지 실제 확인

### C6. Steering Claude Code: CLAUDE.md files, skills, hooks, rules, subagents and more
- 저자: Anthropic (개별 저자 미표기)
- 날짜: 2026-06-18 | 범위판정: IN
- 소스: 기업블로그 (claude.com/blog)
- URL: https://claude.com/blog/steering-claude-code-skills-hooks-rules-subagents-and-more
- ID: -
- 한줄요약: 하네스 커스터마이징 7수단 — CLAUDE.md(상시 로드 지침), rules(.claude/rules, 경로 스코프), skills(.claude/skills, 동적 로드), subagents(.claude/agents, 분리 컨텍스트), hooks(이벤트 트리거), output styles, append system prompt. CLAUDE.md 200줄 이하 권고.
- 검색어: claude.com/blog steering claude code (blog index)
- 하네스관련성: high — 컨텍스트 엔지니어링·스킬·훅·서브에이전트는 하네스 엔지니어링의 실전 구성요소 그 자체. 본 서베이 주제에 직결.
- 확인방법: WebFetch로 페이지 실제 확인

### C7. Agent identity in Claude Tag: a new access model for autonomous, team-wide AI
- 저자: Anthropic (개별 저자 미표기)
- 날짜: 2026-06-24 | 범위판정: IN
- 소스: 기업블로그 (claude.com/blog)
- URL: https://claude.com/blog/agent-identity-access-model
- ID: -
- 한줄요약: 자율·팀 단위 AI를 위한 에이전트 신원(identity)·접근 모델("Claude Tag").
- 검색어: claude.com/blog managed agents 2026 (blog index)
- 하네스관련성: medium — 에이전트 신원·권한은 하네스의 접근제어 계층. 개별 페이지 미검증.
- 확인방법: 스니펫만 (blog index에서 제목·날짜 확인)

### C8. Devin Fusion: Frontier Performance at 35% Lower Cost
- 저자: The Cognition Team (Cognition AI)
- 날짜: 2026-06-29 | 범위판정: IN
- 소스: 기업블로그 (Cognition)
- URL: https://cognition.com/blog/devin-fusion
- ID: -
- 한줄요약: 하이브리드 모델 하네스 — frontier 에이전트 + 저비용 sidekick 에이전트 병렬 운용, 경량 분류기가 컨텍스트 compaction 시점에 모델 동적 라우팅(캐시 페널티 회피). 내부 PR의 88%를 자동 라우팅으로 처리, 비용 35~41% 절감.
- 검색어: Cognition Devin blog 2026 agent multi-agent context
- 하네스관련성: high — "하이브리드 모델 하네스"를 명시. 동적 모델 라우팅·컨텍스트 compaction·멀티에이전트 위임이 하네스 설계 핵심.
- 확인방법: WebFetch로 페이지 실제 확인

### C9. Parallel Context Compaction for Long-Horizon LLM Agent Serving
- 저자: Musa Cim, Burak Topcu, Chita Das, Mahmut Taylan Kandemir (소속 미표기)
- 날짜: 2026-05-22 | 범위판정: IN
- 소스: arXiv (cs 계열)
- URL: https://arxiv.org/abs/2605.23296
- ID: arXiv:2605.23296
- 한줄요약: 장기과제 에이전트의 대화 이력이 컨텍스트 윈도우를 초과하는 문제를, 순차 요약 대신 "병렬 compaction"으로 처리하는 서빙 기법.
- 검색어: agent context engineering blog 2026 long horizon compaction memory
- 하네스관련성: high — 컨텍스트 compaction/관리는 하네스 엔지니어링 핵심 축.
- 확인방법: WebFetch로 페이지 실제 확인
- ⚠ DEDUP: arXiv 논문이므로 scout-academic / scout-adjacent(컨텍스트 엔지니어링 축)에서도 잡힐 가능성 높음.

### C10. Co-Scientist: A multi-agent AI partner to accelerate research
- 저자: Co-Scientist team (Juraj Gottweis, Vivek Natarajan 등, Google DeepMind)
- 날짜: 2026-05-19 | 범위판정: IN
- 소스: 기업블로그 (Google DeepMind)
- URL: https://deepmind.google/blog/co-scientist-a-multi-agent-ai-partner-to-accelerate-research/
- ID: -
- 한줄요약: Gemini 기반 멀티에이전트 연합(generation/proximity/reflection/ranking/evolution/meta-review + supervisor)으로 과학 가설 생성·토너먼트식 랭킹·진화. 문헌·DB(ChEMBL/UniProt) 교차검증에 상당 자원 투입.
- 검색어: Google DeepMind agent 2026 blog coding agent tool use context
- 하네스관련성: medium — 도메인은 과학연구지만 멀티에이전트 오케스트레이션·supervisor·검증 루프 구조가 하네스 패턴. 코딩 하네스는 아님.
- 확인방법: WebFetch로 페이지 실제 확인 (날짜 2026 확인, 2025 아님)

### C11. Investing in multi-agent AI safety research
- 저자: Google DeepMind (개별 저자 미표기)
- 날짜: 2026-06 (정확 일자 미확인) | 범위판정: IN
- 소스: 기업블로그 (Google DeepMind)
- URL: https://deepmind.google/blog/investing-in-multi-agent-ai-safety-research/
- ID: -
- 한줄요약: 멀티에이전트 AI 안전 연구 투자 관련 발표(멀티에이전트 시스템의 안전성).
- 검색어: Google DeepMind agent 2026 blog (blog index)
- 하네스관련성: low~medium — 멀티에이전트 안전은 하네스 안전계층과 인접하나, 하네스 설계 자체는 아님. 개별 페이지 미검증.
- 확인방법: 스니펫만 (blog index에서 제목·월 확인)

### C12. OpenAI Codex Changelog (2026-06 ~ 2026-07)
- 저자: OpenAI (Codex 팀)
- 날짜: 최신 2026-07-01 (Codex CLI 0.142.5) | 범위판정: IN
- 소스: 기업블로그/변경로그 (OpenAI developers)
- URL: https://developers.openai.com/codex/changelog
- ID: -
- 한줄요약: Codex CLI/앱 변경로그. 6/22 토큰 예산 추적(agent threads 전반 rollout token budget), 6/25 MCP 툴 검색 기본화·Codex Remote GA(QR 페어링), 6/18 E2E 암호화 Noise relay 실행기 등.
- 검색어: OpenAI Codex 2026 blog June July agent SDK cloud update
- 하네스관련성: medium — 코딩 에이전트 하네스(툴 검색·토큰 예산·원격 실행기)의 실제 구현 변화. 서베이 인용은 특정 항목 선별 필요.
- 확인방법: WebFetch로 페이지 실제 확인 (최신 날짜 2026-07-01 확인)

---

## OUT (범위 밖) — 맥락·기반 리포트 (부록/서론용, 폐기 금지)

### C13. Harness engineering: leveraging Codex in an agent-first world
- 저자: OpenAI (Martin Fowler 인용 포함)
- 날짜: 2026-02-11 (InfoQ 커버리지 2026-02-21) | 범위판정: OUT
- 소스: 기업블로그 (OpenAI) — 1차 접근 불가, 2차(InfoQ)로 교차확인
- URL: https://openai.com/index/harness-engineering/ (403) / 교차: https://www.infoq.com/news/2026/02/openai-harness-engineering-codex/
- ID: -
- 한줄요약: "Harness Engineering"이라는 용어의 원출처. 엔지니어가 구현 대신 "환경 설계·의도 명세·구조화된 피드백"에 집중, Codex 에이전트가 구현·테스트·관측성 담당. 5개월간 수동 작성 코드 0으로 약 100만 줄 베타 제품 구축. Fowler: "하네스는 컨텍스트 엔지니어링·아키텍처 제약·가비지 컬렉션을 포함한다."
- 검색어: OpenAI agents blog 2026 harness codex tool use
- 하네스관련성: high — 본 서베이 제목 "Harness Engineering"의 어원적 1차 자료. 범위 밖이나 서론·정의에 필수.
- 확인방법: 1차 페이지 접근불가(403) / 2차 출처 InfoQ WebFetch로 확인 → citation-verifier 재확인 필요
- ⚠ 검증필요: 1차 openai.com 페이지를 검증자가 다른 도구로 열어 날짜·저자 재확인 권장.

### C14. Harness design for long-running application development
- 저자: Prithvi Rajasekaran (Anthropic Labs)
- 날짜: 2026-03-24 | 범위판정: OUT
- 소스: 기업블로그 (Anthropic Engineering)
- URL: https://www.anthropic.com/engineering/harness-design-long-running-apps
- ID: -
- 한줄요약: 장기 실행 앱 개발용 하네스 설계. planner/generator/evaluator 역할 분리 멀티에이전트가 단일 에이전트를 능가, 평가와 생성 분리 + 구조적 태스크 분해로 장시간 자율 코딩에서 풀스택 앱 구축.
- 검색어: agent harness engineering blog 2026 Anthropic
- 하네스관련성: high — 제목·내용이 정확히 "harness design". 범위 밖(3월)이나 핵심 기반 자료.
- 확인방법: WebFetch로 페이지 실제 확인

### C15. Scaling Managed Agents: Decoupling the brain from the hands
- 저자: Lance Martin, Gabe Cemaj, Michael Cohen (Anthropic)
- 날짜: 2026-04-08 | 범위판정: OUT
- 소스: 기업블로그 (Anthropic Engineering)
- URL: https://www.anthropic.com/engineering/managed-agents
- ID: -
- 한줄요약: 하네스/모델(brain)과 샌드박스/툴(hands)·세션 로그를 안정 인터페이스로 분리("pets vs cattle"). execute(name,input)→string 통합 툴 인터페이스로 "many brains, many hands". TTFT p50 60%·p95 90%+ 개선.
- 검색어: OpenAI/Anthropic managed agents (Anthropic index)
- 하네스관련성: high — 하네스와 실행환경 분리 아키텍처. C5(6/10 후속)과 짝을 이루는 기반 자료.
- 확인방법: WebFetch로 페이지 실제 확인

### C16. An update on recent Claude Code quality reports (postmortem)
- 저자: Anthropic (개별 저자 미표기)
- 날짜: 2026-04-23 | 범위판정: OUT
- 소스: 기업블로그 (Anthropic Engineering)
- URL: https://www.anthropic.com/engineering/april-23-postmortem
- ID: -
- 한줄요약: 3~4월 Claude Code 품질 저하 3건 포스트모템 — reasoning effort 기본값 변경, 프롬프트 캐싱 버그(thinking history 반복 삭제), "≤25단어" verbosity 프롬프트가 코딩 품질 3% 저하. 시스템프롬프트 변경 통제 강화·점진 롤아웃 예고.
- 검색어: Anthropic engineering blog May 2026 agent (index)
- 하네스관련성: medium — 하네스(시스템프롬프트·캐싱·reasoning effort)의 미세 변화가 에이전트 성능에 미치는 영향의 실증 사례.
- 확인방법: WebFetch로 페이지 실제 확인

### C17. How we built Claude Code auto mode: a safer way to skip permissions
- 저자: John Hughes (Anthropic)
- 날짜: 2026-03-25 | 범위판정: OUT
- 소스: 기업블로그 (Anthropic Engineering)
- URL: https://www.anthropic.com/engineering/claude-code-auto-mode
- ID: -
- 한줄요약: 매 액션 승인(승인 피로) 대신 AI 분류기로 안전 액션 자동 허용·위험 액션 차단. 입력층(프롬프트 인젝션 프로브)+출력층(transcript 분류기, 2단계 필터). 실트래픽 FP 0.4%, FN 17%.
- 검색어: agent harness engineering blog 2026 Anthropic (index)
- 하네스관련성: high — 하네스의 권한/승인 게이트·프롬프트 인젝션 방어 설계. 하네스 안전 핵심.
- 확인방법: WebFetch로 페이지 실제 확인

### C18. Building a C compiler with a team of parallel Claudes
- 저자: Nicholas Carlini (Anthropic Safeguards)
- 날짜: 2026-02-05 | 범위판정: OUT
- 소스: 기업블로그 (Anthropic Engineering)
- URL: https://www.anthropic.com/engineering/building-c-compiler
- ID: -
- 한줄요약: 16개 Claude 에이전트가 git 동기화로 태스크 락을 잡고 병렬 협업, 약 2,000 Claude Code 세션으로 10만 줄 Rust C 컴파일러 구축(Linux 6.9 x86/ARM/RISC-V 컴파일, 테스트 99%). "태스크 검증기가 거의 완벽해야 한다"는 멀티에이전트 하네스 교훈.
- 검색어: Anthropic engineering blog agent (index)
- 하네스관련성: high — 병렬 멀티에이전트 하네스의 대규모 실증 + 검증기(verifier) 중요성. 코딩 하네스 사례.
- 확인방법: WebFetch로 페이지 실제 확인

### C19. Terminal-Bench: Benchmarking Agents on Hard, Realistic Tasks in Command Line Interfaces
- 저자: Mike A. Merrill 외 다수 (84 공저자)
- 날짜: 2026-01-17 | 범위판정: OUT
- 소스: 벤치마크 (arXiv + tbench.ai)
- URL: https://arxiv.org/abs/2601.11868 / 리더보드 https://www.tbench.ai/leaderboard
- ID: arXiv:2601.11868
- 한줄요약: 터미널/CLI 환경 에이전트 벤치마크(Terminal-Bench 2.0, 89개 하드 태스크, 인간 작성 해답·검증 테스트 포함). frontier 모델 <65% 성적.
- 검색어: Terminal-Bench 2026 leaderboard agent benchmark paper
- 하네스관련성: high — 평가 하네스/에이전트 벤치마크. 하네스 성능 측정 인프라.
- 확인방법: WebFetch로 페이지 실제 확인
- ⚠ DEDUP: arXiv 논문이므로 scout-academic 축과 중복 가능성 높음.

### C20. 2026 Agentic Coding Trends Report
- 저자: Anthropic
- 날짜: 2026-01-21 (2차 커버리지 2026-05-27) | 범위판정: OUT
- 소스: 기업 기술리포트 (Anthropic)
- URL: https://resources.anthropic.com/2026-agentic-coding-trends-report
- ID: -
- 한줄요약: 에이전틱 코딩 8대 트렌드 예측(foundation/capability/impact). Rakuten·TELUS·Zapier 사례. 개발자가 AI를 업무 60%에 쓰나 완전 위임은 0~20%("delegation gap").
- 검색어: agentic coding report 2026 state of coding agents benchmark
- 하네스관련성: medium — 에이전틱 코딩 산업 동향. 하네스 채택 맥락 제공(1차 페이지 미개봉, 2차 커버리지로 내용 파악).
- 확인방법: 스니펫만 (1차 resources.anthropic.com 페이지 미검증) → citation-verifier 확인 필요

---

## 검색 각도 요약 (수행한 쿼리)
1. agent harness engineering blog 2026 Anthropic
2. context engineering agents 2026 harness (Bing, 실패)
3. Anthropic context engineering agents blog post
4. Anthropic engineering blog May 2026 agent
5. OpenAI agents blog 2026 harness codex tool use
6. SWE-bench 2026 results leaderboard new benchmark
7. Terminal-Bench 2026 leaderboard agent benchmark paper
8. Cognition Devin blog 2026 agent multi-agent context
9. Google DeepMind agent 2026 blog coding agent tool use context
10. multi-agent orchestration report 2026 production agents
11. claude.com/blog managed agents multiagent orchestration dreaming 2026 (CAPTCHA)
12. Meta AI agent 2026 tool use coding agent report llama
13. agentic coding report 2026 state of coding agents benchmark
14. agent context engineering blog 2026 long horizon compaction memory
15. OpenAI Codex 2026 blog June July agent SDK cloud update
16. agent evaluation harness 2026 SWE-bench multimodal new benchmark paper
+ Anthropic engineering index / claude.com blog index / DeepMind blog index 직접 열람

## 희소성·정직성 노트
- **Meta AI / FAIR**: 2026-05~07 기간 하네스·에이전트 관련 **공식 1차 리포트를 발견하지 못함**. 검색 결과는 전부 3자 요약(aifirstfounders 등)이었음. 이 축에서 Meta 문헌은 희소.
- **일반 멀티에이전트 오케스트레이션 "가이드/블루프린트" 글 다수**(codebridge, linesncircles, explainx, frankx 등)는 SEO/컨설팅성 2차 콘텐츠라 **의도적으로 제외**(1차 랩 리포트 아님). 억지 패딩 방지.
- **SWE-bench 리더보드**: 2026 갱신은 확인되나(예: 7월 103개 모델, SWE-bench Pro 6월 등) 대부분 리더보드 페이지/3자 트래커. 인용 가치 있는 1차 논문/리포트는 별도 검증 필요.
- **OpenAI 도메인 403**: openai.com/index/* 는 WebFetch 403. C13은 2차 출처(InfoQ)로만 교차확인 → 검증자가 다른 도구로 1차 확인 권장. Codex changelog(developers.openai.com, C12)는 정상 접근됨.
- **C4, C7, C11, C20**은 인덱스/스니펫 단계까지만 확인(개별 1차 페이지 미개봉) → "확인방법: 스니펫만"으로 표기, 검증 단계에서 개별 확인 필요.

## 타 scout 대상 dedup 후보 (SendMessage 공유 대상)
- **C9** (arXiv:2605.23296, Parallel Context Compaction) — academic/adjacent(컨텍스트 엔지니어링) 축과 중복 예상
- **C19** (arXiv:2601.11868, Terminal-Bench) — academic 축(벤치마크 논문)과 중복 예상

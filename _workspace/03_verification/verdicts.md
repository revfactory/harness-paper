# 검증 결과 (verdicts) — Harness Engineering 서베이

**검증 방법:** 전체 arXiv 후보를 raw arXiv API(`export.arxiv.org/api/query`)의 원본 Atom XML로 배치 대조. 
API XML은 요약 모델을 거치지 않는 1차 인덱스이므로 제목·제출일 환각이 원천 차단됨. 블로그류는 HTTP 상태코드로 실존 확인.


## 요약
- arXiv 후보 총 95건 검증 → **전부 실존 확인(환각 0건)**
- CONFIRMED (실존 + 2026-05~07 범위 내): **86건**
- OUT-OF-RANGE (실존하나 범위 밖, 부록·배경용): 9건
- REJECTED (실존 부정/날조): 0건
- 블로그/기술리포트: 아래 별도 표 (HTTP 200 확인분)


## CONFIRMED — arXiv (2026-05~07, 리포트 본문 진입 허용)

| arXiv ID | 제출일 | 제목 | 저자 |
|---|---|---|---|
| [2605.01920](https://arxiv.org/abs/2605.01920) | 2026-05-03 | A Language for Describing Agentic LLM Contexts | Noga Peleg Pelc, Gal A. Kaminka, Yoav Goldberg |
| [2605.02092](https://arxiv.org/abs/2605.02092) | 2026-05-03 | NORA: A Harness-Engineered Autonomous Research Agent for End-to-End Spatial Data Science | Bing Zhou, Xiao Huang, Huan Ning, Qiusheng Wu 외 2인 |
| [2605.05400](https://arxiv.org/abs/2605.05400) | 2026-05-06 | Mise en Place for Agentic Coding: Deliberate Preparation as Context Engineering Methodology | Andrew Zigler |
| [2605.08435](https://arxiv.org/abs/2605.08435) | 2026-05-08 | A Dataset of Agentic AI Coding Tool Configurations | Matthias Galster, Seyedmoein Mohsenimofidi, Levi Böhme, Jai Lal Lulla 외 3인 |
| [2605.09998](https://arxiv.org/abs/2605.09998) | 2026-05-11 | Continual Harness: Online Adaptation for Self-Improving Foundation Agents | Seth Karten, Joel Zhang, Tersoo Upaa, Ruirong Feng 외 4인 |
| [2605.10052](https://arxiv.org/abs/2605.10052) | 2026-05-11 | Swarm Skills: A Portable, Self-Evolving Multi-Agent System Specification for Coordination Engineering | Xinyu Zhang, Zhicheng Dou, Deyang Li, Jianjun Tao 외 9인 |
| [2605.12239](https://arxiv.org/abs/2605.12239) | 2026-05-12 | Harness Engineering as Categorical Architecture | Bogdan Banu |
| [2605.12129](https://arxiv.org/abs/2605.12129) | 2026-05-12 | It's Not the Size: Harness Design Determines Operational Stability in Small Language Models | Yong-eun Cho |
| [2605.13357](https://arxiv.org/abs/2605.13357) | 2026-05-13 | AI Harness Engineering: A Runtime Substrate for Foundation-Model Software Agents | Hailin Zhong, Shengxin Zhu |
| [2605.15221](https://arxiv.org/abs/2605.15221) | 2026-05-13 | Effective Harness Engineering for Algorithm Discovery with Coding Agents | Yoichi Ishibashi, Taro Yano, Masafumi Oyamada |
| [2605.14483](https://arxiv.org/abs/2605.14483) | 2026-05-14 | LEMON: Learning Executable Multi-Agent Orchestration via Counterfactual Reinforcement Learning | Xudong Chen, Yixin Liu, Hua Wei, Kaize Ding |
| [2605.21516](https://arxiv.org/abs/2605.21516) | 2026-05-15 | Harnesses for Inference-Time Alignment over Execution Trajectories | Boyuan Wang, Bochao Li, Minghan Wang, Yuxin Tao 외 1인 |
| [2605.18747](https://arxiv.org/abs/2605.18747) | 2026-05-18 | Code as Agent Harness | Xuying Ning, Katherine Tieu, Dongqi Fu, Tianxin Wei 외 38인 |
| [2605.23296](https://arxiv.org/abs/2605.23296) | 2026-05-22 | Parallel Context Compaction for Long-Horizon LLM Agent Serving | Musa Cim, Burak Topcu, Chita Das, Mahmut Taylan Kandemir |
| [2605.24220](https://arxiv.org/abs/2605.24220) | 2026-05-22 | Polar: Agentic RL on Any Harness at Scale | Binfeng Xu, Hao Zhang, Shaokun Zhang, Songyang Han 외 8인 |
| [2605.27276](https://arxiv.org/abs/2605.27276) | 2026-05-26 | SIA: Self Improving AI with Harness & Weight Updates | Prannay Hebbar, Yogendra Manawat, Samuel Verboomen, Alesia Ivanova 외 3인 |
| [2605.30785](https://arxiv.org/abs/2605.30785) | 2026-05-29 | Learning Agent-Compatible Context Management for Long-Horizon Tasks | Lu Yi, Runlin Lei, Liuyi Yao, Yuexiang Xie 외 5인 |
| [2605.30738](https://arxiv.org/abs/2605.30738) | 2026-05-29 | MAVEN: Improving Generalization in Agentic Tool Calling | Omkar Ghugarkar, Vishvesh Bhat, Muhammad Ahmed Mohsin, Asad Aali |
| [2606.03461](https://arxiv.org/abs/2606.03461) | 2026-06-02 | What Makes Interaction Trajectories Effective for Training Terminal Agents? | Sidi Yang, Chaofan Tao, Jierun Chen, Tiezheng Yu 외 10인 |
| [2606.05922](https://arxiv.org/abs/2606.05922) | 2026-06-04 | Evolving Agents in the Dark: Retrospective Harness Optimization via Self-Preference | Wenbo Pan, Shujie Liu, Chin-Yew Lin, Jingying Zeng 외 4인 |
| [2606.06324](https://arxiv.org/abs/2606.06324) | 2026-06-04 | From Failed Trajectories to Reliable LLM Agents: Diagnosing and Repairing Harness Flaws | Mengzhuo Chen, Junjie Wang, Zhe Liu, Yawen Wang 외 1인 |
| [2606.06448](https://arxiv.org/abs/2606.06448) | 2026-06-04 | Agent Memory: Characterization and System Implications of Stateful Long-Horizon Workloads | Yasmine Omri, Ziyu Gan, Zachary Broveak, Robin Geens 외 5인 |
| [2606.05548](https://arxiv.org/abs/2606.05548) | 2026-06-04 | ADK Arena: Evaluating Agent Development Kits via LLM-as-a-Developer | Jintao Huang, Xiaomin Li, Gaurav Mittal, Yu Hu |
| [2606.07412](https://arxiv.org/abs/2606.07412) | 2026-06-05 | Socratic-SWE: Self-Evolving Coding Agents via Trace-Derived Agent Skills | Chuan Xiao, Zhengbo Jiao, Shaobo Wang, Wei Wang 외 4인 |
| [2606.07889](https://arxiv.org/abs/2606.07889) | 2026-06-05 | Strained Coherence: A Pre-Failure Signal in Coding Agent Execution Trajectories | Marut Pandya, Kasey Zhang, Baiqing Lyu |
| [2606.07462](https://arxiv.org/abs/2606.07462) | 2026-06-05 | Act As a Real Researcher: A Suite of Benchmarks Evaluating Frontier LLMs and Agentic Harnesses in Research Lifecycle | Jiayu Wang, Weijiang Lv, Bowen Fu, Jing Fu 외 7인 |
| [2606.08878](https://arxiv.org/abs/2606.08878) | 2026-06-07 | PerspectiveGap: A Benchmark for Multi-Agent Orchestration Prompting | Youran Sun, Xingyu Ren, Kejia Zhang, Xinpeng Liu 외 1인 |
| [2606.08610](https://arxiv.org/abs/2606.08610) | 2026-06-07 | HARBOR: A Harness Framework for Agentic Robot Reinforcement Learning | Zechu Li, Yufeng Jin, Xiaoyang Liu, Puze Liu 외 3인 |
| [2606.09682](https://arxiv.org/abs/2606.09682) | 2026-06-08 | AutoMegaKernel: A Statically-Checked Agent Harness for Self-Retargeting Megakernel Synthesis | Jaber Jaber, Osama Jaber |
| [2606.08960](https://arxiv.org/abs/2606.08960) | 2026-06-08 | Hardening Agent Benchmarks with Adversarial Hacker-Fixer Loops | Ziqian Zhong, Ivgeni Segal, Ivan Bercovich, Shashwat Saxena 외 2인 |
| [2606.10106](https://arxiv.org/abs/2606.10106) | 2026-06-08 | What makes a harness a harness: necessary and sufficient conditions for an agent harness | Sanderson Oliveira de Macedo |
| [2606.09498](https://arxiv.org/abs/2606.09498) | 2026-06-08 | Self-Harness: Harnesses That Improve Themselves | Hangfan Zhang, Shao Zhang, Kangcong Li, Chen Zhang 외 4인 |
| [2606.10209](https://arxiv.org/abs/2606.10209) | 2026-06-08 | Less Context, Better Agents: Efficient Context Engineering for Long-Horizon Tool-Using LLM Agents | Abhilasha Lodha, Mahsa Pahlavikhah Varnosfaderani, Abir Chakraborty, Abhinav Mithal |
| [2606.11686](https://arxiv.org/abs/2606.11686) | 2026-06-10 | Layer-Isolated Evaluation: Gating the Deterministic Scaffold of a Production LLM Agent with a No-LLM, Regression-Locked Test Harness | Sawyer Zhang, Alexander Wang, Sophie Lei |
| [2606.12344](https://arxiv.org/abs/2606.12344) | 2026-06-10 | Claw-SWE-Bench: A Benchmark for Evaluating OpenClaw-style Agent Harnesses on Coding Tasks | Mengyu Zheng, Kai Han, Boxun Li, Haiyang Xu 외 12인 |
| [2606.11869](https://arxiv.org/abs/2606.11869) | 2026-06-10 | Agents All the Way Down; A Methodology for Building Custom AI Agents from Substrate to Production | Marc Alier Forment, Juanan Pereira, Francisco José García-Peñalvo, María José Casañ Guerrero |
| [2606.13643](https://arxiv.org/abs/2606.13643) | 2026-06-11 | Recursive Agent Harnesses | Elias Lumer, Sahil Sen, Kevin Paul, Vamse Kumar Subbiah |
| [2606.13598](https://arxiv.org/abs/2606.13598) | 2026-06-11 | Reward Modeling for Multi-Agent Orchestration | King Yeung Tsang, Zihao Zhao, Vishal Venkataramani, Haizhou Shi 외 4인 |
| [2606.12882](https://arxiv.org/abs/2606.12882) | 2026-06-11 | HarnessBridge: Learnable Bidirectional Controller for LLM Agent Harness | Xiaoxuan Wang, Haixin Wang, Alexander Taylor, Jason Cong 외 2인 |
| [2606.13608](https://arxiv.org/abs/2606.13608) | 2026-06-11 | AgentBeats: Agentifying Agent Assessment for Openness, Standardization, and Reproducibility | Xiaoyuan Liu, Jianhong Tu, Yuqi Chen, Siyuan Xie 외 25인 |
| [2606.13733](https://arxiv.org/abs/2606.13733) | 2026-06-11 | How Task Structure Limits Multi-Agent Success: An Information-Theoretic Analysis | Shi Pan, Ming Luo |
| [2606.14066](https://arxiv.org/abs/2606.14066) | 2026-06-12 | FastContext: Training Efficient Repository Explorer for Coding Agents | Shaoqiu Zhang, Maoquan Wang, Yuling Shi, Yuhang Wang 외 11인 |
| [2606.14832](https://arxiv.org/abs/2606.14832) | 2026-06-12 | PhoneHarness: Harnessing Phone-Use Agents through Mixed GUI, CLI, and Tool Actions | Chenxin Li, Zhengyao Fang, Zhengyang Tang, Pengyuan Lyu 외 17인 |
| [2606.14249](https://arxiv.org/abs/2606.14249) | 2026-06-12 | HarnessX: A Composable, Adaptive, and Evolvable Agent Harness Foundry | Tingyang Chen, Shuo Lu, Kang Zhao, Weicheng Meng 외 10인 |
| [2606.14674](https://arxiv.org/abs/2606.14674) | 2026-06-12 | AgentSpec: Understanding Embodied Agent Scaffolds Through Controlled Composition | Jixuan Chen, Jianzhi Shen, Haoqiang Kang, Zhi Hong 외 9인 |
| [2606.19380](https://arxiv.org/abs/2606.19380) | 2026-06-13 | ClayBuddy: A Framework, Evaluation, & Mitigation of Coding Agent Failures | Kenneth Ge, Andre Assis |
| [2606.15363](https://arxiv.org/abs/2606.15363) | 2026-06-13 | APEX: Adaptive Principle EXtraction A Three-Layer Self-Evolution Framework for Production AI Agents | Ya-Chuan Chen, Tien-Jen Lai, Hsiang-Wei Hu |
| [2606.15903](https://arxiv.org/abs/2606.15903) | 2026-06-14 | Control-Plane Placement Shapes Forgetting: An Architectural Study of Agent Memory Across Thirteen System Configurations | Dongxu Yang |
| [2606.20683](https://arxiv.org/abs/2606.20683) | 2026-06-14 | From Question Answering to Task Completion: A Survey on Agent System and Harness Design | Jianyuan Guo, Zhiwei Hao, Chengcheng Wang, Cheng Fan 외 13인 |
| [2606.15874](https://arxiv.org/abs/2606.15874) | 2026-06-14 | LLM-as-Code: Agentic Programming for Agent Harness | Junjia Qi, Zichuan Fu, Jingtong Gao, Wenlin Zhang 외 3인 |
| [2606.17016](https://arxiv.org/abs/2606.17016) | 2026-06-15 | TokenPilot: Cache-Efficient Context Management for LLM Agents | Buqiang Xu, Zirui Xue, Dianmou Chen, Chenyang Fu 외 11인 |
| [2606.16591](https://arxiv.org/abs/2606.16591) | 2026-06-15 | SING: Synthetic Intention Graph for Scalable Active Tool Discovery in LLM Agents | Qiao Xiao, Haochen Shi, Yisen Gao, Wenbin Hu 외 8인 |
| [2606.24598](https://arxiv.org/abs/2606.24598) | 2026-06-15 | Toward Self-Evolution-Ready Workflow Harnesses: A Reversible Migration Path and Convertibility Taxonomy for Expert LLM Pipelines | Yimo Lin, Zhen Zhang, Yibin Li |
| [2606.17454](https://arxiv.org/abs/2606.17454) | 2026-06-16 | Dissecting model behavior through agent trajectories | Gaurav Gupta, Vatshank Chaturvedi, Jun Huan, Anoop Deoras |
| [2606.17546](https://arxiv.org/abs/2606.17546) | 2026-06-16 | SEAGym: An Evaluation Environment for Self-Evolving LLM Agents | Congjie Zheng, Chuanyi Xue, Bin Liang, Jun Yang 외 1인 |
| [2606.17799](https://arxiv.org/abs/2606.17799) | 2026-06-16 | Position: Coding Benchmarks Are Misaligned with Agentic Software Engineering | Maria I. Gorinova, Macey Baker, Amy Heineike, Maksim Shaposhnikov 외 2인 |
| [2606.19409](https://arxiv.org/abs/2606.19409) | 2026-06-17 | OpenRath: Session-Centered Runtime State for Agent Systems | Fukang Wen, Zhijie Wang, Ruilin Xu |
| [2606.19613](https://arxiv.org/abs/2606.19613) | 2026-06-17 | StaminaBench: Stress-Testing Coding Agents over 100 Interaction Turns | Vlad Sobal, Shuo Yang, Yuting Zhang, Wei Xia 외 1인 |
| [2606.21005](https://arxiv.org/abs/2606.21005) | 2026-06-19 | Building Agent Harnesses for Scientific Curation from Multimodal Sources | Sheng Zhang, Qin Liu, Renqian Luo, Shufang Xie 외 8인 |
| [2606.21228](https://arxiv.org/abs/2606.21228) | 2026-06-19 | Sakana Fugu Technical Report | Yujin Tang, Edoardo Cetin, Jinglue Xu, Qi Sun 외 10인 |
| [2606.21856](https://arxiv.org/abs/2606.21856) | 2026-06-20 | Harness-MU: A Safe, Governed, and Effective Harness for Multi-User LLM Agents | Wangxuan Fan, Xiaoyu Nie, Zhongxiang Dai |
| [2606.22678](https://arxiv.org/abs/2606.22678) | 2026-06-21 | RigorBench: Benchmarking Engineering Process Discipline in Autonomous AI Coding Agents | Meher Bhaskar Madiraju, Meher Sai Preetam Madiraju |
| [2606.22528](https://arxiv.org/abs/2606.22528) | 2026-06-21 | Governance Decay: How Context Compaction Silently Erases Safety Constraints in Long-Horizon LLM Agents | Shiyang Chen |
| [2606.24937](https://arxiv.org/abs/2606.24937) | 2026-06-22 | The Hitchhiker's Guide to Agentic AI: From Foundations to Systems | Haggai Roitman |
| [2606.23449](https://arxiv.org/abs/2606.23449) | 2026-06-22 | AOHP: An Open-Source OS-Level Agent Harness for Personalized, Efficient and Secure Interaction | Shanhui Zhao, Jiacheng Liu, Guohong Liu, Jichao Yan 외 12인 |
| [2606.22953](https://arxiv.org/abs/2606.22953) | 2026-06-22 | Plans Don't Persist: Why Context Management Is Load Bearing for LLM Agents | Aman Mehta, Anupam Datta |
| [2606.24311](https://arxiv.org/abs/2606.24311) | 2026-06-23 | LemonHarness Technical Report | Kailong Ren, Fubo Sun, Jiachen Liu, Liu Yang 외 17인 |
| [2606.25189](https://arxiv.org/abs/2606.25189) | 2026-06-23 | ActPlane: Programmable OS-Level Policy Enforcement for Agent Harnesses | Yusheng Zheng, Tianyuan Wu, Quanzhi Fu, Tong Yu 외 4인 |
| [2606.24775](https://arxiv.org/abs/2606.24775) | 2026-06-23 | Are We Ready For An Agent-Native Memory System? | Wei Zhou, Xuanhe Zhou, Shaokun Han, Hongming Xu 외 4인 |
| [2606.24535](https://arxiv.org/abs/2606.24535) | 2026-06-23 | Governed Shared Memory for Multi-Agent LLM Systems | Yanki Margalit, Nurit Cohen-Inger, Erni Avram, Ran Taig 외 1인 |
| [2606.25447](https://arxiv.org/abs/2606.25447) | 2026-06-24 | The Interplay of Harness Design and Post-Training in LLM Agents | Kyungmin Kim, Youngbin Choi, Seoyeon Lee, Suhyeon Jun 외 2인 |
| [2606.25514](https://arxiv.org/abs/2606.25514) | 2026-06-24 | Unlocking Model Potentials Through Adaptive Multi-Agent Scaffolding for Efficient Issue Resolution | Yang Chen, Aliya Ahmad, Yiheng Zhou, Reyhaneh Jabbarvand |
| [2606.27492](https://arxiv.org/abs/2606.27492) | 2026-06-25 | QueenBee Planner: Skill-Evolving Communication Topologies for Token-Efficient LLM Multi-Agent Systems | Congjia Tian, Yuhang Yao, Jiaming Cui |
| [2606.27243](https://arxiv.org/abs/2606.27243) | 2026-06-25 | NOVA: A Verification-Aware Agent Harness for Architecture Evolution in Industrial Recommender Systems | Shaohua Liu, Liang Fang, Yilong Sun, Shudong Huang 외 15인 |
| [2606.26859](https://arxiv.org/abs/2606.26859) | 2026-06-25 | AgentX: Towards Agent-Driven Self-Iteration of Industrial Recommender Systems | Changxin Lao, Fei Pan, Guozhuang Ma, Han Li 외 58인 |
| [2606.27188](https://arxiv.org/abs/2606.27188) | 2026-06-25 | A Process Harness for Uplifting Legacy Workflows to Agentic BPM: Design and Realization in CUGA FLO | Fabiana Fournier, Lior Limonad |
| [2606.28436](https://arxiv.org/abs/2606.28436) | 2026-06-26 | Dockerless: Environment-Free Program Verifier for Coding Agents | Wenhao Zeng, Yuling Shi, Xiaodong Gu, Chao Hu 외 9인 |
| [2606.28434](https://arxiv.org/abs/2606.28434) | 2026-06-26 | SWE-MeM: Learning Adaptive Memory Management for Long-Horizon Coding Agents | Shuzheng Gao, Wenhao Zeng, Zhaojian Yu, Jianqiao Wangni 외 4인 |
| [2606.29116](https://arxiv.org/abs/2606.29116) | 2026-06-27 | Characterizing Large Language Model Agentic Workflows: A Study on N8n Ecosystem | Yutian Tang, Yuming Zhou, Huaming Chen |
| [2606.28679](https://arxiv.org/abs/2606.28679) | 2026-06-27 | Capability Gates Are Not Authorization: Confused-Deputy Failures in LLM Agent Frameworks | David Mellafe Zuvic |
| [2606.30005](https://arxiv.org/abs/2606.30005) | 2026-06-29 | LLM Agents Are Latent Context Managers: Eliciting Self-Managed Context via a Proprioceptive Dashboard | Binyan Xu, Haitao Li, Kehuan Zhang |
| [2606.29914](https://arxiv.org/abs/2606.29914) | 2026-06-29 | MemDelta: Controlled Baselines and Hidden Confounds in Agent Memory Evaluation | Kuan Wang |
| [2606.30317](https://arxiv.org/abs/2606.30317) | 2026-06-29 | MCP Server Architecture Patterns for LLM-Integrated Applications | Carson Rodrigues, Oysturn Vas |
| [2606.30546](https://arxiv.org/abs/2606.30546) | 2026-06-29 | MAS-Lab: A Specification-Driven Validation Framework for Reliable Multi-Agent Systems | Jordan Augé, Giovanna Carofiglio, Giulio Grassi, Jacques Samain |
| [2606.31174](https://arxiv.org/abs/2606.31174) | 2026-06-30 | ClawArena-Team: Benchmarking Subagent Orchestration and Dynamic Workflows in Language-Model Agents | Kaiwen Xiong, Haonian Ji, Shi Qiu, Zeyu Zheng 외 3인 |
| [2606.31564](https://arxiv.org/abs/2606.31564) | 2026-06-30 | ACE: Pluggable Adaptive Context Elasticizer across Agents | Ning Liao, Zihao Long, Xiaoxing Wang, Xue Yang 외 5인 |

## OUT-OF-RANGE — arXiv (실존 확인, 범위 밖 → 부록/배경 전용)

| arXiv ID | 제출일 | 제목 | 저자 |
|---|---|---|---|
| [2507.13334](https://arxiv.org/abs/2507.13334) | 2025-07-17 | A Survey of Context Engineering for Large Language Models | Lingrui Mei, Jiayu Yao, Yuyao Ge, Yiwei Wang 외 11인 |
| [2601.11868](https://arxiv.org/abs/2601.11868) | 2026-01-17 | Terminal-Bench: Benchmarking Agents on Hard, Realistic Tasks in Command Line Interfaces | Mike A. Merrill, Alexander G. Shaw, Nicholas Carlini, Boxuan Li 외 81인 |
| [2603.22862](https://arxiv.org/abs/2603.22862) | 2026-03-24 | The Evolution of Tool Use in LLM Agents: From Single-Tool Call to Multi-Tool Orchestration | Haoyuan Xu, Chang Li, Xinyan Ma, Xianhao Ou 외 11인 |
| [2603.24709](https://arxiv.org/abs/2603.24709) | 2026-03-25 | Training LLMs for Multi-Step Tool Orchestration with Constrained Data Synthesis and Graduated Rewards | Cheng Jiayang, Xin Liu, Zhihan Zhang, Haoyang Wen 외 7인 |
| [2603.29231](https://arxiv.org/abs/2603.29231) | 2026-03-31 | Beyond pass@1: A Reliability Science Framework for Long-Horizon LLM Agents | Aaditya Khanal, Yangyang Tao, Junxiu Zhou |
| [2604.03515](https://arxiv.org/abs/2604.03515) | 2026-04-03 | Inside the Scaffold: A Source-Code Taxonomy of Coding Agent Architectures | Benjamin Rombaut |
| [2604.11548](https://arxiv.org/abs/2604.11548) | 2026-04-13 | SemaClaw: A Step Towards General-Purpose Personal AI Agents through Harness Engineering | Ningyan Zhu, Huacan Wang, Jie Zhou, Feiyu Chen 외 7인 |
| [2604.21003](https://arxiv.org/abs/2604.21003) | 2026-04-22 | The Last Harness You'll Ever Build | Haebin Seong, Li Yin, Haoran Zhang, Zhan Shi |
| [2604.25850](https://arxiv.org/abs/2604.25850) | 2026-04-28 | Agentic Harness Engineering: Observability-Driven Automatic Evolution of Coding-Agent Harnesses | Jiahang Lin, Shichun Liu, Chengjun Pan, Lizhi Lin 외 7인 |
## CONFIRMED — 블로그/기술 리포트 (HTTP 실존 확인)

| 출처 | 날짜 | 제목 | URL | 상태 |
|---|---|---|---|---|
| Anthropic Eng | 2026-05-25 | How we contain Claude across products | https://www.anthropic.com/engineering/how-we-contain-claude | 200 ✔ |
| claude.com | 2026-05-19 | New in Claude Managed Agents: dreaming, outcomes, multiagent orchestration | https://claude.com/blog/new-in-claude-managed-agents | 200 ✔ |
| claude.com | 2026-05-19 | Managed Agents: self-hosted sandboxes and MCP tunnels | https://claude.com/blog/claude-managed-agents-updates | 200 ✔ |
| claude.com | 2026-06-09 | Managed Agents: schedule + env var vaults | https://claude.com/blog/whats-new-in-claude-managed-agents | 200 ✔ |
| claude.com | 2026-06-10 | The evolution of agentic surfaces: building with Claude Managed Agents | https://claude.com/blog/building-with-claude-managed-agents | 200 ✔ |
| claude.com | 2026-06-18 | Steering Claude Code: CLAUDE.md, skills, hooks, rules, subagents | https://claude.com/blog/steering-claude-code-skills-hooks-rules-subagents-and-more | 200 ✔ |
| claude.com | 2026-06-24 | Agent identity in Claude Tag: access model for team-wide AI | https://claude.com/blog/agent-identity-access-model | 200 ✔ |
| Cognition | 2026-06-29 | Devin Fusion: Frontier Performance at 35% Lower Cost | https://cognition.com/blog/devin-fusion | 200 ✔ |
| Google DeepMind | 2026-05-19 | Co-Scientist: a multi-agent AI partner to accelerate research | https://deepmind.google/blog/co-scientist-a-multi-agent-ai-partner-to-accelerate-research/ | 200 ✔ |
| Google DeepMind | 2026-06 | Investing in multi-agent AI safety research | https://deepmind.google/blog/investing-in-multi-agent-ai-safety-research/ | 200 ✔ |
| OpenAI devs | 2026-06~07 | OpenAI Codex Changelog | https://developers.openai.com/codex/changelog | 200 ✔ |

## OUT-OF-RANGE / 배경 — 블로그·리포트 (실존 확인, 범위 밖)

| 출처 | 날짜 | 제목 | URL | 상태 |
|---|---|---|---|---|
| OpenAI | 2026-02-11 | Harness engineering: leveraging Codex in an agent-first world | https://openai.com/index/harness-engineering/ | 403 (봇차단) — 2차 InfoQ 200✔로 교차확인 |
| InfoQ (2차) | 2026-02-21 | OpenAI Details Harness Engineering (커버리지) | https://www.infoq.com/news/2026/02/openai-harness-engineering-codex/ | 200 ✔ |
| Anthropic Eng | 2026-03-24 | Harness design for long-running application development | https://www.anthropic.com/engineering/harness-design-long-running-apps | 200 ✔ |
| Anthropic Eng | 2026-04-08 | Scaling Managed Agents: Decoupling the brain from the hands | https://www.anthropic.com/engineering/managed-agents | 200 ✔ |
| Anthropic Eng | 2026-03-25 | How we built Claude Code auto mode | https://www.anthropic.com/engineering/claude-code-auto-mode | 200 ✔ |
| Anthropic Eng | 2026-02-05 | Building a C compiler with a team of parallel Claudes | https://www.anthropic.com/engineering/building-c-compiler | 200 ✔ |
| Anthropic | 2026-01-21 | 2026 Agentic Coding Trends Report | https://resources.anthropic.com/2026-agentic-coding-trends-report | 200 ✔ |
| tbench.ai | (live) | Terminal-Bench Leaderboard | https://www.tbench.ai/leaderboard | 200 ✔ |

## 검증자 노트
- **환각 0건**: 95개 arXiv ID 전부 raw API에서 실존·제목·날짜 일치. "LemonHarness"·"Claw-SWE-Bench"·"MemClaw(Governed Shared Memory)"처럼 의심스러운 코드네임도 모두 실존.
- **arXiv YYMM 규칙**: 2026년 ID는 `26MM.xxxxx` (2605=5월, 2606=6월, 2607=7월). 2507.13334은 2025-07 논문(context engineering 서베이)으로 범위 밖 → OUT.
- **7월(2607) 희소**: 현재일 2026-07-01 기준 2607 논문은 사실상 아직 없음. 이는 정상이며 패딩하지 않음.
- **본문 인용 게이트**: CONFIRMED 목록(arXiv IN 86건 + 블로그 11건)만 리포트 본문 인용 허용. OUT은 배경/부록 전용.

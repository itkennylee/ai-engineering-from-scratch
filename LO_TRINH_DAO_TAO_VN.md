# Lộ Trình Đào Tạo AI Engineering From Scratch — Bản Tiếng Việt

> Tài liệu này tổng hợp toàn bộ chương trình đào tạo **AI Engineering from Scratch**:
> **20 phase · 435 bài học · ~314 giờ học · 4 ngôn ngữ lập trình (Python, TypeScript, Rust, Julia)**.
> Mỗi bài học đều xuất ra một artifact tái sử dụng được: prompt, skill, agent hoặc MCP server.

---

## Mục lục

1. [Triết lý đào tạo](#1-triết-lý-đào-tạo)
2. [Cấu trúc một bài học](#2-cấu-trúc-một-bài-học)
3. [Bản đồ phụ thuộc giữa các phase](#3-bản-đồ-phụ-thuộc-giữa-các-phase)
4. [Lộ trình chi tiết 20 phase](#4-lộ-trình-chi-tiết-20-phase)
5. [Lộ trình cá nhân hóa theo trình độ](#5-lộ-trình-cá-nhân-hóa-theo-trình-độ)
6. [Phương pháp học hiệu quả](#6-phương-pháp-học-hiệu-quả)
7. [Bộ artifact thực dụng](#7-bộ-artifact-thực-dụng)
8. [Hướng dẫn bắt đầu](#8-hướng-dẫn-bắt-đầu)
9. [Tài nguyên tham khảo](#9-tài-nguyên-tham-khảo)

---

## 1. Triết lý đào tạo

### Vấn đề mà chương trình giải quyết

> **84% học viên đã sử dụng công cụ AI, nhưng chỉ 18% cảm thấy đủ tự tin để dùng AI ở mức chuyên nghiệp.**
> Chương trình này lấp đầy khoảng trống đó.

Hầu hết tài liệu AI hiện nay rời rạc: một bài báo ở đây, một bài viết về fine-tuning ở kia, vài demo agent hào nhoáng ở nơi khác. Các mảnh ghép hiếm khi ăn khớp. Bạn ship được chatbot nhưng không giải thích được loss curve. Bạn gắn function vào agent nhưng không nói được attention làm gì bên trong model đang gọi nó.

### Nguyên tắc cốt lõi

| Nguyên tắc | Diễn giải |
|---|---|
| **Học theo "xương sống"** | 20 phase xếp chồng tuyến tính: toán học ở nền, agent + production ở mái. |
| **Tự tay viết toán trước, dùng framework sau** | Backprop, tokenizer, attention, agent loop — đều code bằng math thô trước, rồi mới chạy bằng PyTorch / sklearn. |
| **Mỗi bài ship một artifact** | Không phải bài tập về nhà — là prompt, skill, agent, MCP server cài được vào workflow thật. |
| **Free, MIT, open source** | Chạy được trên laptop của bạn. Không cần GPU đắt tiền cho phần lớn bài học. |
| **Không xem video 5 phút** | Đọc vấn đề → derive math → viết code → chạy test → giữ artifact. |

### Lời chứng

> *"The hottest new programming language is English."* — **Andrej Karpathy**
> *"Software engineering is being remade in front of our eyes."* — **Boris Cherny**, người tạo Claude Code
> *"Model sẽ ngày càng tốt. Kỹ năng compound chính là **biết nên build cái gì**."* — Industry consensus, 2026

---

## 2. Cấu trúc một bài học

Mỗi bài học sống trong một thư mục riêng với cùng cấu trúc xuyên suốt toàn chương trình:

```
phases/<NN>-<phase-name>/<NN>-<lesson-name>/
├── code/      Mã nguồn chạy được (Python, TypeScript, Rust, Julia)
├── docs/
│   └── en.md  Nội dung lý thuyết của bài học
└── outputs/   Artifact: prompt, skill, agent, hoặc MCP server
```

### Sáu nhịp của một bài học

```
MOTTO  →  PROBLEM  →  CONCEPT  →  BUILD IT  →  USE IT  →  SHIP IT
```

| Nhịp | Mục đích |
|---|---|
| **MOTTO** | Câu thần chú một dòng — ý niệm cốt lõi của bài. |
| **PROBLEM** | Vấn đề cụ thể, có thật, gây đau — lý do bài học tồn tại. |
| **CONCEPT** | Sơ đồ + trực giác — giải thích "tại sao" trước "như thế nào". |
| **BUILD IT** | Tự code thuật toán bằng math thô, không framework. |
| **USE IT** | Cùng thuật toán đó nhưng chạy bằng PyTorch / sklearn — hiểu framework đang làm gì vì bạn vừa viết phiên bản nhỏ hơn. |
| **SHIP IT** | Đóng gói thành prompt, skill, agent hoặc MCP server tái sử dụng. |

---

## 3. Bản đồ phụ thuộc giữa các phase

```
P0 — Setup & Tooling
   │
P1 — Math Foundations
   │
P2 — ML Fundamentals
   │
P3 — Deep Learning Core
   ├──► P4 — Computer Vision
   ├──► P5 — NLP ────► P7 — Transformers ────► P8 — Generative AI
   ├──► P6 — Speech                │
   └──► P9 — Reinforcement Learning │
                                   │
                  P10 — LLMs from Scratch
                          │
                          ├──► P11 — LLM Engineering ──► P13 — Tools & Protocols
                          │                                       │
                          └──► P12 — Multimodal AI                P14 — Agent Engineering
                                                                   │
                                       ┌───────────────────────────┼─────────────────────┐
                                       │                           │                     │
                              P15 — Autonomous Systems   P17 — Infrastructure   (chia nhánh)
                                       │                           │
                              P16 — Multi-Agent & Swarms   P18 — Ethics & Safety
                                       │                           │
                                       └──────────►  P19 — Capstone Projects  ◄───────────┘
```

**Quy tắc:** Có thể bỏ qua các phase phía dưới nếu đã thành thạo. Nhưng đừng bỏ qua rồi phàn nàn rằng phase phía trên đang vỡ.

---

## 4. Lộ trình chi tiết 20 phase

### Phase 0 — Setup & Tooling · 12 bài · ~14 giờ
> *Chuẩn bị môi trường cho mọi thứ phía sau.*

Dev Environment · Git & Collaboration · GPU Setup & Cloud · APIs & Keys · Jupyter Notebooks · Python Environments · Docker for AI · Editor Setup · Data Management · Terminal & Shell · Linux for AI · Debugging & Profiling

---

### Phase 1 — Math Foundations · 22 bài · ~23 giờ
> *Trực giác đằng sau mọi thuật toán AI — qua code.*

Linear Algebra Intuition · Vectors, Matrices & Operations · Matrix Transformations & Eigenvalues · Calculus for ML · Chain Rule & Autodiff · Probability & Distributions · Bayes' Theorem · Gradient Descent Family · Information Theory (Entropy, KL) · Dimensionality Reduction (PCA, t-SNE, UMAP) · SVD · Tensor Operations · Numerical Stability · Norms & Distances · Statistics for ML · Sampling Methods · Linear Systems · Convex Optimization · Complex Numbers · Fourier Transform · Graph Theory · Stochastic Processes

---

### Phase 2 — ML Fundamentals · 18 bài · ~21 giờ
> *ML cổ điển — vẫn là xương sống của phần lớn AI production.*

What Is ML · Linear Regression from Scratch · Logistic Regression · Decision Trees & Random Forests · SVM · KNN & Distance Metrics · K-Means, DBSCAN · Feature Engineering · Model Evaluation · Bias & Variance · Ensembles (Boosting, Bagging, Stacking) · Hyperparameter Tuning · ML Pipelines & Experiment Tracking · Naive Bayes · Time Series · Anomaly Detection · Imbalanced Data · Feature Selection

---

### Phase 3 — Deep Learning Core · 13 bài · ~15 giờ
> *Mạng neuron từ first principles. Không framework cho đến khi bạn tự viết một cái.*

The Perceptron · Multi-Layer Networks · **Backpropagation from Scratch** · Activation Functions (ReLU, Sigmoid, GELU) · Loss Functions (MSE, Cross-Entropy, Contrastive) · Optimizers (SGD, Momentum, Adam, AdamW) · Regularization (Dropout, Weight Decay, BatchNorm) · Weight Initialization · Learning Rate Schedules · **Build Your Own Mini Framework** · Intro to PyTorch · Intro to JAX · Debugging Neural Networks

---

### Phase 4 — Computer Vision · 28 bài · ~27 giờ
> *Từ pixel đến hiểu biết — image, video, 3D, VLM và world model.*

Image Fundamentals · Convolutions from Scratch · CNNs (LeNet → ResNet) · Image Classification · Transfer Learning · **YOLO from Scratch** · U-Net (Semantic Segmentation) · Mask R-CNN · GANs · Diffusion Models · Stable Diffusion · Video Understanding · 3D Vision (Point Clouds, NeRFs) · ViT · Real-Time Edge · Vision Pipeline (capstone) · SimCLR/DINO/MAE · CLIP · OCR · Image Retrieval · Pose Estimation · 3D Gaussian Splatting · Diffusion Transformers & Rectified Flow · SAM 3 · Vision-Language Models · Monocular Depth · Multi-Object Tracking · World Models & Video Diffusion

---

### Phase 5 — NLP: Foundations to Advanced · 29 bài · ~30 giờ
> *Ngôn ngữ là giao diện đến trí tuệ.*

Text Processing · BoW & TF-IDF · **Word2Vec from Scratch** · GloVe / FastText · Sentiment Analysis · NER · POS Tagging · CNNs/RNNs for Text · Seq2Seq · **Attention Mechanism** · Machine Translation · Summarization · Question Answering · Information Retrieval · Topic Modeling · Text Generation (pre-Transformer) · Chatbots · Multilingual NLP · Subword Tokenization (BPE, WordPiece, Unigram, SentencePiece) · Structured Outputs · NLI · Embedding Models Deep Dive · Chunking for RAG · Coreference Resolution · Entity Linking · Relation Extraction & KG · LLM Eval (RAGAS, DeepEval, G-Eval) · Long-Context Eval (NIAH, RULER, LongBench, MRCR) · Dialogue State Tracking

---

### Phase 6 — Speech & Audio · 17 bài · ~18 giờ
> *Nghe, hiểu, nói.*

Audio Fundamentals · Spectrograms & Mel Features · Audio Classification · ASR · **Whisper Architecture** · Speaker Verification · TTS · Voice Cloning · Music Generation · Audio-Language Models · Real-Time Audio (Python/Rust) · **Voice Assistant Pipeline** · Neural Audio Codecs (EnCodec, SNAC, Mimi, DAC) · VAD & Turn-Taking · Streaming Speech-to-Speech (Moshi, Hibiki) · Anti-Spoofing & Watermarking · Audio Evaluation (WER, MOS, MMAU)

---

### Phase 7 — Transformers Deep Dive · 14 bài · ~14 giờ
> *Kiến trúc đã thay đổi mọi thứ.*

Why Transformers · **Self-Attention from Scratch** · Multi-Head Attention · Positional Encoding (Sinusoidal, RoPE, ALiBi) · Full Transformer (Encoder + Decoder) · BERT · GPT · T5/BART · ViT · Audio Transformers (Whisper) · Mixture of Experts · KV Cache & Flash Attention · Scaling Laws · **Build a Transformer (capstone)**

---

### Phase 8 — Generative AI · 14 bài
> *Tạo image, video, audio, 3D, và nhiều hơn nữa.*

Generative Taxonomy · Autoencoders & VAE · GANs · Conditional GANs (Pix2Pix) · StyleGAN · **DDPM from Scratch** · Latent Diffusion & Stable Diffusion · ControlNet & LoRA · Inpainting/Outpainting · Video Generation · Audio Generation · 3D Generation · Flow Matching & Rectified Flows · Evaluation (FID, CLIP Score)

---

### Phase 9 — Reinforcement Learning · 12 bài
> *Nền móng của RLHF và game-playing AI.*

MDPs · Dynamic Programming · Monte Carlo · Q-Learning, SARSA · DQN · REINFORCE · A2C, A3C · **PPO** · **Reward Modeling & RLHF** · Multi-Agent RL · Sim-to-Real · RL for Games

---

### Phase 10 — LLMs from Scratch · 22 bài · ~30 giờ
> *Build, train, và hiểu large language models.*

Tokenizers (BPE, WordPiece, SentencePiece) · **Building a Tokenizer from Scratch** · Data Pipelines for Pre-Training · **Pre-Training Mini GPT (124M)** · Distributed Training (FSDP, DeepSpeed) · Instruction Tuning (SFT) · **RLHF (Reward Model + PPO)** · **DPO** · Constitutional AI · Evaluation · Quantization (INT8, GPTQ, AWQ, GGUF) · Inference Optimization · Complete LLM Pipeline · Open Model Walkthroughs · **Speculative Decoding & EAGLE-3** · Differential Attention V2 · Native Sparse Attention (DeepSeek NSA) · Multi-Token Prediction (MTP) · DualPipe Parallelism · DeepSeek-V3 Walkthrough · Jamba (Hybrid SSM-Transformer) · Async & Hogwild! Inference

---

### Phase 11 — LLM Engineering · 17 bài
> *Đưa LLM vào production.*

Prompt Engineering · Few-Shot, CoT, Tree-of-Thought · Structured Outputs · Embeddings · **Context Engineering** · **RAG** · Advanced RAG (Chunking, Reranking) · LoRA & QLoRA Fine-Tuning · Function Calling · Evaluation & Testing · Caching & Cost · Guardrails & Safety · Production LLM App · **Model Context Protocol (MCP)** · Prompt Caching · LangGraph (State Machines) · Agent Framework Tradeoffs

---

### Phase 12 — Multimodal AI · 25 bài
> *Nhìn, nghe, đọc và lý luận xuyên modality — từ ViT đến computer-use agent.*

ViT Patch Tokens · CLIP · BLIP-2 Q-Former · Flamingo (Gated Cross-Attention) · LLaVA · Any-Resolution (Patch-n'-Pack, NaFlex) · Open-Weight VLM Recipes · LLaVA-OneVision · Qwen-VL · InternVL3 · Chameleon (Early-Fusion Token) · Emu3 · Transfusion (AR + Diffusion) · Show-o · Janus-Pro · MIO (Any-to-Any Streaming) · Video Temporal Grounding · Long-Video Million-Token · Audio-Language (Whisper → AF3) · Omni Models (Thinker-Talker) · Embodied VLAs (RT-2, OpenVLA, π0, GR00T) · Document Understanding · ColPali Vision-Native RAG · Multimodal RAG · **Multimodal Agents & Computer-Use (capstone)**

---

### Phase 13 — Tools & Protocols · 23 bài
> *Giao diện giữa AI và thế giới thật.*

The Tool Interface · Function Calling Deep Dive · Parallel & Streaming Tool Calls · Structured Output · Tool Schema Design · **MCP Fundamentals** · **Building MCP Server** · Building MCP Client · MCP Transports · MCP Resources & Prompts · MCP Sampling · MCP Roots & Elicitation · MCP Async Tasks · MCP Apps · MCP Security I (Tool Poisoning) · MCP Security II (OAuth 2.1) · MCP Gateways & Registries · MCP Auth in Production (DCR + JWKS) · **A2A Protocol** · OpenTelemetry GenAI · LLM Routing Layer · Skills & Agent SDKs · **Capstone — Tool Ecosystem**

---

### Phase 14 — Agent Engineering · 42 bài · ~60 giờ
> *Build agent từ first principles — loop, memory, planning, framework, benchmark, production, workbench.*

**Tier 1 — Cốt lõi (lessons 1–11):** The Agent Loop · ReWOO & Plan-and-Execute · Reflexion · Tree of Thoughts & LATS · Self-Refine & CRITIC · Tool Use · Memory (MemGPT) · Memory Blocks & Sleep-Time Compute · Hybrid Memory (Mem0) · Skill Libraries & Voyager · Planning (HTN, Evolutionary)

**Tier 2 — Framework (lessons 12–18):** Anthropic Workflow Patterns · LangGraph · AutoGen v0.4 · CrewAI · **OpenAI Agents SDK** · **Claude Agent SDK** · Agno & Mastra

**Tier 3 — Benchmark & Quan sát (lessons 19–24):** SWE-bench, GAIA, AgentBench · WebArena & OSWorld · Computer Use (Claude, OpenAI CUA, Gemini) · Voice Agents (Pipecat, LiveKit) · OpenTelemetry GenAI · Langfuse / Phoenix / Opik

**Tier 4 — Production & Workbench (lessons 25–42):** Multi-Agent Debate · Failure Modes · Prompt Injection & PVE Defense · Orchestration (Supervisor, Swarm, Hierarchical) · Production Runtimes · Eval-Driven Development · **Agent Workbench (12 bài 31–42)** — instructions as executable constraints, repo memory, init scripts, scope contracts, runtime feedback loops, verification gates, reviewer agent, multi-session handoff, real repo workbench, **Capstone: Ship a Reusable Workbench Pack**

---

### Phase 15 — Autonomous Systems · 22 bài
> *Agent dài hạn, tự cải thiện, và safety stack 2026.*

Long-Horizon Agents (METR) · STaR / V-STaR / Quiet-STaR · AlphaEvolve · Darwin Gödel Machine · AI Scientist v2 · Automated Alignment Research (Anthropic AAR) · Recursive Self-Improvement · Bounded Self-Improvement · Coding Agent Landscape (SWE-bench, CodeAct) · Claude Code Permission Modes · Browser Agents & Indirect Prompt Injection · Durable Execution · Cost Governors (Budget, Iteration Cap) · Kill Switches & Canary Tokens · HITL Propose-Then-Commit · Checkpoints & Rollback · Constitutional AI & Rule Overrides · Llama Guard · Anthropic RSP v3.0 · OpenAI Preparedness & DeepMind FSF · METR External Evaluation · CAIS, CAISI & Societal Risk

---

### Phase 16 — Multi-Agent & Swarms · 25 bài
> *Coordination, emergence, và collective intelligence.*

Why Multi-Agent · FIPA-ACL & Speech Acts · Communication Protocols · Primitive Model · **Supervisor / Orchestrator-Worker** · Hierarchical Architecture · Society of Mind & Debate · Role Specialization (Planner / Critic / Executor / Verifier) · Parallel Swarm & Networked · Group Chat & Speaker Selection · Handoffs & Routines · **A2A Protocol** · Blackboard Patterns · Consensus & Byzantine Fault Tolerance · Voting & Self-Consistency · Negotiation & Bargaining · Generative Agents (Emergent Simulation) · Theory of Mind · Swarm Optimization (PSO, ACO) · MARL (MADDPG, QMIX, MAPPO) · Agent Economies · Production Scaling (Queues, Checkpoints) · Failure Modes (MAST, Groupthink, Monoculture) · Evaluation Benchmarks · Case Studies — 2026 SOTA

---

### Phase 17 — Infrastructure & Production · 28 bài
> *Ship AI vào thế giới thực.*

Managed Platforms (Bedrock, Azure OpenAI, Vertex) · Inference Economics (Fireworks, Together, Baseten, Modal) · GPU Autoscaling on K8s (Karpenter, KAI) · **vLLM Internals (PagedAttention, Continuous Batching, Chunked Prefill)** · EAGLE-3 Speculative Decoding · SGLang & RadixAttention · TensorRT-LLM on Blackwell (FP8, NVFP4) · **Inference Metrics (TTFT, TPOT, ITL, Goodput, P99)** · Production Quantization · Cold Start Mitigation · Multi-Region Serving & KV Cache Locality · Edge Inference (ANE, Hexagon, WebGPU, Jetson) · Observability Stack Selection · Prompt & Semantic Caching Economics · Batch APIs (50% Discount) · Model Routing · Disaggregated Prefill/Decode (NVIDIA Dynamo, llm-d) · vLLM Production Stack (LMCache) · **AI Gateways (LiteLLM, Portkey, Kong, Bifrost)** · Shadow / Canary / Progressive Deployment · A/B Testing (GrowthBook, Statsig) · Load Testing (k6, LLMPerf, GenAI-Perf) · SRE for AI (Multi-Agent Incident Response) · Chaos Engineering · Security (Secrets, PII Scrubbing, Audit Logs) · Compliance (SOC 2, HIPAA, GDPR, EU AI Act, ISO 42001) · FinOps · Self-Hosted Serving Selection

---

### Phase 18 — Ethics, Safety & Alignment · 30 bài
> *Build AI giúp đỡ nhân loại. Không phải tùy chọn.*

Instruction-Following as Alignment Signal · Reward Hacking & Goodhart's Law · DPO Family · **Sycophancy as RLHF Amplification** · Constitutional AI & RLAIF · Mesa-Optimization & Deceptive Alignment · Sleeper Agents · In-Context Scheming · Alignment Faking · AI Control (Safety Despite Subversion) · Scalable Oversight & Weak-to-Strong · Red-Teaming (PAIR) · Many-Shot Jailbreaking · ASCII Art & Visual Jailbreaks · Indirect Prompt Injection · Red-Team Tooling (Garak, Llama Guard, PyRIT) · WMDP & Dual-Use Evaluation · Frontier Safety Frameworks (RSP, PF, FSF) · Model Welfare Research · Bias & Representational Harm · Fairness Criteria · Differential Privacy for LLMs · Watermarking (SynthID, Stable Signature, C2PA) · Regulatory Frameworks (EU, US, UK, Korea) · EchoLeak & CVEs for AI · Model / System / Dataset Cards · Data Provenance · Alignment Research Ecosystem (MATS, Redwood, Apollo, METR) · Moderation Systems · Dual-Use Risk (Cyber, Bio, Chem, Nuclear)

---

### Phase 19 — Capstone Projects · 17 dự án · 20–40 giờ mỗi dự án
> *Sản phẩm end-to-end 2026.*

| # | Dự án | Kết hợp phase | Ngôn ngữ |
|:--:|---|---|---|
| 01 | Terminal-Native Coding Agent | P0 P5 P7 P10 P11 P13 P14 P15 P17 P18 | TS, Py |
| 02 | RAG over Codebase (Cross-Repo Semantic Search) | P5 P7 P11 P13 P17 | Py, TS |
| 03 | Real-Time Voice Assistant (ASR→LLM→TTS) | P6 P7 P11 P13 P14 P17 | Py, TS |
| 04 | Multimodal Document QA (Vision-First) | P4 P5 P7 P11 P12 P17 | Py, TS |
| 05 | Autonomous Research Agent (AI-Scientist Class) | P0 P2 P3 P7 P10 P14 P15 P16 P18 | Py |
| 06 | DevOps Troubleshooting Agent for Kubernetes | P11 P13 P14 P15 P17 P18 | Py, TS |
| 07 | End-to-End Fine-Tuning Pipeline | P2 P3 P7 P10 P11 P17 P18 | Py |
| 08 | Production RAG Chatbot (Regulated Vertical) | P5 P7 P11 P12 P17 P18 | Py, TS |
| 09 | Code Migration Agent (Repo-Level Upgrade) | P5 P7 P11 P13 P14 P15 P17 | Py, TS |
| 10 | Multi-Agent Software Engineering Team | P11 P13 P14 P15 P16 P17 | Py, TS |
| 11 | LLM Observability & Eval Dashboard | P11 P13 P17 P18 | TS, Py |
| 12 | Video Understanding Pipeline (Scene→QA) | P4 P6 P7 P11 P12 P17 | Py, TS |
| 13 | MCP Server with Registry and Governance | P11 P13 P14 P17 P18 | Py, TS |
| 14 | Speculative-Decoding Inference Server | P3 P7 P10 P17 | Py |
| 15 | Constitutional Safety Harness + Red-Team Range | P10 P11 P13 P14 P18 | Py |
| 16 | GitHub Issue-to-PR Autonomous Agent | P11 P13 P14 P15 P17 | Py, TS |
| 17 | Personal AI Tutor (Adaptive, Multimodal) | P5 P6 P11 P12 P14 P17 P18 | Py, TS |

---

## 5. Lộ trình cá nhân hóa theo trình độ

| Nền tảng của bạn | Bắt đầu từ | Thời lượng ước tính |
|---|---|---|
| Mới với lập trình và AI | **Phase 0** — Setup | ~306 giờ |
| Biết Python, mới với ML | **Phase 1** — Math Foundations | ~270 giờ |
| Biết ML, mới với deep learning | **Phase 3** — Deep Learning Core | ~200 giờ |
| Biết deep learning, muốn LLM & agent | **Phase 10** — LLMs from Scratch | ~100 giờ |
| Senior engineer, chỉ muốn agent engineering | **Phase 14** — Agent Engineering | ~60 giờ |

### Bài kiểm tra phân loại

Trong Claude, Cursor, Codex hoặc bất kỳ agent nào đã cài skill của chương trình:

```bash
/find-your-level          # 10 câu hỏi, map kiến thức của bạn vào phase phù hợp
/check-understanding 3    # kiểm tra hiểu phase 3 bằng 8 câu trắc nghiệm
```

### Bốn nhánh học gợi ý

**🎯 Nhánh "Builder LLM" — ~6 tháng, ~24 giờ/tuần**
P0 → P1 → P2 → P3 → P5 → P7 → P10 → P11 → P19 (project 07, 14)

**🤖 Nhánh "Agent Engineer" — ~4 tháng, ~24 giờ/tuần**
P0 → (review P3, P7) → P11 → P13 → P14 → P15 → P16 → P19 (project 01, 10, 16)

**🏭 Nhánh "Production AI" — ~3 tháng, ~24 giờ/tuần**
P0 → P11 → P13 → P17 → P18 → P19 (project 06, 08, 11, 13)

**🎨 Nhánh "Multimodal Generative" — ~5 tháng, ~24 giờ/tuần**
P0 → P1 → P3 → P4 → P6 → P7 → P8 → P12 → P19 (project 03, 04, 12, 17)

---

## 6. Phương pháp học hiệu quả

### Quy tắc 6 nhịp khi học mỗi bài

1. **Đọc MOTTO + PROBLEM trước.** Hiểu vì sao bài này tồn tại — đừng vội nhảy vào code.
2. **Vẽ tay sơ đồ CONCEPT.** Tự tay vẽ luồng dữ liệu hoặc kiến trúc bằng giấy bút.
3. **BUILD IT từ math thô.** Đóng tab framework. Chỉ NumPy / pure Python. Phải tự đạo hàm.
4. **Đối chiếu với USE IT.** Cùng thuật toán, viết lại bằng PyTorch/sklearn. So sánh output.
5. **Đọc lại SHIP IT.** Đóng gói thành skill/prompt cài được vào agent của bạn.
6. **Làm `/check-understanding <phase>` sau mỗi phase.** 8 câu — sai 3+ thì học lại 2 bài liên quan.

### Sai lầm cần tránh

| ❌ Đừng | ✅ Hãy |
|---|---|
| Bỏ qua phase nền vì "đã biết rồi" | Làm bài `/find-your-level` trước. Đừng giả định. |
| Copy-paste code mà không chạy | Mỗi `code/` file phải chạy được trên máy bạn. |
| Học một mình toàn bộ 314h | Tham gia community, debug cùng người khác. |
| Dùng framework ngay từ đầu | "Build It" trước "Use It" — đây là spine của khóa học. |
| Skip phần "outputs/" | Đó là artifact thật bạn dùng được, không phải bài tập. |

### Lịch học gợi ý

- **Part-time (10h/tuần):** Hoàn thành 1 phase trung bình mỗi 2–3 tuần. Toàn bộ ~14 tháng.
- **Full-time (40h/tuần):** Hoàn thành 1 phase mỗi 4–7 ngày. Toàn bộ ~8–10 tuần.
- **Sprint cuối tuần:** 1 lesson/tuần. Toàn bộ ~8 năm — không khuyến khích, nhưng vẫn ra artifact.

---

## 7. Bộ artifact thực dụng

Toàn bộ chương trình xuất ra **378 skills + 99 prompts** dưới `phases/**/outputs/`.

### Cài đặt toàn bộ skill vào agent của bạn

```bash
python3 scripts/install_skills.py ~/.claude/skills          # mọi skill, layout nested
python3 scripts/install_skills.py ./out --type all          # skills + prompts + agents
python3 scripts/install_skills.py ./out --phase 14          # chỉ một phase
python3 scripts/install_skills.py ./out --tag rag           # lọc theo tag
python3 scripts/install_skills.py ./out --layout flat       # file phẳng
python3 scripts/install_skills.py ./out --dry-run           # preview, không ghi
```

| `--layout` | Đường dẫn ghi |
|---|---|
| `skills` | `<target>/<name>/SKILL.md` (chuẩn Claude / Cursor) |
| `by-phase` | `<target>/phase-NN/<name>.md` |
| `flat` | `<target>/<name>.md` |

### Đóng gói Agent Workbench vào repo của bạn

Capstone Phase 14 ship một Agent Workbench tái sử dụng (AGENTS.md, schemas, init/verify/handoff scripts):

```bash
python3 scripts/scaffold_workbench.py path/to/your-repo            # full pack + seeds
python3 scripts/scaffold_workbench.py path/to/your-repo --minimal  # bỏ qua docs/
python3 scripts/scaffold_workbench.py path/to/your-repo --dry-run  # chỉ preview
```

### Bốn loại artifact

| Loại | Mô tả | Cách dùng |
|---|---|---|
| **Prompts** | Template prompt cho từng task AI hẹp | Paste vào bất kỳ assistant nào |
| **Skills** | File `SKILL.md` có frontmatter | Drop vào Claude, Cursor, Codex, OpenClaw, Hermes |
| **Agents** | Loop tự động đã viết tay ở Phase 14 | Deploy như autonomous worker |
| **MCP Servers** | Server tuân thủ Model Context Protocol | Plug vào bất kỳ MCP client nào (built end-to-end ở Phase 13) |

---

## 8. Hướng dẫn bắt đầu

### Cách A — Chỉ đọc

Truy cập [aiengineeringfromscratch.com](https://aiengineeringfromscratch.com) hoặc mở bất kỳ thư mục `phases/` nào. Không cần setup.

### Cách B — Clone & chạy

```bash
git clone https://github.com/rohitg00/ai-engineering-from-scratch.git
cd ai-engineering-from-scratch
python phases/01-math-foundations/01-linear-algebra-intuition/code/vectors.py
```

### Cách C — Tìm trình độ phù hợp (Khuyến nghị)

Cài skill chương trình vào agent của bạn rồi chạy:

```bash
/find-your-level
```

10 câu hỏi — map kiến thức vào phase phù hợp, kèm ước tính thời lượng cá nhân hóa.

### Yêu cầu tiên quyết

- Biết viết code (ngôn ngữ nào cũng được; Python sẽ giúp ích).
- Muốn hiểu AI **thực sự hoạt động như thế nào**, không chỉ gọi API.

---

## 9. Tài nguyên tham khảo

### Trong repo này

| Tệp | Mục đích |
|---|---|
| [README.md](README.md) | Tổng quan dự án (tiếng Anh) |
| [ROADMAP.md](ROADMAP.md) | Trạng thái từng phase + lesson (✅ / 🚧 / ⬚) |
| [LESSON_TEMPLATE.md](LESSON_TEMPLATE.md) | Template để viết một bài học mới |
| [CONTRIBUTING.md](CONTRIBUTING.md) | Quy trình đóng góp |
| [FORKING.md](FORKING.md) | Fork cho team / trường học của bạn |
| [glossary/terms.md](glossary/terms.md) | Bảng thuật ngữ AI |
| [catalog.json](catalog.json) | JSON toàn bộ chương trình (auto-build) |

### Script hữu ích

```bash
python3 scripts/build_catalog.py           # rebuild catalog.json
python3 scripts/audit_lessons.py           # kiểm tra invariant L001–L010
python3 scripts/lesson_run.py              # smoke-check syntax Python cả khóa học
python3 scripts/lesson_run.py --phase 14   # chỉ một phase
```

### Bài báo nền tảng được cover trong khóa học

| Bài báo | Phase |
|---|---|
| *Attention Is All You Need* (Vaswani et al., 2017) | [Phase 7](#phase-7--transformers-deep-dive--14-bài--14-giờ) |
| *Language Models are Few-Shot Learners* (GPT-3) | [Phase 10](#phase-10--llms-from-scratch--22-bài--30-giờ) |
| *Denoising Diffusion Probabilistic Models* | [Phase 8](#phase-8--generative-ai--14-bài) |
| *InstructGPT / RLHF* | [Phase 10](#phase-10--llms-from-scratch--22-bài--30-giờ) |
| *Direct Preference Optimization* | [Phase 10](#phase-10--llms-from-scratch--22-bài--30-giờ) |
| *Chain-of-Thought Prompting* | [Phase 11](#phase-11--llm-engineering--17-bài) |
| *ReAct: Reasoning + Acting in LLMs* | [Phase 14](#phase-14--agent-engineering--42-bài--60-giờ) |
| *Model Context Protocol* (Anthropic) | [Phase 13](#phase-13--tools--protocols--23-bài) |

### Liên hệ & cộng đồng

- Website: [aiengineeringfromscratch.com](https://aiengineeringfromscratch.com)
- Maintainer: [Rohit Ghumare (@ghumare64)](https://github.com/rohitg00) — [X / Twitter](https://x.com/ghumare64)
- Báo lỗi / đề xuất: [GitHub Issues](https://github.com/rohitg00/ai-engineering-from-scratch/issues/new/choose)

---

## Tóm tắt một trang

| Hạng mục | Con số |
|---|---|
| Tổng số phase | **20** |
| Tổng số bài học | **435** |
| Tổng số dự án capstone | **17** |
| Tổng thời lượng ước tính | **~314 giờ** |
| Ngôn ngữ lập trình | Python, TypeScript, Rust, Julia |
| Artifact xuất ra | 378 skills + 99 prompts |
| Giấy phép | MIT — free, fork, sell, ship |

> *Bạn không chỉ học AI. Bạn build nó. End-to-end. Bằng chính tay mình.*

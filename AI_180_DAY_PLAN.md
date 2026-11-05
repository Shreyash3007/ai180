# 180-Day AI Engineer Plan (v2)

Day 1 = Nov 5, 2026. Day 180 = May 3, 2027. Days 181 to 360 are outlined at the end.

Target: an AI engineer who understands the model layer, ships real products fast, and has public proof. That profile gets hired by YC startups, applied AI teams and AI PM-track roles. It is also the base for Associate PM later.

---

## 0. What was wrong in v1, and what changed

1. **Users came too late.** v1 had the flagship product at Day 136 and users after that. Now users start at Day 8 and never stop.
2. **Two apps by Day 30 rewarded count, not value.** Now it is one product, picked from real pain interviews, not from what is fun to build.
3. **You already have a real product: Strata.** v1 ignored it. Now Strata is the spine of the plan. Every skill (retrieval, agents, evals, fine-tuning) gets applied to it, and a non-finance project proves the skill transfers. Strata has no analyst usability or willingness-to-pay evidence yet. That is the biggest hole in it, and Phase 2 closes it.
4. **Evals came too late.** Now evals-first from Day 31. You label data and build the harness before you tune anything.
5. **"Train on a large dataset" needed an honest scope.** On a budget of INR 15-25k you cannot pretrain 7B models. You can do full SFT on 0.5B, QLoRA on 7-8B, DPO, continued pretraining of a 0.5B model on roughly 100M tokens, and a small GRPO run. You learn the large-scale side through cost math, systems reading and one 2-GPU run.
6. **"Repeat the phase if you miss the gate" had no slack,** and that is how plans die. Now each phase has 2 buffer days and a debt rule (section 1).
7. **Thinking was not trained, only skills.** Now there is a daily first-principles notebook, estimation, pre-mortems and weekly decision memos.
8. **Frontier signal was thin on systems.** Now profiling, memory math, FSDP, FlashAttention and serving internals are in Phase 4.
9. **Drift risk was ignored.** You have started topics with high energy before and drifted. Section 1 has hard rules against that.

Honest limit: no plan guarantees "frontier labs will hire me" in 180 days. What this guarantees is public, checkable proof that most applicants do not have.

---

## 1. Operating system

**Daily (7 hrs, Days that are not exam days)**
- 2.0 hrs LEARN: videos, papers, docs. Active, with a notebook open
- 3.5 hrs BUILD: code, data, product
- 0.5 hr LOG: what broke, what I measured, what I got wrong
- 1.0 hr UI/UX or reading (section 5 and 6)
- Plus 20 min first-principles notebook (inside the learn block): write one thing you used today, then derive why it works from the ground up

**Exam days (every 7th day: D7, D14, ... D175)**
- 3 hrs closed-book exam on the week's core ideas, no notes, no AI
- 1 hr weekly log, 1 hr public post, rest of the day off
- If you cannot do the exam, redo it the next morning before anything new. That week is not counted

**Gates**
- Every day has a gate. A gate is something you can show, with a number
- Day gate missed: finish it the next day before new work
- Phase gate missed: use the 2 buffer days. Still missed: carry it as "debt" into the next phase and spend the first hour of each day on it until it clears. Never skip two phase gates in a row. If that happens, stop and cut scope, not hours

**Thinking system (this is where logic and judgment get built)**
- Daily: first-principles notebook (20 min)
- Weekly: one decision memo (1 page): the decision, options, what I believe, what would change my mind, what actually happened
- Before every build: a pre-mortem (3 lines: how this fails)
- Every claim gets a number. Do Fermi estimates for cost, latency and tokens before you run anything
- Read 2 papers a week with this template: problem, core idea in 3 lines, what they measured, what I would test next

**Anti-drift rules**
- No new projects. New ideas go in `parking_lot.md` with a date. Look at it only on Day 180
- Mentr, Docketwing, Aegis, simulators and everything else stay parked
- Public commitment: post your Day 1 plan and a weekly update. Find one person who checks your gates every Sunday
- Track gate status in one table in the repo: day, gate, pass or fail, link to proof

**College floor**
- Mark your university exam weeks now. In those weeks run light mode: 3 hrs/day, no new topics, maintenance only, and add those days to the end of the plan. A backlog costs more than it saves

**Product rules (real value, not demos)**
- A product starts with a named person and a repeated, painful workflow, not a technology
- Talk to 10 people before you build (Mom Test: ask about past behavior, never pitch)
- Ship by Day 14, then at least one release every week
- Success = people come back unprompted in week 2, not sign-ups
- Kill criteria written up front: "if fewer than 3 of 10 users return in 2 weeks, change the problem, not the UI"

**Compute and budget**
- Colab and Kaggle free tiers first, then Modal or RunPod. Hard cap INR 25,000 total. Log every rupee

---

## 2. Monthly stage criteria

| Month | Days | Stage | Output you must have | Pass criteria |
|---|---|---|---|---|
| 1 | 1-30 | First principles and shipping | micrograd, BPE, GPT, raw agent loop, Product A live | Derive backprop by hand, GPT reaches target loss, Product A has 5+ outside users who did the core action |
| 2 | 31-60 | Retrieval, data, evals | 2 corpora, 200 gold questions, harness, ablation report, citation UI, Strata analyst study | Each retrieval component has a number for what it bought. 5 analyst sessions done |
| 3 | 61-90 | Agents and infrastructure | Raw and LangGraph agent, 50-task suite, failure taxonomy, merged-or-open OSS PR, Strata infra upgrades | Success rate and failure taxonomy published. PR opened, review answered |
| 4 | 91-120 | Training, part 1 | Eval set, SFT, QLoRA, synthetic dataset, quantized model, DPO | Model on HF Hub with model card, data card, eval table vs prompted baseline |
| 5 | 121-150 | Training part 2 and flagship | CPT, GRPO, 2-GPU run, Strata v2 workflow in production | Strata has 10+ active analysts, one pricing signal |
| 6 | 151-180 | Flagship, hardening, positioning | 30+ users, benchmark, 4 deep posts, 3 teardowns, 40 outreach messages | Real usage data, "what users did vs what I assumed" doc, incident write-up |

Exact day boundaries follow the day-by-day list below (Phase 4 runs D91-D135).

---

## 3. Phases at a glance

- **Phase 1 (D1-30): First principles and shipping muscle.** Math, autograd, GPT, tokenizer, PyTorch, backend, Product A
- **Phase 2 (D31-60): Retrieval, data, evals.** BM25 to rerankers, two corpora, harness, ablations, Strata analyst study
- **Phase 3 (D61-90): Agents and infrastructure.** Raw first, then LangGraph, MCP, tracing, security, OSS PR, Strata infra
- **Phase 4 (D91-135): Training and post-training with Hugging Face.** SFT, QLoRA, DPO, CPT, GRPO, serving, systems
- **Phase 5 (D136-168): Flagship.** Strata v2 as a real product with users and pricing evidence
- **Phase 6 (D169-180): Harden and position.** Auth, monitoring, incident write-up, 4 posts, 40 targeted outreach

Each phase ends with 2 buffer days, which are already included in its last two entries.

---

## 4. Day-by-day plan

Format: **Learn** = what to search on YouTube. **Build** = what to produce. **Gate** = proof that the day counts. If an exact video is missing, search the title in quotes, or search the channel name plus the topic.

### PHASE 1 (D1-30): First principles and shipping muscle

- **D1** Learn: "3Blue1Brown essence of linear algebra" ch 1-4 | Build: public repo `ai180`, uv env, daily log template, gate table, `parking_lot.md` | Gate: repo public, Day 1 log committed, first-principles notebook started
- **D2** Learn: "Karpathy micrograd spelled-out intro to neural networks and backpropagation" (first half) | Build: `Value` class with add, mul, manual grads | Gate: grads match hand calculation on 3 expressions
- **D3** Learn: same video, second half; "The Mom Test Rob Fitzpatrick summary" | Build: finish autograd (tanh, exp, pow, topological backward). Start pain interviews: 10 people, a repeated painful workflow each | Gate: grads match PyTorch on a 2-layer MLP (error < 1e-6). 3 interviews done
- **D4** Learn: "3Blue1Brown neural networks backpropagation calculus" | Build: train your micrograd MLP on the moons dataset. 3 more interviews | Gate: over 95% accuracy, loss curve plotted. 6 interviews done
- **D5** Learn: "StatQuest backpropagation main ideas", "3Blue1Brown gradient descent" | Build: derive backprop for a 2-layer net on paper, verify in code. 4 more interviews | Gate: photo of derivation plus numeric check. 10 interviews done
- **D6** Learn: "3Blue1Brown essence of calculus chain rule", "matrix multiplication as composition" | Build: numpy MLP on MNIST with manual matrix gradients, no autograd. Score the 10 interviews (frequency, pain, reachability, shippable in 14 days) | Gate: over 97% MNIST. Product A chosen with the scoring sheet
- **D7 EXAM** Closed book: write the autograd `Value` class from a blank file in 60 min | Build: Product A one-page spec: user, workflow, success metric, kill criteria | Gate: exam passed. Weekly log. Post #1: the 180-day commitment
- **D8** Learn: "FastAPI full course" | Build: Product A backend: FastAPI, Postgres, one LLM call with structured output (Pydantic). Log tokens and cost per call | Gate: endpoint returns validated JSON, every call logged
- **D9** Learn: "Docker tutorial for beginners TechWorld with Nana" | Build: Dockerize, deploy to Cloud Run, Fly.io or Railway | Gate: public URL live
- **D10** Learn: "Tailwind CSS crash course", "shadcn/ui Next.js tutorial" | Build: minimal UI for the core flow only | Gate: a stranger completes the core flow without help
- **D11** Learn: "Anthropic tool use tutorial", "structured outputs tutorial" | Build: the core AI feature, prompts as versioned files | Gate: 10 hand-made test inputs with a pass/fail table
- **D12** Learn: "Postgres tutorial for beginners", "SQL window functions" | Build: users, sessions, thumbs up/down feedback tables | Gate: feedback rows coming from real use
- **D13** Learn: "Refactoring UI design tips" | Build: onboarding, empty states, error states | Gate: 3 named people use it without you present
- **D14 EXAM** Closed book: whiteboard backprop for a 2-layer net | Build: launch Product A to 10 named people | Gate: 5+ outside users did the core action. Post #2: what I built and what users did
- **D15** Learn: "Karpathy makemore part 1 bigram language model" | Build: bigram char model | Gate: NLL matches the video, sample names generated
- **D16** Learn: "Karpathy makemore part 2 MLP" | Build: embeddings plus MLP, train/dev/test split | Gate: dev loss under 2.2
- **D17** Learn: "Karpathy makemore part 3 activations gradients batchnorm" | Build: init diagnostics, plot activation and gradient stats | Gate: explain with numbers why bad init hurts
- **D18** Learn: "Karpathy makemore part 4 becoming a backprop ninja" | Build: manual backward through the whole net | Gate: all grads match autograd
- **D19** Learn: "Karpathy makemore part 5 WaveNet" | Build: hierarchical model. Talk to 3 Product A users | Gate: dev loss under 2.0. Interview notes with quotes
- **D20** Learn: "Jay Alammar illustrated transformer", "Umar Jamil attention is all you need explained" | Build: single-head causal self-attention in numpy | Gate: matches PyTorch scaled_dot_product_attention
- **D21 EXAM** Closed book: causal self-attention in PyTorch in 45 min | Build: Product A v2 (top user-requested change only) | Gate: exam passed, v2 live. Post #3
- **D22** Learn: "Karpathy let's build GPT from scratch" (first half) | Build: bigram to one self-attention head | Gate: loss falls on tiny Shakespeare
- **D23** Learn: same, second half | Build: multi-head, MLP, LayerNorm, residuals | Gate: val loss under 1.5
- **D24** Learn: "Karpathy let's build the GPT tokenizer" | Build: BPE train, encode, decode from scratch | Gate: exact round-trip on 10 MB text, token counts compared to tiktoken
- **D25** Learn: "PyTorch mixed precision tutorial", "PyTorch profiler tutorial" | Build: AMP, grad clipping, cosine LR, checkpointing, W&B logging | Gate: documented speedup of 1.5x or more
- **D26** Learn: "Karpathy let's reproduce GPT-2 124M" (part 1) | Build: GPT-2 architecture, load HF weights | Gate: logits match HF within tolerance
- **D27** Learn: same, speed section (flash attention, torch.compile, DDP concept) | Build: apply 3 speedups | Gate: tokens/sec table before and after
- **D28 EXAM** Closed book: BPE from scratch plus GPT-2 architecture on a whiteboard | Build: Product A v3 (retention fix) | Gate: exam passed. Post #4: lessons from training a GPT
- **D29** Learn: Anthropic "Building effective agents" (read), "ReAct paper explained" | Build: raw tool-using agent loop, no framework, about 150 lines: 3 tools, retries, max steps, error handling | Gate: handles tool errors and malformed output on 20 test tasks
- **D30 PHASE 1 GATE** Buffer day 1 | Build: gate review | Gate: (1) backprop derived by hand, (2) GPT trained to target loss or GPT-2 matched, (3) Product A live, 5+ outside users, usage chart, (4) raw agent loop. Write "what I understood vs what I assumed". Retakes use the 2 buffer days (D30 plus the next morning)

### PHASE 2 (D31-60): Retrieval, data, evals

- **D31** Learn: "Hamel Husain your AI product needs evals", "Hamel Husain error analysis LLM" | Build: take 30 real Strata outputs, label good or bad, write failure modes | Gate: error taxonomy v1 with counts
- **D32** Learn: "BM25 explained", "TF-IDF explained" | Build: BM25 from scratch | Gate: top-10 matches `rank_bm25` on 20 queries
- **D33** Learn: "sentence embeddings explained", "contrastive learning InfoNCE loss explained" | Build: embedding search with sentence-transformers | Gate: recall@5 on 20 hand-written queries
- **D34** Learn: "HNSW explained", "FAISS tutorial" | Build: brute force vs HNSW, recall vs latency | Gate: table at 3 ef values
- **D35 EXAM** Closed book: BM25 plus cosine retriever with recall@k eval from a blank file | Build: recruit 5 analysts or CFA people for Strata sessions (DM juniors, ask for 30 min) | Gate: exam passed, 5 sessions requested. Post #5: Strata failure taxonomy
- **D36** Learn: "chunking strategies for RAG", "Greg Kamradt 5 levels of text splitting" | Build: ingestion pipeline with 3 chunkers for 2 corpora: finance filings (BSE/NSE results, annual reports) and non-finance (Python and FastAPI docs) | Gate: both corpora ingested, chunk stats table
- **D37** Learn: "RAG from scratch Lance Martin" | Build: hand-label 60 finance gold questions with source spans | Gate: 60 Q/A with page citations
- **D38** Learn: "hybrid search reciprocal rank fusion" | Build: finish 100 finance gold questions. Implement RRF | Gate: 100 Qs done, hybrid returns results
- **D39** Learn: Anthropic "contextual retrieval" (read plus video summaries) | Build: 100 gold questions on the docs corpus | Gate: 200 total gold questions
- **D40** Learn: "LLM as a judge Hamel Husain", "RAGAS faithfulness explained" | Build: eval harness: recall@k, MRR, faithfulness (LLM judge calibrated on 30 human labels) | Gate: one command runs both corpora and prints a table
- **D41** Learn: "chunk size ablation RAG" | Build: ablation 1: chunk size | Gate: numbers for 3 sizes on both corpora
- **D42 EXAM** Closed book: explain recall@k vs MRR vs faithfulness and when each lies | Build: ablation 2: hybrid vs dense vs BM25 | Gate: exam passed, table. Post #6
- **D43** Learn: "cross-encoder reranker explained", "BGE reranker tutorial" | Build: ablation 3: reranker | Gate: recall and latency table
- **D44** Learn: "HyDE query rewriting RAG" | Build: ablation 4: query rewriting | Gate: numbers, with failure examples
- **D45** Learn: "contextual retrieval implementation Anthropic" | Build: ablation 5: contextual chunks | Gate: numbers, with cost per document
- **D46** Learn: "Docling tutorial PDF parsing", "extract tables from PDF financial statements" | Build: parse finance PDFs with tables | Gate: table extraction accuracy on 20 hand-checked tables
- **D47** Learn: "Microsoft GraphRAG explained" | Build: small knowledge graph experiment on finance corpus | Gate: does it help? numbers either way
- **D48** Learn: "RAG citation attribution verification" | Build: citation verifier: each claim mapped to a source span | Gate: citation precision measured on 50 answers
- **D49 EXAM** Closed book: explain HNSW and the retrieval pipeline on a whiteboard | Build: outline the ablation report | Gate: exam passed. Post #7
- **D50** Learn: "Vercel AI SDK streaming chat tutorial" | Build: streaming answers with clickable citations (docs corpus app) | Gate: citations clickable
- **D51** Learn: "Refactoring UI hierarchy spacing" | Build: source panel that highlights the exact span | Gate: click citation, exact span highlighted
- **D52** Learn: "deploying Next.js app Vercel" | Build: deploy doc-QA publicly, share with 10 developers | Gate: live URL, 10 real questions asked
- **D53** Learn: "Steve Krug Don't Make Me Think usability test" | Build: watch 5 strangers use doc-QA and Strata without help | Gate: notes, top 5 stall points
- **D54** Learn: "UX writing microcopy basics" | Build: fix stall points | Gate: 2 retests pass
- **D55** Learn: "evaluating RAG in production" | Build: swap best retrieval config into Strata | Gate: before/after eval on Infosys and TCS docs
- **D56 EXAM** Closed book: design a retrieval eval for a new corpus in 30 min | Build: first Strata analyst sessions | Gate: exam passed, sessions run. Post #8
- **D57** Learn: "how to run user interviews Mom Test follow-ups" | Build: 3 analyst sessions: watch them use Strata, ask about last time they did this task | Gate: notes with quotes
- **D58** Learn: "pricing interview questions willingness to pay" | Build: 2 more sessions plus willingness-to-pay questions | Gate: "what analysts did vs what I assumed" one-pager
- **D59** Learn: "how to write a technical blog post" | Build: publish the ablation report | Gate: published with numbers for every component
- **D60 PHASE 2 GATE** Buffer day 1 | Gate: (1) ablation report published, (2) harness in repo, (3) doc-QA live with 10+ real questions, (4) 5 analyst sessions with notes. Buffer D60 plus next morning

### PHASE 3 (D61-90): Agents and infrastructure

Product C: a codebase or issue-triage agent for a real open-source repo whose maintainers you contact. It is non-finance, it feeds your OSS PR, and it has real users (maintainers).

- **D61** Learn: "Anthropic building effective agents", "workflows vs agents" | Build: pick the repo, read CONTRIBUTING, list 10 open issues, message 3 maintainers about their pain | Gate: repo chosen, 3 messages sent
- **D62** Learn: "agent loop state machine design" | Build: raw agent v1 with typed state (Pydantic) for Product C | Gate: runs end to end on 5 issues
- **D63 EXAM** Closed book: ReAct loop with retries from a blank file in 60 min | Build: write 20 test tasks | Gate: exam passed. Post #9
- **D64** Learn: Anthropic "writing tools for agents" | Build: 6 tools with sharp descriptions and helpful error messages | Gate: tool-call success rate measured
- **D65** Learn: "context engineering for agents", "MemGPT agent memory explained" | Build: context trimming, summaries, simple long-term memory | Gate: same tasks, lower tokens, same success
- **D66** Learn: "Langfuse tutorial tracing LLM" | Build: trace every run (prompts, tools, cost, latency) | Gate: one trace per run visible
- **D67** Learn: "agent evaluation SWE-bench tau-bench explained" | Build: 50-task suite with expected outcomes | Gate: suite runs from one command
- **D68** Learn: "error analysis agents failure modes" | Build: run suite, label every failure | Gate: failure taxonomy with counts
- **D69** Learn: "agent debugging from traces" | Build: fix top 3 failure classes, rerun | Gate: success rate before and after
- **D70 EXAM** Closed book: explain your failure taxonomy and the fix for each class | Build: write the planned LangGraph port | Gate: exam passed. Post #10
- **D71** Learn: "LangGraph LangChain Academy intro", "LangGraph state reducers checkpoints" | Build: LangGraph hello world with a checkpointer | Gate: resume from checkpoint works
- **D72** Learn: "LangGraph build agent from scratch" | Build: port Product C to LangGraph | Gate: passes the same 50-task suite
- **D73** Learn: "LangGraph human in the loop interrupt", "durable execution Temporal explained" | Build: human approval step plus resume after crash | Gate: kill the process mid-run, run resumes correctly
- **D74** Learn: "raw vs framework agents tradeoffs" | Build: compare raw vs LangGraph: success, cost, latency, lines of code | Gate: comparison table and a clear recommendation
- **D75** Learn: "Model Context Protocol tutorial build MCP server" | Build: expose your tools as an MCP server | Gate: a client (Claude or another) calls your tools
- **D76** Learn: "Pydantic AI tutorial", "OpenAI Agents SDK tutorial" | Build: minimal port to one contrast framework | Gate: 3 differences written down
- **D77 EXAM** Closed book: LangGraph graph with checkpoint plus interrupt from a blank file | Build: threat model for Product C | Gate: exam passed. Post #11
- **D78** Learn: "Simon Willison prompt injection lethal trifecta", "e2b sandbox code execution" | Build: red-team with 20 injection attacks, sandbox any code execution | Gate: attack table with before and after
- **D79** Learn: "Anthropic prompt caching tutorial", "LLM model routing" | Build: caching plus routing cheap-vs-strong | Gate: cost per task down 30% or more, no accuracy loss
- **D80** Learn: "how to read open source code LangGraph source walkthrough" | Build: pick a real issue in LangGraph, TRL, vLLM or similar, claim it | Gate: issue claimed, reproduction written
- **D81** Learn: "first open source contribution tutorial" | Build: implement the fix | Gate: tests pass locally
- **D82** Learn: "writing good pull requests" | Build: open the PR | Gate: PR open with tests and clear description
- **D83** Learn: "launching a developer tool Show HN tips" | Build: deploy Product C for 5 real maintainers or developers | Gate: 5 people have run it on real issues
- **D84 EXAM** Closed book: compare durable execution vs plain retries, with an example | Build: usage review, answer PR review comments | Gate: exam passed. Post #12
- **D85** Learn: "ByteByteGo system design", "designing LLM application architecture" | Build: Strata multi-tenant architecture doc | Gate: doc with data flow, failure modes, cost model
- **D86** Learn: "background jobs queues Redis Cloud Tasks tutorial" | Build: Strata long-running extraction as a background job | Gate: job survives restart
- **D87** Learn: "observability LLM apps dashboards" | Build: Strata tracing plus cost per analysis dashboard | Gate: cost per analysis visible
- **D88** Learn: "regression testing LLM CI GitHub Actions" | Build: Strata Infosys and TCS regression suite in CI | Gate: CI fails when accuracy drops
- **D89** Learn: "writing postmortems" | Build: write the agent failure taxonomy post | Gate: draft ready
- **D90 PHASE 3 GATE** Buffer day 1 | Gate: (1) raw and LangGraph agents with 50-task numbers, (2) failure taxonomy published, (3) OSS PR open and answered, (4) Product C used by 5 real people, (5) Strata CI evals running. Buffer D90 plus next morning

### PHASE 4 (D91-135): Training and post-training with Hugging Face

Task: structured extraction of financial line items from Indian results PDFs into JSON. It is checkable, it is what Strata needs, and a small model can plausibly match a frontier model on it.

- **D91 EXAM** Closed book: explain how a transformer forward pass and a training step use memory | Learn: "Hugging Face LLM course chapters 1-3" | Build: Phase 3 retake and Phase 4 setup (HF account, W&B, Modal) | Gate: exam passed. Post #13
- **D92** Learn: "Hugging Face LLM course Transformers Datasets Tokenizers" | Build: load a 0.5B model (Qwen2.5-0.5B), tokenize your task data | Gate: inference runs, tokenization inspected
- **D93** Learn: "Hamel Husain eval datasets" | Build: build a 200-example gold eval set for extraction, hand-verified | Gate: 200 verified examples, never used for training
- **D94** Learn: "benchmarking LLMs cost per token" | Build: baselines: prompted frontier model and prompted 0.5B and 8B models | Gate: accuracy, cost and latency table
- **D95** Learn: "Umar Jamil LoRA explained", "LoRA paper explained" | Build: LoRA from scratch on a tiny model | Gate: matches PEFT output on a toy case
- **D96** Learn: "Hugging Face PEFT tutorial", "TRL SFTTrainer tutorial" | Build: full SFT of the 0.5B model on a small public dataset | Gate: training loss curve, no divergence
- **D97** Learn: "how to read training loss curves" | Build: eval the SFT model on your gold set | Gate: number vs baseline
- **D98 EXAM** Closed book: LoRA math and a minimal training loop | Build: weekly log | Gate: exam passed. Post #14
- **D99** Learn: "Chinchilla scaling laws explained", "transformer FLOPs 6ND memory Adam" | Build: compute and memory calculator | Gate: predict VRAM for a 7B QLoRA run, then verify
- **D100** Learn: "Llama 3 paper walkthrough", "Stanford CS336 data lecture" | Build: data plan: sources, filters, size target | Gate: one-page data plan
- **D101** Learn: "web scraping PDFs BSE NSE results" | Build: collect 500+ results PDFs | Gate: raw corpus with metadata
- **D102** Learn: "synthetic data generation distilabel", "distillation from frontier models" | Build: teacher labeling with schema validation | Gate: 5k labeled candidates
- **D103** Learn: "MinHash LSH dedup explained", "benchmark decontamination" | Build: dedup, quality filters, remove anything near the eval set | Gate: 5k+ verified examples and a data card
- **D104** Learn: "QLoRA explained Tim Dettmers", "bitsandbytes 4-bit tutorial" | Build: QLoRA on a 7-8B model on Colab/Kaggle/Modal | Gate: run completes, checkpoint saved
- **D105 EXAM** Closed book: why QLoRA fits in memory, with numbers | Build: first eval of the QLoRA model | Gate: exam passed. Post #15
- **D106** Learn: "LoRA hyperparameters rank alpha learning rate" | Build: sweep rank and LR (small budget) | Gate: results table with cost
- **D107** Learn: "error analysis fine-tuned model" | Build: categorize every miss | Gate: failure taxonomy of the model
- **D108** Learn: same | Build: fix data issues found, retrain | Gate: improved number with a reason
- **D109** Learn: "LLM benchmarking pitfalls" | Build: final comparison: fine-tune vs prompted frontier vs prompted small | Gate: table including where the fine-tune loses
- **D110** Learn: "quantization GPTQ AWQ GGUF explained" | Build: quantize to AWQ and GGUF | Gate: accuracy loss measured
- **D111** Learn: "vLLM PagedAttention explained", "vLLM serving tutorial" | Build: serve with vLLM, load test | Gate: tokens/sec and cost per million tokens
- **D112 EXAM** Closed book: PagedAttention and continuous batching in your own words | Build: publish model, data card, eval table on HF Hub | Gate: model on Hub. Post #16: results including losses
- **D113** Learn: "RLHF explained Umar Jamil", "DPO explained" | Build: DPO objective derivation on paper | Gate: derivation plus code of the loss
- **D114** Learn: "TRL DPOTrainer tutorial" | Build: create preference data (good vs bad extractions from your own error taxonomy) | Gate: 2k preference pairs
- **D115** Learn: same | Build: run DPO on the SFT model | Gate: run completes
- **D116** Learn: "DPO vs SFT when it helps" | Build: eval DPO vs SFT | Gate: table, honest conclusion
- **D117** Learn: "continued pretraining domain adaptation data mixing" | Build: assemble about 100M tokens of Indian financial text, dedup | Gate: token count and a data card
- **D118** Learn: "catastrophic forgetting continued pretraining" | Build: CPT of the 0.5B model | Gate: run complete, loss curve
- **D119 EXAM** Closed book: compute the FLOPs and time for your CPT run before looking at actual | Build: eval perplexity and downstream extraction | Gate: exam passed. Post #17
- **D120** Learn: "policy gradient explained REINFORCE", "Hugging Face deep RL course" | Build: REINFORCE on CartPole | Gate: reward curve rises
- **D121** Learn: "PPO explained" | Build: read a PPO implementation, annotate | Gate: annotated notes
- **D122** Learn: "DeepSeek R1 GRPO explained" | Build: design a verifiable reward (exact match on numeric fields) | Gate: reward function with unit tests
- **D123** Learn: "TRL GRPOTrainer tutorial" | Build: GRPO on a small model | Gate: run completes, reward curve
- **D124** Learn: "reward hacking examples" | Build: inspect samples, find hacks | Gate: list of hacks found and a patched reward
- **D125** Learn: "RL for LLMs limitations" | Build: write the GRPO result up | Gate: honest write-up with numbers
- **D126 EXAM** Closed book: GRPO vs PPO vs DPO, when to use which | Build: weekly log | Gate: exam passed. Post #18
- **D127** Learn: "Hugging Face Ultra-Scale Playbook", "FSDP explained" | Build: memory math for multi-GPU | Gate: predictions written down
- **D128** Learn: "FlashAttention explained Umar Jamil" | Build: read the algorithm, implement tiled attention in numpy | Gate: matches standard attention
- **D129** Learn: "accelerate DeepSpeed ZeRO tutorial" | Build: 2-GPU run on Modal or RunPod | Gate: scaling efficiency measured
- **D130** Learn: "PyTorch profiler GPU bottlenecks" | Build: profile one training run | Gate: top 3 bottlenecks identified
- **D131** Learn: "Triton GPU programming tutorial" | Build: write one small Triton kernel (softmax) | Gate: matches PyTorch output
- **D132** Learn: "A/B testing models in production" | Build: add the fine-tuned model to Strata as an optional path with fallback to the frontier model | Gate: shadow-run on real Strata documents
- **D133 EXAM** Closed book: the full fine-tuning pipeline from data to serving on a whiteboard | Build: budget review | Gate: exam passed. Post #19
- **D134** Learn: "how to write a model card" | Build: full training report, including where you lost | Gate: published
- **D135 PHASE 4 GATE** Buffer day | Gate: (1) HF Hub model with model card, data card, eval table, (2) SFT, QLoRA, DPO, CPT, GRPO each with numbers, (3) one 2-GPU run, (4) serving cost per million tokens, (5) spend under INR 25k. An honest "did not beat the baseline, here is why" passes. A vague claim fails

### PHASE 5 (D136-168): Flagship. Strata v2 as a real product

Rule: build only what the analyst sessions say matters most. Strata's own notes say W2 (coverage update without a model) and arbitrary workbooks are not built. Let the interview evidence pick one, not your taste.

- **D136** Learn: "Lenny's Podcast how to write a PRD", "Shreyas Doshi pre-mortem" | Build: Strata v2 PRD from the analyst notes: one workflow, metric, kill criteria | Gate: PRD with a single success metric
- **D137** Learn: "PostHog product analytics tutorial" | Build: event plan: activation, return, approval rate, time saved | Gate: event list reviewed
- **D138** Learn: "product analytics funnels retention" | Build: instrument events in Strata | Gate: events visible in dashboard
- **D139** Learn: "jobs to be done framework" | Build: pick the v2 workflow with a written reason and a rejected-options list | Gate: decision memo
- **D140 EXAM** Closed book: write the Strata v2 PRD summary from memory | Build: gold set for the chosen workflow | Gate: exam passed, 50+ gold cases. Post #20
- **D141** Learn: "eval driven development LLM" | Build: baseline the workflow against the gold set | Gate: baseline numbers
- **D142** Learn: "structured extraction production patterns" | Build: retrieval plus extraction for the workflow | Gate: beats baseline
- **D143** Learn: "human in the loop UX approval flows" | Build: agent with checkpoints and analyst approve/edit UI | Gate: analyst can approve or edit each step
- **D144** Learn: "CI evals GitHub Actions" | Build: workflow evals in CI | Gate: CI blocks regressions
- **D145** Learn: "AI UX patterns Perplexity Linear teardown" | Build: UX pass: uncertainty display, undo, empty and failure states | Gate: 3 stall points fixed
- **D146** Learn: "product onboarding teardown" | Build: onboarding and a 2-minute demo flow | Gate: new user reaches value without help
- **D147 EXAM** Closed book: explain your eval design for the workflow | Build: release v2 to 10 analysts | Gate: exam passed, v2 live. Post #21
- **D148** Learn: "cold outreach LinkedIn DM for juniors" | Build: 20 outreach messages a day to junior and mid-level analysts, ask for 20 min to watch them use it | Gate: 40 messages sent
- **D149** Learn: "retention cohort analysis" | Build: first usage review | Gate: who returned, who did not, why
- **D150** Learn: "Mom Test follow-up questions" | Build: 3 analyst interviews | Gate: quotes and a behavior list
- **D151** Learn: "prioritization RICE" | Build: top fix from interviews | Gate: shipped
- **D152** Learn: same | Build: 3 more interviews | Gate: notes
- **D153** Learn: "Van Westendorp pricing", "pricing strategy for B2B SaaS" | Build: pricing test using the proposed INR 2,999, 14,999 and 49,999 tiers: ask for a real commitment, not an opinion | Gate: responses logged
- **D154 EXAM** Closed book: explain the evidence for and against your pricing | Build: release #3 | Gate: exam passed. Post #22
- **D155** Learn: "SLO error budgets explained" | Build: define reliability targets | Gate: SLOs written
- **D156** Learn: "LLM cost optimization production" | Build: cost per analysis reduced | Gate: down 20% or more
- **D157** Learn: "latency optimization streaming LLM" | Build: p95 latency work | Gate: p95 before and after
- **D158** Learn: "A/B test analysis basics" | Build: A/B test the fine-tuned model on real traffic | Gate: quality and cost comparison
- **D159** Learn: "multi-tenant data isolation SaaS" | Build: tenant isolation and data deletion | Gate: isolation tests pass
- **D160** Learn: "SOC 2 basics for startups", "data privacy for user documents" | Build: privacy and retention policy | Gate: written policy
- **D161 EXAM** Closed book: Strata architecture on a whiteboard, with failure modes | Build: release #4 | Gate: exam passed. Post #23
- **D162** Learn: "how benchmarks are built open source dataset release" | Build: open-source India filings extraction benchmark (data plus harness) | Gate: repo public, README with results
- **D163** Learn: "writing a README that sells" | Build: polish and publish benchmark | Gate: someone outside runs it
- **D164** Learn: "decision logs engineering" | Build: decision log of what you reversed and why | Gate: 10 entries
- **D165** Learn: "retention curves SaaS" | Build: cohort analysis | Gate: retention chart
- **D166** Learn: "writing a case study" | Build: "what users did vs what I assumed" document | Gate: published
- **D167** Learn: "user research synthesis" | Build: next 90 days roadmap for Strata from data | Gate: roadmap with kill criteria
- **D168 EXAM and PHASE 5 GATE** Closed book: pricing and retention argument | Gate: (1) 30+ real users reached, 10+ active, (2) weekly releases, (3) usage data and one pricing signal, (4) benchmark public, (5) user-vs-assumption doc. Buffer D168 plus next morning

### PHASE 6 (D169-180): Harden and position

- **D169** Learn: "web app security auth rate limiting" | Build: auth hardening, rate limits, abuse controls | Gate: abuse test passes
- **D170** Learn: "Grafana alerting basics", "Sentry tutorial" | Build: monitoring and alerts | Gate: alert fires on a forced error
- **D171** Learn: "chaos engineering basics" | Build: incident drill, break something on purpose | Gate: incident write-up
- **D172** Learn: "cloud cost budgets alerts" | Build: backups, budgets, restore test | Gate: restore works
- **D173** Learn: "how to write a deep technical post" | Build: post 1: retrieval ablation | Gate: published
- **D174** Learn: same | Build: post 2: agent failure taxonomy | Gate: published
- **D175 EXAM** Closed book: pick any phase and teach it for 20 min, no notes | Build: post 3: eval harness | Gate: exam passed, post published
- **D176** Learn: same | Build: post 4: fine-tune results, including where it lost | Gate: published
- **D177** Learn: "product teardown framework" | Build: 3 AI product teardowns with concrete redesigns | Gate: 3 published
- **D178** Learn: "how to get hired by a startup cold email founders", "Y Combinator Work at a Startup" | Build: list of 40 startups. For each, one specific teardown or small PR as the opener | Gate: 40 targets, 40 specific hooks
- **D179** Build: send 20 outreach messages | Gate: 20 sent, tracked in a sheet
- **D180 FINAL GATE** Build: send 20 more, final review, open `parking_lot.md` for the first time, write the plan for D181-360 | Gate: all phase gates reviewed, a final "what I can do now that I could not on Day 1" list with proof links

---

## 5. UI/UX track (about 5 hrs a week, inside the daily 1 hr)

You asked if this is worth your time: yes, capped. Bad UI hides good engineering. Founders hire people who can take an idea to a usable product alone. You need taste and speed, not a design career.

- **Weeks 1-4 (D1-28): basics.** Search: "Refactoring UI", "Nielsen 10 usability heuristics", "8pt grid system", "type scale design", "color theory for UI", "Kevin Powell CSS". Output: clone 5 real screens pixel by pixel in Tailwind and shadcn/ui. Learn Figma to a basic level ("Figma tutorial for developers")
- **Weeks 5-12 (D29-84): practice.** One teardown a week (search "UX teardown" plus a product you use), one cloned component a day. Output: a personal component kit
- **Weeks 13-26 (D85-180): AI-specific UX.** Streaming and latency masking, citations and provenance, uncertainty and confidence, undo and edit, human approval, failure and empty states. Search: "AI UX patterns", "designing AI products Linear Perplexity Cursor teardown"
- **Every phase gate:** watch 5 strangers use your product with no help. Where they stall is the next fix

---

## 6. Reading list (2 papers a week, one per exam-week boundary if you are short)

Phase 1: Attention Is All You Need, GPT-2, Adam. Phase 2: BM25 background, DPR, Self-RAG, Lost in the Middle, Anthropic contextual retrieval. Phase 3: ReAct, Toolformer, SWE-bench, tau-bench, Anthropic multi-agent research system post. Phase 4: Chinchilla, Llama 3, LoRA, QLoRA, DPO, DeepSeek-R1, FlashAttention, PagedAttention. Books: Chip Huyen "AI Engineering", Designing Data-Intensive Applications (chapters on storage and replication). Search each as "<paper name> explained" on YouTube, then read the paper itself and fill the template from section 1.

---

## 7. Days 181-360: advanced application layer

You said you want the second half at the application layer with advanced depth. This base lets you do that.

- **D181-225: Evals at scale.** Judge calibration at scale, synthetic eval generation, online evals from production traffic, red-teaming pipelines. Output: open-source eval toolkit with real adopters
- **D226-270: Advanced agents.** Long-horizon agents, computer-use agents, multi-agent coordination that actually beats a single agent, agent memory at scale, cost controls. Output: a published agent benchmark and a reference architecture
- **D271-315: Inference and product economics.** Speculative decoding, caching strategies, routing, distillation to cut cost, latency engineering. Output: Strata at a unit cost you can defend
- **D316-360: Product-led growth and leadership.** Distribution, pricing, retention, writing PRDs and strategy docs, hiring conversations. Output: a revenue number for Strata or a shipped product that is clearly yours, plus your APM-track and startup applications with proof

Rule for this half: depth in one area every 45 days, no spreading. Keep the same exam-day rhythm, the same gates and the same one-product rule.

---

## 8. Notes on resources

- YouTube titles change. If an exact video is missing, search the channel name plus topic: Andrej Karpathy, 3Blue1Brown, StatQuest, Umar Jamil, Jay Alammar, Hugging Face, Stanford Online (CS336, CS224N), Hamel Husain, Lance Martin (LangChain), Simon Willison
- Do not watch passively. Pause, write the idea in the notebook, code it the same day
- No tutorial counts until you rebuild it from a blank file

# ML systems career positioning and résumé research

**Research date:** 17 October 2026

**Context:** Bruce Xi — SW/HW Co-Design Engineer, Huawei Canada; under two years of professional experience; open to global opportunities and relocation.

## Conclusion

The strongest professional positioning supported by the work discussed is:

> **Software engineer focused on ML training systems, performance optimization, and evaluation reliability, with hands-on accelerator and compiler-debugging experience.**

The new project is valuable because it connects training data, agent execution, evaluation, and the systems that make training efficient. The earlier kernel and compiler projects provide evidence that Bruce can investigate problems below the model-facing Python layer.

This is a contribution-level engineering profile. It does not require claiming deep expertise in every component of a compiler, kernel library, RL algorithm, or distributed training platform. The useful combination is the ability to understand an ML workload, identify the layer responsible for a failure or bottleneck, implement a change, and validate the result.

The broader research adds **training performance and framework integration** as a substantial career direction alongside LLM post-training systems and agent evaluation. The résumé should preserve all three connections while giving each application a clear primary emphasis.

## What was established in the conversation

- The project had two phases over approximately half a year and **ended in October 2026**. An exact start month was not supplied, so the résumé uses “Completed Oct. 2026.”
- Bruce has under two years of professional experience. Job descriptions were studied across levels to understand responsibilities and terminology, rather than restricted to junior openings.
- A few months on a kernel or compiler project should not become a claim of broad specialist expertise. Concrete contributions remain useful evidence within a wider ML systems profile.
- The objective is market research, career positioning, and a stronger résumé—not merely a list of vacancies or a list of fashionable technologies.
- The current résumé uses two pages to retain the strongest results from the new project, compiler debugging, and Mamba2 training optimization.

## Project record: overall work and individual contributions

The contributions below come from Bruce’s account, his work-summary slides, the existing résumé, and the project report/paper. They were not independently reconstructed from source-code history or training logs.

### Phase one: establishing Ascend kernel-generation training

The [Huawei technical report](https://mp.weixin.qq.com/s/jdQQPb-w--AJjIAnCh63QQ) describes an Ascend kernel-generation workflow with execution-based verification, stricter precision requirements, Triton-only checks, synthetic trajectories, SFT, and multi-turn RL.

Bruce’s stated contributions were:

1. **SFT trajectory distillation.** Generated training trajectories for supervised fine-tuning.
2. **Convolution baseline diagnosis.** Investigated repeated convolution accuracy failures initially attributed to model limitations. Identified the reference computation’s default HF32 mode, rather than full FP32, as the cause of the precision mismatch.

The important engineering signal in the second contribution is distinguishing an evaluation/reference problem from a model capability problem. Incorrect feedback can otherwise misdirect debugging, data selection, and subsequent experiments.

The report’s headline comparison—29% versus 9% on KernelBench Level 2 under its production standard—is a **team-level Pass@8 result**. It should not be attributed solely to Bruce or compared directly with ATRL’s Pass@1 results.

### Phase two: agent tooling, data, experiments, and training efficiency

The reviewed ATRL manuscript is titled *Compaction-Aware Reinforcement Learning for Ascend Triton Kernel Generation*. Its method connects structured context compaction with segment-level training rewards. Checkpoint generation participates in training, and segment rewards combine terminal outcomes with verified local progress.

Bruce’s documented contributions concern the experiments, tooling, data, and training systems supporting the project. The conversation did not establish that he independently invented the paper’s complete RL objective.

| Contribution | Documented result or evidence | Transferable capability |
|---|---|---|
| Controlled harness comparisons | Claude Code and uni-agent produced similar results in the reported comparison, supporting the harness choice for RL integration | Experimental design and engineering trade-offs |
| CANNBot Skills ablations | On an 18-task KernelBench matrix-multiplication subset, Pass@1 increased from 13/18 to 17/18 and Fast@1 from 0/18 to 9/18 | Controlled benchmarking and evaluation-guided development |
| Training-trajectory inspection | Identified four prompt, skills, or tool issues and proposed fixes; missing interface instructions were associated with first-attempt failures on 35/102 tasks in one experiment | Failure analysis and interface debugging |
| msprof integration and guidance | Built and tested profiler tooling and accompanying Triton guidance; one matmul case improved from 2,886 to 2,197 μs, approximately 24% lower latency | Performance diagnostics and research tooling |
| SFT distillation and data preparation | Used DeepSeek-V4-Flash in phase two; selected trajectories using correctness/performance, removed unproductive turns, and compressed content to fit token budgets | Synthetic data generation, curation, and trajectory distillation |
| Partial rollout in verl/vLLM | Added cross-batch execution and continuation across training steps, with importance-sampling correction across policy updates; subsequent RL training was reported approximately 20% faster | Rollout scheduling, straggler mitigation, and training efficiency |

The profiler tools and partial-rollout implementation were integrated into the team’s training repository and used in later training. Project outputs included a Huawei technical report, an ICLR 2027 submission, and a contribution to `verl-ascend-recipe`. A submission is not an acceptance; project outputs should not imply sole authorship.

### Existing work that supports the same profile

- **Mamba2 training optimization:** Ascend C kernels integrated with PyTorch; a kernel achieved 12× forward and 15× backward speedups, with a reported 4.6% reduction in overall training-step time and 1.5% MFU improvement. The résumé preserves “1.5%” as supplied rather than changing it to percentage points.
- **Compiler debugging:** Traced silent corruption through more than 600 compiler-pass dumps to incorrect predicate materialization during MLIR-to-LLVM lowering; implemented a fix and regression tests.
- **Model bring-up:** Helped bring up Qwen and DeepSeek on MindSpeed-LLM and tuned micro-batch size and parallelism configurations.

These provide complementary evidence: kernel-level work, framework integration, numerical judgment, compiler investigation, and training-runtime improvements.

## Research scope and methodology

The initial 38-description review was expanded into a larger, reproducible corpus.

| Stage | Coverage |
|---|---:|
| Main source postings screened | 13,196 |
| Relevant records before deduplication | 1,162 |
| Deduplicated main-corpus descriptions | 865 |
| Employer boards/brands in the main corpus | 85 |
| Focused text-analysis cohort | 506 descriptions across 72 employer boards/brands |
| Adjacent technical descriptions | 359 |
| Separate Tencent search results | 340 |
| Complete Tencent descriptions in the language cross-check | 60 |
| Total retained main corpus plus cross-check | 925 descriptions |

### Collection and screening

The main collection used public employer feeds from Ashby, Greenhouse, and Lever, supplemented by NVIDIA’s public Workday endpoint and Amazon’s public job-search endpoint. Targeted employer-page searches provided additional context, including Google and AMD. Tencent’s public careers interface supplied the Chinese-language cross-check.

The screen focused on technical individual-contributor work involving ML systems, post-training, evaluation, training data, inference, frameworks, or performance. Broader applied-ML roles were retained separately. Management and commercial roles were generally excluded. Classification used explicit heuristics, so edge cases and imperfect classifications remain possible.

Repeated URLs, normalized employer/title pairs, geographic variants, and identical role text within an employer were collapsed. Distinct scope or level titles remain separate; some near-duplicate descriptions can remain.

Recognizable company introductions and benefits sections were removed before vocabulary matching. Each topic was counted once per description, with a second count for distinct employer boards mentioning it.

### Interpretation limits

- This is a **purposive, North-America-heavy sample**, not a census or a random sample of the global labor market.
- A keyword mention is not necessarily a minimum requirement. It may describe responsibilities, a preference, or related systems.
- Employer templates, source availability, query choices, and company size affect counts. Frequencies do not establish a skill’s scarcity, compensation, or hiring value.
- The 506-description cohort is keyword-defined, not a ground-truth employer taxonomy.
- Google/AMD targeted examples and the Tencent supplement are not mixed into the main wording-frequency denominator.
- The Tencent supplement provides one employer’s Chinese-language evidence, not a China-wide frequency estimate.
- Feeds can contain evergreen or older postings. Source availability on the observation date does not guarantee a currently actionable vacancy.
- Collection, screening, deduplication, and counts were automated. The shared indexes distinguish detailed qualitative reading from targeted responsibility/competency excerpts. There is **no claim that all 925 descriptions were manually read in full**.

## Findings from the broader sample

### 1. Training systems and performance form a coherent career direction

Employers describe work connecting model behavior with runtime efficiency, memory use, hardware characteristics, and researcher workflows. For example, Cerebras’ performance-mapping role combines modeling, benchmarking, prototyping, and architecture trade-offs. Waabi’s training-optimization role combines framework work, runtime/memory profiling, and tools used by researchers. [Cerebras](https://jobs.ashbyhq.com/cerebras/fe581188-2bc1-4fce-856d-2df0936a7f56), [Waabi](https://jobs.lever.co/waabi/eedaf111-0efd-4f8f-9c2d-ce829b5cb0eb)

**Implication:** partial rollout and Mamba2 training optimization should reinforce each other. Both demonstrate an ability to improve how ML workloads execute, at different software layers.

### 2. Evaluation infrastructure is substantive engineering work

Prime Intellect explicitly connects model-failure investigation with debugging task and scoring implementations. Microsoft’s evaluation systems description includes execution throughput, reproducibility, traceability, and regression checks. [Prime Intellect](https://www.primeintellect.ai/careers/7ef14297-51c3-45b1-abe4-890489a0bddb), [Microsoft AI](https://job-boards.greenhouse.io/microsoftcorporation/jobs/4425409009)

**Implication:** the HF32 investigation is useful evidence of evaluation judgment and numerical debugging. Its significance is the corrected interpretation of the failure, not merely changing a setting. Trajectory inspection and controlled ablations support the same capability.

### 3. Research productivity depends on dependable software

Mistral’s Forge role connects data preparation, post-training, evaluation, and systems debugging. Thinking Machines embeds software engineers within post-training teams. Deepgram describes accelerating experimentation through data systems, training infrastructure, and internal tooling. [Mistral](https://jobs.ashbyhq.com/mistral.ai/1808c0af-7352-4d0b-9e35-d3d6704e4759), [Thinking Machines](https://jobs.ashbyhq.com/thinkingmachines/4d51cb65-5e5b-42d2-8c28-7073b8574e4b), [Deepgram](https://jobs.ashbyhq.com/deepgram/9a030b32-d671-43e0-a221-4653bb73ba29)

**Implication:** code and tools adopted in subsequent training runs are important evidence. The résumé should communicate what the implementation enabled and who used it, alongside the technical details.

### 4. “ML infrastructure” includes different responsibilities

Training-runtime work involves execution, model/framework behavior, parallelism, and experiments. Cloud/platform work can involve job launching, compute integrations, retries, storage, networking, deployment, and operations. AWS SageMaker illustrates the latter scope. [AWS](https://www.amazon.jobs/en/jobs/10492392/software-development-engineer-ii-aws-sagemaker-ai)

**Implication:** the current evidence is stronger in training execution, profiling, and evaluation tooling than in operating an entire cloud or GPU-fleet platform. Scheduling experience is relevant, but it should not be presented as ownership of every surrounding service.

### 5. Hardware expertise transfers, but backend requirements differ

Some performance roles explicitly require substantial CUDA implementation experience. Other roles emphasize framework adaptation and diagnosis across accelerators. Liquid AI illustrates the former. Tencent’s heterogeneous-accelerator description explicitly names Ascend and includes precision debugging, framework adaptation, and end-to-end performance. [Liquid AI](https://jobs.ashbyhq.com/liquid-ai/dfc3bae5-003f-4438-b51a-4cdfdb4199ba), [Tencent](https://careers.tencent.com/jobdesc.html?postId=2021416952777568256)

**Implication:** retain the Ascend experience and explain the underlying engineering. Demonstrating transfer to another backend would strengthen applications where that backend is required; changing “Ascend” to “CUDA” in the résumé would be inaccurate.

### 6. Similar titles can describe different work

An agent harness can be a production service concerned with real-time transport, deployment, and customer latency, or a research execution environment concerned with rollouts, grading, and training data. Cartesia and Prime Intellect illustrate different responsibilities under related terminology. [Cartesia](https://jobs.ashbyhq.com/cartesia/16cd6cd7-454b-4e44-9a04-6a4677a3e920), [Prime Intellect](https://www.primeintellect.ai/careers/7ef14297-51c3-45b1-abe4-890489a0bddb)

**Implication:** use the responsibilities and required depth to assess a role. A broad title, or the absence of a years-of-experience threshold, does not establish a junior hiring bar.

## Recurring language and résumé translation

The following counts use **506 focused descriptions**. Topics overlap and are mentions, not mandatory requirements or market-wide percentages.

| Topic | Descriptions mentioning it | Employer boards mentioning it |
|---|---:|---:|
| Research collaboration | 321 | 53 |
| Python | 305 | 56 |
| Reliability / recovery | 291 | 59 |
| RL / post-training | 276 | 52 |
| Evaluation | 274 | 55 |
| PyTorch | 238 | 52 |
| Debugging | 196 | 42 |
| Throughput / latency | 187 | 51 |
| Scheduling / orchestration | 173 | 45 |
| Benchmarking | 167 | 41 |
| Profiling | 128 | 37 |
| Numerical correctness | 96 | 34 |
| Synthetic data / curation | 76 | 31 |
| Triton | 63 | 30 |
| LLVM / MLIR | 30 | 8 |

The lower frequency of a specialized term does not make the skill less valuable within its specialty. The practical lesson is to state the engineering capability first and use tools/backends as evidence.

| Work described in the conversation | Useful résumé language | Scope to preserve |
|---|---|---|
| Partial rollout | RL training efficiency; rollout scheduling; straggler mitigation; resumable execution | Do not rename it fully asynchronous training without confirming its actual semantics |
| Distilled SFT trajectories | Synthetic data generation and curation; trajectory distillation; LLM post-training | Describe the data work actually owned; do not invent scale or model improvements |
| msprof tools and guidance | Performance profiling; bottleneck diagnostics; research tooling; agent tool integration | The 24% latency result belongs to one matmul case |
| HF32 baseline issue | Numerical debugging; precision validation; evaluation reliability; root-cause analysis | One diagnosis does not establish expertise in designing low-precision training methods |
| Trajectory inspection | Agent failure analysis; model-trace analysis; interface debugging | Distinguish implemented fixes from proposed fixes |
| Harness/skills comparisons | Controlled experiments; ablation studies; benchmarking | Keep the 18-task subset and eager-PyTorch baseline explicit |
| Compiler investigation | Compiler integration; IR-level debugging; regression testing | Claim the concrete bug fix, not ownership of a complete compiler architecture |
| Mamba2 kernels | Training performance optimization; kernel/framework integration; hardware/software co-design | Separate kernel speedups from end-to-end training improvements |

## Career recommendation

### Primary direction: ML training systems and performance

Lead with partial rollout, the Mamba2 training-step improvement, and profiling. Deepen execution scheduling, concurrency, pause/resume semantics, policy-version handling, checkpoint consistency, and distributed-training behavior.

This direction combines the existing work most directly: understanding the workload, identifying what limits execution, changing the implementation, and measuring the effect.

### Second direction: evaluation and agent research tooling

Lead with the HF32 investigation, controlled comparisons, trajectory diagnostics, and tool integration. Deepen reproducible execution, numerical validation, measurement variance, regression detection, and data provenance.

Seek responsibility for reusable software that produces trustworthy feedback. The engineering depth and effect on research decisions are more informative than the number of experiments run.

### Related direction: framework integration and workload optimization

Lead with kernel/model integration, compiler debugging, model bring-up, and end-to-end gains. Deepen PyTorch execution and one target accelerator backend. This preserves the hardware foundation while allowing specialization to develop through broader model-execution work.

### Adjacent directions requiring additional evidence

- **Production ML platforms:** cloud operations, service reliability, deployment, networking, and storage ownership.
- **Independent RL research:** original method ownership and convincing experimental evidence of model improvement.
- **Specialist kernel/compiler positions:** broader implementation depth in the required backend or compiler subsystem.

These are development directions, not permanent exclusions. The résumé should represent the current evidence accurately while making the intended trajectory clear.

## Evidence worth strengthening

1. **Define the 20% result precisely.** Record whether it means wall-clock speedup, throughput, or step-time reduction; document the baseline, workload, variability, resource allocation, and learning-correctness checks.
2. **Quantify SFT work.** Recover trajectory counts, acceptance rates, token reductions, generation cost, and any measured downstream model effect.
3. **Make ownership reviewable.** Preserve code/PR links, tests, design notes, integration evidence, and the division of responsibility within the team.
4. **Show reusable engineering.** Reliable interfaces, regression checks, repeatable benchmarks, and adoption by others support the market responsibilities identified here.
5. **Demonstrate portability where relevant.** A concrete transfer of profiling or numerical-debugging methods to another backend can strengthen the case without claiming comprehensive expertise in that backend.

## Résumé decisions

- Preserve the official Huawei title and employment dates.
- Use a summary centered on **ML training systems, performance optimization, and evaluation reliability**.
- Keep the new project prominent and connect its tooling/data work to training outcomes.
- Give the compiler project a contribution-specific title: **Triton-to-NPU Compiler Debugging (LLVM/MLIR)**.
- Present the Mamba2 work as **Training Performance Optimization**, supported by the kernel implementation details and measured training impact.
- Retain relevant technical names such as verl, vLLM, msprof, Triton, Ascend C, and LLVM/MLIR as supporting evidence.
- Avoid adding unsupported keywords such as production Kubernetes operations, CUDA expertise, serving-system ownership, reward-model design, or independent authorship of ATRL’s full RL algorithm.
- Keep benchmark sizes, baselines, precision distinctions, and submission status accurate.

## Supporting research data

| File | Contents |
|---|---|
| [Main corpus](research/expanded-jd-corpus-2026-10-17.csv) | 865 deduplicated descriptions with employer, title, source URL, location, topics, and level signals |
| [Keyword evidence](research/keyword-evidence-2026-10-17.csv) | Mention counts by description and employer board |
| [Employer coverage](research/employer-coverage-2026-10-17.csv) | Coverage and collapsed variants by employer |
| [Topic co-occurrence](research/topic-cooccurrence-2026-10-17.csv) | Overlap between role topics and engineering terminology |
| [Chinese-language cross-check](research/china-language-crosscheck-2026-10-17.csv) | 60 Tencent descriptions with original titles and primary links |
| [Detailed reading index](research/close-reading-index-2026-10-17.csv) | Current-corpus matches from the qualitative review |
| [Targeted reading index](research/targeted-review-index-2026-10-17.csv) | Additional responsibility/competency excerpt review |

The shared tables contain metadata, topic labels, and source links. Raw job descriptions, local source slides, and the reviewed manuscript are not included in this repository.

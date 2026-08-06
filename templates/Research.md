SPARK Research & Scientific Investigation Template

Standardized Prompt Architecture for Academic Literature Reviews, Technology
Trade-Off Analysis, Market Research, and Evidence-Based Investigations

1. Introduction

The SPARK Research Template is a specialized, domain-agnostic framework designed
for researchers, academics, data analysts, technical writers, and product
strategists using AI systems (e.g., Claude, ChatGPT, Gemini).

Using Large Language Models for academic, scientific, or market research
presents distinct methodological risks:

  - Hallucinated Citations & Data: Unconstrained models frequently invent
    non-existent academic paper titles, fake author names, fabricated DOI
    numbers, or unverified statistical metrics.
  - Confirmation Bias & Unsubstantiated Claims: Models tend to confirm the
    user's implicit biases rather than evaluating counter-evidence or
    alternative hypotheses objectively.
  - Surface-Level Synthesis: Without explicit analytical frameworks, AI outputs
    generate generic summaries that lack methodological rigor, empirical depth,
    or structural trade-off evaluations.
  - Conflation of Fact, Assumption, and Speculation: Unstructured research
    prompts blur the boundaries between verified empirical data, working
    hypotheses, and speculative extrapolation.

The SPARK Research Template eliminates these risks by enforcing explicit
research questions, scope boundaries, evidence hierarchies, citation integrity
guardrails, bias mitigation rules, and structured trade-off matrices.

2. When to Use This Template

Use the SPARK Research Template across all scientific, academic, technical, and
market investigation activities:

  - Academic Literature Reviews: Systematic literature surveys (SLR),
    state-of-the-art (SOTA) technology evaluations, and research paper
    syntheses.
  - Technical Trade-Off & Architectural Analysis: Comparative benchmarks
    evaluating software frameworks, database engines, hardware architectures, or
    cloud deployment models.
  - Market & Competitive Research: Industry feasibility reports, competitor
    analysis matrices, regulatory compliance evaluations, and TAM/SAM/SOM market
    sizing studies.
  - Scientific & Clinical Investigations: Synthesizing empirical study findings,
    drug mechanism reviews, or medical protocol comparisons.
  - Policy & Strategy Investigations: Policy impact assessments, economic
    feasibility studies, and risk analysis reports.

3. When Not to Use This Template

Do not use the SPARK Research Template for:

  - Direct Software Code Generation: Writing functional application code or
    debugging scripts (use templates/Coding.md instead).
  - Direct Marketing Copywriting: Authoring ad creatives, email launch drips, or
    landing page marketing copy (use templates/Marketing.md instead).

4. How to Fill the Template

Authoring a research investigation prompt using the SPARK architecture follows a
five-phase flow:

+-----------------------------------------------------------------------------------+
|                        RESEARCH PROMPT AUTHORING WORKFLOW                         |
+-----------------------------------------------------------------------------------+
|  1. FORMULATE QUESTION     ──> Define Research Question, Scope & Non-Goals (Sec 2)|
|                                                                                   |
|  2. SET EVIDENCE BASE      ──> Define Known Facts, Assumptions, & Context (Sec 3) |
|                                                                                   |
|  3. SELECT METHODOLOGY     ──> Define Investigation Framework & Guardrails (Sec 4)|
|                                                                                   |
|  4. SPECIFY REPORT SCHEMA  ──> Define Matrix Layout, Citation Rules, & Format(Sec 5)|
|                                                                                   |
|  5. EMBED SCIENTIFIC AUDIT ──> Add Citation Check & Bias Audit Checklist (Sec 7)  |
+-----------------------------------------------------------------------------------+

5. Complete Blank Research SPARK Template

Below is the complete, annotated SPARK Research Template. Bracketed placeholders
indicate the specific research parameters required.

# 1. ROLE & IDENTITY
## 1.1 Role
[Define Research Specialty. Example: "Senior Research Scientist specializing in Distributed Systems Architecture and Empirical Performance Analysis"]

## 1.2 Cognitive Style
- [Research Methodology 1. Example: "First-Principles Evidence Synthesis & Empirical Analysis"]
- [Research Methodology 2. Example: "Systematic Bias Mitigation & Counter-Hypothesis Evaluation"]

## 1.3 Tone & Voice
Academic, objective, analytical, and precise. Avoid speculative language, hyperbole, or unsubstantiated claims.

---

# 2. OBJECTIVE
## 2.1 Primary Research Question
[Single declarative research question. Example: "What are the performance, memory, and scalability trade-offs between HNSW and IVF-PQ indexing algorithms in vector databases for high-dimensional embeddings?"]

## 2.2 Success Criteria
- [Evidence Requirement. Example: "Base analysis strictly on empirical benchmark data and peer-reviewed computer science literature"]
- [Analytical Depth. Example: "Include a structured trade-off evaluation matrix comparing QPS latency, memory footprint, and recall accuracy"]
- [Integrity Target. Example: "Zero hallucinated paper titles, DOIs, or unverified statistical claims"]

## 2.3 Non-Goals & Scope Boundaries
- [Out-of-scope topics. Example: "Do not evaluate flat (exact search) brute-force indexing methods"]
- [Boundary limit. Example: "Do not analyze vector database pricing models or commercial licensing terms"]

---

# 3. CONTEXT
## 3.1 Domain & Historical Background
- Research Domain: [e.g., Computer Science / Machine Learning / Vector Search Infrastructure]
- Baseline Context: [Provide verified background information or problem context]
- Target Audience: [e.g., Principal System Architects, Machine Learning Engineers, Academic Researchers]

## 3.2 Evidence Base & Known Parameters
- Known Empirical Facts: [List 2-3 verified facts or established baseline parameters]
- Working Assumptions: [List any assumptions that must be explicitly declared and tested]
- Data / Literature Sources: [Specify provided text snippets, paper URLs, or general academic pre-training knowledge]

---

# 4. EXECUTION
## 4.1 Research Methodology & Step-by-Step Logic
1. [Deconstruct Research Question: Break the core question down into specific technical dimensions]
2. [Evidence Extraction: Gather empirical metrics, benchmark data, and theoretical mechanisms]
3. [Counter-Argument Analysis: Evaluate edge cases, limitations, and potential counter-evidence]
4. [Synthesis & Trade-off Mapping: Construct comparative trade-off tables and summary findings]
5. [Citation & Integrity Audit: Verify that all facts are cited correctly and speculation is explicitly labeled]

## 4.2 Citation & Evidence Guardrails
- MUST strictly distinguish between verified empirical facts, theoretical hypotheses, and speculative extrapolations.
- MUST NOT fabricate paper titles, authors, DOIs, publication years, or statistical metrics under any circumstances.
- IF an academic citation or exact metric is uncertain, the model MUST explicitly state: `"Exact empirical source unverified; theoretical model indicates..."`

## 4.3 Bias Mitigation Rules
- MUST evaluate counter-arguments, failure modes, and architectural trade-offs for every option analyzed.
- MUST NOT declare a single "best overall" choice without specifying exact operational contexts and trade-off parameters.

---

# 5. OUTPUT SPECIFICATION
## 5.1 Format & Structure
Structured Academic/Technical Research Report formatted in Markdown using the following required layout:
1. Executive Summary & Core Findings
2. Systematic Technical Analysis (Detailed Sub-Sections)
3. Structured Trade-Off Evaluation Matrix (Markdown Table)
4. Limitations, Edge Cases, & Counter-Evidence
5. Explicit Assumptions & References / Source Declarations

## 5.2 Comparative Matrix Schema
[Define columns for trade-off evaluation table, e.g., Metric | Algorithm A | Algorithm B | Operational Trade-Off]

---

# 6. EXAMPLES
## 6.1 Unsubstantiated vs. Evidence-Based Research Synthesis

### Unsubstantiated Claim (Avoid):
"Vector database Index A is vastly superior to Index B and is the best choice for all AI applications."

### Evidence-Based Synthesis (Emulate):
"Index A achieves 3.2x higher query throughput (QPS) at 95% recall compared to Index B under high-dimensional (1536-d) workloads. However, Index A requires 4.1x more RAM for index construction, making Index B preferable for memory-constrained edge deployments."

---

# 7. VERIFICATION & REFINEMENT
## 7.1 Pre-Output Research Integrity Checklist
1. Are all citations and metrics explicitly verified or labeled as theoretical? [YES/NO]
2. Is the analysis free of unverified hyperbole ("vastly superior", "flawless")? [YES/NO]
3. Does the report include a structured trade-off matrix highlighting limitations? [YES/NO]
4. Are working assumptions explicitly separated from empirical facts? [YES/NO]

## 7.2 Self-Correction Loop
- IF any audit check evaluates to NO, rewrite the report internally before rendering final output.

---

# 8. NOTES
## 8.1 Operational Metadata
- Framework Version: SPARK Research v1.0
- Target Model: [e.g., Claude Fable 5 / GPT-5.6-sol]
- Recommended Parameters: Temperature: 0.0 (Strict analytical determinism)

6. Explanation of Every SPARK Section for Research

6.1 Section 1: Role & Identity

  - Purpose: Establishes the model's scientific identity, research domain
    expertise, and analytical reasoning principles.
  - Research Application: Sets an academic tone (e.g., "Senior Principal
    Scientist", "Biostatistician") and enforces analytical styles focused on
    evidence synthesis and bias controls.

6.2 Section 2: Objective

  - Purpose: Formulates the core research question, success parameters, and
    scope boundaries.
  - Research Application: Defines a precise, testable primary research question
    while using Section 2.3 (Non-Goals) to prevent scope creep and off-topic
    tangents.

6.3 Section 3: Context

  - Purpose: Documents domain background, target audience depth, known facts,
    and working assumptions.
  - Research Application: Establishes a clear baseline of known empirical facts
    versus working assumptions, ensuring the model evaluates hypotheses against
    a defined problem context.

6.4 Section 4: Execution

  - Purpose: Directs scientific methodology, evidence extraction, citation
    rules, and bias mitigation guardrails.
  - Research Application: Enforces structured investigation steps (literature
    review, counter-argument analysis, trade-off mapping) and strict guardrails
    banning fabricated citations or unverified statistical claims.

6.5 Section 5: Output Specification

  - Purpose: Controls report structure, executive summaries, trade-off matrix
    schemas, and citation formats.
  - Research Application: Mandates standardized academic layouts (Executive
    Summary, Technical Synthesis, Trade-off Matrix, Limitations, References).

6.6 Section 6: Examples

  - Purpose: Demonstrates the difference between subjective, unsubstantiated
    claims and high-rigor, evidence-based research synthesis.
  - Research Application: Anchors model performance on objective, quantitative,
    and contextual research reporting.

6.7 Section 7: Verification & Refinement

  - Purpose: Implements a pre-publication research integrity checklist auditing
    citations, hyperbole, and bias.
  - Research Application: Forces the model to evaluate its output for
    hallucinations or unverified assumptions before completing generation.

6.8 Section 8: Notes

  - Purpose: Tracks operational metadata, literature cutoff dates, and target
    LLM engine parameters.
  - Research Application: Records model parameters (setting temperature: 0.0 for
    strict determinism) and documents literature cutoff boundaries.

7. Research Best Practices

1.  Formulate Precise, Testable Research Questions: Avoid asking broad queries
    like "Tell me about Vector DBs." Ask focused, technical questions ("What are
    the QPS, recall, and memory trade-offs between HNSW and IVF-PQ vector
    indexing?").
2.  Explicitly Ban Citation Hallucinations: Always include strict guardrails in
    Section 4.2 requiring the model to state explicitly when exact paper
    citations or metrics are unverified.
3.  Separate Facts from Assumptions and Speculation: Use Section 3.2 to define
    baseline empirical facts, and mandate in Section 4.2 that speculative
    extrapolations be clearly labeled as hypothetical.
4.  Enforce Trade-Off Matrices: Require Markdown comparative tables evaluating
    metrics, operational benefits, limitations, and edge-case failure modes
    side-by-side.
5.  Mitigate Confirmation Bias: Mandate in Section 4.3 that the model analyze
    counter-arguments, failure modes, and alternative hypotheses for every
    option evaluated.

8. Common Mistakes in AI Research Prompts

| Mistake                                | Impact on AI Output                                                  | SPARK Remediation                                            |
| :------------------------------------- | :------------------------------------------------------------------- | :----------------------------------------------------------- |
| **Unbounded Research Scope**           | Output is surface-level, generic, and lacks technical depth.         | Define explicit non-goals & scope bounds in **Section 2.3**. |
| **Tolerating Citation Hallucinations** | Model fabricates non-existent paper titles, DOIs, and metrics.       | Enforce zero-hallucination guardrails in **Section 4.2**.    |
| **Confirmation Bias**                  | Model confirms user assumptions without evaluating counter-evidence. | Mandate counter-hypothesis analysis in **Section 4.3**.      |
| **Conflating Fact and Speculation**    | Theoretical hypotheses are presented as verified empirical facts.    | Require explicit evidence labeling in **Section 4.2 & 7.1**. |
| **Missing Trade-Off Context**          | Model declares a single "best" solution without operational context. | Require comparative trade-off tables in **Section 5.2**.     |

9. Example Prompts

Example 1: Academic Literature Review & Technology Trade-Off Analysis

Completed SPARK Prompt

# 1. ROLE & IDENTITY
## 1.1 Role
Principal Computer Science Researcher specializing in Distributed Database Systems and Vector Search Architecture.

## 1.2 Cognitive Style
- First-Principles Systems Analysis
- Methodological Rigor & Empirical Evidence Synthesis

## 1.3 Tone & Voice
Academic, objective, precise, and analytical. Omit non-technical summaries and non-rigorous generalizations.

---

# 2. OBJECTIVE
## 2.1 Primary Research Question
What are the architectural, performance, and operational memory trade-offs between Hierarchical Navigable Small World (HNSW) graphs and Inverted File with Product Quantization (IVF-PQ) for approximate nearest neighbor (ANN) vector search in high-dimensional (>1000 dimensions) deployments?

## 2.2 Success Criteria
- Evaluate trade-offs across three primary metrics: Query Throughput (QPS at 95% Recall), Index Construction Memory Footprint (RAM), and Index Build Latency.
- Include a Markdown trade-off matrix comparing performance across vector dimensions (1536-d vs. 768-d).
- Zero hallucinated paper titles, DOIs, or unverified statistical claims.

## 2.3 Non-Goals & Scope Boundaries
- Do not analyze exact brute-force (Flat) search algorithms.
- Do not evaluate commercial database pricing or vendor cloud hosting costs.

---

# 3. CONTEXT
## 3.1 Domain Context
- Domain: High-dimensional Vector Database Indexing (ANN search).
- Target Audience: Systems Architects designing large-scale (>100 Million vectors) enterprise retrieval-augmented generation (RAG) platforms.

## 3.2 Evidence Base & Known Parameters
- Fact 1: HNSW graphs provide high recall and fast query response but require keeping the entire graph structure in uncompressed RAM.
- Fact 2: IVF-PQ uses vector quantization to compress embeddings, significantly lowering RAM usage at the expense of recall and indexing CPU overhead.

---

# 4. EXECUTION
## 4.1 Step-by-Step Research Methodology
1. Architectural Deconstruction: Explain the underlying graph traversal logic of HNSW vs. the inverted list quantization mechanics of IVF-PQ.
2. Empirical Performance Comparison: Analyze QPS throughput, recall trade-offs, and memory footprints under 1536-dimensional workloads (e.g., OpenAI embeddings).
3. Operational Failure Mode Analysis: Identify memory fragmentation, index build scaling limits, and dynamic vector update limitations for both approaches.
4. Trade-Off Synthesis: Construct a comparative Markdown matrix mapping workloads to optimal index choices.

## 4.2 Citation Integrity Guardrails
- MUST strictly distinguish between verified theoretical mechanics and empirical benchmarks.
- MUST NOT fabricate paper titles, authors, DOIs, or publication years. IF an exact empirical source is unverified, state explicitly: `"Empirical benchmark unverified; theoretical model indicates..."`

## 4.3 Bias Mitigation Rules
- MUST NOT declare a single "best overall" algorithm; frame selection strictly around operational constraints (e.g., RAM budget vs. QPS requirement).

---

# 5. OUTPUT SPECIFICATION
## 5.1 Format & Structure
Structured Markdown Report containing:
1. Executive Technical Summary
2. Architectural Mechanics (HNSW vs. IVF-PQ)
3. Quantitative Performance Comparison
4. Comparative Trade-Off Matrix (Markdown Table)
5. Production Workload Recommendations & Operational Edge Cases

## 5.2 Comparative Matrix Schema
| Metric / Dimension | HNSW Index | IVF-PQ Index | Primary System Trade-Off |
| :--- | :--- | :--- | :--- |
| **QPS (at 95% Recall)** | [Value / Assessment] | [Value / Assessment] | [Trade-off Analysis] |
| **RAM Footprint (100M Vectors)**| [Value / Assessment] | [Value / Assessment] | [Trade-off Analysis] |
| **Index Construction Time** | [Value / Assessment] | [Value / Assessment] | [Trade-off Analysis] |
| **Dynamic Insert Support** | [Value / Assessment] | [Value / Assessment] | [Trade-off Analysis] |

---

# 7. VERIFICATION & REFINEMENT
## 7.1 Pre-Output Integrity Checklist
1. Are all citations and empirical claims verified or explicitly labeled as theoretical models? [YES/NO]
2. Is the report completely free of unverified hyperbole? [YES/NO]
3. Does the trade-off matrix evaluate dynamic vector inserts and memory constraints? [YES/NO]

## 7.2 Self-Correction Loop
- IF checks fail, correct output internally before rendering final response.

---

# 8. NOTES
## 8.1 Operational Metadata
- Framework: SPARK Research v1.0
- Target Model: Claude 3.5 Sonnet
- Temperature: 0.0

Why It Works

  - Defines a clear, high-depth technical research question (HNSW vs. IVF-PQ
    indexing trade-offs).
  - Mandates quantitative evaluation across QPS, RAM, and recall metrics while
    banning citation hallucinations.
  - Uses a structured comparative matrix to frame selection around operational
    context rather than subjective assertions.

Example 2: Market Feasibility & Technology Evaluation (Serverless vs. Kubernetes)

Completed SPARK Prompt

# 1. ROLE & IDENTITY
## 1.1 Role
Lead Enterprise Cloud Infrastructure Analyst and CTO Advisory Consultant.

## 1.2 Cognitive Style
- Total Cost of Ownership (TCO) Financial Modeling
- Risk & Architectural Scalability Assessment

---

# 2. OBJECTIVE
## 2.1 Primary Research Question
What are the financial (TCO), operational, and architectural trade-offs of deploying a microservices platform on Serverless Container Infrastructure (AWS Fargate) versus Managed Kubernetes (AWS EKS) for a mid-market fintech application?

## 2.2 Success Criteria
- Calculate cost break-even points based on request throughput and steady-state compute patterns.
- Evaluate operational overhead (SRE staffing costs, cluster maintenance, security patching).
- Include a 3-year TCO Comparison Matrix.

---

# 3. CONTEXT
## 3.1 Scenario Parameters
- Workload Profile: 50 microservices, average traffic of 5,000 requests/sec with predictable 3x peak spikes during market hours.
- Compliance Bounds: PCI-DSS Level 1 compliance required.
- Current Team: 12 Software Engineers, 1 dedicated Site Reliability Engineer (SRE).

---

# 4. EXECUTION
## 4.1 Research Steps
1. TCO Financial Modeling: Compare AWS Fargate per-vCPU/GB pricing against AWS EKS control plane and worker node EC2 pricing across steady-state vs. bursting workloads.
2. Operational Complexity Assessment: Evaluate Kubernetes cluster upgrade overhead, security patching, and SRE staffing requirements versus Serverless managed infrastructure.
3. Latency & Cold-Start Analysis: Compare cold-start impacts on tail latency (p99) for financial transaction endpoints.
4. Final Feasibility Matrix: Construct a decision framework mapping team size and request volume to the optimal compute deployment model.

## 4.2 Guardrails
- MUST explicitly declare all assumed EC2/Fargate pricing baseline figures used in calculations.
- MUST NOT recommend EKS unless the organization possesses dedicated SRE resources to manage control plane updates and cluster networking.

---

# 5. OUTPUT SPECIFICATION
## 5.1 Structure
Structured Executive Feasibility Brief with:
- Executive Summary & Recommendation
- Financial TCO Break-Even Analysis
- Operational Complexity & Compliance Evaluation
- 3-Year TCO Comparison Table

Why It Works

  - Defines real-world system workloads (5,000 req/sec, PCI-DSS compliance) to
    ground cloud infrastructure evaluation.
  - Evaluates non-software costs (SRE staffing overhead) alongside direct cloud
    compute infrastructure pricing.

10. Copy-and-Paste Version

Copy this clean, unannotated block to start authoring research and scientific
prompts:

# 1. ROLE & IDENTITY
## 1.1 Role
[RESEARCH_SPECIALTY_TITLE]

## 1.2 Cognitive Style
- [RESEARCH_METHODOLOGY_1]
- [RESEARCH_METHODOLOGY_2]

## 1.3 Tone & Voice
Academic, objective, analytical, and precise. Avoid speculative language, hyperbole, or unsubstantiated claims.

---

# 2. OBJECTIVE
## 2.1 Primary Research Question
[PRIMARY_RESEARCH_QUESTION]

## 2.2 Success Criteria
- [EVIDENCE_OR_METRIC_REQUIREMENT]
- [ANALYTICAL_DEPTH_TARGET]
- [INTEGRITY_OR_CITATION_TARGET]

## 2.3 Non-Goals & Scope Boundaries
- [OUT_OF_SCOPE_TOPIC_1]
- [SCOPE_BOUNDARY_2]

---

# 3. CONTEXT
## 3.1 Domain & Historical Background
- Research Domain: [DOMAIN]
- Baseline Context: [BACKGROUND_CONTEXT]
- Target Audience: [TARGET_AUDIENCE]

## 3.2 Evidence Base & Known Parameters
- Known Empirical Facts: [FACTS]
- Working Assumptions: [ASSUMPTIONS]
- Data / Literature Sources: [DATA_SOURCES]

---

# 4. EXECUTION
## 4.1 Research Methodology & Step-by-Step Logic
1. [STEP_1_DECONSTRUCT_QUESTION]
2. [STEP_2_GATHER_EVIDENCE]
3. [STEP_3_COUNTER_ARGUMENT_ANALYSIS]
4. [STEP_4_SYNTHESIS_AND_MATRIX_MAPPING]
5. [STEP_5_CITATION_AND_INTEGRITY_AUDIT]

## 4.2 Citation & Evidence Guardrails
- MUST strictly distinguish between verified empirical facts, theoretical hypotheses, and speculative extrapolations.
- MUST NOT fabricate paper titles, authors, DOIs, publication years, or statistical metrics under any circumstances.
- IF a citation or metric is uncertain, explicitly state: `"Exact empirical source unverified; theoretical model indicates..."`

## 4.3 Bias Mitigation Rules
- MUST evaluate counter-arguments, failure modes, and trade-offs for every option analyzed.
- MUST NOT declare a single "best overall" choice without specifying exact operational contexts.

---

# 5. OUTPUT SPECIFICATION
## 5.1 Format & Structure
[FORMAT_SPECIFICATION]

## 5.2 Comparative Matrix Schema
[MATRIX_SCHEMA_TABLE]

---

# 6. EXAMPLES
## 6.1 Unsubstantiated vs. Evidence-Based Research Synthesis
### Unsubstantiated Claim (Avoid):
[WEAK_UNSUBSTANTIATED_EXAMPLE]

### Evidence-Based Synthesis (Emulate):
[STRONG_EVIDENCE_BASED_EXAMPLE]

---

# 7. VERIFICATION & REFINEMENT
## 7.1 Pre-Output Research Integrity Checklist
1. Are citations and metrics explicitly verified or labeled as theoretical? [YES/NO]
2. Is the analysis free of unverified hyperbole? [YES/NO]
3. Does the report include a structured trade-off matrix highlighting limitations? [YES/NO]
4. Are working assumptions explicitly separated from empirical facts? [YES/NO]

## 7.2 Self-Correction Loop
- IF any audit check evaluates to NO, rewrite report internally before finalizing generation.

---

# 8. NOTES
## 8.1 Operational Metadata
- Framework Version: SPARK Research v1.0
- Target Model: [MODEL_ID]
- Recommended Parameters: Temperature: 0.0

11. Summary

The SPARK Research Template transforms generic AI summaries into
methodology-driven, evidence-based research reports.

By enforcing precise research questions, explicit scope boundaries, strict
citation integrity rules, counter-hypothesis evaluation, and structured
trade-off matrices, researchers can deploy AI systems to accelerate academic,
technical, and market investigations with total confidence.

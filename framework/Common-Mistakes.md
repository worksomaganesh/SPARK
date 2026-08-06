SPARK Framework: Common Prompting Mistakes Guide

Identifying, Understanding, and Remediating Anti-Patterns in Prompt Engineering

1. Introduction

The Common Prompting Mistakes Guide is the official troubleshooting and
anti-pattern documentation for the SPARK Framework.

In production AI application design, low-quality model outputs, hallucinated
data, schema drift, and unexpected costs are rarely caused by fundamental
limitations of the Large Language Model (LLM). Instead, they are usually caused
by structural flaws in the input prompt.

When a prompt lacks explicit context, uses ambiguous instructions, mixes goals
with workflows, or omits verification checks, the model defaults to broad
pre-training distributions. This introduces non-deterministic outputs into
software environments.

This guide analyzes twenty common prompting mistakes. For every anti-pattern, it
explains:

  - The Root Cause: Why developers make the mistake.
  - The System Mechanics: How the flaw degrades LLM self-attention and token
    prediction.
  - The Diagnostic Indicators: How to spot the error in your codebase.
  - The SPARK Remediation: How to fix the flaw using modular SPARK sections.
  - Concrete Examples: Comparative code blocks demonstrating the transition from
    an Incorrect Prompt to a Correct SPARK Prompt.

2. Why Prompt Mistakes Matter

In software systems powered by LLMs, prompt bugs are equivalent to runtime logic
errors in traditional software code.

+-----------------------------------------------------------------------------------+
|                           THE SYSTEMIC COST OF PROMPT BUGS                         |
+-----------------------------------------------------------------------------------+
| FAULTY PROMPT DESIGN                      │ SPARK SYSTEM DESIGN                   |
+-------------------------------------------+---------------------------------------+
| • High output variance across runs        │ • Bounded, deterministic execution    |
| • Frequent parsing & schema errors        │ • Strict programmatic output formats  |
| • Increased token costs & latency         │ • Optimized token consumption & speed |
| • Unhandled edge cases & hallucinations   │ • Explicit fallback & self-audit loops|
| • Inability to version or refactor code   │ • Modular, auditable, testable layout |
+-------------------------------------------+---------------------------------------+

Prompt errors create four major operational risks:

1.  Financial and Latency Waste: Verbose, unstructured prompts consume
    unnecessary context window tokens, increasing API costs and execution
    latency.
2.  Programmatic Pipeline Failures: Output format drift breaks downstream
    JSON/YAML data parsers, causing crashes in production API endpoints.
3.  Security Vulnerabilities: Missing guardrails make applications vulnerable to
    context injection, data exfiltration, and unexpected code execution.
4.  Maintenance Friction: Monolithic, disorganized prompts cannot be debugged,
    unit-tested, or version-controlled across developer teams.

Eliminating these common mistakes ensures your natural language prompts operate
like production-grade software artifacts.

3. Writing Vague Objectives

3.1 What the Mistake Is

Declaring a generic, broad, or ill-defined goal without specifying success
metrics or explicit boundaries.

3.2 Why People Make It

Developers often treat the LLM as a human colleague who shares implicit
background knowledge, assuming the model will automatically understand what a
"good" result looks like.

3.3 Why It Reduces Output Quality

When an objective is vague, the model's self-attention mechanism distributes
probability weights broadly across a wide set of potential token paths. This
causes high output variance, unfocused responses, and scope creep.

3.4 How to Recognize It

  - Prompts containing terms like "analyze this," "fix this code," "write a
    document," or "make this better" without defining specific deliverables.
  - Output responses that vary wildly in structure and length across test runs.

3.5 How to Fix It Using SPARK

Use Section 2 (Objective) to declare a single primary goal supported by
measurable Success Criteria and explicit Non-Goals.

3.6 Practical Comparison

Incorrect Prompt

Analyze our customer churn data and give me some good insights.

Correct SPARK Prompt

# 2. OBJECTIVE
## 2.1 Primary Goal
Analyze the provided quarterly churn CSV dataset to isolate the top three operational drivers of account cancellations among enterprise-tier accounts.

## 2.2 Success Criteria
- Rank drivers by lost Annual Contract Value (ACV).
- Include exact percentage contributions for each identified driver.
- Restrict executive findings to a concise 3-item bulleted list.

## 2.3 Non-Goals
- Do not analyze mid-market or self-serve customer tiers.
- Do not generate marketing or customer retention copy.

3.7 Key Lesson

Define a single primary goal bounded by measurable success metrics and explicit
non-goals in Section 2.

4. Providing Insufficient Context

4.1 What the Mistake Is

Asking the model to execute a task without supplying necessary environmental
parameters, framework versions, database schemas, or system constraints.

4.2 Why People Make It

Developers working daily in a specific codebase often forget that the LLM lacks
visibility into their local environment, internal naming conventions, and
runtime dependencies.

4.3 Why It Reduces Output Quality

Without explicit environment context, the model fills in missing details using
generic pre-training data. This produces code or analysis that is syntactically
valid but fails when deployed to your specific environment.

4.4 How to Recognize It

  - Generated code uses deprecated library methods or wrong language syntax.
  - Generated SQL queries refer to non-existent tables or field names.

4.5 How to Fix It Using SPARK

Consolidate software stack versions, API parameters, database schemas, and
audience parameters inside Section 3 (Context).

4.6 Practical Comparison

Incorrect Prompt

Write a database query to aggregate user spending over the last 30 days.

Correct SPARK Prompt

# 3. CONTEXT
## 3.1 Technical Constraints
- Database Engine: PostgreSQL 16.1
- Schema: `users` (id UUID, created_at TIMESTAMPTZ)
- Schema: `transactions` (id UUID, user_id UUID, amount_cents INT, status VARCHAR, created_at TIMESTAMPTZ)
- Runtime Index: `transactions(user_id, created_at)`
- Parameter Bounds: Only aggregate rows where `status = 'COMPLETED'`.

4.7 Key Lesson

Provide exact schemas, runtime versions, and environment constraints in
Section 3 to eliminate model guesswork.

5. Giving Too Much Unnecessary Context

5.1 What the Mistake Is

Dumping thousands of lines of raw, unfiltered logs, irrelevant code, or long
conversational threads into the context window.

5.2 Why People Make It

It is easier to copy and paste entire files into a prompt than to edit and
isolate the relevant data payload.

5.3 Why It Reduces Output Quality

Excessive context pollutes the model's self-attention matrix. Critical
instructions get lost in noisy background text (a phenomenon known as the Lost
in the Middle effect), increasing token cost and inference latency.

                  ATTENTION POLLUTION FROM CONTEXT DUMPING
                  
Unfiltered Context Dump:
[10,000 lines of raw server logs, debug noise, and HTTP headers]
  └── Attention scores diluted across irrelevant tokens (High Latency & Errors)

Targeted SPARK Payload:
# 3. CONTEXT -> [20 lines of isolated error stack traces]
  └── Attention scores focused directly on critical failure tokens

5.4 How to Recognize It

  - Prompts exceeding thousands of tokens for simple extraction or bug-fixing
    tasks.
  - The model ignores key instructions located near the middle of the prompt
    payload.

5.5 How to Fix It Using SPARK

Filter input payloads to include only relevant stack traces, data rows, or code
snippets within Section 3 (Context).

5.6 Practical Comparison

Incorrect Prompt

Here is our entire 5,000-line application log file from today: [PASTES 5,000 LINES OF UNFILTERED LOGS]. Find out why the server crashed.

Correct SPARK Prompt

# 3. CONTEXT
## 3.1 Isolated Error Log
2024-10-15T14:22:01Z [FATAL] postgresql_pool: Connection pool exhausted. Max connections: 100, Active: 100, Waiting: 42.
2024-10-15T14:22:03Z [ERROR] api_server: GET /api/v1/orders - HTTP 500 - Timeout waiting for database connection.

## 3.2 System Parameters
- Database Pool Max Size: 100
- API Handler Timeout: 5000ms

5.7 Key Lesson

Filter raw context payloads to include only essential data, protecting the
model's attention mechanism and reducing costs.

6. Assigning Unrealistic Roles

6.1 What the Mistake Is

Assigning hyperbolic, exaggerated, or meaningless personas (e.g., "You are an
all-knowing super-intelligence").

6.2 Why People Make It

Early prompting myths suggested that praising the AI or assigning exaggerated
titles would magically unlock higher reasoning capabilities.

6.3 Why It Reduces Output Quality

Exaggerated personas provide no meaningful constraints on the model's activation
space. They consume token budget without establishing practical domain limits or
analytical approaches.

6.4 How to Recognize It

  - Prompts using grand statements like "You are the greatest coder who ever
    lived" or "You have an IQ of 300."

6.5 How to Fix It Using SPARK

Use Section 1 (Role & Identity) to assign realistic, functional titles (e.g.,
"Principal Security Engineer") paired with grounded analytical methodologies.

6.6 Practical Comparison

Incorrect Prompt

You are an all-knowing AI genius who writes perfect code without any bugs. Fix my function.

Correct SPARK Prompt

# 1. ROLE & IDENTITY
## 1.1 Role
You are a Staff Rust Systems Engineer specializing in memory management, concurrency safety, and zero-cost abstractions.

## 1.2 Cognitive Style
- Defensive Programming
- Strict Borrow Checker Compliance
- Zero-Allocation Systems Design

6.7 Key Lesson

Assign functional titles paired with specific analytical methodologies in
Section 1 to establish grounded domain expertise.

7. Using Multiple Conflicting Roles

7.1 What the Mistake Is

Forcing the model to adopt multiple, mutually exclusive personas within a single
prompt (e.g., acting as a creative fiction writer and a strict static-code
analysis engine simultaneously).

7.2 Why People Make It

Developers attempt to complete complex, multi-stage pipelines using a single
system prompt.

7.3 Why It Reduces Output Quality

Assigning conflicting roles splits the model's cognitive perspective. The tone,
terminology, and analysis rules of one persona contaminate the output of the
other.

7.4 How to Recognize It

  - Role statements like "You are a friendly customer support representative and
    a strict legal compliance auditor."
  - Generated outputs that switch awkwardly between informal commentary and
    formal technical analysis.

7.5 How to Fix It Using SPARK

Select a single primary role in Section 1 (Role & Identity). If a workflow
requires multiple distinct perspectives, split it into separate, modular SPARK
prompts executed sequentially.

7.6 Practical Comparison

Incorrect Prompt

# 1. ROLE & IDENTITY
You are a creative marketing copywriter who writes engaging social media posts and a strict compliance lawyer who verifies financial regulations.

Correct SPARK Prompt

# 1. ROLE & IDENTITY
## 1.1 Role
You are a Lead Financial Regulatory Compliance Officer specializing in FINRA marketing disclosures for retail investment products.

## 1.2 Cognitive Style
Risk-Averse, Statutory Analysis, Precise Legal Verification.

7.7 Key Lesson

Assign a single, clear role per prompt. Decouple complex multi-role workflows
into separate, modular SPARK prompts.

8. Mixing Objective with Instructions

8.1 What the Mistake Is

Combining the ultimate goal (WHAT) with operational execution logic (HOW) into a
single unstructured text block.

8.2 Why People Make It

Natural human speech routinely mixes objectives and execution steps in
conversational instructions.

8.3 Why It Reduces Output Quality

Combining goals and step-by-step logic dilutes self-attention focus. It makes
updating execution steps difficult without accidentally altering the core
project targets.

                 DECOUPLING GOALS FROM WORKFLOWS
                 
Unstructured Text (Entangled):
"My goal is to clean CSV data by stripping spaces, removing duplicate emails, and outputting JSON..."
  └── Hard to update logic without altering target goal definitions.

SPARK Modular Layout (Decoupled):
# 2. OBJECTIVE ──> Target State: "Clean, deduplicated customer array."
# 4. EXECUTION ──> Step-by-Step Logic: "1. Trim spaces. 2. Filter regex. 3. Deduplicate."
  └── Clear separation allows independent updates and testing.

8.4 How to Recognize It

  - Prompts that lack clear structural boundaries between goals, workflows, and
    output formatting rules.

8.5 How to Fix It Using SPARK

Isolate the target goal in Section 2 (Objective) and place step-by-step
operational rules in Section 4 (Execution).

8.6 Practical Comparison

Incorrect Prompt

I want to create a customer dashboard, so you need to fetch data from the REST API, process the JSON payload, extract the active users, sort them by registration date, and render a HTML table.

Correct SPARK Prompt

# 2. OBJECTIVE
## 2.1 Primary Goal
Generate a clean HTML user dashboard displaying active customer metrics.

---

# 4. EXECUTION
## 4.1 Step-by-Step Logic
1. Parse the incoming JSON payload from the provided API endpoint.
2. Filter for user objects where `status == 'ACTIVE'`.
3. Sort active user objects by `registered_at` timestamp in descending order.
4. Render the sorted array into an HTML table structure.

8.7 Key Lesson

Separate WHAT success looks like (Section 2) from HOW the task is processed
(Section 4).

9. Writing Ambiguous Instructions

9.1 What the Mistake Is

Using subjective terms like "make it fast," "provide a deep analysis," "keep it
concise," or "make it readable."

9.2 Why People Make It

Subjective words are convenient shortcuts in human conversation, where shared
context clarifies meaning.

9.3 Why It Reduces Output Quality

Subjective adjectives have no fixed quantitative boundaries in the model's
vocabulary space. This leads to unpredictable output lengths, inconsistent
detail, and variable formatting across runs.

9.4 How to Recognize It

  - Prompts relying on adjectives like "concise," "detailed," "clean," "fast,"
    or "suitable."
  - Output lengths that vary wildly between 50 words and 1,000 words across
    executions.

9.5 How to Fix It Using SPARK

Replace subjective words with quantitative metrics, exact bounds, and clear
operational rules in Section 4 (Execution) and Section 5 (Output Specification).

9.6 Practical Comparison

Incorrect Prompt

Write a short, clean summary of this technical article. Make it readable and concise.

Correct SPARK Prompt

# 2. OBJECTIVE
## 2.1 Primary Goal
Generate a technical summary of the provided article for Systems Engineers.

## 2.2 Success Criteria
- Length MUST be strictly between 150 and 200 words.
- Format as a 3-item bulleted list (max 25 words per bullet).
- Target a Flesch-Kincaid Reading Ease score of 50.0-60.0.

9.7 Key Lesson

Replace subjective adjectives with measurable parameters, exact word counts, and
structural constraints.

10. Giving Conflicting Instructions

10.1 What the Mistake Is

Including mutually exclusive instructions across different parts of the prompt
(e.g., asking for an exhaustive deep-dive report while restricting the total
length to 50 words).

10.2 Why People Make It

Prompts grow organically over time. Developers continuously append new
constraints without auditing existing rules for logical collisions.

10.3 Why It Reduces Output Quality

Conflicting rules force the model to arbitrarily decide which constraint to
follow and which to ignore. This introduces instability into production
pipelines.

10.4 How to Recognize It

  - The model routinely violates one specific rule while attempting to satisfy
    another.
  - Prompts containing contradictory statements like "Be extremely thorough" and
    "Keep it as brief as possible."

10.5 How to Fix It Using SPARK

Audit instructions across Section 2 (Objective), Section 4 (Execution), and
Section 5 (Output Specification) to eliminate logic collisions.

10.6 Practical Comparison

Incorrect Prompt

# 2. OBJECTIVE
Provide an exhaustive architectural deep-dive into our entire microservices platform, explaining every service dependency in detail.

# 5. OUTPUT SPECIFICATION
Limit your total response strictly to a single bulleted list of under 50 words.

Correct SPARK Prompt

# 2. OBJECTIVE
Provide a high-level executive summary highlighting the top five microservice dependencies in our platform architecture.

# 5. OUTPUT SPECIFICATION
- Format: Bulleted list containing exactly 5 items.
- Item Bounds: 15 to 20 words per bullet point.
- Total Word Budget: Max 100 words.

10.7 Key Lesson

Audit your prompt sections systematically to identify and eliminate conflicting
instructions.

11. Missing Constraints

11.1 What the Mistake Is

Failing to specify negative boundaries (MUST NOT rules) or failure thresholds,
leaving the model free to execute edge cases unpredictably.

11.2 Why People Make It

Developers focus entirely on the happy-path execution flow, forgetting that LLMs
require explicit boundary rules to avoid undesirable behaviors.

11.3 Why It Reduces Output Quality

Without negative constraints, models will introduce external third-party
dependencies, invent unverified facts, make breaking API changes, or output
conversational filler text.

11.4 How to Recognize It

  - Generated code introduces unauthorized third-party libraries.
  - Model outputs include conversational preambles ("Here is your requested
    response:").

11.5 How to Fix It Using SPARK

Add explicit, capitalized MUST and MUST NOT statements to Section 4.2
(Guardrails).

11.6 Practical Comparison

Incorrect Prompt

Refactor this Python code snippet to improve execution speed.

Correct SPARK Prompt

# 4. EXECUTION
## 4.1 Step-by-Step Logic
1. Identify computational bottlenecks in the nested loop structure.
2. Vectorize operations using `numpy` array methods.

## 4.2 Guardrails
- MUST maintain existing function signatures and parameter names.
- MUST NOT introduce third-party package dependencies outside `numpy`.
- MUST NOT alter existing unit test assertion behaviors.

11.7 Key Lesson

Define explicit MUST and MUST NOT guardrails in Section 4.2 to keep execution
bounded.

12. Over-Constraining the AI

12.1 What the Mistake Is

Overwhelming the prompt with dozens of micro-managed, micro-level rules that
restrict the model's reasoning space.

12.2 Why People Make It

After experiencing an edge-case output failure, developers react by adding
hyper-specific rules for every potential edge case.

12.3 Why It Reduces Output Quality

When a prompt contains too many micro-constraints, the model's self-attention
capacity is consumed entirely by rule validation. This leads to broken logic,
missed instructions, or stalled execution.

                     THE CONSTRAINT BALANCING SPECTRUM
                     
  Under-Constrained                    Balanced (SPARK)                    Over-Constrained
+--------------------+               +-------------------+               +-------------------+
| Unbounded output   |               | Explicit boundaries|               | Rule collisions   |
| High variance      |               | Bounded reasoning |               | Stalled logic     |
| Frequent drift     |               | High reliability  |               | Skipped steps     |
+--------------------+               +-------------------+               +-------------------+

12.4 How to Recognize It

  - Prompts containing long lists of hyper-specific micro-rules (e.g., "Do not
    use the letter 'e'", "Ensure word 4 is a verb").
  - The model fails to complete the core task because it is trapped trying to
    satisfy competing micro-rules.

12.5 How to Fix It Using SPARK

Consolidate micro-rules into high-level, clear guardrails in Section 4.2, and
move structural output requirements to Section 5.

12.6 Practical Comparison

Incorrect Prompt

Write an email summary. Do not use words over 3 syllables. Do not use passive voice ever. Make sure every sentence has exactly 12 words. Do not use exclamation marks. Never use the word "regards". Ensure sentence 2 contains a metric. Do not use adverbs... [20 MORE MICRO-RULES]

Correct SPARK Prompt

# 4. EXECUTION
## 4.2 Guardrails
- MUST use clear, professional language (Target Flesch-Kincaid score: 60+).
- MUST NOT use passive voice constructions.
- MUST NOT include conversational salutations or sign-offs.

12.7 Key Lesson

Focus on high-level operational boundaries. Avoid cluttering the prompt with
fragile micro-rules.

13. Not Specifying Output Format

13.1 What the Mistake Is

Requesting data without defining an explicit output format, syntactical rules,
or structural schema.

13.2 Why People Make It

Developers assume the model will intuitively choose the best format (e.g.,
Markdown, JSON, plain text).

13.3 Why It Reduces Output Quality

Without a declared schema, the output structure varies across executions. The
model may output free-form text, wrap data in Markdown blocks, or add
conversational commentary that breaks downstream data parsers.

13.4 How to Recognize It

  - Automated JSON parsers throwing syntax exceptions in production pipelines.
  - Responses switching unpredictably between bulleted lists, CSV blocks, and
    unstructured paragraphs.

13.5 How to Fix It Using SPARK

Define exact structural schemas and syntactical rules in Section 5 (Output
Specification).

13.6 Practical Comparison

Incorrect Prompt

Extract the user names, email addresses, and account creation dates from this log file and return the list.

Correct SPARK Prompt

# 5. OUTPUT SPECIFICATION
## 5.1 Format & Structure
Raw JSON array of objects.

## 5.2 Syntactical Rules
- Return ONLY valid JSON.
- MUST NOT wrap output in Markdown code blocks (` ```json `).
- Omit conversational preambles and postscripts.

## 5.3 Schema
[
  {
    "user_name": "string",
    "email": "string",
    "created_at": "ISO-8601 Timestamp"
  }
]

13.7 Key Lesson

Always specify exact structural schemas and syntactical rules in Section 5 for
automated data processing.

14. Ignoring the Target Audience

14.1 What the Mistake Is

Generating content without framing who will consume the output (e.g., executive
leadership, platform engineers, retail customers).

14.2 Why People Make It

Developers focus entirely on the technical data extraction task, forgetting that
tone, terminology, and detail density must align with the end user.

14.3 Why It Reduces Output Quality

Without audience framing, the model defaults to a generic tone. Technical
reports become too high-level for senior engineers, or too dense for
non-technical executives.

14.4 How to Recognize It

  - Executive summaries filled with low-level code stack traces.
  - End-user technical guides filled with unexplained internal database jargon.

14.5 How to Fix It Using SPARK

Define the end consumer explicitly in Section 3.3 (Target Audience / Consumer).

14.6 Practical Comparison

Incorrect Prompt

Summarize our recent security incident for the company.

Correct SPARK Prompt

# 3. CONTEXT
## 3.3 Target Audience / Consumer
Chief Risk Officer (CRO) and non-technical board members.

---

# 4. EXECUTION
## 4.1 Communication Rules
- Focus on business impact, financial exposure, and remediation timelines.
- Avoid low-level technical jargon (e.g., explain "SQL Injection" simply as "Unauthorized Database Access").

14.7 Key Lesson

Specify the target audience in Section 3.3 to ensure technical depth and tone
match the end user.

15. Skipping Examples When Needed

15.1 What the Mistake Is

Relying entirely on abstract instructions (zero-shot) for complex data
transformations or custom formatting rules.

15.2 Why People Make It

Writing representative few-shot input-output examples takes extra effort and
planning.

15.3 Why It Reduces Output Quality

Abstract instructions can be interpreted in multiple ways. Without concrete
examples, models frequently misinterpret complex extraction logic or subtle edge
cases.

15.4 How to Recognize It

  - The model correctly follows basic rules but consistently fails on edge-case
    data structures.
  - Formatting errors occur whenever input data contains unexpected characters
    or missing fields.

15.5 How to Fix It Using SPARK

Provide standard and edge-case input-output examples in Section 6 (Examples).

15.6 Practical Comparison

Incorrect Prompt

Convert these unstructured phone number strings into standardized E.164 format, handling extension numbers properly.

Correct SPARK Prompt

# 6. EXAMPLES
## 6.1 Standard Example
- Input: "Phone: (555) 019-2834"
- Output: "+15550192834"

## 6.2 Edge-Case Example (Extension Number)
- Input: "Direct line: 1-555-019-2834 ext. 402"
- Output: "+15550192834x402"

15.7 Key Lesson

Use Section 6 to demonstrate target transformations and edge-case handling using
concrete few-shot examples.

16. Asking Multiple Unrelated Tasks in One Prompt

16.1 What the Mistake Is

Stacking multiple unrelated tasks (e.g., code refactoring, blog copywriting, and
database migrations) into a single monolithic prompt payload.

16.2 Why People Make It

Developers attempt to reduce total API calls by combining distinct operational
steps into a single request.

16.3 Why It Reduces Output Quality

Task stacking causes instruction interference. The model's reasoning becomes
fragmented, leading to skipped steps, reduced detail, and lower quality across
all requested tasks.

16.4 How to Recognize It

  - Prompts containing multiple unrelated tasks separated by "And also please
    do..."
  - The model completes the first task well, but rushes or skips subsequent
    tasks.

16.5 How to Fix It Using SPARK

Break complex multi-task workflows into separate, dedicated SPARK prompts linked
together in an execution chain.

                      CHAINING DECOUPLED SPARK PROMPTS
                      
Monolithic Staked Prompt (High Failure Rate):
[Refactor Code] + [Generate SQL Schema] + [Write Release Notes]
  └── High cognitive load, frequent skipped requirements.

Decoupled SPARK Execution Pipeline (High Reliability):
[Prompt A: Refactor Code] ──> [Prompt B: Generate SQL Schema] ──> [Prompt C: Release Notes]
  └── Each prompt focused on a single, verifiable objective.

16.6 Practical Comparison

Incorrect Prompt

Audit this C++ function for memory leaks, write Python bindings for it, draft a documentation page for our website, and generate a unit test suite in Jest.

Correct SPARK Prompt

# 2. OBJECTIVE
## 2.1 Primary Goal
Perform a dedicated memory safety audit on the provided C++ function to identify potential buffer overflows and unhandled pointer allocations.

## 2.3 Non-Goals
- Do not write Python bindings or wrapper code.
- Do not generate unit tests or user documentation.

16.7 Key Lesson

Focus each prompt on a single objective. Chain decoupled SPARK prompts together
for complex, multi-stage workflows.

17. Assuming the AI Knows Hidden Information

17.1 What the Mistake Is

Referencing internal company jargon, private API endpoints, unstated environment
variables, or implicit business logic without defining them.

17.2 Why People Make It

Developers work daily with internal terms (e.g., "the Phoenix service", "Type 4
errors") and forget that these terms do not exist in public pre-training
datasets.

17.3 Why It Reduces Output Quality

The model will invent a plausible meaning for the unknown term, resulting in
hallucinated logic and non-functional code.

17.4 How to Recognize It

  - Model responses hallucinate explanations for proprietary company acronyms or
    internal service names.

17.5 How to Fix It Using SPARK

Define all proprietary terminology, system abbreviations, and internal concepts
explicitly in Section 3 (Context).

17.6 Practical Comparison

Incorrect Prompt

Fix the deployment error in our Alpha-9 pipeline when processing Orion events.

Correct SPARK Prompt

# 3. CONTEXT
## 3.1 Domain Terminology
- "Alpha-9 Pipeline": Our internal Kubernetes worker pool running Node.js v20 background microservices.
- "Orion Events": JSON event payloads delivered via Apache Kafka on the `events.orders.v1` topic.

## 3.2 Error Payload
[PASTE EXACT ERROR STACK TRACE HERE]

17.7 Key Lesson

Explicitly define all proprietary terminology and internal concepts in
Section 3.

18. Writing Extremely Long Unstructured Prompts

18.1 What the Mistake Is

Authoring prompts as long, uninterrupted walls of narrative text without visual
hierarchy or structural boundaries.

18.2 Why People Make It

Drafting free-form text paragraphs is faster than structuring a prompt into
formatted sections.

18.3 Why It Reduces Output Quality

Unstructured text degrades self-attention accuracy. The model struggles to
separate operational rules from input data, leading to instruction drift and
skipped constraints.

18.4 How to Recognize It

  - Prompts structured as long continuous paragraphs without Markdown headings,
    lists, or section separators.

18.5 How to Fix It Using SPARK

Structure your prompt using the standard 8-block SPARK layout with clear
Markdown headers (#, ##) and structural dividers (---).

18.6 Practical Comparison

Incorrect Prompt

You are a database admin and I need you to look at this SQL query because it is running slowly on our production database and we need to fix it fast. The database is PostgreSQL 15 and the query joins orders and users tables... [CONTINUES FOR 500 WORDS OF UNSTRUCTURED TEXT]

Correct SPARK Prompt

# 1. ROLE & IDENTITY
## 1.1 Role
Senior PostgreSQL Database Administrator.

---

# 2. OBJECTIVE
## 2.1 Primary Goal
Optimize execution performance for the provided target SQL query.

---

# 3. CONTEXT
## 3.1 Environment Parameters
- Engine: PostgreSQL 15.2
- Dataset: `orders` (10M rows), `users` (1M rows)

---

# 4. EXECUTION
## 4.1 Step-by-Step Logic
1. Analyze query execution plan (`EXPLAIN ANALYZE`).
2. Identify missing compound indexes or sequential scans.
3. Rewrite query structure to optimize join operations.

18.7 Key Lesson

Use the 8-block SPARK architecture to give your prompts clear visual and
structural organization.

19. Blindly Trusting the First AI Response

19.1 What the Mistake Is

Accepting model outputs directly into production pipelines without running
validation checks or verification loops.

19.2 Why People Make It

Initial success with simple queries creates false confidence in the model's
ability to handle complex edge cases automatically.

19.3 Why It Reduces Output Quality

LLMs operate probabilistically. Without verification checks, hallucinations,
subtle logic bugs, and schema violations will inevitably reach production
systems.

19.4 How to Recognize It

  - Integration pipelines failing silently in production due to unchecked model
    outputs.

19.5 How to Fix It Using SPARK

Embed binary audit checklists and self-correction loops directly into Section 7
(Verification & Refinement).

19.6 Practical Comparison

Incorrect Prompt

Generate the TypeScript interface definitions for our user API and return the file.

Correct SPARK Prompt

# 7. VERIFICATION & REFINEMENT
## 7.1 Pre-Output Audit Checklist
Evaluate the generated TypeScript code against these criteria before rendering final tokens:
1. Are all object properties explicitly typed (no implicit `any` types)? [YES/NO]
2. Are optional API fields declared using the optional modifier (`?`)? [YES/NO]
3. Does the output omit conversational commentary? [YES/NO]

## 7.2 Self-Correction Loop
- IF any item evaluates to NO, correct the issue internally before outputting the final result.

19.7 Key Lesson

Embed pre-output audit checklists and self-correction loops into Section 7 to
catch generation errors automatically.

20. Failing to Review and Refine Outputs

20.1 What the Mistake Is

Deploying static prompts to production without measuring performance, tracking
failure rates, or refining instructions over time.

20.2 Why People Make It

Prompts are often treated as disposable inputs rather than living software
artifacts that require continuous iteration.

20.3 Why It Reduces Output Quality

Unmonitored prompts degrade over time as real-world input data changes,
underlying model versions update, and new edge cases emerge.

20.4 How to Recognize It

  - Production application error rates rising over time without clear visibility
    into root causes.

20.5 How to Fix It Using SPARK

Maintain version tracking in Section 8 (Notes) and update prompts systematically
based on production test evaluations.

20.6 Practical Comparison

# 8. NOTES
## 8.1 Version History & Maintenance
- Prompt Version: 2.1.0
- Last Evaluated: 2024-10-15
- Evaluation Benchmark: `tests/benchmarks/user_extraction_v2.json`
- Baseline Accuracy: 99.4% Schema Compliance across 1,000 test runs.
- Changelog v2.1.0: Added Section 4.2 Guardrail to prevent hallucinated UUIDs on null input payloads (Fixes Issue #104).

20.7 Key Lesson

Treat prompts as living software artifacts. Track versions, monitor performance,
and refine instructions based on test evaluations.

21. Treating Prompt Engineering as Trial and Error Instead of an Engineering Process

21.1 What the Mistake Is

Approaching prompt authoring through informal, ad-hoc text tweaks rather than
systematic software engineering principles.

21.2 Why People Make It

Trial-and-error editing feels faster in the short term than establishing formal
software architecture standards.

21.3 Why It Reduces Output Quality

Ad-hoc text tweaks solve isolated output errors while introducing unexpected
regressions elsewhere in the system.

+-----------------------------------------------------------------------------------+
|                        TRIAL-AND-ERROR VS. SPARK ENGINEERING                      |
+-----------------------------------------------------------------------------------+
| AD-HOC TRIAL-AND-ERROR            │ SPARK ENGINEERING PROCESS                     |
+-----------------------------------+-----------------------------------------------+
| • Informal, unstructured edits    │ • Modular, structural prompt architecture      |
| • Fixes one bug, breaks another   │ • Isolated components & explicit boundaries   |
| • Subjective, manual evaluation   │ • Systematic benchmark evaluation datasets    |
| • Untracked change history        │ • Version-controlled repository artifacts     |
+-----------------------------------------------------------------------------------+

21.4 How to Recognize It

  - Developers continuously tweaking phrases ("Please ensure...", "Pretty
    please...", "Important!!!") without improving system stability.

21.5 How to Fix It Using SPARK

Adopt the complete SPARK engineering methodology: modular design, explicit
constraints, version control, and systematic evaluation benchmarking.

21.6 Key Lesson

Transition from informal prompt tinkering to systematic software engineering
using the SPARK Framework.

22. Final Checklist to Avoid Common Mistakes

Before deploying any prompt to production, run this final audit to detect and
eliminate common anti-patterns:

| \#     | Diagnostic Check                                                                   | SPARK Remediation Section            | Status |
| :----- | :--------------------------------------------------------------------------------- | :----------------------------------- | :----: |
| **1**  | Is the primary goal clear, testable, and free of vague language?                   | **Section 2 (Objective)**            | \[ \]  |
| **2**  | Are technical stack versions, dependencies, and environment bounds declared?       | **Section 3 (Context)**              | \[ \]  |
| **3**  | Has raw, unnecessary context text been filtered out of the input payload?          | **Section 3 (Context)**              | \[ \]  |
| **4**  | Is the assigned persona grounded, realistic, and domain-appropriate?               | **Section 1 (Role & Identity)**      | \[ \]  |
| **5**  | Have conflicting or overlapping roles been removed?                                | **Section 1 (Role & Identity)**      | \[ \]  |
| **6**  | Are target goals decoupled from execution logic steps?                             | **Section 2 vs. Section 4**          | \[ \]  |
| **7**  | Have subjective terms ("fast", "concise") been replaced with quantitative metrics? | **Section 4 & Section 5**            | \[ \]  |
| **8**  | Are explicit **MUST** and **MUST NOT** boundary rules defined?                     | **Section 4.2 (Guardrails)**         | \[ \]  |
| **9**  | Is there an explicit structural schema (JSON/YAML/Markdown) defined?               | **Section 5 (Output Specification)** | \[ \]  |
| **10** | Is conversational preamble text explicitly forbidden?                              | **Section 5.2 (Syntactical Rules)**  | \[ \]  |
| **11** | Are few-shot input-output examples provided for complex operations?                | **Section 6 (Examples)**             | \[ \]  |
| **12** | Is an inline verification checklist and self-correction loop included?             | **Section 7 (Verification)**         | \[ \]  |
| **13** | Is version metadata and model parameter configuration documented?                  | **Section 8 (Notes)**                | \[ \]  |

23. Summary

High-quality LLM performance is achieved through systematic prompt engineering.
By identifying and eliminating these common anti-patterns, developers transform
unpredictable natural language interactions into deterministic, production-ready
software systems.

Core Remediation Principles

1.  Be Explicit: Replace implicit assumptions and subjective words with explicit
    parameters, quantitative metrics, and concrete schemas.
2.  Decouple Concerns: Keep roles, objectives, environmental context, execution
    logic, output formats, and metadata separated into dedicated SPARK blocks.
3.  Bound Generation: Protect execution flow using explicit MUST and MUST NOT
    guardrails.
4.  Verify Inline: Embed audit checklists and self-correction loops to catch
    generation errors automatically.
5.  Iterate Empirically: Treat prompts as living software artifacts subject to
    version control, regression testing, and continuous optimization.

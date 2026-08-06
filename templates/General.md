SPARK General Template Guide

Universal Prompt Architecture for Standard Task Execution

1. Introduction

The SPARK General Template is the foundational, domain-agnostic template of the
SPARK Framework.

While domain-specific templates (such as code auditing, research analysis, or
copywriting templates) optimize for specialized workflows, the General Template
provides a flexible, modular architecture adaptable to virtually any prompt
engineering task.

This document serves as both a reference guide and an operational starting
point. It contains:

  - Structural guidelines explaining when and how to deploy the template.
  - Detailed breakdowns of every template section.
  - Best practices and anti-patterns.
  - A fully filled, realistic example prompt.
  - A clean, copy-and-pasteable template ready for immediate production
    deployment.

2. When to Use This Template

The General Template is designed for versatile execution across diverse
engineering, research, and business domains.

Use this template when:

  - Starting a New Prompt Project: You need a reliable, pre-structured layout
    for a task that lacks a dedicated domain template.
  - General Task Execution: You are authoring prompts for data transformations,
    technical writing, code refactoring, educational lesson plans, or workflow
    automation.
  - Cross-Disciplinary Teams: Non-engineering team members require a clear,
    standardized format to write production-ready prompts.
  - Rapid Prototyping: You need to validate a task concept quickly before
    creating a specialized system prompt.

3. When Not to Use This Template

Do not use the General Template if:

  - Dedicated Domain Templates Exist: Your task matches a specialized SPARK
    template (e.g., templates/Software-Engineering.md,
    templates/Data-Extraction.md).
  - Simple, Single-Turn Commands: The request is a trivial, one-step text format
    adjustment (e.g., "Convert this list to comma-separated values") where a
    full system architecture introduces unnecessary overhead.
  - Low-Latency Real-Time Streaming: You are deploying micro-prompts in
    environments where context window token overhead must be kept to an absolute
    minimum.

4. How to Fill the Template

Authoring a SPARK prompt using the General Template follows a simple four-step
process:

+-----------------------------------------------------------------------------------+
|                            SPARK AUTHORING WORKFLOW                               |
+-----------------------------------------------------------------------------------+
|  1. DEFINE OUTPUT & GOAL   ──> Fill Section 2 (Objective) & Section 5 (Output)   |
|                                                                                   |
|  2. SET ENVIRONMENT        ──> Fill Section 1 (Role) & Section 3 (Context)       |
|                                                                                   |
|  3. OUTLINE EXECUTION      ──> Fill Section 4 (Execution) & Section 6 (Examples) |
|                                                                                   |
|  4. ADD AUDIT METRICS      ──> Fill Section 7 (Verification) & Section 8 (Notes)  |
+-----------------------------------------------------------------------------------+

1.  Start with the Endpoint (Sections 2 & 5): Begin by defining the primary
    goal, success criteria, and desired output schema. Knowing what you want to
    receive guides how you configure the remaining sections.
2.  Establish the Environment (Sections 1 & 3): Define the model's professional
    role, cognitive style, domain context, and runtime constraints.
3.  Detail the Operational Logic (Sections 4 & 6): Lay out step-by-step
    execution rules, positive/negative guardrails, and representative few-shot
    examples.
4.  Configure Verification & Metadata (Sections 7 & 8): Add an inline self-audit
    checklist, self-correction rules, and version tracking metadata.

5. The Complete Blank SPARK Template

Below is the annotated structure of the universal SPARK template. Each field
contains inline placeholder text indicating what information belongs in that
block.

# 1. ROLE & IDENTITY
## 1.1 Role
[Define the exact professional title and domain expertise. Example: "Senior Distributed Systems Architect"]

## 1.2 Cognitive Style
- [Analytical methodology 1. Example: "First-Principles System Analysis"]
- [Analytical methodology 2. Example: "Defensive Engineering Design"]

## 1.3 Tone & Voice
[Describe communication style, tone, and preamble constraints. Example: "Objective, technical, direct. Omit conversational filler."]

---

# 2. OBJECTIVE
## 2.1 Primary Goal
[Single declarative statement defining the ultimate deliverable.]

## 2.2 Success Criteria
- [Measurable metric or requirement 1]
- [Measurable metric or requirement 2]

## 2.3 Non-Goals
- [Explicit boundary / out-of-scope task 1]
- [Explicit boundary / out-of-scope task 2]

---

# 3. CONTEXT
## 3.1 Background & Domain
[System state, domain background, and historical state relevant to the request.]

## 3.2 System & Technical Constraints
- [Runtime version / Environment constraint 1]
- [Dependency / Resource limit 2]

## 3.3 Target Audience / Consumer
[End-user persona or downstream programmatic service consuming the output.]

---

# 4. EXECUTION
## 4.1 Step-by-Step Logic
1. [Sequential Execution Step 1]
2. [Sequential Execution Step 2]
3. [Sequential Execution Step 3]

## 4.2 Guardrails
- MUST [Positive mandatory operational requirement]
- MUST NOT [Negative operational restriction]

## 4.3 Fallback & Edge Case Handling
- IF [Unexpected Condition / Missing Data] THEN [Deterministic Remediation Action]

---

# 5. OUTPUT SPECIFICATION
## 5.1 Format & Structure
[Format specification: JSON, Markdown, YAML, Plain Text, Code]

## 5.2 Syntactical Rules
- [Formatting constraint 1. Example: "Return raw JSON only."]
- [Formatting constraint 2. Example: "DO NOT wrap in Markdown backticks."]

## 5.3 Schema & Field Definitions
[Paste exact structural JSON Schema, OpenAPI specification, or document layout]

---

# 6. EXAMPLES
## 6.1 Standard Example
### Input:
[Sample standard input payload]

### Expected Output:
[Sample target output matching specification schema]

## 6.2 Edge-Case Example
### Input:
[Sample malformed or edge-case input payload]

### Expected Output:
[Sample deterministic fallback output]

---

# 7. VERIFICATION & REFINEMENT
## 7.1 Pre-Output Audit Checklist
1. [Binary Audit Condition 1] [YES/NO]
2. [Binary Audit Condition 2] [YES/NO]

## 7.2 Self-Correction Loop
- IF any check evaluates to NO, resolve the failure internally before rendering final output.

---

# 8. NOTES
## 8.1 Operational Metadata
- Framework Version: SPARK v1.0
- Author: [Author Name / Team]
- Version: 1.0.0

## 8.2 Model Adaptation Notes
- Target Model: [Target Model ID]
- Recommended Temperature: 0.0

6. Explanation of Every SPARK Section

6.1 Section 1: Role & Identity

  - Purpose: Configures the model's operational persona, domain focus, and
    communication style.
  - Why It Exists: LLMs hold broad pre-training distributions. System-level
    roles narrow the model's activation space toward expert domain patterns.
  - What Belongs Here: Functional professional titles, explicit reasoning
    methodologies (e.g., STRIDE threat modeling, root-cause analysis), and
    communication tone rules.
  - What Does NOT Belong Here: Exaggerated or hyperbolic praise ("You are the
    smartest AI in the world"), or project execution steps.
  - Best Practices: Use functional titles ("Staff Site Reliability Engineer")
    rather than generic ones ("Helpful Assistant").
  - Common Mistakes: Assigning multiple conflicting roles in the same prompt.
  - Practical Tip: Always specify a preamble ban in Section 1.3 ("Omit
    conversational greetings and introductory filler").

6.2 Section 2: Objective

  - Purpose: Establishes the single source of truth for task success.
  - Why It Exists: Models drift off-target when given open-ended instructions.
    Defining clear targets and explicit non-goals focuses the model's attention.
  - What Belongs Here: A single declarative primary goal statement, measurable
    success metrics, and explicit non-goals.
  - What Does NOT Belong Here: Detailed step-by-step processing logic or raw
    data payloads.
  - Best Practices: Keep the primary goal to a single sentence. Formulate
    success criteria as testable statements.
  - Common Mistakes: Goal stacking—combining multiple unrelated targets into one
    prompt.
  - Practical Tip: Use Section 2.3 (Non-Goals) to preemptively cut off common
    secondary tangents.

6.3 Section 3: Context

  - Purpose: Supplies the environmental state, technical parameters, and target
    audience bounds.
  - Why It Exists: LLMs operate strictly on context window inputs during
    inference. Supplying explicit system state prevents the model from
    substituting unverified assumptions.
  - What Belongs Here: Software versions, database schemas, API parameters,
    target audience definitions, and input payload blocks.
  - What Does NOT Belong Here: Abstract execution instructions or general
    persona definitions.
  - Best Practices: Structure technical parameters using key-value lists or code
    blocks.
  - Common Mistakes: Context dumping—pasting thousands of lines of raw,
    unfiltered log files into the prompt.
  - Practical Tip: Separate environment bounds (Section 3.2) from audience
    definitions (Section 3.3).

6.4 Section 4: Execution

  - Purpose: Defines the step-by-step processing logic, operational guardrails,
    and error-handling steps.
  - Why It Exists: LLMs generate text token by token. Sequential execution steps
    prevent the model from skipping steps or hallucinating logic.
  - What Belongs Here: Numbered processing steps, conditional branching
    statements (IF/THEN), positive/negative guardrails (MUST / MUST NOT), and
    fallbacks.
  - What Does NOT Belong Here: Structural output schemas or administrative
    metadata.
  - Best Practices: Highlight constraint keywords using capitalized bold text
    (MUST, MUST NOT). Number steps sequentially.
  - Common Mistakes: Writing execution steps as long narrative paragraphs
    instead of numbered lists.
  - Practical Tip: Always add a fallback rule in Section 4.3 to handle malformed
    or missing input data gracefully.

6.5 Section 5: Output Specification

  - Purpose: Defines the output structure, syntactical constraints, and target
    schema.
  - Why It Exists: Downstream applications require predictable formats. Explicit
    output specifications prevent schema drift and parsing errors.
  - What Belongs Here: File format declarations, syntax rules (e.g., banning
    Markdown fences), field definitions, and JSON/YAML schemas.
  - What Does NOT Belong Here: Business logic rules or domain background text.
  - Best Practices: Supply exact JSON Schema or OpenAPI definitions for
    automated pipelines.
  - Common Mistakes: Requesting "a JSON object" without defining specific key
    names or data types.
  - Practical Tip: Explicitly state how empty or null values should be formatted
    (null, "", []).

6.6 Section 6: Examples

  - Purpose: Demonstrates expected input-to-output transformations using
    few-shot exemplar patterns.
  - Why It Exists: Concrete examples provide unambiguous signals for data
    extraction, reasoning steps, and output formatting.
  - What Belongs Here: Standard input-output pairs and edge-case examples
    demonstrating error handling.
  - What Does NOT Belong Here: Long, irrelevant examples that consume context
    window space unnecessarily.
  - Best Practices: Format example outputs to match the schema defined in
    Section 5.
  - Common Mistakes: Providing examples that violate the guardrails or schemas
    defined in earlier sections.
  - Practical Tip: Always include at least one edge-case example showing how to
    handle invalid or missing data.

6.7 Section 7: Verification & Refinement

  - Purpose: Implements an inline self-audit loop to check responses before
    rendering final output.
  - Why It Exists: LLMs generate text in a single forward pass. Inline
    verification loops allow models to catch and correct errors internally
    before completing generation.
  - What Belongs Here: Binary (YES/NO) pre-output audit questions and
    self-correction instructions.
  - What Does NOT Belong Here: New execution steps or environment parameters.
  - Best Practices: Formulate audit rules as clear binary conditions ("Is the
    JSON schema valid? YES/NO").
  - Common Mistakes: Asking subjective audit questions like "Is this output
    good?"
  - Practical Tip: Direct the model to run the audit loop silently in an
    internal scratchpad before producing final tokens.

6.8 Section 8: Notes

  - Purpose: Stores version metadata, target model configurations, and
    maintenance logs.
  - Why It Exists: Keeps administrative and deployment settings isolated from
    core execution instructions.
  - What Belongs Here: Semantic version numbers (1.0.0), author details, target
    model IDs, temperature settings, and changelogs.
  - What Does NOT Belong Here: Execution logic or system guardrails.
  - Best Practices: Increment version numbers whenever updating execution logic
    or output schemas.
  - Common Mistakes: Placing system guardrails or schema rules inside the Notes
    section.
  - Practical Tip: Document target inference parameters (temperature: 0.0)
    alongside model IDs.

7. Best Practices While Using the Template

1.  Keep Placeholders Clear: Replace all bracketed placeholder text [...] with
    explicit instructions. Never leave unedited brackets in production prompts.
2.  Maintain Section Boundaries: Keep functional instructions inside their
    assigned SPARK sections. Do not mix context into execution blocks or
    guardrails into output specifications.
3.  Delete Unused Optional Fields: If a section (e.g., Section 6 Examples) is
    unnecessary for a simple task, you may omit it, but keep the core structural
    blocks intact.
4.  Use Capitalized Guardrails: Always format operational boundaries using
    capitalized MUST and MUST NOT statements in Section 4.2.
5.  Set Temperature to Deterministic: Set the model temperature parameter to 0.0
    for structured data, coding, or schema-enforced tasks.

8. Common Mistakes

  - Leaving Bracketed Placeholders: Deploying a prompt containing unedited
    template comments like [Define primary goal].
  - Collapsing Headings: Deleting Markdown headings (#, ##), converting the
    structured template back into an unstructured block of text.
  - Contradicting Rules Across Sections: Requesting a 500-word essay in
    Section 2 while limiting total length to 50 words in Section 5.
  - Omitting Output Schemas: Expecting valid, machine-readable JSON without
    defining key names or data types in Section 5.3.

9. Example Filled Template

Here is a complete, real-world example of a production prompt built using the
SPARK General Template:

# 1. ROLE & IDENTITY
## 1.1 Role
You are a Principal Data Infrastructure Engineer specializing in automated log ingestion, event parsing, and telemetry pipeline optimization.

## 1.2 Cognitive Style
- Root-Cause Failure Isolation
- Schema-First Data Architecture
- Defensive Input Sanitization

## 1.3 Tone & Voice
Technical, objective, and precise. Omit conversational greetings, introductory text, and postscript summaries. Output raw data payloads directly.

---

# 2. OBJECTIVE
## 2.1 Primary Goal
Parse an unstructured server error log payload, extract structured security incident metrics, filter out non-security noise, and render a validated JSON report.

## 2.2 Success Criteria
- Isolate all failed authentication and unauthorized access events.
- Extract client IP addresses, user IDs, timestamps, and target endpoints.
- Format the output payload strictly to the Section 5 JSON Schema.

## 2.3 Non-Goals
- Do not process HTTP 200 success events.
- Do not generate network remediation scripts or firewall configuration code.

---

# 3. CONTEXT
## 3.1 Background & Domain
A web application experienced a credential-stuffing attack on the `/api/v2/auth/login` endpoint between 03:00 and 04:00 UTC.

## 3.2 System & Technical Constraints
- Timestamp Format: ISO-8601 (`YYYY-MM-DDTHH:mm:ssZ`).
- Log Source: Linux Nginx access and application error streams.
- IP Resolution: Preserve IPv4 and IPv6 string formats.

## 3.3 Target Audience / Consumer
Automated Security Information and Event Management (SIEM) ingestion pipeline.

---

# 4. EXECUTION
## 4.1 Step-by-Step Logic
1. Read input log lines sequentially.
2. Filter for entries containing `AUTH_FAILURE`, `401 Unauthorized`, or `403 Forbidden`.
3. Extract `timestamp`, `client_ip`, `user_id`, and `target_endpoint` using regular expressions.
4. Construct a structured array of incident objects.
5. Audit the final JSON object against the Section 5 Schema before rendering.

## 4.2 Guardrails
- MUST return valid JSON strictly matching the defined schema.
- MUST NOT include Markdown backtick fencing (` ```json `) in the response.
- MUST map missing `user_id` fields to `null` rather than omitting the key.

## 4.3 Fallback & Edge Case Handling
- IF the input log contains no matching security events, return a valid JSON object with `incident_count: 0` and an empty `incidents: []` array.

---

# 5. OUTPUT SPECIFICATION
## 5.1 Format & Structure
Raw JSON Payload.

## 5.2 Syntactical Rules
- Return raw JSON strictly.
- Omit preamble commentary and Markdown fencing.

## 5.3 Schema & Field Definitions
{
  "timestamp_generated": "ISO-8601 String",
  "incident_count": "Integer",
  "incidents": [
    {
      "timestamp": "ISO-8601 String",
      "client_ip": "String",
      "user_id": "String or Null",
      "endpoint": "String",
      "event_type": "AUTH_FAILURE | UNAUTHORIZED_ACCESS"
    }
  ]
}

---

# 6. EXAMPLES
## 6.1 Standard Example
### Input:
"2024-10-15T03:14:02Z nginx: 192.168.1.50 - user_882 [ERROR] /api/v2/auth/login HTTP 401 Auth Failed"

### Expected Output:
{
  "timestamp_generated": "2024-10-15T03:15:00Z",
  "incident_count": 1,
  "incidents": [
    {
      "timestamp": "2024-10-15T03:14:02Z",
      "client_ip": "192.168.1.50",
      "user_id": "user_882",
      "endpoint": "/api/v2/auth/login",
      "event_type": "AUTH_FAILURE"
    }
  ]
}

## 6.2 Edge-Case Example
### Input:
"2024-10-15T03:14:10Z nginx: 10.0.0.1 - - [INFO] /index.html HTTP 200 OK"

### Expected Output:
{
  "timestamp_generated": "2024-10-15T03:15:00Z",
  "incident_count": 0,
  "incidents": []
}

---

# 7. VERIFICATION & REFINEMENT
## 7.1 Pre-Output Audit Checklist
1. Does the output JSON conform strictly to the Section 5 schema? [YES/NO]
2. Is Markdown code fencing completely removed? [YES/NO]
3. Are non-security HTTP 200 logs excluded from the incidents array? [YES/NO]

## 7.2 Self-Correction Loop
- IF any audit check evaluates to NO, correct the payload internally and re-run the checklist.

---

# 8. NOTES
## 8.1 Operational Metadata
- Framework Version: SPARK v1.0
- Author: Security Operations Engineering Team
- Prompt Version: 1.2.0

## 8.2 Model Adaptation Notes
- Target Model: `claude-fable-5
- Recommended Parameters: Temperature: 0.0, Top_P: 1.0

10. Copy-and-Paste Version

Copy the clean, unannotated block below to start authoring a new SPARK prompt:

# 1. ROLE & IDENTITY
## 1.1 Role
[ROLE_TITLE]

## 1.2 Cognitive Style
- [REASONING_STYLE_1]
- [REASONING_STYLE_2]

## 1.3 Tone & Voice
[TONE_DESCRIPTION]

---

# 2. OBJECTIVE
## 2.1 Primary Goal
[PRIMARY_GOAL_STATEMENT]

## 2.2 Success Criteria
- [SUCCESS_CRITERIA_1]
- [SUCCESS_CRITERIA_2]

## 2.3 Non-Goals
- [NON_GOAL_1]
- [NON_GOAL_2]

---

# 3. CONTEXT
## 3.1 Background & Domain
[BACKGROUND_TEXT]

## 3.2 System & Technical Constraints
- [CONSTRAINT_1]
- [CONSTRAINT_2]

## 3.3 Target Audience / Consumer
[TARGET_AUDIENCE]

---

# 4. EXECUTION
## 4.1 Step-by-Step Logic
1. [STEP_1]
2. [STEP_2]
3. [STEP_3]

## 4.2 Guardrails
- MUST [MANDATORY_REQUIREMENT]
- MUST NOT [NEGATIVE_RESTRICTION]

## 4.3 Fallback & Edge Case Handling
- IF [UNEXPECTED_CONDITION] THEN [FALLBACK_ACTION]

---

# 5. OUTPUT SPECIFICATION
## 5.1 Format & Structure
[FORMAT_TYPE]

## 5.2 Syntactical Rules
- [SYNTAX_RULE_1]
- [SYNTAX_RULE_2]

## 5.3 Schema & Field Definitions
[SCHEMA_DEFINITION]

---

# 6. EXAMPLES
## 6.1 Standard Example
### Input:
[SAMPLE_INPUT]

### Expected Output:
[SAMPLE_OUTPUT]

## 6.2 Edge-Case Example
### Input:
[EDGE_CASE_INPUT]

### Expected Output:
[EDGE_CASE_OUTPUT]

---

# 7. VERIFICATION & REFINEMENT
## 7.1 Pre-Output Audit Checklist
1. [CHECKLIST_ITEM_1] [YES/NO]
2. [CHECKLIST_ITEM_2] [YES/NO]

## 7.2 Self-Correction Loop
- IF any audit check evaluates to NO, correct the output internally before completing execution.

---

# 8. NOTES
## 8.1 Operational Metadata
- Framework Version: SPARK v1.0
- Author: [AUTHOR_NAME]
- Version: 1.0.0

## 8.2 Model Adaptation Notes
- Target Model: [MODEL_ID]
- Recommended Parameters: Temperature: 0.0

11. Summary

The SPARK General Template provides a standardized, modular layout for
general-purpose prompt execution.

By organizing prompt instructions into eight functional sections—Role,
Objective, Context, Execution, Output Specification, Examples, Verification, and
Notes—developers can replace informal text prompts with structured, auditable
software artifacts.

SPARK Automation & AI Agent Workflow Template

Standardized Prompt Architecture for Autonomous Agents, API Orchestration,
Scripting, and Business Process Automation

1. Introduction

The SPARK Automation Template is a specialized, platform-agnostic framework
designed for automation architects, DevOps engineers, AI workflow builders, and
operations teams using Large Language Models (e.g., Claude, ChatGPT, Cursor) and
automation tools (e.g., Python, n8n, Make, Zapier, Model Context Protocol [MCP]
agents).

Automating business processes and constructing AI agents with LLMs introduces
distinct systemic failure modes:

  - Non-Idempotent Executions: Automated scripts re-run on duplicate events and
    create duplicate records, charges, or database entries.
  - Silent Error Cascades: Unhandled API rate limits, network timeouts, or
    schema changes cause background workflows to fail silently without
    triggering alerts.
  - Security & Credential Leaks: Prompts that do not enforce strict secrets
    management lead to hardcoded API keys, exposed Bearer tokens, or excessive
    permission scopes.
  - Unbounded Agent Loops: Autonomous AI agents equipped with external tools run
    infinite loops, consume excessive API credits, or trigger unintended actions
    without human-in-the-loop (HITL) checkpoints.

The SPARK Automation Template eliminates these risks by enforcing explicit
trigger definitions, input/output payload schemas, error-handling retry
strategies, idempotency rules, rate-limit guards, and structured logging.

2. When to Use This Template

Use the SPARK Automation Template across all automated workflow engineering and
agent orchestration activities:

  - Autonomous AI Agents & Tool Use: Prompts for agents equipped with external
    tools (via Model Context Protocol [MCP], Function Calling, or ReAct loops).
  - API Orchestration & Webhooks: Building pipelines that ingest webhooks,
    transform JSON payloads, and sync data across third-party APIs (e.g.,
    GitHub, Slack, CRM, Stripe).
  - Python & Shell Automation Scripts: Writing cron jobs, file-processing
    scripts, database sync workers, or web scrapers.
  - No-Code / Low-Code Workflows: Designing flow logic for workflow automation
    platforms like n8n, Make, or Zapier.
  - Business Process & Approval Workflows: Automating invoice processing, lead
    qualification, ticket triage, or employee onboarding drips with
    Human-in-the-Loop (HITL) approvals.

3. When Not to Use This Template

Do not use the SPARK Automation Template for:

  - Interactive Frontend UI Components: Building React or HTML interface views
    (use templates/Coding.md instead).
  - Static Marketing Copy: Authoring ad text or general blog posts (use
    templates/Marketing.md instead).

4. How to Fill the Template

Authoring an automation prompt using the SPARK architecture follows a five-phase
flow:

+-----------------------------------------------------------------------------------+
|                       AUTOMATION PROMPT AUTHORING WORKFLOW                        |
+-----------------------------------------------------------------------------------+
|  1. DEFINE TRIGGER & PAYLOADS ──> Set Event Trigger, Inputs, & Outputs (Sec 3)    |
|                                                                                   |
|  2. DECLARE WORKFLOW GOAL     ──> Set Target SLA, Rate Limits, & Metrics (Sec 2)  |
|                                                                                   |
|  3. MAP STATE FLOW & TOOLS    ──> Outline Logic, Retries, & Tool Specs (Sec 4)    |
|                                                                                   |
|  4. SPECIFY CODE / JSON SCHEMAS──> Define Executable Code & Log Format (Sec 5)    |
|                                                                                   |
|  5. EMBED RESILIENCE AUDIT    ──> Add Idempotency & Error Handling Checks (Sec 7) |
+-----------------------------------------------------------------------------------+

5. Complete Blank Automation SPARK Template

Below is the complete, annotated SPARK Automation Template. Bracketed
placeholders indicate the specific automation parameters required.

# 1. ROLE & IDENTITY
## 1.1 Role
[Define Automation Specialty. Example: "Senior AI Workflow Engineer specializing in resilient Python API integrations and autonomous agent orchestration"]

## 1.2 Cognitive Style
- [System Principle 1. Example: "Idempotent, Event-Driven Process Architecture"]
- [System Principle 2. Example: "Defensive Error Handling & Structured Observability"]

## 1.3 Tone & Voice
Technical, concise, objective, and direct. Return executable automation code, workflow configs, or agent system prompts with zero conversational preamble.

---

# 2. OBJECTIVE
## 2.1 Primary Goal
[Single declarative statement defining the target automation deliverable.]

## 2.2 Success Criteria
- [Reliability Target. Example: "100% error containment with zero unhandled API exceptions"]
- [Idempotency Target. Example: "Prevent duplicate processing using primary key deduplication"]
- [SLA / Latency Target. Example: "Workflow execution MUST complete within 5000ms per event"]

## 2.3 Non-Goals
- [Out-of-scope integrations. Example: "Do not build web UI frontend dashboards"]
- [Prohibited practices. Example: "Do not store secrets as plain text in source code"]

---

# 3. CONTEXT
## 3.1 Trigger Event & Execution Schedule
- Trigger Source: [e.g., Incoming Webhook POST / Cron Schedule `0 8 * * 1-5` / Kafka Event Stream]
- Execution Environment: [e.g., Python 3.11 Lambda / n8n Workflow Engine / Node.js MCP Server / Docker Container]

## 3.2 Input & Output Payloads
- Input Schema: [Paste incoming JSON payload schema or payload data map]
- Output Schema: [Paste target destination API payload schema or database record structure]

## 3.3 External Tooling & Integrations
- APIs / Services: [e.g., GitHub REST API v3, Slack Webhooks, OpenAI API, Postgres 16]
- MCP Servers / Tools: [e.g., `github-mcp-server`, `fetch-mcp-tool`, `postgres-mcp`]
- Auth Strategy: [e.g., OAuth 2.0 Bearer Token stored in `process.env.SLACK_BOT_TOKEN`]

---

# 4. EXECUTION
## 4.1 Step-by-Step Logic & State Flow
1. [Step 1: Event Ingestion & Secret/Signature Verification]
2. [Step 2: Input Payload Validation & Idempotency Check]
3. [Step 3: Core Transformation / AI Agent Tool Call Execution]
4. [Step 4: Target Destination API Request / Database Write]
5. [Step 5: Structured Logging & Notification Dispatches]

## 4.2 Guardrails & Safety Controls
- MUST enforce idempotency checks (e.g., check `event_id` or `invoice_id` in Redis/DB before execution).
- MUST handle API rate limits (HTTP 429) using exponential backoff with jitter.
- MUST NOT store API keys or passwords in raw code strings; read exclusively from environment variables.
- MUST include Human-in-the-Loop (HITL) approval steps for destructive actions (e.g., database deletes, high-value payments).

## 4.3 Exception, Retry & Fallback Strategy
- IF [API Rate Limit / HTTP 429] THEN [Retry up to 3 times with exponential backoff (2s, 4s, 8s)].
- IF [Network Timeout / Connection Error] THEN [Route payload to Dead Letter Queue (DLQ) and dispatch Slack alert].
- IF [Validation Error / Bad Payload] THEN [Log HTTP 400 error details and drop message without retrying].

---

# 5. OUTPUT SPECIFICATION
## 5.1 Format & Structure
Deliverable format: [e.g., Single Executable Python Script / n8n Workflow JSON Export / MCP Tool Definition System Prompt]

## 5.2 Logging & Observability Schema
All workflow logs MUST be output as structured JSON matching this schema:
```json
{
  "timestamp": "ISO-8601 String",
  "workflow_id": "String",
  "execution_id": "UUID",
  "event_type": "String",
  "status": "SUCCESS | RETRY | FAILED",
  "execution_time_ms": "Integer",
  "error_details": "String or Null"
}

6. EXAMPLES

6.1 Idempotent & Fault-Tolerant Execution Example

Unsafe Implementation (Avoid):

# Unsafe: No retry, no secret management, hardcoded values
import requests
res = requests.post("https://api.service.com/data", json={"user": "123"}, headers={"Authorization": "Bearer my-secret-key"})

Resilient SPARK Implementation (Emulate):

# Resilient: Environment variables, exponential backoff, rate-limit handling, structured logging
import os, time, requests, logging

def send_payload_with_retry(payload, max_retries=3):
    token = os.getenv("API_BEARER_TOKEN")
    url = os.getenv("TARGET_API_URL")
    for attempt in range(max_retries):
        try:
            res = requests.post(url, json=payload, headers={"Authorization": f"Bearer {token}"}, timeout=5)
            if res.status_code == 200:
                return res.json()
            elif res.status_code == 429: # Rate limited
                time.sleep(2 ** attempt)
        except requests.exceptions.RequestException as e:
            if attempt == max_retries - 1:
                logging.error(f'{{"status": "FAILED", "attempt": {attempt+1}, "error": "{str(e)}"}}')
                raise
            time.sleep(2 ** attempt)

7. VERIFICATION & REFINEMENT

7.1 Pre-Deployment Automation Audit Checklist

1.  Is the workflow completely idempotent (duplicate events do not create
    duplicate records)? [YES/NO]
2.  Are all credentials and API keys read from environment variables? [YES/NO]
3.  Does the execution logic handle API rate limits (HTTP 429) and network
    timeouts gracefully? [YES/NO]
4.  Are failure alerts configured to notify an operations channel
    (Slack/PagerDuty) on DLQ routes? [YES/NO]

7.2 Self-Correction Loop

  - IF any audit check evaluates to NO, resolve the failure internally before
    outputting final workflow code.

8. NOTES

8.1 Operational Metadata

  - Framework Version: SPARK Automation v1.0
  - Target Model: [e.g., Claude Fable 5 / GPT-5.6-sol]
  - Recommended Parameters: Temperature: 0.0 (Strict deterministic logic)


---

## 6. Explanation of Every SPARK Section for Automation

### 6.1 Section 1: Role & Identity
* **Purpose**: Sets the model's operational identity as a systems automation architect or integration engineer.
* **Automation Application**: Establishes a technical focus (e.g., "AI Workflow Engineer specializing in n8n pipelines") and enforces deterministic execution styles.

### 6.2 Section 2: Objective
* **Purpose**: Defines the automation goal, SLA execution bounds, and non-goals.
* **Automation Application**: Bounds execution metrics (e.g., max latency <5000ms, 100% error containment) and sets non-goals (e.g., preventing unnecessary scope creep into UI building).

### 6.3 Section 3: Context
* **Purpose**: Documents event triggers, incoming/outgoing JSON schemas, external APIs, MCP tool definitions, and authentication methods.
* **Automation Application**: Grounds the model in real payload structures, execution schedules (cron, webhooks), and environment security context.

### 6.4 Section 4: Execution
* **Purpose**: Defines the step-by-step state flow, idempotency rules, rate-limit retries, and fallback strategies.
* **Automation Application**: Guides workflow processing step-by-step. Enforces idempotency, exponential backoffs, and Dead Letter Queue (DLQ) routing.

### 6.5 Section 5: Output Specification
* **Purpose**: Controls output deliverable format (Python code, n8n JSON, agent prompts) and structured logging schemas.
* **Automation Application**: Ensures all log outputs follow a unified, parseable JSON schema for centralized observability platforms (Datadog, CloudWatch).

### 6.6 Section 6: Examples
* **Purpose**: Provides few-shot code or workflow configuration examples comparing unsafe implementations with fault-tolerant, idempotent patterns.
* **Automation Application**: Anchors model generation on resilient coding techniques.

### 6.7 Section 7: Verification & Refinement
* **Purpose**: Implements a pre-deployment audit checklist evaluating idempotency, rate limiting, and secrets security.
* **Automation Application**: Forces the model to audit its generated script or workflow configuration for silent error risks before outputting code.

### 6.8 Section 8: Notes
* **Purpose**: Tracks operational metadata, environment variables, and target LLM engine parameters.
* **Automation Application**: Documents runtime settings (`temperature: 0.0` for deterministic logic) and workflow version histories.

---

## 7. Automation Best Practices

1. **Enforce Absolute Idempotency**: Design every workflow script so that receiving duplicate trigger events yields the same result without creating duplicate records or double charges.
2. **Handle Rate Limits with Exponential Backoff**: Always catch HTTP 429 (Too Many Requests) and HTTP 503 (Service Unavailable) status codes and retry requests using exponential backoff with jitter (`2s`, `4s`, `8s`).
3. **Never Hardcode Credentials**: Read all API tokens, database connection strings, and private keys exclusively from environment variables (`process.env` or `os.getenv`).
4. **Implement Dead Letter Queues (DLQ) for Unhandled Failures**: Route payloads that fail all retry attempts to a DLQ storage bucket or trigger an immediate Slack/PagerDuty notification.
5. **Enforce Human-in-the-Loop (HITL) Checkpoints for Destructive Actions**: Never allow autonomous AI agents to execute destructive file operations, database deletions, or financial transactions without an explicit approval step.

---

## 8. Common Mistakes in AI Automation Prompts

| Mistake | Impact on AI Output | SPARK Remediation |
| :--- | :--- | :--- |
| **Non-Idempotent Workflows** | Duplicate webhooks cause duplicate database records or charges. | Enforce idempotency checks in **Section 4.2**. |
| **Ignoring API Rate Limits** | Scripts crash when third-party APIs return HTTP 429 status codes. | Mandate exponential backoff in **Section 4.3**. |
| **Hardcoded Credentials** | API keys and secrets are leaked in code repositories or logs. | Enforce environment variables in **Section 3.3 & 4.2**. |
| **Unbounded Agent Loops** | Autonomous agents run infinite tool-execution loops, wasting credits. | Define max execution bounds & HITL steps in **Section 4.2**. |
| **Unstructured Text Logs** | Failure logs cannot be parsed or monitored by CloudWatch/Datadog. | Enforce JSON logging schema in **Section 5.2**. |

---

## 9. Example Prompts

### Example 1: Automated GitHub Issue Triage & Slack Alert Workflow (Python/Webhooks)

#### Completed SPARK Prompt

```markdown
# 1. ROLE & IDENTITY
## 1.1 Role
Senior DevOps Automation Engineer specializing in Python event-driven webhook processing and GitHub API integrations.

## 1.2 Cognitive Style
- Idempotent Webhook Processing
- Fault-Tolerant Error Handling & Rate Limit Resiliency

## 1.3 Tone & Voice
Technical, concise, direct. Return executable Python script with structured JSON logging. Omit preamble.

---

# 2. OBJECTIVE
## 2.1 Primary Goal
Create a Python FastAPI webhook service (`POST /webhooks/github`) that ingests GitHub `issues` events, categorizes issue urgency using OpenAI API, applies label tags via GitHub API, and dispatches high-urgency alerts to Slack.

## 2.2 Success Criteria
- Filter and process incoming webhook events in under 3000ms.
- Catch HTTP 429 rate limits from GitHub API and retry using exponential backoff.
- Ensure duplicate webhook delivery (`X-GitHub-Delivery` header) does not trigger duplicate AI API calls.

## 2.3 Non-Goals
- Do not build a web UI dashboard.
- Do not store issue bodies in a persistent database.

---

# 3. CONTEXT
## 3.1 Event Trigger & Payloads
- Trigger: Incoming GitHub Webhook `issues.opened` event payload.
- Key Input Fields: `action`, `issue.number`, `issue.title`, `issue.body`, `repository.full_name`.
- Auth: Validate incoming `X-Hub-Signature-256` header against `process.env.GITHUB_WEBHOOK_SECRET`.

## 3.2 External Integrations
- GitHub REST API: Apply label (`POST /repos/{owner}/{repo}/issues/{issue_number}/labels`).
- Slack Webhook API: Send rich block-kit JSON payload to `process.env.SLACK_ALERT_WEBHOOK_URL`.
- OpenAI API (`gpt-4o-mini`): Classify issue urgency (`CRITICAL`, `HIGH`, `MEDIUM`, `LOW`).

---

# 4. EXECUTION
## 4.1 Execution Logic
1. Signature Verification: Compute HMAC SHA-256 hash of incoming raw body using `GITHUB_WEBHOOK_SECRET`. Return HTTP 401 if invalid.
2. Idempotency Check: Check if `X-GitHub-Delivery` GUID exists in Redis. If present, return HTTP 200 `{"status": "DUPLICATE_IGNORED"}`.
3. Classification: Pass issue title and body to OpenAI API to classify urgency and select label (`bug`, `security`, `feature`).
4. Label Tagging: Call GitHub API to attach selected label to the issue.
5. Slack Alerting: IF urgency is `CRITICAL` or `HIGH`, dispatch a formatted Slack block-kit message to the alerts channel.
6. Cache Delivery GUID: Store `X-GitHub-Delivery` GUID in Redis with a 24-hour TTL.

## 4.2 Guardrails
- MUST verify webhook signature HMAC SHA-256 header before processing payload.
- MUST NOT make GitHub or Slack API requests if incoming `action != 'opened'`.
- MUST use exponential backoff (`time.sleep(2 ** attempt)`) if GitHub API returns HTTP 429.

## 4.3 Error Fallback
- IF OpenAI classification fails, default label to `triage-needed` and dispatch warning log.

---

# 5. OUTPUT SPECIFICATION
## 5.1 Format & Structure
Return a single, executable Python script (`app/webhook_handler.py`) utilizing FastAPI and `httpx` async client.

## 5.2 Logging Schema
Log all outputs as structured JSON:
```json
{
  "timestamp": "ISO-8601 String",
  "delivery_id": "String",
  "issue_number": "Integer",
  "classified_urgency": "CRITICAL | HIGH | MEDIUM | LOW",
  "status": "PROCESSED | DUPLICATE | ERROR"
}

7. VERIFICATION & REFINEMENT

7.1 Pre-Deployment Audit Checklist

1.  Is the HMAC SHA-256 webhook signature verified securely? [YES/NO]
2.  Does the Redis delivery GUID check prevent duplicate executions? [YES/NO]
3.  Are GitHub API rate limits caught and retried with backoff? [YES/NO]

7.2 Self-Correction Loop

  - IF checks fail, correct code internally before rendering final response.


#### Why It Works
* Verifies incoming webhook HMAC signatures to prevent unauthorized API trigger calls.
* Enforces idempotency by caching the GitHub delivery GUID in Redis.
* Handles GitHub API rate limits with backoffs and defaults to a safe fallback label (`triage-needed`) if the AI classification step fails.

---

### Example 2: Multi-Agent Market Research Workflow (Model Context Protocol [MCP])

#### Completed SPARK Prompt

```markdown
# 1. ROLE & IDENTITY
## 1.1 Role
Lead AI Agent Architect specializing in Model Context Protocol (MCP) tool integration and multi-agent task execution loops.

---

# 2. OBJECTIVE
## 2.1 Primary Goal
Configure a multi-agent autonomous research system using two specialized MCP tools (`fetch-mcp` and `postgres-mcp`) to scrape competitor product updates, synthesize strategic insights, and log structured records to a PostgreSQL database.

## 2.2 Success Criteria
- Enforce a maximum of 5 tool-execution iterations per research query to prevent infinite loops.
- Include a Human-in-the-Loop (HITL) approval step before writing records to the production database.

---

# 3. CONTEXT
## 3.1 Tools & MCP Servers
- Tool 1: `fetch_web_page(url: str)` via `fetch-mcp` server.
- Tool 2: `write_competitor_record(data: json)` via `postgres-mcp` server.

---

# 4. EXECUTION
## 4.1 Step-by-Step Agent Logic
1. Ingest target competitor company domain.
2. Execute `fetch_web_page` tool to extract raw HTML content from company changelog or blog page.
3. Synthesize product updates into a structured JSON record.
4. Human-in-the-Loop Check: Output summary to console and request user confirmation `[Y/N]` before database commit.
5. IF user confirms `Y`, execute `write_competitor_record` tool call to insert data into PostgreSQL.

## 4.2 Safety Guardrails
- MUST limit total tool-execution loop count strictly to 5 calls per run.
- MUST NOT execute `write_competitor_record` without explicit human confirmation.

---

# 5. OUTPUT SPECIFICATION
## 5.1 Format
Return the complete System Prompt and Agent Loop Configuration schema in JSON format.

Why It Works

  - Prevents infinite tool-execution loops by enforcing a strict iteration
    ceiling (max 5 calls).
  - Integrates a Human-in-the-Loop (HITL) confirmation checkpoint before
    allowing the agent to write data to a production database.

10. Copy-and-Paste Version

Copy this clean, unannotated block to start authoring automation and AI agent
workflow prompts:

# 1. ROLE & IDENTITY
## 1.1 Role
[AUTOMATION_ROLE_TITLE]

## 1.2 Cognitive Style
- [SYSTEM_PRINCIPLE_1]
- [SYSTEM_PRINCIPLE_2]

## 1.3 Tone & Voice
Technical, concise, objective, and direct. Return executable automation code, workflow configs, or agent prompts with zero preamble.

---

# 2. OBJECTIVE
## 2.1 Primary Goal
[PRIMARY_AUTOMATION_DELIVERABLE_STATEMENT]

## 2.2 Success Criteria
- [RELIABILITY_OR_CONTAINMENT_TARGET]
- [IDEMPOTENCY_REQUIREMENT]
- [LATENCY_OR_SLA_TARGET]

## 2.3 Non-Goals
- [OUT_OF_SCOPE_INTEGRATION_1]
- [PROHIBITED_PRACTICE_2]

---

# 3. CONTEXT
## 3.1 Trigger Event & Execution Schedule
- Trigger Source: [TRIGGER_SOURCE]
- Execution Environment: [EXECUTION_ENVIRONMENT]

## 3.2 Input & Output Payloads
- Input Schema: [INPUT_PAYLOAD_SCHEMA]
- Output Schema: [OUTPUT_PAYLOAD_SCHEMA]

## 3.3 External Tooling & Integrations
- APIs / Services: [APIS_AND_SERVICES]
- MCP Servers / Tools: [MCP_SERVERS_OR_TOOLS]
- Auth Strategy: [AUTHENTICATION_STRATEGY]

---

# 4. EXECUTION
## 4.1 Step-by-Step Logic & State Flow
1. [STEP_1_EVENT_INGESTION_AND_AUTH_VERIFICATION]
2. [STEP_2_INPUT_VALIDATION_AND_IDEMPOTENCY_CHECK]
3. [STEP_3_CORE_TRANSFORMATION_OR_AGENT_TOOL_CALL]
4. [STEP_4_TARGET_DESTINATION_EXECUTION]
5. [STEP_5_LOGGING_AND_NOTIFICATIONS]

## 4.2 Guardrails & Safety Controls
- MUST enforce idempotency checks to prevent duplicate execution processing.
- MUST handle API rate limits (HTTP 429) using exponential backoff with jitter.
- MUST NOT store API keys or passwords in raw code strings.
- MUST include Human-in-the-Loop (HITL) checkpoints for destructive or database-writing actions.

## 4.3 Exception, Retry & Fallback Strategy
- IF [RATE_LIMIT_SCENARIO] THEN [RETRY_ACTION]
- IF [NETWORK_TIMEOUT_SCENARIO] THEN [FALLBACK_DLQ_ROUTE]
- IF [INVALID_PAYLOAD_SCENARIO] THEN [ERROR_LOG_ACTION]

---

# 5. OUTPUT SPECIFICATION
## 5.1 Format & Structure
[DELIVERABLE_FORMAT_SPECIFICATION]

## 5.2 Logging & Observability Schema
```json
{
  "timestamp": "ISO-8601 String",
  "workflow_id": "String",
  "execution_id": "UUID",
  "status": "SUCCESS | RETRY | FAILED",
  "execution_time_ms": "Integer",
  "error_details": "String or Null"
}

6. EXAMPLES

6.1 Idempotent & Fault-Tolerant Execution Example

Unsafe Implementation (Avoid):

[WEAK_UNSAFE_EXAMPLE]

Resilient SPARK Implementation (Emulate):

[STRONG_RESILIENT_EXAMPLE]

7. VERIFICATION & REFINEMENT

7.1 Pre-Deployment Automation Audit Checklist

1.  Is the workflow completely idempotent (no duplicate database records)?
    [YES/NO]
2.  Are all API keys read securely from environment variables? [YES/NO]
3.  Does execution logic catch API rate limits (HTTP 429) and network timeouts?
    [YES/NO]
4.  Are failure alerts configured to notify an operations channel on DLQ routes?
    [YES/NO]

7.2 Self-Correction Loop

  - IF any audit check evaluates to NO, resolve failure internally before
    finalizing output.

8. NOTES

8.1 Operational Metadata

  - Framework Version: SPARK Automation v1.0
  - Target Model: [MODEL_ID]
  - Recommended Parameters: Temperature: 0.0


---

## 11. Summary

The **SPARK Automation Template** converts fragile AI automation scripts into resilient, idempotent, enterprise-grade workflows.

By declaring explicit event triggers, incoming/outgoing JSON schemas, tool definitions, idempotency rules, exponential backoff retries, and structured JSON logging, operations and engineering teams can deploy autonomous AI agents and API integration pipelines with total confidence.

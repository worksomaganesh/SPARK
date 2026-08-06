SPARK Coding & Software Engineering Template

Standardized Prompt Architecture for Software Development, Refactoring, and Code
Architecture

1. Introduction

The SPARK Coding Template is a specialized, language-agnostic template designed
for software engineering tasks using AI coding assistants (e.g., Cursor, Claude,
ChatGPT, GitHub Copilot, Gemini).

Generating production-grade software with Large Language Models presents
distinct engineering challenges:

  - Architectural Drift: Models generate isolated code snippets that ignore
    existing codebase patterns, dependency versions, or system architectures.
  - Security & Edge-Case Failures: Unbounded prompts lead to hardcoded secrets,
    unhandled null exceptions, missing input sanitization, and unsafe memory
    access.
  - Type & Syntax Errors: Missing language-version declarations cause models to
    use deprecated APIs or syntax incompatible with your runtime environment.

The SPARK Coding Template eliminates these failures by enforcing strict context
definitions, explicit runtime constraints, type-safety rules, security
guardrails, and unit testing requirements.

2. When to Use This Template

Use the SPARK Coding Template for all software development activities across any
programming language, framework, or cloud stack:

  - Building New Modules & Services: Designing REST APIs, microservices,
    database access layers, or UI components from scratch.
  - Refactoring Legacy Code: Restructuring technical debt, optimizing algorithms
    for time/memory complexity, or upgrading language versions (e.g., Python 2
    to 3, JavaScript to TypeScript).
  - Debugging & Defect Remediation: Root-cause analysis and resolution of bug
    reports, stack traces, race conditions, or memory leaks.
  - Writing Unit & Integration Tests: Generating test suites (e.g., PyTest,
    Jest, JUnit, Go testing) with mock fixtures and edge-case coverage.
  - System Architecture & Database Design: Designing SQL/NoSQL schemas, OpenAPI
    specifications, or Infrastructure-as-Code (Terraform, Kubernetes manifests).

3. When Not to Use This Template

Do not use the SPARK Coding Template for:

  - Trivial One-Line Queries: Quick syntax lookups or simple regular expression
    generation (e.g., "Regex for email validation").
  - Non-Engineering Content: Writing general business documentation, blog posts,
    or marketing copy (use templates/General.md instead).

4. How to Fill the Template

Authoring a software engineering prompt with SPARK follows a five-phase flow:

+-----------------------------------------------------------------------------------+
|                        CODING PROMPT AUTHORING WORKFLOW                           |
+-----------------------------------------------------------------------------------+
|  1. SET RUNTIME CONTEXT ──> Define Language, Framework, & Library Versions (Sec 3)|
|                                                                                   |
|  2. DECLARE OBJECTIVE   ──> Define Target Module & Non-Goals (Sec 2)              |
|                                                                                   |
|  3. DEFINE ARCHITECTURE ──> Outline Step-by-Step Logic & Guardrails (Sec 4)       |
|                                                                                   |
|  4. SPECIFY CODE FORMAT ──> Define Type Safety, Error Schema, & Tests (Sec 5)    |
|                                                                                   |
|  5. EMBED CODE AUDIT    ──> Add Linting & Security Checklist (Sec 7)              |
+-----------------------------------------------------------------------------------+

5. Complete Blank Coding SPARK Template

Below is the complete, annotated SPARK Coding Template. Bracketed placeholders
indicate the specific engineering details required.

# 1. ROLE & IDENTITY
## 1.1 Role
[Define Senior Engineering Specialty. Example: "Principal Backend Engineer specializing in high-throughput Python async microservices"]

## 1.2 Cognitive Style
- [Engineering Principle 1. Example: "SOLID Object-Oriented Design"]
- [Engineering Principle 2. Example: "Defensive Error Handling & Zero-Trust Security"]

## 1.3 Tone & Voice
Technical, concise, and direct. Omit conversational preamble. Return production-ready code with inline documentation.

---

# 2. OBJECTIVE
## 2.1 Primary Goal
[Single declarative statement defining the exact software deliverable.]

## 2.2 Success Criteria
- [Performance / Complexity Metric. Example: "Execution time MUST be O(N) or better"]
- [Type-Safety Requirement. Example: "100% strict type hints with zero `any` types"]
- [Testing Target. Example: "Include PyTest unit tests with >90% branch coverage"]

## 2.3 Non-Goals
- [Out-of-scope refactoring. Example: "Do not modify existing database migration files"]
- [Unwanted dependencies. Example: "Do not introduce third-party HTTP libraries; use standard library"]

---

# 3. CONTEXT
## 3.1 Software Stack & Runtime Environment
- Language & Version: [e.g., Python 3.11 / TypeScript 5.2 / Go 1.21 / Rust 1.75]
- Primary Framework: [e.g., FastAPI 0.104 / React 18.2 / Spring Boot 3.2]
- Key Libraries: [e.g., Pydantic v2, SQLAlchemy 2.0, Tokio, Zod]
- Database Engine: [e.g., PostgreSQL 16, Redis 7, MongoDB 6]

## 3.2 Existing Architecture & File Layout

[Paste relative directory structure or module dependency map here]


## 3.3 Target Consumer
[Downstream caller. Example: "Internal API Gateway consuming JSON RPC services"]

---

# 4. EXECUTION
## 4.1 Step-by-Step Implementation Logic
1. [Step 1: Data validation & input sanitization]
2. [Step 2: Core domain logic / processing algorithm]
3. [Step 3: Database transaction / external I/O execution]
4. [Step 4: Response construction & error handling]

## 4.2 Guardrails (Security & Code Quality)
- MUST [Positive Code Boundary. Example: "MUST use parameterized SQL queries to prevent SQL injection"]
- MUST NOT [Negative Code Boundary. Example: "MUST NOT store API keys or passwords as hardcoded strings"]

## 4.3 Fallback & Error Handling
- IF [Error Scenario 1] THEN [Catch exception, log structured JSON, return HTTP 400 Bad Request]
- IF [Error Scenario 2] THEN [Retry operation 3 times with exponential backoff before throwing custom Exception]

---

# 5. OUTPUT SPECIFICATION
## 5.1 Format & Structure
[Format specification: Single File / Multi-File Markdown code blocks with file path headers]

## 5.2 Syntactical & Style Rules
- [Style Guide. Example: "Adhere strictly to PEP 8 / Google TypeScript Style Guide"]
- [Documentation. Example: "Include JSDoc / Google-Style Docstrings for all public interfaces"]
- [Fencing. Example: "Return code inside fenced Markdown blocks with language identifiers"]

## 5.3 Interface & Type Schema
[Define target interface, data model, or function signature]

---

# 6. EXAMPLES
## 6.1 Input/Output Processing Example
### Expected Function Call:
```[language]
// Example input invocation

Expected Output Structure:

// Example returned data or generated object

7. VERIFICATION & REFINEMENT

7.1 Pre-Execution Code Audit Checklist

1.  Are all user input fields validated and sanitized before processing?
    [YES/NO]
2.  Does the implementation handle database connection timeouts and null
    pointers? [YES/NO]
3.  Is memory complexity bounded without potential memory leaks or infinite
    loops? [YES/NO]
4.  Are unit tests provided covering happy-path and failure scenarios? [YES/NO]

7.2 Self-Correction Loop

  - IF any audit check evaluates to NO, resolve the defect internally before
    outputting code.

8. NOTES

8.1 Operational Metadata

  - Framework Version: SPARK Coding v1.0
  - Target Model: [e.g., Claude Fable 5 / GPT-5.6 sol / Cursor Agent]
  - Recommended Parameters: Temperature: 0.0 (Deterministic execution)


---

## 6. Explanation of Every SPARK Section for Coding

### 6.1 Section 1: Role & Identity
* **Purpose**: Sets the model's software engineering specialization and design principles.
* **Coding Application**: Specifies engineering seniority (e.g., "Staff Systems Engineer") and domain focus (e.g., "Distributed Transactions", "React UI Performance"). This primes the model to output clean, maintainable, production-ready code.

### 6.2 Section 2: Objective
* **Purpose**: Defines the exact code deliverable, performance targets, and non-goals.
* **Coding Application**: Clarifies what code needs to be written while establishing performance bounds (e.g., Big-O time/space constraints) and non-goals (e.g., preventing unnecessary rewrites of peripheral files).

### 6.3 Section 3: Context
* **Purpose**: Documents the technical environment, language versions, existing codebase, and dependencies.
* **Coding Application**: Prevents syntax and import errors by specifying exact versions (e.g., "Python 3.11", "React 18"). Supplying file structures ensures generated code imports modules using correct relative paths.

### 6.4 Section 4: Execution
* **Purpose**: Details the step-by-step logic, security guardrails, and exception handling logic.
* **Coding Application**: Guides the model through input validation, core processing, and database transactions. Guardrails enforce security standards (e.g., OWASP Top 10 prevention, memory leak checks).

### 6.5 Section 5: Output Specification
* **Purpose**: Governs code layout, styling guidelines, type safety rules, and documentation standards.
* **Coding Application**: Enforces strict code formatting (PEP 8, ESLint rules), type annotations (`TypeScript`, Python type hints), docstrings, and code fencing conventions.

### 6.6 Section 6: Examples
* **Purpose**: Demonstrates expected function invocations, parameter types, and returned data models.
* **Coding Application**: Provides few-shot input/output examples to anchor complex algorithmic transformations or custom data serialization.

### 6.7 Section 7: Verification & Refinement
* **Purpose**: Implements an inline static analysis check before code generation completes.
* **Coding Application**: Forces the model to audit its code against memory safety checks, type correctness, error handling, and unit test requirements before outputting final tokens.

### 6.8 Section 8: Notes
* **Purpose**: Tracks operational parameters, target LLM engines, and prompt versions.
* **Coding Application**: Specifies model configuration (e.g., setting `temperature: 0.0` for deterministic execution) and documents prompt change histories.

---

## 7. Coding Best Practices

1. **Always Declare Exact Language & Framework Versions**: Never write "Python" or "React" alone. Write "Python 3.11 with FastAPI 0.104" or "React 18.2 with TypeScript 5.2" to prevent the model from using deprecated or incompatible syntax.
2. **Enforce Type Safety**: Require strict type annotations (`TypeScript`, Python `typing`, Rust types, Go interfaces). Disallow explicit or implicit `any` types.
3. **Mandate Defensive Error Handling**: Specify custom exception classes, HTTP status code mappings, and fallback retry mechanisms in Section 4.3.
4. **Isolate Code via Non-Goals**: Prevent AI coding assistants from modifying unprompted files or adding unapproved third-party dependencies by using Section 2.3.
5. **Request Unit Tests Alongside Production Code**: Require test suites (PyTest, Jest, Go Test) with happy-path, boundary, and error-state assertions.

---

## 8. Common Mistakes in AI Coding Prompts

| Mistake | Impact on AI Output | SPARK Remediation |
| :--- | :--- | :--- |
| **Omitting Version Details** | Model generates code using deprecated APIs or incompatible syntax. | Specify exact versions in **Section 3.1**. |
| **Missing Security Guardrails** | Code is vulnerable to SQL Injection, XSS, or hardcoded secrets. | Enforce OWASP security rules in **Section 4.2**. |
| **Unbounded Scope** | Model rewrites entire files, introducing breaking changes to working code. | Set explicit non-goals in **Section 2.3**. |
| **Ignoring Error Handling** | Code crashes on missing fields, null pointers, or network timeouts. | Define exception rules in **Section 4.3**. |
| **Missing Output Schemas** | Generated code uses mismatched data structures or missing fields. | Define interface schemas in **Section 5.3**. |

---

## 9. Example Prompts

### Example 1: Building a High-Throughput Async REST API (Python/FastAPI)

#### Completed SPARK Prompt

```markdown
# 1. ROLE & IDENTITY
## 1.1 Role
Senior Python Infrastructure Engineer specializing in high-throughput, asynchronous REST APIs and database access layers.

## 1.2 Cognitive Style
- Clean Architecture (Repository Pattern)
- Async I/O Performance Optimization
- Defensive Type Safety

## 1.3 Tone & Voice
Technical, concise, direct. Return production code with docstrings. Omit conversational preamble.

---

# 2. OBJECTIVE
## 2.1 Primary Goal
Create a FastAPI endpoint (`POST /v1/orders`) that validates incoming order payloads, writes records asynchronously to PostgreSQL using SQLAlchemy 2.0, and publishes an order creation event to Redis Pub/Sub.

## 2.2 Success Criteria
- Endpoint processing latency MUST execute under 20ms at p99.
- 100% type-hint coverage verified by `mypy --strict`.
- PyTest async unit test suite included with >90% code coverage.

## 2.3 Non-Goals
- Do not create user authentication middleware.
- Do not write database migration scripts.

---

# 3. CONTEXT
## 3.1 Software Stack
- Python: 3.11.6
- Framework: FastAPI 0.104.1
- ORM: SQLAlchemy 2.0.23 (Async Engine with `asyncpg`)
- Validation: Pydantic v2.5
- Redis Client: `redis-py` 5.0 (Async Redis)

## 3.2 File Layout Context

app/ ├── main.py ├── models/ │ └── order.py ├── schemas/ │ └── order.py └──
repositories/ └── order_repository.py


---

# 4. EXECUTION
## 4.1 Step-by-Step Logic
1. Define Pydantic v2 validation schema (`OrderCreateRequest`) with strict field constraints.
2. Implement async repository method to insert order into PostgreSQL using SQLAlchemy 2.0 async session.
3. Publish JSON serialized event payload to Redis channel `orders:created`.
4. Return HTTP 201 Created with created `OrderResponse` model.

## 4.2 Guardrails
- MUST use parameterized SQLAlchemy ORM models to prevent SQL injection.
- MUST NOT use synchronous database drivers or blocking I/O calls.
- MUST catch `SQLAlchemyError` and Redis network exceptions, mapping them to structured HTTP 500 JSON responses.

## 4.3 Fallback & Error Handling
- IF Pydantic validation fails, return HTTP 422 Unprocessable Entity with field error details.
- IF Redis publish fails, log the error as `WARNING` but allow the HTTP 201 order database commit to succeed.

---

# 5. OUTPUT SPECIFICATION
## 5.1 Format & Structure
Deliver code in multi-file Markdown blocks, explicitly indicating relative file paths:
- `app/schemas/order.py`
- `app/repositories/order_repository.py`
- `app/main.py`
- `tests/test_orders.py`

## 5.2 Syntactical Rules
- PEP 8 compliant formatting.
- Explicit async docstrings (Google Style) for all public functions.

---

# 7. VERIFICATION & REFINEMENT
## 7.1 Pre-Execution Code Audit Checklist
1. Are all database operations non-blocking (`await session.execute()`)? [YES/NO]
2. Are Pydantic schemas using v2 syntax (`ConfigDict`)? [YES/NO]
3. Are unit tests written using `pytest-asyncio` and mock fixtures? [YES/NO]

## 7.2 Self-Correction Loop
- IF any check evaluates to NO, fix the code internally before rendering final response.

---

# 8. NOTES
## 8.1 Operational Metadata
- Framework: SPARK Coding v1.0
- Target Model: Claude Sonnet 5
- Temperature: 0.0

Why It Works

  - Specifies exact Python, FastAPI, SQLAlchemy, and Pydantic library versions,
    preventing version mismatch syntax errors.
  - Enforces non-blocking async operations (asyncpg) and explicit fallback error
    handling for database vs. cache failures.
  - Requires complete multi-file structure alongside PyTest async unit tests.

Example 2: State-Safe UI Component (React / TypeScript)

Completed SPARK Prompt

# 1. ROLE & IDENTITY
## 1.1 Role
Principal Frontend Engineer specializing in React performance, accessibility (a11y), and TypeScript type safety.

---

# 2. OBJECTIVE
## 2.1 Primary Goal
Build a reusable, accessible Data Table component (`DataTable.tsx`) in React 18 and TypeScript with client-side sorting, filtering, and pagination.

## 2.2 Success Criteria
- Zero TypeScript `any` types.
- Fully accessible keyboard navigation conforming to WAI-ARIA Data Table standards.
- Re-render optimization using `React.memo` and `useCallback`.

## 2.3 Non-Goals
- Do not import external UI component libraries (e.g., MUI, AntD, Tailwind UI). Use CSS Modules only.

---

# 3. CONTEXT
## 3.1 Software Stack
- React: 18.2.0
- TypeScript: 5.2.2
- Styling: CSS Modules (`DataTable.module.css`)
- Icons: `lucide-react`

---

# 4. EXECUTION
## 4.1 Step-by-Step Logic
1. Define generic TypeScript interface `DataTableProps<T>`.
2. Manage pagination, sorting column, and sort direction via internal state hooks (`useState`).
3. Compute sorted and paginated data subset inside a `useMemo` hook to avoid recalculations on un-related re-renders.
4. Render accessible HTML5 table markup (`<table>`, `<thead>`, `<tbody>`, `aria-sort`, `aria-label`).

## 4.2 Guardrails
- MUST support generic data arrays (`T extends Record<string, unknown>`).
- MUST NOT trigger unnecessary re-renders when parent state updates.
- MUST provide keyboard event handlers (`Enter`, `Space`) for column header sorting buttons.

---

# 5. OUTPUT SPECIFICATION
## 5.1 Format & Structure
Return code in two file blocks:
- `src/components/DataTable/DataTable.tsx`
- `src/components/DataTable/DataTable.module.css`

---

# 7. VERIFICATION & REFINEMENT
## 7.1 Pre-Execution Code Audit Checklist
1. Is the component fully typed with generics without type assertions (`as target`)? [YES/NO]
2. Are WAI-ARIA accessibility attributes included on all interactive table elements? [YES/NO]

## 7.2 Self-Correction Loop
- IF checks fail, correct code internally before finalizing generation.

Why It Works

  - Uses TypeScript generics (DataTableProps<T>) to make the component reusable
    across any data type without resorting to any.
  - Enforces strict WCAG/WAI-ARIA accessibility compliance and React performance
    memoization.

10. Copy-and-Paste Version

Copy this clean, unannotated block to start authoring software engineering
prompts:

# 1. ROLE & IDENTITY
## 1.1 Role
[SENIOR_ROLE_TITLE]

## 1.2 Cognitive Style
- [ENGINEERING_PRINCIPLE_1]
- [ENGINEERING_PRINCIPLE_2]

## 1.3 Tone & Voice
Technical, concise, direct. Omit preamble. Return production-ready code with docstrings.

---

# 2. OBJECTIVE
## 2.1 Primary Goal
[PRIMARY_DELIVERABLE_STATEMENT]

## 2.2 Success Criteria
- [PERFORMANCE_OR_COMPLEXITY_METRIC]
- [TYPE_SAFETY_REQUIREMENT]
- [TESTING_COVERAGE_TARGET]

## 2.3 Non-Goals
- [OUT_OF_SCOPE_TASK_1]
- [OUT_OF_SCOPE_TASK_2]

---

# 3. CONTEXT
## 3.1 Software Stack & Runtime Environment
- Language & Version: [LANGUAGE_VERSION]
- Primary Framework: [FRAMEWORK_VERSION]
- Key Libraries: [LIBRARIES]
- Database Engine: [DATABASE_VERSION]

## 3.2 Existing Architecture & File Layout

[FILE_STRUCTURE_MAP]


## 3.3 Target Consumer
[DOWNSTREAM_CALLER]

---

# 4. EXECUTION
## 4.1 Step-by-Step Implementation Logic
1. [STEP_1]
2. [STEP_2]
3. [STEP_3]

## 4.2 Guardrails (Security & Code Quality)
- MUST [MANDATORY_SECURITY_OR_QUALITY_RULE]
- MUST NOT [PROHIBITED_PRACTICE]

## 4.3 Fallback & Error Handling
- IF [ERROR_SCENARIO_1] THEN [HANDLING_ACTION_1]
- IF [ERROR_SCENARIO_2] THEN [HANDLING_ACTION_2]

---

# 5. OUTPUT SPECIFICATION
## 5.1 Format & Structure
[FILE_FORMAT_AND_STRUCTURE]

## 5.2 Syntactical & Style Rules
- [STYLE_GUIDE]
- [DOCUMENTATION_STANDARD]

## 5.3 Interface & Type Schema
[TYPE_INTERFACE_DEFINITIONS]

---

# 6. EXAMPLES
## 6.1 Input/Output Processing Example
### Expected Function Call:
```[LANGUAGE]
// Input sample

Expected Output Structure:

// Output sample

7. VERIFICATION & REFINEMENT

7.1 Pre-Execution Code Audit Checklist

1.  Are all user input fields validated and sanitized? [YES/NO]
2.  Are connection timeouts and null pointers handled explicitly? [YES/NO]
3.  Is memory and time complexity optimized? [YES/NO]
4.  Are unit tests included covering happy-path and failure scenarios? [YES/NO]

7.2 Self-Correction Loop

  - IF any audit check evaluates to NO, resolve the defect internally before
    outputting code.

8. NOTES

8.1 Operational Metadata

  - Framework Version: SPARK Coding v1.0
  - Target Model: [MODEL_ID]
  - Recommended Parameters: Temperature: 0.0


---

## 11. Summary

The **SPARK Coding Template** replaces informal coding prompts with structured software specifications.

By declaring exact language versions, explicit type-safety constraints, security guardrails, error-handling logic, and unit testing requirements, developers can use AI assistants to generate clean, maintainable, secure, and production-ready code.

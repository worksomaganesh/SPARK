Applying the SPARK Framework to Cursor AI

Official Field Guide and Real-World Software Engineering Examples for Cursor AI
Code Editor

1. Introduction

Cursor AI is an AI-native code editor built on top of VS Code that integrates
Large Language Models (such as Claude Sonnet 5 and GPT-5.6 sol) directly into
software engineering workflows.

Key features of Cursor include:

  - Cursor Composer (Cmd+I / Ctrl+I): Multi-file code generation and
    repository-wide refactoring.
  - Cursor Chat (Cmd+L / Ctrl+L): Context-aware repository analysis utilizing
    @Codebase indexing.
  - Inline Generation (Cmd+K / Ctrl+K): Direct code edits and refactoring within
    specific file selections.
  - System Rules (.cursorrules): Project-level custom instructions enforced
    across all AI interactions.

However, using Cursor without a structured framework can lead to significant
software engineering issues:

  - Architectural Drift: Cursor Composer generates multi-file code that breaks
    established project patterns, directory conventions, or dependency versions.
  - Unbounded File Edits: AI edits bleed into unintended files, introducing
    breaking API changes across peripheral modules.
  - Missing Error Handling & Type Safety: Unconstrained code generation defaults
    to implicit any types, missing null checks, and unhandled exceptions.
  - Hardcoded Secrets & Security Gaps: Code generated without safety guardrails
    frequently includes hardcoded API keys, raw unparameterized SQL queries, or
    vulnerable endpoints.

The SPARK Framework solves these issues by providing a structured layout that
bounds Cursor's multi-file execution engines.

2. Why Use SPARK with Cursor

Cursor relies on vector embeddings of your local codebase (@Codebase) combined
with multi-file edit execution models. When a prompt uses SPARK's structured
headings, Cursor's attention mechanism isolates project context from execution
guardrails with high precision.

+-----------------------------------------------------------------------------------+
|                        ATTENTION MAPPING IN CURSOR AI                             |
+-----------------------------------------------------------------------------------+
| UNSTRUCTURED CURSOR PROMPT          │ SPARK STRUCTURED CURSOR PROMPT              |
+-------------------------------------+---------------------------------------------+
| "Hey, refactor my auth system to    | # 1. ROLE & IDENTITY                        |
| use JWTs. Make it clean, update     | # 2. OBJECTIVE                              |
| the database files, and fix tests." | # 3. CONTEXT (@Codebase / @Files)           |
|                                     | # 4. EXECUTION (Step-by-Step Logic)         |
|                                     | # 4.2 GUARDRAILS (MUST / MUST NOT)          |
|                                     | # 5. OUTPUT SPECIFICATION (Exact Files)     |
+-------------------------------------+---------------------------------------------+
|  Result: Modifies unintended files, |  Result: Precise multi-file edits,          |
|  introduces breaking API changes.   |  100% type safety, zero peripheral edits.   |
+-----------------------------------------------------------------------------------+

Using SPARK with Cursor delivers four key benefits:

1.  Multi-File Scope Control in Composer: Defining explicit Non-Goals
    (Section 2.3) and Output Specifications (Section 5) prevents Cursor Composer
    from modifying files outside the target scope.
2.  Deterministic Context Indexing: Structuring @Codebase and @Files references
    inside Section 3 (Context) ensures Cursor indexes exact repository
    interfaces.
3.  Automated Security Enforcement: Placing OWASP security rules inside
    Section 4.2 (Guardrails) ensures generated code uses parameterized queries,
    environment variables, and defensive validation.
4.  Persistent Project Enforcement via .cursorrules: SPARK sections map directly
    into Cursor's .cursorrules file to enforce global coding standards across
    all developers on a team.

3. Cursor Features That Work Well with SPARK

3.1 Project System Rules (.cursorrules)

Cursor reads a .cursorrules file placed in the root of your project directory to
enforce global system instructions. SPARK sections map into .cursorrules as
follows:

# .cursorrules (Global SPARK Rules)

# 1. ROLE & IDENTITY
You are a Principal Software Engineer specializing in TypeScript 7.0.2, React 19.28, and Node.js v24.19.0 LTS microservices.

# 4. EXECUTION GUARDRAILS
- MUST use strict TypeScript annotations. Zero `any` or `unknown` types allowed.
- MUST use parameterized SQL queries (`pg` / `Prisma`). Never concatenate strings in queries.
- MUST NOT modify files outside the user's explicitly requested directory scope.
- MUST write PyTest / Jest unit tests for all new functional endpoints.

# 5. OUTPUT SPECIFICATION
- Return code in multi-file Markdown blocks with clear relative file path headers.
- Format code according to repository ESLint / Prettier rules.

3.2 Cursor Composer (Cmd+I / Ctrl+I)

Composer executes multi-file code generation. To prevent Composer from
hallucinating file paths or making breaking changes across your project:

  - Define explicit relative file path headers in Section 5.1.
  - Include explicit negative guardrails (MUST NOT) in Section 4.2 prohibiting
    modifications to shared configuration files.

3.3 Cursor Chat & Context Tags (@Codebase, @Files, @Folder)

When asking questions or initiating refactoring tasks in Cursor Chat (Cmd+L),
map Cursor's context tags into Section 3 (Context):

# 3. CONTEXT
## 3.1 Codebase References
- Target Module: @Folder:src/auth
- Shared Interfaces: @File:src/types/user.ts
- Database Schema: @File:prisma/schema.prisma

4. Best Practices for AI-Assisted Coding

1.  Explicitly Declare Software Versions: State exact runtime and library
    versions in Section 3.1 (e.g., Python 3.14.7, FastAPI 0.104, React 19.2.8).
2.  Prevent Scope Creep with Non-Goals: Use Section 2.3 to explicitly list
    files, databases, or migrations that Cursor MUST NOT touch.
3.  Require Type-Safe Schemas: Force strict schema validation (Pydantic v2.13.4, Zod,
    TypeScript types) in Section 5.3 before code generation starts.
4.  Demand Unit Tests Alongside Code: Always require unit tests (PyTest, Jest,
    Vitest, Go Test) in Section 2.2 and Section 5.1 to verify generated code
    immediately.
5.  Enforce Security Boundaries: Require environment variables for secrets and
    parameterized queries for database operations in Section 4.2.

5. Managing Large Codebases with SPARK

In large repositories (>100,000 lines of code), providing unrestricted @Codebase
context to Cursor can introduce noise into the LLM's attention mechanism.

To manage large codebases effectively:

1.  Scope context using @Folder or @File tags inside Section 3.1 rather than
    relying solely on global @Codebase searches.
2.  Outline current architectural dependency maps inside Section 3.2 so Cursor
    understands module relationships before proposing edits.
3.  Require explicit dry-run steps in Section 4.1 (e.g., "Step 1: List all files
    to be modified and wait for approval before generating code").

6. Using SPARK for Refactoring

Refactoring legacy code carries the risk of introducing breaking API changes or
unintended side effects.

When authoring a SPARK refactoring prompt:

  - Set a strict non-goal in Section 2.3: MUST NOT alter public function
    signatures or exported interface contracts.
  - Enforce backwards compatibility in Section 4.2: MUST ensure all existing
    unit tests pass without modifications to test assertions.
  - Request before-and-after structural comparisons in Section 5.1.

7. Using SPARK for Debugging

When resolving complex runtime errors, deadlocks, or memory leaks with Cursor:

  - Paste the exact stack trace and runtime environment details inside Section 3
    (Context).
  - Require a two-stage execution in Section 4.1:
    1.  Stage 1: Provide a Root-Cause Failure Analysis explaining the memory or
        state mechanics driving the error.
    2.  Stage 2: Provide the minimal, isolated bug fix payload.
  - Add a guardrail in Section 4.2: MUST NOT rewrite working peripheral
    functions to fix the isolated bug.

8. Using SPARK for Documentation

Auto-generating technical documentation (OpenAPI specs, JSDoc/Docstrings,
Architecture Diagrams) with Cursor:

  - Direct Cursor to read target source files using @File tags in Section 3.
  - Specify exact documentation standards (e.g., Google Python Docstrings,
    OpenAPI 3.0 YAML, Mermaid.js diagrams) in Section 5.
  - Enforce completeness in Section 4.2: MUST document all edge-case error
    response codes (400, 401, 404, 500), not just happy-path responses.

9. Complete SPARK Examples

9.1 Creating a New Project: Production Rust Web Microservice

Problem Statement

A developer needs to scaffold a new, production-grade Rust web microservice
using Axum, Tokio, and SQLx with strict error handling and health check
endpoints.

Complete SPARK Prompt

# 1. ROLE & IDENTITY
## 1.1 Role
Principal Rust Systems Engineer specializing in high-throughput, memory-safe asynchronous web microservices using Axum and Tokio.

## 1.2 Cognitive Style
- Zero-Cost Abstraction & Memory Safety
- Defensive Async State Management

## 1.3 Tone & Voice
Technical, concise, direct. Return complete production Rust code with docstrings. Omit preamble.

---

# 2. OBJECTIVE
## 2.1 Primary Goal
Scaffold a production-ready Rust web microservice (`user-service`) using `axum`, `tokio`, `sqlx` (PostgreSQL), and `serde` featuring a `/health` endpoint and a `/v1/users` CRUD route handler.

## 2.2 Success Criteria
- 100% compile-ready code passing `cargo check` with zero warnings.
- Explicit custom error handling implementing Axum's `IntoResponse` trait.
- Integration test file using `tokio::test`.

## 2.3 Non-Goals
- Do not build frontend HTML templates.
- Do not implement OAuth2 authentication servers.

---

# 3. CONTEXT
## 3.1 Environment Dependencies
- Rust Edition: 2021 (Rust 1.75+)
- Key Crates: `axum = "0.7"`, `tokio = { version = "1.35", features = ["full"] }`, `sqlx = { version = "0.7", features = ["postgres", "runtime-tokio-native-tls"] }`, `serde = { version = "1.0", features = ["derive"] }`

---

# 4. EXECUTION
## 4.1 Step-by-Step Logic
1. Create `Cargo.toml` dependency file.
2. Define custom `AppError` enum implementing Axum `IntoResponse` to map database errors to HTTP 500 JSON.
3. Define database model structs (`User`) with `sqlx::FromRow` and `serde::Serialize`.
4. Construct Axum router in `src/main.rs` attaching shared database pool state (`AppState`).
5. Write integration test in `tests/health_check.rs`.

## 4.2 Guardrails
- MUST use environment variables (`std::env::var("DATABASE_URL")`) for connection strings.
- MUST NOT use `unwrap()` or `expect()` in production route handlers; handle all `Result` types explicitly.

---

# 5. OUTPUT SPECIFICATION
## 5.1 Format & Structure
Return code in multi-file Markdown blocks with relative file path headers:
- `Cargo.toml`
- `src/main.rs`
- `src/error.rs`
- `src/models.rs`
- `src/handlers.rs`
- `tests/health_check.rs`

Why the Prompt Works

  - Bans unwrap() calls in Section 4.2, forcing Cursor to write production-grade
    error handling.
  - Specifies exact crate versions (axum = "0.7") to prevent syntax mismatches
    between Axum major versions.

Expected Cursor AI Output

Six distinct, fully compilable Rust files containing Axum route handlers, SQLx
query bindings, custom IntoResponse error implementations, and Tokio integration
tests.

Possible Improvements

Add Dockerfile and docker-compose.yml local database setup requirements.

9.2 Understanding an Existing Codebase: AST Analysis of a Repository

Problem Statement

A developer joining a new team needs a structural architectural analysis of a
complex TypeScript/Node.js repository indexed in Cursor via @Codebase.

Complete SPARK Prompt

# 1. ROLE & IDENTITY
## 1.1 Role
Principal Software Architect and Technical Lead Auditor.

## 1.2 Cognitive Style
- High-Level System Decomposition
- Dependency Mapping & Architectural Risk Analysis

---

# 2. OBJECTIVE
## 2.1 Primary Goal
Perform a structural architectural analysis of the `@Codebase` to map module boundaries, data flow pipelines, database ORM models, and technical debt risks.

## 2.2 Success Criteria
- Identify core entry points, routing layers, and database access patterns.
- Render a Mermaid.js component diagram illustrating service module dependencies.
- Highlight top 3 architectural risks (e.g., circular dependencies, unhandled async promises).

---

# 3. CONTEXT
## 3.1 Codebase Target
Indexed repository context via @Codebase targeting `@Folder:src`.

---

# 4. EXECUTION
## 4.1 Logic & Steps
1. Scan `@Folder:src` to identify entry point files (`index.ts`, `server.ts`, `app.ts`).
2. Map directory hierarchy to architectural patterns (e.g., MVC, Clean Architecture, Monolith).
3. Trace data flow from HTTP request handlers to database queries.
4. Construct a Mermaid.js diagram showing component relationships.
5. Identify anti-patterns or missing error boundary handlers.

## 4.2 Guardrails
- MUST reference actual file paths from the repository.
- MUST NOT invent hypothetical modules not present in `@Codebase`.

---

# 5. OUTPUT SPECIFICATION
## 5.1 Format
Structured Markdown Architecture Report:
- `## Executive Architecture Summary`
- `## Module Dependency Map (Mermaid.js Diagram)`
- `## Data Flow Pipeline`
- `## Architectural Risks & Recommendations`

Why the Prompt Works

  - Leverages Cursor's @Codebase vector indexing while constraining analysis to
    concrete files in @Folder:src.
  - Forces Cursor to output a visual Mermaid.js diagram detailing real codebase
    dependencies.

Expected Cursor AI Output

A clear, accurate Architecture Report mapping the project's real entry points,
controllers, services, and database layers, complete with a rendered Mermaid.js
dependency diagram.

Possible Improvements

Ask Cursor to generate a list of missing unit test files across the repository.

9.3 Refactoring Legacy Code: Converting Monolithic CommonJS to TypeScript

Problem Statement

A developer needs to refactor an unstructured CommonJS JavaScript file
(authService.js) into a modern, type-safe TypeScript module using ES Modules and
Zod validation.

Complete SPARK Prompt

# 1. ROLE & IDENTITY
## 1.1 Role
Principal TypeScript Architect specializing in Node.js backend modernization and type-safe refactoring.

---

# 2. OBJECTIVE
## 2.1 Primary Goal
Refactor the legacy file `@File:src/legacy/authService.js` into a modern TypeScript module `@File:src/services/authService.ts` using ES Modules, strict typing, and Zod validation.

## 2.2 Success Criteria
- 100% type-hint coverage passing `tsc --strict`.
- Zero explicit or implicit `any` types.
- Preserve exact public method signatures to avoid breaking caller modules.

## 2.3 Non-Goals
- Do not modify database table schemas or Prisma migration files.

---

# 3. CONTEXT
## 3.1 Legacy Code Reference
Target source code: @File:src/legacy/authService.js
Target environment: TypeScript 7.0.2, Node.js v24.19.0 LTS, Zod v4.4.3

---

# 4. EXECUTION
## 4.1 Step-by-Step Refactoring Logic
1. Analyze `@File:src/legacy/authService.js` to identify exported functions and parameters.
2. Define Zod validation schemas for all payload inputs.
3. Infer TypeScript interfaces directly from Zod schemas.
4. Refactor function bodies to use async/await and ES Module exports (`export const ...`).
5. Ensure error handling uses custom application Exception classes.

## 4.2 Guardrails
- MUST NOT use CommonJS `require()` or `module.exports`.
- MUST NOT alter exported function names or parameter order.

---

# 5. OUTPUT SPECIFICATION
## 5.1 Format
Return single refactored TypeScript file block targeting `src/services/authService.ts`.

Why the Prompt Works

  - References the specific legacy file using Cursor's @File context tag in
    Section 3.1.
  - Prevents breaking downstream callers by mandating exported function
    signature preservation in Section 2.2.

Expected Cursor AI Output

A clean, fully typed TypeScript module containing Zod schemas, explicit
interfaces, async/await execution, and ES Module exports.

Possible Improvements

Run Cursor Composer (Cmd+I) using this prompt to update both the refactored
service and its unit test file simultaneously.

9.4 Debugging an Application: Resolving a Go Channel Deadlock

Problem Statement

A Go application crashes intermittently under high concurrency due to a channel
deadlock in a worker pool implementation.

Complete SPARK Prompt

# 1. ROLE & IDENTITY
## 1.1 Role
Staff Systems Engineer specializing in Go runtime concurrency, channel synchronization, and deadlock resolution.

---

# 2. OBJECTIVE
## 2.1 Primary Goal
Identify the deadlock root cause in `@File:pkg/worker/pool.go`, explain the channel synchronization failure, and provide a fixed, thread-safe implementation using `sync.WaitGroup` and buffered channels.

---

# 3. CONTEXT
## 3.1 Faulty Source File
Target file: @File:pkg/worker/pool.go

## 3.2 Error Stack Trace
`fatal error: all goroutines are asleep - deadlock!`

---

# 4. EXECUTION
## 4.1 Logic & Steps
1. Trace channel send/receive operations across worker goroutines in `@File:pkg/worker/pool.go`.
2. Pinpoint unclosed channels or un-buffered sends causing blocked goroutines.
3. Refactor worker pool to ensure `close(jobs)` and `wg.Wait()` execute in correct order.
4. Provide a Go benchmark test verifying concurrent worker pool execution under load.

## 4.2 Guardrails
- MUST use `sync.WaitGroup` to track active worker completion.
- MUST NOT remove channel buffering without documenting performance impacts.

---

# 5. OUTPUT SPECIFICATION
## 5.1 Format
1. `## Root-Cause Failure Analysis` (Concise explanation of channel block)
2. `## Refactored Code` (`pkg/worker/pool.go`)
3. `## Verification Test` (`pkg/worker/pool_test.go`)

Why the Prompt Works

  - Directs Cursor to perform a root-cause concurrency analysis before
    generating code, ensuring the deadlock fix is fully explained.
  - Provides both the fixed code and a race-detector-compliant test file
    (pool_test.go).

Expected Cursor AI Output

A clear explanation of why unclosed worker channels caused goroutine starvation,
followed by corrected Go channel logic and a benchmark unit test.

Possible Improvements

Request additional context-cancellation (context.Context) handling for graceful
shutdown.

9.5 Building a REST API: FastAPI Async Endpoint with SQLAlchemy 2.0

Problem Statement

A backend developer needs a FastAPI REST endpoint (POST /v1/products) with async
SQLAlchemy 2.0 database access, Pydantic v2 validation, and unit tests.

Complete SPARK Prompt

# 1. ROLE & IDENTITY
## 1.1 Role
Principal Python Engineer specializing in async FastAPI microservices and SQLAlchemy 2.0 ORM layers.

---

# 2. OBJECTIVE
## 2.1 Primary Goal
Implement a complete `POST /v1/products` REST API endpoint that validates incoming product payloads, inserts records asynchronously into PostgreSQL using SQLAlchemy 2.0, and returns created product data.

## 2.2 Success Criteria
- 100% strict type hint coverage verified by `mypy --strict`.
- Async database calls using SQLAlchemy 2.0 `asyncpg`.
- Include PyTest async unit tests using `pytest-asyncio`.

---

# 3. CONTEXT
## 3.1 Existing Repository References
- Database Session Setup: @File:app/database.py
- Existing ORM Base: @File:app/models/base.py

---

# 4. EXECUTION
## 4.1 Implementation Steps
1. Create Pydantic v2 schemas (`ProductCreate`, `ProductResponse`) in `app/schemas/product.py`.
2. Create SQLAlchemy 2.0 ORM model (`ProductModel`) in `app/models/product.py`.
3. Create Async Repository class (`ProductRepository`) in `app/repositories/product.py`.
4. Register FastAPI route handler in `app/api/v1/products.py`.
5. Write async unit test in `tests/api/test_products.py`.

## 4.2 Guardrails
- MUST use SQLAlchemy 2.0 `select()` and `async_session` execution.
- MUST NOT use synchronous `db.query()` legacy SQLAlchemy 1.x syntax.
- MUST map `SQLAlchemyError` exceptions to HTTP 500 JSON error responses.

---

# 5. OUTPUT SPECIFICATION
## 5.1 Format
Deliver code in multi-file Markdown blocks:
- `app/schemas/product.py`
- `app/models/product.py`
- `app/repositories/product.py`
- `app/api/v1/products.py`
- `tests/api/test_products.py`

Why the Prompt Works

  - Explicitly references existing project database setups
    (@File:app/database.py) so generated code integrates seamlessly into the
    codebase.
  - Enforces SQLAlchemy 2.0 async conventions while banning legacy 1.x
    synchronous patterns.

Expected Cursor AI Output

Five distinct Python files configured to run asynchronously with Pydantic v2
validation, SQLAlchemy 2.0 repository methods, and PyTest async fixtures.

Possible Improvements

Add Redis caching rules in app/repositories/product.py for GET endpoints.

9.6 Developing a React Component: Accessible DataTable in React 19.2.8 & Tailwind

Problem Statement

A frontend developer needs a reusable, accessible React 19.2.8 DataTable component
with sorting, pagination, and Tailwind CSS styling.

Complete SPARK Prompt

# 1. ROLE & IDENTITY
## 1.1 Role
Principal Frontend Engineer specializing in React 19.2.8, TypeScript, Tailwind CSS, and WCAG accessibility standards.

---

# 2. OBJECTIVE
## 2.1 Primary Goal
Build a reusable, generic React 19.2.8 DataTable component (`DataTable.tsx`) supporting column sorting, client-side pagination, and accessible ARIA markup.

## 2.2 Success Criteria
- Zero explicit or implicit TypeScript `any` types (support generic types `DataTableProps<T>`).
- Full keyboard navigation and WAI-ARIA Data Table accessibility compliance.
- Styled exclusively with Tailwind CSS utility classes.

---

# 3. CONTEXT
## 3.1 Tech Stack
React 19.2.8, TypeScript 7.0.2, Tailwind CSS 4.3.3, Lucide React Icons (`lucide-react`).

---

# 4. EXECUTION
## 4.1 Step-by-Step Logic
1. Define generic TypeScript interfaces (`Column<T>`, `DataTableProps<T>`).
2. Manage sorting and pagination state using `useState` hooks.
3. Memoize sorted and sliced data arrays using `useMemo` to prevent unnecessary re-renders.
4. Render HTML5 `<table>` with ARIA sorting attributes (`aria-sort`, `aria-label`).
5. Render pagination control bar with page size selector.

## 4.2 Guardrails
- MUST memoize computational sorting functions using `useMemo`.
- MUST NOT use inline style objects (`style={{...}}`); use Tailwind CSS classes exclusively.

---

# 5. OUTPUT SPECIFICATION
## 5.1 Format
Multi-file output:
- `src/components/DataTable/DataTable.tsx`
- `src/components/DataTable/DataTable.stories.tsx` (Storybook Story)

Why the Prompt Works

  - Enforces generic TypeScript safety (DataTableProps<T>) so the component
    works with any data model.
  - Mandates WCAG accessibility compliance and React performance memoization.

Expected Cursor AI Output

A clean, fully typed React 19.2.8 component styled with Tailwind CSS, featuring
keyboard accessibility, memoized sorting/pagination, and a companion Storybook
story file.

Possible Improvements

Add server-side pagination prop callbacks (onPageChange, onSortChange).

9.7 Writing Unit Tests: PyTest Async Test Suite with Mock Fixtures

Problem Statement

A developer needs a comprehensive PyTest unit test suite for an existing API
service module (@File:app/services/user_service.py).

Complete SPARK Prompt

# 1. ROLE & IDENTITY
## 1.1 Role
Senior Quality Assurance & Python Test Automation Engineer specializing in `pytest`, `pytest-asyncio`, and mock object design.

---

# 2. OBJECTIVE
## 2.1 Primary Goal
Write a comprehensive, async PyTest test suite targeting `@File:app/services/user_service.py` to achieve >90% branch code coverage.

## 2.2 Success Criteria
- Test happy-path execution, validation failures, and database timeout scenarios.
- Use `unittest.mock.AsyncMock` to isolate tests from live external database calls.
- 100% compliant with `pytest-asyncio` markers (`@pytest.mark.asyncio`).

---

# 3. CONTEXT
## 3.1 Target Service File
Target module to test: @File:app/services/user_service.py

---

# 4. EXECUTION
## 4.1 Step-by-Step Testing Strategy
1. Analyze function branches and exception paths in `@File:app/services/user_service.py`.
2. Construct PyTest fixtures in `conftest.py` for mock database sessions and mock user payloads.
3. Write test functions covering:
   - `test_create_user_success`
   - `test_create_user_duplicate_email_raises_exception`
   - `test_get_user_not_found_returns_none`
   - `test_database_timeout_raises_service_error`

## 4.2 Guardrails
- MUST NOT execute real database network calls during unit tests.
- MUST use `@pytest.mark.asyncio` on all async test functions.

---

# 5. OUTPUT SPECIFICATION
## 5.1 Format
- `tests/unit/test_user_service.py`

Why the Prompt Works

  - Directs Cursor to analyze all conditional code branches in the target file
    before writing tests, ensuring high test coverage.
  - Enforces isolation from live databases by requiring AsyncMock fixtures.

Expected Cursor AI Output

A complete PyTest test file (test_user_service.py) featuring async fixtures,
mock database exceptions, and happy-path vs. failure assertions.

Possible Improvements

Add coverage reporting flags (--cov=app/services) to execution commands.

9.8 Generating Technical Documentation: OpenAPI 3.0 YAML & Architecture Specs

Problem Statement

A technical writer needs an OpenAPI 3.0 YAML specification generated
automatically from existing FastAPI route handlers.

Complete SPARK Prompt

# 1. ROLE & IDENTITY
## 1.1 Role
Principal API Documentation Architect specializing in OpenAPI 3.0 specifications and RESTful documentation.

---

# 2. OBJECTIVE
## 2.1 Primary Goal
Generate a valid OpenAPI 3.0 YAML specification document by analyzing the route handlers in `@Folder:app/api/v1`.

---

# 3. CONTEXT
## 3.1 Target Routes
Source code directory: @Folder:app/api/v1

---

# 4. EXECUTION
## 4.1 Analysis & Generation Logic
1. Scan `@Folder:app/api/v1` to extract endpoints, HTTP methods, path parameters, and query parameters.
2. Inspect corresponding Pydantic request/response schemas.
3. Map error handling decorators to standard HTTP 400, 401, 404, and 500 error schema components.
4. Construct OpenAPI 3.0 YAML hierarchy including Bearer Authentication security schemes.

## 4.2 Guardrails
- MUST generate 100% valid OpenAPI 3.0 YAML syntax.
- MUST NOT omit error status code definitions (400, 401, 500).

---

# 5. OUTPUT SPECIFICATION
## 5.1 Format
Single valid OpenAPI 3.0 YAML block saved to `docs/openapi.yaml`.

Why the Prompt Works

  - Inspects actual route files (@Folder:app/api/v1) using Cursor's folder
    indexing tag to construct precise API definitions.
  - Mandates complete error status code documentation.

Expected Cursor AI Output

A complete, valid OpenAPI 3.0 YAML specification file (docs/openapi.yaml)
mapping all routes, schemas, parameters, and authentication rules.

Possible Improvements

Add Swagger UI HTML integration setup instructions.

9.9 Designing System Architecture: Event-Driven Payment Pipeline

Problem Statement

A lead architect needs a System Architecture Specification and Mermaid.js
sequence diagram for a high-throughput, event-driven payment clearing pipeline.

Complete SPARK Prompt

# 1. ROLE & IDENTITY
## 1.1 Role
Principal Distributed Systems Architect specializing in event-driven financial architectures and Apache Kafka pipelines.

---

# 2. OBJECTIVE
## 2.1 Primary Goal
Design an Event-Driven Payment Clearing System architecture specification using Apache Kafka, PostgreSQL, and Redis.

## 2.2 Success Criteria
- Include a Mermaid.js sequence diagram illustrating payment authorization, fraud checks, database commits, and Kafka event publishing.
- Detail failure modes, idempotency key checks, and Dead Letter Queue (DLQ) handling.

---

# 3. CONTEXT
## 3.1 System Performance Constraints
Throughput: 10,000 TPS at p99 < 50ms latency.
Availability: 99.999% uptime (Five Nines).

---

# 4. EXECUTION
## 4.1 Step-by-Step Logic
1. System Component Overview: Define API Gateway, Payment Worker, Fraud Microservice, Kafka Broker, and PostgreSQL Cluster roles.
2. End-to-End Sequence Flow: Draft Mermaid.js sequence diagram illustrating message lifecycle.
3. State & Idempotency Strategy: Detail Redis key checking to prevent double-charging.
4. Error & DLQ Strategy: Outline handling for failed fraud checks vs. database connection timeouts.

## 4.2 Guardrails
- MUST validate Mermaid.js diagram syntax for rendering correctness.
- MUST explicitly detail idempotency key validation steps.

---

# 5. OUTPUT SPECIFICATION
## 5.1 Format
Markdown Architecture Spec saved to `docs/architecture/payment_pipeline.md`.

Why the Prompt Works

  - Forces visual architecture mapping using Mermaid.js diagrams alongside
    technical text descriptions.
  - Focuses heavily on critical financial system requirements (idempotency, DLQ
    error routes).

Expected Cursor AI Output

A detailed System Architecture specification containing system SLAs, state
transition rules, a valid Mermaid.js sequence diagram, and an idempotency
strategy.

Possible Improvements

Include a Kubernetes deployment manifest spec in docs/architecture/k8s.yaml.

9.10 Implementing New Features: Adding OAuth2 PKCE Authentication

Problem Statement

A developer needs to implement an OAuth2 Authorization Code Flow with PKCE in an
existing Express/TypeScript backend.

Complete SPARK Prompt

# 1. ROLE & IDENTITY
## 1.1 Role
Principal Security Engineer specializing in OAuth 2.0 / OIDC authentication protocols and Node.js security.

---

# 2. OBJECTIVE
## 2.1 Primary Goal
Implement an OAuth2 PKCE (Proof Key for Code Exchange) authorization flow in `@Folder:src/auth` to allow mobile client logins securely.

## 2.2 Success Criteria
- Validate `code_challenge` (SHA-256) and `code_verifier` strings according to RFC 7636.
- Issue secure, HTTP-only, SameSite JWT refresh cookies upon successful token exchange.

---

# 3. CONTEXT
## 3.1 Existing Auth Directory
Existing Auth Code: @Folder:src/auth
JWT Utilities: @File:src/utils/jwt.ts

---

# 4. EXECUTION
## 4.1 Implementation Steps
1. Create PKCE utility helper functions (`crypto.createHash('sha256')`) in `src/auth/pkce.ts`.
2. Implement `/oauth/authorize` route storing `code_challenge` in Redis with 5-minute TTL.
3. Implement `/oauth/token` route verifying `code_verifier` hash against stored challenge.
4. Issue access token JSON and set secure HTTP-only refresh cookie.

## 4.2 Guardrails
- MUST enforce SHA-256 `code_challenge_method` (`S256`).
- MUST NOT allow unhashed `plain` PKCE code challenge methods.
- MUST store authorization codes in Redis with strict expiration times (max 5 mins).

---

# 5. OUTPUT SPECIFICATION
## 5.1 Format
Multi-file code output:
- `src/auth/pkce.ts`
- `src/auth/routes.ts`
- `tests/auth/pkce.test.ts`

Why the Prompt Works

  - Restricts authentication implementation to secure standards (banning
    insecure plain PKCE methods in Section 4.2).
  - Uses @Folder:src/auth context to ensure the new feature connects cleanly to
    existing JWT utilities.

Expected Cursor AI Output

Three complete TypeScript files providing SHA-256 PKCE challenge generation,
Express authorization route handlers, and unit tests verifying token exchanges.

Possible Improvements

Add rate-limiting middleware (express-rate-limit) to the /oauth/token route.

9.11 Performance Optimization: Vectorizing Python Loop Computations

Problem Statement

A data engineer needs to optimize a slow, CPU-bound Python script that processes
financial time-series data using nested for loops.

Complete SPARK Prompt

# 1. ROLE & IDENTITY
## 1.1 Role
Principal Python Performance Engineer specializing in numerical computation vectorization and NumPy/Pandas optimization.

---

# 2. OBJECTIVE
## 2.1 Primary Goal
Refactor the slow financial calculation function in `@File:analytics/indicators.py` to use vectorized `numpy` and `pandas` array operations, targeting a 10x+ execution speedup.

## 2.2 Success Criteria
- Eliminate 100% of explicit Python `for` loops in the calculation body.
- Maintain floating-point numerical equivalence (within `1e-6` tolerance) compared to original output.
- Include a performance benchmark script using `timeit`.

---

# 3. CONTEXT
## 3.1 Target Performance File
Target code: @File:analytics/indicators.py

---

# 4. EXECUTION
## 4.1 Optimization Logic
1. Analyze nested loops in `@File:analytics/indicators.py` calculating moving averages and volatility.
2. Replace iterative loop indexing with vectorized NumPy array broadcasting and `pandas.Series.rolling()` operations.
3. Write a PyTest numerical equivalence test (`np.testing.assert_allclose`) comparing legacy loop outputs with vectorized outputs.
4. Benchmark execution time across 1,000,000 data points.

## 4.2 Guardrails
- MUST NOT alter returned data array shapes or column key names.
- MUST maintain numerical precision tolerance within `1e-6`.

---

# 5. OUTPUT SPECIFICATION
## 5.1 Format
- `analytics/indicators.py` (Vectorized code)
- `tests/test_indicators_perf.py` (Benchmark & Equivalence test)

Why the Prompt Works

  - Defines a clear, measurable success metric (10x speedup, eliminating
    explicit loops) in Section 2.2.
  - Requires numerical equivalence testing (np.testing.assert_allclose) to
    verify that optimization does not introduce mathematical drift.

Expected Cursor AI Output

A refactored, highly optimized Python module using vectorized NumPy operations,
alongside a PyTest benchmark script proving execution speedups while verifying
numerical precision.

Possible Improvements

Evaluate additional speedups using Numba JIT compilation (@njit).

9.12 Security Improvements: Remediating SQL Injection & Hardcoded Secrets

Problem Statement

A security engineer needs Cursor Composer to audit an existing API endpoint file
(@File:routes/user.js) and remediate SQL Injection vulnerabilities and hardcoded
secrets.

Complete SPARK Prompt

# 1. ROLE & IDENTITY
## 1.1 Role
Principal Application Security Auditor specializing in OWASP Top 10 remediation and Node.js secure coding practices.

---

# 2. OBJECTIVE
## 2.1 Primary Goal
Audit and remediate security vulnerabilities in `@File:routes/user.js`, eliminating SQL injection flaws and moving hardcoded JWT secrets to environment variables.

---

# 3. CONTEXT
## 3.1 Target Vulnerable File
Vulnerable source file: @File:routes/user.js

---

# 4. EXECUTION
## 4.1 Remediation Steps
1. Scan `@File:routes/user.js` for unparameterized SQL string concatenations (`"SELECT * FROM users WHERE id = " + req.query.id`).
2. Replace raw SQL strings with parameterized query placeholders (`db.query('SELECT * FROM users WHERE id = $1', [req.query.id])`).
3. Replace hardcoded secret strings (`const SECRET = "mysecret123"`) with `process.env.JWT_SECRET`.
4. Add input sanitization using `express-validator` schemas.

## 4.2 Guardrails
- MUST use parameterized SQL bindings for all database queries.
- MUST NOT allow hardcoded fallbacks if `process.env.JWT_SECRET` is missing; throw a startup error instead.

---

# 5. OUTPUT SPECIFICATION
## 5.1 Format
Refactored file output targeting `routes/user.js`.

Why the Prompt Works

  - Addresses OWASP Top 10 vulnerabilities directly by mandating parameterized
    SQL queries and environment variable usage.
  - Forces a startup error if critical security environment variables are
    missing, preventing insecure execution defaults.

Expected Cursor AI Output

A remediated, secure JavaScript file containing parameterized SQL queries,
express-validator input sanitization, and environment variable secret
references.

Possible Improvements

Run Cursor Composer across the entire @Folder:routes directory to apply security
remediations globally.

10. Common Mistakes

1.  Prompting Composer Without Scope Non-Goals: Allowing Cursor Composer (Cmd+I)
    to modify multi-file codebases without defining Section 2.3 Non-Goals,
    causing it to alter unprompted peripheral files.
2.  Omitting Context Tags (@File, @Folder, @Codebase): Writing prompts in Cursor
    Chat without referencing target files using @ tags, forcing Cursor to guess
    where functions are defined.
3.  Leaving .cursorrules Unconfigured: Operating without a root .cursorrules
    file, causing Cursor to default to generic coding conventions instead of
    your project's specific style guide.
4.  Ignoring Explicit Version Declarations: Omitting framework version numbers
    in Section 3.1, leading Cursor to generate code using deprecated or
    incompatible APIs.
5.  Accepting Code Without Unit Tests: Failing to require unit tests in
    Sections 2.2 and 5.1, making it difficult to verify if generated code
    introduced breaking changes.

11. Tips for Better Results

  - Maintain an Active .cursorrules File: Store global SPARK identity rules
    (Section 1), quality guardrails (Section 4.2), and formatting guidelines
    (Section 5) in a .cursorrules file in every repository.
  - Combine SPARK with Cursor Composer (Cmd+I): Use complete SPARK prompts in
    Composer when executing multi-file feature builds or complex refactoring
    tasks.
  - Use @Folder Tags for Scoped Refactoring: When refactoring a specific module,
    reference @Folder:src/target_module in Section 3 to restrict Cursor's
    indexing scope.
  - Run Step-by-Step Execution Loops: Require Cursor to output an architectural
    plan in Section 4.1 before generating multi-file code changes.

12. Summary

The SPARK Framework turns Cursor AI into a deterministic, enterprise-grade
software engineering tool.

By structuring prompts into Role, Objective, Context, Execution, Output
Specification, Examples, Verification, and Notes—and leveraging Cursor's
@Codebase indexing, .cursorrules files, and Composer multi-file
execution—developers and teams can build, refactor, debug, test, and document
complex software systems with total reliability.

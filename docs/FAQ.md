Frequently Asked Questions (FAQ)

Official Reference Guide for the SPARK Framework (v1.0)

1. Introduction

Welcome to the official Frequently Asked Questions (FAQ) guide for the SPARK
Framework (Specialized Prompt Architecture for Reliable Knowledge).

This document provides answers to common questions regarding SPARK's
architecture, philosophy, installation, template usage, AI platform
compatibility, performance troubleshooting, and open-source contribution
guidelines.

If you are new to the framework, we recommend reviewing Installation.md and
Framework.md alongside this FAQ.

2. General Questions

2.1 What is the SPARK Framework?

SPARK (Specialized Prompt Architecture for Reliable Knowledge) is an
open-source, enterprise-grade prompt engineering standard. It organizes natural
language prompts into eight standardized, modular functional sections to make
prompts deterministic, reproducible, auditable, and maintainable.

2.2 What does SPARK stand for?

SPARK stands for Specialized Prompt Architecture for Reliable Knowledge.

2.3 Why was SPARK created?

Traditional prompting relies on informal, trial-and-error natural language
queries ("chatting with AI"). This causes non-deterministic outputs, schema
violations, conversational fluff, and high maintenance costs. SPARK was created
to treat prompt writing as a formal software engineering discipline.

2.4 Is SPARK a software package, library, or web application?

No. SPARK is an open-source declarative architecture standard consisting of
Markdown specifications (.md), templates, skills, and field guides. It requires
no compilers, software build tools, package managers (npm, pip), or server
hosting.

2.5 Is SPARK free and open source?

Yes. SPARK is 100% free and open source, released under the permissive MIT
License. You may use, modify, and distribute SPARK for personal, academic,
commercial, and enterprise applications without cost or royalty fees.

2.6 Who should use SPARK?

SPARK is designed for software engineers, prompt engineers, AI researchers,
product managers, startup founders, technical writers, marketers, educators, and
students who require consistent, production-grade outputs from Large Language
Models.

2.7 How does SPARK differ from traditional prompt engineering tips?

Traditional prompt engineering offers informal "tricks" (e.g., "be polite",
"take a deep breath", "I will tip you $200"). SPARK provides a structural,
modular system architecture based on context entropy reduction, self-attention
anchoring, explicit guardrails, schema enforcement, and inline self-audit loops.

3. Framework Architecture Questions

3.1 Why does SPARK have eight sections?

SPARK's eight sections mirror the functional layers of software architecture,
isolating specific cognitive tasks so they do not conflict within the model's
context window:

+-----------------------------------------------------------------------------------+
|                        THE 8 SPARK FUNCTIONAL BLOCKS                              |
+-----------------------------------------------------------------------------------+
| 1. Role & Identity       ──> Sets expert persona, cognitive style, & tone rules   |
| 2. Objective             ──> Declares primary goal, success metrics, & non-goals |
| 3. Context               ──> Supplies software stack, domain facts, & audience    |
| 4. Execution             ──> Outlines step-by-step logic, guardrails, & retries  |
| 5. Output Specification  ──> Defines strict schemas, formatting, & preamble bans |
| 6. Examples              ──> Demonstrates input-output mappings (few-shot)       |
| 7. Verification          ──> Embeds pre-output self-audit & correction loops      |
| 8. Notes                 ──> Stores version control metadata & inference params   |
+-----------------------------------------------------------------------------------+

3.2 Are all eight SPARK sections mandatory for every prompt?

No. Sections 1 through 5 constitute the Core Structural Execution Block and
should be included in all production prompts. Sections 6 (Examples), 7
(Verification), and 8 (Notes) are optional for simple tasks, though strongly
recommended for enterprise software pipelines, security audits, and complex data
extraction.

3.3 Which SPARK sections can be omitted for simple tasks?

  - Section 6 (Examples) can be omitted if direct natural language instructions
    in Section 4 are completely unambiguous.
  - Section 8 (Notes) can be omitted for throwaway, single-turn interactive
    queries that do not require version control tracking.

3.4 Can I modify or reorder the SPARK sections?

We strongly recommend maintaining the canonical numeric order (1 through 8).
Transformer attention mechanisms process tokens sequentially from top to bottom;
establishing identity (Section 1) and goal parameters (Section 2) before reading
context (Section 3) and execution steps (Section 4) builds an optimal attention
map.

3.5 Why are guardrails formatted with capitalized MUST and MUST NOT keywords?

Capitalized bold keywords (MUST, MUST NOT) act as visual and semantic anchors in
the LLM's self-attention matrix, significantly increasing the probability that
negative boundaries will be enforced during token generation.

3.6 What is the role of Section 7 (Verification & Refinement)?

Section 7 embeds an inline self-audit checklist directly into the generation
pipeline. Because auto-regressive models generate text in a single forward pass,
Section 7 forces the model to evaluate its output against binary criteria
(YES/NO) and correct errors internally before completing generation.

4. Usage & AI Platform Compatibility Questions

4.1 Which AI models work with SPARK?

SPARK is model-agnostic. It works across all major frontier models and
open-weight models, including OpenAI GPT-5.6 sol, 5.6 terra, Anthropic Claude
Sonnet/Opus 5, Google Gemini 3.1 Pro/3.6 Flash, Meta Llama 4, Mistral, Qwen, and
DeepSeek.

4.2 How do I use SPARK with OpenAI ChatGPT?

Paste complete SPARK prompts directly into the ChatGPT chat interface. For
persistent system persona enforcement, place Section 1 (Role & Identity) and
Section 4.2 (Guardrails) into ChatGPT's Custom Instructions. Refer to
examples/ChatGPT.md for detailed field guidance.

4.3 How do I use SPARK with Anthropic Claude?

Paste SPARK prompts into Claude 3.5 Sonnet or save SPARK system directives
inside Claude Projects. To force Claude to render clean code or documents
without conversational preambles, require output as a standalone Claude Artifact
in Section 5.1. Refer to examples/Claude.md for field guidance.

4.4 How do I use SPARK with Google Gemini & Google AI Studio?

In Google AI Studio, paste Section 1, Section 4.2, and Section 5.2 into the
System Instructions panel. For 100% schema compliance, map Section 5.3 schemas
directly to AI Studio's native response_mime_type="application/json" setting.
Refer to examples/Gemini.md for field guidance.

4.5 How do I use SPARK with Cursor AI Code Editor?

Save default SPARK system rules inside a .cursorrules file placed in your
project root. When executing multi-file refactoring with Cursor Composer
(Cmd+I), paste completed SPARK prompts and scope file access using @Files or
@Folder tags in Section 3. Refer to examples/Cursor.md for field guidance.

4.6 Does SPARK work with local / open-weight LLMs (Ollama, LM Studio, Llama 3)?

Yes. Open-weight models running locally via Ollama, LM Studio, or vLLM respond
exceptionally well to SPARK's structured Markdown headings and explicit
guardrails, which help prevent instruction drift in smaller parameter models
(7B–70B).

4.7 Can SPARK prompts be integrated into software API pipelines?

Yes. SPARK prompts are standard UTF-8 text strings. You can store .spark or .md
prompt templates in your software repository, populate variables
programmatically, and pass them as system or user messages in OpenAI, Anthropic,
or Google API SDK calls.

5. Template Questions

5.1 What templates are included in SPARK?

The templates/ directory includes seven specialized templates:

1.  General.md: Universal fallback template for general tasks.
2.  Coding.md: Software engineering, API design, & refactoring.
3.  Marketing.md: Copywriting, brand strategy, & ad campaigns.
4.  Research.md: Literature reviews & technology trade-off analysis.
5.  Startup.md: MVP scoping, Lean validation, & pitch decks.
6.  Automation.md: AI agents, webhooks, & cron workflows.
7.  Education.md: Lesson plans, analogies, & active quizzes.

5.2 Which template should a beginner start with?

Beginners should start with templates/General.md. It provides the complete
annotated 8-block SPARK architecture alongside a clean copy-and-paste block
suitable for any task.

5.3 How do I choose between General.md and a specialized template?

If your task falls explicitly into software engineering, marketing, research,
startup strategy, automation, or education, use the corresponding specialized
template. For cross-disciplinary or uncategorized tasks, use General.md.

5.4 How do I fill out bracketed placeholders [LIKE_THIS] in templates?

Replace all bracketed text [LIKE_THIS] with your specific project parameters,
data payloads, or constraints. Delete the brackets before submitting the prompt.
Never leave unedited placeholder brackets in production prompts.

5.5 Can I create custom SPARK templates for my organization?

Yes. We encourage organizations to create internal SPARK templates (e.g.,
templates/LegalAudit.md, templates/ClinicalReview.md) tailored to private
business rules and schemas.

6. Repository & Reading Path Questions

6.1 How is the SPARK repository organized?

spark/
├── README.md                  # Quick-start framework overview
├── Framework.md               # Core architectural specification
├── Philosophy.md              # First-principles engineering foundation
├── Best-Practices.md          # 21 operational prompt engineering habits
├── Common-Mistakes.md         # Anti-patterns and troubleshooting
├── templates/                 # 7 reusable domain templates
├── examples/                  # Platform field guides & 50+ real-world prompts
├── skills/                    # Executable system instructions (Claude Skill)
└── docs/                      # Installation guide & FAQ

6.2 What is the recommended reading path for non-technical users?

1.  README.md \rightarrow 2. Installation.md \rightarrow 3. templates/General.md
    \rightarrow 4. examples/Before-After.md

6.3 What is the recommended reading path for developers and AI engineers?

1.  Framework.md \rightarrow 2. Philosophy.md \rightarrow 3. Best-Practices.md
    \rightarrow 4. Common-Mistakes.md \rightarrow 5. Platform-specific guide in
    examples/

7. Troubleshooting & Performance Tuning

7.1 Why is the AI still including conversational preamble text ("Here is your output:")?

Models like ChatGPT and Claude are fine-tuned to be polite assistants. To
eliminate preambles completely:

1.  Explicitly ban preambles in Section 1.3 and Section 5.2:
    MUST NOT include conversational greetings, introductory text ("Here is your
    output:"), or sign-offs. Return the requested payload strictly.
2.  In Claude, mandate output as a standalone Claude Artifact in Section 5.1.
3.  In Gemini, use Google AI Studio System Instructions with
    response_mime_type="application/json".

7.2 Why is the AI ignoring my negative guardrails or boundaries?

  - Cause: Guardrails were written as passive narrative sentences rather than
    explicit boundaries.
  - Fix: Format all guardrails in Section 4.2 using capitalized bold keywords
    (MUST, MUST NOT):
    - MUST NOT introduce third-party package dependencies.

7.3 What should I do if the AI output violates my requested JSON/YAML schema?

1.  Provide a complete, un-truncated schema in Section 5.3 rather than an
    informal description.
2.  In Section 5.2, explicitly ban Markdown code fences if raw JSON is required
    by API parsers.
3.  Include a representative JSON output example in Section 6.1 (Few-shot
    conditioning).
4.  Require a schema check in Section 7.1 (Does output match Section 5.3 schema?
    [YES/NO]).

7.4 How do I prevent the model from generating hallucinated facts or fake citations?

Add explicit citation integrity guardrails to Section 4.2:

MUST NOT fabricate paper titles, authors, DOIs, or statistical metrics. IF an
exact empirical metric is unverified, state explicitly: "Exact citation
unverified; theoretical model indicates..."

7.5 Why is the AI generating code with deprecated or wrong library versions?

  - Cause: Section 3 (Context) omitted exact framework and language versions.
  - Fix: State exact software versions explicitly in Section 3.1 (e.g.,
    Python 3.11, FastAPI 0.104, SQLAlchemy 2.0 asyncpg, React 18.2,
    TypeScript 5.2).

7.6 What should I do if my SPARK prompt hits the model's token length limit?

1.  Remove conversational narrative text from Section 3 Context (filter out raw
    logs or unnecessary source code).
2.  Omit Section 6 (Examples) if direct natural language rules in Section 4 are
    sufficient.
3.  Split multi-stage workflows into separate, chained SPARK prompts executed
    sequentially.

8. Best Practices & Advanced Techniques

8.1 What temperature parameter should I use with SPARK prompts?

  - Temperature 0.0 (Deterministic): Use for coding, API design, database
    schemas, mathematical reasoning, data extraction, and security audits.
  - Temperature 0.2–0.3 (Structured Analysis): Use for research reviews, startup
    strategy, and technical documentation.
  - Temperature 0.5–0.7 (Controlled Creative): Use for marketing copywriting,
    social media positioning, and brainstorming.

8.2 How do I combine XML tags with SPARK Markdown headers?

Claude and Gemini natively understand XML tags. You can nest XML tags within
SPARK sections to isolate data payloads:

# 3. CONTEXT
<environment>
  <language>TypeScript 5.2</language>
  <framework>Next.js 14</framework>
</environment>

<input_codebase>
  [PASTE CODE HERE]
</input_codebase>

8.3 How do I version-control SPARK prompts in Git?

Save SPARK prompts as .spark or .md files in your software repository under a
dedicated /prompts directory. Commit prompt changes via Pull Requests alongside
application code, documenting updates in Section 8 (Notes).

9. Contribution & Community Questions

9.1 How can I contribute to the SPARK Framework?

We welcome open-source contributions! You can contribute by:

  - Submitting Pull Requests to improve documentation, templates, or field
    guides.
  - Adding new domain templates or platform examples.
  - Reporting typos, broken links, or clarity improvements via GitHub Issues.

Review our contribution guidelines in CONTRIBUTING.md before submitting Pull
Requests.

9.2 Can I use SPARK in commercial products, client consulting, or paid courses?

Yes. The MIT License permits unrestricted commercial use, modification, and
distribution. You do not need explicit permission to teach SPARK, incorporate it
into commercial products, or use it in consulting engagements.

10. Future Development & Roadmap

10.1 Will SPARK receive future version releases?

Yes. SPARK is actively maintained. Future updates will introduce expanded
multi-agent orchestration specifications, Model Context Protocol (MCP) prompt
guidelines, and automated prompt evaluation test harnesses.

11. Summary

The SPARK Framework turns natural language interaction with Large Language
Models into a predictable, auditable software engineering discipline.

For further details, explore the complete documentation suite:

  - Architectural Specification: Framework.md
  - Engineering Philosophy: Philosophy.md
  - 21 Best Practices: Best-Practices.md
  - Common Anti-Patterns: Common-Mistakes.md
  - Setup Guide: docs/Installation.md

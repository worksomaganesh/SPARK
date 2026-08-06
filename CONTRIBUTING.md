Contributing to the SPARK Framework

A Guide to Submitting SPARK Prompts, Templates, Specifications, and
Documentation

1. Welcome & Vision

Thank you for your interest in contributing to the SPARK Framework (Specialized
Prompt Architecture for Reliable Knowledge)!

Our mission is to transform natural language interaction with Large Language
Models from informal, non-deterministic "trial-and-error prompting" into a
modular, verifiable, and open-source software engineering discipline.

Whether you are fixing a typo in documentation, adding a production-ready prompt
to our libraries, creating a new domain template, refining an AI platform field
guide, or improving the core specification, your contributions are invaluable to
the global AI engineering community.

2. Code of Conduct

We are committed to fostering a welcoming, respectful, and inclusive community.
By participating in this project, you agree to abide by our community standards:

  - Be Respectful: Treat all contributors, maintainers, and community members
    with professional courtesy, empathy, and respect.
  - Be Constructive: Focus on constructive, evidence-based feedback during code
    and prompt reviews.
  - Be Inclusive: Encourage participation from contributors of all backgrounds,
    skill levels, and disciplines.
  - Focus on Quality: Prioritize technical rigor, clarity, and determinism in
    all submitted prompt artifacts.

3. Ways You Can Contribute

There are many ways to contribute to the SPARK Framework repository, regardless
of whether you are a non-technical writer or a senior AI systems architect:

+-----------------------------------------------------------------------------------+
|                            CONTRIBUTION OPPORTUNITIES                             |
+-----------------------------------------------------------------------------------+
|  1. SUBMIT SPARK PROMPTS   ──> Add tested prompts to our specialized libraries.   |
|  2. CREATE TEMPLATES       ──> Author new domain templates in /templates.         |
|  3. EXPAND FIELD GUIDES    ──> Add real-world platform examples to /examples.     |
|  4. IMPROVE SPECIFICATIONS ──> Refine core specifications & guidelines.           |
|  5. REPORT BUGS & ISSUES   ──> Submit hallucination reports or schema bug issues.|
+-----------------------------------------------------------------------------------+

A. Submitting New SPARK Prompts

Contribute high-quality, fully populated SPARK prompts to our specialized prompt
libraries (prompts/Business/, prompts/Coding/, prompts/Content/,
prompts/Research/, prompts/AI-Agents/).

B. Authoring Domain Templates

Create new reusable domain templates in templates/ (e.g., templates/Legal.md,
templates/Cybersecurity.md, templates/DataScience.md).

C. Refining Field Guides & Platform Examples

Expand our platform field guides in examples/ (ChatGPT.md, Claude.md, Gemini.md,
Cursor.md) with real-world, high-density prompt transformations.

D. Framework & Specification Enhancements

Improve core architectural specifications (SPARK-Specification.md, Framework.md,
Philosophy.md, Best-Practices.md, Common-Mistakes.md).

E. Reporting Issues & Prompt Hallucinations

Open GitHub Issues to report edge-case failures, schema drift, or
non-deterministic behaviors observed in existing prompts.

4. Prompt Quality & Submission Guidelines

To maintain enterprise-grade quality across the repository, all submitted
prompts MUST adhere to strict quality control standards.

4.1 Strict SPARK v1.0 Compliance

Every submitted prompt MUST strictly follow the canonical 8-block SPARK
architecture:

# 1. ROLE & IDENTITY
## 1.1 Role
## 1.2 Cognitive Style
## 1.3 Tone & Voice

---

# 2. OBJECTIVE
## 2.1 Primary Goal
## 2.2 Success Criteria
## 2.3 Non-Goals

---

# 3. CONTEXT
## 3.1 Background & Domain
## 3.2 System & Technical Constraints
## 3.3 Target Audience / Consumer

---

# 4. EXECUTION
## 4.1 Step-by-Step Logic
## 4.2 Guardrails
## 4.3 Fallback & Edge Case Handling

---

# 5. OUTPUT SPECIFICATION
## 5.1 Format & Structure
## 5.2 Syntactical Rules
## 5.3 Schema & Field Definitions

---

# 6. EXAMPLES
## 6.1 Standard Example
## 6.2 Edge-Case Example

---

# 7. VERIFICATION & REFINEMENT
## 7.1 Pre-Output Audit Checklist
## 7.2 Self-Correction Loop

---

# 8. NOTES
## 8.1 Operational Metadata
## 8.2 Model Adaptation Notes

[!IMPORTANT] Prompts that omit core SPARK sections or use informal, unstructured
narrative text will be requested to be refactored before merging.

4.2 Quality Standards & Anti-Hallucination Rules

  - No Unbounded Logic: Every prompt MUST include explicit stopping criteria,
    input validation, and fallback rules in Section 4.3.
  - Capitalized Guardrails: Positive and negative boundaries in Section 4.2 MUST
    use capitalized MUST and MUST NOT syntax.
  - No Buzzword Fluff: Prompts MUST explicitly forbid generic marketing
    buzzwords (revolutionary, seamless, game-changing, next-gen) in Section 4.2.
  - No Unrealistic Claims: Prompts MUST NOT encourage harmful, unethical,
    illegal, or deceptive practices.
  - Deterministic Schemas: All structured data requests MUST supply full, valid
    schemas (JSON Schema, OpenAPI 3.0, YAML, or TypeScript interfaces) in
    Section 5.3.

4.3 Mandatory Multi-Model Testing

Before submitting a prompt, you MUST test it on at least one major frontier LLM
engine:

  - OpenAI ChatGPT (GPT-4o or o1)
  - Anthropic Claude (Claude 3.5 Sonnet)
  - Google Gemini (Gemini 1.5 Pro)
  - Cursor AI Code Editor

Verify that the model output contains zero conversational preamble text,
adheres 100% to the requested schema, and respects all Section 4.2 guardrails.

4.4 File Naming & Directory Conventions

  - File Format: All files MUST be valid CommonMark Markdown (.md).
  - Naming Style: Use kebab-case for file names (e.g., async-fastapi-service.md,
    customer-discovery-script.md).
  - Directory Layout:
      - New Domain Templates → templates/YourTemplate.md
      - New Platform Examples \rightarrow examples/YourPlatform.md
      - New Library Prompts \rightarrow prompts/CategoryName/prompt-name.md

5. Git & GitHub Contribution Workflow

Follow this step-by-step Git workflow to submit your contributions:

+-----------------------------------------------------------------------------------+
|                             GIT CONTRIBUTION WORKFLOW                             |
+-----------------------------------------------------------------------------------+
|  STEP 1: Fork the official SPARK repository on GitHub                            |
|  STEP 2: Clone your fork locally (`git clone`)                                   |
|  STEP 3: Create a feature branch (`git checkout -b feature/my-prompt`)           |
|  STEP 4: Author and test your SPARK prompt or documentation                      |
|  STEP 5: Commit changes using Conventional Commits (`git commit -m "feat: ..."`) |
|  STEP 6: Push branch to your fork (`git push origin feature/my-prompt`)          |
|  STEP 7: Open a Pull Request (PR) against SPARK's `main` branch                   |
+-----------------------------------------------------------------------------------+

Step 1: Fork the Repository

Navigate to https://github.com/worksomaganesh/SPARK and click the Fork button
near the top right corner to create your personal copy of the repository.

Step 2: Clone Your Fork

Open your terminal and clone your fork locally:

git clone https://github.com/YOUR_USERNAME/spark.git
cd spark

Step 3: Create a Feature Branch

Create a descriptive feature branch for your changes:

git checkout -b feature/add-fintech-risk-prompt

Step 4: Author & Test Your Changes

Add your new prompt, template, or documentation update to the appropriate
directory. Test your prompt against an LLM engine to verify output determinism
and schema compliance.

Step 5: Commit Changes

Write clean, concise commit messages following the Conventional Commits
specification:

git add .
git commit -m "feat(prompts): add FinTech risk audit prompt to business library"

Common commit prefixes:

  - feat: Adding a new prompt, template, skill, or specification.
  - fix: Correcting an error, schema bug, or typo in an existing prompt or file.
  - docs: Updating documentation files (README.md, Installation.md, FAQ.md).
  - style: Fixing formatting, Markdown alignment, or whitespace.

Step 6: Push to Your Fork

Push your branch to your remote GitHub fork:

git push origin feature/add-fintech-risk-prompt

Step 7: Open a Pull Request (PR)

Navigate to the original SPARK repository
(https://github.com/worksomaganesh/SPARK) and click Compare & pull request.
Fill out the Pull Request template checklist detailed below.

6. Pull Request (PR) Review Process

6.1 Copy-Pasteable PR Checklist

When opening a Pull Request, copy and paste the following checklist into your PR
description, marking completed items with an x ([x]):

## Pull Request Summary
- **Type of Contribution**: [ ] New Prompt | [ ] New Template | [ ] Documentation Fix | [ ] Framework Spec
- **Target Category/File**: `prompts/Business/fintech-risk-audit.md`

## SPARK v1.0 Quality Control Checklist
- [ ] Prompt follows the official 8-block SPARK architecture (Sections 1 through 8).
- [ ] Section 2.1 contains a single declarative primary goal statement.
- [ ] Section 2.3 lists explicit Non-Goals to prevent scope creep.
- [ ] Section 4.2 Guardrails use capitalized **MUST** and **MUST NOT** keywords.
- [ ] Section 4.2 explicitly bans generic marketing hype words ("revolutionary", "seamless").
- [ ] Section 5.3 contains a complete, non-placeholder schema definition.
- [ ] Section 7.1 contains a binary (YES/NO) pre-output audit checklist.
- [ ] Prompt has been tested on at least one LLM (ChatGPT / Claude / Gemini / Cursor).
- [ ] Markdown formatting renders cleanly without broken syntax or code blocks.
- [ ] File name uses valid `kebab-case.md` naming convention.

6.2 Review Timelines & Merge Criteria

1.  Automated Verification: GitHub Actions will run automated linter checks on
    your PR to verify Markdown formatting and structural heading hierarchies.
2.  Maintainer Review: A SPARK maintainer will review your submission within 48
    to 72 hours.
3.  Feedback & Revisions: If changes are requested, address the feedback in your
    feature branch and push new commits. The PR will update automatically.
4.  Merging: Once approved by at least one core maintainer, your PR will be
    merged into the main branch!

7. Licensing & Contributor Agreement

By submitting a Pull Request to the SPARK Framework repository, you agree that
your contributions will be licensed under the repository's open-source MIT
License.

You confirm that:

  - You are the sole author of the submitted content or have the legal right to
    submit it.
  - The submitted content does not violate any third-party copyrights,
    trademarks, or proprietary trade secrets.
  - The submitted content is free of malicious, harmful, or deceptive
    code/prompt instructions.

8. Questions & Getting Help

If you have questions before contributing or need help structuring a prompt:

  - GitHub Discussions: Join our community discussions at
    https://github.com/worksomaganesh/SPARK/discussions.
  - GitHub Issues: Open an issue for bug reports or feature requests at
    https://github.com/worksomaganesh/SPARK/issues.

Thank you for helping build the world's highest-quality prompt engineering
framework!

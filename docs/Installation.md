Installing and Getting Started with the SPARK Framework

A Complete Guide to Setting Up, Downloading, and Integrating SPARK Across AI
Platforms

1. Introduction

Welcome to the SPARK Framework (Specialized Prompt Architecture for Reliable
Knowledge).

Unlike traditional software tools, web applications, or Python packages, SPARK
is a declarative, open-source prompt engineering standard. It requires no
compilers, build tools, package managers (npm, pip), or runtime servers.

Installing SPARK simply means downloading or cloning the official open-source
repository to your local computer and integrating its structured Markdown
templates, workflow specifications, and skills into your preferred Large
Language Model (LLM) tools—such as ChatGPT, Anthropic Claude, Google Gemini,
Google AI Studio, or Cursor AI.

This guide provides step-by-step instructions for setting up SPARK locally,
understanding the repository layout, and deploying SPARK templates across major
AI platforms in under five minutes.

2. System Requirements

Because the SPARK Framework consists entirely of structured Markdown (.md)
specifications and templates, system requirements are minimal:

| Component            | Minimum Requirement                                | Recommended                                |
| :------------------- | :------------------------------------------------- | :----------------------------------------- |
| **Operating System** | macOS, Windows 10/11, Linux, or ChromeOS           | Any modern OS                              |
| **Text Editor**      | Any basic text editor (Notepad, TextEdit)          | Visual Studio Code, Obsidian, or Cursor AI |
| **Web Browser**      | Any modern browser (Chrome, Firefox, Safari, Edge) | Latest Google Chrome or Brave Browser      |
| **Git (Optional)**   | None (ZIP download available)                      | Git CLI (v2.30+) or GitHub Desktop         |
| **Disk Space**       | \< 10 MB                                           | 50 MB                                      |

[!NOTE] SPARK works entirely offline on your local computer as a reference
library. An internet connection is only required when copying templates into
online AI tools or cloning repository updates.

3. Prerequisites

To get the most out of the SPARK Framework, you should have:

1.  An Account with an AI Provider: Access to an LLM interface such as OpenAI
    ChatGPT, Anthropic Claude, Google Gemini, Google AI Studio, or an AI code
    editor like Cursor.
2.  Basic Markdown Knowledge: Familiarity with basic Markdown syntax (# Headers,
    **bold text**, code blocks) is helpful, though not required.

4. Installation Methods

Choose one of the three installation options below to download SPARK to your
local machine:

+-----------------------------------------------------------------------------------+
|                            CHOOSE YOUR INSTALLATION METHOD                        |
+-----------------------------------------------------------------------------------+
|  OPTION A: Download ZIP Archive     ──> Non-developers / Quickest setup           |
|  OPTION B: Git Clone via CLI        ──> Developers / Recommended for version control|
|  OPTION C: GitHub Desktop           ──> Visual GUI interface                      |
+-----------------------------------------------------------------------------------+

Option A: Download ZIP Archive (No Git Required)

This is the easiest method for non-developers, researchers, marketers, or anyone
who does not use command-line tools.

1.  Open your web browser and navigate to the official SPARK GitHub repository:
    https://github.com/spark-framework/spark
2.  Click the green Code button near the top right of the page.
3.  Select Download ZIP from the dropdown menu.
4.  Once downloaded, locate the spark-main.zip file in your computer's Downloads
    folder.
5.  Extract (unzip) the file:
      - macOS: Double-click spark-main.zip.
      - Windows: Right-click spark-main.zip and select Extract All...
        \rightarrow Extract.
6.  Move the extracted spark-main folder to your preferred working directory
    (e.g., Documents or Desktop).

Option B: Clone via Git CLI (Recommended for Developers)

Cloning via the Git command-line interface (CLI) allows software engineers and
prompt engineers to receive framework updates easily using git pull.

1.  Open your terminal application:
      - macOS / Linux: Open Terminal.
      - Windows: Open Git Bash or PowerShell.
2.  Navigate to the directory where you want to store the SPARK repository:
    cd ~/Documents/Projects
3.  Run the git clone command:
    git clone https://github.com/spark-framework/spark.git
4.  Navigate into the cloned SPARK directory:
    cd spark
5.  Verify the files are present by listing the directory contents:
      - macOS / Linux: ls -la
      - Windows: dir

Option C: Download via GitHub Desktop

If you prefer a graphical user interface (GUI) for version control:

1.  Download and open GitHub Desktop (https://desktop.github.com).
2.  Click File in the top menu bar \rightarrow select Clone Repository....
3.  Select the URL tab.
4.  Enter the repository URL: https://github.com/spark-framework/spark
5.  Choose your local folder path and click Clone.

5. Repository Structure Overview

Once downloaded, open the spark folder in your preferred text editor (e.g., VS
Code, Cursor, or Obsidian). The repository is organized into eight functional
directories:

spark/
├── README.md                  # Framework overview & quick-start guide
├── Framework.md               # Flagship architectural specification
├── Philosophy.md              # First-principles engineering foundation
├── Best-Practices.md          # 21 operational prompt engineering habits
├── Common-Mistakes.md         # Anti-patterns and troubleshooting guide
│
├── templates/                 # Production-ready SPARK prompt templates
│   ├── General.md             # Universal starting template
│   ├── Coding.md              # Software development & code refactoring
│   ├── Marketing.md           # Copywriting, brand strategy, & ads
│   ├── Research.md            # Literature reviews & trade-off analysis
│   ├── Startup.md             # MVP scoping, Lean validation, & pitch decks
│   ├── Automation.md          # AI agents, API webhooks, & cron scripts
│   └── Education.md           # Lesson plans & active learning guides
│
├── examples/                  # Real-world prompt transformation guides
│   ├── ChatGPT.md             # Field guide & 12 examples for OpenAI ChatGPT
│   ├── Claude.md              # Field guide & 12 examples for Anthropic Claude
│   ├── Gemini.md              # Field guide & 13 examples for Google Gemini
│   ├── Cursor.md              # Field guide & 12 examples for Cursor AI
│   └── Before-After.md        # 10 side-by-side prompt transformations
│
├── skills/                    # Executable system instructions & AI skills
│   └── Claude-Skill.md        # System directive for Claude Projects/Skills
│
└── docs/                      # Official framework documentation
    └── Installation.md        # This installation and setup guide

6. First-Time Setup

To verify that your installation is working correctly:

1.  Open the spark repository folder in a text editor (e.g., VS Code or Cursor).
2.  Open templates/General.md.
3.  Locate Section 10: Copy-and-Paste Version.
4.  Copy the raw template block to your clipboard.
5.  Open your preferred AI tool (e.g., ChatGPT, Claude, or Gemini).
6.  Paste the template into the message input box, fill out the placeholder
    brackets [LIKE_THIS], and press Send.
7.  Verify that the AI output adheres strictly to the requested structure
    without conversational preambles.

7. Recommended Reading Order

To build a deep understanding of the SPARK Framework, we recommend reading the
core documentation files in the following order:

+-----------------------------------------------------------------------------------+
|                            RECOMMENDED LEARNING PROGRESSION                       |
+-----------------------------------------------------------------------------------+
|  1. README.md            ──> High-level framework overview & core concepts    |
|  2. docs/Installation.md ──> Setup guide & platform integration (This file)       |
|  3. Framework.md         ──> Deep dive into the 8 SPARK functional blocks        |
|  4. Philosophy.md        ──> First-principles engineering mindset behind SPARK   |
|  5. Best-Practices.md    ──> 21 habits for writing high-performance prompts    |
|  6. Common-Mistakes.md   ──> Anti-patterns to identify and eliminate               |
|  7. templates/           ──> Select a template for your domain                    |
|  8. examples/            ──> Review platform-specific field guides                |
+-----------------------------------------------------------------------------------+

8. How to Use SPARK

Every SPARK prompt follows an 8-block modular structure:

1.  Role & Identity: Sets the expert persona and tone rules.
2.  Objective: Declares the primary goal, success criteria, and non-goals.
3.  Context: Supplies technical dependencies, domain state, and target audience
    bounds.
4.  Execution: Outlines step-by-step logic, capitalized guardrails (MUST / MUST
    NOT), and error handling.
5.  Output Specification: Defines strict formatting schemas and bans
    conversational preambles.
6.  Examples: Demonstrates expected input-output transformations using few-shot
    exemplars.
7.  Verification & Refinement: Embeds an inline pre-output self-audit checklist
    and correction loop.
8.  Notes: Tracks operational metadata and recommended temperature settings
    (0.0).

9. Using Templates

SPARK provides seven pre-built domain templates in the templates/ directory:

/templates
├── General.md      <-- Universal fallback template
├── Coding.md       <-- Software development, APIs, & refactoring
├── Marketing.md    <-- Copywriting, email drips, & ad strategy
├── Research.md     <-- Literature reviews & technology trade-offs
├── Startup.md      <-- MVP scoping, pitch decks, & Lean validation
├── Automation.md   <-- AI agents, webhooks, & cron scripts
└── Education.md    <-- Lesson plans, analogies, & active quizzes

How to Use a Template

1.  Open the desired template file in templates/ (e.g., templates/Coding.md).
2.  Scroll to the bottom section labeled Copy-and-Paste Version.
3.  Copy the raw Markdown text block.
4.  Replace all bracketed placeholders [LIKE_THIS] with your specific project
    details.
5.  Paste the completed prompt into your AI model.

10. Using Examples

The examples/ directory contains real-world prompt transformations demonstrating
how SPARK improves model outputs across different platforms and use cases:

  - examples/ChatGPT.md: 12 complete prompts optimized for OpenAI ChatGPT models
    (GPT-5.6 Sol, 5.6 Terra, 5.6 Luna).
  - examples/Claude.md: 12 complete prompts optimized for Anthropic Claude
    (Claude Sonnet 5, Claude Projects, Artifacts).
  - examples/Gemini.md: 13 complete prompts optimized for Google Gemini 3.1 Pro
    and Google AI Studio (multimodal image/PDF analysis, 2M+ token contexts).
  - examples/Cursor.md: 12 complete software development prompts optimized for
    Cursor AI editor (.cursorrules, Composer).
  - examples/Before-After.md: 10 side-by-side prompt comparisons showing
    informal prompts transformed into SPARK prompts.

Refer to these files whenever you need inspiration or want to see how expert
prompt engineers structure complex requests.

11. Using the Claude Skill

The file skills/Claude-Skill.md contains an executable system directive that
turns Anthropic Claude into an automated SPARK Prompt Architect.

How to Install the Claude Skill

Method A: Inside a Claude Project (Web Interface)

1.  Open Anthropic Claude (https://claude.ai) and navigate to Projects.
2.  Create a new Project or open an existing one.
3.  Click Set Project Instructions.
4.  Open skills/Claude-Skill.md on your computer, scroll down to the Appendix:
    Raw Executable Skill System Directive, and copy the code block.
5.  Paste the directive into the Claude Project Instructions box and save.
6.  Now, whenever you ask Claude to "write a prompt" inside that project, Claude
    will automatically output structured SPARK prompts.

Method B: Local File for Claude Code / CLI (.claude/skills/)

If using local AI developer tools that support the .claude/skills/ directory:

1.  Create a .claude/skills/ folder in your local project repository.
2.  Copy skills/Claude-Skill.md into .claude/skills/spark.md.

12. Deploying SPARK Across AI Platforms

12.1 Deploying in ChatGPT

Method 1: Direct Message Input

Copy your completed SPARK prompt from a template file and paste it directly into
the ChatGPT chat bar (gpt-5.6 Sol or 5.6 Luna).

Method 2: Custom Instructions (Persistent Persona)

1.  In ChatGPT, click your profile icon in the bottom-left corner \rightarrow
    select Custom Instructions.
2.  In the top box (What would you like ChatGPT to know about you?), paste
    Section 1 (Role & Identity) and Section 3 (Context).
3.  In the bottom box (How would you like ChatGPT to respond?), paste
    Section 4.2 (Guardrails) and Section 5.2 (Syntactical Rules / Preamble
    Bans).
4.  Click Save.

12.2 Deploying in Anthropic Claude

Method 1: Claude Artifacts

When requesting code, API specifications, or long reports from Claude
Sonnet 5, ensure Section 5.1 includes this directive:

MUST render the deliverable as a standalone Claude Artifact document. Omit
conversational preambles outside the Artifact window.

Method 2: Claude Projects Knowledge Base

When working with large document sets or codebases:

1.  Upload your codebase files or reference PDFs to the Project Knowledge Base.
2.  Reference the uploaded files in Section 3 (Context) of your prompt using XML
    tags:
    # 3. CONTEXT
    <uploaded_docs>
      [Referencing uploaded files: architecture_spec.pdf]
    </uploaded_docs>

12.3 Deploying in Google Gemini & Google AI Studio

Method 1: Google AI Studio (System Instructions + JSON Mode)

1.  Open Google AI Studio (https://aistudio.google.com).
2.  Select Gemini 3.1 Pro as the target model.
3.  In the left panel, expand System Instructions.
4.  Paste Section 1 (Role & Identity), Section 4.2 (Guardrails), and Section 5.2
    (Preamble Bans) into the System Instructions box.
5.  In the right configuration panel, set Temperature to 0.0.
6.  If requesting structured JSON outputs, set Response MIME Type to
    application/json and paste your Section 5.3 schema into the JSON Schema
    builder.

Method 2: Multimodal Context Inputs

Attach images, architecture diagrams, or PDF scans directly in the prompt input
box and reference them explicitly in Section 3:

# 3. CONTEXT
## 3.1 Visual Payload
[Attached Image: AWS_Architecture_Diagram.png]

12.4 Deploying in Cursor AI Code Editor

Method 1: Global Project Rules (.cursorrules)

Create a .cursorrules file in the root directory of your project repository and
paste your default SPARK system rules:

# .cursorrules (SPARK System Standard)

# 1. ROLE & IDENTITY
You are a Principal Software Engineer specializing in TypeScript 5.2, React 18, and Node.js v20.

# 4. EXECUTION GUARDRAILS
- MUST write 100% strict TypeScript types. Zero `any` or `unknown` types allowed.
- MUST use parameterized SQL queries to prevent SQL injection vulnerabilities.
- MUST NOT modify files outside the user's requested directory scope.
- MUST write unit tests (Jest/Vitest) for all new functional modules.

# 5. OUTPUT SPECIFICATION
- Return code in multi-file Markdown blocks with clear relative file path headers.
- Omit conversational preamble text.

Method 2: Cursor Composer (Cmd+I / Ctrl+I)

Paste completed SPARK prompts directly into Cursor Composer when executing
multi-file refactoring or scaffolding tasks across your codebase. Use @Files or
@Folder tags in Section 3 to scope Cursor's file indexing.

13. Updating SPARK

As the SPARK Framework open-source project evolves, new templates, examples, and
documentation improvements will be released.

Updating via Git CLI

If you installed SPARK using git clone (Option B), navigate to your local spark
folder in your terminal and run:

git pull origin main

This fetches and merges the latest updates into your local repository without
overwriting any custom files you created in separate directories.

Updating via ZIP Archive

If you installed SPARK via ZIP download (Option A), download the fresh
spark-main.zip archive from GitHub and extract it over your existing folder.

14. Troubleshooting

Issue 1: "The AI still includes conversational preamble text ('Here is your prompt:')"

  - Cause: Models like ChatGPT and Claude are fine-tuned to be polite
    assistants.
  - Resolution: Ensure Section 1.3 and Section 5.2 contain an explicit,
    capitalized preamble ban:
    MUST NOT include conversational greetings, introductory text ("Here is your
    requested output:"), or closing sign-offs. Return the requested deliverable
    strictly.

Issue 2: "The AI misses guardrails or generates prohibited features"

  - Cause: Guardrails were written as passive narrative sentences instead of
    capitalized, explicit constraints.
  - Resolution: Format all guardrails in Section 4.2 using capitalized bold text
    (MUST, MUST NOT):
    - MUST NOT introduce third-party package dependencies.

Issue 3: "The AI outputs code using deprecated or wrong library versions"

  - Cause: Section 3 (Context) omitted exact framework version numbers.
  - Resolution: Explicitly state exact runtime versions in Section 3.1 (e.g.,
    Python 3.11, FastAPI 0.104, React 18.2, TypeScript 5.2).

Issue 4: "Cursor Composer modifies unintended files across my project"

  - Cause: Missing Section 2.3 Non-Goals and Section 4.2 file boundary
    guardrails.
  - Resolution: Add explicit non-goals in Section 2.3 restricting modifications
    strictly to target directory paths.

15. Frequently Asked Installation Questions (FAQ)

Q1: Is the SPARK Framework free?

Yes. SPARK is a 100% free, open-source framework licensed under the permissive
MIT License. You can use it for personal, commercial, and enterprise
applications without cost.

Q2: Do I need a paid API key or subscription to use SPARK?

No. SPARK is a structural prompting standard. You can use it with free AI tiers
(e.g., ChatGPT Free, Claude Free, Gemini Free) or paid tiers (ChatGPT Plus,
Claude Pro, Gemini Advanced, Cursor Pro, OpenAI API, Anthropic API).

Q3: Does SPARK send any data to external servers?

No. SPARK runs entirely on your local machine as a set of static Markdown files.
No data is collected, tracked, or transmitted by the SPARK Framework repository.

Q4: Can I customize SPARK templates for my company's private codebase?

Yes. You are encouraged to create custom templates based on SPARK and commit
them to your organization's private GitHub or GitLab repositories.

Q5: What is the difference between templates/ and examples/?

  - templates/: Blank, reusable prompt layouts with bracketed placeholders
    [LIKE_THIS] ready to be filled out for new tasks.
  - examples/: Fully completed, real-world prompts showing how SPARK is applied
    across specific AI platforms (ChatGPT, Claude, Gemini, Cursor) and domains.

Q6: Can I use SPARK with open-weight models like Llama 3 or Mistral?

Yes. SPARK is model-agnostic. Open-weight models running locally via Ollama, LM
Studio, or vLLM respond exceptionally well to SPARK's structured Markdown
headings and explicit guardrails.

16. Summary

Installing the SPARK Framework takes less than five minutes and establishes a
professional prompt engineering workflow across your entire development setup.

By cloning or downloading the repository, learning the 8 core functional blocks,
and deploying SPARK templates into ChatGPT, Claude Projects, Google AI Studio,
or Cursor AI, you eliminate AI non-determinism and transform natural language
interaction into a predictable, auditable software engineering discipline.

Quick Commands Reference

# Clone SPARK Repository
git clone https://github.com/spark-framework/spark.git

# Navigate to SPARK Directory
cd spark

# Pull Latest Framework Updates
git pull origin main

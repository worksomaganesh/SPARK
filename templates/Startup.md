SPARK Startup & Product Strategy Template

Standardized Prompt Architecture for Founder Strategy, Idea Validation, MVP
Scoping, GTM Planning, and Fundraising

1. Introduction

The SPARK Startup Template is a specialized framework designed for startup
founders, product managers, venture strategists, and innovation teams using
Large Language Models (e.g., Claude, ChatGPT, Gemini).

Using AI for startup strategy, market evaluation, and product planning carries
distinct strategic risks:

  - Generic "Cheerleader" Advice: Unconstrained models tend to validate every
    business idea indiscriminately, outputting optimistic praise rather than
    critical, first-principles market analysis.
  - Solution-in-Search-of-a-Problem: Prompts that jump directly to features
    without establishing a validated customer pain point produce bloated,
    unviable product concepts.
  - Ignoring Unit Economics & Constraints: Without explicit operational
    parameters (e.g., team size, runway, target CAC/LTV ratios), AI models
    recommend capital-intensive strategies unsuitable for early-stage ventures.
  - Superficial Business Plans: Generic prompts generate high-level buzzwords
    ("AI-powered ecosystem") that fail to define concrete Ideal Customer
    Profiles (ICPs), competitive defensibility, or Go-To-Market (GTM) execution
    steps.

The SPARK Startup Template eliminates these failure modes by forcing founders to
articulate explicit problem statements, customer personas, unique value
propositions (UVPs), startup stages, resource constraints, and Lean validation
metrics.

2. When to Use This Template

Use the SPARK Startup Template across all phases of the venture lifecycle:

  - Idea Validation & Customer Discovery: Formulating problem hypotheses,
    designing customer interview scripts, identifying target ICPs, and testing
    market feasibility.
  - MVP Scoping & Product Roadmap: Scoping Minimum Viable Products (MVPs),
    defining core feature sets using prioritization frameworks (e.g., MoSCoW),
    and drafting user stories.
  - Business Model & Pricing Strategy: Designing Business Model Canvases,
    analyzing unit economics (LTV, CAC, payback period), and evaluating pricing
    tiers.
  - Go-To-Market (GTM) & Growth Planning: Designing initial customer acquisition
    playbooks, cold outbound strategies, positioning statements, and launch
    checklists.
  - Fundraising & Pitch Preparation: Structuring 10-slide pitch deck narratives,
    formulating investor Q&A objection matrices, and drafting executive
    summaries.

3. When Not to Use This Template

Do not use the SPARK Startup Template for:

  - Direct Software Code Development: Writing functional application code or
    database scripts (use templates/Coding.md instead).
  - Direct Ad Copywriting: Writing character-limited ad copy or social media
    marketing posts (use templates/Marketing.md instead).

4. How to Fill the Template

Authoring a startup strategy prompt using the SPARK architecture follows a
five-phase flow:

+-----------------------------------------------------------------------------------+
|                        STARTUP PROMPT AUTHORING WORKFLOW                          |
+-----------------------------------------------------------------------------------+
|  1. DEFINE PROBLEM & PERSONA ──> State Pain Point, ICP, & Startup Stage (Sec 3)   |
|                                                                                   |
|  2. DECLARE VENTURE TARGET  ──> State Primary Goal & Validation Metrics (Sec 2)   |
|                                                                                   |
|  3. APPLY LEAN METHODOLOGY  ──> Set Scoping Logic & Critical Guardrails (Sec 4)   |
|                                                                                   |
|  4. SPECIFY DELIVERABLE     ──> Define Matrix Layout, Canvas, or Pitch Deck (Sec 5)|
|                                                                                   |
|  5. EMBED FOUNDER AUDIT     ──> Add Fluff Removal & Unit Economics Check (Sec 7)  |
+-----------------------------------------------------------------------------------+

5. Complete Blank Startup SPARK Template

Below is the complete, annotated SPARK Startup Template. Bracketed placeholders
indicate the specific venture parameters required.

# 1. ROLE & IDENTITY
## 1.1 Role
[Define Advisor Persona. Example: "Principal Venture Strategist and YC-Style Startup Advisor specializing in B2B SaaS Product-Market Fit"]

## 1.2 Cognitive Style
- [Strategic Principle 1. Example: "First-Principles Customer-Centric Validation (Lean Startup)"]
- [Strategic Principle 2. Example: "Unsparing Critical Analysis & Capital-Efficient Unit Economics"]

## 1.3 Tone & Voice
Direct, strategic, objective, and analytical. Avoid generic praise, startup hype, or superficial buzzwords. Focus strictly on actionable, evidence-based business guidance.

---

# 2. OBJECTIVE
## 2.1 Primary Goal
[Single declarative statement defining the startup deliverable.]

## 2.2 Success Criteria
- [Validation Target. Example: "Define 5 testable problem hypotheses with explicit pass/fail conversion thresholds"]
- [Resource Bounds. Example: "MVP scope MUST be executable by a 2-engineer team within 6 weeks"]
- [Analytical Depth. Example: "Include a competitive defensibility matrix detailing moats against incumbents"]

## 2.3 Non-Goals
- [Out-of-scope tasks. Example: "Do not write production software code or build live website UI"]
- [Prohibited recommendations. Example: "Do not recommend paid ad acquisition strategies requiring >$10k/mo budget"]

---

# 3. CONTEXT
## 3.1 Venture Profile
- Startup Name: [Startup Name]
- Core Concept: [1-2 sentence description of the proposed solution]
- Stage of Startup: [e.g., Idea Stage / Pre-Seed / Seed / Early Traction / Series A]
- Primary Industry / Domain: [e.g., Developer Tools / HealthTech / B2B SaaS / FinTech]

## 3.2 Problem & Customer Persona
- Target Customer (ICP): [Define exact buyer and user persona, e.g., Heads of Security at 50-200 person tech companies]
- Acute Problem Statement: [What specific, painful, and frequent problem does the customer experience?]
- Current Workaround: [How does the customer solve or endure this problem today without your product?]
- Unique Value Proposition (UVP): [Why is your proposed solution 10x better than existing workarounds?]

## 3.3 Resource Bounds & Constraints
- Team Size & Skills: [e.g., 2 Full-Stack Engineers, 1 Solo Non-Technical Founder]
- Financial Runway / Budget: [e.g., $50,000 bootstrapped / $1.5M Seed round raised]
- Timeline Target: [e.g., Launch MVP in 45 days]

---

# 4. EXECUTION
## 4.1 Execution Logic & Methodology
1. [Deconstruct Problem & Assumptions: Identify core unvalidated hypotheses and risks]
2. [Evaluate Market & Competitors: Analyze current workarounds, incumbents, and defensibility]
3. [Define Actionable Solution / Strategy: Outline Lean execution steps or product specifications]
4. [Establish Validation Experiments: Design low-cost tests to validate demand before building]
5. [Synthesize Operational Plan: Format output into actionable matrices, roadmaps, or pitch structures]

## 4.2 Guardrails & Critical Constraints
- MUST evaluate business viability through the lens of capital efficiency, unit economics (CAC, LTV), and speed to market.
- MUST NOT validate ideas using generic praise; MUST identify top 3 existential risks or failure modes for the business model.
- MUST keep MVP feature recommendations strictly limited to core value delivery (Ruthless Scope Pruning).

## 4.3 Fallback & Risk Mitigation
- IF [High Risk 1: Customer unwillingness to pay], THEN [Outline a cold discovery interview script to test price tolerance before building].

---

# 5. OUTPUT SPECIFICATION
## 5.1 Format & Structure
Structured Strategic Brief formatted in Markdown using the following required sections:
1. Executive Summary & Critical Venture Analysis
2. Problem-Solution Fit Analysis & ICP Definition
3. Core Deliverable (e.g., MVP Roadmap / GTM Playbook / Pitch Deck Narrative)
4. Risk Matrix & Unvalidated Hypotheses
5. Next Actionable Experiments (30-60-90 Day Execution Plan)

## 5.2 Deliverable Schema / Matrix Layout
[Define target table schema, e.g., Feature | User Value | Technical Complexity | MVP Priority (Must/Should/Won't)]

---

# 6. EXAMPLES
## 6.1 Superficial vs. First-Principles Startup Analysis

### Superficial Analysis (Avoid):
"This is a revolutionary AI application with a massive $50 Billion TAM. Every business will want to use this seamless platform."

### First-Principles Analysis (Emulate):
"Targeting a broad $50B TAM introduces customer acquisition inefficiency. Instead, narrow ICP focus to mid-market DevOps teams (100-300 employees) currently wasting >15 hours/week on manual compliance audits. Validate demand by securing 5 paid pilot LOIs ($500/mo) before writing backend integration code."

---

# 7. VERIFICATION & REFINEMENT
## 7.1 Pre-Output Founder Audit Checklist
1. Is the proposed MVP scope realistic given the team size and budget constraints defined in Section 3.3? [YES/NO]
2. Are top existential risks and competitive threats explicitly identified? [YES/NO]
3. Is the plan focused on customer problem validation rather than premature feature scaling? [YES/NO]
4. Are all generic hype terms ('revolutionary', 'game-changing') completely removed? [YES/NO]

## 7.2 Self-Correction Loop
- IF any audit check evaluates to NO, rewrite the analysis internally before rendering final output.

---

# 8. NOTES
## 8.1 Operational Metadata
- Framework Version: SPARK Startup v1.0
- Target Model: [e.g., Claude Fable 5 / GPT-5.6-sol]
- Recommended Parameters: Temperature: 0.2 (Rigorous, realistic strategic reasoning)

6. Explanation of Every SPARK Section for Startup Tasks

6.1 Section 1: Role & Identity

  - Purpose: Configures the model's professional identity as a critical venture
    advisor or product strategist.
  - Startup Application: Adopts strict Lean Startup frameworks (e.g., Y
    Combinator evaluation style) and explicitly forbids superficial praise or
    fluff.

6.2 Section 2: Objective

  - Purpose: Declares the primary business deliverable, testable validation
    targets, and scope non-goals.
  - Startup Application: Bounds the target deliverable (e.g., MVP scoping,
    customer discovery plan) and enforces strict non-goals to prevent premature
    scaling recommendations.

6.3 Section 3: Context

  - Purpose: Captures core venture parameters, problem statements, customer
    personas (ICP), UVPs, stage, and resource constraints.
  - Startup Application: Grounds AI recommendations in real operational
    constraints (runway, team skills, timeline), ensuring strategies are
    executable for early-stage teams.

6.4 Section 4: Execution

  - Purpose: Outlines step-by-step strategic logic, Lean guardrails, risk
    mitigations, and feature pruning rules.
  - Startup Application: Directs execution through problem deconstruction and
    experiment design. Guardrails enforce ruthless MVP scope pruning and unit
    economic checks.

6.5 Section 5: Output Specification

  - Purpose: Governs output layout, Business Model Canvas structures, feature
    prioritization matrices, and pitch schemas.
  - Startup Application: Ensures deliverables are presented in actionable
    formats (e.g., MoSCoW matrices, 30-60-90 day execution roadmaps).

6.6 Section 6: Examples

  - Purpose: Demonstrates the difference between superficial startup hype and
    rigorous, first-principles market analysis.
  - Startup Application: Anchors model output on realistic,
    unit-economics-driven advice.

6.7 Section 7: Verification & Refinement

  - Purpose: Implements a founder audit checklist evaluating resource
    constraints, risk identification, and hype removal.
  - Startup Application: Forces the model to evaluate whether its
    recommendations are realistic for the founder's specific stage and budget.

6.8 Section 8: Notes

  - Purpose: Tracks operational metadata, target LLM engines, and venture prompt
    versioning.
  - Startup Application: Records model parameters (temperature: 0.2 for
    strategic rigor) and maintains prompt version histories.

7. Startup Best Practices

1.  Always Define Resource Bounds First: Never ask for strategic advice without
    stating team size, runway, and timeline targets in Section 3.3. Strategies
    that work for Series B companies fail in pre-seed environments.
2.  Focus on Problems, Not Features: Anchor every prompt on the customer's acute
    pain point and current workaround before discussing product features.
3.  Prune MVP Scope Ruthlessly: Require the AI model to prioritize features
    using strict frameworks (e.g., Must-Have vs. Nice-to-Have) in Section 4.2 to
    accelerate speed-to-market.
4.  Demand Risk Identification: Explicitly instruct the model in Section 4.2 to
    list the top existential risks (e.g., customer acquisition cost, technical
    feasibility, distribution bottlenecks) for every business model.
5.  Design Validation Experiments Before Building: Force the model to outline
    low-cost validation experiments (e.g., smoke tests, landing page conversion
    tests, customer interviews) before committing engineering resources to code.

8. Common Mistakes in AI Startup Prompts

| Mistake                           | Impact on AI Output                                                            | SPARK Remediation                                          |
| :-------------------------------- | :----------------------------------------------------------------------------- | :--------------------------------------------------------- |
| **Omitting Team & Runway Bounds** | Model recommends expensive enterprise sales or paid ad playbooks.              | Define exact budget & team size in **Section 3.3**.        |
| **Jumping Straight to Solution**  | Product scope becomes bloated with features that lack customer demand.         | Mandate Acute Problem & ICP definition in **Section 3.2**. |
| **Accepting Uncritical Praise**   | Model validates weak business ideas without identifying market risks.          | Direct critical YC-style audit in **Section 1.1 & 4.2**.   |
| **Vague Customer Persona**        | Target market is defined broadly ("small businesses"), diluting GTM execution. | Define exact Ideal Customer Profile in **Section 3.2**.    |
| **Premature Feature Scaling**     | MVP recommendations require months of complex engineering.                     | Enforce ruthless scope pruning in **Section 4.2**.         |

9. Example Prompts

Example 1: B2B SaaS Startup Idea Validation & Customer Discovery Plan

Completed SPARK Prompt

# 1. ROLE & IDENTITY
## 1.1 Role
Senior B2B SaaS Venture Strategist and Customer Discovery Expert specializing in early-stage validation (Pre-Seed).

## 1.2 Cognitive Style
- Lean Startup Methodology (Steve Blank / Eric Ries)
- First-Principles Customer Problem Decomposition

## 1.3 Tone & Voice
Direct, analytical, objective, and pragmatic. Avoid startup buzzwords or superficial praise.

---

# 2. OBJECTIVE
## 2.1 Primary Goal
Generate an Idea Validation & Customer Discovery Plan for a proposed B2B SaaS platform (`LogiGuard`) that automates compliance auditing for mid-market logistics companies.

## 2.2 Success Criteria
- Identify top 3 unvalidated business model risks.
- Formulate a 10-question customer discovery interview script designed to test problem severity without pitching the solution.
- Outline 2 low-cost demand validation experiments executable in under 14 days.

## 2.3 Non-Goals
- Do not design software UI wireframes or technical system architecture.
- Do not create financial revenue projections or 5-year valuation models.

---

# 3. CONTEXT
## 3.1 Venture Profile
- Concept: `LogiGuard` - Automated DOT/FMCSA safety compliance and driver document audit software.
- Stage: Idea Stage (Zero code written).
- Industry: Logistics & Supply Chain Fleet Management.

## 3.2 Problem & Customer Persona
- Ideal Customer Profile (ICP): Fleet Safety Directors at mid-sized trucking fleets (50 to 250 trucks).
- Hypothesized Pain Point: Manual driver qualification file audits take 20+ hours/week and result in heavy DOT fines during surprise audits.
- Current Workaround: Paper binders, manual Excel spreadsheets, and physical filing cabinets.

## 3.3 Resource Constraints
- Founder: Single non-technical founder with 8 years of logistics industry experience.
- Budget: $5,000 for validation experiments.
- Timeline: 30 days to validate problem-solution fit before hiring a dev agency.

---

# 4. EXECUTION
## 4.1 Execution Logic
1. Risk Decomposition: Isolate top 3 existential risks (e.g., Willingness to pay, Willingness to adopt new software, Data privacy concerns).
2. Customer Discovery Script: Draft 10 non-leading interview questions focusing on past behavior, actual costs incurred, and current Excel workarounds.
3. Validation Experiments: Design 2 low-cost experiments (e.g., Concierge MVP manual audit service, Landing Page with cold outbound) to measure intent.
4. Go/No-Go Decision Criteria: Define quantitative metrics required to justify moving to MVP development.

## 4.2 Guardrails
- MUST strictly follow The Mom Test principles (no leading questions, no asking "Would you buy this?").
- MUST NOT recommend building software before completing 15 customer discovery interviews.

---

# 5. OUTPUT SPECIFICATION
## 5.1 Structure
Structured Markdown Validation Brief:
1. Risk & Hypothesis Matrix
2. Customer Discovery Interview Script (10 Questions + Evaluation Criteria)
3. Lean Demand Validation Experiments (2 Playbooks)
4. Go/No-Go Conversion Thresholds

---

# 7. VERIFICATION & REFINEMENT
## 7.1 Pre-Output Audit Checklist
1. Are all discovery questions non-leading and focused on past customer behavior? [YES/NO]
2. Are validation experiments executable within the $5,000 budget and 30-day timeline? [YES/NO]

## 7.2 Self-Correction Loop
- IF questions sound like a sales pitch, rewrite them internally to focus on problem discovery before finalizing.

Why It Works

  - Focuses strictly on problem validation before writing code, adhering to Lean
    Startup principles.
  - Uses The Mom Test methodology to create a non-leading customer discovery
    interview script.
  - Sets clear, quantitative Go/No-Go criteria within $5k budget and 30-day
    timeline bounds.

Example 2: Scoping an MVP Feature Roadmap (MoSCoW Method)

Completed SPARK Prompt

# 1. ROLE & IDENTITY
## 1.1 Role
Principal Product Manager specializing in MVP feature scoping and Lean product launches for HealthTech startups.

---

# 2. OBJECTIVE
## 2.1 Primary Goal
Scope the Minimum Viable Product (MVP) feature set and 6-week product roadmap for a HIPAA-compliant physical therapy patient home-exercise tracking app (`FlexiCare`).

## 2.2 Success Criteria
- Categorize features using the MoSCoW Framework (Must-Have, Should-Have, Could-Have, Won't-Have).
- Restrict Must-Have scope to features executable by a 2-engineer team in 6 weeks.
- Include a Markdown Feature Prioritization Matrix detailing technical complexity and user value.

---

# 3. CONTEXT
## 3.1 Venture Profile
- App Concept: `FlexiCare` - Asynchronous video exercise verification app for physical therapy clinics.
- Resource Bounds: 1 Senior Full-Stack Engineer, 1 React Native Engineer, 6-week build timeline.
- Compliance Bounds: Strict HIPAA compliance required for video storage and patient health data (PHI).

---

# 4. EXECUTION
## 4.1 Execution Logic
1. Core Value Path Identification: Map the absolute minimum path required for a patient to record an exercise and a therapist to review it.
2. Feature Pruning (MoSCoW): Move all non-essential features (e.g., social sharing, gamification badges, AI pose detection) to Could-Have/Won't-Have.
3. Architecture Simplification: Leverage managed HIPAA-compliant backend services (e.g., AWS HealthLake, Supabase with HIPAA BAA) to minimize custom backend code.
4. Sprint Execution Roadmap: Map Must-Have features across 3 bi-weekly development sprints.

## 4.2 Guardrails
- MUST prune all features not directly required for core patient-therapist video exchange.
- MUST NOT include complex AI pose estimation in the initial MVP build.

---

# 5. OUTPUT SPECIFICATION
## 5.1 Format
Structured Product Requirements Document (PRD) containing:
- Executive MVP Scope Summary
- MoSCoW Feature Categorization Matrix
- 6-Week Sprint Execution Plan (3 Sprints)

Why It Works

  - Prunes scope ruthlessly by enforcing a strict 6-week build timeline for
    a 2-engineer team.
  - Separates core value features (video upload/review) from complex
    distractions (AI pose estimation).

10. Copy-and-Paste Version

Copy this clean, unannotated block to start authoring startup and product
strategy prompts:

# 1. ROLE & IDENTITY
## 1.1 Role
[STARTUP_ADVISOR_ROLE_TITLE]

## 1.2 Cognitive Style
- [LEAN_STARTUP_PRINCIPLE_1]
- [STRATEGIC_PRINCIPLE_2]

## 1.3 Tone & Voice
Direct, strategic, objective, and analytical. Avoid generic praise, startup hype, or superficial buzzwords.

---

# 2. OBJECTIVE
## 2.1 Primary Goal
[PRIMARY_VENTURE_DELIVERABLE_STATEMENT]

## 2.2 Success Criteria
- [VALIDATION_OR_BUSINESS_TARGET_1]
- [RESOURCE_BOUND_CONSTRAINT_2]
- [DELIVERABLE_DEPTH_TARGET_3]

## 2.3 Non-Goals
- [OUT_OF_SCOPE_TASK_1]
- [PROHIBITED_RECOMMENDATION_2]

---

# 3. CONTEXT
## 3.1 Venture Profile
- Startup Name: [STARTUP_NAME]
- Core Concept: [CORE_CONCEPT]
- Stage of Startup: [STAGE]
- Primary Industry / Domain: [INDUSTRY]

## 3.2 Problem & Customer Persona
- Target Customer (ICP): [IDEAL_CUSTOMER_PROFILE]
- Acute Problem Statement: [CUSTOMER_PAIN_POINT]
- Current Workaround: [CURRENT_WORKAROUND]
- Unique Value Proposition (UVP): [UNIQUE_VALUE_PROPOSITION]

## 3.3 Resource Bounds & Constraints
- Team Size & Skills: [TEAM_SKILLS]
- Financial Runway / Budget: [RUNWAY_BUDGET]
- Timeline Target: [TIMELINE]

---

# 4. EXECUTION
## 4.1 Execution Logic & Methodology
1. [STEP_1_PROBLEM_DECONSTRUCTION]
2. [STEP_2_MARKET_AND_COMPETITOR_EVALUATION]
3. [STEP_3_STRATEGY_SPECIFICATION]
4. [STEP_4_VALIDATION_EXPERIMENTS]
5. [STEP_5_OPERATIONAL_SYNTHESIS]

## 4.2 Guardrails & Critical Constraints
- MUST evaluate viability through capital efficiency, unit economics, and speed to market.
- MUST NOT validate ideas using generic praise; MUST identify top 3 existential business risks.
- MUST keep MVP feature recommendations strictly limited to core value delivery.

## 4.3 Fallback & Risk Mitigation
- IF [HIGH_RISK_SCENARIO] THEN [REMEDIATION_ACTION]

---

# 5. OUTPUT SPECIFICATION
## 5.1 Format & Structure
[FORMAT_SPECIFICATION]

## 5.2 Deliverable Schema / Matrix Layout
[MATRIX_LAYOUT_SCHEMA]

---

# 6. EXAMPLES
## 6.1 Superficial vs. First-Principles Startup Analysis
### Superficial Analysis (Avoid):
[WEAK_HYPERBOLIC_EXAMPLE]

### First-Principles Analysis (Emulate):
[STRONG_FIRST_PRINCIPLES_EXAMPLE]

---

# 7. VERIFICATION & REFINEMENT
## 7.1 Pre-Output Founder Audit Checklist
1. Is proposed scope realistic given team size and budget constraints? [YES/NO]
2. Are top existential risks and competitive threats explicitly identified? [YES/NO]
3. Is plan focused on customer problem validation rather than feature scaling? [YES/NO]
4. Are all generic hype terms completely removed? [YES/NO]

## 7.2 Self-Correction Loop
- IF any audit check evaluates to NO, rewrite analysis internally before rendering final response.

---

# 8. NOTES
## 8.1 Operational Metadata
- Framework Version: SPARK Startup v1.0
- Target Model: [MODEL_ID]
- Recommended Parameters: Temperature: 0.2

11. Summary

The SPARK Startup Template replaces uncritical AI praise with methodology-driven
venture advisory.

By forcing founders and product managers to define explicit customer pain
points, Ideal Customer Profiles, resource bounds, Lean validation experiments,
and unit economics constraints, teams can deploy AI to accelerateProduct-Market
Fit with clarity and capital efficiency.

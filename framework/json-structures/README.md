# JSON Structures for SPARK

**Purpose:** This guide explains when and how to represent a SPARK prompt as JSON, how JSON prompting differs from ordinary English prompting, and how to validate structured prompt data.

JSON is an optional representation for SPARK. The core SPARK framework remains the eight-part prompt architecture documented in [Framework.md](../Framework.md). JSON does not replace those sections, guarantee better model reasoning, or force every AI application to accept JSON input.

## 1. Why Add JSON Structures to SPARK?

SPARK already separates a prompt into Role & Identity, Objective, Context, Execution, Output Specification, Examples, Verification & Refinement, and Notes. A JSON representation can make those parts easier for software to generate, store, inspect, reuse, and validate.

JSON structures are especially useful when:
- A prompt is assembled dynamically by an application.
- Several prompts share the same fields and conventions.
- A workflow needs to validate required prompt components.
- Prompt data is stored, version-controlled, or passed between software components.
- A team wants to transform a structured prompt into Markdown or provider-specific API messages.

For a simple one-off question, natural-language Markdown may be easier. Use JSON when the structure provides a concrete benefit.

## 2. JSON Is a Representation, Not a Prompting Superpower

JSON (JavaScript Object Notation) is a text format for structured data. It uses objects, arrays, strings, numbers, booleans, and null.

A JSON-formatted prompt groups instructions into fields. That can reduce ambiguity and improve maintainability, but **JSON does not inherently make an answer more accurate, intelligent, or reliable than a clear natural-language prompt**.

Output quality still depends on the clarity and completeness of instructions, the model, relevant context, examples, validation, and the application that submits the prompt.

Keep these three cases separate:

| Technique | Purpose |
|---|---|
| JSON-formatted prompt | Organizes input instructions and context |
| Requesting JSON output | Asks the model to return data in JSON format |
| JSON Schema / structured output | Defines or enforces a machine-checkable output shape when supported by the validator or provider |

A JSON input does not automatically make the response JSON. A request for JSON does not alone guarantee valid JSON. Schema conformance also does not guarantee factual correctness.

## 3. Mapping the Eight SPARK Sections to JSON

SPARK's eight sections can be represented as JSON fields. The names below form a practical mapping for this guide; they are not a replacement for the canonical section names in the main framework.

| SPARK section | Suggested JSON field | Typical contents |
|---|---|---|
| 1. Role & Identity | `role_identity` | Role, expertise, tone, communication style |
| 2. Objective | `objective` | Primary goal, success criteria, non-goals |
| 3. Context | `context` | Background, audience, inputs, technical environment |
| 4. Execution | `execution` | Steps, constraints, must-do and must-not-do rules |
| 5. Output Specification | `output_specification` | Format, required sections, schema, length |
| 6. Examples | `examples` | Representative input/output pairs and edge cases |
| 7. Verification & Refinement | `verification` | Checks, validation criteria, uncertainty handling |
| 8. Notes | `notes` | Version, owner, model-specific considerations |

Not every prompt needs every field populated. Keep SPARK's guidance on optional sections, and avoid adding fields that do not help the task.

## 4. Reusable JSON Prompt Template

Use this as a starting point and replace the sample values with task-specific details. It is valid JSON and intentionally uses plain data fields rather than executable instructions.

```json
{
  "spark_version": "1.0",
  "role_identity": {
    "role": "[ROLE OR EXPERTISE]",
    "tone": "[TONE]",
    "communication_style": "[STYLE]"
  },
  "objective": {
    "primary_goal": "[WHAT MUST BE ACHIEVED]",
    "success_criteria": [
      "[MEASURABLE OR CHECKABLE CRITERION]"
    ],
    "non_goals": []
  },
  "context": {
    "background": "[RELEVANT BACKGROUND]",
    "audience": "[INTENDED AUDIENCE]",
    "inputs": {}
  },
  "execution": {
    "steps": [
      "[STEP 1]",
      "[STEP 2]"
    ],
    "must_do": [],
    "must_not_do": [],
    "assumptions": []
  },
  "output_specification": {
    "format": "Markdown",
    "required_sections": [],
    "language": "English",
    "schema": null
  },
  "examples": [],
  "verification": {
    "checks": [
      "Confirm that the response addresses the primary goal.",
      "Check required sections and constraints.",
      "Identify unsupported assumptions or uncertainty."
    ]
  },
  "notes": {
    "template_version": "1.0",
    "model_specific_settings": []
  }
}
```

This template is a data representation of a prompt. An application or user still needs to pass the information to the model in a way the chosen AI platform supports. A host application may convert the JSON into SPARK Markdown or into separate system/user messages.

## 5. Worked Example: Explain REST APIs

### Natural-language version

> Explain REST APIs to a beginner in clear English. Include a definition, a practical example, HTTP methods, common misconceptions, and revision questions. Do not claim that every HTTP API is fully RESTful.

### JSON-structured version

```json
{
  "spark_version": "1.0",
  "role_identity": {
    "role": "Beginner-friendly software engineering tutor",
    "tone": "Clear and patient",
    "communication_style": "Plain English with practical examples"
  },
  "objective": {
    "primary_goal": "Explain REST APIs accurately to a beginner",
    "success_criteria": [
      "Define REST and API",
      "Explain resources, endpoints, and HTTP methods",
      "Include a practical request and response example",
      "Distinguish REST APIs from HTTP APIs generally"
    ],
    "non_goals": [
      "Assume prior backend development experience"
    ]
  },
  "context": {
    "background": "The learner has already studied APIs and HTTP/HTTPS",
    "audience": "Beginner software engineering student",
    "inputs": {}
  },
  "execution": {
    "steps": [
      "Define key terms",
      "Explain a realistic example",
      "Show common HTTP methods",
      "Explain important REST constraints",
      "Finish with revision questions and answers"
    ],
    "must_do": [
      "Use accurate, accessible explanations",
      "Label illustrative endpoints as examples"
    ],
    "must_not_do": [
      "Claim that JSON plus HTTP automatically satisfies all REST constraints"
    ],
    "assumptions": []
  },
  "output_specification": {
    "format": "Markdown",
    "required_sections": [
      "Definition",
      "How it works",
      "HTTP methods",
      "REST constraints",
      "Examples",
      "Revision questions"
    ],
    "language": "English",
    "schema": null
  },
  "examples": [],
  "verification": {
    "checks": [
      "Verify technical distinctions",
      "Check every required section is present",
      "Avoid unsupported claims"
    ]
  },
  "notes": {
    "template_version": "1.0",
    "model_specific_settings": []
  }
}
```

Both versions communicate essentially the same request. The JSON version is easier for software to inspect field by field; the natural-language version is shorter and easy to read. Neither format guarantees a better answer on its own.

## 6. JSON Prompt vs. JSON Output

A common source of confusion is assuming that a JSON prompt makes the AI return JSON.

### JSON prompt input

You send structured instructions such as:

```json
{
  "task": "Classify the feedback",
  "input_text": "The app is useful, but it loads slowly.",
  "desired_output": "JSON"
}
```

This organizes the input, but the model may still return prose unless the output requirements and platform configuration make JSON output explicit.

### JSON response request

You can ask the model to return an object with specific fields:

```json
{
  "sentiment": "mixed",
  "key_issues": ["slow loading"],
  "positive_points": ["useful app"]
}
```

When software depends on the structure, parse the result and validate it. Do not assume that a natural-language instruction alone guarantees conformance.

### Schema-constrained output

Some AI APIs provide a structured-output feature based on a supported JSON Schema. When correctly configured, it can constrain the generated response to the defined structure. Check the chosen provider's current documentation and limitations.

Even schema-valid output may contain false or unsuitable content. Validate meaning, permissions, and business rules separately.

## 7. A Starter JSON Schema for SPARK Prompt Records

The following JSON Schema validates the outer structure of a SPARK prompt record. It checks the presence and types of the eight fields; it does not prove that the instructions are good or that an AI response is correct.

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "title": "SPARK Prompt Record",
  "type": "object",
  "required": [
    "spark_version",
    "role_identity",
    "objective",
    "context",
    "execution",
    "output_specification",
    "examples",
    "verification",
    "notes"
  ],
  "properties": {
    "spark_version": {
      "type": "string"
    },
    "role_identity": {
      "type": "object"
    },
    "objective": {
      "type": "object"
    },
    "context": {
      "type": "object"
    },
    "execution": {
      "type": "object"
    },
    "output_specification": {
      "type": "object"
    },
    "examples": {
      "type": "array"
    },
    "verification": {
      "type": "object"
    },
    "notes": {
      "type": "object"
    }
  },
  "additionalProperties": false
}
```

This is a starter schema, not a complete validator for every nested field. You can expand it to validate nested properties, required subfields, allowed formats, and project-specific rules. If your workflow allows optional sections to be omitted, adapt the schema accordingly.

## 8. Best Practices

1. **Start from the task, not the format.** Decide what information the model needs and what the downstream application expects.
2. **Keep field names consistent.** Use the same field names across templates and tools.
3. **Make constraints explicit.** State what must be included, excluded, and verified.
4. **Keep input data distinct from instructions.** Treat user-supplied text and retrieved content as untrusted data; do not allow them to silently override the intended rules.
5. **Use the smallest useful structure.** Avoid needless nesting and fields that do not affect the task.
6. **Validate JSON before use.** Parse it and check required fields and types.
7. **Validate model output separately.** Structural correctness is not factual correctness.
8. **Keep secrets out of version control.** Never commit API keys, passwords, or access tokens.
9. **Test across target models.** SPARK is intended to be portable, but model behavior and structured-output features differ by provider.
10. **Record changes.** Version important prompt templates and explain changes in commit messages or notes.

## 9. When Should You Use JSON Structures?

| Situation | Recommendation |
|---|---|
| Simple one-off question | Plain English or SPARK Markdown is usually sufficient |
| Long prompt with distinct fields | JSON may improve organization |
| Reusable prompt generator | JSON is useful for storing and editing parameters |
| Automated pipeline | Use JSON where programmatic processing is needed; validate it |
| AI must return a strict data shape | Use a supported structured-output feature or validate the response against a schema |
| Creative brainstorming | Use whichever format communicates the task most clearly |

## 10. Security Considerations

- Do not store credentials or secrets in prompt JSON files.
- Treat externally supplied JSON values as untrusted input.
- Validate values before using them in file paths, database queries, shell commands, or API requests.
- Avoid executing content just because it appears in a field called `instructions`.
- Restrict the capabilities available to any AI agent that consumes a prompt.
- Review side effects before an agent writes files, sends messages, changes repositories, or performs other consequential operations.

## 11. Related SPARK Documentation

- [SPARK Framework Specification](../Framework.md)
- [SPARK Best Practices](../Best-Practices.md)
- [SPARK Common Mistakes](../Common-Mistakes.md)
- [General Prompt Template](../../templates/General.md)
- [Before-and-After Examples](../../examples/Before-After.md)

## Key Takeaway

**JSON structures give SPARK prompts a machine-readable representation.** They are especially useful for reusable templates, programmatic prompt generation, and validation. They do not replace SPARK's eight-part methodology, and they do not automatically outperform clear natural-language prompts or guarantee correct AI output.

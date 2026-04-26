---
name: prompt-optimizer
description: "Use when improving a prompt, rewriting a prompt for better results, generating a prompt from a brief, adapting a prompt for a specific model, diagnosing why a prompt is failing, or producing prompt variants for speed, quality, extraction, reasoning, or creativity. Optimizes rough, under-specified, or inconsistent prompts into stronger prompts with clearer instructions, context, constraints, examples, and output schemas."
---

# Prompt Optimizer

Turn weak prompts into stronger, testable prompts. Default to improving the prompt directly instead of giving abstract prompt-engineering advice.

## Workflow

1. Identify the task type, target outcome, and success criteria.
2. Detect missing pieces: objective, audience, source context, constraints, output format, examples, evaluation criteria, and target model or platform.
3. If a missing detail is mission-critical, ask briefly. Otherwise proceed with explicit assumptions instead of stalling.
4. Rewrite the prompt using the lightest structure that will reliably improve results.
5. Provide variants only when they materially help, such as concise, high-control, creative, extraction, or reasoning-first versions.
6. Include a short explanation of what changed and a lightweight eval checklist.

## Core Optimization Rules

- Make the model's job concrete: task, scope, input, output, and definition of done.
- Put durable behavior and tone guidance near the top. Put task-specific details close to the task.
- Separate instructions, context, examples, and output requirements clearly.
- Specify the output shape whenever parseability matters. Use JSON, tables, labeled sections, or explicit templates as needed.
- Prefer testable constraints over vague adjectives. For example, "use 5 bullets max" beats "be concise."
- Add examples only when they reduce ambiguity, improve style fidelity, or clarify edge cases.
- Ask for visible intermediate artifacts only when they help quality, such as assumptions, a checklist, a scoring rubric, or a brief plan. Do not ask for hidden chain-of-thought.
- Remove repetition, conflicting instructions, and unnecessary persona fluff.
- Match the prompt style to the task:
  - extraction or classification: strict schema, labels, edge cases, unknown handling
  - generation or rewriting: audience, tone, must-include points, structure, length
  - analysis or reasoning: evidence standard, allowed assumptions, decision criteria, failure handling
- Treat prompting as an iterative system. If the user provides failures, examples, or eval results, use them.

## Model-Aware Adaptation

### OpenAI-style prompts

- When the environment supports system and user messages, keep durable behavior in the system message and task-specific instructions in the user message.
- For structured outputs, define keys, types, enums, and invalid-case behavior clearly.
- Keep few-shot examples compact and consistent.

### Claude-style prompts

- Use XML tags when prompts contain multiple blocks such as instructions, context, examples, and formatting rules.
- Be explicit about level of thoroughness, tradeoffs, and what to do when the input is incomplete.
- Keep the structure easy to scan and edit.

### Generic or cross-model prompts

- Use plain labeled sections when no target model is specified.
- Avoid vendor-specific syntax unless the user names the target model or platform.
- Prefer robust plain language over clever phrasing.

## Prompt Patterns

### 1. Minimal upgrade

Use when the original prompt is short and mostly salvageable.

```text
Task:
Context:
Constraints:
Output format:
Quality bar:
```

### 2. Structured operator prompt

Use for prompts with multiple components, especially for Claude-style workflows.

```xml
<goal>...</goal>
<context>...</context>
<input>...</input>
<constraints>...</constraints>
<output_format>...</output_format>
<quality_checks>...</quality_checks>
```

### 3. Extraction or classification prompt

Always define the schema, labels, edge cases, and what to do when evidence is missing or ambiguous.

### 4. Analysis or reasoning prompt

State the decision to make, the evidence standard, constraints, and the expected output format. Prefer visible summaries, checklists, or decision tables over hidden reasoning requests.

### 5. Writing or transformation prompt

Specify audience, tone, must-include points, must-avoid points, target structure, length, and optional examples.

## Default Response Format

When optimizing a prompt, use this output unless the user asks for something else.

### Optimized prompt

Return the improved prompt first, with clean formatting and no extra commentary inside the prompt unless the prompt itself calls for it.

### Why this is better

Briefly explain the most important improvements, such as clarified objective, stronger output schema, better constraints, or improved context separation.

### Assumptions

List any assumptions made because the user did not provide enough detail.

### Variants

Only include variants when they are useful. Good defaults are:
- concise version
- high-control version
- creative version

### Quick eval

Provide 3 to 5 test cases or checks that the user can use to compare the original and optimized prompts.

## Failure Diagnosis

When the user asks why a prompt is underperforming, look for these issues first:

- ambiguous task or audience
- missing context or missing source material
- weak or missing output specification
- conflicting instructions
- prompt bloat or repeated constraints
- no examples where style or labels are hard to infer
- no eval loop or no comparison cases

## Working Style

- If the user gives a rough idea instead of a draft prompt, build a fresh prompt from scratch.
- If the user names a target model, adapt the structure accordingly.
- If the user gives examples of bad outputs, use them as optimization fuel.
- If the task is simple, keep the optimized prompt short. Do not overengineer.
- If the task is high-stakes, increase specificity, validation steps, and failure handling.

## References

Use these bundled references when needed:

- `references/best-practices.md` for consolidated research-backed rules
- `references/prompt-templates.md` for reusable prompt skeletons
- `references/eval-checklist.md` for lightweight prompt testing and regression checks

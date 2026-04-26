# Best Practices

This reference consolidates recurring prompt-engineering guidance that appears across official OpenAI, Anthropic, and Google prompt guides.

## Cross-vendor patterns that consistently help

### 1. Be explicit

Say exactly what the model should do, for whom, and what a good answer looks like. Specific instructions outperform vague requests.

### 2. Add the missing context

Include the relevant background, source material, constraints, definitions, and decision criteria the model would otherwise have to guess.

### 3. Specify output format

If the output must be parseable or consistent, define the exact structure. Examples: valid JSON, markdown table, bullet list, labeled sections, or a fixed template.

### 4. Use examples strategically

Few-shot examples help when style, labels, or edge-case handling are hard to infer. Keep examples short, representative, and internally consistent.

### 5. Separate prompt components clearly

Distinguish instructions, context, examples, and formatting requirements. For Claude-style prompts, XML tags are especially useful when multiple blocks might get mixed together.

### 6. Prefer testable constraints

Concrete constraints create better behavior than soft adjectives. Length limits, required sections, citation rules, forbidden content, schema requirements, and pass-fail checks are all stronger than saying "make it good."

### 7. Match the prompt to the task

Use different prompt shapes for extraction, classification, writing, analysis, coding, and decision support. There is no single universal perfect prompt.

### 8. Iterate with evals

Prompting improves fastest when prompts are tested against examples, bad outputs, and edge cases. Compare variants instead of guessing.

### 9. Keep prompts as simple as the job allows

Longer prompts are not automatically better. Extra detail should earn its keep by removing ambiguity or controlling important behavior.

### 10. Re-check prompts when models change

Different model families and snapshots can respond differently. Re-run evals when switching models or major prompt versions.

## Useful heuristics for optimization

- If the output is too generic, add audience, stakes, and a stronger quality bar.
- If the output is inconsistent, tighten the schema and examples.
- If the model ignores a requirement, move that requirement earlier and make it testable.
- If the model overexplains, define target length and structure.
- If the prompt feels bloated, remove duplicate instructions and low-value roleplay.

## Common anti-patterns

- Asking for everything at once with no prioritization
- Mixing input data with instructions in a confusing way
- Using contradictory constraints
- Demanding hidden reasoning instead of asking for a visible summary, checklist, or decision table
- Overfitting to one example and forgetting edge cases
- Treating one successful output as proof the prompt is robust

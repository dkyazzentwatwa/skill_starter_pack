# Prompt Templates

## Universal task template

```text
You are helping with [task].

Goal:
[what success looks like]

Context:
[relevant background, source material, audience, constraints]

Instructions:
1. [step or requirement]
2. [step or requirement]
3. [step or requirement]

Output format:
[exact structure]

Quality bar:
- [criterion]
- [criterion]
- [criterion]
```

## Claude-style XML template

```xml
<goal>...</goal>
<context>...</context>
<input>...</input>
<constraints>
- ...
- ...
</constraints>
<output_format>
...
</output_format>
<quality_checks>
- ...
- ...
</quality_checks>
```

## JSON extraction template

```text
Extract information from the input below.

Return valid JSON with this schema:
{
  "field_1": "string",
  "field_2": ["string"],
  "confidence": "high | medium | low",
  "notes": "string"
}

Rules:
- If a value is missing, use null.
- Do not invent facts.
- Base every field on the provided input only.
```

## Rewrite template

```text
Rewrite the source text for [audience].

Keep:
- [must-keep point]
- [must-keep point]

Avoid:
- [must-avoid item]
- [must-avoid item]

Target style:
- tone: [tone]
- length: [length]
- structure: [structure]

Output only the rewritten text.
```

## Decision-support template

```text
Evaluate the options below and recommend the best choice.

Decision goal:
...

Options:
...

Decision criteria:
1. ...
2. ...
3. ...

Constraints:
...

Return:
1. a comparison table
2. the recommended option
3. the main risks and tradeoffs
4. any missing information that would change the recommendation
```

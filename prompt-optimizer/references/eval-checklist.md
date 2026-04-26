# Eval Checklist

Use this reference when the user wants to know whether an optimized prompt is actually better.

## Lightweight prompt-eval loop

1. Collect 3 to 10 representative test cases.
2. Include at least one easy case, one realistic case, and one edge case.
3. Run the original prompt and the optimized prompt on the same cases.
4. Compare outputs using a small scorecard.
5. Keep the better version and note any regressions.

## Simple scorecard

Score each output on these dimensions:

- instruction following
- factual grounding
- format compliance
- completeness
- concision
- tone or style fit
- error handling under ambiguity

## Good regression checks

- Does the model still handle missing data correctly?
- Does the output remain parseable?
- Did the prompt become slower or much more verbose than needed?
- Did the new wording accidentally remove an important requirement?
- Does the prompt still work on edge cases, not just the happy path?

## When to generate variants

Create variants when the task has an obvious tradeoff, such as:

- speed versus quality
- creativity versus control
- terse versus explanatory
- broad exploration versus strict extraction

## Rule of thumb

A prompt is better only if it improves results across multiple examples, not because it looks more sophisticated.

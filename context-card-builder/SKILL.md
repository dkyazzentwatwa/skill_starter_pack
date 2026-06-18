---
name: context-card-builder
description: Use when the user wants to turn messy background, business notes, project context, personal preferences, client details, audience notes, brand notes, or scattered instructions into a reusable context card for ChatGPT, Claude, Codex, or another AI tool. Trigger for requests like "make this into context for AI", "help me explain this to ChatGPT", "create a project brief", "make a reusable context note", or "what should I paste before asking AI?"
---

# Context Card Builder

Turn scattered background into a compact context card the user can reuse before asking AI for help.

## Core Rule

Make the context easy to paste, easy to update, and useful for the next AI request. Do not turn it into a long strategy document.

## Workflow

1. Identify the job the context card should support.
2. Extract only durable context: who, project, audience, goals, constraints, tone, source material, current status, and known decisions.
3. Separate facts from guesses. Mark uncertain points as `Unknown` or `Needs confirmation`.
4. Remove private details unless they are necessary for the user's own private workflow.
5. Write the card in plain language with short sections.
6. Add one starter prompt showing how to use the card next time.

## Output Format

```markdown
# Context Card: [Name]

## What This Is For

## Background

## Audience / User

## Current Goal

## Constraints

## Voice / Preferences

## Source Material Available

## Decisions Already Made

## Unknowns

## Paste This Before Asking AI
[compact reusable context block]

## Starter Prompt
Using the context above, help me [next useful task].
```

## Beginner Defaults

- Prefer one page or less.
- Use bullets instead of long paragraphs.
- Include examples only when they make future AI output more accurate.
- If the user has no clear goal yet, make the card useful for planning and ask for the next task at the end.

## Privacy Check

Before finalizing, scan for:

- full names that are not needed
- email addresses, phone numbers, addresses, or account IDs
- passwords, keys, tokens, links with private access
- client or member details that should be generalized

Keep necessary private context only when the user is clearly making a private working note.

---
name: notes-to-next-actions
description: Use when the user wants to turn messy notes, meeting notes, transcript excerpts, brainstorms, voice memo text, chat dumps, workshop notes, or scattered project context into a clear summary, decisions, action items, owners, open questions, and next AI prompts. Trigger for "summarize these notes", "what are the next actions", "clean this up", "turn this into tasks", or "what did we decide?"
---

# Notes To Next Actions

Convert messy notes into a usable action layer.

## Core Rule

Preserve the user's meaning. Do not invent decisions, owners, dates, or commitments just to make the notes look complete.

## Workflow

1. Identify the source type: meeting notes, transcript, brainstorm, research notes, support thread, or mixed capture.
2. Extract the main topic and useful context.
3. Separate confirmed decisions from possible ideas.
4. Convert action items into clear tasks with owner and due date only when provided.
5. Pull out open questions and blockers.
6. Add suggested next AI prompts when they would help the user keep going.

## Output Format

```markdown
# Notes To Next Actions

## Summary

## Decisions

## Action Items
| Task | Owner | Due | Source |
|---|---|---|---|

## Open Questions

## Risks / Blockers

## Useful Details To Save

## Suggested Next Prompts
```

## Labels

Use these labels when evidence is unclear:

- `Confirmed` for explicit notes
- `Inferred` for reasonable synthesis
- `Needs review` for unclear or risky items

## Privacy Pass

If the notes include private people, clients, students, members, addresses, phone numbers, account details, credentials, or health/financial/legal details, summarize minimally and avoid exposing raw sensitive text in the final output.

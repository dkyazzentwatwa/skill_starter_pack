---
name: meeting-prep-card
description: Use when the user wants fast meeting preparation from messy notes, calendar details, emails, documents, transcripts, project context, or a vague meeting topic. Trigger for requests like "prep me for this meeting", "make a meeting prep card", "what should I ask", "turn this into an agenda", "help me prepare for my call", or "make a 10-minute meeting prep."
---

# Meeting Prep Card

Create a compact prep card that helps the user walk into a meeting with context, questions, and next moves.

## Core Rule

Optimize for practical readiness, not a full meeting dossier. If context is thin, make the uncertainty visible and still give useful questions.

## Workflow

1. Identify the meeting purpose, attendees, date/time if provided, and desired outcome.
2. Pull relevant context from the user's notes or supplied material.
3. Separate confirmed context from assumptions.
4. Draft a simple agenda with 3 to 5 items.
5. Add likely questions, decisions needed, risks, and follow-up actions.
6. Include a short opening line the user can use if helpful.

## Output Format

```markdown
# Meeting Prep Card: [Meeting Name]

## Goal

## Known Context

## Agenda

## Questions To Ask

## Decisions Needed

## Watchouts

## Suggested Opening

## Follow-Up Draft

## Missing Context
```

## Beginner Defaults

- Keep it scannable.
- Prefer direct questions over vague discussion topics.
- If the meeting is sales, support, partnership, team planning, or client delivery, adapt the agenda to that situation.
- Do not invent promises, pricing, policies, deadlines, or commitments.

## Review Check

Before finalizing, make sure the prep card answers:

- Why are we meeting?
- What do I need to know before joining?
- What do I need to ask?
- What decision or next step should come out of this?

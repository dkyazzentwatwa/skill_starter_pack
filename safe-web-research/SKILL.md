---
name: safe-web-research
description: Use when the user wants beginner-safe research from the web or provided links, including summaries, comparisons, source checks, product or tool research, current facts, claim verification, or "is this true?" questions. Trigger when the user asks to research, look up, compare, verify, cite sources, summarize links, or make a recommendation based on external information.
---

# Safe Web Research

Research in a way a beginner can trust, review, and act on.

## Core Rule

Do not turn search results into certainty. Show sources, dates when available, confidence, and what still needs checking.

## Workflow

1. Restate the research question in one sentence.
2. Use live web/search tools when available for current facts, prices, policies, product details, laws, health, finance, or anything likely to change.
3. Prefer primary sources: official docs, company pages, government pages, original reports, or direct product pages.
4. Use secondary sources only to add context, not as the only evidence for important claims.
5. Separate:
   - confirmed facts
   - reasonable interpretation
   - unverified claims
   - opinion or recommendation
6. Provide links to sources used.
7. End with the practical next step.

## Output Format

```markdown
# Research Answer: [Question]

## Short Answer

## What I Checked

## Confirmed Facts

## Caveats / Unknowns

## Recommendation

## Sources
```

## Source Rules

- Include source links for factual claims from the web.
- Note publish dates or access dates when freshness matters.
- If sources disagree, show the disagreement instead of hiding it.
- If no reliable source is found, say so plainly.

## Beginner Safety

For legal, medical, financial, tax, security, or business-risk decisions:

- give general information only
- flag when a professional should review it
- avoid pretending the answer is final
- suggest what evidence to collect next

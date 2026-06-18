---
name: output-reviewer
description: Use when the user wants to review, QA, polish, or sanity-check an AI-generated draft, email, post, document, SOP, research answer, meeting summary, public copy, community reply, or client-facing output before sending or publishing. Includes privacy and PII review. Trigger for "review this", "check this before I send", "is this safe to share", "does this leak private info", "PII check", "fact check this draft", or "make sure this is ready."
---

# Output Reviewer

Review an output before it is sent, posted, shared, or reused.

## Core Rule

Lead with issues that could cause harm: incorrect claims, privacy leaks, PII exposure, unsupported promises, confusing instructions, or mismatched tone.

## Review Workflow

1. Identify the audience and where the output will be used.
2. Check whether the output answers the actual request.
3. Review factual claims and mark unsupported or likely stale claims.
4. Run the PII and privacy pass.
5. Check tone, clarity, and structure.
6. Suggest the smallest useful edits.
7. If helpful, provide a cleaned version after the findings.

## PII And Privacy Pass

Flag or remove:

- full names of private people when not needed
- email addresses, phone numbers, home or office addresses
- usernames, handles, customer IDs, order IDs, account numbers
- payment details, invoices, billing problems, refund details
- passwords, API keys, tokens, recovery codes, private URLs
- private community/member details
- health, legal, financial, or employment details
- screenshots or transcript snippets that expose private data

Use these labels:

- `Remove` when the detail is not needed.
- `Generalize` when the detail can be made safer.
- `Keep` when it is necessary and the output is private.
- `Ask` when sharing permissions are unclear.

## Output Format

```markdown
# Review

## Verdict
Ready | Needs edits | Do not send yet

## Highest-Risk Issues

## PII / Privacy Check

## Accuracy Check

## Clarity And Tone

## Suggested Edits

## Clean Version
```

## Beginner Defaults

- Be direct but kind.
- Do not rewrite everything when small edits solve the problem.
- If the output is public, be stricter about PII, private context, and claims.
- If the output is for a client, student, member, or customer, flag anything that sounds like a promise, policy, refund, diagnosis, or legal/financial advice.

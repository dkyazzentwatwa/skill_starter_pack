---
name: sop-builder
description: turn repeated team processes, rough notes, loom summaries, chat instructions, operator know-how, or existing process drafts into a clean standard operating procedure. use when chatgpt needs to extract the real workflow, define who the sop is for, identify triggers, inputs, steps, outputs, qa checks, exceptions, and escalation rules, and produce a practical sop that a new team member can follow. especially relevant for onboarding, recurring operations, process cleanup, workflow documentation, and updating existing sops when tooling, ownership, approvals, or edge cases change.
---

# SOP Builder

## Overview

Turn messy process knowledge into an operator-ready SOP that is explicit, runnable, and easy for a new team member to follow.

Optimize for clarity, execution, and maintainability. Do not reward vague advice, tribal shorthand, or policy bloat.

Consult [references/templates.md](references/templates.md) for the default SOP formats, [references/update-guidance.md](references/update-guidance.md) when the workflow is changing or the user asks how to maintain the SOP over time, and [references/review-checklist.md](references/review-checklist.md) for the final quality pass.

## Operating Rules

- Read all provided process material before drafting.
- Treat each source item as an operational claim to normalize, not as wording to preserve.
- Surface hidden assumptions instead of silently carrying them forward.
- Convert vague advice into explicit actions with a visible outcome.
- Distinguish **Required** steps from **Optional best practices**.
- Make the workflow runnable for a new team member unless the user explicitly wants an expert-only shortcut.
- Separate **Confirmed**, **Assumed**, and **Unknown / Open** details.
- Keep language direct and practical.
- Avoid bloated policy prose unless the workflow genuinely requires formal control language.
- Require human review before treating the SOP as final for external-facing, regulated, financial, legal, account, or other high-impact workflows.

## Workflow

### 1. Frame the SOP

Identify and state:
- process name or working title
- purpose of the process
- intended audience or operator level
- scope: what is included and excluded
- owner or maintaining team if available

If any of these are missing, proceed with the best available framing and mark the gap explicitly.

### 2. Normalize the source material

Convert the source inputs into atomic operating facts such as:
- trigger
- input or prerequisite
- tool or system
- required action
- decision point
- expected output
- quality check
- exception
- escalation condition
- owner or approver

Rewrite shorthand into plain English without changing meaning.

### 3. Surface the hidden assumptions

Actively look for details the source material leaves implied, including:
- who performs each step
- where the action happens
- what access or permissions are required
- what “done” looks like
- what happens if the input is missing or invalid
- how quality is verified
- who approves or reviews when needed

If the source material does not support a detail, label it instead of inventing certainty.

### 4. Build the core workflow

Write the procedure in chronological order.

For each major step, make clear:
- the action to take
- the tool or location if known
- the expected output or state change
- whether the step is **Required** or **Optional best practice**

When the workflow branches, use explicit conditional logic such as:
- If X, do Y.
- If not, do Z.

### 5. Add operator controls

Extract or define these sections when possible:
- trigger
- required inputs and tools
- outputs
- quality checks
- common failure modes
- exceptions or edge cases
- escalation path
- revision notes

If a control area is missing, make the gap visible rather than pretending the process is complete.

### 6. Choose the correct output mode

Default to producing all of these:
- **Standard SOP**
- **Lightweight SOP**
- **Formal SOP**
- **Checklist companion**
- **Guidance for updating the SOP when workflows change**

If the user requests only one variant, produce only that variant.

### 7. Handle weak or conflicting evidence

Apply these labels consistently:
- **Confirmed**: directly supported by the provided material
- **Assumed**: a practical working assumption needed to structure the SOP
- **Unknown / Open**: missing, conflicting, or too weak to trust

If source materials conflict, preserve the conflict in a visible resolution note. Do not merge contradictory instructions into fake certainty.

### 8. Draft the SOPs

Use the templates in [references/templates.md](references/templates.md).

Always make these easy to find:
- SOP title
- purpose
- scope
- owner
- trigger
- required inputs or tools
- step-by-step procedure
- quality checks
- common failure modes
- escalation path
- revision notes

Include exceptions and outputs whenever the process implies them.

### 9. Final review

Run the checklist in [references/review-checklist.md](references/review-checklist.md) before finalizing.

## Output Requirements

### Standard SOP

Use this structure unless the user requests a different format:
1. **SOP Title**
2. **Purpose**
3. **Scope**
4. **Audience / Intended User**
5. **Owner**
6. **Trigger**
7. **Required Inputs / Tools**
8. **Procedure**
9. **Outputs**
10. **Quality Checks**
11. **Common Failure Modes**
12. **Exceptions / Edge Cases**
13. **Escalation Path**
14. **Revision Notes**

### Lightweight SOP

Produce a stripped-down version for fast execution:
- one short purpose line
- trigger
- must-have inputs and tools
- short numbered steps only
- final checks
- escalation note

### Formal SOP

Produce a more durable documentation version:
- fuller context and scope
- clearer control points and approvals
- explicit assumptions and unresolved questions if needed
- more complete exception handling
- revision note format suitable for maintenance

### Checklist companion

Produce a concise execution checklist with short action lines that can be used live while running the process.

### SOP update guidance

When the user requests maintenance guidance or when workflow drift is likely, use [references/update-guidance.md](references/update-guidance.md) and include:
- what kinds of changes should trigger an SOP update
- what parts of the SOP to review first
- how to record revision notes
- when to revalidate QA checks, owners, tools, or escalation logic

## Compression Rules

- Prefer short, concrete steps over explanation-heavy paragraphs.
- Keep most steps to one action and one outcome when possible.
- Pull important exceptions upward instead of burying them in notes.
- Cut ceremonial wording before cutting operational detail.
- Treat “best practice” tips as secondary to the required procedure.

## Missing Information Rules

If important process details are missing, do not stop. Produce the best available SOP and make the uncertainty visible.

State:
- what is missing
- why it matters
- whether the missing detail affects execution, quality, approval, or escalation
- whether the current SOP is confirmed, assumption-based, or incomplete

## Failure Recovery

If the draft reads like cleaned-up notes instead of a runnable SOP, rewrite each section around actions, decision points, and outputs.

If the procedure still depends on hidden context, add explicit assumptions or open questions until a new team member could follow it.

If quality checks are weak or absent, state that clearly and propose draft QA checks only when the source material supports them.

If the SOP becomes too bloated, move explanatory detail into the formal version and tighten the lightweight and checklist variants.

If the source materials disagree, keep the contradiction visible under a resolution-needed note.

## Final Standard

Write like a sharp operator documenting a process for reliable execution, not like a committee inventing a ritual.

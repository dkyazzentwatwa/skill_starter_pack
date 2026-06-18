---
name: workflow-to-skill
description: Use when the user has completed one useful AI workflow and wants to make it repeatable as a skill, checklist, SOP, reusable prompt, or "next time do this" workflow. Trigger for requests like "turn this into a skill", "make this repeatable", "skillify this", "make a checklist from what we just did", "create a reusable workflow", or "how do I ask ChatGPT/Claude/Codex to do this next time?"
---

# Workflow To Skill

Turn one successful workflow into a reusable skill or checklist for next time.

## Core Rule

Only skillify a workflow that has a real repeatable pattern. If the material is just an idea, opinion, or one-time answer, make a checklist or prompt instead.

## Workflow

1. Identify the completed workflow: starting input, desired output, tools used, key decisions, and final proof.
2. Extract the repeatable shape, not every one-off detail.
3. Name the trigger: what a future user would say when this skill should be used.
4. Define inputs needed before the workflow can run.
5. Write the steps in order with review checks and stop conditions.
6. Choose the lightest reusable form:
   - prompt when the process is simple
   - checklist when a human should drive it
   - SOP when a team member should follow it
   - skill when an AI assistant should run it repeatedly
7. Include a beginner-friendly example prompt.

## Output Format

```markdown
# [Skill or Checklist Name]

## Use When

## Inputs Needed

## Workflow
1.
2.
3.

## Review Checks

## Safety Rules

## Stop And Ask If

## Example Prompt

## Successful Output
```

## Skill Folder Guidance

If the user asks for an installable Codex or Claude skill:

- Create a folder named with lowercase hyphen-case.
- Include only `SKILL.md` plus optional `agents/openai.yaml`.
- Put detailed examples or long templates in `references/` only when they are truly needed.
- Keep the skill body lean and focused on the reusable process.

## Beginner Defaults

- Use plain language.
- Avoid tool jargon unless the workflow depends on it.
- Include one "next time paste this" prompt.
- Add review checks so beginners know when the AI output is ready.

---
name: gobble-skillify
description: Capture-router workflow for turning pasted sources, saved links, article text, transcripts, meeting excerpts, research notes, or inbox files into useful Markdown notes, routing recommendations, or draft Codex skills/checklists. Use when the user asks to "gobble", "skillify", process captured material, file research into a vault, clean an inbox, decide whether something is worth saving, create wikilinked notes from source material, or turn a repeatable process into a portable skill-style workflow.
---

# Gobble Skillify

## Core Rule

Do not assume the source is worth saving. Judge first, then route.

Use this skill to:

- decide keep/reject/review for captured material
- extract only useful context
- suggest a filing route
- draft a concise Markdown note
- flag claims that need verification
- identify whether the source contains a repeatable process
- draft a skill/checklist when the source is repeatable

## First Moves

1. Identify the source type: article, transcript, meeting note, saved post, raw inbox file, process description, or mixed capture.
2. Identify the working surface: plain chat, Markdown vault, Obsidian vault, repo docs, project folder, or community resource folder.
3. If working inside a vault or repo, read local instructions first when available, especially `AGENTS.md`, `CLAUDE.md`, or folder READMEs.
4. Default to read-only analysis unless the user asks to create, append, move, or edit files.
5. If filing, prefer existing folders and templates. Ask before inventing new folder structures.

## Gobble Pass

For every capture, produce this decision:

```markdown
## Keep or Reject

Choice: keep | reject | keep small excerpt | needs human review

## Why

- ...

## Best Route

Suggested destination:

## Clean Note Draft

Title:
Source:
Date captured:

Summary:

Useful points:

Action ideas:

Verification needed:

Related wikilinks:

## Skillify?

Choice: no | maybe | yes
Reason:
```

Keep the note draft concise. The purpose is future usability, not a full article rewrite.

## Routing Heuristics

Use these defaults unless local instructions say otherwise:

| Source | Usual route |
|--------|-------------|
| Useful background article | `05-reference/` or project `research/` |
| Repeatable process | `06-outputs/skill-drafts/` or project `resources/` |
| Meeting/community signal | project `meetings/`, `planning/`, or `scans/` |
| Quote, statistic, or product claim | reference/research note with verification needed |
| Vague idea with no current use | inbox or reject |
| Low-value noise | reject and do not save |

If the repository or vault has explicit routing rules, follow those over this table.

## Skillify Pass

Only skillify when the source contains a repeatable process. Do not skillify one-time opinions, vague inspiration, or unsupported claims.

When skillifying, draft:

```markdown
# Skill or Checklist Name

## Use When

## Inputs Needed

## Workflow

1.
2.
3.

## Safety Rules

## Review Checklist

## Stop and Ask If

## Example Prompt

## Successful Output
```

If the user asks for an actual Codex skill package, create or update a folder with a required `SKILL.md` and follow any available skill-creation instructions. Keep installable skill folders lean; put community-facing installation notes outside the skill folder.

## Filing Rules

When writing into a Markdown vault or repo:

- Preserve frontmatter and existing wikilinks.
- Use existing templates when the vault requires them.
- Include source and capture date.
- Add verification notes for product claims, pricing, legal/medical/financial advice, statistics, and anything likely to change.
- Keep private member details, credentials, cookies, access tokens, private screenshots, and paid content out of shared notes unless explicitly approved.
- Never write directly into confirmed memory folders when the vault has a human-in-the-loop memory flow.
- Do not move or delete inbox files unless the user explicitly asks.
- Report exact files created or changed.

## Stop Conditions

Stop and ask before filing if:

- the destination is unclear
- the source contains sensitive private data
- the capture may be copyrighted paid material
- the source includes credentials or tokens
- filing would require a new folder structure
- the note would expose private community/member information
- the user asked for a public/shareable artifact but permissions are unclear

## Useful Prompts

Gobble a source:

```text
Use $gobble-skillify to gobble this source. Tell me whether to keep, reject, route, or skillify it. Do not create files unless I ask.
```

File a source:

```text
Use $gobble-skillify to process this source and file the smallest useful Markdown note in the right place. Follow local AGENTS.md instructions and tell me every file you changed.
```

Skillify a process:

```text
Use $gobble-skillify to turn this repeatable process into a draft skill/checklist. Keep it portable and include safety rules, review checks, and stop conditions.
```

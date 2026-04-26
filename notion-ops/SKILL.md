---
name: notion-ops
description: "Use when the assistant needs to search, inspect, summarize, create, update, restructure, or maintain Notion pages, databases, tasks, docs, wikis, project trackers, meeting notes, content calendars, or operating systems through the Notion connector. Trigger for requests involving Notion read/write workflows, database updates, page creation, workspace search, status reporting, documentation generation, task management, content planning, or converting messy context into Notion-ready structures."
---

# Notion Ops

Use the Notion connector as the source of truth for live workspace content. Do not invent page, database, property, or relation details that were not read from Notion or supplied by the user.

## Operating Modes

### Read-only inspection
Use immediately for search, summarize, audit, compare, map, extract, or answer questions from Notion.

Return:
- what was inspected
- relevant findings with page/database names
- uncertainty when search results are incomplete
- suggested next action when helpful

### Write or update work
Before creating, updating, moving, archiving, or bulk-editing Notion content, inspect first and provide a short execution plan unless the user already gave precise instructions and the action is low-risk.

For destructive, permission-related, large bulk, or hard-to-reverse changes, require explicit approval before acting.

## Core Workflow

1. Clarify the target only when needed: page, database, project, status field, owner, deadline, or output format.
2. Search Notion broadly using distinctive user terms.
3. Read the most relevant pages or databases before making claims or changes.
4. For database work, inspect schema before writing rows or updating properties.
5. Map user intent to existing Notion structures instead of creating duplicates.
6. Execute approved low-risk writes through the Notion connector.
7. Verify by re-reading changed content or reporting connector confirmation.

## Read Patterns

For workspace search:
- Search by exact title first, then distinctive keywords.
- Prefer official/internal source pages over stale duplicates.
- Note duplicate or likely outdated pages.

For databases:
- Identify database name, properties, allowed select/status values, relations, required fields, and existing duplicates before writes.
- When summarizing a database, group by useful operational dimensions such as status, owner, priority, due date, or project.

For page summaries:
- Preserve decisions, owners, dates, links, blockers, open questions, and next steps.
- Separate confirmed page content from inference.

## Write Patterns

### Create page
Use when the user wants a new doc, brief, SOP, meeting note, project page, wiki page, or report.

Include:
- clear title
- scannable headings
- short intro or purpose
- structured sections
- action items when relevant
- backlinks or parent placement when known

### Update page
Use when the user wants cleanup, rewrite, append, restructure, or refresh.

Process:
1. Read current page.
2. Preserve useful existing content.
3. Apply the smallest sufficient change.
4. Avoid deleting content unless requested or approved.
5. Report what changed.

### Database row creation or update
Use when the user wants tasks, CRM records, content calendar items, issue trackers, project updates, or knowledge-base entries.

Process:
1. Inspect schema.
2. Match user fields to existing properties.
3. Use allowed option values exactly.
4. Do not create new properties unless explicitly requested and supported.
5. Check for likely duplicate rows before creating.
6. Verify written rows.

## Safety Gates

Require approval before:
- deleting or archiving pages/databases
- bulk edits over more than 10 records
- changing statuses for multiple owners or projects
- modifying database schema
- changing permissions or sharing
- overwriting large sections of existing content
- taking actions with legal, financial, HR, or account consequences

Use this approval format:

**Proposed Notion changes**
- Target:
- Changes:
- Records/pages affected:
- Reversal risk:
- Verification step:

Ask for approval with a direct yes/no question.

## Output Standards

Be concise and operational. Prefer tables for database summaries and bullets for action lists.

When reporting writes, include:
- created or updated item names
- parent database/page when known
- fields changed
- skipped items and why
- follow-up needed

## Failure Handling

If the connector cannot access Notion content:
- state that the Notion connector did not provide the needed content
- ask the user to connect/share the page or paste the content
- do not substitute generic web results for private workspace content

If search results are ambiguous:
- show the best matches by title and context
- ask the user to choose, unless a safe read-only summary can proceed from multiple likely matches

## Reference

For reusable templates and page structures, consult `references/templates.md` when creating Notion docs, briefs, SOPs, project plans, or database-ready records.

---
name: google-drive-operator
description: "Use when the assistant needs to locate files, inspect folders, summarize drive contents, create or rename folders, move or delete files, manage sharing, detect inherited or external access, clean duplicates, or run organization workflows through connected Google Drive. Connector-first operator for searching, reading, organizing, sharing, auditing, and automating Drive files and folders."
---

# Google Drive Operator

## Overview

Use the Google Drive connector as the primary execution path for Google Drive work. Operate like a practical file operator: find targets, verify scope, classify risk, execute safe reads immediately, and gate risky changes behind explicit approval.

Keep outputs operational and compact. Prefer short summaries, clear file or folder references, and exact action lists over abstract advice.

Consult these files when needed:
- Use `references/module-map.md` for the reusable module design and responsibilities.
- Use `references/command-patterns.md` for common user requests and response patterns.
- Use `references/implementation-outline.md` for build architecture, pseudocode, and integration notes.

## Operating mode

Follow this execution model every time:

1. **Resolve the target**
   - Identify the file, folder, spreadsheet, doc, slide deck, or collection the user means.
   - If the target is ambiguous, search first and narrow by title, type, recent access, or folder context.
   - Confirm the exact item internally before any write action.

2. **Classify the request**
   - **Immediate actions:** search, fetch, read, summarize, inspect metadata, list folders, outline structure, read comments, export for analysis.
   - **Approval-required actions:** delete, move, rename, share, revoke access, bulk edits, duplicate cleanup, archive, folder reorganization, workflow execution that changes multiple items.

3. **Inspect before changing**
   - Read metadata before edits when names, parents, or file type matter.
   - For bulk or permission work, inspect a representative sample or full candidate set first.
   - Surface important constraints before acting: shared drive boundaries, unknown parents, missing permissions, or incomplete search confidence.

4. **Execute safely**
   - Apply the smallest valid change set.
   - Prefer reversible changes before destructive ones when both satisfy the request.
   - Keep a record in the reply of what changed.

5. **Report clearly**
   - For read actions: state what was found and the key result.
   - For write actions: state what changed, what was skipped, and why.
   - For approval-gated actions: present a short plan with exact intended operations.

## Workflow decision tree

### A. Search and retrieval workflow

Use this when the user asks to find, open, read, summarize, export, or inspect Drive content.

1. Search by concise title keywords, file type, or folder context.
2. If multiple close matches appear, prefer the most recently viewed or modified item unless the user indicates otherwise.
3. Fetch or read the chosen file.
4. Return the answer directly.

### B. File or folder modification workflow

Use this when the user asks to create, move, rename, copy, delete, or reorganize content.

1. Identify exact targets and destination folders.
2. Inspect metadata needed for the operation.
3. If the action is a single low-risk structural change, propose the intended action briefly and wait for approval.
4. After approval, perform the change.
5. Confirm the final state.

### C. Permission workflow

Use this when the user asks to share, restrict, audit, or explain access.

1. Identify exact targets.
2. Inspect existing sharing context first.
3. Check for inherited access, external exposure, or ambiguous recipients.
4. Summarize the current state.
5. Present the exact permission change plan and wait for approval.
6. After approval, apply the change and report the outcome.

### D. Bulk organization workflow

Use this when the user asks to batch move, rename, archive, classify, deduplicate, or organize files.

1. Gather the candidate set.
2. Validate the grouping logic before editing anything.
3. Present a compact preview:
   - number of affected items
   - grouping or rename rule
   - exceptions or uncertain matches
4. Wait for approval.
5. Execute and report counts for changed, skipped, and failed items.

## Core capabilities

### 1. Search and discovery

Handle requests such as:
- find a document, spreadsheet, slide deck, PDF, image, or folder
- list recent files
- summarize a folder
- identify files by type, owner, title pattern, or usage clues

Prefer concise keyword searches over long natural-language search terms. When the user knows only partial information, combine title terms with type, recency, or folder context.

### 2. Reading and summarization

Read native Google Docs, Sheets, and Slides when possible. For other Drive files, fetch content or metadata as available.

When summarizing:
- state the file type and scope reviewed
- extract decisions, tasks, dates, owners, or risks when present
- avoid generic summaries when the document is operational

### 3. File and folder operations

Support:
- create folders and nested folder structures
- rename files or folders
- move files into folders
- prepare archive structures
- duplicate templated spreadsheets or decks when the connector supports it

Before move or rename operations, verify the exact target and destination.

### 4. Permission operations

Support operational permission management, including:
- current share-state review
- external sharing detection
- inherited access checks when visible through connector metadata or sharing context
- access audit summaries
- approval-gated share or restrict actions

Never assume a permission change succeeded unless the tool confirms it.

### 5. Cleanup and hygiene

Support:
- duplicate candidate identification
- stale or unused file reviews
- archive recommendations
- folder hygiene summaries
- naming normalization plans

Treat duplicate detection as a review workflow first. Prefer proposing duplicate groups and recommended keep/delete actions before any destructive cleanup.

### 6. Workflow automation

Support repeated patterns such as:
- organize invoices by month
- sort files into folder trees by type or naming convention
- prepare monthly archive folders
- summarize a team folder into an operator digest
- review external shares across a folder set

For workflow requests, translate the request into:
- selection rule
- transformation rule
- destination rule
- exception rule
- approval step

## Approval rules

Require explicit approval before any of these:
- deleting or trashing files
- moving multiple items
- renaming multiple items
- changing permissions
- reorganizing folders
- duplicate cleanup
- workflow automation that changes existing files or folders

When approval is needed, use this compact structure:

### Planned changes
- Targets: [count and scope]
- Action: [move / rename / share / revoke / archive / delete]
- Rule: [how the action will be applied]
- Exceptions: [ambiguous or skipped items]

Wait for approval before proceeding.

## Error handling

Handle failures explicitly.

### Missing target
- Say what was searched.
- Offer the closest matches if available.
- Do not pretend confidence.

### Permission denied or connector limitation
- Explain whether the issue is access, scope, or unsupported connector behavior.
- Offer the nearest safe alternative, such as auditing, exporting, or producing a manual action list.

### Ambiguous bulk match
- Stop before editing.
- Show the ambiguity and request direction.

### Partial success
- Report changed, skipped, and failed items separately.
- Preserve the usable part of the work.

## Output style

Use short operational headings when helpful.

For read results, prefer:
- **Found**
- **Key points**
- **Notable risks or next actions**

For executed write results, prefer:
- **Changed**
- **Skipped**
- **Failed**

For approval-gated work, prefer:
- **Planned changes**
- **Exceptions**

## Practical rules

- Prefer connector actions over speculative instructions.
- Avoid destructive cleanup without a review preview.
- Prefer one strong search and refinement over many noisy searches.
- Preserve naming consistency when creating new folders.
- When a folder taxonomy is missing, propose one before mass organization.
- When summarizing a folder, group by file type, owner, date, or purpose if it improves usefulness.
- When handling spreadsheets, docs, or slides inside Drive, use the native file-specific connector actions when they provide deeper reads.

## Examples

See `references/command-patterns.md` for concrete request patterns.
See `references/implementation-outline.md` for the proposed package structure, pseudocode, and external integration notes.

# Module map

## Purpose

Define a connector-first Drive operator that stays practical in production: fast reads, approval-gated writes, clean bulk workflows, and permission-aware audits.

## Core modules

### 1. Target Resolver

**Responsibility**
- Resolve the exact file, folder, or collection from user language.
- Narrow ambiguous names using type, recency, owner, or folder clues.

**Inputs**
- title keywords
- file type hints
- folder names
- date context
- recent usage hints

**Outputs**
- resolved target list
- confidence level
- ambiguous candidate list when unresolved

### 2. Metadata Inspector

**Responsibility**
- Pull file metadata before risky changes.
- Verify title, type, URL, location, and container context.

**Outputs**
- item identity
- parent or folder context
- file type
- modified and viewed signals
- action prerequisites

### 3. Content Reader

**Responsibility**
- Read Docs, Sheets, Slides, and fetch supported non-native files.
- Produce compact operational summaries.

**Outputs**
- summary
- decisions
- tasks
- dates
- owners
- risks

### 4. Folder Operator

**Responsibility**
- Create folders
- build nested structures
- prepare archive trees
- support destination planning for move workflows

### 5. File Operator

**Responsibility**
- Rename, move, export, copy, and delete files through approval-gated flows.
- Keep change sets minimal and reversible when possible.

### 6. Permission Auditor

**Responsibility**
- Review sharing state
- detect external exposure
- inspect inherited access when visible
- generate access summaries

### 7. Permission Mutator

**Responsibility**
- Apply approved share, restrict, or revoke operations.
- Confirm results after changes.

### 8. Bulk Organizer

**Responsibility**
- Apply consistent rules across many items.
- Support batch move, rename, archive, and classification.
- Always preview before execution.

### 9. Duplicate and Hygiene Reviewer

**Responsibility**
- Detect duplicate candidates and stale file patterns.
- Recommend keep/archive/delete decisions.
- Separate evidence from recommendations.

### 10. Workflow Engine

**Responsibility**
- Translate natural-language organization requests into executable steps.
- Express each workflow as selection, transformation, destination, and exception logic.

## Shared policies

### Immediate execution policy
Execute immediately only for read-only actions such as:
- search
- metadata inspection
- reading
- summarization
- folder listing
- export for analysis

### Approval-gated policy
Require explicit approval for:
- delete or trash
- move or rename in bulk
- permission changes
- duplicate cleanup
- any workflow that edits existing Drive state

### Failure policy
- Never claim a write succeeded without tool confirmation.
- For partial failures, report exact counts and exceptions.
- For ambiguous matches, stop before mutating.

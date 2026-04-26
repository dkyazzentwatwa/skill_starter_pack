# Command patterns

## Quick read and discovery

### Example 1
**User request**
Find the latest quarterly budget sheet.

**Expected behavior**
- Search by concise title terms
- prefer spreadsheets
- bias toward recent viewed or modified matches
- return the most likely match and key metadata

### Example 2
**User request**
Summarize the contracts folder.

**Expected behavior**
- inspect folder contents
- group by type or recency
- summarize notable files, stale items, and likely next actions

## Targeted edits

### Example 3
**User request**
Rename this file to 2026 Q2 planning deck.

**Expected behavior**
- verify exact target
- present one-line intended change
- wait for approval
- rename after approval

### Example 4
**User request**
Move all onboarding PDFs into a 2026 archive folder.

**Expected behavior**
- gather candidate files
- create archive folder if missing
- preview count and destination rule
- wait for approval
- move and report counts

## Permission operations

### Example 5
**User request**
Who can access this folder?

**Expected behavior**
- inspect current share state
- identify direct and inherited access if visible
- flag external access
- provide audit summary

### Example 6
**User request**
Share the roadmap folder with finance as viewers.

**Expected behavior**
- resolve folder and recipient target
- inspect current permissions first
- present exact permission change plan
- wait for approval
- apply change and confirm

## Cleanup operations

### Example 7
**User request**
Find duplicate proposal files and clean them up.

**Expected behavior**
- detect duplicate candidates by title, type, location, and recency clues
- propose keep/delete groups
- wait for approval before destructive action
- report changed, skipped, failed

### Example 8
**User request**
What files in this shared drive look stale or unused?

**Expected behavior**
- inspect recency and folder patterns
- return a review summary with archive recommendations
- do not move or delete without approval

## Workflow automation

### Example 9
**User request**
Organize all invoices by month.

**Expected behavior**
- define candidate selection rule for invoice files
- derive month grouping rule from file name, date metadata, or content hints available through connector reads
- preview folder structure and counts
- wait for approval
- execute organization and report results

### Example 10
**User request**
Audit this client folder for risky sharing.

**Expected behavior**
- inspect folder and representative contents
- identify external exposure and unexpected sharing
- summarize risk level and affected items
- propose remediation plan only after the audit

## Response patterns

### Read-only result pattern
- Found
- Key points
- Risks or next actions

### Executed change pattern
- Changed
- Skipped
- Failed

### Approval preview pattern
- Planned changes
- Rule
- Exceptions

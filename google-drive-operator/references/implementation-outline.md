# Implementation outline

## Package summary

### Skill name
google-drive-operator

### Description
A connector-first Google Drive operator that uses ChatGPT-connected Drive workflows for file retrieval, organization, sharing, auditing, and automation. It is designed for real operators, developers, and agents who need safe execution for both simple and advanced Drive tasks.

## Suggested file structure

```text
google-drive-operator/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── module-map.md
    ├── command-patterns.md
    └── implementation-outline.md
```

## Realistic implementation model

This skill is realistic because it is connector-first. It does not depend on unsupported local Drive filesystem access. Instead, it relies on three layers:

1. **Connector discovery layer**
   - search Drive files and folders
   - inspect metadata
   - list folder contents

2. **Content layer**
   - read Docs, Sheets, Slides, and supported fetched files
   - generate summaries and operational insights

3. **Mutation layer**
   - create files or folders
   - rename, move, export, share, or restrict items
   - run bulk workflows only after preview and approval

## Pseudocode

### Main request router

```pseudo
function handle_drive_request(user_request):
    target = resolve_target(user_request)
    action = classify_action(user_request)
    risk = classify_risk(action)

    if target.is_ambiguous:
        return present_candidate_list(target.candidates)

    if action in READ_ONLY_ACTIONS:
        data = execute_read_flow(target, action)
        return summarize_result(data)

    inspection = inspect_for_write(target, action)

    if risk in APPROVAL_REQUIRED:
        plan = build_change_plan(target, action, inspection)
        return request_approval(plan)

    result = execute_write_flow(target, action, inspection)
    return report_mutation_result(result)
```

### Bulk organization workflow

```pseudo
function organize_files(rule_set):
    candidates = collect_candidates(rule_set.selection)
    preview = build_preview(candidates, rule_set)

    if preview.has_ambiguity:
        return request_clarification(preview)

    return request_approval(preview)
```

```pseudo
function execute_approved_organization(rule_set, candidates):
    changed = []
    skipped = []
    failed = []

    for file in candidates:
        destination = derive_destination(file, rule_set)
        if destination is null:
            skipped.append(file)
            continue
        try:
            move_or_rename(file, destination)
            changed.append(file)
        except error as e:
            failed.append({file, e})

    return {changed, skipped, failed}
```

### Permission audit workflow

```pseudo
function audit_permissions(target):
    metadata = inspect_metadata(target)
    shares = inspect_current_sharing(target)
    inherited = inspect_inherited_access_if_visible(target)
    external = detect_external_access(shares)

    return build_audit_summary(metadata, shares, inherited, external)
```

### Duplicate review workflow

```pseudo
function review_duplicates(scope):
    candidates = find_similar_files(scope)
    groups = cluster_by_title_type_location(candidates)
    ranked = rank_keep_candidates(groups)
    return build_duplicate_review(groups, ranked)
```

## Optional integrations

### Supabase
Use Supabase to persist:
- folder taxonomies
- rename rules
- duplicate review decisions
- workflow job logs
- audit history

Useful tables:
- `drive_workflows`
- `drive_audits`
- `drive_duplicate_groups`
- `drive_folder_policies`

### Make.com
Use Make.com to trigger:
- scheduled folder hygiene reviews
- monthly invoice organization
- stale file digest delivery
- access audit summaries to email or Slack

### External APIs
Add API integrations only when the connector cannot supply a needed capability. Keep the skill connector-first by default.

## Naming conventions

### Folder names
Prefer stable, human-readable names such as:
- `Invoices/2026/03`
- `Archive/2026/Q1`
- `Clients/Acme/Roadmap`

### Bulk rename formats
Prefer deterministic patterns such as:
- `YYYY-MM-DD - title`
- `client - document type - version`
- `team - topic - quarter`

## Edge cases to handle

- same file title in multiple folders
- shared drive items with different edit constraints
- files lacking obvious date signals for month-based sorting
- permission changes blocked by role limits
- external shares on nested items inside otherwise internal folders
- partial failures during batch operations

## Quality checklist

- simple reads execute immediately
- destructive or bulk actions require approval
- ambiguous targets stop before mutation
- permission work starts with an audit summary
- duplicate cleanup uses a review-first flow
- outputs stay compact and operational

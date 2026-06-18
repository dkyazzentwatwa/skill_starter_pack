# Skill Starter Pack

A portable starter pack of 22 reusable AI skills for Codex, Claude Code, ChatGPT, and Claude.

Last checked against current public docs: 2026-06-17.

## What this pack is

Skills are reusable task instructions that an AI assistant can load only when they are relevant. This repo follows the open Agent Skills pattern: a skill is usually a folder with a `SKILL.md` file, plus optional `scripts/`, `references/`, `assets/`, and product-specific metadata.

Use this pack as:

- A ready-to-install set of practical skills.
- A template library for writing your own skills.
- A compatibility bridge between code-agent tools and chat apps that support uploaded skills.

## Skills Included

| Name | Format | Purpose |
|------|--------|---------|
| `brainstorming` | folder | Turn ideas into fully formed designs and specs before implementation |
| `brand-voice` | folder | Write, rewrite, or audit content in a specific brand voice |
| `content-repurposer` | folder | Convert one source piece into multi-platform content outputs |
| `context-card-builder` | folder | Turn messy background into reusable AI context |
| `executive-brief` | folder | Synthesize messy inputs into concise, decision-ready briefings |
| `gobble-skillify` | folder | Route captures and turn repeatable workflows into skills or checklists |
| `google-drive-operator` | folder | Search, organize, and manage Google Drive files through natural language |
| `ig-story-carousel` | folder | Generate polished Instagram carousel slides and stories |
| `inbox-briefing` | folder | Produce daily Gmail and Calendar briefing digests |
| `meeting-prep-card` | folder | Prepare for meetings from messy context |
| `notes-to-next-actions` | folder | Convert messy notes into decisions, tasks, and next prompts |
| `notion-ops` | folder | Read/write Notion pages, databases, and content |
| `output-reviewer` | folder | Review drafts for accuracy, readiness, privacy, and PII |
| `prompt-optimizer` | folder | Turn weak prompts into stronger, testable prompts |
| `safe-web-research` | folder | Research with sources, caveats, and clear confidence |
| `sop-builder` | folder | Transform process knowledge into operator-ready SOPs |
| `strategy` | folder | Give business strategy recommendations grounded in reality |
| `workflow-to-skill` | folder | Turn one successful workflow into a repeatable skill |
| `docx-skill` | folder | Create, read, and edit Word documents |
| `pdf` | folder | Process PDF files: extract, merge, split, fill forms, OCR |
| `pptx` | folder | Create, edit, and analyze PowerPoint presentations |
| `xlsx` | folder | Create, edit, and analyze Excel spreadsheets |

The included `.skill` files are ZIP archive copies of `ig-story-carousel`, `inbox-briefing`, and `strategy`. The expanded folders are easier to inspect and edit. If an app requires a `.zip` extension, copy or rename the `.skill` file to `.zip` before uploading.

## Compatibility Snapshot

| Surface | Best install shape | Invocation style | Notes |
|---------|--------------------|------------------|-------|
| Codex CLI, IDE extension, and Codex app | Folder under `.agents/skills/` or `~/.agents/skills/` | Explicit with `$skill-name` or implicit by description | Codex uses `agents/openai.yaml` when present for display metadata, invocation policy, and dependencies. |
| Claude Code | Folder under `.claude/skills/` or `~/.claude/skills/` | Explicit with `/skill-name` or implicit by description | Claude Code also supports project, personal, enterprise, and plugin skill locations. |
| ChatGPT app | Uploaded skill ZIP | Automatic when relevant | Skills are available in supported ChatGPT workspaces and do not sync across products yet. |
| Claude app | Uploaded skill ZIP through Customize > Skills | Automatic when relevant, with slash commands where available | Requires code execution and file creation to be enabled. Team and Enterprise owners can provision skills organization-wide. |

Skills teach process. They do not grant account access by themselves. Connector-backed skills still require the matching app, MCP server, or connector to be available and authorized in the product you are using.

## Install for Codex

Codex reads skill folders from repository, user, admin, and system locations. For a repo-local install:

```bash
mkdir -p .agents/skills
cp -R executive-brief .agents/skills/
```

For a personal install available across repositories:

```bash
mkdir -p ~/.agents/skills
cp -R executive-brief ~/.agents/skills/
```

Repeat with any folder-based skill in this repo. Codex detects skill changes automatically in most cases; restart Codex if a new or updated skill does not appear.

For distributed Codex workflows, use the folder skills while authoring locally, then package reusable sets as Codex plugins when you want to ship multiple skills, app mappings, MCP configuration, or presentation assets together.

## Install for Claude Code

For a personal Claude Code install:

```bash
mkdir -p ~/.claude/skills
cp -R executive-brief ~/.claude/skills/
```

For a project-specific install:

```bash
mkdir -p .claude/skills
cp -R executive-brief .claude/skills/
```

Claude Code exposes skills as slash commands based on the skill directory name. For example:

```text
/executive-brief
```

It can also choose a skill automatically when the request matches the skill description. Keep descriptions short, specific, and trigger-oriented.

## Install for ChatGPT

ChatGPT supports uploaded skills in supported workspaces.

1. Package the skill as a ZIP if it is not already archived.
2. In ChatGPT, open Skills from your profile or workspace skill page.
3. Choose New skill, then Upload from your computer.
4. Review any scan or review status before using the skill.

For a folder skill:

```bash
zip -r executive-brief.zip executive-brief
```

Then upload `executive-brief.zip`.

For a bundled `.skill` archive:

```bash
cp inbox-briefing.skill inbox-briefing.zip
```

Then upload `inbox-briefing.zip` if ChatGPT expects a `.zip` file.

## Install for the Claude app

Claude supports custom skills in the Claude app when code execution and file creation are enabled.

1. Package a skill folder as a ZIP.
2. Open Claude.
3. Go to Customize > Skills.
4. Add or create a skill, then upload the ZIP.
5. Toggle the skill on.

For Team and Enterprise accounts, owners can also provision approved skill ZIPs from Organization settings > Skills so members do not need to upload them individually.

## Packaging Tips

A valid folder skill should look like this:

```text
my-skill/
  SKILL.md
  references/
  scripts/
  assets/
  agents/
    openai.yaml
```

Only `SKILL.md` is required. Keep heavy reference material in `references/`, keep executable helpers in `scripts/`, and link to those files from `SKILL.md` so the agent can load them only when needed.

For best portability:

- Put `name` and `description` in the `SKILL.md` frontmatter.
- Make `name` lowercase with hyphens.
- Make `description` explain both what the skill does and when to use it.
- Keep one skill focused on one repeatable job.
- Prefer instructions over scripts unless deterministic code is truly useful.
- Review any skill with scripts before installing it in a chat app or sharing it with a team.

## Connector and App Requirements

These skills need external tools, apps, MCP servers, or connectors to be configured before they can complete the full workflow:

- `inbox-briefing`: Gmail and Google Calendar access.
- `google-drive-operator`: Google Drive access.
- `notion-ops`: Notion access.

OpenAI now uses "apps" as the unified term for ChatGPT connectors and interactive app integrations. Claude uses connectors and plugins in addition to skills. In both ecosystems, the skill is the workflow guidance; the connected app or MCP layer supplies live access to external systems.

## License Notes

Four skills in this pack contain proprietary code:

- `docx-skill/`
- `pdf/`
- `pptx/`
- `xlsx/`

Each of these includes a `LICENSE.txt` file in its folder. Read it before redistributing or modifying the scripts these skills reference. The `SKILL.md` instruction files themselves are free to use and adapt; the proprietary license covers the bundled utilities.

## Current Source Links

- [OpenAI Codex Agent Skills](https://developers.openai.com/codex/skills)
- [OpenAI Skills in ChatGPT](https://help.openai.com/en/articles/20001066-skills-in-chatgpt)
- [OpenAI Apps in ChatGPT](https://help.openai.com/en/articles/11487775-connectors-in-chatgpt)
- [Claude Code skills](https://code.claude.com/docs/en/skills)
- [Claude skills overview](https://support.claude.com/en/articles/12512176-what-are-skills)
- [Use skills in Claude](https://support.claude.com/en/articles/12512180-use-skills-in-claude)
- [Agent Skills specification](https://agentskills.io/specification)

## Community Use

Fork, adapt, and share these skills according to the license terms above. When sharing with a team, test each skill in your target product first, especially any skill that includes scripts or depends on connected apps.

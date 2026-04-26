# Skill Starter Pack

A collection of 15 production-ready skills for Claude Code and compatible AI agents. Use these skills as templates, starting points, or directly in your workflow.

## Skills Included

| Name | Type | Purpose |
|------|------|---------|
| **brainstorming** | folder | Turn ideas into fully formed designs and specs before implementation |
| **brand-voice** | folder | Write, rewrite, or audit content in a specific brand voice |
| **content-repurposer** | folder | Convert one source piece into multi-platform content outputs |
| **executive-brief** | folder | Synthesize messy inputs into concise, decision-ready briefings |
| **google-drive-operator** | folder | Search, organize, and manage Google Drive files through natural language |
| **notion-ops** | folder | Read/write Notion pages, databases, and content seamlessly |
| **prompt-optimizer** | folder | Turn weak prompts into stronger, testable prompts |
| **sop-builder** | folder | Transform process knowledge into operator-ready SOPs |
| **docx-skill** | folder | Create, read, and edit Word documents (.docx) |
| **pdf** | folder | Process PDF files: extract, merge, split, fill forms, OCR |
| **pptx** | folder | Create, edit, and analyze PowerPoint presentations |
| **xlsx** | folder | Create, edit, and analyze Excel spreadsheets |
| **ig-story-carousel** | .skill ZIP | Generate polished Instagram carousel slides and stories |
| **inbox-briefing** | .skill ZIP | Produce daily Gmail + Calendar briefing digests |
| **strategy** | .skill ZIP | Give business strategy recommendations grounded in reality |

## Installation

### Folder-Based Skills

Copy the entire folder into your Claude Code skills directory:

```bash
# Claude Code on macOS/Linux
cp -r <skill-name> ~/.claude/skills/

# Claude Code on Windows
cp -r <skill-name> %USERPROFILE%\.claude\skills\
```

### .skill ZIP Files

Copy the ZIP file directly into your skills directory:

```bash
# macOS/Linux
cp <skill-name>.skill ~/.claude/skills/

# Windows
cp <skill-name>.skill %USERPROFILE%\.claude\skills\
```

No need to unzip — the Claude Code runtime handles `.skill` archives automatically.

## License Notes

**Four skills in this pack contain proprietary code:**

- `docx-skill/` 
- `pdf/`
- `pptx/`
- `xlsx/`

Each of these includes a `LICENSE.txt` file in its folder. **Read it before redistributing or modifying the scripts these skills reference.** The `SKILL.md` instruction files themselves are free to use and adapt; the proprietary license covers the Python/JavaScript utilities bundled with them.

**Non-standard frontmatter field:** The `license: Proprietary` line in those skills' SKILL.md is not part of the official Anthropic skill authoring specification and will be silently ignored by the skill loader. It's preserved as attribution metadata.

## Compatibility Notes

### Connector Requirements

These skills require specific MCP connectors to be active in your Claude Code workspace:

- **inbox-briefing**: Requires Gmail and Google Calendar MCP connectors
- **google-drive-operator**: Requires Google Drive MCP connector  
- **notion-ops**: Requires Notion MCP connector

### Body Line Count

`docx-skill/SKILL.md` is 585 lines (85 lines over the soft 500-line limit suggested by the Anthropic skill authoring standard). It functions correctly as-is. Advanced users may want to move the XML Reference section (~125 lines) into a `references/xml-reference.md` file with a link from SKILL.md to improve context window efficiency.

## Technical Details

All skills conform to the [Anthropic skill authoring specification](https://agentskills.io/specification):

- Descriptions start with "Use when..." and specify triggering conditions (not workflow summaries)
- SKILL.md bodies are organized for progressive disclosure
- Code examples are production-ready
- Script dependencies are documented

## Community Use

These skills are ready to share with your team or community:

- ✅ Tested with Claude models (Opus, Sonnet, Haiku)
- ✅ No hardcoded platform dependencies (no "ChatGPT" branding)
- ✅ Compatible with standard Claude Code skill directories
- ✅ Self-contained (no cross-dependencies except where documented)

Feel free to fork, adapt, or redistribute according to the license terms noted above.

## Questions?

Refer to the official Anthropic skill authoring guide at `/skills/writing-skills/` for deeper details on how skills work, testing strategies, and best practices.

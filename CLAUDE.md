# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Claude Code plugin providing strategic planning and executive coaching tools for founders and solopreneurs. The plugin integrates with Notion via the Notion MCP server to manage Year Plans, Quarterly Reviews, Vision documents, Personal Operating Models, and multi-coach systems.

**Plugin Type**: Pure markdown-based Claude Code plugin (no code dependencies)
**Primary Integration**: Notion MCP server for data persistence
**Architecture**: Commands (explicit invocations) + Skills (auto-triggered agents)

## Key Architecture

### Plugin Structure

```
.claude-plugin/
├── plugin.json           # Plugin metadata (name, version, description)
├── config.template.json  # Template for user configuration
├── config.json          # User's Notion page URLs (gitignored, personal)
└── resources/
    └── founder-wisdom.md # Curated founder advice (used by coaches)

commands/                 # Explicit command invocations
├── coach.md             # Executive coach command
├── financial-coach.md   # Financial coach command
├── year-plan.md         # Year planning command
├── quarterly-review.md  # Quarterly review command
├── vision.md            # Vision/manifesto command
├── personal-operating-model.md
├── working-with-me.md
└── get-year-and-quarter.md

skills/                   # Auto-triggered skills
├── executive-coach/SKILL.md
├── financial-coach/SKILL.md
├── year-plan/SKILL.md
├── quarterly-review/SKILL.md
├── vision/SKILL.md
├── personal-operating-model/SKILL.md
└── working-with-me/SKILL.md
```

### Configuration System

**User configuration is loaded in this priority order:**

1. `.claude/config.md` or `CLAUDE.md` in working directory (project-specific)
2. `.claude-plugin/config.json` (plugin default)

**Configuration structure** (`.claude-plugin/config.json`):
```json
{
  "notion": {
    "vision": "https://www.notion.so/...",
    "yearPlan": "https://www.notion.so/...",
    "personalOperatingModel": "https://www.notion.so/...",
    "goldenRules": "https://www.notion.so/...",
    "logbook": "https://www.notion.so/...",
    "founderWisdom": "https://www.notion.so/..."
  }
}
```

**CRITICAL**: Always use the Read tool to load config at workflow start. Never hardcode URLs.

### Commands vs Skills

- **Commands** (`commands/*.md`): Explicitly invoked via `/founder-support-system:command-name`
- **Skills** (`skills/*/SKILL.md`): Auto-trigger based on SKILL.md `description` field keywords

Both point to the same underlying workflows but provide different entry points.

### Notion Integration Pattern

All skills and commands follow this pattern:

1. **Load Configuration** (Step 0):
   - Use Read tool to load `.claude-plugin/config.json`
   - Extract `config.notion.*` URLs for all pages

2. **Fetch Context** (if fresh session):
   - Use `mcp__notion__notion-fetch` with URLs from config
   - Cache context for session (don't re-fetch if conversation exists)

3. **Interactive Workflow**:
   - Use `AskUserQuestion` for structured input
   - Reference fetched Notion pages for context

4. **Save Output**:
   - Use `mcp__notion__notion-update-page` or `mcp__notion__notion-create-pages`
   - For Logbook: Create sub-pages organized by `YYYY/QN - Title`

### Key Skills & Their Workflows

**Year Plan** (`skills/year-plan/SKILL.md`):
- 60-90 minute comprehensive annual planning
- OKR-based (max 2-3 OKRs)
- Quarterly themes and strategic constraints
- Saves to `config.notion.yearPlan`

**Quarterly Review** (`skills/quarterly-review/SKILL.md`):
- 30-60 minute structured review
- 7-section framework
- START/STOP/STAY/DOUBLE-DOWN decisions
- Saves to Logbook as sub-page: `YYYY/QN - Quarterly Review`

**Executive Coach** (`skills/executive-coach/SKILL.md`):
- Fast tactical coaching (<2 min)
- Fetches context ONCE per session (Year Plan, Vision, Golden Rules, POM)
- Max 1-2 questions to user
- Console output only (no Notion saving)

**Financial Coach** (`skills/financial-coach/SKILL.md`):
- Burn rate and runway coaching
- Base/Best/Worst scenario planning (Stage 2 Capital method)
- References Year Plan financial targets
- Console output only

**Personal Operating Model** (`skills/personal-operating-model/SKILL.md`):
- 60-90 minute self-assessment
- 11 comprehensive sections
- Core Loop: Input → Transformation → Output
- Evidence-based strengths/weaknesses

**Vision** (`skills/vision/SKILL.md`):
- 60-90 minute philosophical foundation
- Mission themes, core beliefs, anti-manifesto
- Saved to `config.notion.vision`

## Common Development Tasks

When editing skills or commands:

1. **Update skill trigger keywords**: Edit the `description` field in SKILL.md frontmatter
2. **Add new Notion pages**: Update config.template.json and document in SETUP.md
3. **Modify workflows**: Edit the markdown in commands/*.md or skills/*/SKILL.md
4. **Update version**: Edit `.claude-plugin/plugin.json` version field
5. **Document changes**: Update CHANGELOG.md

## Important Patterns

### Fetching Notion Pages

```markdown
1. Load config.json with Read tool
2. Extract URL: config.notion.yearPlan
3. Use mcp__notion__notion-fetch with ID or URL
4. Cache context (don't re-fetch in same session)
```

### Creating Logbook Entries

Quarterly reviews are saved as sub-pages under Logbook:

```markdown
Parent: config.notion.logbook
Title format: "2025/Q1 - Quarterly Review"
Use mcp__notion__notion-create-pages with parent.page_id
```

### Interactive Workflows

All planning skills use `AskUserQuestion` for structured input:
- Keep questions focused (1-4 questions per call)
- Use multiSelect: false for single choice
- Provide context in question text
- Reference fetched Notion data for validation

### Coach Pattern

Coaches (executive-coach, financial-coach) follow this pattern:
- Fetch context ONCE on fresh start
- Max 1-2 questions to user
- Direct, bold, uncompromising tone
- Console output only (never save to Notion)
- Reference Year Plan, Vision, Golden Rules, Founder Wisdom

## Philosophy & Constraints

**Prime Directive**: Turn reflection into decisions.

**Coaching Principles**:
- Executive Coach: Strategic alignment, OKR focus, challenge misalignments
- Financial Coach: Burn rate realism, Base/Best/Worst scenarios, early monetization

**Planning Constraints**:
- Year Plan: Max 2-3 OKRs (focus over breadth)
- Quarterly Review: START/STOP/STAY/DOUBLE-DOWN framework
- Personal Operating Model: Evidence-based (no aspirational BS)

**Thought Leaders Referenced**:
- OKR frameworks (Google, Measure What Matters)
- Pieter Levels (ship fast, monetize early, bootstrap)
- Stage 2 Capital (Base/Best/Worst scenario planning)
- Reboot.io (Personal Operating Model)
- Clare Hughes Johnson (Scaling People)

## Testing & Validation

**Test configuration loading**:
```bash
/founder-support-system:get-year-and-quarter
```

**Test Notion integration**:
```bash
/founder-support-system:coach
# Should fetch Year Plan, Vision, Golden Rules without errors
```

**Test skill auto-triggering**:
- Say "coach me" → should trigger executive-coach skill
- Say "quarterly review" → should trigger quarterly-review skill
- Ask about "burn rate" → should trigger financial-coach skill

## Important Files

- `README.md`: User-facing documentation
- `SETUP.md`: Detailed setup instructions for Notion integration
- `PUBLISH.md`: GitHub publishing workflow
- `CHANGELOG.md`: Version history
- `.claude-plugin/config.template.json`: Config template (committed)
- `.claude-plugin/config.json`: User config (gitignored, personal URLs)
- `.claude-plugin/resources/founder-wisdom.md`: Curated founder advice

## .gitignore Rules

**Always gitignored**:
- `.claude-plugin/config.json` (contains personal Notion URLs)
- `*.log`
- `.DS_Store`
- `node_modules/` (though not used in this plugin)

**Always committed**:
- `.claude-plugin/config.template.json` (template for users)
- All commands/*.md and skills/*/SKILL.md
- `.claude-plugin/resources/` (bundled resources)

## Notes for Claude Code Instances

1. **Configuration loading**: Always use Read tool to load config, never hardcode URLs
2. **Session context**: Fetch Notion pages ONCE per session, cache for subsequent questions
3. **Logbook organization**: Create sub-pages with format `YYYY/QN - Title`
4. **Coach behavior**: Fast (<2 min), max 1-2 questions, console only
5. **Planning sessions**: Comprehensive (30-90 min), save to Notion
6. **No code dependencies**: This is a pure markdown plugin, no build steps required
7. **MCP dependency**: Requires Notion MCP server configured in user's Claude Code settings

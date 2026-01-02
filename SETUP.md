# Setup Guide - Founder Support System

## Prerequisites

1. **Claude Code** installed and configured
2. **Notion workspace** with the following pages created:
   - Vision page
   - Year Plan page
   - Personal Operating Model page
   - Golden Rules page
   - Logbook page
   - Founder Wisdom page

3. **Notion MCP server** configured in Claude Code

## Step-by-Step Setup

### 1. Install Plugin

```bash
claude plugin install github:Pitchlab/founder-support-system
```

Or install locally:
```bash
git clone https://github.com/Pitchlab/founder-support-system.git
cd founder-support-system
claude plugin install .
```

### 2. Install and Configure Notion MCP Server

The plugin requires the Notion MCP server to read and update Notion pages.

**Installation**:
- Follow the official guide: [Notion MCP Server](https://github.com/anthropics/notion-mcp)
- Add to your Claude Code MCP settings (usually in `~/.config/claude-code/mcp.json` or similar)

**Configuration**:
Add the Notion MCP server to your MCP settings with your Notion API token.

### 3. Create Notion Pages

Create these pages in your Notion workspace:

#### Vision
- Template: Blank page
- Title: "Strategy - Vision" (or your preferred title)
- Purpose: Store your manifesto, core beliefs, mission themes
- Used by: vision skill, all coaches

#### Year Plan
- Template: Blank page
- Title: "Strategy - Year Plan" (or your preferred title)
- Purpose: Store annual OKRs, financial targets, quarterly themes
- Used by: year-plan skill, quarterly-review, all coaches

#### Personal Operating Model
- Template: Blank page
- Title: "Strategy - Personal Operating Model v1" (or your preferred title)
- Purpose: Store your operating manual (strengths, weaknesses, decision system)
- Used by: personal-operating-model skill, executive-coach, working-with-me

#### Golden Rules
- Template: Blank page
- Title: "Strategy - Golden Rules" (or your preferred title)
- Purpose: Store your non-negotiable working principles
- Structure: Bulleted list of your non-negotiables (e.g., "No meetings before 10am", "Sales before scale")
- Used by: All skills and coaches

#### Logbook
- Template: Blank page
- Title: "Logbook" (or your preferred title)
- Purpose: Parent page for quarterly review entries (organized by year/quarter)
- Organization: Will auto-populate with `YYYY/QN - Quarterly Review` sub-pages
- Used by: quarterly-review skill

#### Founder Wisdom
- Template: Blank page
- Title: "Founder Wisdom" (or your preferred title)
- Purpose: Store wisdom from founders you respect
- Structure: Sections by founder (e.g., "Pieter Levels", "Paul Graham"), key lessons and quotes
- Used by: financial-coach, executive-coach
- Note: The plugin includes a bundled resource file with curated wisdom. This Notion page is optional but recommended for personalization.

### 4. Get Page URLs

For each page:
1. Open the page in Notion
2. Click "Share" → "Copy link"
3. URL format: `https://www.notion.so/Page-Title-{PAGE_ID}`

### 5. Configure Plugin

The plugin loads configuration in the following order (first found wins):
1. `.claude/config.md` or `CLAUDE.md` - Project-specific configuration (recommended)
2. `.claude-plugin/config.json` - Plugin default configuration

#### Option 1: Project-Specific Configuration (Recommended)

Create or update `.claude/config.md` or `CLAUDE.md` in your working directory:

```markdown
# Project Configuration

## Notion URLs

- vision: https://www.notion.so/Strategy-Vision-YOUR-PAGE-ID
- yearPlan: https://www.notion.so/Strategy-Year-Plan-YOUR-PAGE-ID
- personalOperatingModel: https://www.notion.so/Strategy-Personal-Operating-Model-YOUR-PAGE-ID
- goldenRules: https://www.notion.so/Strategy-Golden-Rules-YOUR-PAGE-ID
- logbook: https://www.notion.so/Logbook-YOUR-PAGE-ID
- founderWisdom: https://www.notion.so/Founder-Wisdom-YOUR-PAGE-ID
```

**Benefits**:
- Per-project configuration (different Notion workspaces for different projects)
- Version-controlled (can be committed to git)
- Context-aware (plugin automatically detects project configuration)

#### Option 2: Plugin Default Configuration

Alternatively, use global defaults via `.claude-plugin/config.json`:

1. Copy the config template:
   ```bash
   cp .claude-plugin/config.template.json .claude-plugin/config.json
   ```

2. Update `.claude-plugin/config.json` with your Notion page URLs:
   ```json
   {
     "notion": {
       "vision": "https://www.notion.so/Strategy-Vision-YOUR-PAGE-ID",
       "yearPlan": "https://www.notion.so/Strategy-Year-Plan-YOUR-PAGE-ID",
       "personalOperatingModel": "https://www.notion.so/Strategy-Personal-Operating-Model-YOUR-PAGE-ID",
       "goldenRules": "https://www.notion.so/Strategy-Golden-Rules-YOUR-PAGE-ID",
       "logbook": "https://www.notion.so/Logbook-YOUR-PAGE-ID",
       "founderWisdom": "https://www.notion.so/Founder-Wisdom-YOUR-PAGE-ID"
     }
   }
   ```

**Benefits**:
- Single configuration for all projects
- No need to configure each project separately

### 6. Test Installation

```bash
# Test year/quarter detection
/founder-support-system:get-year-and-quarter

# Test coaching (should load your Notion pages)
/founder-support-system:coach
```

If you get Notion errors, verify:
- Notion MCP server is configured and running
- Page URLs are correct in config.json
- You have access to all pages in Notion

## Usage

### Recommended Workflow

Start with:
1. **Vision** (60-90 min) - Define your philosophical foundation
2. **Golden Rules** (30 min) - Define your non-negotiables
3. **Year Plan** (60-90 min) - Set annual OKRs and strategy
4. **Personal Operating Model** (60-90 min) - Create your operating manual
5. **Quarterly Review** (30-60 min) - Review at end of each quarter

Daily:
- Use coaches for decisions and focus checks (`/founder-support-system:coach` or `/founder-support-system:financial-coach`)

### Commands vs Skills

**Commands** (explicit invocation):
- Use when you want to explicitly trigger a workflow
- Example: `/founder-support-system:year-plan`

**Skills** (auto-triggered):
- Auto-trigger based on conversation keywords
- Example: Saying "coach me" automatically triggers executive-coach skill
- Example: Asking about "burn rate" automatically triggers financial-coach skill

## Troubleshooting

### Error: "Could not fetch Notion page"
- Check config.json URLs are correct
- Verify Notion MCP server is running
- Ensure you have page access in Notion
- Test Notion connection with a simple query

### Error: "Command not found"
- Reinstall plugin: `claude plugin uninstall founder-support-system && claude plugin install github:Pitchlab/founder-support-system`
- Verify plugin is installed: `claude plugin list`

### Skills not triggering automatically
- Skills auto-trigger on keywords like "quarterly review", "year plan", "coach me"
- Or use explicit commands: `/founder-support-system:quarterly-review`
- Check the description field in each SKILL.md file for trigger keywords

### Notion MCP Server Not Working
- Verify MCP server is configured in Claude Code settings
- Check your Notion API token is valid
- Ensure you have granted the integration access to your Notion pages
- Restart Claude Code after MCP configuration changes

## Advanced Configuration

### Custom Page Titles
You can use any page titles in Notion. The config.json only needs the page URLs, not the titles.

### Multiple Workspaces
To use different Notion workspaces, create separate config.json files and swap them as needed, or maintain different plugin installations.

### Backup Your Config
Since `.claude-plugin/config.json` is gitignored (to protect your personal URLs), make sure to back it up separately.

## Support

Issues: https://github.com/Pitchlab/founder-support-system/issues

---
description: Setup guide and documentation for the Founder Support System plugin
allowed-tools: []
---

# Founder Support System - Setup & Help

Strategic planning and executive coaching plugin for founders and solopreneurs.

## Quick Start

### 1. Install Notion MCP Server

This plugin requires the Notion MCP server to read/write Notion pages.

**Installation**: Follow the [Notion MCP Server Guide](https://github.com/anthropics/notion-mcp)

Add to your Claude Code MCP settings (usually `~/.config/claude-code/mcp.json` or via Claude settings).

### 2. Create Notion Pages

Create these 6 pages in your Notion workspace:

1. **Vision** - Your manifesto, mission themes, core beliefs
2. **Year Plan** - Annual OKRs, financial targets, quarterly themes
3. **Personal Operating Model** - Strengths, weaknesses, decision system
4. **Golden Rules** - Non-negotiable working principles
5. **Logbook** - Parent page for quarterly review entries
6. **Founder Wisdom** - Curated principles from thought leaders (optional)

**Page Structure**: Use blank pages. The plugin will populate them with structured content.

### 3. Get Notion Page URLs

For each page:
1. Open in Notion
2. Click "Share" → "Copy link"
3. URL format: `https://www.notion.so/Page-Title-{PAGE_ID}`

### 4. Configure the Plugin

**Option A: Project-Specific (Recommended)**

Create `.claude/config.md` in your project directory:

```markdown
# Project Configuration

## Notion URLs

- vision: https://www.notion.so/YOUR-VISION-PAGE-URL
- yearPlan: https://www.notion.so/YOUR-YEAR-PLAN-PAGE-URL
- personalOperatingModel: https://www.notion.so/YOUR-POM-PAGE-URL
- goldenRules: https://www.notion.so/YOUR-GOLDEN-RULES-PAGE-URL
- logbook: https://www.notion.so/YOUR-LOGBOOK-PAGE-URL
- founderWisdom: https://www.notion.so/YOUR-FOUNDER-WISDOM-PAGE-URL
```

**Benefits**: Different Notion workspaces per project, version-controlled

**Option B: Global Configuration**

Create `.claude-plugin/config.json` in the plugin directory:

```json
{
  "notion": {
    "vision": "https://www.notion.so/YOUR-VISION-PAGE-URL",
    "yearPlan": "https://www.notion.so/YOUR-YEAR-PLAN-PAGE-URL",
    "personalOperatingModel": "https://www.notion.so/YOUR-POM-PAGE-URL",
    "goldenRules": "https://www.notion.so/YOUR-GOLDEN-RULES-PAGE-URL",
    "logbook": "https://www.notion.so/YOUR-LOGBOOK-PAGE-URL",
    "founderWisdom": "https://www.notion.so/YOUR-FOUNDER-WISDOM-PAGE-URL"
  }
}
```

**Benefits**: Single configuration for all projects

### 5. Test Installation

```bash
# Test basic command
/founder-support-system:get-year-and-quarter

# Test Notion integration
/founder-support-system:coach
```

## Available Commands

### Planning & Review
- `/founder-support-system:year-plan` - Create/update annual plan (60-90 min)
- `/founder-support-system:quarterly-review` - Structured quarterly review (30-60 min)
- `/founder-support-system:vision` - Create vision and manifesto (60-90 min)
- `/founder-support-system:personal-operating-model` - Self-assessment (60-90 min)
- `/founder-support-system:working-with-me` - User manual creation (20-30 min)

### Coaching (Fast, < 2 min)
- `/founder-support-system:coach` - Executive coach for daily decisions
- `/founder-support-system:financial-coach` - Burn rate and revenue coach

### Utilities
- `/founder-support-system:get-year-and-quarter` - Get current year/quarter
- `/founder-support-system:help` - This help screen

## Auto-Triggering Skills

Skills auto-trigger based on conversation context:

- **"coach me"** → Executive coach
- **"burn rate"**, **"runway"** → Financial coach
- **"year plan"**, **"annual planning"** → Year Plan skill
- **"quarterly review"**, **"Q1/Q2/Q3/Q4 review"** → Quarterly Review
- **"vision"**, **"manifesto"** → Vision skill

## Philosophy

**Prime Directive**: Turn reflection into decisions.

Based on:
- OKR frameworks (Google, Measure What Matters)
- Pieter Levels (ship fast, monetize early, bootstrap)
- Stage 2 Capital (Base/Best/Worst financial planning)
- Reboot.io (Personal Operating Model)
- Clare Hughes Johnson (Scaling People)

**Constraints**:
- Year Plan: Max 2-3 OKRs (focus over breadth)
- Quarterly Review: START/STOP/STAY/DOUBLE-DOWN framework
- Personal Operating Model: Evidence-based (no aspirational BS)

## Troubleshooting

### "Command not found"
- Verify plugin is installed: `claude plugin marketplace list`
- Reinstall: `claude plugin marketplace add Pitchlab/founder-support-system`

### "Could not fetch Notion page"
- Check config URLs are correct (`.claude/config.md` or `.claude-plugin/config.json`)
- Verify Notion MCP server is running
- Ensure you have page access in Notion
- Test Notion connection separately

### Skills not auto-triggering
- Use explicit commands instead: `/founder-support-system:coach`
- Or say trigger phrases: "coach me", "quarterly review", etc.

### Notion MCP Server not working
- Verify MCP server is configured in Claude Code settings
- Check Notion API token is valid
- Ensure integration has access to your pages
- Restart Claude Code after MCP configuration changes

## Documentation

- **Full Setup Guide**: https://github.com/Pitchlab/founder-support-system/blob/main/SETUP.md
- **Repository**: https://github.com/Pitchlab/founder-support-system
- **Issues**: https://github.com/Pitchlab/founder-support-system/issues

## Quick Reference Card

```
┌─────────────────────────────────────────────────┐
│  FOUNDER SUPPORT SYSTEM                         │
├─────────────────────────────────────────────────┤
│  DAILY USE:                                     │
│  • "coach me" - Executive coaching              │
│  • "burn rate" - Financial coaching             │
│                                                  │
│  PLANNING (60-90 min sessions):                 │
│  • /founder-support-system:year-plan            │
│  • /founder-support-system:quarterly-review     │
│  • /founder-support-system:vision               │
│  • /founder-support-system:personal-operating-  │
│    model                                        │
│                                                  │
│  CONFIG:                                        │
│  • .claude/config.md (project-specific)         │
│  • .claude-plugin/config.json (global)          │
│                                                  │
│  REQUIRES:                                      │
│  • Notion MCP Server                            │
│  • 6 Notion pages (Vision, Year Plan, POM,     │
│    Golden Rules, Logbook, Founder Wisdom)       │
└─────────────────────────────────────────────────┘
```

---

**Need more help?** See the full setup guide at:
https://github.com/Pitchlab/founder-support-system/blob/main/SETUP.md

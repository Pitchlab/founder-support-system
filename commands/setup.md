---
description: Interactive setup wizard for Founder Support System - configure Notion URLs
allowed-tools: [AskUserQuestion, Write, Read, Bash, mcp__notion__*]
---

# Founder Support System - Interactive Setup

This setup wizard will help you configure your Notion integration in 3 steps:

1. Verify Notion MCP Server is installed
2. Collect your Notion page URLs
3. Create configuration file

Let's get started!

---

## Step 1: Verify Notion MCP Server

**IMPORTANT**: This plugin requires the Notion MCP Server to work.

If you haven't installed it yet:
1. Follow: https://github.com/anthropics/notion-mcp
2. Add to Claude Code MCP settings
3. Restart Claude Code
4. Come back and run `/founder-support-system:setup` again

**Have you already installed and configured the Notion MCP Server?**

Use `AskUserQuestion` to confirm:

```json
{
  "questions": [
    {
      "question": "Have you installed and configured the Notion MCP Server?",
      "header": "MCP Server",
      "multiSelect": false,
      "options": [
        {
          "label": "Yes, it's configured",
          "description": "I've installed the Notion MCP server and added it to Claude Code settings"
        },
        {
          "label": "No, not yet",
          "description": "I need to install it first"
        }
      ]
    }
  ]
}
```

**If "No"**: Stop here and provide the installation link.

**If "Yes"**: Continue to Step 2.

---

## Step 2: Create Notion Pages

You need to create these 6 pages in your Notion workspace:

### Required Pages

1. **Vision** - Your manifesto, mission themes, core beliefs
2. **Year Plan** - Annual OKRs, financial targets, quarterly themes
3. **Personal Operating Model** - Strengths, weaknesses, decision system
4. **Golden Rules** - Non-negotiable working principles
5. **Logbook** - Parent page for quarterly review entries
6. **Founder Wisdom** - Curated principles from thought leaders (optional)

### How to Create

For each page:
1. Create a **blank page** in Notion
2. Give it a clear title (e.g., "Strategy | Vision", "Strategy | Year Plan")
3. Click "Share" → "Copy link"
4. Save the URL (you'll need it in the next step)

**Page URL format**: `https://www.notion.so/Page-Title-{PAGE_ID}`

**Have you created all 6 Notion pages?**

Use `AskUserQuestion` to confirm:

```json
{
  "questions": [
    {
      "question": "Have you created all 6 Notion pages and have their URLs ready?",
      "header": "Notion Pages",
      "multiSelect": false,
      "options": [
        {
          "label": "Yes, I have all URLs",
          "description": "I've created the pages and copied their share links"
        },
        {
          "label": "No, I need to create them",
          "description": "I'll create the pages first"
        }
      ]
    }
  ]
}
```

**If "No"**: Pause here and let them create the pages.

**If "Yes"**: Continue to Step 3.

---

## Step 3: Configure Notion URLs

Now let's collect your Notion page URLs and create the configuration file.

### Collect URLs

Use `AskUserQuestion` to get each URL. **Important**: Users can paste full URLs - don't require specific format:

```json
{
  "questions": [
    {
      "question": "What is the URL for your Vision page? (Paste the full Notion share link)",
      "header": "Vision URL",
      "multiSelect": false,
      "options": [
        {
          "label": "Paste URL",
          "description": "I'll paste the full Notion URL (https://www.notion.so/...)"
        }
      ]
    },
    {
      "question": "What is the URL for your Year Plan page?",
      "header": "Year Plan URL",
      "multiSelect": false,
      "options": [
        {
          "label": "Paste URL",
          "description": "I'll paste the full Notion URL"
        }
      ]
    },
    {
      "question": "What is the URL for your Personal Operating Model page?",
      "header": "POM URL",
      "multiSelect": false,
      "options": [
        {
          "label": "Paste URL",
          "description": "I'll paste the full Notion URL"
        }
      ]
    },
    {
      "question": "What is the URL for your Golden Rules page?",
      "header": "Golden Rules URL",
      "multiSelect": false,
      "options": [
        {
          "label": "Paste URL",
          "description": "I'll paste the full Notion URL"
        }
      ]
    },
    {
      "question": "What is the URL for your Logbook page?",
      "header": "Logbook URL",
      "multiSelect": false,
      "options": [
        {
          "label": "Paste URL",
          "description": "I'll paste the full Notion URL"
        }
      ]
    },
    {
      "question": "What is the URL for your Founder Wisdom page? (Optional - can skip)",
      "header": "Founder Wisdom",
      "multiSelect": false,
      "options": [
        {
          "label": "Paste URL",
          "description": "I'll paste the full Notion URL"
        },
        {
          "label": "Skip for now",
          "description": "I'll add this later"
        }
      ]
    }
  ]
}
```

### Create Configuration

Once you have all the URLs from the user's answers, create `.claude/config.md`:

1. **Check if `.claude/` directory exists**:
   ```bash
   mkdir -p .claude
   ```

2. **Write the config file** using the `Write` tool:

```markdown
# Project Configuration

## Notion Integration

The founder-support-system plugin uses these Notion page URLs:

```json
{
  "notion": {
    "vision": "USER_PROVIDED_VISION_URL",
    "yearPlan": "USER_PROVIDED_YEAR_PLAN_URL",
    "personalOperatingModel": "USER_PROVIDED_POM_URL",
    "goldenRules": "USER_PROVIDED_GOLDEN_RULES_URL",
    "logbook": "USER_PROVIDED_LOGBOOK_URL",
    "founderWisdom": "USER_PROVIDED_FOUNDER_WISDOM_URL"
  }
}
\```
```

3. **Add to .gitignore** (if in a git repo):
   ```bash
   # Check if .gitignore exists
   if [ -f .gitignore ]; then
     # Check if .claude/ is already in .gitignore
     if ! grep -q "^\.claude/$" .gitignore; then
       echo ".claude/" >> .gitignore
     fi
   fi
   ```

---

## Step 4: Test Configuration

Let's verify the setup works by fetching one of your Notion pages:

Use `mcp__notion__notion-fetch` with the Vision URL to test:

```javascript
mcp__notion__notion-fetch(visionUrl)
```

**If successful**:
```
✅ Configuration complete!

Your Notion integration is set up and working.

Next steps:
- Try: /founder-support-system:coach
- Or start planning: /founder-support-system:year-plan
- Need help? /founder-support-system:help
```

**If failed**:
```
❌ Could not connect to Notion page.

Troubleshooting:
1. Verify Notion MCP Server is running
2. Check the page URL is correct
3. Ensure the page is shared with your Notion integration
4. Try manually in Notion: Open the page and click Share

Need help? /founder-support-system:help
```

---

## Configuration Created

Your configuration has been saved to:
- **File**: `.claude/config.md` (gitignored)
- **Scope**: This project directory only

**To use a global configuration** (across all projects), create `.claude-plugin/config.json` instead.

---

## Complete! 🎉

You're all set up. The plugin is ready to use.

### Quick Start

Try these commands:
- `/founder-support-system:coach` - Get coaching on priorities
- `/founder-support-system:year-plan` - Create your annual plan
- `/founder-support-system:help` - View all commands

### What You Can Do Now

**Daily coaching** (< 2 min):
- Say "coach me" or use `/founder-support-system:coach`
- Ask about "burn rate" or use `/founder-support-system:financial-coach`

**Strategic planning** (60-90 min sessions):
- `/founder-support-system:year-plan` - Annual OKRs and strategy
- `/founder-support-system:quarterly-review` - Review and plan
- `/founder-support-system:vision` - Create your manifesto
- `/founder-support-system:personal-operating-model` - Self-assessment

---

**Documentation**: https://github.com/Pitchlab/founder-support-system

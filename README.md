# Founder Support System

Strategic planning and executive coaching plugin for founders and solopreneurs.

## Overview

A comprehensive Claude Code plugin providing:
- **Year Planning**: OKR-based annual planning with strategic constraints
- **Quarterly Reviews**: 30-60 min structured reviews with START/STOP/STAY/DOUBLE-DOWN decisions
- **Personal Operating Model**: 60-90 min self-assessment covering strengths, weaknesses, pitfalls, decision system
- **Vision & Manifesto**: Philosophical foundation with conviction and edge
- **Multi-Coach System**: Executive Coach (strategy), Financial Coach (burn rate/runway)
- **Working with Me**: User manual for colleagues and partners

## Installation

### Prerequisites

1. **Claude Code** installed and configured
2. **Notion MCP Server** - Required for Notion integration
   - Install: [Notion MCP Server Guide](https://github.com/anthropics/notion-mcp)
   - Configuration: Add to your Claude Code MCP settings
3. **Notion workspace** with configured pages (see [SETUP.md](./SETUP.md))

### Install Plugin

```bash
# From GitHub
claude plugin install github:Pitchlab/founder-support-system

# Or clone and install locally
git clone https://github.com/Pitchlab/founder-support-system.git
cd founder-support-system
claude plugin install .
```

### Quick Setup

1. Create Notion pages (Vision, Year Plan, Personal Operating Model, Golden Rules, Logbook, Founder Wisdom)
2. Copy page URLs from Notion
3. Configure `.claude-plugin/config.json` with your Notion URLs
4. Start using commands and coaches

See [SETUP.md](./SETUP.md) for detailed step-by-step instructions.

## Planning System Structure

The plugin integrates with a structured Notion workspace:

```
┌─────────────────────────────────────────────────────────────┐
│                         DASHBOARD                            │
├─────────────────────────────────────────────────────────────┤
│  • Inbox (capture zone)                                     │
│  • The System (daily operating rhythm)                      │
│  • Daily Rhythm (habits, routines)                          │
│  • Quarterly Rhythm (review cadence)                        │
│  • Logbook (quarterly review entries)                       │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│                         STRATEGY                             │
├─────────────────────────────────────────────────────────────┤
│  • Year Plan (OKRs, quarterly themes, strategic constraints)│
│  • Vision (mission themes, core beliefs, manifesto)         │
│  • Personal Operating Model (strengths, weaknesses, system) │
│  • Golden Rules (non-negotiable working principles)         │
│  • Founder Wisdom (curated principles from thought leaders) │
└─────────────────────────────────────────────────────────────┘
```

**Integration**: The plugin reads and updates these pages using the Notion MCP server.

## Commands

### Planning & Review
- `/founder-support-system:year-plan` - Create/update annual Year Plan (60-90 min)
- `/founder-support-system:quarterly-review` - Structured quarterly review (30-60 min)
- `/founder-support-system:vision` - Create vision and manifesto (60-90 min)
- `/founder-support-system:personal-operating-model` - Comprehensive self-assessment (60-90 min)
- `/founder-support-system:working-with-me` - User manual creation (20-30 min)

### Coaching
- `/founder-support-system:coach` - Executive coach for daily decisions (< 2 min)
- `/founder-support-system:financial-coach` - Burn rate and revenue coach (< 2 min)

### Utilities
- `/founder-support-system:get-year-and-quarter` - Get current year and quarter

## Skills

Skills auto-trigger based on conversation context:

- **Year Plan**: Triggers when user mentions "year plan", "OKRs", "annual planning"
- **Quarterly Review**: Triggers when user mentions "quarterly review", "Q1/Q2/Q3/Q4 review"
- **Vision**: Triggers when user mentions "vision", "manifesto", "mission"
- **Personal Operating Model**: Triggers when user mentions "POM", "operating model", "strengths assessment"
- **Working with Me**: Triggers when user mentions "working with me", "user manual"
- **Executive Coach**: Triggers when user says "coach me", "am I on track", "what should I focus on"
- **Financial Coach**: Triggers when user asks about "burn rate", "runway", "revenue targets", "finances"

## Features

### Year Planning
- OKR-based annual planning (max 2-3 OKRs)
- Quarterly themes and outcomes
- Strategic constraints and anti-goals
- Financial targets and kill criteria
- "The Challenge": one out-of-comfort-zone behavior shift

### Quarterly Reviews
- 7-section review framework
- START/STOP/STAY/DOUBLE-DOWN decisions
- Financial and capability tracking
- Meta-analysis with constraint identification
- Saves to Notion Logbook (organized by year/quarter)

### Personal Operating Model
- 11 comprehensive sections
- Core Loop: Input → Transformation → Output
- Evidence-based strengths assessment
- Failure patterns with interrupt rules
- Decision defaults and execution playbook
- Philosophy: "Design a system that works"

### Multi-Coach System
- **Executive Coach**: Strategic alignment, OKRs, focus checks
- **Financial Coach**: Burn rate, runway, Base/Best/Worst scenarios
- Both reference your Year Plan, Vision, Golden Rules, and Founder Wisdom

### Vision & Manifesto
- 7 mission themes (big-picture objectives)
- Core beliefs (operating principles)
- Anti-manifesto (what you stand against)
- Saved to Notion for reference by coaches

### Working with Me
- Personal user manual for colleagues/partners
- Covers communication, management style, boundaries
- References Personal Operating Model and Golden Rules

## Philosophy

Based on:
- **OKR frameworks** (Google, Measure What Matters)
- **Personal Operating Model** (Reboot.io)
- **Pieter Levels' bootstrapping** (ship fast, monetize early)
- **Stage 2 Capital's Base/Best/Worst planning** (scenario-based financial planning)
- **Clare Hughes Johnson's leadership frameworks** (Scaling People)

**Prime Directive**: Turn reflection into decisions.

## Requirements

- Claude Code CLI
- Notion workspace with configured pages
- Notion MCP Server configured

## Configuration

The plugin loads Notion page URLs in the following order (first found wins):

### 1. Project-Specific Configuration (Recommended)

Add configuration to `.claude/config.md` or `CLAUDE.md` in your project directory:

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

**Benefits**: Per-project configuration, workspace-specific URLs, version-controlled

### 2. Plugin Default Configuration

Alternatively, use `.claude-plugin/config.json` for global defaults:

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

See [SETUP.md](./SETUP.md) for detailed configuration instructions.

## Documentation

- [SETUP.md](./SETUP.md) - Step-by-step setup guide
- [CHANGELOG.md](./CHANGELOG.md) - Version history
- [PUBLISH.md](./PUBLISH.md) - GitHub publishing guide

## License

MIT

## Author

Erik van der Pluijm (erik@pitchlab.nl)

---
description: Interactive quarterly business review - performance, development, finance, and strategic planning
allowed-tools: [Skill]
---

# Quarterly Review Command

Run a comprehensive interactive quarterly review of your business covering performance, development, finance, and well-being. The review is saved to Notion for future reference and planning.

## Purpose

This command guides you through a structured Personal Business Quarterly Review (PBQR) that:
- Reviews the past quarter across all business dimensions
- Identifies patterns, constraints, and opportunities
- Sets clear objectives for the next quarter
- Produces a Notion Quarterly Log page for tracking

**Prime Directive: Turn reflection into decisions.**

## Usage

```bash
/planning-strategy:quarterly-review
```

**No arguments required** - The skill will guide you interactively.

## How It Works

This command invokes the `quarterly-review` skill, which:

1. **Determines the quarter** to review (the preceding quarter that just ended)
2. **Fetches reference materials** from Notion:
   - Personal Operating Model
   - Golden Rules
   - Year Plan
   - Previous Quarterly Log
3. **Guides you interactively** through 7 sections:
   - Quarter Snapshot (reality check)
   - Narrative Review (frictions & tailwinds)
   - Financial Review (scoreboard)
   - Goals Review (OKR-lite)
   - Capability & Asset Growth
   - Strategic Synthesis (patterns & decisions)
   - Meta-Analysis (Claude's strategic advice)
4. **Compiles the review** into a structured document
5. **Saves to Notion** under the Logbook page

## What You'll Need

**Time**: 30-60 minutes of focused attention

**Information**:
- Sales activity data (conversations, proposals, win/loss)
- Financial data (revenue, costs)
- Previous quarter goals (auto-fetched from Notion if available)
- Reflections on what worked and what didn't

## Output

A comprehensive Quarterly Log page in Notion containing:
- Quarter snapshot and narrative
- Financial scoreboard
- Goals review and next quarter objectives
- Capability growth tracking
- Strategic decisions (START / STOP / STAY / DOUBLE-DOWN)
- Claude's strategic analysis and recommendations

**Saved to**: https://www.notion.so/Your-Logbook-Page

## Review Framework

The review follows this structure:

### 0. Quarter Snapshot
5-10 bullets capturing what actually happened

### 1. Narrative Review
- Lived experience (frictions vs tailwinds)
- Constraints & struggles (categorized)

### 2. Financial Review
- Sales activity
- Revenue & costs
- Financial trajectory

### 3. Goals Review
- Last quarter assessment (Keep/Kill/Complete)
- Next quarter objectives (Growth, Leverage, Foundation)

### 4. Capability & Asset Growth
- Skills gained
- Business development
- Outreach & visibility
- Brag list (evidence file)

### 5. Strategic Synthesis
- Patterns observed
- START / STOP / STAY / DOUBLE-DOWN decisions

### 6. Meta-Analysis
- Biggest constraint
- Strategic focus recommendation
- Misalignment flags

## Design Principles

**Direct, No Fluff**: Signal only, no motivational language
**User Control**: You confirm before anything is saved
**Anti-Sycophancy**: Honest assessment, critical thinking
**Interactive**: Questions guide you, no pre-filled answers
**Actionable**: Every section feeds into decisions

## Success Criteria

A successful quarterly review should:
1. Kill at least ONE goal, tool, or idea
2. Identify the single biggest constraint
3. Generate 3 clear objectives for next quarter
4. Take 30-60 minutes of focused time
5. Result in a Notion page you'll actually use

## Example Flow

```
User: /planning-strategy:quarterly-review

Claude: Let me start your Q4 2025 Quarterly Review.

First, I'll fetch your reference materials...
✓ Personal Operating Model loaded
✓ Golden Rules loaded
✓ Year Plan 2025 loaded
✓ Q3 2025 Quarterly Log loaded

Let's begin with the Quarter Snapshot...

[Interactive questions follow]
```

## Tips for Best Results

1. **Block focused time** - Don't rush this
2. **Be honest** - Especially about what didn't work
3. **Have data ready** - Financial numbers, metrics
4. **Kill something** - If you don't stop/kill anything, you're not being honest
5. **Review Golden Rules** - Make sure decisions align

## Related Commands

- `/general:get-year-and-quarter` - Determine which quarter to review
- *Future: `/planning-strategy:update-year-plan`* - Update annual strategy

## Notes

- The skill automatically determines the PRECEDING quarter (the one that just ended)
- All answers are interactive - no pre-filled templates
- The review is saved to Notion only after your confirmation
- Previous quarter data is auto-fetched if it exists
- Claude provides strategic analysis based on your inputs

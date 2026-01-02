---
description: Interactive annual strategic planning and Year Plan creation/update
allowed-tools: [Skill]
---

# Year Plan Command

Create or update your comprehensive Year Plan with focused OKRs, financial targets, quarterly themes, and strategic constraints.

**Rule: If it doesn't move one of your OKR bars, it's a distraction.**

## Purpose

This command guides you through an interactive annual planning session that:
- Defines your strategic theme and one-year outcome
- Sets concrete financial targets and kill criteria
- Establishes 2-3 focused OKRs (Financial, Visibility, Development)
- Plans quarterly focus areas and priorities
- Defines positioning, visibility, and network goals
- Identifies risks and anti-goals
- Produces an updated Year Plan page in Notion

## Usage

```bash
/planning-strategy:year-plan
```

**No arguments required** - The skill will guide you interactively.

## How It Works

This command invokes the `year-plan` skill, which:

1. **Determines the current year** using `/general:get-year-and-quarter`
2. **Fetches reference materials** from Notion:
   - Vision (manifesto)
   - Personal Operating Model
   - Golden Rules
   - Current Year Plan (if exists)
   - Recent Quarterly Logs
3. **Guides you interactively** through 11 sections:
   - Strategic Theme & North Star
   - Financial Plan (revenue, profit, safety)
   - Objectives & Key Results (2-3 OKRs)
   - Quarterly Focus (themes and priorities)
   - Operating Priorities (weekly habits, time allocation)
   - Visibility & Positioning
   - Network & Leverage
   - Product/IP Bets (optional)
   - Risks & Anti-Goals
   - Review Cadence
   - Strategic Dashboard (progress tracking)
4. **Checks Vision alignment** to ensure coherence
5. **Updates Notion Year Plan** page after confirmation
6. **Archives old plan** at the end of the document

## What You'll Need

**Time**: 60-90 minutes of focused strategic thinking

**Information**:
- Last year's performance (if available)
- Financial targets and constraints
- Strategic priorities and focus areas
- Key capabilities to develop
- Market positioning ideas

## Output

A comprehensive Year Plan page in Notion containing:

### 1. Strategic Dashboard
Visual OKR progress bars (initially 0%)

### 2. North Star
- One-year outcome (Financial, Visibility, Development)
- Strategic constraints (hard rules)

### 3. Financial Plan
- Revenue targets (annual, monthly, mix)
- Profit & safety (margin, owner pay, runway, buffer)
- Financial kill criteria

### 4. Objectives & Key Results
2-3 focused OKRs with measurable key results

### 5. Quarterly Focus
Q1-Q4 themes, primary outcomes, max projects, non-goals

### 6. Operating Priorities
- Weekly non-negotiables (3 habits)
- Strategic work allocation (time %)

### 7. Visibility & Positioning
- Positioning statement
- Visibility KPIs (posts, reach, conversations, leads)

### 8. Network & Leverage
- Relationship targets
- Network rules

### 9. Product/IP Bets (Optional)
Active experiments with validation signals and decision dates

### 10. Risks & Anti-Goals
Known risks and identities to avoid

### 11. Review Cadence
Weekly, monthly, quarterly, yearly tracking

**Saved to**: https://www.notion.so/Your-Year-Plan-Page

## Year Plan Framework

```
Strategic Theme (One sentence, non-negotiable)
    ↓
North Star Outcome (Financial, Visibility, Development)
    ↓
2-3 OKRs (Measurable objectives with key results)
    ↓
Quarterly Focus (Execution layer with themes)
    ↓
Operating Priorities (Weekly habits, time allocation)
    ↓
Review & Track (Weekly KPIs, Monthly decisions, Quarterly rewrites)
```

## Design Principles

**Max 2-3 OKRs**: Focus beats volume
**SMART Targets**: Specific, measurable, achievable, relevant, time-bound
**Kill Criteria**: Know when to stop or pivot
**Vision Aligned**: Always check against long-term vision
**User Control**: Confirm before updating Notion
**Anti-Sycophancy**: Be realistic, not optimistic

## Success Criteria

A successful Year Plan should:
1. ✅ Have 2-3 focused OKRs (not 10)
2. ✅ Include clear financial kill criteria
3. ✅ Define quarterly themes (not detailed plans)
4. ✅ Align with Vision and Golden Rules
5. ✅ Be referenced weekly (not filed away)
6. ✅ Kill at least one thing explicitly (anti-goals)

## Example Flow

```
User: /planning-strategy:year-plan

Claude: Let me start your 2026 Year Plan.

First, I'll fetch your reference materials...
✓ Vision loaded
✓ Personal Operating Model loaded
✓ Golden Rules loaded
✓ Current Year Plan (2025) loaded

Let's begin with your Strategic Theme...

What is the ONE strategic theme for 2026? This is your non-negotiable focus.

[Interactive questions follow across 11 sections]

...

I've compiled your 2026 Year Plan. Should I save this to Notion?
```

## Key Sections Explained

### Strategic Dashboard
Visual progress bars for your primary OKRs. Update these monthly to track progress.

### North Star
Your one-year vision expressed as concrete outcomes, not activities. Answers "what does success look like?"

### Financial Plan
Hard numbers: revenue targets, profit margins, runway, buffer. Includes kill criteria to know when to change course.

### OKRs (2-3 Max)
- **Financial**: Buffer size, revenue growth, profit margin
- **Visibility**: Reach, conversations, leads, thought leadership
- **Development**: Skills gained, expertise level, capabilities

Each OKR has 2-3 measurable key results.

### Quarterly Focus
Break the year into themes. Each quarter has:
- One primary outcome
- Max project limit
- Explicit non-goals

### Operating Priorities
The weekly reality:
- 3 binary habits (done/not done)
- Time allocation across creation, delivery, visibility, ops

### Visibility & Positioning
How you show up in the market:
- Who you help, what outcome, what angle
- Measurable KPIs for visibility

### Network & Leverage
Relationship building targets and rules. Quality over quantity.

### Product/IP Bets
Optional experiments with clear validation signals and kill dates. Max 2 bets.

### Risks & Anti-Goals
What could go wrong, and what you will NOT become. Prevents mission drift.

## Tips for Best Results

1. **Block 90 minutes** - Don't rush strategic planning
2. **Review last year** - What worked? What didn't?
3. **Be realistic** - Ambitious but achievable targets
4. **Max 2-3 OKRs** - More objectives = less focus
5. **Set kill criteria** - Know when to stop
6. **Align with Vision** - Check coherence with long-term vision
7. **Define anti-goals** - What you will NOT do
8. **Reference Golden Rules** - Ensure compliance

## Related Commands

- `/planning-strategy:quarterly-review` - Review past quarter and plan next
- `/general:get-year-and-quarter` - Determine current year and quarter

## Notes

- The skill automatically determines the current year
- Old Year Plans are archived at the end of the document
- All answers are interactive - no pre-filled templates
- The Year Plan is updated only after your confirmation
- Progress bars start at 0% - update weekly/monthly
- Quarterly Focus is high-level themes, not detailed plans

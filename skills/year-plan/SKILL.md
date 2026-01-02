---
description: Interactive annual strategic planning and Year Plan update covering financial goals, OKRs, visibility, positioning, and quarterly focus areas. Use when user mentions "year plan", "annual plan", "update year plan", "strategic plan", "set annual goals", or wants to plan for the upcoming year.
allowed-tools: [SlashCommand, mcp__notion__*, AskUserQuestion, Bash(date:*), Read, Write]
---

# Year Plan: Interactive Annual Strategic Planning

**Rule: If it doesn't move one of your OKR bars, it's a distraction.**

## Overview

This interactive skill guides you through creating or updating your comprehensive Year Plan, covering:
- North Star outcome (one-year vision)
- Financial targets and kill criteria
- 2-3 focused OKRs (Financial, Visibility, Development)
- Quarterly focus themes
- Operating priorities and habits
- Visibility and positioning strategy
- Risks and anti-goals

The output is saved as an updated Year Plan page in Notion for ongoing tracking and execution.

## Notion Integration

**Configuration:**
Notion page URLs are loaded in the following order (first found wins):
1. `.claude/config.md` or `CLAUDE.md` - Project-specific configuration (check working directory)
2. `.claude-plugin/config.json` - Plugin default configuration

Use the Read tool to load configuration at the start of the workflow.

**Required Pages (configured in config files):**
- **Vision** (config.notion.vision): Strategy vision and manifesto
- **Personal Operating Model** (config.notion.personalOperatingModel): Strengths, weaknesses, operating manual
- **Golden Rules** (config.notion.goldenRules): Non-negotiable working principles
- **Logbook** (config.notion.logbook): Parent page for quarterly reviews (reference)
- **Year Plan** (config.notion.yearPlan): Output page for year plan

## Approach

Allowed-skills: Use the `financial-coach`, `levels-coach` and `executive-coach` skills for input if needed! Or use the `supercoach` agent! 

## Workflow

### Step 0: Setup & Context Gathering

1. **Load Configuration**:
   ```javascript
   // Use Read tool to load Notion page URLs from config
   // Try in order (first found wins):
   // 1. .claude/config.md (check for notion.* URLs in markdown)
   // 2. CLAUDE.md (check for notion.* URLs in markdown)
   // 3. .claude-plugin/config.json (JSON format)
   // Extract config.notion.vision, config.notion.yearPlan, config.notion.personalOperatingModel,
   // config.notion.goldenRules, config.notion.logbook
   // Use these URLs for all mcp__notion__notion-fetch calls below
   ```

2. **Determine Current Year**:
   ```bash
   # Call the command to determine year
   /founder-support-system:get-year-and-quarter
   ```
   This determines the current year for planning.

2. **Fetch Reference Materials**:
   Use `mcp__notion__notion-fetch` to retrieve:
   - Vision (manifesto, long-term direction)
   - Personal Operating Model (strengths, weaknesses)
   - Golden Rules (must-follow working principles)
   - Current Year Plan (if exists) for comparison
   - Recent Quarterly Logs for trend analysis

3. **Brief Context Summary**:
   Show user a 3-line summary:
   - Year being planned (e.g., "2026")
   - Vision summary (key themes)
   - Current state vs last year (if available)

---

### Section 1: Strategic Theme & North Star

**Purpose:** Define the non-negotiable focus and one-year outcome.

#### 1.1 Strategic Theme

**Interactive Question** (use `AskUserQuestion`):

"What is the ONE strategic theme for [YEAR]? This is your non-negotiable focus for the entire year. Examples: 'Scale advisory capacity', 'Build passive income', 'Establish thought leadership'."

**Format**: Open-ended text response

---

#### 1.2 One-Year Outcome

**Interactive Questions** (use `AskUserQuestion`):

Ask user to define outcomes in 3 areas:

1. **Financial Outcome**: "By Dec 31 [YEAR], what financial state will the business be in?"
   - Examples: "€100K revenue, €30K buffer", "€120K ARR with 40% profit margin"

2. **Visibility Outcome**: "By Dec 31 [YEAR], what visibility/reach will you have?"
   - Examples: "5K LinkedIn followers, 100 qualified leads", "Published book, 50 speaking engagements"

3. **Development Outcome**: "By Dec 31 [YEAR], what will you have learned or become expert in?"
   - Examples: "Expert in multi-agent orchestration", "Published 20 deep-dive articles on AI"

**Detailed Instructions for Financial Outcome**:
Use the following template for inspiration. 

```
Base/Best/Worst Case Planning Framework (Stage 2 Capital)

Three parallel scenarios that adapt to reality, not just one wishful-thinking plan.

Structure:
- Base Case: Built from actual historical data (last 3-6 months) + realistic hiring
- Best Case: Upside scenario (partnerships scale, pricing works, new products hit)
- Worst Case: Downside planning (churn rises, funding delays, key people leave)

Financial Focus:
- Each scenario has prescribed growth target + burn rate
- Track monthly against all 3 scenarios to know where you stand
- Pre-define trigger actions: "If we hit X revenue in Q2, unlock Y hires"
- Quarterly board reviews with all 3 scenarios

Sales/Marketing Strategy:
- Pressure-test assumptions with full GTM team in one room
- "Can marketing produce X leads 6 months from now at that cost?"
- "Can reps close 1 more deal/month by midyear?"
- Watch for stacked assumptions and unrealistic ramp times

Template: https://stage2.stockpress.co/shares/8353d6f2-e034-4f48-bf36-6a88092335d6

---
Sources:

- https://www.dearstage2.com/p/base-best-worst-your-2026-planning
```

Start with questions about the previous quarter / year. What was the revenue? What were the costs? What was the sales effort? 
Then, look at the upside. What is the goal to achieve? Help the user to estimate the required revenue by looking at salaries, costs, investments, buffer size. A sound buffer size is a minimum of 6-12 months of runway. 
Finally, look at the downside: what could go wrong? How to mitigate these risks? 

**Output**:
```markdown
# Year Plan — [YEAR]

**Business:** Your company/project
**Strategic Theme:** [One sentence theme]

---

## 1. North Star

### 1.1 One-Year Outcome

**By Dec 31 [YEAR], this business will:**

* **Financial**: [Outcome 1]
* **Visibility**: [Outcome 2]
* **Development**: [Outcome 3]
```
---

#### 1.3 Strategic Constraints (Hard Rules)

**Interactive Question** (use `AskUserQuestion`):

"What are 3 strategic constraints (hard rules) that define how you'll operate this year? These reduce optionality on purpose. Examples: 'No projects under €5K', 'Max 2 active clients', 'Only B2B, no B2C'."

Ask for 3 constraints.

**Output**:
```markdown
### 1.2 Strategic Constraints (Hard Rules)

* [Constraint 1]
* [Constraint 2]
* [Constraint 3]

<!-- These reduce optionality on purpose and define freedom to act -->
```

---

### Section 2: Financial Plan (Non-Optional)

**Purpose:** Set concrete financial targets and safety thresholds.

#### 2.1 Revenue Targets

**Interactive Questions** (use `AskUserQuestion`):

1. "What is your annual revenue target for [YEAR]?" (e.g., €100,000)
2. "What monthly baseline do you need to hit?" (auto-calculate: annual/12)
3. "What is your revenue mix?"
   - Consulting: [%]
   - Products/IP: [%]
   - Other: [%]

---

#### 2.2 Profit & Safety

**Interactive Questions**:

1. "What is your target profit margin?" (e.g., 40%)
2. "What monthly owner pay do you need?" (e.g., €4,000/month)
3. "How many months of runway do you want?" (e.g., 6 months)
4. "What is your cash buffer goal?" (e.g., €25,000)

**Output**:
```markdown
## 2. Financial Plan (Non-Optional)

### 2.1 Revenue Targets (SMART)

* **Annual Revenue:** €[X]
* **Monthly Baseline:** €[X] / month
* **Revenue Mix:**
  * Consulting: [%]
  * Products / IP: [%]
  * Other: [%]

---

### 2.2 Profit & Safety

* **Target Profit Margin:** [%]
* **Owner Pay:** €[X] / month
* **Runway (months):** [X]
* **Cash Buffer Goal:** €[X]
```

---

#### 2.3 Financial Kill Criteria

**Interactive Question**:

"What are 2 financial conditions that would force you to stop or change course? Examples: 'Revenue below €3K/month for 3 consecutive months', 'Buffer drops below €10K'."

**Output**:
```markdown
### 2.3 Financial Kill Criteria

Stop or change course if:

* [Condition 1]
* [Condition 2]
```

---

### Section 3: Objectives & Key Results (OKRs)

**Purpose:** Define 2-3 focused objectives with measurable key results.

**Framework**: Max 2-3 OKRs from:
- **Financial** (buffer size, revenue growth)
- **Visibility** (reach, conversations, leads)
- **Development** (learning, expertise level)

#### Interactive Process

For each OKR (2-3 total), ask:

1. **Objective Name**: "What is the objective?" (e.g., "Build Financial Safety Net")
2. **Why It Matters**: "Why does this objective matter? One sentence." (e.g., "Enables risk-taking and long-term thinking")
3. **Key Results** (3 max): "What are 3 measurable key results for this objective?"
   - Format: Metric + Target
   - Example: "Cash buffer → €30K", "Monthly revenue → €10K", "Profit margin → 45%"

**Output**:
```markdown
## 3. Objectives & Key Results (Year-Level)

### Objective A — [Objective Name]

**Why this matters:** [One sentence]

| Key Result | Metric     | Target     |
| ---------- | ---------- | ---------- |
| KR1        | [Metric]   | [Number]   |
| KR2        | [Metric]   | [Number]   |
| KR3        | [Metric]   | [Number]   |

---

### Objective B — [Objective Name]

**Why this matters:** [One sentence]

| Key Result | Metric     | Target     |
| ---------- | ---------- | ---------- |
| KR1        | [Metric]   | [Number]   |
| KR2        | [Metric]   | [Number]   |
| KR3        | [Metric]   | [Number]   |

---

### Objective C — [Objective Name] (Optional)

[Same structure]
```

---

### Section 4: Quarterly Focus (Execution Layer)

**Purpose:** Break the year into quarterly themes with clear priorities.

#### Interactive Process

For each quarter (Q1-Q4), ask:

1. **Theme**: "What is the one-word theme for [Q]?" (e.g., "Foundation", "Growth", "Scale", "Harvest")
2. **Primary Outcome**: "What is the ONE primary outcome for [Q]?" (e.g., "Launch advisory package", "Hit €10K MRR")
3. **Max Active Projects**: "How many projects can you handle simultaneously in [Q]?" (e.g., 2)
4. **Non-Goals**: "What will you explicitly NOT do in [Q]?" (e.g., "No new product development", "No conferences")

**Output**:
```markdown
## 4. Quarterly Focus (Execution Layer)

### Q1 — [Theme]

* **Primary Outcome:** [One]
* **Max Active Projects:** [Number]
* **Non-Goals:** [Explicitly what not to do]

### Q2 — [Theme]

* **Primary Outcome:** [One]
* **Max Active Projects:** [Number]
* **Non-Goals:** [Explicitly what not to do]

### Q3 — [Theme]

* **Primary Outcome:** [One]
* **Max Active Projects:** [Number]
* **Non-Goals:** [Explicitly what not to do]

### Q4 — [Theme]

* **Primary Outcome:** [One]
* **Max Active Projects:** [Number]
* **Non-Goals:** [Explicitly what not to do]
```

---

### Section 5: Operating Priorities (What You Actually Do)

**Purpose:** Define weekly habits and work allocation.

#### 5.1 Weekly Non-Negotiables

**Interactive Question**:

"What are 3 weekly non-negotiables (habits you track binary: done/not done)? Examples: '3 client conversations', 'Publish 1 article', 'Review finances'."

---

#### 5.2 Strategic Work Allocation

**Interactive Question**:

"How do you want to allocate your time across these categories (must total 100%)?"

Present options with suggested defaults:
- Creation / Thinking: [%]
- Delivery / Clients: [%]
- Visibility / Network: [%]
- Ops / Admin: [%]

**Output**:
```markdown
## 5. Operating Priorities (What You Actually Do)

### 5.1 Weekly Non-Negotiables

* [Habit 1]
* [Habit 2]
* [Habit 3]

Tracked weekly. Binary done / not done.

---

### 5.2 Strategic Work Allocation

* **Creation / Thinking:** [%]
* **Delivery / Clients:** [%]
* **Visibility / Network:** [%]
* **Ops / Admin:** [%]

If reality diverges → fix system, not willpower.
```

---

### Section 6: Visibility & Positioning (Measurable)

**Purpose:** Define positioning and set visibility KPIs.

#### 6.1 Positioning Statement

**Interactive Question**:

"Complete this positioning statement: 'I help [who] achieve [outcome] using [angle].'"

Example: "I help AI product teams achieve production-ready multi-agent systems using practical orchestration patterns."

---

#### 6.2 Visibility KPIs

**Interactive Questions**:

Ask for targets:
1. "How many posts/articles will you publish?" (e.g., 52)
2. "What reach/impressions target?" (e.g., 100K)
3. "How many inbound conversations?" (e.g., 50)
4. "How many qualified leads?" (e.g., 20)

**Output**:
```markdown
## 6. Visibility & Positioning (Optional but Measurable)

### Positioning Statement

> "I help [who] achieve [outcome] using [angle]."

---

### Visibility KPIs

* Posts published: [Number]
* Reach / impressions: [Number]
* Inbound conversations: [Number]
* Qualified leads: [Number]
```

---

### Section 7: Network & Leverage

**Purpose:** Set relationship and network growth targets.

#### Interactive Questions

1. "How many warm relationships do you want to build?" (e.g., 30)
2. "How many deep conversations (1+ hour)?" (e.g., 25)
3. "How many strategic alliances/partners?" (e.g., 3-5)

**Output**:
```markdown
## 7. Network & Leverage

### Strategic Relationship Targets

* **Warm relationships:** [Number]
* **Deep conversations:** [Number]
* **Alliances / partners:** [Number]

---

### Network Rules

* No coffee without intent
* No follow-ups without notes
* No calls without synthesis
```

---

### Section 8: Product / IP Bets (Optional)

**Purpose:** Define active product/IP experiments with clear kill criteria.

#### Interactive Question

"Do you have any product/IP bets for this year? (Yes/No)"

If **Yes**, for each bet (max 2):

1. **Bet Name**: "What is the product/IP bet?" (e.g., "AI Orchestration Course")
2. **Hypothesis**: "What's your one-sentence hypothesis?" (e.g., "Product teams will pay €500 for practical multi-agent patterns")
3. **Validation Signal**: "What metric validates this?" (e.g., "10 pre-sales by June")
4. **Decision Date**: "When will you decide to kill or double-down?" (e.g., "July 1, 2026")

**Output**:
```markdown
## 8. Product / IP Bets (Optional Section)

### Active Bets (Max 2)

**Bet 1: [Name]**
* **Hypothesis:** [One sentence]
* **Validation Signal:** [Clear metric]
* **Decision Date:** [Date]

**Bet 2: [Name]**
* **Hypothesis:** [One sentence]
* **Validation Signal:** [Clear metric]
* **Decision Date:** [Date]

Kill fast. Document learnings.
```

If **No**, output:
```markdown
## 8. Product / IP Bets

*No active product bets for [YEAR]. Focus on services/consulting.*
```

---

### Section 9: Risks & Anti-Goals

**Purpose:** Identify risks and define what you will NOT become.

#### Interactive Questions

1. **Known Risks**: "What are 2-3 known risks for this year?" (e.g., "Client concentration risk", "Market downturn", "Burnout")
2. **Anti-Goals**: "What will you NOT become? What traps will you avoid?" (e.g., "Not a generalist consultant", "Not dependent on one client", "Not working 60-hour weeks")

**Output**:
```markdown
## 9. Risks & Anti-Goals

### Known Risks

* [Risk 1]
* [Risk 2]
* [Risk 3]

---

### What You Will Not Become

* [Identity to avoid]
* [Trap to avoid]
* [Pattern to avoid]

This section prevents drift.
```

---

### Section 10: Review Cadence

**Purpose:** Define how you'll track and update the plan.

**Output** (auto-generated):
```markdown
## 10. Review Cadence

* **Weekly:** Update OKR progress bars + KPIs
* **Monthly:** Kill / double down decisions on projects
* **Quarterly:** Rewrite priorities (not goals) based on learnings
* **Year-End:** Post-mortem + next year thesis
```

---

### Section 11: Strategic Dashboard (Auto-Generated)

**Purpose:** Visual progress tracking for primary OKRs.

Based on user's OKRs, create progress bars (initially at 0%):

**Output**:
```markdown
## Strategic Dashboard

**Primary OKR 1** — [Name]
▩□□□□□□□□□ | 0%

**Primary OKR 2** — [Name]
▩□□□□□□□□□ | 0%

**Primary OKR 3** — [Name] (if exists)
▩□□□□□□□□□ | 0%

> Rule: If it doesn't move one of these bars, it's a distraction.
```

---

### Section 12: The Challenge (Out-of-Comfort-Zone Focus)

**Purpose:** Identify ONE specific behavior/focus that is hugely beneficial but completely outside comfort zone.

**Philosophy:** Growth happens at the edge of discomfort. This Challenge identifies the one thing that will unlock disproportionate results but requires operating in new territory.

**Process:**

1. **Analyze Year Plan Context**:
   Review user's:
   - OKRs and what they require
   - Quarterly focus themes
   - Operating priorities
   - Past patterns from Quarterly Logs (if available)
   - Personal Operating Model (strengths/weaknesses)

2. **Identify Comfort Zone Pattern**:
   Look for what user gravitates toward vs avoids:
   - Building vs shipping
   - Solo work vs meeting people
   - Research vs execution
   - Perfecting vs publishing
   - Writing vs speaking
   - Planning vs doing

3. **Interactive Question** (use `AskUserQuestion`):

   "Based on your Year Plan, what's the ONE behavior shift that would be hugely beneficial but feels completely outside your comfort zone?

   Examples:
   - ZERO build time → 100% SHIP/PUBLISH (if you over-build)
   - 100% MEET PEOPLE (if you work solo)
   - NO RESEARCH → PURE EXECUTION (if you over-analyze)
   - PUBLISH BEFORE PERFECT (if you over-polish)
   - SPEAK > WRITE (if you hide behind text)"

   **Format**: Open-ended text response

4. **Challenge Framing**:

   Once user identifies the challenge, frame it as a clear commitment:

   **Interactive Question** (use `AskUserQuestion`):

   "How will you measure this Challenge in [YEAR]?

   Make it binary or countable. Examples:
   - Ship 12 products (1/month) with ZERO polish
   - Have 100 face-to-face conversations
   - Publish 52 articles (1/week) same-day drafts
   - Give 24 talks (2/month) to real audiences"

   **Format**: Open-ended text response

**Output**:
```markdown
## The Challenge

**Behavior Shift:** [ONE uncomfortable focus]

**Why This Matters:** [How it unlocks Year Plan outcomes]

**Success Metric:** [Binary/countable measure]

**Anti-Pattern to Kill:** [What old behavior must stop]

---

> "If you're comfortable, you're not growing."
```

**Examples of Strong Challenges**:

✅ **ZERO Build → 100% Ship**
- Behavior Shift: No building without committed customer
- Success Metric: Launch 12 products, sell before coding
- Anti-Pattern: Building speculatively for 3+ months

✅ **100% MEET PEOPLE**
- Behavior Shift: Every week includes in-person meetings
- Success Metric: 100 face-to-face conversations by Dec 31
- Anti-Pattern: Hiding behind screen/async communication

✅ **PUBLISH BEFORE PERFECT**
- Behavior Shift: Same-day publish, zero polish
- Success Metric: 52 articles published within 24h of starting
- Anti-Pattern: Editing for weeks, never shipping

**Red Flags** (Challenge too weak):
- ❌ "Be more consistent" (vague)
- ❌ "Improve quality" (no behavior shift)
- ❌ "Try new things" (not specific)
- ❌ "Work harder" (not uncomfortable, just more)

---

### Step 8: Vision Alignment Check

**Process**:

1. Review user's Vision page content
2. Compare Year Plan objectives against Vision themes
3. Flag any **misalignments** or gaps

**Interactive Question**:

"Based on your Vision '[Vision summary]', does this Year Plan align? Any adjustments needed?"

Use `AskUserQuestion` with options:
- "Fully aligned - proceed"
- "Minor tweaks needed - adjust [specific area]"
- "Major misalignment - rethink objectives"

---

### Step 9: Compile & Save to Notion

**Process**:

1. **Compile Full Year Plan**:
   Combine all sections in this order:
   - Strategic Dashboard (with progress bars)
   - Section 1: North Star
   - Section 2: Financial Plan
   - Section 3: OKRs
   - Section 4: Quarterly Focus
   - Section 5: Operating Priorities
   - Section 6: Visibility & Positioning
   - Section 7: Network & Leverage
   - Section 8: Product/IP Bets
   - Section 9: Risks & Anti-Goals
   - Section 10: Review Cadence
   - Section 12: The Challenge

2. **Show Preview to User**:
   Display the complete Year Plan for user approval.

3. **Ask for Confirmation**:
   ```markdown
   I've compiled your [YEAR] Year Plan.

   Should I save this to Notion as the new Year Plan? (Yes/No)

   Note: The old year plan will be archived at the end of the document if it exists.
   ```

4. **If Yes, Update Notion Year Plan Page**:
   - Use `mcp__notion__notion-fetch` to get existing Year Plan page
   - If previous year plan exists, move it to the end under "## Archive - [Previous Year]"
   - Use `mcp__notion__notion-update-page` with `replace_content` to update the full page
   - Content: Full compiled Year Plan in Notion-flavored Markdown

5. **Confirm Completion**:
   ```markdown
   ✅ Year Plan for [YEAR] saved to Notion!

   📄 https://www.notion.so/Your-Year-Plan-Page

   **Next Steps**:
   - Review weekly to track OKR progress
   - Update progress bars monthly
   - Revisit quarterly to adjust focus
   - Reference during quarterly reviews
   ```

---

## Important Notes

- **Be Direct**: No motivational fluff. Signal only.
- **User Control**: Always confirm before updating Notion
- **Vision Alignment**: Always check against Vision page
- **Golden Rules Compliance**: Reference Golden Rules throughout
- **Max 2-3 OKRs**: Focus beats volume
- **Archive Old Plans**: Keep history for learning

## Error Handling

- If Notion pages don't load, ask user to verify URLs
- If previous Year Plan doesn't exist, create fresh (no archive)
- If user gets stuck on a question, offer to skip or provide examples
- Always save progress if user wants to pause

## Success Criteria

A successful Year Plan should:
1. Have 2-3 focused OKRs (not 10)
2. Include clear financial kill criteria
3. Define quarterly themes (not detailed plans)
4. Align with Vision and Golden Rules
5. Be referenced weekly (not filed away)
6. Kill at least one thing explicitly (anti-goals)

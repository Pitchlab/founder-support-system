---
description: Interactive quarterly business review covering performance, development, finance, and well-being. Use when user mentions "quarterly review", "quarter review", "Q1/Q2/Q3/Q4 review", "review past quarter", or wants to assess quarterly performance and plan next steps.
allowed-tools: [SlashCommand, mcp__notion__*, AskUserQuestion, Bash(date:*), Read, Write]
---

# Quarterly Review: Personal Business Quarterly Review (PBQR)

**Prime Directive: Turn reflection into decisions.**
If it doesn't change next quarter, it doesn't belong here.

## Overview

This interactive skill guides you through a comprehensive quarterly review of your business covering:
- Performance and lived experience
- Financial scoreboard
- Goals and objectives
- Capability and asset growth
- Strategic synthesis and decisions

The output is saved as a Quarterly Log page in Notion for reference and planning.

## Notion Integration

**Configuration:**
Notion page URLs are loaded in the following order (first found wins):
1. `.claude/config.md` or `CLAUDE.md` - Project-specific configuration (check working directory)
2. `.claude-plugin/config.json` - Plugin default configuration

Use the Read tool to load configuration at the start of the workflow.

**Required Pages (configured in config files):**
- **Year Plan** (config.notion.yearPlan): Strategic plan and OKRs
- **Personal Operating Model** (config.notion.personalOperatingModel): Strengths, weaknesses, operating manual
- **Golden Rules** (config.notion.goldenRules): Non-negotiable working principles
- **Logbook** (config.notion.logbook): Output location for quarterly review

## Workflow

### Step 0: Setup & Context Gathering

1. **Load Configuration**:
   ```javascript
   // Use Read tool to load Notion page URLs from config
   // Try in order (first found wins):
   // 1. .claude/config.md (check for notion.* URLs in markdown)
   // 2. CLAUDE.md (check for notion.* URLs in markdown)
   // 3. .claude-plugin/config.json (JSON format)
   // Extract config.notion.yearPlan, config.notion.personalOperatingModel,
   // config.notion.goldenRules, config.notion.logbook
   // Use these URLs for all mcp__notion__notion-fetch calls below
   ```

2. **Determine Quarter to Review**:
   ```bash
   # Call the command to determine quarter
   /founder-support-system:get-year-and-quarter
   ```
   This determines the PRECEDING quarter (the one that just ended).

2. **Fetch Reference Materials**:
   Use `mcp__notion__notion-fetch` to retrieve:
   - Personal Operating Model (strengths, weaknesses)
   - Golden Rules (must-follow working principles)
   - Year Plan for current year (strategic objectives)
   - Previous Quarterly Log (if exists) for comparison

3. **Brief Context Summary**:
   Show user a 3-line summary:
   - Quarter being reviewed (e.g., "Q4 2025")
   - Current year objectives from Year Plan
   - Key themes from previous quarter (if available)

---

### Section 1: Quarter Snapshot (Reality Check)

**Purpose:** Establish shared reality before analysis.

**Interactive Process:**

Use `AskUserQuestion` with these trigger questions:

1. **What worked with less effort than expected?**
   *Signals leverage, fit, and hidden advantages.*

2. **Where did you spend the most energy for the least return?**
   *Exposes false priorities and sunk-cost thinking.*

3. **What surprised you—positively or negatively?**
   *Surprises reveal broken assumptions.*

4. **If this quarter repeated 3 more times, would the business be stronger or weaker? Why?**
   *Forces trajectory thinking instead of point-in-time evaluation.*

5. **What did you avoid or postpone that now feels costly?**
   *Highlights fear, discomfort, or unresolved decisions.*

**Format**: Use `multiSelect: false` for open-ended responses.

**Output Structure**:
```markdown
## Quarter Snapshot: Q[X] [YEAR]

### What Happened
- [5-10 bullets from user responses]

### Narrative Summary
[One paragraph synthesizing the above]

### Quarterly Reset — Keep it alive

*instructions:* This is the maintenance ritual. Short. Non-negotiable. If you skip this, the model rots.

#### The four questions
1. Where did I create disproportionate value?
2. Where did I fight my nature?
3. Which pitfall showed up again?
4. What rule or constraint must tighten?

#### Updates (refer to Personal Operating Model in Notion)
- Strengths to exploit more:
- Weakness routing improvements:
- New constraints:
- Remove constraints (if proven safe):

```

---

### Section 2: Narrative Review

#### 2.1 Lived Experience

**Questions** (use `AskUserQuestion`):

Ask about **3 frictions** and **3 tailwinds**:

1. **Frictions**: "What consistently pushed you uphill this quarter? Where did things feel hard?"
2. **Tailwinds**: "What moved with little effort? What had natural momentum?"

**Output**:
```markdown
## Lived Experience

### Frictions (What Pushed Uphill)
1. [Friction 1]
2. [Friction 2]
3. [Friction 3]

### Tailwinds (What Moved Easily)
1. [Tailwind 1]
2. [Tailwind 2]
3. [Tailwind 3]
```

---

#### 2.2 Constraints & Struggles

**Questions** (use `AskUserQuestion` with multiple choice + open):

For each struggle identified in 2.1, ask user to categorize:

Options:
- **Structural** (system/process issue)
- **Capability** (skill/knowledge gap)
- **Positioning** (market/message problem)
- **Personal** (energy, focus, well-being)

**Output**:
```markdown
## Constraints & Struggles

### [Struggle Name] - [Category]
[User's explanation]

→ **Action**: [Structural/Positioning → next quarter priorities | Personal → environment design]
```

---

### Section 3: Financial Review (Scoreboard)

**Interactive Questions** (use `AskUserQuestion`):

#### 3.1 Sales Activity
Ask for:
- Real conversations held
- Proposals sent / won / lost
- Average deal size
- Sales cycle length

#### 3.2 Revenue & Cost
Ask for:
- Gross revenue
- Fixed costs
- Variable costs
- Revenue per hour estimate

#### 3.3 Financial Trajectory
Ask:
- "Are you on track vs annual target? (Yes/No/Unsure)"
- "If nothing changes, where do you land in 12 months?"

**Output**:
```markdown
## Financial Review

### Sales Activity
| Metric | Q[X] [YEAR] | Trend vs Last Quarter |
|--------|-------------|----------------------|
| Conversations | [X] | [↑/↓/→] |
| Proposals Sent | [X] | [↑/↓/→] |
| Proposals Won | [X] | [↑/↓/→] |
| Avg Deal Size | €[X] | [↑/↓/→] |
| Sales Cycle | [X] days | [↑/↓/→] |

### Revenue & Cost
- **Gross Revenue**: €[X]
- **Fixed Costs**: €[X]
- **Variable Costs**: €[X]
- **Net**: €[X]
- **Revenue/Hour**: €[X]

### Financial Trajectory
- **Annual Target Status**: [🟢 On Track | 🟡 Behind | 🔴 Off Track]
- **12-Month Projection**: [User's answer]

→ [If Red: Mandatory strategic change required]
```

---

### Section 4: Goals Review (OKR-Lite)

#### 4.1 Review Last Quarter Objectives

**Process**:
1. Fetch previous Quarterly Log (if exists)
2. Extract previous quarter's objectives
3. For each objective, ask user: "Keep / Kill / Complete?"

**Output**:
```markdown
## Last Quarter Objectives Review

### Objective 1: [Name]
- **Status**: [Keep | Kill | Complete]
- **Reason**: [User's explanation]

[Repeat for each objective]
```

---

#### 4.2 Next Quarter Objectives (Max 3)

**Interactive Process**:

Ask user to define **exactly 3 objectives**:
- **One growth objective** (revenue, reach, market)
- **One leverage objective** (systems, efficiency, automation)
- **One foundation objective** (skills, infrastructure, health)

For each objective, ask:
1. "What measurable outcome defines success?"
2. "What single constraint does this address?"
3. "What are 2-4 key results?"

**Output**:
```markdown
## Next Quarter Objectives: Q[X+1] [YEAR]

### 1. Growth Objective: [Name]
**Constraint Addressed**: [User's answer]

**Key Results**:
1. [KR1]
2. [KR2]
3. [KR3]
4. [KR4]

---

### 2. Leverage Objective: [Name]
**Constraint Addressed**: [User's answer]

**Key Results**:
1. [KR1]
2. [KR2]

---

### 3. Foundation Objective: [Name]
**Constraint Addressed**: [User's answer]

**Key Results**:
1. [KR1]
2. [KR2]
```

---

### Section 5: Capability & Asset Growth

**Interactive Questions** (use `AskUserQuestion`):

#### 5.1 Learning & Skill Accretion
- "What can you do now that you couldn't 90 days ago?"
- "Where have you applied these skills?"

#### 5.2 Business Development
- "How many new meaningful connections?"
- "Who moved from cold to warm?"
- "Who created second-order opportunities?"

#### 5.3 Outreach & Visibility
- "What did you publish or share?"
- "What created inbound interest?"
- "What fell flat?"

#### 5.4 Brag List
- "What did you ship?"
- "What concrete results for clients?"
- "What changed for your audience?"

**Output**:
```markdown
## Capability & Asset Growth

### Skills Gained
- [Skill 1]: Applied in [context]
- [Skill 2]: Applied in [context]

### Business Development
- **New Connections**: [X]
- **Warm Relationships**: [X]
- **Strategic Allies**: [Names]

### Outreach & Visibility
**Experiments Run**:
- [Experiment 1]: [Result]
- [Experiment 2]: [Result]

**Key Insight**: [One thing to double down on]

### Brag List (Evidence File)
- [Achievement 1]
- [Achievement 2]
- [Achievement 3]

**Concrete ROI**: [User's answer]
```

---

### Section 6: Strategic Synthesis (Most Important)

#### 6.1 Patterns

Ask user: "Looking back at everything above, what patterns do you see?"

Prompt for:
- What repeated?
- What scaled?
- What drained disproportionate energy?

**Output**: Max 3 patterns

---

#### 6.2 Decisions (START / STOP / STAY / DOUBLE-DOWN)

**Interactive Process** (use `AskUserQuestion` with options):

Present the framework and ask user to fill in:

**START**:
- "What ONE thing would unlock leverage next quarter?"

**STOP**:
- "What ONE thing is net negative and must be cut?"

**STAY**:
- "What ONE behavior/system is working and should continue?"

**DOUBLE-DOWN**:
- "What ONE proven asset should you amplify?"

**Output**:
```markdown
## Strategic Synthesis

### Patterns Observed
1. [Pattern 1]
2. [Pattern 2]
3. [Pattern 3]

### Strategic Decisions

#### START
**[One thing to start]**
Why: [User's rationale]

#### STOP
**[One thing to stop]**
Why: [User's rationale]

#### STAY
**[One thing to stay]**
Why: [User's rationale]

#### DOUBLE-DOWN
**[One proven asset to amplify]**
Why: [User's rationale]
```

---

### Section 7: Meta-Analysis (Claude's Strategic Advice)

**Process**:

After gathering all user input, provide **direct, no-fluff strategic advice**:

1. Identify the **single biggest constraint** limiting progress
2. Propose **one strategic focus** for next quarter
3. Recommend specific actions (start/stop/double-down)
4. Flag any **misalignment** between effort, revenue, and positioning

**Tone**: Be direct. No motivational language. Optimize for leverage, clarity, and compounding advantage.

**Output**:
```markdown
## Strategic Advice (Claude Analysis)

### Single Biggest Constraint
[Constraint identification]

### Recommended Strategic Focus for Q[X+1]
[One clear focus area]

### Specific Recommendations
**START**: [One thing]
**STOP**: [One thing]
**DOUBLE-DOWN**: [One thing]

### Misalignment Flags
[Any gaps between effort, revenue, and long-term positioning]

---

**Final Note**: If this review doesn't kill at least one goal, tool, or idea, it's not honest enough.
```

---

### Step 8: Compile & Save to Notion

**Process**:

1. **Compile Full Quarterly Review**:
   Combine all sections above into a single, well-structured markdown document.

2. **Show Preview to User**:
   Display the complete review for user approval.

3. **Ask for Confirmation**:
   ```markdown
   I've compiled your Q[X] [YEAR] Quarterly Review.

   Should I save this to Notion under the Logbook page? (Yes/No)
   ```

4. **If Yes, Save to Notion**:
   - Use `mcp__notion__notion-create-pages` to create a new page titled "Q[X] [YEAR] Quarterly Review"
   - Set parent page to: https://www.notion.so/Your-Logbook-Page
   - Content: Full compiled review in Notion-flavored Markdown
   - Add properties if the Logbook has a database structure (Year, Quarter, etc.)

5. **Confirm Completion**:
   ```markdown
   ✅ Quarterly Review saved to Notion!

   📄 [Link to new page]

   **Next Steps**:
   - Review your Next Quarter Objectives
   - Update Year Plan if needed
   - Schedule check-ins for key results
   ```

---

## Important Notes

- **Be Direct**: No motivational fluff. Signal only.
- **User Control**: Always confirm before saving to Notion
- **Anti-Sycophancy**: Challenge patterns, call out misalignments
- **Surgical Questions**: Ask exactly what's needed, no more
- **Golden Rules Compliance**: Reference Golden Rules throughout if they relate to decisions

## Error Handling

- If Notion pages don't load, ask user to verify URLs
- If previous quarter doesn't exist, skip comparison
- If user gets stuck on a question, offer to skip or come back later
- Always save progress if user wants to pause

## Success Criteria

A successful quarterly review should:
1. Take 30-60 minutes of focused interaction
2. Produce at least ONE decision to stop/kill something
3. Identify the single biggest constraint
4. Generate 3 clear objectives for next quarter
5. Result in a Notion page the user will actually reference

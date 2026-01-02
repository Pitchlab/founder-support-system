---
description: Interactive 'Working with Me' document creation for sharing your work style, preferences, and operating principles with colleagues, partners, and clients. Use when user mentions "working with me", "create working with me", "user manual", "how to work with me", or wants to document their work style and preferences.
allowed-tools: [SlashCommand, mcp__notion__*, AskUserQuestion, Read, Write]
---

# Working with Me: Interactive User Manual Creation

**Purpose**: Create a comprehensive "Working with Me" document that serves as a user manual for colleagues, business partners, and clients.

## Overview

This interactive skill guides you through creating a personal "Working with Me" document covering:
- Your role and goals
- Personality and communication preferences
- Operating approach (cadence, meetings, 1:1s)
- Management style and decision-making
- How you support your team
- Boundaries and pitfalls

The output is saved as a new page in Notion under your Resources page.

## Notion Integration

**Configuration:**
Notion page URLs are loaded in the following order (first found wins):
1. `.claude/config.md` or `CLAUDE.md` - Project-specific configuration (check working directory)
2. `.claude-plugin/config.json` - Plugin default configuration

**Required Pages (configured in config files):**
- **Personal Operating Model** (config.notion.personalOperatingModel): Strengths, weaknesses, pitfalls
- **Golden Rules** (config.notion.goldenRules): Non-negotiable principles
- **Year Plan** (config.notion.yearPlan): Strategic context
- **Logbook** (config.notion.logbook): Historical patterns

**Output**: Creates a new "Working with Me" page

## Workflow

### Step 0: Setup & Context Gathering

1. **Load Configuration**:
   ```javascript
   // Use Read tool to load Notion page URLs from config
   // Try in order (first found wins):
   // 1. .claude/config.md (check for notion.* URLs in markdown)
   // 2. CLAUDE.md (check for notion.* URLs in markdown)
   // 3. .claude-plugin/config.json (JSON format)
   // Extract all config.notion.* URLs for use below
   ```

2. **Determine Current Year/Quarter**:
   ```bash
   /founder-support-system:get-year-and-quarter
   ```

2. **Fetch Reference Materials**:
   Use `mcp__notion__notion-fetch` to retrieve:
   - Personal Operating Model (strengths, weaknesses, work style)
   - Golden Rules (must-follow working principles)
   - Year Plan (current role, OKRs, strategic focus)
   - Recent Quarterly Logs (for context on patterns)

3. **Brief Context Summary**:
   Show user what you've gathered:
   ```
   I've reviewed your Personal Operating Model, Golden Rules, and Year Plan.

   I'll guide you through creating your "Working with Me" document covering:
   - Your role and goals
   - Personality and communication preferences
   - Operating approach and cadence
   - Management style
   - How you support your team

   This will take about 20-30 minutes.
   ```

---

### Section 1: My Role

**Purpose:** Define your role and goals clearly.

**Context to Reference:**
- Year Plan (strategic theme, OKRs, North Star)
- Personal Operating Model (what you're good at)

**Interactive Question** (use `AskUserQuestion`):

"What is your role and what are your primary goals?

Consider:
- Official title and what it means in practice
- Core responsibilities (what you own)
- Primary goals for [YEAR]
- Who you serve (team, clients, partners)"

**Format**: Open-ended text response

**Output**:
```markdown
# Working with [Your Name]

## My Role

[User's response about role and goals]
```

---

### Section 2: About Me

**Purpose:** Share personality, communication preferences, and boundaries.

**Context to Reference:**
- Personal Operating Model (personality traits, communication style)
- Golden Rules (working principles)

**Interactive Questions** (use `AskUserQuestion`):

1. **Personality**:
   "How would you describe your personality at work?

   Consider:
   - Are you introverted or extroverted?
   - How do you recharge?
   - What energizes you at work?
   - What drains you?"

   **Format**: Open-ended text response

2. **Communication Preferences**:
   "What are your communication preferences?

   Consider:
   - Email vs Slack vs face-to-face
   - Response time expectations
   - When to schedule meetings vs async
   - How you like to receive urgent vs non-urgent info"

   **Format**: Open-ended text response

3. **Boundaries**:
   "What are your working boundaries?

   Consider:
   - Working hours and availability
   - Weekend/evening communication
   - When NOT to reach out
   - Personal time protection"

   **Format**: Open-ended text response

**Output**:
```markdown
## About Me

### Personality
[User's response about personality]

### Communication Preferences
[User's response about communication]

### Boundaries
[User's response about boundaries]
```

---

### Section 3: Operating Approach

**Purpose:** Document how you work day-to-day, including meetings, 1:1s, and cadence.

**Context to Reference:**
- Golden Rules (recurring practices, meeting protocols)
- Year Plan (quarterly planning cadence)
- Personal Operating Model (how you structure time)

**Interactive Questions** (use `AskUserQuestion`):

1. **1:1s and Meetings**:
   "How do you approach 1:1s and recurring meetings?

   Consider:
   - Frequency (weekly, biweekly)
   - Structure (shared doc, agenda format)
   - What you cover in 1:1s
   - Team meeting cadence and format"

   **Format**: Open-ended text response

2. **What to Loop You In On**:
   "What should people loop you in on vs handle independently?

   Consider:
   - Decision types that need your input
   - When to FYI vs ask for approval
   - What you want visibility into
   - What you trust others to own"

   **Format**: Open-ended text response

3. **Strategic and Planning Cadence**:
   "What's your strategic and planning rhythm?

   Consider:
   - Quarterly planning sessions
   - Monthly reviews
   - Annual planning
   - How you want to be involved"

   **Format**: Open-ended text response

**Output**:
```markdown
## Operating Approach

### 1:1s and Meetings
[User's response about 1:1s]

### What to Loop Me In On
[User's response about decision escalation]

### Strategic and Planning Cadence
[User's response about planning rhythm]
```

---

### Section 4: Management Style

**Purpose:** Describe how you manage people, make decisions, and give/receive feedback.

**Context to Reference:**
- Personal Operating Model (leadership style, decision-making approach)
- Golden Rules (management principles)

**Interactive Questions** (use `AskUserQuestion`):

1. **Management Approach**:
   "How would you describe your management style?

   Consider:
   - Collaborative, hands-on, or hands-off?
   - Micromanager or delegator?
   - How much autonomy do you give?
   - When do you get involved in details?"

   **Format**: Open-ended text response

2. **Decision-Making**:
   "How do you make decisions?

   Consider:
   - Data-driven vs intuitive?
   - Fast vs deliberate?
   - Solo vs collaborative?
   - What context do you need?"

   **Format**: Open-ended text response

3. **Feedback**:
   "How do you give and receive feedback?

   Consider:
   - How often do you give feedback?
   - Direct or indirect style?
   - How do you want to receive feedback?
   - Public vs private preferences"

   **Format**: Open-ended text response

4. **Principles and North Stars**:
   "What principles or North Stars guide your work?

   (I'll reference your Golden Rules here, but add any others)"

   **Format**: Open-ended text response

**Output**:
```markdown
## Management Style

### How I Manage
[User's response about management approach]

### Decision-Making
[User's response about decisions]

### Feedback
[User's response about feedback]

### Principles and North Stars

**Golden Rules** (from Notion):
[Reference Golden Rules from Notion]

**Additional Principles**:
[User's additional principles]
```

---

### Section 5: Supporting You and Your Team

**Purpose:** Set expectations for career discussions, development, and goals.

**Context to Reference:**
- Year Plan (OKRs, development goals)
- Personal Operating Model (growth areas)

**Interactive Questions** (use `AskUserQuestion`):

1. **Career and Development Discussions**:
   "How do you approach career and development conversations?

   Consider:
   - How often do you discuss career goals?
   - What format (dedicated session, ongoing)?
   - What kind of support do you offer?
   - How do you track development?"

   **Format**: Open-ended text response

2. **Goals and Progress**:
   "How do you track goals and check on progress?

   Consider:
   - Goal-setting cadence (quarterly, annual)
   - How you measure progress
   - Accountability approach
   - Adjustment process"

   **Format**: Open-ended text response

3. **Inclusion in Work**:
   "How do you like to be included in your team's work?

   Consider:
   - Materials you want to see
   - Forums you want to attend
   - Work in progress vs final review
   - How to celebrate wins"

   **Format**: Open-ended text response

**Output**:
```markdown
## Supporting You and Your Team

### Career and Development
[User's response about career discussions]

### Goals and Progress
[User's response about tracking]

### How to Include Me
[User's response about involvement]
```

---

### Section 6: Pitfalls and Working Around Them

**Purpose:** Share your known weaknesses and how others can work around them.

**Context to Reference:**
- Personal Operating Model (weaknesses, blind spots)
- Quarterly Logs (patterns of struggle)

**Interactive Question** (use `AskUserQuestion`):

"What are your known pitfalls and how can people work around them?

Consider:
- Weaknesses from your Personal Operating Model
- Patterns that cause problems
- What you struggle with
- How others can help compensate

Be honest—this helps people work with you effectively."

**Format**: Open-ended text response

**Output**:
```markdown
## Pitfalls and Working Around Them

**Known Weaknesses** (from Personal Operating Model):
[Reference weaknesses from POM]

**How to Work Around Them**:
[User's response about compensating strategies]
```

---

### Section 7: Personal Touch

**Purpose:** Add personality and humanity to the document.

**Interactive Question** (use `AskUserQuestion`):

"Finally, what personal touch do you want to add?

This could be:
- What makes work fun for you (like Clare's 'good craic')
- A quirk people should know about
- What gets you up in the morning
- What you value beyond the mechanics

Remember: You spend a lot of waking hours at work—what makes those hours meaningful?"

**Format**: Open-ended text response

**Output**:
```markdown
## More About Working with Me

[User's personal touch]

---

*Last updated: [Current Date]*
*This document reflects how I work as of [Quarter/Year]. I'll update it as I evolve.*
```

---

### Step 8: Compile & Save to Notion

**Process**:

1. **Compile Full "Working with Me" Document**:
   Combine all sections in this order:
   - My Role
   - About Me (Personality, Communication, Boundaries)
   - Operating Approach (1:1s, Loop-ins, Planning Cadence)
   - Management Style (How I Manage, Decision-Making, Feedback, Principles)
   - Supporting You and Your Team (Career, Goals, Inclusion)
   - Pitfalls and Working Around Them
   - More About Working with Me (Personal Touch)
   - Footer (Last updated date)

2. **Show Preview to User**:
   Display the complete document for user approval.

3. **Ask for Confirmation**:
   ```markdown
   I've compiled your "Working with Me" document.

   Should I save this to Notion under Resources? (Yes/No)

   This will create a new page called "Working with me" under:
   https://www.notion.so/Your-Resources-Page
   ```

4. **If Yes, Create New Notion Page**:
   - Use `mcp__notion__notion-create-pages` to create new page:
     - Parent: Resources page (https://www.notion.so/Your-Resources-Page)
     - Title: "Working with me"
     - Content: Full compiled document in Notion-flavored Markdown

5. **Confirm Completion**:
   ```markdown
   ✅ "Working with Me" document saved to Notion!

   📄 [Link to new page]

   **Next Steps**:
   - Review and refine as needed
   - Share with new colleagues, partners, clients
   - Update quarterly or when your role/style changes
   - Reference during onboarding conversations
   ```

---

## Important Notes

- **Be Honest**: This document only works if it's truthful about your style and pitfalls
- **User Control**: Always confirm before creating Notion page
- **Reference Context**: Pull from POM, Golden Rules, Year Plan throughout
- **Personality Matters**: The personal touch (Section 7) makes this human and relatable
- **Keep Updated**: Suggest updating quarterly or when role changes significantly

## Error Handling

- If Notion pages don't load, ask user to verify URLs
- If user gets stuck on a question, offer examples or skip
- If user wants to revise a section, allow editing before final save
- Always save progress if user wants to pause

## Success Criteria

A successful "Working with Me" document should:
1. Be honest about style, preferences, and pitfalls
2. Include specific examples (not generic statements)
3. Reference Golden Rules and Personal Operating Model
4. Have personality (personal touch at the end)
5. Be actionable (people know what to do/not do)
6. Be shareable (ready to send to new colleagues)

---

## Examples of Strong vs Weak Content

### ✅ Strong Example (Specific, Honest, Actionable):

**Communication Preferences**:
"I read email fast but hate writing long responses due to carpal tunnel. I'll read every email within 18 hours but won't always respond—assume I read it. If you need a response, use 'RESPONSE NEEDED' in subject or ping me on Slack. For FYIs, write 'FYI' in subject and I'll know no response needed."

### ❌ Weak Example (Generic, Vague):

**Communication Preferences**:
"I prefer email for most communication. I try to respond quickly. Let me know if something is urgent."

**Why it's weak**: Doesn't specify timing, doesn't explain what "quickly" means, no guidance on urgent vs non-urgent.

---

### ✅ Strong Example (Honest about Pitfalls):

**Pitfalls and Working Around Them**:
"I say yes too often and overcommit my time. If you see my calendar filling up with low-value meetings, call me out. I also tend to jump into details when I should stay strategic—remind me to delegate when you see this happening."

### ❌ Weak Example (Not Honest):

**Pitfalls and Working Around Them**:
"I'm very organized and disciplined. Sometimes I work too hard."

**Why it's weak**: Not a real weakness, sounds like humble-bragging, gives no actionable guidance.

---

## Template Inspiration

This skill is based on Clare Hughes Johnson's "Working with Me" template from *Scaling People*. The template integrates with your Personal Operating Model, Golden Rules, and Year Plan.

**Philosophy**: "Sharing what gets you up in the morning on a personal level can be as important as the mechanics of working together."

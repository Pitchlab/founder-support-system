---
description: Interactive Personal Operating Model (POM) creation - define your strengths, weaknesses, pitfalls, decision system, and execution playbook. Use when user mentions "personal operating model", "create POM", "operating model", "my strengths and weaknesses", or wants to define how they work best.
allowed-tools: [SlashCommand, mcp__notion__*, AskUserQuestion, Bash(date:*)]
---

# Personal Operating Model: Interactive Self-Assessment

**Create a comprehensive operating model that describes how you create value, your strengths/weaknesses, failure patterns, and execution playbook.**

## Overview

This skill guides you through an interactive interview to create your Personal Operating Model (POM) - a living document that defines:
- How you create value (Core Loop)
- Your energy-positive strengths and unique edge
- Structural weaknesses and repeating pitfalls
- Decision system and operating constraints
- Energy rhythms and execution playbook

**Philosophy**: "Treat weaknesses as design constraints. The goal is not self-improvement theatre. The goal is a system that works."

**Speed**: 60-90 minutes
**Tone**: Analytical, honest, design-oriented
**Output**: Notion page update (config.notion.personalOperatingModel)

## Notion Integration

**Configuration:**
Notion page URLs are loaded in the following order (first found wins):
1. `.claude/config.md` or `CLAUDE.md` - Project-specific configuration (check working directory)
2. `.claude-plugin/config.json` - Plugin default configuration

**Reference Pages (configured in config files, fetch ONCE per session):**
- **Year Plan** (config.notion.yearPlan): Current year focus, OKRs, strategic themes
- **Golden Rules** (config.notion.goldenRules): Working principles
- **Founder Wisdom** (config.notion.founderWisdom): Patterns to emulate
- **Logbook** (config.notion.logbook, optional): Recent quarterly logs for pattern finding

**Output Page:**
- **Personal Operating Model** (config.notion.personalOperatingModel): POM output location

## Workflow

### Step 1: Context Gathering

**Load Configuration**:
```javascript
// Use Read tool to load Notion page URLs from config
// Try in order (first found wins):
// 1. .claude/config.md (check for notion.* URLs in markdown)
// 2. CLAUDE.md (check for notion.* URLs in markdown)
// 3. .claude-plugin/config.json (JSON format)
// Extract all config.notion.* URLs for use below
```

**Fetch context from Notion** (using URLs from config):
1. Year Plan (current year focus, OKRs, strategic themes)
2. Golden Rules (working principles)
3. Founder Wisdom (patterns to emulate)
4. Previous POM version (if exists)
5. Optional: Recent Quarterly Logs (for pattern finding)

**Analyze for patterns**:
- What strengths appear in Year Plan?
- What constraints show up in Golden Rules?
- What failure patterns appear in Quarterly Logs?
- What wisdom resonates from Founder Wisdom?

---

### Step 2: Interactive Interview (11 Sections)

**For each section**:
1. Present section purpose
2. Ask 3-5 deep interview questions (not fill-in-the-blank)
3. Listen to answers
4. Synthesize into template datapoints
5. Confirm synthesis before moving to next section

**Pacing**: This is 60-90 minutes. Don't rush. Depth > speed.

---

#### Section 1: Core Loop — How You Create Value

**Purpose**: Define your personal "value engine" as Input → Transformation → Output.

**Interview Questions** (ask using AskUserQuestion):

1. **Inputs**: "Think about the last 3 projects where you felt most in flow. What kinds of raw materials were you working with? (problems, data, people, situations, ideas)"

2. **Transformation**: "When you take that input, what do you actually DO to it? Not the deliverable, but the steps. Do you simplify? Frame? Systematize? Connect dots? Diagnose? What's your signature move?"

3. **Outputs**: "Which of your outputs have kept paying you back over time? What have you created that changed other people's decisions or created a durable asset?"

4. **Avoid**: "What kinds of inputs do people bring you that you CAN handle but really SHOULDN'T? What drains you even if you're good at it?"

**Synthesize into**:
- Inputs I'm best with: [list]
- Inputs I should avoid: [list]
- Transformation steps: [3-step sequence]
- Signature move: [one sentence]
- Outputs that compound: [list]
- Core Loop one-liner: "I transform [X] into [Y] by [Z], producing [W]."

---

#### Section 2: Strengths — Energy-Positive Capabilities

**Purpose**: Identify strengths that are BOTH high-performing AND energy-positive.

**Interview Questions**:

1. **Recognition**: "What do people consistently thank you for or come to you for help with? What compliments do you hear repeatedly?"

2. **Speed**: "What do you do significantly faster than your peers? Where do you see the answer while others are still figuring out the question?"

3. **Energy**: "What work feels easy to you but seems hard to others? What could you do all day without getting tired?"

4. **Context**: "Pick one of those strengths. In what contexts does it absolutely shine? When does it weaken or backfire?"

5. **Evidence**: "For your top strength, give me 2-3 concrete examples with outcomes. Not 'I'm good at X' but 'I did X, which resulted in Y'."

**Synthesize into** (repeat for top 3-5 strengths):
- Strength: [name]
- What I do better than most: [description]
- Why it works (mechanism): [explanation]
- Evidence: [2-3 examples with outcomes]
- Contexts where it shines: [list]
- Contexts where it weakens: [list]
- How to exploit it more: [strategy]

---

#### Section 3: Unique Strong Points — Your Asymmetric Edge

**Purpose**: Identify your rare combination that creates unfair advantage.

**Interview Questions**:

1. **Combination**: "What's your unusual combination of skills or experiences? Most people have A or B, but you have both A AND B. What is that for you?"

2. **Domain Bridging**: "What do you know deeply that few people around you know? What can you connect across domains that others can't?"

3. **Context Dominance**: "In which specific contexts do you absolutely dominate? What kind of problems are 'made for you'?"

4. **Timing**: "At what stage or timing is your advantage highest? (0→1, scaling, crisis, research, turnaround, mature optimization)"

**Synthesize into**:
- Rare combination: [A + B + C]
- Unfair advantage this creates: [description]
- Best contexts: [industry/team size/maturity/constraints]
- Best timing: [stage]
- Problems that fit me: [types]
- I win when: [conditions]
- I lose when: [conditions]

---

#### Section 4: Weaknesses — Structural Limitations

**Purpose**: Treat weaknesses as design constraints, not character flaws.

**Interview Questions**:

1. **Categorize**: "Think about your weaknesses. Which are skill gaps you could train? Which are energy drains you should avoid? Which are blind spots you must design around?"

2. **Consistent Underperformance**: "What consistently underperforms no matter how hard you try? Where do you reliably fall short?"

3. **Trigger Conditions**: "When do these weaknesses show up most? What situations activate them?"

4. **Mitigation**: "For your biggest weakness, what's the best mitigation strategy? (Outsource / automate / partner / checklist / timebox / avoid entirely)"

5. **Good Enough**: "What's your 'good enough' standard for this weakness? When is it OK to be mediocre here?"

**Synthesize into** (repeat for top 3-6 weaknesses):
- Weakness: [name]
- What consistently underperforms: [description]
- Trigger conditions: [when it shows up]
- Cost when ignored: [impact]
- Best mitigation strategy: [approach]
- Environmental fix: [change context, not self]
- "Good enough" standard: [minimum bar]

**Categorize**:
- Skill gaps: [trainable]
- Energy drains: [should avoid]
- Blind spots: [must design around]

---

#### Section 5: Pitfalls — Repeating Failure Patterns

**Purpose**: Identify failure patterns that require rules and interrupts, not motivation.

**Interview Questions**:

1. **Pattern Recognition**: "What mistake have you made 3+ times in your career? What's your 'here we go again' moment?"

2. **Over-Investment**: "Where do you consistently over-invest time, money, or energy for diminishing returns?"

3. **Avoidance**: "What do you consistently avoid that you KNOW matters? What important thing do you procrastinate on?"

4. **Early Warnings**: "For your biggest pitfall, what are the early warning signals? What's observable BEFORE you fall into it?"

5. **Rationalization**: "When you're falling into this pitfall, what do you tell yourself to justify it? What's your typical excuse?"

**Synthesize into** (repeat for 3-5 pitfalls):
- Pitfall: [name + "(3x)" marker]
- Pattern (what I do): [description]
- Early warning signals: [observable signs]
- Typical rationalization: [what I tell myself]
- Damage if unchecked: [impact]
- Interrupt rule: [hard rule, not advice]
- Recovery protocol: [what to do after]

---

#### Section 6: Decision System — How You Should Decide

**Purpose**: Define decision defaults that beat deliberation.

**Interview Questions**:

1. **Speed Default**: "Are you naturally a fast decider or a slow/careful decider? Where does this serve you? Where does it hurt you?"

2. **Confidence Threshold**: "What confidence level do you need to act? 60%? 80%? 95%? Does this vary by decision type?"

3. **Reversibility**: "How aware are you of reversible vs irreversible decisions? Do you treat them the same or differently?"

4. **Opportunities**: "When a new opportunity comes (project, partnership, product idea), what's your decision rule? What minimum info do you need?"

5. **Success Metrics**: "How do you know if something is working? What are your leading indicators vs lagging indicators?"

**Synthesize into**:

**Decision Defaults**:
- Default speed: [fast/medium/slow]
- Default confidence threshold: [60%/80%/95%]
- What I tend to overdo: [speed or caution]

**Decision Rules by Type**:

A) **Opportunities** (new projects, partnerships, ideas):
- Decision rule: [criteria]
- Minimum info required: [list]
- Kill-switch condition: [when to stop]
- Timebox for exploration: [duration]

B) **Commitments** (long-term contracts, hires, big bets):
- Decision rule: [criteria]
- Required confidence: [%]
- Pre-mortem question: [how does this fail?]
- Exit plan: [escape hatch]

C) **Daily Execution** (what to do today):
- Decision rule: [default]
- "If unsure, do this" default: [action]
- What you never do first: [avoid]

**Evaluation Function**:
- Leading indicators: [list]
- Lagging indicators: [list]
- Non-negotiable indicators: [list]

---

#### Section 7: Operating Constraints — Your Guardrails

**Purpose**: Constraints protect long-term leverage from short-term motion.

**Interview Questions**:

1. **Non-Negotiables**: "What will you NOT do, even if it pays well? What crosses a line for you?"

2. **Toxic Contexts**: "What types of work degrade your output? What clients or contexts are poison for you?"

3. **Capacity Limits**: "What's your max parallel projects before quality drops? Max weekly meetings? Max deep work themes per week?"

4. **Default No**: "What are the 3 criteria where, if ANY are true, the answer is automatically no?"

**Synthesize into**:

**Non-Negotiables**:
- I do not accept: [list]
- I do not work in: [contexts]
- I do not build: [types]

**Capacity Constraints**:
- Max parallel projects: [number]
- Max weekly meetings: [number]
- Max deep work themes per week: [number]

**Default "No" Criteria**:
- If any of these are true, answer is no:
  1. [criterion]
  2. [criterion]
  3. [criterion]

---

#### Section 8: Energy & Rhythm — Cognitive Weather Map

**Purpose**: Design your schedule around your brain, not obligations.

**Interview Questions**:

1. **Peak Windows**: "When during the day do you do your BEST thinking? When are you best at execution? When are you socially strongest?"

2. **Low Energy**: "When you're in a low-energy state, what tasks are safe? What tasks are dangerous?"

3. **Burnout Indicators**: "What are your first 3 warning signs of burnout? What happens before you crash?"

4. **Recovery**: "What reliably restores you? What's your minimum viable recovery protocol?"

**Synthesize into**:

**Peak Windows**:
- Peak deep work window: [time]
- Peak execution window: [time]
- Peak social window: [time]

**Low-Energy Protocol**:
- Low-energy safe tasks: [list]
- Low-energy danger tasks: [list]

**Burnout Indicators & Recovery**:
- Warning signs:
  1. [signal]
  2. [signal]
  3. [signal]
- Recovery protocol (minimum viable): [steps]

---

#### Section 9: Environment Design — Make Right Behavior Easier

**Purpose**: Redesign surroundings so good path is default path.

**Interview Questions**:

1. **Friction**: "Where do you need MORE friction to stop bad habits? Where do you need LESS friction to ship more?"

2. **Tools**: "What tools genuinely amplify you (not just trendy)? What tools create drag?"

3. **People**: "What archetypes of people do you work best with? What kind of people drain you?"

4. **Structures**: "What structures keep you honest? (deadlines, public commitments, peer review, dashboards)"

**Synthesize into**:

**Friction & Leverage**:
- Add friction to: [habits to slow]
- Remove friction from: [habits to speed]

**Tools, People, Structures**:
- Tools that amplify you: [list]
- People archetypes you work best with: [types]
- Structures that keep you honest: [mechanisms]

---

#### Section 10: Execution Playbook — How You Ship

**Purpose**: Define default execution pattern for repeatable outcomes.

**Interview Questions**:

1. **Phases**: "Walk me through how you move from idea to shipped. What are your phases?"

2. **Skips**: "What do you consistently skip that you shouldn't? What causes delays?"

3. **Overdoing**: "What do you overdo? Where do you over-engineer or over-polish?"

4. **Definition of Done**: "How do you define 'done'? What's your minimum quality bar? What's your shipping cadence?"

5. **Anti-Stall**: "When progress stalls, what do you do? What's your go-to move to unstick yourself?"

**Synthesize into**:

**Default Project Phases**:
1. [phase]
2. [phase]
3. [phase]
4. [phase]
5. [phase]

**Definition of Done**:
- "Done" means (observable outcomes): [criteria]
- Quality bar (minimum): [standard]
- Shipping cadence: [frequency]

**Anti-Stall Mechanisms**:
- If progress stalls, I do:
  1. [action]
  2. [action]
  3. [action]

---

#### Section 11: Experiments — Improve the Model, Not the Self

**Purpose**: Small experiments that change the system. One variable at a time.

**Interview Questions**:

1. **Clarity**: "What experiment would create 10x clarity in how you work?"

2. **Speed**: "What would create 2x shipping speed?"

3. **Pitfall Reduction**: "What would reduce your biggest pitfall?"

4. **Hypothesis**: "Pick one experiment. What's your hypothesis? What are you testing?"

5. **Metrics**: "How will you measure success? How will you know it failed?"

**Synthesize into** (1-3 experiments):

**Experiment: [name]**
- Hypothesis: [what you believe]
- Change (what you will do): [specific action]
- Duration: [timeframe]
- Success metric: [measure]
- Failure metric: [measure]
- Review date: [when to assess]

---

### Step 3: Final Synthesis & Review

**After all 11 sections**:

1. **Read back full compiled POM**
2. **Check for inconsistencies**:
   - Do strengths align with Core Loop?
   - Do pitfalls contradict decision rules?
   - Do constraints conflict with experiments?
3. **Ask follow-up questions** (AskUserQuestion) for clarity
4. **Tighten vague answers**
5. **Add examples where abstract**

---

### Step 4: Save to Notion

**Update POM page**: https://www.notion.so/Your-POM-Page

**Format**:
```markdown
# Personal Operating Model (POM)

*Last updated: [date]*

> Use this as a working document. Write short. Be concrete. Prefer examples over abstractions.

---

## 1) Core Loop — How You Create Value

[Section 1 synthesis]

---

## 2) Strengths — Energy-Positive Capabilities

[Section 2 synthesis]

---

[Continue for all 11 sections...]

---

## Appendix: Revision History

- [Date]: Created/Updated via planning-strategy:personal-operating-model
```

**Ask for confirmation** before saving (AskUserQuestion):
- "Ready to save this Personal Operating Model to Notion?"

**After saving**:
- Provide Notion URL
- Suggest next steps (quarterly review to update)

---

## Key Principles

### 1. Deep Questions, Not Templates
- Don't just ask "what are your strengths?"
- Ask "when do people thank you? What feels easy to you but hard to others?"
- Questions should YIELD insights, not just collect data

### 2. Synthesis Over Transcription
- Don't just record answers
- Analyze patterns
- Connect dots across sections
- Point out contradictions

### 3. Evidence Over Abstraction
- Push for concrete examples
- "I'm strategic" → "I did X strategic thing, which resulted in Y"
- Numbers, dates, names when possible

### 4. Design Mindset, Not Therapy
- Weaknesses are constraints to route around, not problems to fix
- Pitfalls need rules and interrupts, not motivation
- Environment design > willpower

### 5. Actionable, Not Aspirational
- "Be more organized" ❌
- "Use checklist for client onboarding" ✅

---

## Success Criteria

A successful POM session should:
1. ✅ Take 60-90 minutes of focused time
2. ✅ Include concrete examples (not generic statements)
3. ✅ Identify 3-5 strengths with evidence
4. ✅ Name 3-5 pitfalls with interrupt rules
5. ✅ Define decision defaults for opportunities, commitments, daily execution
6. ✅ Create 1-3 experiments to test
7. ✅ Reference Year Plan, Golden Rules, Founder Wisdom
8. ✅ Save to Notion POM page

---

## Anti-Patterns to Avoid

❌ **Don't**:
- Rush through sections
- Accept vague answers ("I'm good at strategy")
- Let user be overly positive (this isn't a resume)
- Skip evidence and examples
- Ignore contradictions between sections

✅ **Do**:
- Push for specificity
- Ask for evidence
- Point out tensions
- Connect to Year Plan and Golden Rules
- Synthesize patterns across sections
- Make it actionable

---

## Integration with Planning-Strategy

**POM feeds into**:
- Executive Coach (uses POM to understand strengths/weaknesses)
- Working with Me (pulls from POM for pitfalls)
- Year Plan (aligns OKRs with strengths, avoids pitfalls)
- Quarterly Review (updates POM based on observed patterns)

**POM is updated by**:
- Quarterly Review (new patterns observed)
- Year Plan (new strategic constraints)
- Daily coaching (when pitfalls are triggered)

**Cadence**:
- Create: Once (this session)
- Major update: Annually
- Light update: Quarterly (via quarterly review)
- Reference: Daily (coaches use it)

---

## Error Handling

- If Notion pages fail to load, proceed with general interview (no specific references)
- If user gives vague answers, ask follow-up for specificity
- If section is unclear, provide 2-3 examples to clarify
- If user is overwhelmed, suggest breaking into 2 sessions (Sections 1-6, then 7-11)

---

## Notes

- **Time**: 60-90 minutes total
- **Honesty Required**: This is not a resume or LinkedIn profile
- **Living Document**: Update quarterly via quarterly review
- **Design Tool**: Use to make decisions, route work, set constraints
- **Integration**: Feeds executive coach, working-with-me, year plan

**Philosophy**: "You're not optimizing yourself. You're designing a system that works."

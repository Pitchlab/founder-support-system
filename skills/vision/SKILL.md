---
description: Interactive vision and manifesto creation that pushes for bold, clear, philosophically grounded statements. Use when user mentions "vision", "manifesto", "update vision", "create vision", "what do I stand for", or wants to articulate their fundamental beliefs and direction.
allowed-tools: [SlashCommand, mcp__notion__*, AskUserQuestion, Bash(date:*), Read, Write]
---

# Vision: Interactive Manifesto Creation

**Push for substance. Reject bland business speak. Build a vision worth defending.**

## Overview

This skill guides you through creating a **bold, philosophically grounded vision and manifesto** that articulates what you stand for, why it matters, and what you refuse to compromise on.

**NOT generic corporate mission statements.**
**NOT ChatGPT business speak.**
**Clarity. Conviction. Edge.**

**Time**: 60-90 minutes of focused thinking
**Tone**: Provocative questions, sharp challenges, uncompromising standards
**Output**: Vision page in Notion with manifesto from the future

## Notion Integration

**Configuration:**
Notion page URLs are loaded in the following order (first found wins):
1. `.claude/config.md` or `CLAUDE.md` - Project-specific configuration (check working directory)
2. `.claude-plugin/config.json` - Plugin default configuration

Use the Read tool to load configuration at the start of the workflow.

**Output Page (configured in config.json):**
- **Vision** (config.notion.vision): Output page for vision and manifesto

**Reference Pages (configured in config.json):**
- **Year Plan** (config.notion.yearPlan): Strategic plan and OKRs
- **Personal Operating Model** (config.notion.personalOperatingModel): Strengths and weaknesses
- **Golden Rules** (config.notion.goldenRules): Non-negotiable principles

## Workflow

### Step 0: Setup & Context

1. **Load Configuration**:
   ```javascript
   // Use Read tool to load Notion page URLs from config
   // Read .claude-plugin/config.json
   // Extract config.notion.vision, config.notion.yearPlan, config.notion.personalOperatingModel,
   // config.notion.goldenRules
   // Use these URLs for all mcp__notion__notion-fetch calls below
   ```

2. **Fetch Current Vision** (if exists):
   - Read existing Vision page from Notion
   - Extract current themes, beliefs, non-negotiables
   - Identify what's working vs what's bland/generic

2. **Fetch Reference Context**:
   - Year Plan (strategic direction, OKRs)
   - Personal Operating Model (strengths, nature)
   - Golden Rules (non-negotiables)

3. **Set Expectations**:
   ```
   We're building a vision that passes the Kevin Kelly / Steve Jobs test:
   - Does it have CONVICTION?
   - Does it challenge the default?
   - Would you defend it in a room full of skeptics?

   I will push back on:
   - Generic business speak
   - Vague platitudes
   - "We help people X" without the WHY
   - Anything that sounds like ChatGPT wrote it

   This takes time. Block 60-90 minutes.
   Ready?
   ```

---

### Section 1: The Provocative Questions

**Purpose**: Force clarity on what actually matters.

Use `AskUserQuestion` to ask **all 5 questions** (one question block, 5 separate questions):

1. **Where do humans still matter most when agents become competent?**
   - Not tasks. Not roles.
   - Judgment, intent, framing, responsibility — or something else?

2. **What kind of environment do you need to become dangerously good?**
   - Not comfortable. Not admiring.
   - Who do you want to be surrounded by so you're no longer the obvious expert?

3. **What must never be outsourced to machines, even if it could be?**
   - This is your ethical and strategic line.
   - Cross it, and the whole narrative collapses.

4. **What signal do you want people to associate with your name before your company?**
   - Builder? Architect? Interpreter? Challenger? Trailblazer? Prophet?
   - You can only lead with one.

5. **If you look back in 15 years, what would make this phase feel inevitable?**
   - Not successful.
   - Necessary. Correct. True to your nature.

**Format**: Use text input for depth (not multiple choice).

---

### Section 2: Challenge the Answers

**Purpose**: Reject generic, push for specificity.

For each answer, analyze:
- Is it specific or vague?
- Is it defensible or platitude?
- Does it have edge or is it safe?

**If answer is generic/bland**:
```
⚠️ This feels like business speak.

"[Quote their answer]"

Test: Would your competitor say this too? If yes, it's not a vision—it's a category description.

Try again. What makes THIS true for you that isn't true for everyone else?
```

**If answer is sharp**:
```
✓ This has teeth. Let's use it.
```

Use `AskUserQuestion` to iterate on weak answers (max 2 rounds per question).

---

### Section 3: Extract Core Beliefs & Themes

**Purpose**: Distill answers into 3-5 core beliefs and mission themes.

Based on answers, propose:

**A. Core Beliefs** (philosophical foundation):

**Core Belief 1**: [One-sentence belief]
- Implication: [What this means in practice]
- Line in the sand: [What you refuse to do because of this]

**Example**:
```
Core Belief 1: Humans are the source of meaning, not machines.
- Implication: AI generates output. Only humans decide what matters.
- Line in the sand: Never automate decisions I can't justify or audit.
```

**B. Mission Themes** (how beliefs show up daily):

For each core belief, identify how it manifests in everyday work:
- What does this belief look like in practice?
- How does it shape what/how/why you work?
- What evidence would prove you're living this theme?

**Example**:
```
Theme: Intent-First Design
- Shows up as: Every system starts with "what human intent does this serve?"
- Evidence: Design docs have explicit "intent preservation" section
- Practice: No feature ships without answering "does this amplify or replace human judgment?"
```

Present beliefs and themes using `AskUserQuestion`:
- "Do these capture your core beliefs and how they manifest?"
- "What's missing or wrong?"

Iterate until user confirms.

---

### Section 4: Draft the Manifesto

**Purpose**: Write from the future, with conviction.

**Style Guidelines**:
- Write as if 15 years have passed and you're looking back
- Start with "From here, I can see how it happened..."
- Use **"I"** not "we" (personal vision)
- Be philosophical but grounded
- Have form AND function (not just bullet points)
- Channel Kevin Kelly / Steve Jobs / clear thinkers
- No generic business speak
- No excessive bold formatting (let words do the work)

**Structure** (flexible, not rigid):

1. **Opening**: From the future, set the stage
   - What inflection point did you see?
   - What bet did most people miss?

2. **The Fork in the Road**: What choice did you make differently?
   - What path did others take?
   - What harder path did you choose?

3. **Core Beliefs** (3-5 beliefs as paragraphs, not list):
   - Weave beliefs into narrative
   - Each belief = philosophical claim + practical implication
   - Show the cost of violating each belief

4. **The Work**: What does this look like in practice?
   - Environment needed
   - Standards maintained
   - Lines never crossed

5. **The Bet**: What are you building toward?
   - Not prediction, but commitment
   - What future are you creating?

6. **Closing**: Why this matters
   - One-line summary of stance
   - The hill you'll die on

**Length**: 600-1000 words (enough for substance, not fluff)

---

### Section 5: Style Check

**Purpose**: Ensure it's sharp, not bland.

Run manifesto through these tests:

**Test 1: The Competitor Test**
- Could your competitor say this? If yes → too generic

**Test 2: The Conviction Test**
- Would you defend this in a room full of skeptics? If no → too safe

**Test 3: The ChatGPT Test**
- Does it sound like AI wrote it? If yes → rewrite with edge

**Test 4: The Bold Formatting Test**
- Remove all **bold** and *italics*. Does it still hit? If no → words are weak

**Test 5: The One-Line Test**
- Can you summarize the whole vision in one sentence? If no → unclear

Present test results using `AskUserQuestion`:
- "The manifesto fails [X] tests. Here's why: [analysis]"
- "Revise or proceed anyway?"

If tests fail, iterate on manifesto (max 2 rounds).

---

### Section 6: Refine & Polish

**Purpose**: Make every word count.

**Refinement Process**:

1. **Cut ruthlessly**:
   - Remove hedging language ("somewhat", "kind of", "perhaps")
   - Remove redundancy
   - Remove paragraphs that don't advance the argument

2. **Strengthen claims**:
   - Replace weak verbs with strong ones
   - Replace vague nouns with specific ones
   - Add concrete examples where abstract

3. **Check rhythm**:
   - Vary sentence length
   - Use short sentences for impact
   - Use longer sentences for complexity

4. **Final read**:
   - Read aloud mentally
   - Does it flow?
   - Does it build?
   - Does it land?

Present refined version using `AskUserQuestion`:
- "Here's the polished manifesto. Approve or request changes?"

---

### Section 7: Compile & Save to Notion

**Purpose**: Archive the vision for reference.

**Notion Page Structure**:

```markdown
# Vision

*Updated: [Date]*

---

## Manifesto

[Full manifesto text]

---

## Core Beliefs

1. **[Belief 1]**
   - Implication: [What this means]
   - Line in the sand: [What you refuse]

2. **[Belief 2]**
   ...

---

## One-Line Summary

[One sentence that captures everything]

---

## Provocation Questions (Archive)

<details>
<summary>Questions that shaped this vision</summary>

1. Where do humans still matter most when agents become competent?
   - Answer: [Your answer]

2. What kind of environment do you need to become dangerously good?
   - Answer: [Your answer]

3. What must never be outsourced to machines, even if it could be?
   - Answer: [Your answer]

4. What signal do you want people to associate with your name?
   - Answer: [Your answer]

5. If you look back in 15 years, what would make this phase feel inevitable?
   - Answer: [Your answer]

</details>

---

## Archive

<details>
<summary>Previous Versions</summary>

### [Previous Date]
[Previous manifesto if exists]

</details>
```

**Before Saving**:
- Use `AskUserQuestion` to confirm: "Save this vision to Notion?"
- If yes, use `mcp__notion__notion-update-page` with `command: replace_content`
- Archive old version at bottom if one exists

**After Saving**:
```
✓ Vision saved to Notion

Your manifesto is now your north star. Reference it when:
- Making strategic decisions
- Saying no to opportunities
- Explaining what you stand for
- Feeling lost or drifting

The best visions are living documents. Revisit yearly or when fundamental beliefs shift.
```

---

## Key Principles

### 1. Push, Don't Coddle
- Challenge generic answers immediately
- Make user defend vague claims
- Reject business speak without mercy

### 2. Substance Over Format
- Prioritize WHAT is said over HOW it looks
- Form follows function (but both matter)
- No hiding behind bold formatting

### 3. Clarity Is Kindness
- Vague visions are useless
- Force specificity even if uncomfortable
- Better to have 3 clear beliefs than 10 vague ones

### 4. Write From the Future
- Not "we will..." but "from here, I can see..."
- Inevitability, not aspiration
- Describe what happened, not what might

### 5. Personal, Not Corporate
- Use "I" not "we"
- This is YOUR vision, not a company's
- Defend YOUR beliefs, not market positioning

---

## Anti-Patterns to Avoid

❌ **Don't**:
- Accept first-draft generic answers
- Let user hide behind business jargon
- Write manifestos that sound like everyone else's
- Use excessive bold/italics to compensate for weak words
- Create visions that aren't defensible
- Skip the challenge/refinement rounds

✅ **Do**:
- Push for specificity and edge
- Challenge vague claims immediately
- Reference Kevin Kelly / Steve Jobs / clear thinkers as standards
- Iterate until it passes all 5 tests
- Make user defend their beliefs
- Ensure vision is clear enough to guide decisions

---

## Success Criteria

A successful vision should:
1. ✅ Pass all 5 style tests (competitor, conviction, ChatGPT, bold, one-line)
2. ✅ Be specific enough that you'd reject opportunities based on it
3. ✅ Have 3-5 core beliefs with clear lines in the sand
4. ✅ Be defensible in a room full of skeptics
5. ✅ Feel inevitable when you read it (not aspirational)
6. ✅ Take 60-90 minutes of hard thinking
7. ✅ Make you slightly uncomfortable (if it's too safe, it's not a vision)

---

## Example Opening (Style Reference)

```
From here, I can see how it happened.

The machines learned to act. They learned to plan, to delegate, to correct
themselves mid-stride. And for a strange, vertiginous decade, humanity stood
at a threshold most people couldn't name: the moment when doing became cheap
and meaning became the only scarce resource left.

Most of the industry didn't see it that way. They saw labor costs. They saw
scale. They saw the logical extension of automation into every crevice of
human effort—and they called it progress.

I took a different bet...
```

**Why this works**:
- Sets scene from the future
- Identifies the inflection point
- Shows the fork (most people vs you)
- Creates tension
- Promises a stance

Use this as reference for tone and structure.

---

## Error Handling

- If user gives up or rushes, remind: "Vague visions are worse than no vision. Take the time."
- If answers are all generic after 2 rounds, pause and ask: "Do you actually believe something different, or are we just wordsmithing?"
- If manifesto fails all 5 tests, don't save to Notion. Iterate.
- If user can't articulate core beliefs, suggest: "Come back when you've done more work. Vision requires conviction."

## Final Note

**The goal is not to create a pretty document.**
**The goal is to force clarity on what you stand for—so you can defend it, act on it, and build toward it.**

If the process doesn't make you uncomfortable, you're not pushing hard enough.

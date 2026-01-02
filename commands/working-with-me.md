---
description: Interactive creation of a 'Working with Me' document for colleagues, partners, and clients
allowed-tools: [Skill]
---

# Working with Me Command

Create a comprehensive "Working with Me" document that serves as a user manual for how to work with you effectively.

## Purpose

This command invokes the `working-with-me` skill to interactively create a personal user manual covering:
- Your role and goals
- Personality and communication preferences
- Operating approach (meetings, 1:1s, cadence)
- Management style and decision-making
- How you support your team
- Known pitfalls and how to work around them
- Personal touch that makes work meaningful

**When to use**: When onboarding new colleagues, starting partnerships, or wanting to clearly document your work style.

## Usage

```bash
/planning-strategy:working-with-me
```

**No parameters needed** - the skill guides you through an interactive interview.

## How It Works

This command invokes the `working-with-me` skill, which:

1. **Fetches context** from Notion:
   - Personal Operating Model (strengths, weaknesses)
   - Golden Rules (working principles)
   - Year Plan (current role, goals)
   - Quarterly Logs (for patterns)

2. **Guides you through 7 sections**:
   - My Role
   - About Me (personality, communication, boundaries)
   - Operating Approach (1:1s, decision escalation, planning cadence)
   - Management Style (how you manage, decide, give feedback)
   - Supporting You and Your Team (career discussions, goals, inclusion)
   - Pitfalls and Working Around Them (honest weaknesses)
   - Personal Touch (what makes work fun)

3. **Compiles comprehensive document**

4. **Saves to Notion** as new page under Resources

## Example Session

```bash
/planning-strategy:working-with-me

Claude:
I've reviewed your Personal Operating Model, Golden Rules, and Year Plan.

I'll guide you through creating your "Working with Me" document covering:
- Your role and goals
- Personality and communication preferences
- Operating approach and cadence
- Management style
- How you support your team

This will take about 20-30 minutes.

**Section 1: My Role**

What is your role and what are your primary goals?

Consider:
- Official title and what it means in practice
- Core responsibilities (what you own)
- Primary goals for 2026
- Who you serve (team, clients, partners)

User: "I'm a Strategy Consultant focused on AI agents and
multi-agent systems. My goals for 2026 are to hit €100K revenue,
establish thought leadership, and become expert in orchestration..."

Claude:
**Section 2: About Me - Personality**

How would you describe your personality at work?

[Continues through all 7 sections...]

Claude:
✅ "Working with Me" document saved to Notion!

📄 https://www.notion.so/Working-with-me-[new-id]

**Next Steps**:
- Review and refine as needed
- Share with new colleagues, partners, clients
- Update quarterly or when your role/style changes
```

## What You'll Get

**Structured "Working with Me" Document** covering:

### 1. My Role
- Your title and responsibilities
- Primary goals for the year
- Who you serve

### 2. About Me
- **Personality**: Work style, energy sources/drains
- **Communication Preferences**: Email/Slack/face-to-face, response times
- **Boundaries**: Working hours, availability, personal time

### 3. Operating Approach
- **1:1s and Meetings**: Frequency, structure, format
- **What to Loop Me In On**: Decision types, FYI vs approval
- **Strategic Cadence**: Quarterly planning, monthly reviews

### 4. Management Style
- **How I Manage**: Collaborative, hands-on, or hands-off
- **Decision-Making**: Data-driven or intuitive, fast or deliberate
- **Feedback**: How you give and receive it
- **Principles**: Golden Rules + additional North Stars

### 5. Supporting You and Your Team
- **Career and Development**: Discussion cadence, support offered
- **Goals and Progress**: Tracking approach, accountability
- **How to Include Me**: Materials to see, forums to attend

### 6. Pitfalls and Working Around Them
- Known weaknesses from Personal Operating Model
- Patterns that cause problems
- How others can compensate

### 7. More About Working with Me
- Personal touch (what makes work fun/meaningful)
- Quirks people should know
- What gets you up in the morning

**Saved to**: https://www.notion.so/Your-Resources-Page

## Tips for Best Results

1. **Be Brutally Honest**: This document only works if it's truthful
   - Don't hide weaknesses—they're helpful to know
   - Be specific about preferences (not "I like email" but "I read email within 18 hours")
   - Share real pitfalls people can work around

2. **Use Concrete Examples**:
   - ✅ "I dislike being caught last-minute with big work efforts—give me 1 week notice for anything requiring >4 hours"
   - ❌ "I like to plan ahead"

3. **Add Personality**:
   - Share what makes work fun for you
   - Include quirks (like Clare's "good craic")
   - Make it human, not just mechanics

4. **Reference Your Context**:
   - The skill pulls from your POM, Golden Rules, Year Plan
   - Build on that context rather than repeating it
   - Add nuance and specifics

5. **Make It Actionable**:
   - People should know what to do/not do after reading
   - Clear guidance on communication, meetings, decisions
   - Specific escalation criteria

## When to Use This

**Good Times to Create/Update**:
- ✅ Starting a new role or major pivot
- ✅ Onboarding new team members
- ✅ Beginning new partnerships or client relationships
- ✅ After quarterly review (patterns have changed)
- ✅ When you notice recurring friction with how people work with you

**When to Share**:
- New colleagues joining your team
- Partners starting a collaboration
- Clients for long-term engagements
- Anyone who will work closely with you

## Integration with Workflow

**Typical Flow**:

1. **Create Initial Version**: Use `/planning-strategy:working-with-me`
2. **Review Quarterly**: Update when patterns change
3. **Share Proactively**: Send to new colleagues/partners
4. **Reference in Onboarding**: Use as conversation starter

**Related Commands**:
- `/planning-strategy:quarterly-review` - Identify patterns to update in Working with Me
- `/planning-strategy:year-plan` - Sets role/goals context
- `/planning-strategy:vision` - Defines principles and values

## Success Criteria

A successful "Working with Me" document should:
1. ✅ Be honest about style, preferences, and pitfalls
2. ✅ Include specific examples (not generic statements)
3. ✅ Reference Golden Rules and Personal Operating Model
4. ✅ Have personality (personal touch at the end)
5. ✅ Be actionable (people know what to do/not do)
6. ✅ Be shareable (ready to send to new colleagues)

## Notes

- **Time**: 20-30 minutes of focused attention
- **Honesty Required**: Generic answers won't help anyone
- **Living Document**: Update quarterly or when role/style changes
- **Based on**: Clare Hughes Johnson's template from *Scaling People*
- **Integration**: Pulls context from POM, Golden Rules, Year Plan, Quarterly Logs

**Philosophy**: "Sharing what gets you up in the morning on a personal level can be as important as the mechanics of working together."

## Related Commands

- `/planning-strategy:vision` - Define your core beliefs and principles
- `/planning-strategy:year-plan` - Set your role and goals context
- `/planning-strategy:quarterly-review` - Identify patterns and changes to update

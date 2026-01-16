# Meeting Intelligence Agent - Prompt Templates

Ready-to-use prompts for different meeting workflow stages. Customize the bracketed sections for your specific needs.

---

## 1. Pre-Meeting Context Brief

### Prompt Template

```
I have a meeting coming up and need to prepare efficiently.

**Meeting Details:**
- Title: [Meeting Title]
- Attendees: [List of attendees and their roles]
- Program/Project: [Program name]
- Type: [Daily sync/Weekly review/Stakeholder update/Planning/etc.]

**Context Sources:**
- Last meeting notes: [Paste or reference last meeting summary]
- Current sprint/milestone: [Key objectives or current focus]
- Open risks/blockers: [Known issues or concerns]
- Recent updates: [Any relevant changes since last sync]

**Generate a pre-meeting brief that includes:**
1. Key topics likely to be discussed (based on program state)
2. Decisions that need to be made
3. Questions I should ask or be prepared to answer
4. Important context each attendee should know
5. Suggested agenda items (3-5 bullets)

Keep it concise - under 10 bullets total. Focus on what I need to know RIGHT NOW to be effective in this meeting.
```

### Example Usage

```
I have a meeting coming up and need to prepare efficiently.

**Meeting Details:**
- Title: Payment Platform Q1 Planning
- Attendees: Engineering Lead (Sarah), Product Manager (Mike), Security Lead (James)
- Program/Project: Payment Platform Modernization
- Type: Quarterly Planning

**Context Sources:**
- Last meeting notes: Discussed migration timeline concerns, security audit findings
- Current sprint/milestone: Completing Phase 1 (read-only API), starting Phase 2 planning
- Open risks/blockers: Database performance under load, third-party vendor integration delays
- Recent updates: Security audit completed with 3 high-priority findings

**Generate a pre-meeting brief...**
```

---

## 2. Meeting Summary Generator

### Prompt Template

```
Transform these meeting notes into a structured summary suitable for stakeholder distribution.

**Meeting Context:**
- Title: [Meeting Title]
- Date: [Date]
- Attendees: [List]
- Duration: [Time]

**Raw Notes:**
[Paste your meeting notes here - bullet points, incomplete sentences, timestamps, anything]

**Generate a summary with:**
1. **Overview** - 2-3 sentence summary of what was covered
2. **Key Decisions** - Numbered list of decisions made with brief context
3. **Action Items** - Checklist format with owner and due date
   - [ ] Action - Owner: Name - Due: Date
4. **Open Questions** - Issues requiring follow-up or more discussion
5. **Next Steps** - What happens next, next meeting date if applicable

**Tone:** Professional but conversational, suitable for sending to technical stakeholders.

**Additional Instructions:**
- Flag any action items without clear owners
- Highlight any blockers or risks mentioned
- Preserve technical details where relevant
```

### Example Usage

```
Transform these meeting notes into a structured summary suitable for stakeholder distribution.

**Meeting Context:**
- Title: API Migration Sync
- Date: January 14, 2026
- Attendees: Sarah (Eng), Mike (PM), Alex (TPM)
- Duration: 30 min

**Raw Notes:**
- discussed timeline for phase 2
- sarah raised concern about testing coverage, need more QA resources
- mike wants to demo to execs next week - decided feb 1st better
- action: alex schedule exec demo for feb 1
- action: sarah get estimate for additional QA support by friday
- question: do we need compliance review before phase 2? mike checking
- blocked on vendor API docs, mike escalating to their PM
- next sync: same time next week

**Generate a summary with:**
...
```

---

## 3. Action Item Extractor

### Prompt Template

```
Extract all action items from these meeting notes and create a structured tracking list.

**Meeting:** [Meeting Title] - [Date]

**Notes:**
[Paste meeting notes or transcript]

**Extract and format as:**

### Action Items

**Critical Path (Blockers or Dependencies):**
- [ ] [Action description] - Owner: [Name] - Due: [Date] - Status: [Not Started/In Progress/Blocked]

**This Week:**
- [ ] [Action description] - Owner: [Name] - Due: [Date] - Status: [Status]

**Next Week / Future:**
- [ ] [Action description] - Owner: [Name] - Due: [Date] - Status: [Status]

**Missing Information:**
- List any action items that are unclear, missing owners, or missing due dates

**Instructions:**
- Prioritize based on urgency and dependencies
- Flag items without clear owners or deadlines
- Note any blockers or dependencies between items
- If due date isn't specified, suggest one based on context
```

---

## 4. Stakeholder Communication Draft

### Prompt Template

```
Create a stakeholder update email based on this meeting summary.

**Meeting Summary:**
[Paste the meeting summary]

**Stakeholders to Update:**
[List stakeholders and their roles/interests]

**Tone and Style:**
- [Executive/Technical/Cross-functional]
- [Level of detail: High-level/Moderate/Detailed]

**Key Points to Emphasize:**
- [What stakeholders care most about]

**Generate:**
An email update that includes:
1. Clear subject line
2. Brief opening (context/purpose of meeting)
3. Key highlights (decisions, progress, wins)
4. Action items relevant to recipients
5. Any blockers/escalations needing their input
6. Next steps and timeline

Keep it scannable - use bullets where appropriate. Total length: [200-300 words / 400-500 words / etc.]
```

### Example Usage

```
Create a stakeholder update email based on this meeting summary.

**Meeting Summary:**
[Paste your generated summary from earlier]

**Stakeholders to Update:**
- VP Engineering (cares about timeline and resource needs)
- Director of Security (needs visibility on compliance)
- Finance lead (budget implications)

**Tone and Style:**
- Executive (high-level, business impact focused)
- Moderate detail

**Key Points to Emphasize:**
- We're on track but need QA resources
- Security findings being addressed
- Executive demo scheduled

**Generate:**
...
```

---

## 5. Meeting Series Insight Analyzer

### Prompt Template

```
Analyze patterns across multiple meetings to surface insights and recommendations.

**Meeting Series:** [Name of recurring meeting]
**Time Period:** [Date range]

**Summaries from last [N] meetings:**

**Meeting 1 ([Date]):**
[Summary]

**Meeting 2 ([Date]):**
[Summary]

**Meeting 3 ([Date]):**
[Summary]

[etc.]

**Analyze and provide:**

1. **Recurring Themes** - What topics keep coming up?
2. **Chronic Blockers** - What's repeatedly preventing progress?
3. **Action Item Patterns** - What types of actions are most common? Who's frequently overcommitted?
4. **Decision Velocity** - Are decisions being made and stuck to, or revisited?
5. **Recommendations** - What should change about these meetings or the program to be more effective?

Focus on actionable insights for a TPM to improve program execution.
```

---

## 6. Quick Meeting Prep (Speed Version)

### Ultra-Fast Prompt (30 seconds)

```
Meeting in 5 minutes: "[Meeting Title]" with [Attendees]

Last time we discussed: [1-2 sentence summary]

In 5 bullets, tell me:
- What's likely on the agenda today
- One question I should definitely ask
- Any landmines to avoid
- Key update I should share
- One decision we might need to make
```

---

## Tips for Effective Prompts

### Do's
✅ Provide specific meeting context (title, attendees, program)
✅ Include relevant background information
✅ Specify desired output format clearly
✅ Set appropriate tone and detail level
✅ Give the AI constraints (word count, bullet limits)

### Don'ts
❌ Dump unstructured walls of text without context
❌ Ask for outputs without specifying format
❌ Omit critical information (who, what, when)
❌ Use vague terms like "summarize this"
❌ Forget to specify your audience

### Customization Tips

**For different meeting types:**
- **Executive updates**: Emphasize business impact, minimize technical details
- **Technical deep-dives**: Preserve technical accuracy, include architecture context
- **Sprint planning**: Focus on capacity, dependencies, and commitments
- **Incident reviews**: Highlight timeline, impact, and action items

**For different AI tools:**
- **Gemini**: Great for multi-turn refinement, handles longer context
- **NotebookLM**: Excellent for analyzing meeting series and patterns
- **Claude**: Strong at maintaining tone and style consistency
- **ChatGPT**: Good for quick iterations and format variations

---

## Advanced: Chaining Prompts

For complex workflows, chain multiple prompts:

1. **Pre-meeting prep** → Save output
2. **During meeting** → Take quick notes referencing prep
3. **Post-meeting summary** → Feed notes + prep into summary prompt
4. **Stakeholder update** → Feed summary into communication prompt
5. **Action tracking** → Feed summary into action extractor

This creates a consistent information flow while letting you control each stage.

---

**Next Steps:**
1. Copy a template that matches your next meeting
2. Customize the bracketed sections
3. Run it through your AI tool
4. Refine based on results
5. Save successful variations for reuse

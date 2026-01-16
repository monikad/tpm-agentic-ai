# Task Organization Agent

An intelligent system that helps TPMs prioritize, categorize, and surface insights from the chaos of multi-program task management.

## The Problem

As TPMs managing multiple programs, we're drowning in tasks:
- Action items from 20+ meetings per week
- Issues and tickets across multiple tracking systems
- Cross-program dependencies nobody sees
- Constantly shifting priorities
- Tasks buried in email, Slack, docs, and sticky notes

**The reality:** We spend more time organizing tasks than completing them. Critical items get lost in the noise. We're reactive instead of strategic.

## The Solution

A Task Organization Agent that automatically categorizes, prioritizes, surfaces dependencies, and provides intelligent insights about your workload across programs.

## Core Capabilities

### 1. Intelligent Task Capture

**What it does:**
- Extracts action items from meeting notes, emails, Slack
- Automatically categorizes by program, type, and urgency
- Identifies owners, dependencies, and deadlines
- Flags ambiguous or incomplete tasks for clarification

**Sources:**
- Meeting summaries (from Meeting Intelligence Agent)
- Email and Slack threads
- Project management tools (Jira, Linear, Asana)
- Document comments and suggestions
- Quick voice/text notes

### 2. Smart Prioritization

**What it does:**
Uses multiple signals to rank tasks by actual importance:
- **Explicit urgency**: Due dates, SLA timers, escalation flags
- **Implicit signals**: Stakeholder seniority, program criticality, team velocity
- **Dependency impact**: Tasks blocking others get boosted
- **Strategic alignment**: Connection to quarterly goals and OKRs
- **Risk indicators**: Tasks related to known risks or incidents

**Priority Dimensions:**
- Impact vs. Effort matrix
- Critical path analysis
- Stakeholder importance
- Technical risk level
- Business value

### 3. Dependency Detection

**What it does:**
Identifies relationships between tasks that aren't explicitly linked:
- Tasks blocking other tasks
- Tasks requiring same resources
- Sequential dependencies
- Cross-program impacts
- Hidden assumptions

**Why it matters:**
Surfaces the non-obvious. "Can't launch Feature A until Legal approves Feature B's terms" - connections that live in your head but aren't documented.

### 4. Workload Intelligence

**What it does:**
- Analyzes capacity across programs and people
- Identifies overcommitment patterns
- Suggests rebalancing or delegation
- Flags bottlenecks and single points of failure
- Predicts missed deadlines based on current state

**Insights Generated:**
- "You have 17 tasks due this week, average completion time suggests 9 are at risk"
- "Sarah is assigned to 23 tasks across 4 programs - potential bottleneck"
- "3 critical path items depend on vendor response, no escalation plan visible"

### 5. Contextual Surfacing

**What it does:**
Proactively surfaces the right tasks at the right time:
- Pre-meeting: Tasks related to attendees and topics
- Monday planning: Week's critical path
- Friday review: Uncompleted commitments
- Before 1:1s: Tasks assigned to that person
- Stakeholder pings: Related context and history

## Technical Architecture

### Tools Used
- **Gemini**: Task analysis, categorization, and insight generation
- **NotebookLM**: Pattern recognition across task history
- **RAG System**: Context retrieval from related docs and discussions
- **Task APIs**: Integration with Jira, Linear, Asana, etc.
- **Calendar Integration**: Time-based task surfacing

### Data Model
```
Task {
  id: unique identifier
  title: clear description
  program: which program/project
  owner: who's responsible
  status: not_started | in_progress | blocked | done
  priority: calculated score
  due_date: deadline
  dependencies: [task_ids]
  related_tasks: [task_ids]
  source: where it came from
  context: relevant background
  tags: [categories]
  metadata: {
    created_date,
    last_updated,
    stakeholders,
    risk_level,
    effort_estimate
  }
}
```

## Implementation Guide

### Level 1: Simple Task Extraction

Start with extracting tasks from one source (e.g., meeting notes):

**Prompt Template:**
```
Extract all action items from these notes and format as structured tasks.

NOTES:
[Your meeting notes]

OUTPUT FORMAT:
- [ ] [Clear, actionable task description]
  - Owner: [Name]
  - Due: [Date or "TBD"]
  - Program: [Which program]
  - Priority: [High/Medium/Low based on context]
  - Dependencies: [Any blockers mentioned]
```

### Level 2: Multi-Source Aggregation

Combine tasks from multiple sources into one prioritized view:

1. Extract tasks from each source
2. Deduplicate similar tasks
3. Apply prioritization criteria
4. Generate daily/weekly focus list

### Level 3: Intelligent Dashboard

Build a system that:
- Automatically pulls tasks from all sources
- Categorizes and prioritizes continuously
- Surfaces insights and recommendations
- Updates based on completion and changes

## Sample Prompts

### Task Extraction from Meeting

```
Extract actionable tasks from this meeting summary.

MEETING CONTEXT:
- Program: Payment Platform Modernization
- Attendees: Engineering, Product, Security
- Date: Jan 14, 2026

SUMMARY:
[Paste meeting summary]

EXTRACT:
All tasks with:
- Clear action description
- Owner (or "UNASSIGNED" if unclear)
- Estimated due date based on discussion
- Category: technical | process | communication | decision
- Priority: critical | high | medium | low
- Dependencies on other work mentioned

Flag any tasks that are vague or need clarification.
```

### Weekly Prioritization

```
Analyze my task list and help me prioritize this week.

TASKS:
[Paste your task list from all sources]

CONTEXT:
- Current date: January 15, 2026
- This week's focus: Finalize Q1 planning, unblock engineering teams
- Known risks: Vendor delay on API, understaffed QA team
- Key meetings: Exec review (Thurs), Sprint planning (Fri)

GENERATE:
1. Critical Path (must happen this week)
2. High Impact (should happen if possible)
3. Can Wait (defer if necessary)
4. Need Clarification (tasks too vague to prioritize)

For each task, briefly explain why it's in that category.
```

### Dependency Analysis

```
Analyze these tasks for hidden dependencies and risks.

PROGRAM: [Program name]
TASKS:
[List of tasks with owners and dates]

FIND:
1. Tasks blocking other tasks
2. Tasks depending on external parties (vendors, other teams)
3. Resource conflicts (same person on too many critical paths)
4. Missing prerequisites (tasks that need something not listed)
5. Timeline risks (dependencies that make deadlines unrealistic)

Visualize the critical path and flag the biggest risks.
```

### Workload Rebalancing

```
Analyze workload distribution and suggest rebalancing.

TEAM TASKS:
Person A: [List of tasks]
Person B: [List of tasks]
Person C: [List of tasks]

CONSTRAINTS:
- Person A: On vacation Jan 20-27
- Person B: New to team, limited context
- Person C: Subject matter expert but overcommitted

ANALYZE:
1. Who's overloaded vs. underutilized?
2. What tasks could be delegated or redistributed?
3. What's the risk if we don't rebalance?
4. Specific recommendations for task reassignment

Consider skill requirements, context, and urgency.
```

## Success Metrics

**Time Saved:**
- Task organization: 2-3 hours/week → 30 min/week
- Priority decisions: 15-20 min/day → 5 min/day
- Context retrieval: 10+ min/task → 2 min/task

**Quality Improvements:**
- Fewer missed deadlines (better visibility)
- Reduced context switching (better grouping)
- Proactive risk mitigation (dependency detection)
- More strategic time allocation (less reactive fire-fighting)

## Real-World Examples

### Example 1: Task Extraction

**Raw Meeting Notes:**
"Sarah to check database capacity by Friday. Mike needs to follow up with vendor about API docs. Legal review blocking - Alex escalating to VP. Team should review security findings before next week's planning."

**AI-Organized Output:**
```
TASKS EXTRACTED:

Critical (Blocking):
- [ ] Escalate legal review delay to VP
  Owner: Alex | Due: Jan 16 | Program: Payment Platform
  Dependency: Blocking Phase 2 launch planning

High Priority:
- [ ] Analyze database capacity for Phase 2 load
  Owner: Sarah | Due: Jan 17 | Program: Payment Platform
  
- [ ] Follow up with vendor on API documentation timeline
  Owner: Mike | Due: Jan 16 | Program: Payment Platform
  Dependency: Engineering team waiting

Medium Priority:
- [ ] Review security audit findings
  Owner: Engineering Team | Due: Jan 21 | Program: Payment Platform
  Context: Needed before sprint planning Jan 22

NEEDS CLARIFICATION:
- "Team should review" - Who specifically? All engineers or subset?
```

### Example 2: Workload Analysis

**AI Insight:**
```
WORKLOAD ANALYSIS - Week of Jan 15

⚠️ OVERCOMMITTED:
Sarah (Engineering Lead)
- 12 high-priority tasks across 3 programs
- 8 tasks due this week (historical completion: 5/week avg)
- 3 tasks are single-points-of-failure
Recommendation: Delegate database optimization to Tom, defer non-critical code reviews

⚠️ BOTTLENECK RISK:
Legal Team
- Blocking 4 launch-critical items
- Average response time: 10 days (estimated need: 5 days)
Recommendation: Executive escalation needed today

✅ CAPACITY AVAILABLE:
Tom (Senior Engineer)
- 4 tasks this week, usually handles 7-8
- Has relevant database expertise for Sarah's overflow
Recommendation: Assign database capacity analysis task
```

## Lessons Learned

### What Works Well
✅ Automated task extraction saves huge amounts of time
✅ Priority scoring reveals what actually matters vs. what feels urgent
✅ Dependency visualization prevents "didn't know that was blocking" surprises
✅ Weekly review prompts catch falling tasks early

### What Needs Human Judgment
⚠️ Political sensitivity (some tasks are more important than they appear)
⚠️ Changing priorities (AI can't predict sudden executive shifts)
⚠️ Effort estimation (AI over-relies on stated deadlines)
⚠️ Delegation decisions (relationship and growth factors matter)

### Common Pitfalls
❌ Trusting AI priority without context check
❌ Over-categorizing - sometimes "just do it" is better than perfect organization
❌ Analysis paralysis - spending more time organizing than executing
❌ Forgetting to update task status (garbage in, garbage out)

## Best Practices

### Task Hygiene
- Update task status regularly (daily or after each completion)
- Use clear, action-oriented task descriptions
- Always specify owner and due date
- Tag tasks with program and category
- Link to relevant context (docs, tickets, discussions)

### Prioritization
- Re-run priority analysis weekly, not daily (avoid churn)
- Override AI when you have information it doesn't
- Focus on top 5-7 tasks per week, defer the rest
- Distinguish "urgent" from "important"
- Build in buffer for unexpected work (only plan 60-70% of capacity)

### Dependency Management
- Document dependencies explicitly, don't rely on memory
- Set up alerts for blocked tasks
- Identify critical path weekly
- Have backup plans for external dependencies
- Over-communicate dependencies to stakeholders

## Integration Ideas

**Combine with other agents:**
- **Meeting Agent** → **Task Organizer**: Auto-extract action items from all meetings
- **Task Organizer** → **Communication Optimizer**: Generate status updates from task state
- **Task Organizer** → **Presentation Generator**: Create roadmap slides from task groupings

## Future Enhancements

**Next iterations could include:**
- Automatic task creation from Slack/email mentions
- Predictive deadline risk scoring
- Suggested task batching for efficiency
- Learning from past estimation accuracy
- Team capacity forecasting

## Getting Started

### Week 1: Extraction
- Pick one task source (meetings, email, or project tool)
- Create extraction prompt
- Manually review and refine for 1 week
- Build confidence in accuracy

### Week 2: Prioritization
- Dump all tasks from all sources
- Run weekly prioritization prompt
- Compare AI priority vs. your intuition
- Adjust criteria based on mismatches

### Week 3: Insights
- Add dependency analysis
- Run workload distribution check
- Start surfacing proactive insights
- Share findings with team

### Week 4: Automation
- Set up regular extraction from consistent sources
- Create dashboard or weekly review ritual
- Integrate with existing tools
- Refine based on actual usage

## Related Projects

- [Meeting Intelligence Agent](../meeting-assistant/) - Primary source of action items
- [Communication Optimizer](../communication-optimizer/) - Turn task status into updates
- [Presentation Generator](../presentation-generator/) - Visualize program status from tasks

---

**Remember:** The goal isn't perfect task management. It's spending less time managing tasks and more time completing the ones that matter. Use AI to surface signal from noise.

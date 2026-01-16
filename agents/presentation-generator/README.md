# Presentation Generator Agent

An AI assistant that transforms meeting notes, project data, and strategic documents into executive-ready presentation slides - saving TPMs hours of deck creation time.

## The Problem

TPMs spend endless hours creating presentations:
- Weekly status updates for leadership
- Quarterly program reviews
- Technical deep-dives for different audiences
- Incident retrospectives
- Resource requests and proposals
- Onboarding and knowledge transfer

**The reality:** We already have the content (in notes, docs, dashboards). We just need to restructure it for slide format. But this "just" takes 2-4 hours per deck.

## The Solution

A Presentation Generator that takes your existing content and automatically creates slide outlines, key messages, and content suggestions tailored to your audience and purpose.

## Core Capabilities

### 1. Content-to-Slides Transformation

**What it does:**
- Analyzes source material (meeting summaries, project docs, data)
- Extracts key messages and insights
- Structures content into logical slide flow
- Suggests titles, bullets, and talking points
- Identifies data/metrics that should be visualized

**Input Sources:**
- Meeting summaries and notes
- Project documentation
- Task lists and roadmaps
- Metrics and dashboards
- Previous presentations
- Strategy documents

### 2. Audience-Adaptive Formatting

**What it does:**
Generates different presentations from the same content:
- **Executive (C-suite)**: Business impact, decisions needed, 5-7 slides
- **Engineering Leadership**: Technical depth, architecture, risks, 10-15 slides
- **Cross-functional Teams**: Balanced detail, action items, 8-12 slides
- **Board/Investors**: Strategic outcomes, metrics, growth, 5-10 slides

**Adaptation includes:**
- Detail level (high-level vs. technical)
- Jargon usage (business vs. technical terms)
- Metrics emphasis (ROI vs. performance)
- Slide count and density

### 3. Standard Deck Templates

**What it does:**
Creates common TPM presentation types:

**Program Status Update:**
- Current state summary
- Progress vs. plan
- Key wins and achievements
- Risks and blockers
- Upcoming milestones
- Asks/decisions needed

**Quarterly Business Review:**
- Quarter highlights
- OKR progress
- Key metrics and trends
- Major accomplishments
- Lessons learned
- Next quarter preview

**Technical Deep-Dive:**
- Problem statement
- Current architecture
- Proposed solution
- Trade-offs and alternatives
- Implementation plan
- Success metrics

**Incident Retrospective:**
- Timeline and impact
- Root cause analysis
- Response effectiveness
- Action items and owners
- Prevention measures
- Process improvements

### 4. Visual Recommendations

**What it does:**
- Suggests chart types for data (bar, line, pie, timeline)
- Recommends diagram types (flowchart, architecture, swim lanes)
- Identifies content better shown visually vs. text
- Proposes slide layouts based on content
- Flags text-heavy slides for simplification

### 5. Narrative Flow Optimization

**What it does:**
- Creates logical progression of ideas
- Builds narrative arc (problem → solution → action)
- Front-loads key messages
- Ensures smooth transitions between slides
- Adds context where needed
- Suggests appendix slides for detail

## Technical Architecture

### Tools Used
- **Gemini**: Content analysis and slide generation
- **NotebookLM**: Analyzing past successful presentations for patterns
- **RAG System**: Pulling relevant content from knowledge base
- **Template Library**: Standard slide structures and formats

### Generation Pipeline
```
Input: Source Content + Audience + Purpose
↓
Content Analysis: Extract key points, data, decisions
↓
Structure: Organize into logical sections and flow
↓
Slide Generation: Create titles, bullets, talking points
↓
Visual Suggestions: Recommend charts and diagrams
↓
Output: Slide outline + content + speaker notes
```

## Implementation Guide

### Quick Start: Prompt-Based Generation

**Basic Template:**
```
Create a presentation outline from this content.

AUDIENCE: [Who will see this - e.g., VP Engineering, exec team, all-hands]
PURPOSE: [What you want to achieve - inform, decide, align, celebrate]
TIME LIMIT: [How long - 5 min, 15 min, 30 min]
TONE: [Formal/Casual, Optimistic/Realistic]

CONTENT:
[Paste your source material - meeting summaries, docs, data]

GENERATE:
1. Suggested presentation title
2. Slide-by-slide outline with:
   - Slide title
   - Key message (one sentence)
   - 3-5 bullets or content description
   - Visual suggestion (if applicable)
3. Recommended appendix slides for Q&A

Target: [Number] slides for a [Duration] presentation
```

### Advanced: Automated Deck Creation

Build a workflow that:
1. Aggregates weekly meeting summaries
2. Pulls current program metrics
3. Identifies risks and blockers from task system
4. Generates draft status update deck
5. TPM reviews and customizes
6. Export to PowerPoint/Google Slides

## Sample Prompts

### Weekly Status Update

```
Create a weekly program status update for leadership.

AUDIENCE: VP Engineering, Director of Product
TIME: 10-minute review in exec meeting
FOCUS: Progress, blockers, decisions needed

CONTENT:

Last Week's Summary:
[Paste summary from meeting agent]

Current Metrics:
- Velocity: 45 points (target: 50)
- Sprint completion: 85%
- P0 bugs: 2 (down from 5)
- Release confidence: Medium

Upcoming Milestones:
- Phase 2 launch: Feb 1 (at risk)
- Security audit: Jan 25 (on track)
- Integration testing: Jan 22 (on track)

Active Risks:
- Vendor API delay pushing launch date
- QA resource gap affecting test coverage

GENERATE:
5-7 slide outline for program status. Include:
- One-slide executive summary
- Progress highlights (wins)
- Metrics trends
- Key blockers with impact
- Decision needed from leadership
```

### Quarterly Business Review

```
Create a Q1 program review presentation.

AUDIENCE: Executive leadership team + Board observers
TIME: 30 minutes with Q&A
PURPOSE: Show program value, secure Q2 resources

CONTENT:

Q1 Goals & Achievements:
[Paste OKRs and completion status]

Key Metrics:
[Paste metrics summary - user growth, performance, reliability]

Major Milestones Completed:
[List significant deliveries]

Challenges Overcome:
[Significant blockers that were resolved]

Lessons Learned:
[Key insights from the quarter]

Q2 Preview:
[Planned initiatives and goals]

Resource Request:
[What you need for Q2]

GENERATE:
10-12 slide deck that:
- Celebrates wins (positive tone)
- Shows business impact (metrics)
- Demonstrates smart decision-making (challenges overcome)
- Sets up Q2 ask (resource request)
- Inspires confidence in program

Include speaker notes for complex slides.
```

### Technical Architecture Review

```
Create a technical deep-dive presentation on our system architecture.

AUDIENCE: Engineering team + Technical Architects
TIME: 45 minutes with discussion
PURPOSE: Align on architecture direction, get feedback

CONTENT:

Current State:
- Monolithic architecture on AWS
- PostgreSQL database
- REST APIs
- React frontend

Challenges:
- Scaling limitations
- Deployment complexity
- Team coordination overhead

Proposed Future State:
- Microservices architecture
- Event-driven communication
- Kubernetes orchestration
- GraphQL API gateway

Migration Plan:
[Outline of phases]

Trade-offs:
[Pros and cons of approach]

GENERATE:
15-slide technical presentation that:
- Sets context (why change is needed)
- Shows current pain points with data
- Explains proposed architecture clearly
- Visualizes key components and data flow
- Outlines migration approach
- Addresses risks and mitigation
- Defines success metrics

Suggest diagrams for architecture slides.
```

### Incident Retrospective

```
Create an incident retrospective presentation.

AUDIENCE: Engineering team, Engineering leadership, Product
TIME: 30 minutes
PURPOSE: Share learnings, commit to improvements

INCIDENT DATA:

Timeline:
- 2:15 PM: Customer reports checkout failures
- 2:30 PM: Team identifies database connection pool exhaustion
- 3:45 PM: Mitigation deployed (connection pool increase)
- 4:30 PM: Full resolution (query optimization deployed)

Impact:
- Duration: 2 hours 15 minutes
- Affected users: ~15,000 checkout attempts
- Revenue impact: ~$50K in failed transactions
- Customer complaints: 47

Root Cause:
- Inefficient query introduced in recent deployment
- Missing load testing for checkout flow
- No connection pool monitoring alerts

Response Effectiveness:
- Detection: Customer report (should be internal monitoring)
- Diagnosis: 15 minutes (good)
- Mitigation: 1 hour 15 min (acceptable)
- Communication: Delayed stakeholder notification

Action Items:
[List of follow-up tasks]

GENERATE:
8-10 slide retrospective that:
- States impact clearly but not blamefully
- Shows detailed timeline
- Explains root cause technically
- Evaluates our response
- Commits to specific improvements
- Ends on learning note, not defensive tone
```

## Success Metrics

**Time Saved:**
- Status update decks: 2-3 hours → 30-45 min
- Quarterly reviews: 6-8 hours → 2-3 hours
- Technical deep-dives: 4-5 hours → 1-2 hours

**Quality Improvements:**
- More consistent messaging
- Better narrative flow
- Appropriate detail for audience
- Fewer revision cycles

## Real-World Examples

### Example: Executive Status Update

**AI-Generated Outline:**

```
PRESENTATION: Payment Platform - Weekly Status
AUDIENCE: VP Engineering, Director Product
DURATION: 10 minutes (7 slides)

---

SLIDE 1: Executive Summary
Title: "Payment Platform: Week of Jan 15"
Key Message: On track for Feb 1 launch with one critical blocker requiring decision

• Progress: Phase 1 complete, Phase 2 80% done
• At Risk: Vendor API delay threatens Feb 1 launch
• Decision Needed: Build workaround vs. escalate vendor vs. delay launch
• Resource Status: Team at capacity, QA bottleneck identified

Visual: Status dashboard with green/yellow/red indicators

---

SLIDE 2: This Week's Wins
Key Message: Strong execution despite challenges

• ✅ Database migration completed 3 days ahead of schedule
• ✅ Prevented P0 auth bug through proactive monitoring
• ✅ Security audit passed with only minor findings
• ✅ Team velocity improved 12% over last sprint

Visual: Timeline showing milestones achieved

---

SLIDE 3: Key Metrics Trending
Key Message: Performance and quality improving

• API Latency: 40% improvement (250ms → 150ms p95)
• Error Rate: Down to 0.02% (target: <0.05%)
• Test Coverage: 87% (up from 78%)
• Sprint Velocity: 45 points (target: 50)

Visual: Line chart showing metric trends

---

SLIDE 4: Critical Blocker - Vendor API Delay
Key Message: 6-week vendor delay puts Feb 1 launch at risk

• Issue: Third-party API docs delayed Dec 15 → Jan 30
• Impact: Blocks Phase 2 integration, team productivity declining
• Options:
  1. Build temporary workaround (2 eng-weeks, tech debt)
  2. Executive escalation to vendor (uncertain timeline)
  3. Delay launch to Feb 15 (affects go-to-market plan)
• Recommendation: Option 2 with Option 3 as backup

Visual: Decision tree or risk matrix

---

SLIDE 5: Resource Update
Key Message: QA capacity gap identified, manageable with action

• Current: 2 QA engineers covering 3 programs
• Need: Additional QA support for comprehensive testing
• Impact: Test coverage at 87%, target 95% for launch
• Ask: Temporarily allocate QA from Platform team (2 weeks)

Visual: Resource allocation chart

---

SLIDE 6: February Milestones
Key Message: Clear path to success with decision today

• Week 1 (Jan 20-24): Complete Phase 2 development
• Week 2 (Jan 27-31): Integration testing + QA
• Week 3 (Feb 3-7): Production rollout (pending decision today)
• Week 4 (Feb 10-14): Monitoring + optimization

Visual: Gantt chart or timeline

---

SLIDE 7: Next Steps & Asks
Key Message: Decision needed today, then clear execution path

ASKS FROM LEADERSHIP:
1. Approve vendor escalation approach by EOD
2. Temporary QA allocation from Platform team
3. Go/no-go decision for Feb 1 by Friday

NEXT SYNC:
• Same time next week
• Will have vendor escalation outcome
• Will show final test results

---

APPENDIX SLIDES (for Q&A):
A1: Technical Architecture Details
A2: Detailed Test Plan
A3: Security Audit Findings
A4: Budget Status
```

**Speaker Notes for Slide 4:**
"This is our biggest risk right now. We've been waiting on vendor API documentation since December 15th - it's now delayed to January 30th, a full 6-week slip. Our engineering team is blocked and productivity is dropping. I've outlined three options: build a workaround which adds technical debt, escalate through their executive team, or delay our launch. I recommend executive escalation given the strategic importance, but we need a decision today to keep February 1st viable."

## Lessons Learned

### What Works Well
✅ AI excels at structuring scattered information into coherent narrative
✅ Saves massive time on first draft - start at 70% done instead of 0%
✅ Consistent slide formatting and messaging
✅ Good at extracting key points from verbose content
✅ Helpful visual suggestions (though need refinement)

### What Needs Human Touch
⚠️ Visual design - AI suggests types, you create beauty
⚠️ Data visualization - AI flags data, you build charts
⚠️ Speaker notes - AI drafts, you add your voice
⚠️ Storytelling nuance - AI structures, you add emotion
⚠️ Political sensitivity - Some messages need careful wording

### Common Pitfalls
❌ Accepting AI output without customization
❌ Too much content per slide (AI tends to be verbose)
❌ Missing emotional intelligence in sensitive topics
❌ Generic visuals that don't match brand/style
❌ Skipping speaker notes preparation

## Best Practices

### Content Preparation
- Gather all source material first
- Clarify audience and purpose upfront
- Define success criteria (what decision/action do you want?)
- Note any sensitive topics requiring careful framing

### Generation Process
1. **First pass**: Generate full outline with AI
2. **Review**: Cut 20-30% of content (AI over-includes)
3. **Enhance**: Add visuals, refine messaging
4. **Practice**: Read through with speaker notes
5. **Refine**: Adjust based on timing and flow

### Presentation Hygiene
- One key message per slide (AI sometimes packs too much)
- 3-5 bullets max per slide (AI tends toward 6-7)
- Use visuals over text where possible
- Front-load your ask or key message
- Build appendix slides for detail/Q&A

## Integration Ideas

**Combine with other agents:**
- **Meeting Agent** → **Presentation Generator**: Weekly status from meeting summaries
- **Task Organizer** → **Presentation Generator**: Roadmap slides from task groupings
- **Communication Optimizer** → **Presentation Generator**: Consistent messaging across channels

**Workflow Example:**
1. Meeting Agent generates weekly summaries
2. Task Organizer provides current sprint status
3. Presentation Generator creates status deck
4. Communication Optimizer drafts email to accompany deck
5. TPM reviews, customizes, presents

## Future Enhancements

**Next iterations could include:**
- Direct export to PowerPoint/Google Slides with formatting
- Brand-compliant templates and color schemes
- Automatic data visualization from metrics
- Learning from past presentation performance (engagement, questions)
- A/B testing messaging for different audiences

## Getting Started

### Week 1: Template-Based
- Pick one recurring presentation type
- Create prompt template with typical structure
- Generate 2-3 versions
- Refine template based on quality

### Week 2: Content Aggregation
- Identify all content sources for a presentation
- Practice feeding multiple sources to AI
- Experiment with content prioritization
- Build confidence in output quality

### Week 3: Audience Adaptation
- Take one presentation
- Generate 3 versions for different audiences
- Compare AI choices with your instinct
- Refine audience adaptation criteria

### Week 4: Full Workflow
- Automate content aggregation from agents
- Generate draft deck automatically
- Review and customize workflow
- Measure time savings

## Related Projects

- [Meeting Intelligence Agent](../meeting-assistant/) - Source content for status updates
- [Task Organizer](../task-organizer/) - Roadmap and progress data
- [Communication Optimizer](../communication-optimizer/) - Consistent messaging

---

**Remember:** The goal is to spend less time building slides and more time on the strategic thinking behind them. AI handles structure and first drafts. You add the insight, emotion, and polish that make presentations compelling.

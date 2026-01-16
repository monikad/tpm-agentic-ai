# Meeting Intelligence Agent

An AI-powered assistant that transforms meeting workflows from preparation through follow-up, designed specifically for TPM needs.

## The Problem

As TPMs, we're in back-to-back meetings across multiple programs. Each meeting requires:
- Context gathering from previous discussions, docs, and tickets
- Understanding who'll be there and what they care about
- Taking structured notes while actively participating
- Extracting and tracking action items
- Writing and distributing summaries
- Following up on commitments

**The cost:** Hours of prep and admin work that takes us away from strategic thinking and relationship building.

## The Solution

A Meeting Intelligence Agent that automates the repetitive cognitive work while maintaining quality and context awareness.

## Core Capabilities

### 1. Pre-Meeting Preparation
**What it does:**
- Analyzes calendar invite and meeting title
- Pulls relevant context from previous meetings, documents, and project trackers
- Identifies key stakeholders and their priorities
- Generates suggested agenda items
- Surfaces potential blockers or discussion topics

**Example Prompt Pattern:**
```
Prepare me for a meeting titled "[Meeting Title]" with [Attendees].
Context: [Program/Project Name]
Pull relevant information from: [Last 3 sync notes, current sprint plan, open risks]
Focus on: decisions needed, open questions, stakeholder concerns
```

### 2. Real-Time Meeting Support
**What it does:**
- Provides quick context lookup during discussions
- Suggests talking points based on meeting flow
- Flags when discussions diverge from objectives
- Tracks decisions and action items as they occur

**Implementation Approach:**
Use a combination of:
- Live transcript analysis (if available)
- Quick voice-to-text note capture
- Structured note templates with AI auto-population

### 3. Post-Meeting Processing
**What it does:**
- Generates structured meeting summary
- Extracts action items with owners and deadlines
- Identifies decisions made and open questions
- Creates follow-up task list
- Drafts stakeholder communications

**Output Format:**
```markdown
## Meeting Summary: [Title] - [Date]

**Attendees:** [List]
**Duration:** [Time]

### Key Decisions
1. [Decision with context]
2. [Decision with context]

### Action Items
- [ ] [Action] - Owner: [Name] - Due: [Date]
- [ ] [Action] - Owner: [Name] - Due: [Date]

### Open Questions
1. [Question requiring follow-up]
2. [Question requiring follow-up]

### Next Steps
- [Next meeting/milestone]
- [Dependencies to track]
```

### 4. Follow-Up Automation
**What it does:**
- Tracks action item completion
- Sends reminders to owners
- Surfaces blockers before next sync
- Maintains meeting history and patterns

## Technical Architecture

### Tools Used
- **Gemini**: Multi-turn conversation for context gathering and summary generation
- **NotebookLM**: Historical meeting analysis and pattern recognition
- **RAG System**: Document and previous meeting retrieval
- **Calendar API**: Meeting metadata and scheduling
- **Task Management Integration**: Action item creation and tracking

### Data Flow
```
Pre-Meeting: Calendar Event → Context Retrieval → Brief Generation
During: Voice/Text Input → Structured Notes → Real-time Tracking
Post: Raw Notes → AI Processing → Summary + Actions
Follow-Up: Action Tracking → Reminder Generation → Status Updates
```

## Implementation Guide

### Option 1: Simple Prompt-Based Approach
Use a structured prompt template with your preferred AI tool (Gemini, Claude, etc.)

**Files needed:**
- `prompts/pre-meeting-brief.txt`
- `prompts/meeting-summary.txt`
- `prompts/action-extraction.txt`

### Option 2: Automated Pipeline
Build a lightweight automation that connects your calendar, notes app, and task manager.

**Components:**
- Calendar webhook trigger
- Context aggregation script
- AI processing pipeline
- Output distribution (email, Slack, task system)

### Option 3: Hybrid Approach (Recommended)
Automate the repetitive parts, keep human judgment for nuanced decisions.

**What to automate:**
- Context gathering from known sources
- Basic summary structure
- Action item extraction
- Reminder scheduling

**What to review manually:**
- Decision accuracy
- Stakeholder-sensitive communications
- Priority assessment
- Strategic implications

## Getting Started

### Step 1: Define Your Meeting Types
Create templates for your common meeting patterns:
- Program syncs
- Stakeholder reviews
- Sprint planning
- Architecture reviews
- Executive updates

### Step 2: Map Your Information Sources
Identify where meeting context lives:
- Previous meeting notes
- Project documentation
- Issue trackers (Jira, Linear, etc.)
- Team communication (Slack, Teams)
- Design docs and specs

### Step 3: Build Your First Template
Start with your most frequent meeting type. Create a prompt that:
1. Takes the meeting title and attendees
2. Pulls context from 2-3 key sources
3. Generates a 5-bullet prep brief

### Step 4: Iterate and Expand
- Use the template for 3-5 meetings
- Note what's missing or inaccurate
- Refine the prompt and sources
- Gradually add more automation

## Sample Prompts

See the `/prompts` directory for ready-to-use templates:
- `pre-meeting-context.md` - Gather and synthesize context
- `meeting-summary-generator.md` - Transform notes to summary
- `action-item-extractor.md` - Pull structured action items
- `stakeholder-update.md` - Generate communication from summary

## Success Metrics

**Time Saved:**
- Meeting prep: 15-20 min → 3-5 min per meeting
- Note organization: 10-15 min → 2-3 min per meeting
- Follow-up: 10 min → 1-2 min per meeting

**Quality Improvements:**
- More consistent documentation
- Fewer missed action items
- Better stakeholder communication
- Improved meeting continuity

## Lessons Learned

### What Works Well
✅ Pre-meeting context gathering - huge time saver
✅ Action item extraction - more accurate than manual
✅ Summary generation - consistent quality
✅ Template-based approaches - easy to customize

### What Needs Human Review
⚠️ Decision validation - AI can miss nuance
⚠️ Priority assessment - requires program context
⚠️ Stakeholder sensitivity - political considerations
⚠️ Strategic implications - needs TPM judgment

### Common Pitfalls
❌ Over-automating - some meetings need full human attention
❌ Context overload - too much information confuses the AI
❌ One-size-fits-all - different meetings need different approaches
❌ Ignoring edge cases - handle urgent/sensitive meetings differently

## Future Enhancements

**Next iterations could include:**
- Automated agenda generation based on program state
- Proactive conflict/blocker identification
- Meeting effectiveness scoring
- Cross-program pattern recognition
- Stakeholder sentiment analysis

## Contributing

Have ideas for improving meeting intelligence? Found a better prompt pattern? Open an issue or submit a PR!

## Related Projects

- [Communication Optimizer](../communication-optimizer/) - Draft stakeholder updates from meeting summaries
- [Task Organizer](../task-organizer/) - Manage action items across programs
- [Presentation Generator](../presentation-generator/) - Create exec updates from meeting history

---

**Remember:** This agent augments your TPM skills, it doesn't replace your judgment. Use it to eliminate toil, not to avoid the hard work of program management.

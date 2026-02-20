# Product Requirements Document: Chatly
**Version:** 1.0
**Date:** February 19, 2026
**Author:** Kartik Bhalerao
**Status:** Draft — Internal Review
**Document Type:** Product Requirements Document (PRD)

---

## Table of Contents

[Diagrams & Wireframes](#diagrams--wireframes)

1. [Executive Summary](#1-executive-summary)
2. [Problem Statement & Market Opportunity](#2-problem-statement--market-opportunity)
3. [Target Users & Personas (Jobs-to-Be-Done)](#3-target-users--personas-jobs-to-be-done)
4. [Product Goals & OKRs](#4-product-goals--okrs)
5. [Feature Requirements (Core + Advanced)](#5-feature-requirements-core--advanced)
6. [User Stories & Acceptance Criteria](#6-user-stories--acceptance-criteria)
7. [Technical Architecture Overview](#7-technical-architecture-overview)
8. [Integrations & Third-Party Tools](#8-integrations--third-party-tools)
9. [UX/UI Requirements & User Flows](#9-uxui-requirements--user-flows)
10. [Non-Functional Requirements](#10-non-functional-requirements)
11. [Success Metrics & Analytics Framework](#11-success-metrics--analytics-framework)
12. [Go-to-Market Strategy](#12-go-to-market-strategy)
13. [Risk Analysis & Mitigation](#13-risk-analysis--mitigation)
14. [Competitive Landscape](#14-competitive-landscape)
15. [Product Roadmap (MVP to V2)](#15-product-roadmap-mvp-to-v2)

---

## Diagrams & Wireframes

> All diagrams are live in FigJam. Click any link to open, view, and edit in Figma.

| # | Diagram | Description | Open in FigJam |
|---|---|---|---|
| 1 | **User Flow** | End-to-end journey: Signup → Upload → Extract → Review → Sync → Dashboard | [View Diagram →](https://www.figma.com/online-whiteboard/create-diagram/9169c202-6167-4eea-875c-ef19c59c0fbd?utm_source=claude&utm_content=edit_in_figjam) |
| 2 | **System Architecture** | NLP Pipeline → Pipeline Builder → Jira / Slack / Notion / Linear / Trello | [View Diagram →](https://www.figma.com/online-whiteboard/create-diagram/08e00113-f8f4-4e90-933f-7612d1342572?utm_source=claude&utm_content=edit_in_figjam) |
| 3 | **Conversation State Diagram** | How a conversation moves: Raw → Processing → Extracted → Approved → Synced → Tracking | [View Diagram →](https://www.figma.com/online-whiteboard/create-diagram/198d263f-8ff0-49ba-a0e4-1f0eda8513bd?utm_source=claude&utm_content=edit_in_figjam) |
| 4 | **Sequence Diagram** | Step-by-step interaction: User ↔ Chatly ↔ NLP Engine ↔ Jira / Slack / Notion | [View Diagram →](https://www.figma.com/online-whiteboard/create-diagram/a18914bf-e109-4f9c-8ca7-a751513253b5?utm_source=claude&utm_content=edit_in_figjam) |
| 5 | **Product Roadmap Gantt** | MVP → V1 → V2 timeline with all 16 features mapped across 7 months | [View Diagram →](https://www.figma.com/online-whiteboard/create-diagram/4348bb18-b40a-4cb0-809e-59092b814359?utm_source=claude&utm_content=edit_in_figjam) |

---

## 1. Executive Summary

### Product Name
Chatly

### One-Line Description
Chatly automatically transforms AI conversations into structured execution pipelines, bridging the gap between AI-generated insights and real-world task execution.

### Problem Being Solved
Every day, individuals and teams use AI assistants (ChatGPT, Claude, Gemini, Copilot) to think through problems, plan projects, and generate ideas. The outputs of these conversations are intellectually rich but operationally inert. Action items are buried in chat threads. Decisions are never formally recorded. No one is assigned ownership. Deadlines exist only in natural language. The moment the conversation window closes, organizational value evaporates.

### Solution Overview
Chatly is a SaaS platform that sits on top of AI conversations — intercepting, parsing, and structuring them in real time or post-session. Using a multi-stage NLP pipeline, Chatly identifies action items, decisions, owners, deadlines, and blockers from any AI conversation transcript. It then auto-generates execution pipelines and syncs structured tasks directly into the workflow tools teams already use: Jira, Notion, Slack, Trello, Linear, Asana, and GitHub.

### Business Impact
- Reduces post-meeting/post-session setup time by an estimated 70-80%
- Eliminates task loss from unstructured AI conversations
- Creates a closed-loop system from ideation (AI conversation) to execution (workflow tool)
- Positions as the connective tissue between the AI productivity layer and the execution layer

### Resource Requirements (Estimated)
| Resource | Requirement |
|---|---|
| Engineering Team | 6-8 engineers (2 NLP/ML, 3 full-stack, 1 DevOps, 1 QA) |
| Design | 1 senior product designer + 1 UX researcher |
| Product | 1 PM (lead) + 1 APM |
| Timeline to MVP | 16 weeks |
| Initial Infrastructure Budget | $40,000-$60,000/year (cloud + LLM API costs) |
| Target ARR (Year 1) | $1.5M-$3M |

### Risk Summary
Primary risks include LLM API cost volatility, accuracy of NLP extraction at scale, integration maintenance overhead across third-party platforms, and user trust in automated task creation. These are addressed in Section 13.

---

## 2. Problem Statement & Market Opportunity

### 2.1 The Core Problem

AI assistants have become the primary thinking partner for knowledge workers. According to industry surveys (2025), over 65% of enterprise knowledge workers use AI assistants daily for planning, brainstorming, and decision-making. Yet there is a fundamental structural gap in the AI productivity loop:

```
AI Conversation (Thinking) --[GAP]--> Execution (Doing)
```

This gap manifests in four measurable failure modes:

1. **Task Loss:** Action items discussed in AI conversations never make it into task management systems. Estimated 40-60% of AI-generated action items are never executed.
2. **Decision Debt:** Decisions reached with AI assistance are not formally recorded, leading to repeated deliberation and organizational confusion.
3. **Ownership Vacuum:** When action items are not formally assigned, accountability defaults to zero. No one acts.
4. **Integration Friction:** Even when users manually try to move AI outputs to tools like Jira or Notion, the effort involved causes significant delay and context switching, often resulting in incomplete or inaccurate task entry.

### 2.2 Market Opportunity

#### Total Addressable Market (TAM)
The global project management software market was valued at $6.8B in 2024 and is projected to reach $15.06B by 2030 (CAGR of 13.7%). The adjacent AI productivity tools market is valued at $12B+ and growing at 25%+ CAGR. Chatly targets the intersection of these two markets.

**TAM:** $18B+ (project management + AI productivity tools combined addressable space)

#### Serviceable Addressable Market (SAM)
Targeting knowledge workers in companies with 10-5,000 employees across technology, consulting, product management, and marketing sectors who use AI assistants and workflow tools.

**SAM:** $3.2B (approximately 18% of TAM, based on AI tool adoption rates and segment sizing)

#### Serviceable Obtainable Market (SOM)
Realistic 3-year capture based on GTM capacity and competitive dynamics.

**SOM:** $48M (Year 3 ARR target, representing ~1.5% of SAM)

#### Market Timing
Three macro trends converge to create an ideal market entry window in 2026:

1. **AI Assistant Ubiquity:** ChatGPT, Claude, Gemini, and Copilot have achieved mass adoption. AI conversations are now a daily work artifact, not a novelty.
2. **Tool Fatigue + Integration Demand:** Users are overwhelmed by disconnected tools. The demand for unified, automated workflows is at an all-time high.
3. **LLM Cost Reduction:** GPT-4-class inference costs have dropped 80%+ since 2023, making real-time conversation analysis economically viable at scale.

### 2.3 The Opportunity Gap

No product in the current market directly addresses the AI-to-execution pipeline problem:

- AI assistants (ChatGPT, Claude) generate outputs but do not structure or route them
- Task managers (Jira, Asana) accept tasks but do not generate them from conversations
- Meeting transcription tools (Otter.ai, Fireflies) extract action items from human meetings, not AI conversations
- Zapier/Make handle integration automation but require manual trigger configuration

Chatly occupies a greenfield category: **AI Conversation Operationalization.**

---

## 3. Target Users & Personas (Jobs-to-Be-Done)

### 3.1 Primary Persona: The Strategic Product Manager

**Name:** Priya, 31
**Role:** Senior Product Manager at a Series B SaaS company (150 employees)
**Tech Stack:** ChatGPT daily for PRD drafting, Jira for task tracking, Notion for documentation, Slack for communication

**Jobs-to-Be-Done:**
- When I finish an AI session for planning a feature, I need my action items in Jira immediately so that nothing gets lost between thinking and building.
- When I use AI to make a product decision, I need that decision formally logged so that I can reference it in future conversations and retrospectives.
- When I delegate tasks that emerge from AI conversations, I need ownership and deadlines attached so that my team has clear accountability.

**Pain Points:**
- Spends 20-30 minutes after every AI session manually creating Jira tickets
- Action items from AI conversations frequently fall through the cracks
- Cannot easily audit which decisions were made with AI assistance vs. without

**Behavioral Characteristics:**
- Power AI user (5+ sessions per day)
- Multi-tool workflow (Jira + Notion + Slack)
- High value on time savings and process reliability

**Willingness to Pay:** $30-50/user/month for a tool that saves 2+ hours/week

---

### 3.2 Secondary Persona: The Engineering Team Lead

**Name:** Rohan, 34
**Role:** Engineering Lead at a fintech startup (80 engineers)
**Tech Stack:** Claude for architecture planning and code review discussions, Linear for issue tracking, GitHub for code, Slack for communication

**Jobs-to-Be-Done:**
- When I use AI to plan a technical architecture, I need the resulting tasks, dependencies, and decisions structured in Linear so that my team can start sprinting immediately.
- When a blocker surfaces during an AI-assisted debugging session, I need that blocker logged and escalated automatically so that it is not forgotten.
- When I conduct an AI-assisted retrospective, I need action items auto-assigned to team members so that we actually improve.

**Pain Points:**
- Technical planning in AI tools produces rich context that is then painstakingly re-entered into Linear
- Blockers identified in AI conversations are not systematically tracked
- Sprint planning takes an additional hour of setup after AI-assisted planning sessions

**Willingness to Pay:** $25-40/user/month (team license preferred)

---

### 3.3 Tertiary Persona: The Strategy Consultant

**Name:** Anjali, 28
**Role:** Associate at a management consulting firm
**Tech Stack:** ChatGPT + Gemini for research and deck preparation, Notion for documentation, Trello for personal task management

**Jobs-to-Be-Done:**
- When I conduct AI research sessions for client deliverables, I need key decisions and action items documented automatically so that I can maintain a clean audit trail.
- When I work across multiple client projects simultaneously, I need AI conversation outputs organized by project so that context does not bleed across engagements.
- When I share AI-generated insights with clients, I need them in structured, professional formats that can be directly imported into client-facing tools.

**Pain Points:**
- Manual documentation of AI sessions is time-consuming and error-prone
- No organized system for cross-project AI conversation management
- Clients increasingly ask for documentation of AI-assisted analysis processes

**Willingness to Pay:** $20-35/user/month

---

### 3.4 Persona Summary Matrix

| Attribute | Priya (PM) | Rohan (Eng Lead) | Anjali (Consultant) |
|---|---|---|---|
| AI Usage Frequency | 5+ sessions/day | 3-5 sessions/day | 2-4 sessions/day |
| Primary AI Tool | ChatGPT | Claude | ChatGPT + Gemini |
| Primary Task Tool | Jira | Linear | Notion/Trello |
| Team Size | 15-30 | 20-80 | 5-15 |
| Budget Sensitivity | Medium | Low | High |
| Integration Priority | Jira, Notion, Slack | Linear, GitHub, Slack | Notion, Trello |
| MVP Feature Priority | Action extraction, Jira sync | Decision logging, Linear sync | Multi-project org, export |

---

## 4. Product Goals & OKRs

### 4.1 Product Vision Statement
Chatly makes every AI conversation executable — transforming the raw output of AI-assisted thinking into structured, assigned, tracked work.

### 4.2 Strategic Pillars

1. **Extraction Accuracy:** Be the most accurate AI conversation parser in the market
2. **Integration Breadth:** Support every major workflow tool without friction
3. **Zero-Interruption UX:** Work invisibly in the background; surface value without adding workflow steps
4. **Trust and Control:** Give users full visibility into what was extracted and why, with easy correction

---

### 4.3 OKRs by Quarter

#### Q1 2026 (MVP Launch — Weeks 1-16)

**Objective 1: Ship a high-quality MVP that validates core value proposition**

| Key Result | Measurement | Target |
|---|---|---|
| KR1.1 | Beta users onboarded | 200 |
| KR1.2 | Avg. action item extraction accuracy (P/R F1) | ≥ 82% |
| KR1.3 | Integrations live at launch | 3 (Jira, Notion, Slack) |
| KR1.4 | Avg. session setup time post-onboarding | < 5 minutes |

**Objective 2: Demonstrate user retention and engagement**

| Key Result | Measurement | Target |
|---|---|---|
| KR2.1 | Week-4 retention rate (beta) | ≥ 55% |
| KR2.2 | Avg. sessions processed per user per week | ≥ 4 |
| KR2.3 | NPS score at end of beta | ≥ 40 |

---

#### Q2 2026 (V1 Launch — General Availability)

**Objective 3: Achieve initial commercial traction**

| Key Result | Measurement | Target |
|---|---|---|
| KR3.1 | Paying customers (teams) | 50 |
| KR3.2 | Monthly Recurring Revenue | $75,000 |
| KR3.3 | Integration suite expanded | 6 tools |
| KR3.4 | Customer churn rate | < 5%/month |

**Objective 4: Scale extraction quality**

| Key Result | Measurement | Target |
|---|---|---|
| KR4.1 | Extraction F1 score | ≥ 88% |
| KR4.2 | Pipeline sync failure rate | < 2% |
| KR4.3 | Avg. latency for post-session processing | < 30 seconds |

---

#### Q3-Q4 2026 (V2 — Platform Maturity)

**Objective 5: Establish Chatly as the category leader in AI conversation operationalization**

| Key Result | Measurement | Target |
|---|---|---|
| KR5.1 | ARR | $1.5M |
| KR5.2 | Paying teams | 200+ |
| KR5.3 | Integration coverage (tools) | 10+ |
| KR5.4 | Enterprise deals (50+ seat) | 5 |
| KR5.5 | Analyst recognition / press mentions | 10+ |

---

## 5. Feature Requirements (Core + Advanced)

### Priority Definitions
- **P0 — Must Have (MVP):** Blocks product from shipping; fundamental to core value proposition
- **P1 — Should Have (V1):** Significantly enhances value; ships within 90 days of MVP
- **P2 — Nice to Have (V2+):** Adds differentiation; scheduled for V2 roadmap

---

### 5.1 Core Feature Set

#### F-01: AI Conversation Ingestion Engine (P0)

**Description:** The system must accept AI conversation transcripts via multiple input methods and normalize them into a common internal format for downstream NLP processing.

**Input Methods:**
- Manual paste (text input field in Chatly UI)
- File upload (.txt, .json, .md, .docx, .pdf)
- Browser extension for live capture from ChatGPT, Claude, Gemini, Copilot web UIs
- API endpoint (for programmatic ingestion from custom AI tools)
- Webhook listener (for AI platforms that support webhook callbacks)

**Normalization Requirements:**
- Strip UI chrome, timestamps, and formatting artifacts
- Identify and label speaker turns (User / AI)
- Segment conversation into logical blocks (topic segments)
- Handle multi-turn conversations of up to 50,000 tokens

**Acceptance Criteria:**
- System accepts all listed input methods without error
- Normalization preserves full semantic content
- Transcripts up to 50,000 tokens processed without timeout
- Processing initiation confirmed to user within 2 seconds of submission

---

#### F-02: NLP Extraction Pipeline (P0)

**Description:** A multi-stage NLP pipeline that analyzes normalized conversation content and extracts structured entities.

**Extracted Entity Types:**

| Entity | Description | Example |
|---|---|---|
| Action Item | A concrete task to be performed | "Build the authentication module" |
| Decision | A conclusion or choice reached | "We will use PostgreSQL over MongoDB" |
| Owner | A person or role responsible | "Rohan", "the design team" |
| Deadline | A time constraint or date | "by end of Q2", "Friday" |
| Blocker | An impediment to progress | "Waiting on API credentials from vendor" |
| Context Tag | Topic or project label | "#backend", "#product-launch" |
| Priority Signal | Urgency indicators | "urgent", "critical", "must have" |

**Pipeline Stages:**
1. **Preprocessing:** Tokenization, POS tagging, named entity recognition
2. **Semantic Role Labeling:** Identify agent (owner), action (verb), object (task), temporal (deadline)
3. **Classification:** Binary classifiers for action item vs. decision vs. blocker
4. **Resolution:** Coreference resolution to link pronouns to named entities
5. **Confidence Scoring:** Each extracted item receives a confidence score (0.0-1.0)
6. **Structured Output:** JSON schema output for each extracted entity

**Acceptance Criteria:**
- Extraction F1 score ≥ 82% on benchmark dataset at MVP, ≥ 88% at V1
- Confidence scores calibrated within 10% of actual accuracy
- Pipeline processes 10,000 tokens in < 8 seconds
- All outputs conform to defined JSON schema

---

#### F-03: Extraction Review & Correction UI (P0)

**Description:** A user interface that presents extracted items for review before syncing to workflow tools. Users must be able to confirm, edit, reject, or add items.

**UI Components:**
- Extraction summary panel (counts of action items, decisions, blockers)
- Item cards for each extracted entity with source quote highlighted in conversation
- Inline editing for item text, owner, deadline, priority
- Confidence indicator per item (color-coded: green ≥ 80%, yellow 50-79%, red < 50%)
- Bulk actions: approve all, reject all, approve high-confidence only
- Add manual item button
- Source conversation panel with highlighting on extraction source text

**Acceptance Criteria:**
- All extracted items displayed within 3 seconds of extraction completion
- Source highlighting accurately maps to correct conversation segment
- Edits persisted immediately (no save button required)
- Bulk approve action processes all items in < 2 seconds

---

#### F-04: Execution Pipeline Builder (P0)

**Description:** After review, Chatly generates a structured execution pipeline — an ordered, linked set of tasks with dependencies, owners, and deadlines — ready for export to workflow tools.

**Pipeline Features:**
- Auto-dependency detection (items referencing shared entities linked)
- Priority ordering based on priority signals and deadline proximity
- Pipeline visualization (Kanban-style board and list view)
- Group by: Owner, Priority, Topic, Deadline
- Export as: Jira Epic+Stories, Notion page, Linear project, plain Markdown

**Acceptance Criteria:**
- Pipeline generated from approved extractions in < 5 seconds
- Dependency links accurately reflect conversational sequencing
- All four view modes render correctly across desktop breakpoints
- Export to at least 3 integration targets functional at MVP

---

#### F-05: Workflow Integration Sync (P0)

**Description:** One-click or automated synchronization of the generated execution pipeline into connected workflow tools.

**MVP Integrations (P0):**
- Jira (create Issues, Epics, Sub-tasks; assign owner; set due date; set priority)
- Notion (create Database entries or Page blocks; populate properties)
- Slack (post structured summary to designated channel)

**Sync Behavior:**
- OAuth 2.0 authentication with each integration
- Field mapping UI: Chatly fields mapped to integration fields (configurable per workspace)
- Conflict detection: check for duplicate tasks before creating
- Sync status tracking: pending, synced, failed, manually resolved
- Retry logic: failed syncs retry 3x with exponential backoff
- Webhook listener for sync confirmation from target tool

**Acceptance Criteria:**
- OAuth flow completes in < 3 steps per integration
- Field mapping UI allows mapping all Chatly fields to target tool fields
- Sync failure rate < 2% under normal operating conditions
- Users notified of sync failures within 30 seconds

---

#### F-06: Conversation & Pipeline Dashboard (P0)

**Description:** A centralized dashboard where users can view all past conversations, their extraction status, pipeline status, and sync status across all integrations.

**Dashboard Views:**
- All Sessions (list with search, filter by date/tool/status/owner)
- Session Detail (conversation + extractions + pipeline + sync log)
- My Tasks (cross-session view of items assigned to the logged-in user)
- Team Overview (admin view: all sessions across workspace members)

**Acceptance Criteria:**
- Dashboard loads within 2 seconds for workspaces with up to 500 sessions
- Search returns results within 1 second
- Session detail accurately reflects real-time sync status

---

#### F-07: Workspace & Team Management (P0)

**Description:** Multi-user workspace management with role-based access control.

**Roles:**
- Admin: Full access, billing management, integration setup, team management
- Member: Can process conversations, view own sessions, sync to connected tools
- Viewer: Read-only access to sessions and pipelines (no sync capability)

**Features:**
- Invite by email with role assignment
- SSO support (Google OAuth at MVP; SAML at V1)
- Workspace-level integration configuration
- Per-member integration permission override

**Acceptance Criteria:**
- Role permissions enforced server-side (not just UI)
- Invite flow completes in < 2 minutes from send to onboarded
- Admin can revoke access with immediate effect

---

### 5.2 Advanced Feature Set

#### F-08: Real-Time Processing Mode (P1)

**Description:** Browser extension monitors active AI conversations and processes them in near-real-time, surfacing extractions as the conversation progresses rather than post-session.

**Behavior:**
- Extension detects supported AI platform (ChatGPT, Claude, Gemini, Copilot)
- On each AI response, extension sends incremental transcript delta to Chatly API
- Extractions appear in a side panel overlay within 3 seconds of response completion
- User can approve/reject/edit inline in the overlay
- Approved items queue for sync without interrupting the conversation

**Acceptance Criteria:**
- Extension available for Chrome and Edge at P1
- Side panel overlay does not impact AI platform page performance by > 5%
- Incremental extraction latency < 3 seconds per AI response
- Items extracted in real-time identical to post-session extraction (consistency)

---

#### F-09: Decision Log & Knowledge Base (P1)

**Description:** A persistent, searchable log of all decisions extracted across all conversations, functioning as an organizational memory of AI-assisted decisions.

**Features:**
- Decision cards with: decision text, context, conversation source, date, participants
- Tag-based organization
- Full-text search with semantic similarity matching
- Link related decisions across sessions
- Decision timeline view (chronological history for a project/topic)
- Export to Notion page, Confluence page, or PDF

**Acceptance Criteria:**
- Decision log searchable across all workspace sessions in < 1 second
- Semantic search returns relevant decisions even when exact keywords are absent
- Export formats render correctly in target tools

---

#### F-10: Owner Assignment & Mention Resolution (P1)

**Description:** Intelligent owner resolution that maps mentioned names or roles from AI conversations to actual workspace members or external stakeholders.

**Features:**
- Workspace member directory integration for mention resolution
- Fuzzy matching: "Rohan" resolved to "Rohan Mehta (rohan@company.com)"
- Role-based assignment: "the design team" routes to team group
- Unresolved owner: flag for manual assignment before sync
- Integration-specific owner mapping (e.g., Jira username != Slack handle)

**Acceptance Criteria:**
- Known member mentions resolved with 95%+ accuracy
- Ambiguous mentions flagged for human review, never silently misassigned
- Owner maps persisted per workspace for continuous improvement

---

#### F-11: Deadline Normalization & Calendar Sync (P1)

**Description:** Natural language deadline extraction and normalization to absolute dates, with optional sync to Google Calendar or Outlook.

**Features:**
- NLP deadline resolution: "by end of Q2" → June 30, 2026; "next Friday" → contextual resolution
- Timezone-aware deadline storage
- Calendar event creation for task deadlines (Google Calendar, Outlook)
- Deadline conflict detection: alert when multiple high-priority items share the same deadline
- Deadline drift alerts: notify owner when deadline passes without task completion

**Acceptance Criteria:**
- Relative deadline phrases normalized correctly in 90%+ of cases
- Calendar sync creates events matching task names and deadline dates
- Conflict detection alerts generated within 1 minute of pipeline creation

---

#### F-12: Multi-Session Synthesis (P1)

**Description:** Ability to process multiple AI conversation sessions together and produce a unified execution pipeline, identifying cross-session dependencies and conflicting decisions.

**Features:**
- Session grouping by project tag or manual selection
- Cross-session deduplication (identical action items merged)
- Conflict detection: contradictory decisions flagged for human resolution
- Unified pipeline view across selected sessions
- Timeline view: ordered by conversation date

**Acceptance Criteria:**
- Synthesis of up to 10 sessions completes in < 20 seconds
- Duplicate detection achieves 90%+ precision (low false positive rate)
- Conflict flags include specific decision text and source sessions for context

---

#### F-13: AI Conversation Templates (P2)

**Description:** Pre-built conversation templates for common use cases that are optimized for Chatly extraction accuracy. Templates guide users to structure AI conversations in ways that yield higher-quality structured outputs.

**Template Library:**
- Sprint Planning Session
- Product Requirements Brainstorm
- Architecture Review
- Retrospective Analysis
- Competitive Analysis
- Customer Interview Synthesis
- OKR Planning Session

**Features:**
- Template library browsable in Chatly UI
- Copy template prompt to clipboard or inject into supported AI platform via extension
- Template-specific extraction schema (e.g., retro template extracts: what went well, what to improve, action items)
- Community template contributions (V2)

**Acceptance Criteria:**
- 7 templates available at V2 launch
- Template-specific extraction schemas demonstrably improve F1 by 5%+ vs. generic extraction

---

#### F-14: Analytics & Reporting (P2)

**Description:** Workspace-level and individual analytics on AI conversation productivity, task completion rates, and extraction patterns.

**Metrics Dashboard:**
- Sessions processed (total, trend)
- Action items generated vs. completed (completion rate)
- Average time from conversation to task sync
- Top owners (by task volume)
- Integration usage distribution
- Decision log growth over time
- Blocker frequency and resolution time

**Reports:**
- Weekly digest (auto-email to workspace admin and members)
- Sprint summary (tasks derived from sessions in a date range)
- Team productivity report (tasks per member, completion rates)

**Acceptance Criteria:**
- Analytics dashboard loads in < 3 seconds
- Data accurate to within 15-minute refresh window
- Weekly digest email delivered by 8:00 AM Monday in user's timezone

---

#### F-15: API Access & Webhooks (P2)

**Description:** Public REST API and webhook system enabling enterprise customers and developers to integrate Chatly programmatically into custom workflows.

**API Capabilities:**
- Submit conversations for processing
- Retrieve extraction results
- Retrieve pipeline status
- Trigger sync to connected tools
- Manage workspace members and permissions

**Webhook Events:**
- session.processed
- extraction.completed
- pipeline.created
- sync.succeeded
- sync.failed
- item.updated

**Acceptance Criteria:**
- API documented with OpenAPI 3.0 specification
- API authentication via API keys (scoped: read, write, admin)
- Webhook payloads delivered within 5 seconds of event
- 99.9% API uptime SLA for enterprise tier

---

## 6. User Stories & Acceptance Criteria

### 6.1 Ingestion & Processing Stories

---

**US-001: Paste Conversation for Processing**
*As a product manager, I want to paste an AI conversation transcript into Chatly so that I can extract structured action items without manually reviewing the entire chat.*

**Acceptance Criteria:**
- Given I am on the Chatly dashboard, When I click "New Session" and paste text into the input field and click "Process," Then Chatly accepts the input and begins processing within 2 seconds.
- Given the processing completes, When I navigate to the session view, Then I see a list of extracted action items, decisions, blockers, and owners.
- Given the transcript contains no identifiable action items, When processing completes, Then Chatly displays a message: "No action items detected. You can add items manually."

---

**US-002: Upload Conversation File**
*As a consultant, I want to upload an exported conversation file (.txt or .json) so that I can process conversations I have exported from AI tools.*

**Acceptance Criteria:**
- Given I am on the "New Session" screen, When I drag and drop or browse-select a .txt or .json file ≤ 10MB, Then the file uploads and processing begins within 3 seconds.
- Given I upload an unsupported file format, When the upload completes, Then I see an error: "Unsupported file format. Please upload .txt, .json, .md, or .docx files."
- Given I upload a file > 10MB, Then I see an error: "File exceeds 10MB limit. Please split the conversation and upload in parts."

---

**US-003: Browser Extension Live Capture**
*As an engineering lead, I want the Chatly browser extension to capture my conversation with Claude in real time so that I do not have to manually export and upload transcripts.*

**Acceptance Criteria:**
- Given the Chatly extension is installed and I am logged into Chatly, When I open a supported AI platform (Claude.ai, ChatGPT.com), Then the Chatly side panel activates automatically.
- Given the AI model delivers a response, When 1 second passes after response completion, Then the side panel updates with any new extracted items from that response.
- Given I toggle the extension off via the side panel, When I resume the conversation, Then no data is captured or sent to Chatly.

---

### 6.2 Extraction & Review Stories

---

**US-004: Review Extracted Action Items**
*As a product manager, I want to review all extracted action items before they are synced to Jira so that I can ensure accuracy and avoid creating incorrect tickets.*

**Acceptance Criteria:**
- Given a session has been processed, When I open the extraction review screen, Then all extracted action items are displayed with their source quote highlighted in the conversation panel.
- Given an extracted item has a confidence score below 50%, When it is displayed, Then it is visually flagged with a red indicator and a tooltip explaining "Low confidence — please review."
- Given I click "Edit" on an action item, When I modify the text and click away, Then the item is updated without requiring a separate save action.

---

**US-005: Reject Irrelevant Extractions**
*As an engineering lead, I want to reject extracted items that are not genuine action items so that my pipeline does not contain noise.*

**Acceptance Criteria:**
- Given an extracted item is displayed, When I click the "Reject" button, Then the item is immediately removed from the extraction list and moved to a "Rejected" section accessible via a toggle.
- Given I have rejected items in the "Rejected" section, When I click "Restore" on a rejected item, Then the item moves back to the active extraction list.
- Given I reject more than 3 items in a session, When the session completes, Then Chatly records the rejection context for model improvement.

---

**US-006: Manually Add Action Items**
*As a consultant, I want to manually add action items that the AI did not extract so that my pipeline is complete even if the conversation was ambiguous.*

**Acceptance Criteria:**
- Given I am on the extraction review screen, When I click "Add Item," Then a blank item card appears in edit mode.
- Given I fill in the item text and click away, When the item is saved, Then it appears in the active extraction list marked as "Manually Added."
- Given I add an item manually, When I sync to a workflow tool, Then manually added items are synced alongside extracted items with no distinction in the target tool.

---

### 6.3 Pipeline & Integration Stories

---

**US-007: Sync Execution Pipeline to Jira**
*As a product manager, I want to sync my approved action items to Jira with one click so that my team can immediately begin working without me manually creating tickets.*

**Acceptance Criteria:**
- Given Jira is connected to my workspace and I have approved extractions, When I click "Sync to Jira," Then Chatly creates Jira issues for each approved action item within 10 seconds.
- Given an action item has an owner resolved to a Jira user, When the issue is created, Then the issue is assigned to that Jira user.
- Given a deadline is extracted and normalized, When the issue is created, Then the Jira due date field is set to the normalized deadline.
- Given a Jira sync fails for one or more items, When the sync completes, Then Chatly displays: "X items failed to sync. View details," with specific error reasons per item.

---

**US-008: Post Pipeline Summary to Slack**
*As a team lead, I want Chatly to post a formatted summary of the extracted pipeline to a Slack channel so that my team is immediately informed of new tasks without checking another tool.*

**Acceptance Criteria:**
- Given Slack is connected and a Slack channel is configured for the workspace, When I click "Post to Slack," Then a formatted message appears in the configured Slack channel within 5 seconds.
- Given the Slack message is posted, When a team member views it, Then the message includes: session name, total items, top 3 action items with owners and deadlines, and a link to the full pipeline in Chatly.
- Given Slack is not connected, When I click "Post to Slack," Then I am prompted to connect Slack via OAuth.

---

**US-009: Create Notion Page from Pipeline**
*As a consultant, I want to create a Notion page from my execution pipeline so that I can share a structured deliverable with my client directly from a Notion workspace.*

**Acceptance Criteria:**
- Given Notion is connected and I select a target Notion database, When I click "Export to Notion," Then a new Notion page is created with action items as database entries within 15 seconds.
- Given the Notion page is created, When I view it in Notion, Then each action item appears as a separate row with columns: Task, Owner, Deadline, Priority, Status (default: Not Started).
- Given I have previously exported this session to Notion, When I click "Export to Notion" again, Then Chatly asks: "A Notion page already exists for this session. Update existing page or create new?" before proceeding.

---

### 6.4 Dashboard & Management Stories

---

**US-010: View All Past Sessions**
*As a product manager, I want to view all my past Chatly sessions in a dashboard so that I can track the status of every pipeline I have created.*

**Acceptance Criteria:**
- Given I navigate to the Dashboard, When the page loads, Then I see a list of all sessions sorted by most recent, with columns: Session Name, Date, Items Extracted, Sync Status, Integrations Used.
- Given I use the search bar, When I type a keyword, Then sessions with matching content in name or extracted items appear within 1 second.
- Given I apply a filter (e.g., "Synced to Jira"), When the filter is applied, Then only sessions with at least one Jira-synced item are displayed.

---

**US-011: View Team Sessions (Admin)**
*As a workspace admin, I want to view all sessions across my team so that I can monitor overall AI conversation activity and pipeline health.*

**Acceptance Criteria:**
- Given I am an Admin and navigate to "Team Overview," When the page loads, Then I see all sessions across all workspace members with member name visible.
- Given I click on a team member's session, When the session detail opens, Then I can view the full extraction and pipeline but cannot edit items unless I am the session owner or an Admin.
- Given I am a Member (not Admin), When I navigate to "Team Overview," Then I see a 403 Forbidden error or I am redirected to My Sessions.

---

## 7. Technical Architecture Overview

> **Wireframes:** [System Architecture →](https://www.figma.com/online-whiteboard/create-diagram/08e00113-f8f4-4e90-933f-7612d1342572?utm_source=claude&utm_content=edit_in_figjam) | [Conversation State Diagram →](https://www.figma.com/online-whiteboard/create-diagram/198d263f-8ff0-49ba-a0e4-1f0eda8513bd?utm_source=claude&utm_content=edit_in_figjam)

### 7.1 High-Level Architecture

Chatly is built on a microservices architecture deployed on AWS, designed for horizontal scalability, fault isolation, and independent service deployment.

```
+------------------+     +------------------+     +------------------+
|   Client Layer   |     |   API Gateway    |     |   Auth Service   |
|                  |     |                  |     |                  |
|  Web App (React) |---->| REST + WebSocket |---->| JWT / OAuth 2.0  |
|  Browser Ext.    |     | Rate Limiting    |     | SSO (SAML V1)    |
|  Mobile (V2)     |     | Request Routing  |     |                  |
+------------------+     +------------------+     +------------------+
                                  |
         +------------------------+-------------------------+
         |                        |                         |
+--------v--------+   +-----------v--------+   +----------v--------+
| Ingestion Svc   |   | NLP Pipeline Svc   |   | Integration Svc   |
|                 |   |                    |   |                   |
| - File parsing  |   | - Preprocessing    |   | - Jira adapter    |
| - Normalization |   | - Entity extract.  |   | - Notion adapter  |
| - Segmentation  |   | - Classification   |   | - Slack adapter   |
| - Token count   |   | - Coref resol.     |   | - Linear adapter  |
|                 |   | - Confidence score |   | - Sync queue      |
+--------+--------+   +-----------+--------+   +----------+--------+
         |                        |                         |
         +------------------------+-------------------------+
                                  |
                    +-------------v-------------+
                    |    Message Broker (SQS)   |
                    |    + Event Bus (SNS)       |
                    +-------------+-------------+
                                  |
              +-------------------+-------------------+
              |                   |                   |
    +---------v------+   +--------v-------+  +--------v-------+
    |  Pipeline Svc  |   |  Storage Layer |  |  Notif. Svc    |
    |                |   |                |  |                |
    | - Pipeline gen |   | - PostgreSQL   |  | - Email        |
    | - Dep. detect  |   |   (primary DB) |  | - Slack notif. |
    | - Priority ord |   | - Redis cache  |  | - In-app notif.|
    | - Export gen   |   | - S3 (files)   |  |                |
    +----------------+   | - Pinecone     |  +----------------+
                         |   (vector DB)  |
                         +----------------+
```

### 7.2 NLP Pipeline Architecture

The NLP pipeline is the core intellectual property of Chatly. It uses a hybrid approach combining fine-tuned transformer models with LLM API calls for disambiguation.

```
Input Transcript
       |
       v
[Stage 1: Preprocessing]
- Sentence tokenization (SpaCy)
- POS tagging
- Named Entity Recognition (SpaCy en_core_web_trf)
- Speaker turn labeling
       |
       v
[Stage 2: Semantic Role Labeling]
- Agent / Action / Object / Temporal extraction
- AllenNLP SRL or fine-tuned BERT-SRL model
       |
       v
[Stage 3: Classification]
- Action Item classifier (fine-tuned RoBERTa)
- Decision classifier (fine-tuned RoBERTa)
- Blocker classifier (fine-tuned RoBERTa)
- Multi-label capable (one sentence can be action + decision)
       |
       v
[Stage 4: Coreference Resolution]
- SpaCy neuralcoref or FastCoref
- Resolve pronouns and references to named entities
       |
       v
[Stage 5: LLM Disambiguation]
- Low-confidence items (score < 0.65) passed to GPT-4o mini
- LLM confirms, corrects, or discards
- Adds natural language deadline normalization
       |
       v
[Stage 6: Structured Output]
- JSON schema validation
- Confidence scoring
- Source span mapping
       |
       v
Structured Extraction Result (JSON)
```

**LLM Cost Management Strategy:**
- Only items with confidence < 0.65 sent to LLM (reduces LLM calls by ~60%)
- GPT-4o mini used (cost: ~$0.15/1M input tokens) rather than GPT-4o
- Caching: identical sentence patterns cached in Redis (30-day TTL)
- Batch processing for post-session mode (lower latency requirement, lower cost tier)

### 7.3 Data Model (Core Entities)

```sql
-- Workspace
workspace (
  id UUID PRIMARY KEY,
  name VARCHAR(255),
  plan ENUM('free', 'pro', 'enterprise'),
  created_at TIMESTAMP,
  settings JSONB
)

-- User
user (
  id UUID PRIMARY KEY,
  workspace_id UUID REFERENCES workspace(id),
  email VARCHAR(255) UNIQUE,
  name VARCHAR(255),
  role ENUM('admin', 'member', 'viewer'),
  created_at TIMESTAMP
)

-- Session (a processed AI conversation)
session (
  id UUID PRIMARY KEY,
  workspace_id UUID REFERENCES workspace(id),
  owner_id UUID REFERENCES user(id),
  name VARCHAR(500),
  raw_transcript TEXT,
  normalized_transcript JSONB,
  token_count INTEGER,
  status ENUM('pending', 'processing', 'extracted', 'reviewed', 'synced', 'error'),
  source ENUM('paste', 'upload', 'extension', 'api'),
  source_platform VARCHAR(100),
  created_at TIMESTAMP,
  processed_at TIMESTAMP
)

-- Extracted Item
extracted_item (
  id UUID PRIMARY KEY,
  session_id UUID REFERENCES session(id),
  item_type ENUM('action_item', 'decision', 'blocker', 'context_tag'),
  text TEXT,
  source_span_start INTEGER,
  source_span_end INTEGER,
  owner_raw VARCHAR(255),
  owner_resolved_user_id UUID REFERENCES user(id),
  deadline_raw VARCHAR(255),
  deadline_normalized TIMESTAMP,
  priority ENUM('critical', 'high', 'medium', 'low', 'unset'),
  confidence_score DECIMAL(3,2),
  status ENUM('pending_review', 'approved', 'rejected', 'manually_added'),
  is_manual BOOLEAN DEFAULT FALSE,
  created_at TIMESTAMP,
  updated_at TIMESTAMP
)

-- Pipeline
pipeline (
  id UUID PRIMARY KEY,
  session_id UUID REFERENCES session(id),
  workspace_id UUID REFERENCES workspace(id),
  status ENUM('draft', 'active', 'archived'),
  created_at TIMESTAMP
)

-- Pipeline Item (approved extraction linked to pipeline)
pipeline_item (
  id UUID PRIMARY KEY,
  pipeline_id UUID REFERENCES pipeline(id),
  extracted_item_id UUID REFERENCES extracted_item(id),
  sort_order INTEGER,
  dependency_ids UUID[],
  created_at TIMESTAMP
)

-- Integration Configuration
integration_config (
  id UUID PRIMARY KEY,
  workspace_id UUID REFERENCES workspace(id),
  tool ENUM('jira', 'notion', 'slack', 'linear', 'trello', 'asana', 'github'),
  oauth_token_encrypted TEXT,
  field_mappings JSONB,
  default_project_id VARCHAR(255),
  created_at TIMESTAMP,
  updated_at TIMESTAMP
)

-- Sync Log
sync_log (
  id UUID PRIMARY KEY,
  pipeline_item_id UUID REFERENCES pipeline_item(id),
  integration_config_id UUID REFERENCES integration_config(id),
  tool VARCHAR(50),
  external_item_id VARCHAR(255),
  external_item_url TEXT,
  status ENUM('pending', 'synced', 'failed', 'retrying'),
  error_message TEXT,
  synced_at TIMESTAMP,
  retry_count INTEGER DEFAULT 0
)
```

### 7.4 API Design (REST)

**Base URL:** `https://api.chatly.io/v1`

**Authentication:** Bearer token (JWT) in Authorization header. API keys for programmatic access.

**Core Endpoints:**

```
POST   /sessions                     Create and submit a session for processing
GET    /sessions                     List sessions (paginated, filterable)
GET    /sessions/{id}                Get session detail
DELETE /sessions/{id}                Delete session

GET    /sessions/{id}/extractions    Get all extracted items for a session
PATCH  /extractions/{id}             Update an extracted item (text, owner, deadline, status)
POST   /sessions/{id}/extractions    Manually add an extracted item

POST   /sessions/{id}/pipeline       Generate pipeline from approved extractions
GET    /sessions/{id}/pipeline       Get pipeline for a session
POST   /pipelines/{id}/sync          Trigger sync to integration
GET    /pipelines/{id}/sync-log      Get sync log for pipeline

GET    /workspaces/{id}/integrations List configured integrations
POST   /workspaces/{id}/integrations Add integration (triggers OAuth flow)
DELETE /integrations/{id}            Remove integration

GET    /workspaces/{id}/members      List members
POST   /workspaces/{id}/members      Invite member
PATCH  /members/{id}                 Update member role
DELETE /members/{id}                 Remove member
```

**WebSocket API:**
`wss://api.chatly.io/v1/sessions/{id}/stream`
Used for real-time extraction progress updates during processing.

**Rate Limits:**

| Tier | Requests/Minute | Sessions/Day | Token Limit/Session |
|---|---|---|---|
| Free | 30 | 5 | 10,000 |
| Pro | 120 | 50 | 50,000 |
| Enterprise | 600 | Unlimited | 200,000 |

### 7.5 Technology Stack

| Layer | Technology | Rationale |
|---|---|---|
| Frontend (Web) | React 18 + TypeScript | Team familiarity, component ecosystem |
| Frontend (Extension) | Chrome Extension Manifest V3 | Required for Chrome Web Store compatibility |
| Backend (API) | Node.js + Express (API Gateway) | Fast iteration; WebSocket support |
| NLP Services | Python + FastAPI | Python ML ecosystem; SpaCy, HuggingFace |
| Pipeline & Integration Svc | Python + FastAPI | Consistent with NLP service language |
| Primary Database | PostgreSQL 16 (AWS RDS) | Relational integrity; JSONB for flexibility |
| Cache | Redis (AWS ElastiCache) | Session caching; rate limiting; NLP result cache |
| Vector Database | Pinecone | Semantic search for Decision Log |
| Object Storage | AWS S3 | Conversation file uploads; export artifacts |
| Message Queue | AWS SQS | Async NLP job queue |
| Event Bus | AWS SNS | Cross-service event propagation |
| LLM API | OpenAI GPT-4o mini | Cost-efficient disambiguation |
| NLP Models | HuggingFace Transformers (self-hosted) | Fine-tuned RoBERTa classifiers |
| CI/CD | GitHub Actions | Team familiarity |
| Infrastructure | AWS (ECS Fargate + RDS + ElastiCache) | Managed services; autoscaling |
| Monitoring | Datadog | APM, logs, custom metrics |
| Error Tracking | Sentry | Real-time error alerting |

---

## 8. Integrations & Third-Party Tools

### 8.1 Integration Priority Matrix

| Tool | Priority | Data Pushed | Users Served |
|---|---|---|---|
| Jira | P0 (MVP) | Issues, Epics, Sub-tasks, Assignees, Due Dates, Priority | PMs, Eng Leads |
| Notion | P0 (MVP) | Database entries, Page blocks, Properties | PMs, Consultants |
| Slack | P0 (MVP) | Channel messages, DMs, Formatted summaries | All personas |
| Linear | P1 (V1) | Issues, Projects, Cycles, Assignees, Priorities | Eng Leads |
| Trello | P1 (V1) | Cards, Lists, Members, Due Dates, Labels | Consultants, PMs |
| Asana | P1 (V1) | Tasks, Sections, Assignees, Due Dates | PMs, Ops teams |
| GitHub | P1 (V1) | Issues, Labels, Assignees, Milestones | Eng Leads |
| Google Calendar | P1 (V1) | Events (deadline-based) | All personas |
| Outlook Calendar | P2 (V2) | Events (deadline-based) | Enterprise users |
| Confluence | P2 (V2) | Pages, Decision logs | Enterprise users |
| Monday.com | P2 (V2) | Items, Subitems, Assignees | Ops teams |
| ClickUp | P2 (V2) | Tasks, Docs, Assignees | Ops, PMs |
| Zapier | P2 (V2) | Webhook trigger for custom workflows | Power users |

### 8.2 Integration Implementation Details

#### Jira Integration
- **Auth:** OAuth 2.0 with Atlassian identity
- **API:** Jira Cloud REST API v3
- **Scope:** `read:jira-work`, `write:jira-work`, `read:jira-user`
- **Field Mapping:** Chatly action item → Jira Issue (Story type); Chatly priority → Jira priority; Chatly deadline → Jira due date; Chatly owner → Jira assignee
- **Epic Handling:** If session has 5+ action items, option to create parent Epic grouping
- **Webhook:** Listen to Jira issue status changes to update Chatly sync log

#### Notion Integration
- **Auth:** Notion OAuth
- **API:** Notion API v1 (Blocks + Databases)
- **Field Mapping:** Chatly action item → Notion Database row; properties: Name (title), Owner (person), Deadline (date), Priority (select), Status (select, default "Not Started"), Source (url, links to Chatly session)
- **Page creation:** Option to create structured Notion page instead of database rows (for decision log export)

#### Slack Integration
- **Auth:** Slack OAuth 2.0 (Bot token)
- **API:** Slack Web API
- **Scopes:** `chat:write`, `channels:read`, `users:read`
- **Message Format:** Block Kit formatted message with summary section and task list
- **Channel Configuration:** Workspace admin configures default channel; per-session override available

---

## 9. UX/UI Requirements & User Flows

> **Wireframes:** [User Flow →](https://www.figma.com/online-whiteboard/create-diagram/9169c202-6167-4eea-875c-ef19c59c0fbd?utm_source=claude&utm_content=edit_in_figjam) | [Sequence Diagram →](https://www.figma.com/online-whiteboard/create-diagram/a18914bf-e109-4f9c-8ca7-a751513253b5?utm_source=claude&utm_content=edit_in_figjam) | [State Diagram →](https://www.figma.com/online-whiteboard/create-diagram/198d263f-8ff0-49ba-a0e4-1f0eda8513bd?utm_source=claude&utm_content=edit_in_figjam)

### 9.1 Design Principles

1. **Minimal Friction:** The most common actions (process, review, sync) must be completable in 3 clicks or fewer.
2. **Transparency:** Users always understand what was extracted and why, including confidence indicators and source highlighting.
3. **Progressive Disclosure:** Advanced features (multi-session synthesis, decision log, analytics) are accessible but never presented before core value is delivered.
4. **Error Recovery:** Every failure state includes a clear explanation and actionable recovery path.
5. **Accessibility:** WCAG 2.1 Level AA compliance required for all UI components.

### 9.2 Core User Flows

#### Flow 1: First-Time User Onboarding (Target: < 5 minutes to first processed session)

```
1. Sign Up (Google OAuth or email)
       |
2. Workspace Setup
   - Workspace name
   - Invite team members (optional, skippable)
       |
3. Connect First Integration
   - Prompted to connect Jira, Notion, or Slack
   - OAuth flow (< 3 steps)
   - Field mapping defaults pre-filled
       |
4. Process First Session
   - Guided prompt: "Paste a recent AI conversation below"
   - Sample conversation provided if user selects "Use Example"
   - Processing animation (< 10 seconds)
       |
5. Review Extractions
   - Results displayed with annotations
   - Tooltip guides: "These are your action items. Click to edit."
       |
6. Sync to Tool
   - One-click sync to connected tool
   - Success confirmation with link to created items
       |
7. Dashboard Redirect
   - "Your pipeline is live. Here's your dashboard."
```

#### Flow 2: Regular Session Processing (Target: < 2 minutes from paste to sync)

```
1. Dashboard → "New Session" button
       |
2. Input Method Selection
   - Paste Text (default)
   - Upload File
   - Import from Extension (if installed)
       |
3. Optional: Session Name + Project Tag
       |
4. Submit for Processing
   - Processing status bar displayed
       |
5. Extraction Review Screen
   - Left panel: original conversation (source spans highlighted)
   - Right panel: extracted items grouped by type
   - Actions: Edit | Reject | Add | Approve All
       |
6. Approve and Generate Pipeline
   - Pipeline visualization displayed
   - Dependency lines auto-drawn
       |
7. Sync Selection
   - Select target tool(s) (checkboxes)
   - Confirm field mappings (pre-filled from workspace defaults)
   - Click "Sync"
       |
8. Sync Confirmation
   - Per-item sync status displayed
   - Links to created items in target tools
   - "View in Dashboard" button
```

#### Flow 3: Browser Extension Real-Time Capture

```
1. User opens Claude.ai or ChatGPT.com
       |
2. Chatly extension activates (icon badge: green = active)
       |
3. User conducts conversation with AI
       |
4. Side panel shows extractions in near-real-time
   - Items appear as the conversation progresses
   - Each item: text preview + type badge + confidence
       |
5. Inline Review in Side Panel
   - Approve / Reject / Edit per item
       |
6. End Session
   - User clicks "Finish Session" in side panel
   - All approved items compiled into pipeline
       |
7. Sync (from extension or Chatly web app)
```

### 9.3 Information Architecture

```
Chatly Web App
|
|-- Dashboard (Home)
|   |-- My Sessions (list)
|   |-- Team Sessions (Admin only)
|   |-- My Tasks (cross-session task view)
|   |-- Quick Stats (items today, synced today)
|
|-- New Session
|   |-- Paste / Upload / Import
|   |-- Processing
|   |-- Extraction Review
|   |-- Pipeline Builder
|   |-- Sync
|
|-- Session Detail (/sessions/:id)
|   |-- Overview
|   |-- Extractions
|   |-- Pipeline
|   |-- Sync Log
|   |-- Decision Log
|
|-- Decision Log
|   |-- All Decisions (searchable)
|   |-- By Project Tag
|   |-- By Date Range
|
|-- Analytics (Admin)
|   |-- Workspace Overview
|   |-- Team Activity
|   |-- Sync Performance
|
|-- Settings
    |-- Workspace Settings
    |-- Integrations
    |-- Members & Roles
    |-- Billing
    |-- API Keys
    |-- Profile
```

### 9.4 UI Component Requirements

| Component | Description |
|---|---|
| Conversation Viewer | Split-pane view with syntax-highlighted extraction spans |
| Item Card | Card component with: type badge, text, owner chip, deadline tag, confidence bar, action buttons |
| Confidence Indicator | Color-coded bar + percentage (green ≥ 80%, yellow 50-79%, red < 50%) |
| Pipeline Board | Kanban-style drag-and-drop board; swimlanes by owner or priority |
| Sync Status Badge | Per-item status: Pending / Synced / Failed / Not Synced |
| Integration Connector | OAuth flow modal with step indicator; field mapping table |
| Session List | Virtualized list with search, filter, and sort |

---

## 10. Non-Functional Requirements

### 10.1 Performance Requirements

| Metric | Requirement | Measurement Method |
|---|---|---|
| API response time (p95) | < 200ms for all non-processing endpoints | Datadog APM |
| Post-session processing time | < 30 seconds for sessions up to 10,000 tokens | Internal job duration metric |
| Real-time extraction latency | < 3 seconds per AI response (extension) | Client-side timing log |
| Dashboard load time | < 2 seconds (p95, 500 sessions) | Synthetic monitoring |
| Sync to Jira/Notion/Slack | < 10 seconds per pipeline (< 20 items) | Sync log timestamps |
| Concurrent users supported | 1,000 concurrent users at MVP; 10,000 at V2 | Load test (k6) |
| NLP pipeline throughput | 100 sessions/minute at V1; 1,000 sessions/minute at V2 | Queue depth monitoring |

### 10.2 Availability & Reliability

| Metric | Requirement |
|---|---|
| API uptime SLA | 99.9% (Pro); 99.95% (Enterprise) |
| Planned maintenance windows | < 4 hours/month; off-peak hours only; 48-hour advance notice |
| RTO (Recovery Time Objective) | < 1 hour for total service failure |
| RPO (Recovery Point Objective) | < 15 minutes (database backup frequency) |
| Data redundancy | Multi-AZ RDS; S3 cross-region replication for file uploads |

### 10.3 Security Requirements

| Requirement | Implementation |
|---|---|
| Encryption in transit | TLS 1.3 for all API and web traffic |
| Encryption at rest | AES-256 for database (RDS encryption); S3 SSE |
| OAuth tokens | Encrypted at rest using AES-256; never exposed in logs |
| PII handling | Conversation transcripts treated as sensitive data; no logging of raw transcript content |
| Authentication | JWT with 1-hour expiry; refresh token rotation |
| Authorization | Server-side RBAC enforcement; workspace isolation enforced at DB query level |
| API rate limiting | Per-user and per-workspace limits; IP-based throttling for unauthenticated endpoints |
| Vulnerability management | Automated SAST scanning (Snyk) in CI/CD; quarterly penetration testing |
| Compliance framework | SOC 2 Type I at V1 launch; SOC 2 Type II audit by end of Year 1 |
| GDPR compliance | Data residency selection (US/EU); right-to-deletion API; DPA available for enterprise |
| Data retention | Default 12-month session retention; configurable per workspace (Pro+) |

### 10.4 Scalability Requirements

| Scenario | Requirement |
|---|---|
| Session volume growth | Architecture supports 10x volume increase without re-architecture |
| New integration addition | New integration adapter deployable independently without downtime |
| NLP model upgrade | Model hot-swap capability (canary deployment with A/B traffic split) |
| Workspace data isolation | No cross-workspace data leakage under any failure condition |
| Token limit increase | Configurable per tier without code changes |

### 10.5 Usability Requirements

| Requirement | Specification |
|---|---|
| Accessibility | WCAG 2.1 Level AA compliance |
| Browser support | Chrome 110+, Edge 110+, Firefox 115+, Safari 16+ |
| Responsive design | Fully functional at 1280px, 1440px, 1920px desktop widths |
| Keyboard navigation | All core actions completable via keyboard only |
| Screen reader support | ARIA labels on all interactive components |
| Internationalization | English at MVP; internationalization framework (i18n) integrated from Day 1 for V2 |

---

## 11. Success Metrics & Analytics Framework

### 11.1 North Star Metric

**Execution Pipelines Created per Week (Workspace-Level)**

This metric captures the frequency with which users are converting AI conversations into structured, actionable pipelines. It measures core product value delivered, not just usage activity.

### 11.2 Metric Hierarchy

#### Acquisition Metrics
| Metric | Target (MVP Beta) | Target (V1) |
|---|---|---|
| Signups | 200 | 1,000 |
| Activation rate (processed ≥1 session) | 70% | 75% |
| Time to first pipeline (from signup) | < 8 minutes | < 5 minutes |

#### Engagement Metrics
| Metric | Target (V1) |
|---|---|
| Sessions processed per active user per week | ≥ 4 |
| Pipeline creation rate (sessions → pipelines) | ≥ 75% |
| Sync rate (pipelines → at least 1 integration sync) | ≥ 60% |
| Extension active users / total users | ≥ 30% |
| DAU/MAU ratio | ≥ 40% |

#### Retention Metrics
| Metric | Target (V1) |
|---|---|
| Week-1 retention | ≥ 65% |
| Month-1 retention | ≥ 50% |
| Month-3 retention | ≥ 35% |
| Churned account recovery rate | ≥ 15% (via win-back campaigns) |

#### Revenue Metrics
| Metric | Target (End of Year 1) |
|---|---|
| MRR | $125,000 |
| ARR | $1.5M |
| Avg. Revenue Per Account (ARPA) | $600/month (team) |
| Gross Revenue Churn | < 5%/month |
| Net Revenue Retention | ≥ 110% |
| LTV:CAC Ratio | ≥ 3:1 |

#### Quality Metrics
| Metric | Target (MVP) | Target (V1) |
|---|---|---|
| NLP Extraction F1 Score | ≥ 82% | ≥ 88% |
| User correction rate (edits per session) | < 2.5 edits | < 1.5 edits |
| Sync failure rate | < 3% | < 1.5% |
| NPS Score | ≥ 35 | ≥ 50 |

### 11.3 Analytics Instrumentation Plan

**Tracking Framework:** Segment (customer data pipeline) → Mixpanel (product analytics) + Amplitude (funnel analysis)

**Key Events to Track:**

| Event Name | Trigger | Properties |
|---|---|---|
| session_submitted | User submits conversation | source, token_count, workspace_id |
| session_processed | Processing completes | duration_ms, items_extracted, session_id |
| item_reviewed | User acts on an extraction | action (approved/rejected/edited), item_type, confidence_score |
| pipeline_created | Pipeline generated | item_count, session_id |
| sync_triggered | User initiates sync | target_tool, item_count |
| sync_completed | Sync finishes | success_count, failure_count, duration_ms |
| integration_connected | User connects new tool | tool_name, workspace_id |
| extension_activated | Extension detects AI platform | platform (chatgpt/claude/gemini) |

**Funnel Definitions:**
1. Acquisition Funnel: Visit → Signup → First Session Submitted → First Pipeline Created → First Sync
2. Engagement Funnel: Login → New Session → Process → Review → Sync
3. Retention Cohort: Weekly cohort analysis by signup date

---

## 12. Go-to-Market Strategy

### 12.1 Positioning

**Positioning Statement:**
For knowledge workers and teams who use AI assistants daily, Chatly is the AI conversation operationalization platform that automatically transforms AI conversations into structured, executed work — unlike manual task entry or generic automation tools, Chatly understands the semantic content of AI conversations and routes tasks, decisions, and ownership directly into the tools your team already uses.

**Category:** AI Conversation Operationalization (category creation strategy)

**Key Messages by Persona:**
- PMs: "Turn every ChatGPT planning session into a Jira sprint in one click."
- Eng Leads: "Stop re-entering architecture decisions into Linear. Chatly does it automatically."
- Consultants: "Deliver AI-assisted projects with clean, auditable documentation. Automatically."

### 12.2 Pricing Model

#### Tiers

| Tier | Price | Target | Limits |
|---|---|---|---|
| Free | $0/month | Individual exploration | 5 sessions/month, 10,000 tokens/session, 1 integration |
| Pro (Individual) | $19/month | Power individual users | 50 sessions/month, 50,000 tokens/session, 3 integrations |
| Team | $49/user/month (min 3 seats) | Small to mid teams | Unlimited sessions, 50,000 tokens/session, all integrations, admin dashboard |
| Enterprise | Custom ($75+/user/month) | Companies 50+ users | Unlimited everything, SSO/SAML, SOC 2, SLA, dedicated support, custom NLP fine-tuning |

**Pricing Strategy Notes:**
- Free tier drives organic viral growth through workspace invitations
- Team tier is the primary growth engine; upsell from individual Pro
- Annual billing at 20% discount to improve cash flow

### 12.3 Distribution Channels

#### Primary Channels

1. **Product-Led Growth (PLG):** Free tier → viral invite loops → team adoption → Team tier conversion
   - Target: 60% of ARR from PLG-originated accounts

2. **App Marketplaces:**
   - Jira Marketplace (Atlassian)
   - Notion Integrations Gallery
   - Slack App Directory
   - These placements provide high-intent discovery at zero CAC

3. **Content Marketing:**
   - SEO-optimized blog: "How to turn ChatGPT outputs into Jira tickets," etc.
   - YouTube: workflow demonstration videos
   - Target: 30,000 monthly organic visitors by Month 6

#### Secondary Channels

4. **Partnership / Co-Marketing:**
   - AI tool partnerships (target: integration spotlight from Notion, Linear)
   - PM community partnerships (Lenny's Newsletter, Product School, Reforge)

5. **Outbound Sales (Enterprise):**
   - Target VP Product, VP Engineering, and Heads of Strategy at 200-2,000 person companies
   - Outbound email + LinkedIn sequencing
   - SDR hire at Month 4 post-launch

6. **Product Hunt Launch:**
   - Coordinated launch for visibility and initial user spike
   - Target: Top 3 Product of the Day

### 12.4 Launch Plan

| Phase | Timeline | Activities |
|---|---|---|
| Pre-Launch (Weeks 1-12) | Build & beta | Private beta with 50 hand-selected users; weekly feedback calls; Product Hunt teaser |
| Beta Expansion (Weeks 12-16) | Soft launch | Open beta waitlist; onboard 200 users; iterate on extraction quality and UX |
| GA Launch (Week 16) | Public launch | Product Hunt launch; press outreach (TechCrunch, The Rundown, Ben's Bites); email blast to waitlist |
| Growth Phase (Months 5-12) | Scale | Content marketing engine; marketplace listings; first outbound sales motion |

---

## 13. Risk Analysis & Mitigation

### 13.1 Risk Register

| Risk ID | Risk | Category | Likelihood | Impact | Severity | Mitigation |
|---|---|---|---|---|---|---|
| R-01 | NLP extraction accuracy insufficient for user trust | Technical | High | High | Critical | Hybrid NLP + LLM approach; confidence scoring; human review layer mandatory before sync |
| R-02 | LLM API cost spikes make unit economics unviable | Financial | Medium | High | High | Fine-tuned local models for common cases; LLM used only for disambiguation; token limits per tier |
| R-03 | Integration breaking changes from Jira/Notion/Slack API updates | Technical | Medium | High | High | API version pinning; integration monitoring with automated alerts; SLA-backed response time for fixes |
| R-04 | User privacy concerns about uploading AI conversation transcripts | Legal/Trust | High | High | Critical | Privacy-by-design architecture; enterprise data residency; clear DPA; on-premise option roadmap (V3) |
| R-05 | Slow adoption due to behavior change friction | Market | Medium | High | High | PLG motion; extension makes Chatly zero-friction overlay; generous free tier |
| R-06 | Competitor (Jira, Notion, Linear) ships native AI-to-task feature | Competitive | Medium | High | High | Accelerate integration breadth and NLP quality; brand "conversation operationalization" as distinct category |
| R-07 | OpenAI / Anthropic restrict API access for third-party processing of their conversations | Legal | Low | Critical | High | Multi-LLM strategy; legal review of API ToS; pivot to user-export-based ingestion if needed |
| R-08 | Browser extension rejected from Chrome Web Store | Technical | Low | High | Medium | Pre-submission compliance review; fallback: manual upload flow remains primary; Firefox extension as backup |
| R-09 | Data breach exposing conversation transcripts | Security | Low | Critical | High | Encryption at rest and in transit; zero-log policy for raw transcripts; SOC 2 audit; bug bounty program |
| R-10 | Key engineering talent attrition (especially NLP expertise) | Operational | Medium | High | High | Competitive compensation; NLP knowledge documentation; cross-training; consider NLP as managed service API |

### 13.2 Scenario Planning

#### Scenario A: NLP Quality Falls Short
- **Trigger:** Beta feedback shows users spending > 5 minutes correcting extractions per session (F1 < 75%)
- **Response:** Shift NLP pipeline to higher LLM reliance; invest in labeled training data collection; implement "suggest mode" where Chatly provides suggestions but does not auto-create (reduces correction burden)

#### Scenario B: API ToS Conflict
- **Trigger:** OpenAI or Anthropic issues guidance that third-party processing of exported conversations violates ToS
- **Response:** Shift to user-owned export model (users export their own data; Chatly processes it); engage legal to clarify ToS interpretation; publish public policy statement

#### Scenario C: Competitor Ships Similar Feature
- **Trigger:** Jira, Notion, or Linear announces native AI conversation → task extraction
- **Response:** Accelerate cross-platform (multi-tool) value proposition, which native tools cannot replicate; deepen NLP accuracy and customization; accelerate enterprise segment with SOC 2 + custom NLP fine-tuning as differentiators

---

## 14. Competitive Landscape

### 14.1 Competitive Matrix

| Capability | Chatly | Otter.ai | Fireflies.ai | Zapier | Notion AI | Linear AI |
|---|---|---|---|---|---|---|
| AI conversation extraction | Native, purpose-built | Human meeting focus | Human meeting focus | None | Limited (within Notion) | Limited (within Linear) |
| Multi-tool integration | 10+ tools | Jira, Notion, Slack | CRM + Slack | Unlimited (manual config) | Notion only | Linear only |
| Decision logging | Structured, searchable | Basic transcript | Basic transcript | None | None | None |
| Real-time extension | Yes (planned P1) | Meeting bot (different paradigm) | Meeting bot | No | No | No |
| Confidence scoring | Yes | No | No | No | No | No |
| NLP pipeline | Custom, multi-stage | Transcription-only | Transcription-only | Rule-based triggers | Prompt-based (GPT) | Prompt-based |
| Owner resolution | Workspace-aware | No | No | No | No | No |
| Pipeline visualization | Yes | No | No | No | No | No |
| Pricing (team) | $49/user/month | $20/user/month | $19/user/month | $69/month flat | $10/user/month | $8/user/month |

### 14.2 Competitive Positioning

**Otter.ai and Fireflies.ai** are the closest analogy products, but they are fundamentally oriented around human-to-human meeting transcription. They do not address the growing category of AI-to-human conversations. Their NLP is built for speaker-labeled meeting notes, not AI conversation extraction.

**Notion AI and Linear AI** are embedded AI features within single-tool ecosystems. They do not extract across tools, do not support multi-integration sync, and are limited to their own platform's data model.

**Zapier and Make** can automate workflows but require manual configuration of every rule. They cannot semantically understand conversation content and do not provide extraction, review, or pipeline generation.

**ChatGPT / Claude / Gemini** themselves do not structure their outputs. They are Chatly's largest source of conversation transcripts, not competitors.

### 14.3 Defensibility

Chatly's moat is built on three dimensions:

1. **Data Network Effect:** Every correction a user makes on extracted items feeds a proprietary training dataset. Over time, Chatly's extraction quality becomes self-reinforcing and increasingly difficult to replicate.
2. **Integration Network:** Each integration added increases the switching cost for workspaces using multiple tools. A team using Chatly with Jira + Notion + Slack + Linear has four simultaneous switching costs.
3. **Category Ownership:** By naming and evangelizing "AI Conversation Operationalization," Chatly aims to be the brand synonymous with the category, similar to how Zoom became synonymous with video calls.

---

## 15. Product Roadmap (MVP to V2)

> **Wireframe:** [Product Roadmap Gantt (FigJam) →](https://www.figma.com/online-whiteboard/create-diagram/4348bb18-b40a-4cb0-809e-59092b814359?utm_source=claude&utm_content=edit_in_figjam)

### 15.1 MVP (Weeks 1-16) — Core Value Validation

**Theme:** Prove that structured extraction from AI conversations creates enough value to retain users and drive initial payments.

| Feature | Priority | Owner Team | Est. Weeks |
|---|---|---|---|
| Ingestion Engine (paste + file upload) | P0 | Backend | Weeks 1-4 |
| NLP Extraction Pipeline (v1) | P0 | NLP | Weeks 2-8 |
| Extraction Review UI | P0 | Frontend | Weeks 4-8 |
| Execution Pipeline Builder | P0 | Frontend + Backend | Weeks 7-10 |
| Jira Integration | P0 | Backend | Weeks 6-10 |
| Notion Integration | P0 | Backend | Weeks 8-12 |
| Slack Integration | P0 | Backend | Weeks 9-11 |
| Conversation & Pipeline Dashboard | P0 | Frontend | Weeks 9-12 |
| Workspace & Team Management | P0 | Backend | Weeks 3-6 |
| Auth (Google OAuth + email) | P0 | Backend | Weeks 1-2 |
| Beta Onboarding Flow | P0 | Frontend | Weeks 12-14 |
| Internal QA + Beta Testing | P0 | QA | Weeks 14-16 |

**MVP Exit Criteria:**
- 200 beta users onboarded
- Extraction F1 ≥ 82%
- Jira, Notion, Slack integrations functional with < 2% sync failure rate
- Week-4 retention ≥ 55%
- NPS ≥ 40

---

### 15.2 V1 (Months 5-8) — Commercial Launch

**Theme:** Expand integration breadth, sharpen extraction quality, and build the monetization engine.

| Feature | Priority | Owner Team | Est. Weeks |
|---|---|---|---|
| Real-Time Browser Extension (Chrome) | P1 | Frontend (Ext.) | Months 5-6 |
| Owner Assignment & Mention Resolution | P1 | NLP + Backend | Month 5 |
| Deadline Normalization + Calendar Sync | P1 | NLP + Backend | Month 5 |
| Decision Log & Knowledge Base | P1 | Frontend + Backend | Month 6 |
| Multi-Session Synthesis | P1 | Backend + NLP | Month 6 |
| Linear Integration | P1 | Backend | Month 5 |
| Trello Integration | P1 | Backend | Month 5 |
| Asana Integration | P1 | Backend | Month 6 |
| GitHub Issues Integration | P1 | Backend | Month 6 |
| Google Calendar Sync | P1 | Backend | Month 6 |
| SSO (Google OAuth enterprise) | P1 | Backend | Month 7 |
| Billing & Subscription (Stripe) | P0 | Backend | Month 5 |
| NLP Model v2 (improved classifiers) | P0 | NLP | Month 6 |
| Analytics Dashboard (internal) | P1 | Frontend | Month 7 |
| SOC 2 Type I Audit Initiation | P1 | Infra + Legal | Month 7 |

**V1 Exit Criteria:**
- 50 paying teams, $75K MRR
- Extraction F1 ≥ 88%
- 6 integrations live
- Month-1 retention ≥ 50%

---

### 15.3 V2 (Months 9-18) — Platform Maturity & Enterprise

**Theme:** Enterprise-grade reliability, developer ecosystem, and analytics to establish Chatly as the market-defining platform.

| Feature | Priority | Est. Quarter |
|---|---|---|
| AI Conversation Templates Library | P2 | Q3 2026 |
| Analytics & Reporting Dashboard | P2 | Q3 2026 |
| Public REST API + Webhook System | P2 | Q3 2026 |
| Zapier + Make Integration | P2 | Q3 2026 |
| Confluence Integration | P2 | Q3 2026 |
| Monday.com Integration | P2 | Q3 2026 |
| ClickUp Integration | P2 | Q4 2026 |
| SAML SSO (Okta, Azure AD) | P2 | Q4 2026 |
| Custom NLP Fine-Tuning (Enterprise) | P2 | Q4 2026 |
| Outlook Calendar Sync | P2 | Q4 2026 |
| Mobile App (iOS + Android) | P2 | Q1 2027 |
| On-Premise Deployment (Beta) | P2 | Q1 2027 |
| SOC 2 Type II Certification | P2 | Q1 2027 |
| Community Template Contributions | P2 | Q2 2027 |
| AI Assistant (ask Chatly questions about past sessions) | P2 | Q2 2027 |

---

### 15.4 Visual Roadmap Summary

```
TIMELINE:  Month 1-4          Month 5-8          Month 9-18
           |--MVP (Beta)--|   |--V1 (GA)------|   |--V2 (Enterprise)----------|

FOCUS:     Core Extraction    Integration Scale   Platform + Enterprise
           Jira/Notion/Slack  Linear/Asana/GH     API/SAML/Custom NLP
           Dashboard          Decision Log        Analytics/Mobile
           Team Mgmt          Real-Time Ext.      On-Premise Option

REVENUE:   $0 (beta)         $75K MRR (Month 8)  $125K+ MRR (Month 12)

USERS:     200 beta users    50 teams / 1K users  200 teams / 5K+ users
```

---

## Appendix A: Assumptions

1. AI platform providers (OpenAI, Anthropic, Google) do not materially restrict third-party processing of user-exported conversation transcripts within the timeline of this roadmap.
2. The target market continues to adopt AI assistants at current or higher rates through 2026-2027.
3. OpenAI GPT-4o mini API pricing remains within 2x of February 2026 pricing.
4. Core engineering team (6-8 engineers) can be fully assembled within 8 weeks of funding.
5. Integration APIs (Jira, Notion, Slack) maintain backward compatibility during the V1 timeline.

## Appendix B: Open Questions

| Question | Owner | Target Resolution |
|---|---|---|
| What is the acceptable minimum F1 score for user trust without a mandatory review step? | PM + UX Research | Week 8 (beta feedback) |
| Should Chatly store raw transcripts, or only extracted structured data? | Legal + Engineering | Week 2 |
| What is the optimal balance between NLP model inference (self-hosted) vs. LLM API calls for cost and accuracy? | NLP Lead | Week 6 |
| Does the browser extension require Manifest V3 compatibility on Day 1, or can MV2 be used initially? | Extension Lead | Week 4 |
| Should Chatly build its own fine-tuned model or use a third-party provider for NLP classification? | NLP Lead + CTO | Week 3 |

## Appendix C: Glossary

| Term | Definition |
|---|---|
| Action Item | A concrete, executable task identified from an AI conversation |
| Execution Pipeline | A structured, ordered set of tasks with owners, deadlines, and dependencies derived from a conversation |
| Extraction | The process of identifying and structuring entities from raw conversation text |
| F1 Score | Harmonic mean of precision and recall; used to measure NLP extraction quality |
| Integration Adapter | A service module that handles communication with a specific third-party tool (e.g., Jira adapter) |
| NLP | Natural Language Processing |
| Pipeline Sync | The action of pushing a structured execution pipeline to one or more workflow tools |
| Session | A single AI conversation submitted to Chatly for processing |
| SRL | Semantic Role Labeling — NLP technique for identifying "who did what to whom when" |
| Workspace | An organizational unit in Chatly containing users, sessions, integrations, and settings |

---

*Document Version: 1.0*
*Last Updated: February 19, 2026*
*Next Review Date: March 19, 2026*
*Prepared by: Kartik Bhalerao*
*Confidential — For Internal Distribution Only*

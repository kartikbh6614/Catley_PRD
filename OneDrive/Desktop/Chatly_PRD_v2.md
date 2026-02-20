# Product Requirements Document: Chatly

> **LEGAL DISCLAIMER:** All legal content in this document is for informational and planning purposes only. It does not constitute legal advice or create an attorney-client relationship. All legal frameworks, contract templates, compliance strategies, and regulatory interpretations must be reviewed and validated by qualified legal counsel before implementation or reliance.

---

## Document Control

| Field | Value |
|---|---|
| **Product Name** | Chatly |
| **Version** | 2.0 |
| **Status** | Draft — Internal Review |
| **Date Created** | February 19, 2026 |
| **Last Updated** | February 20, 2026 |
| **Author** | Kartik Bhalerao |
| **Document Type** | Product Requirements Document (PRD) |
| **Next Review Date** | March 20, 2026 |
| **Classification** | Confidential — Internal Distribution Only |

### Version History

| Version | Date | Author | Changes |
|---|---|---|---|
| 1.0 | Feb 19, 2026 | Kartik Bhalerao | Initial draft |
| 2.0 | Feb 20, 2026 | Kartik Bhalerao | Full restructure; Legal & Compliance Framework added (Section 13); Financial Projections added (Section 18); Data Architecture section added (Section 8); Risk register expanded; Roadmap updated with legal milestones |

### Document Reviewers & Approvals

| Role | Name | Status | Date |
|---|---|---|---|
| Product Lead | Kartik Bhalerao | Author | Feb 20, 2026 |
| Legal Counsel | TBD | Pending | — |
| CTO | TBD | Pending | — |
| Head of Design | TBD | Pending | — |
| Head of Engineering | TBD | Pending | — |

---

## Table of Contents

1. [Executive Summary](#1-executive-summary)
2. [Problem Statement & Market Opportunity](#2-problem-statement--market-opportunity)
3. [Target Users & Personas](#3-target-users--personas-jobs-to-be-done)
4. [Product Goals & OKRs](#4-product-goals--okrs)
5. [Feature Requirements](#5-feature-requirements-core--advanced)
6. [User Stories & Acceptance Criteria](#6-user-stories--acceptance-criteria)
7. [Technical Architecture](#7-technical-architecture-overview)
8. [Data Architecture & Privacy Design](#8-data-architecture--privacy-design)
9. [Integrations & Third-Party Tools](#9-integrations--third-party-tools)
10. [UX/UI Requirements & User Flows](#10-uxui-requirements--user-flows)
11. [Non-Functional Requirements](#11-non-functional-requirements)
12. [Success Metrics & Analytics Framework](#12-success-metrics--analytics-framework)
13. [Legal & Compliance Framework](#13-legal--compliance-framework)
14. [Go-to-Market Strategy](#14-go-to-market-strategy)
15. [Risk Analysis & Mitigation](#15-risk-analysis--mitigation)
16. [Competitive Landscape](#16-competitive-landscape)
17. [Product Roadmap (MVP to V2)](#17-product-roadmap-mvp-to-v2)
18. [Financial Projections](#18-financial-projections)
19. [Appendices](#appendices)

---

## 1. Executive Summary

### 1.1 Product Identity

| Field | Details |
|---|---|
| **Product Name** | Chatly |
| **Category** | AI Conversation Operationalization (new category) |
| **One-Line Description** | Chatly automatically transforms AI conversations into structured execution pipelines, bridging the gap between AI-generated insights and real-world task execution. |
| **Stage** | Pre-seed / Early-stage SaaS |
| **Target Launch** | Q2 2026 (MVP Beta) |

### 1.2 Problem vs. Solution

| Problem | Chatly's Solution |
|---|---|
| Action items from AI conversations never reach task managers | NLP pipeline extracts and auto-creates tasks in Jira, Linear, Asana |
| Decisions made with AI are not formally recorded | Persistent, searchable Decision Log across all sessions |
| No ownership assigned from AI outputs | Owner resolution maps names to real workspace members |
| Manual re-entry of AI outputs wastes 20–30 min/session | One-click sync reduces this to < 2 minutes |
| No audit trail of AI-assisted planning | Full session history with extraction provenance |

### 1.3 Business Impact

- Reduces post-AI-session setup time by an estimated **70–80%**
- Eliminates task loss from unstructured AI conversations
- Creates a **closed-loop system** from ideation (AI conversation) → execution (workflow tool)
- Positions as the connective tissue between the AI productivity layer and the execution layer

### 1.4 Resource Requirements

| Resource | Requirement |
|---|---|
| Engineering Team | 6–8 engineers (2 NLP/ML, 3 full-stack, 1 DevOps, 1 QA) |
| Design | 1 senior product designer + 1 UX researcher |
| Product | 1 PM (lead) + 1 APM |
| Legal | Qualified legal counsel (data privacy, IP, SaaS contracts) |
| Timeline to MVP | 16 weeks |
| Initial Infrastructure Budget | $40,000–$60,000/year (cloud + LLM API costs) |
| Target ARR (Year 1) | $1.5M–$3M |

### 1.5 Risk Summary

Primary risks include LLM API cost volatility, NLP extraction accuracy, integration maintenance overhead, user privacy concerns, and AI platform ToS compliance. All risks addressed in Sections 13 (Legal) and 15 (Risk Analysis).

---

## 2. Problem Statement & Market Opportunity

### 2.1 The Core Problem

AI assistants have become the primary thinking partner for knowledge workers. Over 65% of enterprise knowledge workers use AI assistants daily for planning, brainstorming, and decision-making (industry surveys, 2025). Yet a fundamental structural gap persists:

```
AI Conversation (Thinking) ──[GAP]──► Execution (Doing)
```

**Four measurable failure modes:**

| Failure Mode | Description | Estimated Impact |
|---|---|---|
| Task Loss | AI-generated action items never reach task systems | 40–60% of items never executed |
| Decision Debt | AI-assisted decisions not formally recorded | Repeated deliberation; organizational confusion |
| Ownership Vacuum | No one assigned → no one acts | 0% accountability default |
| Integration Friction | Manual re-entry is slow and error-prone | 20–30 min/session wasted |

### 2.2 Market Opportunity

#### Market Sizing

| Market | Size | Growth |
|---|---|---|
| Project Management Software | $6.8B (2024) → $15.06B (2030) | 13.7% CAGR |
| AI Productivity Tools | $12B+ | 25%+ CAGR |
| **TAM (Combined)** | **$18B+** | — |
| **SAM** (AI-adopting knowledge workers, 10–5,000 employee companies) | **$3.2B** | ~18% of TAM |
| **SOM** (3-year realistic capture) | **$48M** | ~1.5% of SAM |

#### Market Timing — Three Converging Macro Trends (2026)

1. **AI Assistant Ubiquity:** ChatGPT, Claude, Gemini, Copilot have achieved mass daily adoption
2. **Tool Fatigue + Integration Demand:** Users want unified, automated workflows — not more tools
3. **LLM Cost Reduction:** GPT-4-class inference costs dropped 80%+ since 2023 — real-time analysis is now economically viable

### 2.3 The Opportunity Gap

No product directly addresses the AI-to-execution pipeline problem:

| Category | Product | Gap |
|---|---|---|
| AI Assistants | ChatGPT, Claude, Gemini | Generate outputs — do not structure or route them |
| Task Managers | Jira, Asana, Linear | Accept tasks — do not generate from conversations |
| Meeting Tools | Otter.ai, Fireflies | Extract from human meetings — not AI conversations |
| Automation | Zapier, Make | Handle integrations — require manual rule configuration |

**Chatly occupies a greenfield category: AI Conversation Operationalization.**

---

## 3. Target Users & Personas (Jobs-to-Be-Done)

### 3.1 Primary Persona: Strategic Product Manager

| Field | Details |
|---|---|
| **Name** | Priya, 31 |
| **Role** | Senior PM, Series B SaaS (150 employees) |
| **Tech Stack** | ChatGPT, Jira, Notion, Slack |
| **AI Usage** | 5+ sessions/day |
| **Willingness to Pay** | $30–50/user/month |

**Jobs-to-Be-Done:**
- When I finish an AI planning session → I need action items in Jira immediately so nothing gets lost
- When I make a product decision with AI → I need that decision formally logged and referenceable
- When I delegate tasks from AI conversations → I need ownership and deadlines attached

**Pain Points:**
- Spends 20–30 min after every AI session manually creating Jira tickets
- Action items frequently fall through the cracks
- Cannot audit which decisions were AI-assisted vs. not

---

### 3.2 Secondary Persona: Engineering Team Lead

| Field | Details |
|---|---|
| **Name** | Rohan, 34 |
| **Role** | Engineering Lead, fintech startup (80 engineers) |
| **Tech Stack** | Claude, Linear, GitHub, Slack |
| **AI Usage** | 3–5 sessions/day |
| **Willingness to Pay** | $25–40/user/month |

**Jobs-to-Be-Done:**
- AI architecture planning → tasks and dependencies in Linear immediately so team sprints immediately
- Blockers surfaced in AI sessions → logged and escalated automatically so they are not forgotten
- AI-assisted retrospectives → action items auto-assigned to team members so we actually improve

**Pain Points:**
- Rich planning context from AI is re-entered manually into Linear
- Blockers from AI sessions not systematically tracked
- Sprint setup takes 1+ extra hour after AI-assisted planning

---

### 3.3 Tertiary Persona: Strategy Consultant

| Field | Details |
|---|---|
| **Name** | Anjali, 28 |
| **Role** | Associate, management consulting firm |
| **Tech Stack** | ChatGPT + Gemini, Notion, Trello |
| **AI Usage** | 2–4 sessions/day |
| **Willingness to Pay** | $20–35/user/month |

**Jobs-to-Be-Done:**
- AI research sessions → automatically documented with clean audit trail for clients
- Multi-project AI conversations → organized by project without context bleed
- AI-generated insights → professional formats importable into client-facing tools

**Pain Points:**
- Manual documentation of AI sessions is time-consuming and error-prone
- No organized system for cross-project AI conversation management
- Clients increasingly ask for documentation of AI-assisted analysis

---

### 3.4 Persona Summary Matrix

| Attribute | Priya (PM) | Rohan (Eng Lead) | Anjali (Consultant) |
|---|---|---|---|
| AI Usage Frequency | 5+/day | 3–5/day | 2–4/day |
| Primary AI Tool | ChatGPT | Claude | ChatGPT + Gemini |
| Primary Task Tool | Jira | Linear | Notion/Trello |
| Team Size | 15–30 | 20–80 | 5–15 |
| Budget Sensitivity | Medium | Low | High |
| Integration Priority | Jira, Notion, Slack | Linear, GitHub, Slack | Notion, Trello |
| MVP Feature Priority | Action extraction, Jira sync | Decision logging, Linear sync | Multi-project org, export |

---

## 4. Product Goals & OKRs

### 4.1 Product Vision

> **Chatly makes every AI conversation executable** — transforming the raw output of AI-assisted thinking into structured, assigned, tracked work.

### 4.2 Strategic Pillars

| Pillar | Description |
|---|---|
| Extraction Accuracy | Be the most accurate AI conversation parser in the market |
| Integration Breadth | Support every major workflow tool without friction |
| Zero-Interruption UX | Work invisibly; surface value without adding workflow steps |
| Trust and Control | Full visibility into what was extracted and why, with easy correction |
| Legal & Privacy First | Privacy-by-design; compliant by architecture, not by patch |

### 4.3 OKRs by Quarter

#### Q1 2026 — MVP Launch (Weeks 1–16)

**Objective 1: Ship a high-quality MVP that validates core value proposition**

| Key Result | Measurement | Target |
|---|---|---|
| KR1.1 | Beta users onboarded | 200 |
| KR1.2 | Extraction accuracy (F1 score) | ≥ 82% |
| KR1.3 | Integrations live at launch | 3 (Jira, Notion, Slack) |
| KR1.4 | Avg. session setup time post-onboarding | < 5 minutes |

**Objective 2: Demonstrate user retention and engagement**

| Key Result | Measurement | Target |
|---|---|---|
| KR2.1 | Week-4 retention rate (beta) | ≥ 55% |
| KR2.2 | Avg. sessions processed/user/week | ≥ 4 |
| KR2.3 | NPS score at end of beta | ≥ 40 |

---

#### Q2 2026 — V1 Launch (General Availability)

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

#### Q3–Q4 2026 — V2 (Platform Maturity)

**Objective 5: Establish Chatly as category leader**

| Key Result | Measurement | Target |
|---|---|---|
| KR5.1 | ARR | $1.5M |
| KR5.2 | Paying teams | 200+ |
| KR5.3 | Integration coverage | 10+ tools |
| KR5.4 | Enterprise deals (50+ seat) | 5 |
| KR5.5 | SOC 2 Type II certification | Achieved |
| KR5.6 | Analyst recognition / press mentions | 10+ |

---

## 5. Feature Requirements (Core + Advanced)

### Priority Definitions

| Priority | Label | Meaning |
|---|---|---|
| P0 | Must Have (MVP) | Blocks shipping; fundamental to core value proposition |
| P1 | Should Have (V1) | Significantly enhances value; ships within 90 days of MVP |
| P2 | Nice to Have (V2+) | Adds differentiation; V2 roadmap |

---

### 5.1 Core Feature Set

#### F-01: AI Conversation Ingestion Engine (P0)

**Description:** Accept AI conversation transcripts via multiple input methods and normalize them into a common format for downstream NLP processing.

**Input Methods:**
- Manual paste (text input in Chatly UI)
- File upload (.txt, .json, .md, .docx, .pdf)
- Browser extension (live capture from ChatGPT, Claude, Gemini, Copilot web UIs)
- REST API endpoint (programmatic ingestion from custom AI tools)
- Webhook listener (for AI platforms with webhook callbacks)

**Normalization Requirements:**
- Strip UI chrome, timestamps, and formatting artifacts
- Identify and label speaker turns (User / AI)
- Segment conversation into logical topic blocks
- Handle multi-turn conversations up to 50,000 tokens

**Acceptance Criteria:**
- All input methods accepted without error
- Normalization preserves full semantic content
- Transcripts up to 50,000 tokens processed without timeout
- Processing initiation confirmed to user within 2 seconds of submission

---

#### F-02: NLP Extraction Pipeline (P0)

**Description:** Multi-stage NLP pipeline that analyzes normalized conversation content and extracts structured entities.

**Extracted Entity Types:**

| Entity | Description | Example |
|---|---|---|
| Action Item | A concrete task to be performed | "Build the authentication module" |
| Decision | A conclusion or choice reached | "We will use PostgreSQL over MongoDB" |
| Owner | A person or role responsible | "Rohan", "the design team" |
| Deadline | A time constraint or date | "by end of Q2", "next Friday" |
| Blocker | An impediment to progress | "Waiting on API credentials from vendor" |
| Context Tag | Topic or project label | "#backend", "#product-launch" |
| Priority Signal | Urgency indicators | "urgent", "critical", "must have" |

**Pipeline Stages:**
1. Preprocessing: Tokenization, POS tagging, NER (SpaCy)
2. Semantic Role Labeling: Agent / Action / Object / Temporal extraction
3. Classification: Action item / decision / blocker classifiers (fine-tuned RoBERTa, multi-label)
4. Coreference Resolution: Link pronouns to named entities
5. LLM Disambiguation: Low-confidence items (< 0.65) sent to GPT-4o mini
6. Confidence Scoring: Each item scored 0.0–1.0
7. Structured Output: JSON schema output per entity

**Acceptance Criteria:**
- F1 score ≥ 82% at MVP; ≥ 88% at V1
- Confidence scores calibrated within 10% of actual accuracy
- 10,000 tokens processed in < 8 seconds
- All outputs conform to defined JSON schema

---

#### F-03: Extraction Review & Correction UI (P0)

**Description:** Interface for reviewing extracted items before sync. Users can confirm, edit, reject, or add items.

**UI Components:**
- Extraction summary panel (counts by type)
- Item cards with source quote highlighted in conversation panel
- Inline editing (text, owner, deadline, priority)
- Confidence indicator (green ≥ 80%, yellow 50–79%, red < 50%)
- Bulk actions: approve all / reject all / approve high-confidence only
- Add manual item button
- Source conversation panel with extraction span highlighting

**Acceptance Criteria:**
- All items displayed within 3 seconds of extraction completion
- Source highlighting accurately maps to correct conversation segment
- Edits persisted immediately (no save button required)
- Bulk approve processes all items in < 2 seconds

---

#### F-04: Execution Pipeline Builder (P0)

**Description:** Generates a structured execution pipeline — ordered, linked tasks with dependencies, owners, and deadlines — ready for export.

**Features:**
- Auto-dependency detection (items referencing shared entities linked)
- Priority ordering (priority signals + deadline proximity)
- Pipeline visualization (Kanban board + list view)
- Group by: Owner / Priority / Topic / Deadline
- Export as: Jira Epic+Stories, Notion page, Linear project, plain Markdown

**Acceptance Criteria:**
- Pipeline generated from approved extractions in < 5 seconds
- Dependency links accurately reflect conversational sequencing
- All view modes render correctly across desktop breakpoints
- Export to ≥ 3 integration targets functional at MVP

---

#### F-05: Workflow Integration Sync (P0)

**Description:** One-click or automated synchronization of execution pipeline into connected workflow tools.

**MVP Integrations (P0):** Jira, Notion, Slack

**Sync Behavior:**
- OAuth 2.0 authentication per integration
- Field mapping UI (Chatly fields → integration fields, configurable per workspace)
- Conflict detection: check for duplicates before creating
- Sync status tracking: pending / synced / failed / manually resolved
- Retry logic: 3x with exponential backoff
- Webhook listener for sync confirmation from target tool

**Acceptance Criteria:**
- OAuth flow completes in < 3 steps per integration
- All Chatly fields mappable to target tool fields
- Sync failure rate < 2% under normal conditions
- Users notified of failures within 30 seconds

---

#### F-06: Conversation & Pipeline Dashboard (P0)

**Description:** Centralized dashboard for all past conversations, extraction status, pipeline status, and sync status.

**Views:**
- All Sessions (search + filter by date/tool/status/owner)
- Session Detail (conversation + extractions + pipeline + sync log)
- My Tasks (cross-session, assigned to logged-in user)
- Team Overview (admin: all sessions across workspace)

**Acceptance Criteria:**
- Loads within 2 seconds for workspaces with ≤ 500 sessions
- Search returns results within 1 second
- Session detail reflects real-time sync status

---

#### F-07: Workspace & Team Management (P0)

**Description:** Multi-user workspace management with role-based access control (RBAC).

**Roles:**

| Role | Permissions |
|---|---|
| Admin | Full access, billing, integrations, team management |
| Member | Process conversations, view own sessions, sync to tools |
| Viewer | Read-only access to sessions and pipelines (no sync) |

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

Browser extension captures active AI conversations in near-real-time. Side panel overlay appears within 3 seconds of AI response completion. Approved items queue for sync without interrupting the conversation. Available Chrome + Edge at P1.

---

#### F-09: Decision Log & Knowledge Base (P1)

Persistent, searchable log of all decisions extracted across all sessions. Full-text + semantic similarity search. Decision cards with: text, context, source conversation, date, participants. Export to Notion, Confluence, PDF.

---

#### F-10: Owner Assignment & Mention Resolution (P1)

Intelligent resolution of mentioned names/roles to workspace members. Fuzzy matching ("Rohan" → "Rohan Mehta"). Role-based assignment ("the design team" → team group). Ambiguous mentions flagged for human review — never silently misassigned.

---

#### F-11: Deadline Normalization & Calendar Sync (P1)

NLP resolution of natural language deadlines to absolute dates. Timezone-aware storage. Google Calendar + Outlook sync. Deadline conflict detection and drift alerts when deadline passes without completion.

---

#### F-12: Multi-Session Synthesis (P1)

Process multiple sessions together into a unified pipeline. Cross-session deduplication. Conflict detection (contradictory decisions flagged). Unified pipeline view across selected sessions. Up to 10 sessions in < 20 seconds.

---

#### F-13: AI Conversation Templates (P2)

Pre-built templates for Sprint Planning, PRD Brainstorm, Architecture Review, Retrospective, Competitive Analysis, Customer Interview Synthesis, OKR Planning. Template-specific extraction schemas improve F1 by 5%+ vs. generic. 7 templates at V2 launch.

---

#### F-14: Analytics & Reporting (P2)

Workspace productivity analytics: sessions processed, action item completion rates, top owners, integration usage, decision log growth, blocker frequency. Weekly digest email by 8:00 AM Monday in user's timezone.

---

#### F-15: Public API & Webhooks (P2)

REST API (OpenAPI 3.0) + webhook system for enterprise programmatic integration. Scoped API key auth (read / write / admin). Webhook events: `session.processed`, `extraction.completed`, `pipeline.created`, `sync.succeeded`, `sync.failed`, `item.updated`. 99.9% API uptime SLA for enterprise.

---

## 6. User Stories & Acceptance Criteria

### 6.1 Ingestion & Processing

**US-001: Paste Conversation for Processing**
*As a PM, I want to paste an AI conversation into Chatly so that I can extract structured action items without manually reviewing the entire chat.*

- Given I click "New Session" and paste text → Chatly begins processing within 2 seconds
- Given processing completes → I see extracted action items, decisions, blockers, and owners
- Given no action items found → "No action items detected. You can add items manually."

---

**US-002: Upload Conversation File**
*As a consultant, I want to upload an exported conversation file so that I can process conversations exported from AI tools.*

- Given valid file ≤ 10MB → uploads and processing begins within 3 seconds
- Given unsupported format → "Unsupported file format. Please upload .txt, .json, .md, or .docx files."
- Given file > 10MB → "File exceeds 10MB limit. Please split and upload in parts."

---

**US-003: Browser Extension Live Capture**
*As an engineering lead, I want the Chatly extension to capture my Claude conversation in real time.*

- Given extension installed + logged in, When I open Claude.ai → side panel activates automatically
- Given AI delivers a response → side panel updates with new extracted items within 1 second
- Given I toggle extension off → no data captured or sent to Chatly

---

### 6.2 Extraction & Review

**US-004: Review Extracted Action Items**
*As a PM, I want to review all extracted items before Jira sync to ensure accuracy.*

- Given session processed → all items displayed with source quote highlighted in conversation panel
- Given item confidence < 50% → flagged red with tooltip "Low confidence — please review"
- Given I click Edit → item updates without separate save action

---

**US-005: Reject Irrelevant Extractions**
*As an engineering lead, I want to reject items that are not genuine action items.*

- Given I click Reject → item moves to Rejected section (accessible via toggle)
- Given I click Restore in Rejected section → item moves back to active list
- Given > 3 rejections → rejection context recorded for model improvement

---

**US-006: Manually Add Action Items**
*As a consultant, I want to manually add items the AI did not extract.*

- Given I click "Add Item" → blank item card in edit mode
- Given I fill in text and click away → item saved, marked "Manually Added"
- Given I sync → manually added items sync alongside extracted items with no distinction in target tool

---

### 6.3 Pipeline & Integration

**US-007: Sync Execution Pipeline to Jira**
*As a PM, I want to sync approved items to Jira with one click.*

- Given Jira connected + approved extractions → Chatly creates Jira issues within 10 seconds
- Given owner resolved to Jira user → issue assigned to that user
- Given deadline extracted and normalized → Jira due date set to normalized date
- Given sync fails for any items → "X items failed to sync. View details" with per-item error reasons

---

**US-008: Post Pipeline Summary to Slack**
*As a team lead, I want Chatly to post a formatted pipeline summary to Slack.*

- Given Slack connected + channel configured → formatted message in configured channel within 5 seconds
- Message includes: session name, total items, top 3 action items with owners/deadlines, link to pipeline
- Given Slack not connected → prompted to connect via OAuth

---

**US-009: Create Notion Page from Pipeline**
*As a consultant, I want to create a Notion page from my execution pipeline.*

- Given Notion connected + target database selected → Notion page created with action items as rows within 15 seconds
- Each row: Task, Owner, Deadline, Priority, Status (default: Not Started)
- Given previous export exists → "Update existing page or create new?" before proceeding

---

### 6.4 Dashboard & Management

**US-010: View All Past Sessions**
- Dashboard shows all sessions sorted by most recent: Name, Date, Items Extracted, Sync Status, Integrations Used
- Search returns matching results within 1 second
- Filter (e.g., "Synced to Jira") shows only matching sessions

---

**US-011: View Team Sessions (Admin)**
- Admin sees all sessions across workspace with member names visible
- Admin can view but not edit unless session owner or Admin
- Non-admin accessing Team Overview → 403 or redirect to My Sessions

---

## 7. Technical Architecture Overview

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

```
Input Transcript
       │
       ▼
[Stage 1: Preprocessing]
  Sentence tokenization (SpaCy) · POS tagging · NER · Speaker turn labeling
       │
       ▼
[Stage 2: Semantic Role Labeling]
  Agent / Action / Object / Temporal extraction (AllenNLP SRL / fine-tuned BERT-SRL)
       │
       ▼
[Stage 3: Classification]
  Action Item / Decision / Blocker classifiers (fine-tuned RoBERTa, multi-label capable)
       │
       ▼
[Stage 4: Coreference Resolution]
  Pronoun + reference → named entity resolution (SpaCy neuralcoref / FastCoref)
       │
       ▼
[Stage 5: LLM Disambiguation]
  Low-confidence items (score < 0.65) → GPT-4o mini
  Confirms / corrects / discards · Natural language deadline normalization
       │
       ▼
[Stage 6: Structured Output]
  JSON schema validation · Confidence scoring · Source span mapping
       │
       ▼
Structured Extraction Result (JSON)
```

**LLM Cost Management:**
- Only items with confidence < 0.65 sent to LLM (~60% reduction in LLM calls)
- GPT-4o mini (~$0.15/1M input tokens) not GPT-4o
- Redis caching for identical sentence patterns (30-day TTL)
- Batch processing for post-session mode (lower cost tier)

### 7.3 Data Model (Core Entities)

```sql
-- Workspace
workspace (
  id UUID PRIMARY KEY,
  name VARCHAR(255),
  plan ENUM('free', 'pro', 'enterprise'),
  data_residency ENUM('us', 'eu'),         -- Legal: data residency selection
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
  gdpr_consent_at TIMESTAMP,               -- Legal: consent timestamp
  data_deletion_requested_at TIMESTAMP,    -- Legal: right to deletion
  created_at TIMESTAMP
)

-- Session (a processed AI conversation)
session (
  id UUID PRIMARY KEY,
  workspace_id UUID REFERENCES workspace(id),
  owner_id UUID REFERENCES user(id),
  name VARCHAR(500),
  raw_transcript TEXT,                     -- Encrypted at rest (AES-256)
  normalized_transcript JSONB,
  token_count INTEGER,
  status ENUM('pending','processing','extracted','reviewed','synced','error'),
  source ENUM('paste', 'upload', 'extension', 'api'),
  source_platform VARCHAR(100),
  retention_expires_at TIMESTAMP,          -- Legal: data retention policy
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
  status ENUM('pending_review','approved','rejected','manually_added'),
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

-- Pipeline Item
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
  tool ENUM('jira','notion','slack','linear','trello','asana','github'),
  oauth_token_encrypted TEXT,              -- AES-256 encrypted; never exposed
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

-- Audit Log (Legal: data access and modification trail)
audit_log (
  id UUID PRIMARY KEY,
  workspace_id UUID REFERENCES workspace(id),
  actor_user_id UUID REFERENCES user(id),
  action VARCHAR(100),
  resource_type VARCHAR(50),
  resource_id UUID,
  ip_address INET,
  user_agent TEXT,
  created_at TIMESTAMP
)

-- Data Deletion Request (Legal: GDPR/CCPA right to erasure)
data_deletion_request (
  id UUID PRIMARY KEY,
  user_id UUID REFERENCES user(id),
  workspace_id UUID REFERENCES workspace(id),
  requested_at TIMESTAMP,
  completed_at TIMESTAMP,
  status ENUM('pending', 'processing', 'completed', 'failed'),
  deletion_scope ENUM('user_data', 'workspace_data', 'all')
)
```

### 7.4 API Design (REST)

**Base URL:** `https://api.chatly.io/v1`
**Auth:** Bearer JWT in Authorization header. Scoped API keys for programmatic access.

```
POST   /sessions                        Create and submit session for processing
GET    /sessions                        List sessions (paginated, filterable)
GET    /sessions/{id}                   Get session detail
DELETE /sessions/{id}                   Delete session

GET    /sessions/{id}/extractions       Get all extracted items
PATCH  /extractions/{id}               Update extracted item (text, owner, deadline, status)
POST   /sessions/{id}/extractions      Manually add extracted item

POST   /sessions/{id}/pipeline         Generate pipeline from approved extractions
GET    /sessions/{id}/pipeline         Get pipeline
POST   /pipelines/{id}/sync            Trigger sync to integration
GET    /pipelines/{id}/sync-log        Get sync log

GET    /workspaces/{id}/integrations   List configured integrations
POST   /workspaces/{id}/integrations   Add integration (triggers OAuth)
DELETE /integrations/{id}              Remove integration

GET    /workspaces/{id}/members        List members
POST   /workspaces/{id}/members        Invite member
PATCH  /members/{id}                   Update member role
DELETE /members/{id}                   Remove member

-- Legal / Privacy endpoints
POST   /users/{id}/deletion-request    GDPR/CCPA data deletion request
GET    /users/{id}/data-export         Export all user data (portability right)
GET    /workspaces/{id}/audit-log      Get audit log (admin only)
```

**WebSocket:** `wss://api.chatly.io/v1/sessions/{id}/stream`
Real-time extraction progress during processing.

**Rate Limits:**

| Tier | Requests/Min | Sessions/Day | Token Limit/Session |
|---|---|---|---|
| Free | 30 | 5 | 10,000 |
| Pro | 120 | 50 | 50,000 |
| Enterprise | 600 | Unlimited | 200,000 |

### 7.5 Technology Stack

| Layer | Technology | Rationale |
|---|---|---|
| Frontend (Web) | React 18 + TypeScript | Component ecosystem; team familiarity |
| Frontend (Extension) | Chrome Extension Manifest V3 | Chrome Web Store requirement |
| Backend (API) | Node.js + Express | Fast iteration; WebSocket support |
| NLP Services | Python + FastAPI | Python ML ecosystem (SpaCy, HuggingFace) |
| Pipeline & Integration | Python + FastAPI | Consistent with NLP service language |
| Primary Database | PostgreSQL 16 (AWS RDS) | Relational integrity; JSONB flexibility |
| Cache | Redis (AWS ElastiCache) | Session caching; rate limiting; NLP result cache |
| Vector Database | Pinecone | Semantic search for Decision Log |
| Object Storage | AWS S3 | File uploads; export artifacts |
| Message Queue | AWS SQS | Async NLP job queue |
| Event Bus | AWS SNS | Cross-service event propagation |
| LLM API | OpenAI GPT-4o mini | Cost-efficient disambiguation |
| NLP Models | HuggingFace Transformers (self-hosted) | Fine-tuned RoBERTa classifiers |
| CI/CD | GitHub Actions | Team familiarity |
| Infrastructure | AWS ECS Fargate + RDS + ElastiCache | Managed services; autoscaling |
| Monitoring | Datadog | APM, logs, custom metrics |
| Error Tracking | Sentry | Real-time error alerting |
| Secrets Management | AWS Secrets Manager | OAuth tokens; API keys; no secrets in code |

---

## 8. Data Architecture & Privacy Design

### 8.1 Data Flow Overview

```
User Submits Conversation
         │
         ▼
[Ingestion Service]
  Receive raw transcript → Encrypt in transit (TLS 1.3) → Encrypt at rest (AES-256)
  Store in session table (workspace-isolated)
         │
         ▼
[NLP Pipeline]
  Process normalized transcript
  Raw transcript NEVER logged to application logs
  NLP worker receives anonymized session reference only
         │
         ▼
[Extraction Results]
  Stored as structured extracted_item records
  Linked to session (workspace-isolated at DB query level)
         │
         ▼
[Integration Sync]
  Push structured data to third-party tools via OAuth
  OAuth tokens AES-256 encrypted in integration_config
  Sync log records external IDs only (not transcript content)
         │
         ▼
[Retention & Deletion]
  Sessions auto-deleted per workspace retention policy
  User deletion requests processed within 30 days
  Audit log retained 7 years (compliance requirement)
```

### 8.2 Data Classification

| Data Type | Classification | Handling |
|---|---|---|
| Raw conversation transcripts | Highly Sensitive (PII potential) | AES-256 at rest; never logged; workspace-isolated |
| Extracted items | Sensitive | Encrypted at rest; workspace-isolated |
| OAuth tokens | Highly Sensitive | AES-256 encrypted; never exposed in logs or API responses |
| User email / name | PII | Standard GDPR PII treatment |
| Sync logs | Internal | Retained per compliance requirements |
| Audit logs | Compliance | Retained 7 years; tamper-evident |
| Analytics / metrics | Aggregated (anonymized) | No PII; safe for analytics pipelines |

### 8.3 Data Residency

| Region | Available | Notes |
|---|---|---|
| United States (us-east-1) | MVP | Default region |
| European Union (eu-west-1) | V1 | Required for GDPR compliance |
| Asia Pacific | V2 | Enterprise expansion |

Workspace-level region selection at signup. Data never leaves selected region without explicit user action.

### 8.4 Data Retention Policy

| Data Type | Default Retention | Configurable |
|---|---|---|
| Raw session transcripts | 12 months | Yes (Pro+: 1–36 months) |
| Extracted items | 24 months | Yes (Pro+) |
| Audit logs | 7 years | No (compliance) |
| Sync logs | 24 months | Yes |
| Deleted user data | Purged within 30 days of deletion request | No |

---

## 9. Integrations & Third-Party Tools

### 9.1 Integration Priority Matrix

| Tool | Priority | Data Pushed | Users Served |
|---|---|---|---|
| Jira | P0 (MVP) | Issues, Epics, Sub-tasks, Assignees, Due Dates, Priority | PMs, Eng Leads |
| Notion | P0 (MVP) | Database entries, Page blocks, Properties | PMs, Consultants |
| Slack | P0 (MVP) | Channel messages, Formatted summaries | All personas |
| Linear | P1 (V1) | Issues, Projects, Cycles, Assignees | Eng Leads |
| Trello | P1 (V1) | Cards, Lists, Members, Due Dates | Consultants, PMs |
| Asana | P1 (V1) | Tasks, Sections, Assignees, Due Dates | PMs, Ops |
| GitHub | P1 (V1) | Issues, Labels, Assignees, Milestones | Eng Leads |
| Google Calendar | P1 (V1) | Events (deadline-based) | All personas |
| Outlook Calendar | P2 (V2) | Events (deadline-based) | Enterprise |
| Confluence | P2 (V2) | Pages, Decision logs | Enterprise |
| Monday.com | P2 (V2) | Items, Subitems, Assignees | Ops |
| ClickUp | P2 (V2) | Tasks, Docs, Assignees | Ops, PMs |
| Zapier | P2 (V2) | Webhook trigger for custom workflows | Power users |

### 9.2 Integration Implementation Details

#### Jira
- **Auth:** OAuth 2.0 (Atlassian identity)
- **API:** Jira Cloud REST API v3
- **Scopes:** `read:jira-work`, `write:jira-work`, `read:jira-user`
- **Mapping:** Action item → Issue (Story); priority → Jira priority; deadline → due date; owner → assignee
- **Epic Handling:** 5+ items → option to create parent Epic grouping
- **Webhook:** Jira status changes → update Chatly sync log

#### Notion
- **Auth:** Notion OAuth
- **API:** Notion API v1 (Blocks + Databases)
- **Mapping:** Action item → Database row; columns: Name, Owner, Deadline, Priority, Status (default "Not Started"), Source URL (links to Chatly session)

#### Slack
- **Auth:** Slack OAuth 2.0 (Bot token)
- **Scopes:** `chat:write`, `channels:read`, `users:read`
- **Format:** Block Kit formatted messages; workspace admin configures default channel; per-session override available

---

## 10. UX/UI Requirements & User Flows

### 10.1 Design Principles

| Principle | Implementation |
|---|---|
| Minimal Friction | Core actions completable in ≤ 3 clicks |
| Transparency | Always show what was extracted + why (confidence + source highlighting) |
| Progressive Disclosure | Advanced features never block core value delivery |
| Error Recovery | Every failure state has a clear explanation + actionable recovery path |
| Accessibility | WCAG 2.1 Level AA compliance required for all components |
| Privacy-Visible | Users clearly see what data is stored; easy access to delete/export controls |

### 10.2 Core User Flows

#### Flow 1: First-Time Onboarding (Target: < 5 minutes to first pipeline)

```
1. Sign Up (Google OAuth or email)
2. Workspace Setup (name + optional team invite)
3. Connect First Integration (Jira / Notion / Slack → OAuth → field mapping defaults)
4. Process First Session (paste or use sample conversation → < 10s processing)
5. Review Extractions (guided tooltips: "These are your action items. Click to edit.")
6. Sync to Tool (one-click)
7. Dashboard Redirect ("Your pipeline is live. Here's your dashboard.")
```

#### Flow 2: Regular Session Processing (Target: < 2 minutes paste to sync)

```
1. Dashboard → "New Session"
2. Input Method (Paste / Upload / Import from Extension)
3. Optional: Session Name + Project Tag
4. Submit → Processing status bar
5. Extraction Review (split-pane: conversation left, extracted items right)
   - Actions: Edit | Reject | Add | Approve All
6. Approve + Generate Pipeline (dependency visualization)
7. Sync Selection (checkboxes + field mapping confirmation)
8. Sync Confirmation (per-item status + links to created items in target tools)
```

#### Flow 3: Browser Extension Real-Time Capture

```
1. Open Claude.ai or ChatGPT.com → extension activates (badge: green = active)
2. Conduct AI conversation
3. Side panel shows extractions in near-real-time (per AI response)
4. Inline review per item (Approve / Reject / Edit)
5. "Finish Session" → items compiled into pipeline
6. Sync from extension side panel or Chatly web app
```

### 10.3 Information Architecture

```
Chatly Web App
│
├── Dashboard (Home)
│   ├── My Sessions
│   ├── Team Sessions (Admin only)
│   ├── My Tasks (cross-session)
│   └── Quick Stats (items today, synced today)
│
├── New Session
│   ├── Input (Paste / Upload / Import)
│   ├── Processing
│   ├── Extraction Review
│   ├── Pipeline Builder
│   └── Sync
│
├── Session Detail (/sessions/:id)
│   ├── Overview
│   ├── Extractions
│   ├── Pipeline
│   ├── Sync Log
│   └── Decision Log
│
├── Decision Log
│   ├── All Decisions (searchable)
│   ├── By Project Tag
│   └── By Date Range
│
├── Analytics (Admin)
│   ├── Workspace Overview
│   ├── Team Activity
│   └── Sync Performance
│
└── Settings
    ├── Workspace
    ├── Integrations
    ├── Members & Roles
    ├── Billing
    ├── Privacy & Data     ← Legal: data export, deletion, consent management
    ├── API Keys
    └── Profile
```

### 10.4 UI Component Requirements

| Component | Description |
|---|---|
| Conversation Viewer | Split-pane with syntax-highlighted extraction spans |
| Item Card | Type badge, text, owner chip, deadline tag, confidence bar, action buttons |
| Confidence Indicator | Color-coded bar + % (green ≥ 80%, yellow 50–79%, red < 50%) |
| Pipeline Board | Kanban drag-and-drop; swimlanes by owner or priority |
| Sync Status Badge | Pending / Synced / Failed / Not Synced per item |
| Integration Connector | OAuth modal with step indicator; field mapping table |
| Privacy Dashboard | View stored data; request export; request deletion |
| Session List | Virtualized list with search, filter, sort |

---

## 11. Non-Functional Requirements

### 11.1 Performance

| Metric | Requirement | Method |
|---|---|---|
| API response time (p95) | < 200ms (non-processing endpoints) | Datadog APM |
| Post-session processing | < 30s for ≤ 10,000 tokens | Job duration metric |
| Real-time extraction latency | < 3s per AI response (extension) | Client-side timing |
| Dashboard load time | < 2s (p95, 500 sessions) | Synthetic monitoring |
| Sync to Jira/Notion/Slack | < 10s (< 20 items) | Sync log timestamps |
| Concurrent users | 1,000 at MVP; 10,000 at V2 | k6 load test |
| NLP throughput | 100 sessions/min at V1; 1,000/min at V2 | Queue depth monitoring |

### 11.2 Availability & Reliability

| Metric | Requirement |
|---|---|
| API uptime SLA | 99.9% (Pro); 99.95% (Enterprise) |
| Maintenance windows | < 4 hours/month; off-peak; 48h advance notice |
| RTO (Recovery Time Objective) | < 1 hour for total service failure |
| RPO (Recovery Point Objective) | < 15 minutes (database backup frequency) |
| Data redundancy | Multi-AZ RDS; S3 cross-region replication |

### 11.3 Security

| Requirement | Implementation |
|---|---|
| Encryption in transit | TLS 1.3 for all API and web traffic |
| Encryption at rest | AES-256 (RDS encryption + S3 SSE) |
| OAuth tokens | AES-256 encrypted; never exposed in logs |
| PII handling | Raw transcripts treated as sensitive PII; zero logging policy |
| Authentication | JWT (1-hour expiry) + refresh token rotation |
| Authorization | Server-side RBAC; workspace isolation at DB query level |
| Rate limiting | Per-user + per-workspace; IP-based throttling for unauthenticated endpoints |
| SAST | Automated scanning (Snyk) in CI/CD pipeline |
| Penetration testing | Quarterly external pen test |
| Secrets management | AWS Secrets Manager; no secrets in code or environment files |
| Bug bounty | Launched at V1 GA |

### 11.4 Scalability

| Scenario | Requirement |
|---|---|
| Session volume growth | 10x increase supportable without re-architecture |
| New integration addition | Independent deployment; zero downtime |
| NLP model upgrade | Hot-swap via canary A/B deployment |
| Workspace isolation | Zero cross-workspace data leakage under any failure condition |
| Token limit increase | Configurable per tier; no code changes required |

### 11.5 Usability & Accessibility

| Requirement | Specification |
|---|---|
| Accessibility | WCAG 2.1 Level AA compliance |
| Browser support | Chrome 110+, Edge 110+, Firefox 115+, Safari 16+ |
| Responsive design | Fully functional at 1280px, 1440px, 1920px |
| Keyboard navigation | All core actions completable via keyboard only |
| Screen reader | ARIA labels on all interactive components |
| Internationalization | English at MVP; i18n framework integrated Day 1 for V2 expansion |

---

## 12. Success Metrics & Analytics Framework

### 12.1 North Star Metric

> **Execution Pipelines Created per Week (Workspace-Level)**

Captures frequency of converting AI conversations into structured, actionable pipelines — core product value delivered, not just usage activity.

### 12.2 Metric Hierarchy

#### Acquisition

| Metric | Target (Beta) | Target (V1) |
|---|---|---|
| Signups | 200 | 1,000 |
| Activation (processed ≥ 1 session) | 70% | 75% |
| Time to first pipeline (from signup) | < 8 min | < 5 min |

#### Engagement

| Metric | Target (V1) |
|---|---|
| Sessions/active user/week | ≥ 4 |
| Pipeline creation rate (sessions → pipelines) | ≥ 75% |
| Sync rate (pipelines → ≥ 1 integration sync) | ≥ 60% |
| Extension active users / total users | ≥ 30% |
| DAU/MAU | ≥ 40% |

#### Retention

| Metric | Target (V1) |
|---|---|
| Week-1 retention | ≥ 65% |
| Month-1 retention | ≥ 50% |
| Month-3 retention | ≥ 35% |
| Churned account recovery (win-back) | ≥ 15% |

#### Revenue

| Metric | Target (End Year 1) |
|---|---|
| MRR | $125,000 |
| ARR | $1.5M |
| ARPA (team) | $600/month |
| Gross Revenue Churn | < 5%/month |
| Net Revenue Retention | ≥ 110% |
| LTV:CAC | ≥ 3:1 |

#### Quality

| Metric | Target (MVP) | Target (V1) |
|---|---|---|
| NLP Extraction F1 Score | ≥ 82% | ≥ 88% |
| User correction rate (edits/session) | < 2.5 | < 1.5 |
| Sync failure rate | < 3% | < 1.5% |
| NPS Score | ≥ 35 | ≥ 50 |

### 12.3 Analytics Instrumentation

**Stack:** Segment → Mixpanel (product analytics) + Amplitude (funnel analysis)

**Key Events:**

| Event | Trigger | Properties |
|---|---|---|
| `session_submitted` | User submits conversation | source, token_count, workspace_id |
| `session_processed` | Processing completes | duration_ms, items_extracted, session_id |
| `item_reviewed` | User acts on extraction | action (approved/rejected/edited), item_type, confidence_score |
| `pipeline_created` | Pipeline generated | item_count, session_id |
| `sync_triggered` | User initiates sync | target_tool, item_count |
| `sync_completed` | Sync finishes | success_count, failure_count, duration_ms |
| `integration_connected` | User connects tool | tool_name, workspace_id |
| `extension_activated` | Extension detects AI platform | platform (chatgpt/claude/gemini) |

**Funnel Definitions:**
1. Acquisition: Visit → Signup → First Session Submitted → First Pipeline Created → First Sync
2. Engagement: Login → New Session → Process → Review → Sync
3. Retention: Weekly cohort analysis by signup date

---

## 13. Legal & Compliance Framework

> **ATTORNEY REVIEW REQUIRED:** All content in this section is informational planning material only. No element constitutes legal advice. All legal frameworks, contract terms, compliance strategies, and regulatory interpretations must be reviewed and approved by qualified legal counsel before implementation or use.

### 13.1 Regulatory Compliance Overview

Chatly processes AI conversation transcripts which may contain PII, strategic business information, and sensitive organizational data. As a globally operating SaaS platform, Chatly must comply with the following regulatory frameworks:

#### Data Protection Regulations

| Regulation | Jurisdiction | Applicability | Required By |
|---|---|---|---|
| **GDPR** | European Union | Any EU data subject's data processed | MVP Launch |
| **CCPA / CPRA** | California, USA | California residents | MVP Launch |
| **LGPD** | Brazil | Brazilian users | V1 (international expansion) |
| **PIPEDA** | Canada | Canadian users | V1 |
| **PDPA** | Singapore / Thailand | APAC expansion | V2 |

#### AI-Specific Regulations

| Regulation | Jurisdiction | Key Obligations | Required By |
|---|---|---|---|
| **EU AI Act** | European Union | Chatly NLP pipeline likely classified as Limited Risk. Requires transparency notices to users about AI-generated extractions; right to human review of all extractions before sync | V1 (EU users) |
| **US AI Executive Orders** | United States | Transparency in AI outputs; bias testing for federal contracts | V2 (if pursuing FedRAMP) |

#### Industry-Specific Regulations (Future Segments)

| Regulation | Trigger | Obligation |
|---|---|---|
| **HIPAA** | Healthcare enterprise clients | BAA required; PHI handling restrictions; audit trails |
| **SOX** | Public company clients | Financial data handling; audit log integrity |
| **FERPA** | Education institution clients | Student data protection requirements |
| **FISMA / FedRAMP** | US Government contracts | Mandatory security controls; ATO process |

---

### 13.2 Data Privacy Architecture & Policy

#### 13.2.1 Privacy-by-Design Principles

1. **Data Minimization:** Collect only data strictly necessary. Raw transcripts discarded from pipeline workers after extraction; only structured outputs retained.
2. **Purpose Limitation:** Data collected for NLP processing is not used for advertising, profiling, or sold to third parties.
3. **Storage Limitation:** Configurable retention periods with automatic deletion on expiry.
4. **Accuracy:** Users can correct extracted data at any time via the review UI.
5. **Integrity & Confidentiality:** AES-256 at rest; TLS 1.3 in transit for all personal data.
6. **Accountability:** DPA-ready documentation; audit logs; DPO appointment required before EU launch.

#### 13.2.2 User Consent Framework

| Consent Type | When | Mechanism |
|---|---|---|
| Account creation consent | Signup | Affirmative checkbox (unchecked by default) |
| Data processing consent | Signup | Clear disclosure of how transcripts are processed, stored, and deleted |
| Cookie consent | First visit | GDPR-compliant banner; granular opt-in by category |
| Marketing consent | Signup + in-app | Separate opt-in; unsubscribe in every email |
| Third-party sync consent | Per-integration connection | OAuth flow + explicit disclosure of data shared with third party |

**Consent Records:** Timestamp, policy version, IP address, and consent method stored per user for all GDPR/CCPA-covered data subjects.

#### 13.2.3 Data Subject Rights Implementation

| Right | Regulation | Chatly Implementation | SLA |
|---|---|---|---|
| Right to Access | GDPR Art. 15, CCPA | `GET /users/{id}/data-export` API; in-app "Download My Data" | 30 days |
| Right to Erasure | GDPR Art. 17, CCPA | `POST /users/{id}/deletion-request`; cascading deletion of sessions, extractions, pipelines | 30 days |
| Right to Portability | GDPR Art. 20 | Machine-readable export (JSON / CSV) | 30 days |
| Right to Rectification | GDPR Art. 16 | In-app editing of all personal data fields | Immediate |
| Right to Restriction | GDPR Art. 18 | Processing suspension on request pending review | 30 days |
| Right to Object | GDPR Art. 21, CCPA | Opt-out of analytics; opt-out of model training | Immediate |
| Do Not Sell (CCPA) | CCPA § 1798.120 | "Do Not Sell My Personal Information" link in footer | Immediate |

#### 13.2.4 Cross-Border Data Transfer Mechanisms

| Transfer Scenario | Mechanism |
|---|---|
| EU → US | Standard Contractual Clauses (SCCs) — EU Commission 2021 version |
| EU → UK | UK International Data Transfer Agreement (IDTA) |
| EU → other third countries | SCCs + Transfer Impact Assessment (TIA) per destination |
| Sub-processor transfers | DPA with each sub-processor |

**Sub-Processor Registry** (to be maintained and published publicly):

| Sub-Processor | Purpose | Location | Transfer Mechanism |
|---|---|---|---|
| AWS | Infrastructure, storage, compute | US + EU regions | SCCs |
| OpenAI | LLM disambiguation (low-confidence items) | US | SCCs + DPA |
| Pinecone | Vector database (semantic search) | US | SCCs |
| Stripe | Payment processing | US | SCCs |
| Datadog | Monitoring and logging | US | SCCs |
| Sentry | Error tracking | US | SCCs |
| Segment | Analytics pipeline | US | SCCs |

---

### 13.3 Terms of Service & Enterprise Contract Framework

> All contract templates require qualified attorney review and approval before use.

#### 13.3.1 Terms of Service — Key Clauses

**1. Acceptable Use Policy**
Users may not process conversations containing: classified government information, ITAR/EAR export-controlled data, or data where third-party processing is prohibited by the source platform's ToS. Users are responsible for ensuring they have the right to upload and process submitted content.

**2. Intellectual Property Ownership**
- Conversation content submitted remains the IP of the user/their organization
- Chatly extracts structured data from user content but claims no ownership of conversation content
- NLP models, pipeline architecture, extraction algorithms, and platform software are exclusive IP of Chatly Inc.
- Users grant Chatly a limited, non-exclusive license to process submitted content solely to provide the service

**3. Limitation of Liability**
- Total aggregate liability: amounts paid by customer in the 12 months preceding the claim
- Not liable for: inaccurate NLP extractions; decisions made based on AI-extracted items; third-party integration failures beyond Chatly's reasonable control
- Exclusions from cap: data breach caused by Chatly's gross negligence; willful misconduct; death or personal injury

**4. Service Level Agreement Remedies**

| SLA Metric | Target | Remedy |
|---|---|---|
| API uptime (Pro) | 99.9% | 10% monthly credit per 0.1% below target |
| API uptime (Enterprise) | 99.95% | 20% monthly credit per 0.05% below target |
| Sync failure rate | < 2% | Service credit if exceeded two consecutive months |

**5. Data Processing**
Chatly processes conversation transcripts as a data processor on behalf of the customer (data controller) under GDPR. A DPA is incorporated by reference for all customers with EU data subjects.

**6. Termination**
- For convenience: 30-day notice (Pro); 90-day notice (Enterprise)
- Immediate termination for material breach (30-day cure period for remediable breaches)
- On termination: customer data exported and deleted within 30 days; audit logs retained per legal requirements

**7. Governing Law**
- Default: Delaware, USA (AAA arbitration; individual arbitration; class action waiver)
- Enterprise EU: Ireland (GDPR lead supervisory authority: Ireland DPC)

---

#### 13.3.2 Enterprise Contract Suite

| Document | Purpose | When Required |
|---|---|---|
| **Master Service Agreement (MSA)** | Overarching commercial terms; liability; IP; termination | All enterprise deals |
| **Order Form** | Specific deal terms: seats, price, term, integrations | Per deal |
| **Data Processing Agreement (DPA)** | GDPR/CCPA data processor obligations | Any customer with EU or California data subjects |
| **Business Associate Agreement (BAA)** | HIPAA compliance | Healthcare clients handling PHI |
| **Security Addendum** | Security controls, audit rights, breach notification SLAs | Enterprise security reviews |
| **SLA Addendum** | Custom uptime, support SLAs, escalation paths | Enterprise clients requiring SLA guarantees |
| **NDA / MNDA** | Mutual non-disclosure during procurement | Standard for enterprise sales process |

**DPA Key Terms:**
- Process personal data only on documented controller instructions
- Article 32 Technical and Organizational Measures (TOMs): encryption, access controls, incident response
- Sub-processor changes: 30-day advance notice; customer right to object
- Data return or deletion within 30 days of contract termination
- Assistance with data subject requests and supervisory authority inquiries
- Breach notification: without undue delay (within 72 hours of Chatly becoming aware)

---

### 13.4 Intellectual Property Strategy

#### 13.4.1 Protectable IP Assets

| Asset | Protection Strategy | Timeline |
|---|---|---|
| NLP extraction pipeline architecture | Trade secret + Patent application | Patent filing: Month 6 |
| Fine-tuned RoBERTa classifiers | Trade secret (do not publish model weights) | Ongoing |
| Proprietary training dataset (user corrections) | Trade secret; contractual protections in ToS | Ongoing |
| "Chatly" brand name / logo | Trademark registration (USPTO + EUIPO) | Month 1 |
| "AI Conversation Operationalization" | Trademark registration (USPTO); brand use strategy | Month 3 |
| Browser extension code | Copyright (automatic) + code obfuscation | Ongoing |

#### 13.4.2 Employee & Contractor IP Agreements

- All employees and contractors must sign IP Assignment and Confidentiality Agreements before starting
- IP assignment covers all work product created during employment/engagement
- Non-compete provisions reviewed per jurisdiction (California: unenforceable; Delaware: enforceable with reasonable scope)
- Moonlighting policy: employees must disclose external AI/SaaS projects; no work on competing products

#### 13.4.3 Open Source Dependency Management

| Risk | Mitigation |
|---|---|
| Copyleft licenses (GPL/AGPL) | SCA in CI/CD (Snyk); GPL/AGPL dependencies prohibited in core pipeline |
| MIT/Apache 2.0 | Permitted; maintain attribution notices |
| ML model patent risk | Review model licenses; use only permissively licensed models |
| OpenAI API usage | Comply with OpenAI usage policies; do not use API outputs to train competing models |

#### 13.4.4 User Content & Conversation Data Ownership

**Users own their conversation content.** Chatly's right is limited to processing it for service delivery. Chatly will not:
- Use conversation content to train models without explicit opt-in consent
- Share conversation content with third parties except sub-processors under DPA
- Retain raw transcripts beyond the workspace's retention policy setting

**Model Training Opt-in Program:** Users who voluntarily opt in to contribute anonymized correction data receive service credit and early feature access. Opt-in is granular, revocable, and separately tracked from core service consent.

---

### 13.5 Regulatory Compliance Roadmap

| Milestone | Timeline | Description |
|---|---|---|
| Privacy Policy v1 | MVP (Week 16) | GDPR/CCPA compliant; attorney-reviewed and published |
| Terms of Service v1 | MVP (Week 16) | SaaS ToS; attorney-reviewed |
| Cookie consent banner | MVP (Week 16) | GDPR-compliant; granular opt-in by category |
| Standard DPA template | MVP (Week 16) | GDPR DPA for EU customers |
| Sub-processor list published | MVP (Week 16) | Publicly available on website |
| Data rights endpoints live | MVP (Week 14) | Deletion, export, audit log APIs |
| SOC 2 Type I initiation | Month 7 (V1) | Engage auditor; readiness assessment |
| EU AI Act transparency compliance | V1 (EU launch) | Legal review of NLP pipeline classification; transparency notices |
| EU data residency (eu-west-1) | V1 (Month 7) | AWS EU region for EU workspaces |
| GDPR DPO appointment | V1 (Month 7) | Required for large-scale EU data processing |
| HIPAA BAA template | V1 (Month 8) | Required before any healthcare enterprise deal |
| SOC 2 Type I report | Month 10 | Required for enterprise sales qualification |
| ISO 27001 initiation | Q4 2026 | Enhances enterprise trust globally |
| SOC 2 Type II audit | Q1 2027 | Demonstrates ongoing compliance controls |
| LGPD / PIPEDA compliance | Q1 2027 | International expansion — Brazil + Canada |
| FedRAMP Moderate initiation | Q2 2027 | Only if pursuing US Government contracts |

---

### 13.6 Legal Risk Register

| Risk ID | Legal Risk | Likelihood | Impact | Severity | Mitigation |
|---|---|---|---|---|---|
| L-01 | **AI Platform ToS Violation** — OpenAI or Anthropic claims processing exported conversations violates ToS | Low | Critical | High | Legal ToS review before MVP; user-export ingestion model; DPA with OpenAI; quarterly ToS monitoring |
| L-02 | **GDPR Violation** — Processing EU data subjects' transcripts without adequate legal basis or security | Medium | Critical | Critical | Privacy-by-design architecture; SCCs; DPA with sub-processors; DPO appointment; ongoing GDPR audit |
| L-03 | **CCPA Non-Compliance** — Failure to honor California consumer rights | Low | High | High | All CCPA rights endpoints at MVP; "Do Not Sell" link; privacy-first architecture |
| L-04 | **IP Infringement** — NLP model training using third-party data without license | Medium | High | High | SCA in CI/CD; legal review of all training data; permissively licensed models only |
| L-05 | **Liability from Faulty Extraction** — User makes business decision based on incorrect extraction; sues | Medium | Medium | Medium | Limitation of liability in ToS; mandatory review UI before sync; confidence indicators; "informational only" disclaimers |
| L-06 | **Data Breach** — Unauthorized access to conversation transcripts | Low | Critical | High | AES-256 encryption; zero-log policy for raw transcripts; pen testing; SOC 2; cyber liability insurance; 72h GDPR notification |
| L-07 | **HIPAA Violation** — Healthcare client PHI processed without BAA | Low | Critical | High | BAA required before healthcare onboarding; HIPAA compliance checklist |
| L-08 | **Employment Law** — Worker misclassification; IP assignment gaps for international contractors | Medium | Medium | Medium | Jurisdiction-appropriate contractor agreements; attorney review per country |
| L-09 | **Export Control / Sanctions** — Chatly used to process ITAR/EAR-controlled information | Low | High | Medium | Acceptable Use Policy prohibition; geo-blocking for sanctioned countries |
| L-10 | **Patent Troll Risk** — Third party claims patent on AI conversation extraction techniques | Medium | High | High | Prior art search before patent filing; defensive patent portfolio; FTO analysis at V1 |

---

## 14. Go-to-Market Strategy

### 14.1 Positioning

**Positioning Statement:**
For knowledge workers and teams who use AI assistants daily, Chatly is the AI conversation operationalization platform that automatically transforms AI conversations into structured, executed work — unlike manual task entry or generic automation tools, Chatly understands the semantic content of AI conversations and routes tasks, decisions, and ownership directly into the tools your team already uses.

**Category:** AI Conversation Operationalization (category creation strategy)

**Key Messages by Persona:**
- PMs: *"Turn every ChatGPT planning session into a Jira sprint in one click."*
- Eng Leads: *"Stop re-entering architecture decisions into Linear. Chatly does it automatically."*
- Consultants: *"Deliver AI-assisted projects with clean, auditable documentation. Automatically."*

### 14.2 Pricing Model

| Tier | Price | Target | Limits |
|---|---|---|---|
| Free | $0/month | Individual exploration | 5 sessions/month, 10K tokens/session, 1 integration |
| Pro (Individual) | $19/month | Power individual users | 50 sessions/month, 50K tokens/session, 3 integrations |
| Team | $49/user/month (min 3 seats) | Small–mid teams | Unlimited sessions, 50K tokens/session, all integrations, admin dashboard |
| Enterprise | Custom ($75+/user/month) | 50+ user companies | Unlimited everything, SSO/SAML, SOC 2, SLA, dedicated support, custom NLP fine-tuning |

**Strategy Notes:**
- Annual billing at 20% discount to improve cash flow
- Free tier drives organic viral growth through workspace invitations
- Team tier is the primary growth engine; upsell from Individual Pro

### 14.3 Distribution Channels

#### Primary

1. **Product-Led Growth (PLG):** Free → viral invite loops → team adoption → Team tier conversion. Target: 60% of ARR from PLG-originated accounts.

2. **App Marketplaces:** Jira Marketplace (Atlassian), Notion Integrations Gallery, Slack App Directory — high-intent discovery at zero CAC.

3. **Content Marketing:** SEO blog ("How to turn ChatGPT outputs into Jira tickets"); YouTube workflow demos. Target: 30K monthly organic visitors by Month 6.

#### Secondary

4. **Partnership / Co-Marketing:** AI tool integration spotlights; PM communities (Lenny's Newsletter, Reforge, Product School)
5. **Outbound Sales (Enterprise):** Target VP Product, VP Engineering at 200–2,000 person companies; SDR hire Month 4 post-launch
6. **Product Hunt Launch:** Coordinated launch; target Top 3 Product of the Day

### 14.4 Launch Plan

| Phase | Timeline | Activities |
|---|---|---|
| Pre-Launch (Weeks 1–12) | Build & beta | Private beta (50 hand-selected users); weekly feedback calls; Product Hunt teaser |
| Beta Expansion (Weeks 12–16) | Soft launch | Open beta waitlist; onboard 200 users; iterate on extraction quality and UX |
| GA Launch (Week 16) | Public launch | Product Hunt; press outreach (TechCrunch, The Rundown, Ben's Bites); waitlist email blast |
| Growth Phase (Months 5–12) | Scale | Content marketing engine; marketplace listings; first outbound sales motion |

---

## 15. Risk Analysis & Mitigation

### 15.1 Risk Register

| Risk ID | Risk | Category | Likelihood | Impact | Severity | Mitigation |
|---|---|---|---|---|---|---|
| R-01 | NLP extraction accuracy insufficient for user trust | Technical | High | High | Critical | Hybrid NLP + LLM approach; confidence scoring; mandatory human review before sync |
| R-02 | LLM API cost spikes make unit economics unviable | Financial | Medium | High | High | Fine-tuned local models; LLM only for disambiguation; token limits per tier |
| R-03 | Integration breaking changes from Jira/Notion/Slack APIs | Technical | Medium | High | High | API version pinning; integration monitoring; SLA-backed fix response time |
| R-04 | User privacy concerns about uploading AI transcripts | Legal/Trust | High | High | Critical | Privacy-by-design; EU data residency; DPA; clear consent — see Section 13 |
| R-05 | Slow adoption due to behavior change friction | Market | Medium | High | High | PLG motion; extension as zero-friction overlay; generous free tier |
| R-06 | Competitor ships native AI-to-task feature | Competitive | Medium | High | High | Accelerate integration breadth and NLP quality; own "AI Conversation Operationalization" category |
| R-07 | OpenAI / Anthropic restrict third-party conversation processing | Legal | Low | Critical | High | Multi-LLM strategy; ToS legal review; user-export ingestion fallback — see Section 13, L-01 |
| R-08 | Browser extension rejected from Chrome Web Store | Technical | Low | High | Medium | Pre-submission compliance review; manual upload remains primary; Firefox extension backup |
| R-09 | Data breach exposing conversation transcripts | Security | Low | Critical | High | AES-256 encryption; zero-log policy; SOC 2; bug bounty; cyber insurance — see Section 13, L-06 |
| R-10 | Key NLP engineering talent attrition | Operational | Medium | High | High | Competitive comp; NLP knowledge documentation; cross-training; managed NLP API as fallback |
| R-11 | GDPR enforcement action from EU supervisory authority | Legal | Low | Critical | High | Privacy-by-design; DPO appointment; SCCs — see Section 13, L-02 |
| R-12 | CAC exceeds LTV (financial model failure) | Financial | Medium | High | High | PLG-first to minimize CAC; monitor LTV:CAC monthly; pivot to higher-ACV enterprise if needed |

### 15.2 Scenario Planning

**Scenario A: NLP Quality Falls Short**
- Trigger: Beta feedback shows > 5 min correcting extractions/session (F1 < 75%)
- Response: Increase LLM reliance; invest in labeled training data collection; implement "suggest mode" (no auto-create)

**Scenario B: AI Platform ToS Conflict**
- Trigger: OpenAI or Anthropic prohibits third-party processing of exported conversations
- Response: Shift to user-owned export model; engage legal counsel; publish public policy statement

**Scenario C: Competitor Ships Similar Feature**
- Trigger: Jira, Notion, or Linear announces native AI → task extraction
- Response: Accelerate cross-platform multi-tool value; deepen NLP; accelerate enterprise with SOC 2 + custom NLP fine-tuning as differentiators

**Scenario D: GDPR Enforcement Action**
- Trigger: EU supervisory authority initiates investigation
- Response: Engage DPO + external counsel immediately; cooperate fully; suspend EU operations if required; document remediation publicly

---

## 16. Competitive Landscape

### 16.1 Competitive Matrix

| Capability | Chatly | Otter.ai | Fireflies.ai | Zapier | Notion AI | Linear AI |
|---|---|---|---|---|---|---|
| AI conversation extraction | Native, purpose-built | Human meeting focus | Human meeting focus | None | Limited (Notion only) | Limited (Linear only) |
| Multi-tool integration | 10+ tools | Jira, Notion, Slack | CRM + Slack | Unlimited (manual config) | Notion only | Linear only |
| Decision logging | Structured, searchable | Basic transcript | Basic transcript | None | None | None |
| Real-time extension | Yes (P1) | Meeting bot | Meeting bot | No | No | No |
| Confidence scoring | Yes | No | No | No | No | No |
| NLP pipeline | Custom multi-stage | Transcription-only | Transcription-only | Rule-based triggers | GPT prompt-based | GPT prompt-based |
| Owner resolution | Workspace-aware | No | No | No | No | No |
| Pipeline visualization | Yes | No | No | No | No | No |
| Privacy controls | Enterprise-grade (SOC 2, DPA) | Standard | Standard | Standard | Standard | Standard |
| Pricing (team) | $49/user/month | $20/user/month | $19/user/month | $69/month flat | $10/user/month | $8/user/month |

### 16.2 Competitive Positioning

**Otter.ai / Fireflies.ai:** Human-to-human meeting transcription. NLP built for speaker-labeled meeting notes — not AI conversation extraction. Fundamentally different paradigm.

**Notion AI / Linear AI:** Single-tool AI features. Cannot extract across tools, no multi-integration sync, limited to their platform's data model.

**Zapier / Make:** Integration automation without semantic understanding. Require manual rule configuration; cannot understand conversation content.

**ChatGPT / Claude / Gemini:** Chatly's largest transcript source — not competitors.

### 16.3 Defensibility Moat

1. **Data Network Effect:** User corrections feed a proprietary training dataset that self-reinforces and becomes increasingly difficult to replicate at scale
2. **Integration Network:** Each additional integration increases workspace switching cost. A team using Jira + Notion + Slack + Linear has four simultaneous switching costs
3. **Category Ownership:** By naming and evangelizing "AI Conversation Operationalization," Chatly aims to be the category-defining brand — as Zoom became synonymous with video calls

---

## 17. Product Roadmap (MVP to V2)

### 17.1 MVP (Weeks 1–16) — Core Value Validation

**Theme:** Prove structured extraction from AI conversations creates enough value to retain users and drive initial payments.

| Feature | Priority | Owner Team | Est. Weeks |
|---|---|---|---|
| Ingestion Engine (paste + file upload) | P0 | Backend | Weeks 1–4 |
| NLP Extraction Pipeline v1 | P0 | NLP | Weeks 2–8 |
| Extraction Review UI | P0 | Frontend | Weeks 4–8 |
| Execution Pipeline Builder | P0 | Frontend + Backend | Weeks 7–10 |
| Jira Integration | P0 | Backend | Weeks 6–10 |
| Notion Integration | P0 | Backend | Weeks 8–12 |
| Slack Integration | P0 | Backend | Weeks 9–11 |
| Conversation & Pipeline Dashboard | P0 | Frontend | Weeks 9–12 |
| Workspace & Team Management + RBAC | P0 | Backend | Weeks 3–6 |
| Auth (Google OAuth + email) | P0 | Backend | Weeks 1–2 |
| **Privacy Policy + ToS published** | P0 | Legal + Product | Week 14 |
| **DPA template + Cookie consent banner** | P0 | Legal + Backend | Week 14 |
| **Data deletion + export API endpoints** | P0 | Backend | Weeks 12–14 |
| **Audit log implementation** | P0 | Backend | Weeks 10–12 |
| Beta Onboarding Flow | P0 | Frontend | Weeks 12–14 |
| Internal QA + Beta Testing | P0 | QA | Weeks 14–16 |

**MVP Exit Criteria:**
- 200 beta users onboarded
- Extraction F1 ≥ 82%
- Jira, Notion, Slack integrations with < 2% sync failure rate
- Week-4 retention ≥ 55%
- NPS ≥ 40
- Privacy Policy, ToS, DPA live and attorney-reviewed
- Data rights APIs functional

---

### 17.2 V1 (Months 5–8) — Commercial Launch

**Theme:** Expand integrations, sharpen NLP, build monetization engine, launch enterprise-ready legal stack.

| Feature | Priority | Owner Team | Est. |
|---|---|---|---|
| Real-Time Browser Extension (Chrome) | P1 | Frontend (Ext.) | Months 5–6 |
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
| Analytics Dashboard | P1 | Frontend | Month 7 |
| **SOC 2 Type I audit initiation** | P1 | Infra + Legal | Month 7 |
| **HIPAA BAA template (attorney-reviewed)** | P1 | Legal | Month 8 |
| **EU data residency (eu-west-1)** | P1 | Infra | Month 7 |
| **DPO appointment** | P1 | Legal | Month 7 |
| **Sub-processor registry published** | P1 | Legal + Product | Month 7 |
| **EU AI Act transparency notices** | P1 | Product + Legal | Month 8 |

**V1 Exit Criteria:**
- 50 paying teams; $75K MRR
- Extraction F1 ≥ 88%
- 6 integrations live
- Month-1 retention ≥ 50%
- SOC 2 Type I audit initiated
- Enterprise legal stack (DPA, BAA, Security Addendum) available

---

### 17.3 V2 (Months 9–18) — Platform Maturity & Enterprise

**Theme:** Enterprise-grade reliability, developer ecosystem, compliance certifications, and global scale.

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
| **SOC 2 Type II certification** | P2 | Q1 2027 |
| **ISO 27001 certification** | P2 | Q1 2027 |
| **LGPD / PIPEDA compliance** | P2 | Q1 2027 |
| **EU AI Act full compliance review** | P2 | Q1 2027 |
| Mobile App (iOS + Android) | P2 | Q1 2027 |
| On-Premise Deployment (Beta) | P2 | Q1 2027 |
| FedRAMP Moderate initiation | P2 | Q2 2027 |
| Community Template Contributions | P2 | Q2 2027 |
| AI Assistant (ask Chatly about past sessions) | P2 | Q2 2027 |

---

### 17.4 Visual Roadmap Summary

```
TIMELINE:   Month 1–4           Month 5–8            Month 9–18
            |──MVP (Beta)──|    |──V1 (GA)──────|    |──V2 (Enterprise)──────────|

PRODUCT:    Core Extraction      Integration Scale     Platform + Enterprise
            Jira/Notion/Slack    Linear/Asana/GH       API/SAML/Custom NLP
            Dashboard            Decision Log           Analytics/Mobile
            Team Mgmt            Real-Time Extension    On-Premise Option

LEGAL:      ToS/Privacy/DPA     SOC 2 initiation       SOC 2 Type II
            Cookie consent       HIPAA BAA              ISO 27001
            Data rights APIs     EU residency + DPO     LGPD/PIPEDA/EU AI Act

REVENUE:    $0 (beta)            $75K MRR (Month 8)    $125K+ MRR (Month 12)

USERS:      200 beta users       50 teams / 1K users   200 teams / 5K+ users
```

---

## 18. Financial Projections

### 18.1 Revenue Model

- **Primary:** SaaS subscriptions (Free / Pro / Team / Enterprise)
- **Secondary (V2+):** Professional services — custom onboarding, NLP fine-tuning for enterprise

### 18.2 Revenue Projections

| Period | MRR | ARR | Paying Teams | Avg. Seats/Team | ARPA/Month |
|---|---|---|---|---|---|
| Month 4 (MVP Beta) | $0 | $0 | 0 | — | — |
| Month 8 (V1 GA) | $75,000 | $900,000 | 50 | 8 | $1,500 |
| Month 12 | $125,000 | $1,500,000 | 100 | 10 | $1,250 |
| Month 18 | $250,000 | $3,000,000 | 200 | 12 | $1,250 |

### 18.3 Unit Economics

| Metric | Target (V1) | Target (Year 2) |
|---|---|---|
| Average Contract Value (ACV) | $8,000/year | $15,000/year (team + enterprise mix) |
| CAC (blended) | < $2,500 | < $3,000 |
| LTV (36-month, team) | > $7,500 | > $10,000 |
| LTV:CAC | ≥ 3:1 | ≥ 4:1 |
| Gross Margin | 75%+ | 80%+ |
| Payback Period | < 12 months | < 10 months |
| Net Revenue Retention | ≥ 110% | ≥ 120% |

### 18.4 Cost Structure (Monthly Estimates)

| Cost Category | MVP | V1 | V2 |
|---|---|---|---|
| Infrastructure (AWS) | $3,000–$5,000 | $8,000–$12,000 | $20,000–$35,000 |
| LLM API (OpenAI) | $500–$2,000 | $3,000–$6,000 | $8,000–$15,000 |
| Engineering (6–8 FTE) | $60,000–$80,000 | $80,000–$100,000 | $120,000–$150,000 |
| Design (2 FTE) | $15,000–$20,000 | $20,000–$25,000 | $25,000–$30,000 |
| Legal & Compliance | $5,000–$10,000 | $8,000–$15,000 | $10,000–$20,000 |
| Sales & Marketing | $5,000 | $20,000–$30,000 | $40,000–$60,000 |
| SaaS Tools + Misc | $3,000 | $5,000 | $8,000 |

### 18.5 Funding Requirements

| Round | Target | Use of Funds | Timeline |
|---|---|---|---|
| Pre-Seed | $500K–$1M | MVP build (6 months runway); legal setup; infrastructure | Pre-MVP |
| Seed | $3M–$5M | V1 launch; team scale to 15 FTE; marketing; SOC 2 | Month 6 |
| Series A | $10M–$20M | V2 enterprise features; international expansion; sales team | Month 18 |

---

## Appendices

### Appendix A: Assumptions

1. AI platform providers (OpenAI, Anthropic, Google) do not materially restrict third-party processing of user-exported conversation transcripts within this roadmap timeline.
2. Target market continues to adopt AI assistants at current or higher rates through 2026–2027.
3. OpenAI GPT-4o mini API pricing remains within 2x of February 2026 pricing.
4. Core engineering team (6–8 engineers) assembled within 8 weeks of funding.
5. Integration APIs (Jira, Notion, Slack) maintain backward compatibility during V1 timeline.
6. EU AI Act requires transparency obligations for Chatly's Limited Risk classification — not pre-market conformity assessment.

---

### Appendix B: Open Questions

| # | Question | Owner | Target Resolution |
|---|---|---|---|
| 1 | Minimum F1 score for user trust without mandatory review step? | PM + UX Research | Week 8 (beta feedback) |
| 2 | Store raw transcripts or only extracted structured data? | Legal + Engineering | Week 2 |
| 3 | Optimal NLP self-hosted inference vs. LLM API cost/accuracy balance? | NLP Lead | Week 6 |
| 4 | Browser extension: Manifest V3 on Day 1 or MV2 initially? | Extension Lead | Week 4 |
| 5 | Build own fine-tuned model or use third-party NLP provider? | NLP Lead + CTO | Week 3 |
| 6 | Chatly Inc. incorporation jurisdiction (Delaware recommended)? | Legal Counsel | Pre-formation |
| 7 | Full-time DPO required at V1 or acceptable as fractional role? | Legal Counsel | Month 5 |
| 8 | Launch model training opt-in program at MVP or post-Series A? | PM + Legal | Month 4 |
| 9 | Enterprise price floor for custom NLP fine-tuning add-on? | CEO + PM | Month 10 |
| 10 | Does processing content through OpenAI's API for disambiguation violate OpenAI's ToS? | Legal Counsel | Week 2 |

---

### Appendix C: Glossary

| Term | Definition |
|---|---|
| Action Item | A concrete, executable task identified from an AI conversation |
| BAA | Business Associate Agreement — HIPAA contract between covered entity and service provider |
| CCPA / CPRA | California Consumer Privacy Act / California Privacy Rights Act |
| DPA | Data Processing Agreement — GDPR contract between data controller and processor |
| DPO | Data Protection Officer — GDPR-required role for large-scale personal data processors |
| Execution Pipeline | A structured, ordered set of tasks with owners, deadlines, and dependencies derived from a conversation |
| Extraction | The process of identifying and structuring entities from raw conversation text |
| F1 Score | Harmonic mean of precision and recall; measures NLP extraction quality |
| FedRAMP | Federal Risk and Authorization Management Program — US government cloud security standard |
| GDPR | General Data Protection Regulation (European Union) |
| Integration Adapter | A service module handling communication with a specific third-party tool |
| LGPD | Lei Geral de Proteção de Dados — Brazil's data protection law |
| MSA | Master Service Agreement — overarching commercial contract framework |
| NLP | Natural Language Processing |
| PIPEDA | Personal Information Protection and Electronic Documents Act (Canada) |
| Pipeline Sync | The action of pushing a structured execution pipeline to one or more workflow tools |
| PLG | Product-Led Growth — acquisition strategy driven by the product itself |
| SCC | Standard Contractual Clauses — EU-approved mechanism for cross-border data transfers |
| Session | A single AI conversation submitted to Chatly for processing |
| SOC 2 | Service Organization Control 2 — security and compliance audit standard for SaaS |
| SRL | Semantic Role Labeling — NLP technique identifying "who did what to whom when" |
| TAM / SAM / SOM | Total / Serviceable / Serviceable Obtainable Market |
| TOM | Technical and Organizational Measures — GDPR Article 32 security control requirements |
| Workspace | An organizational unit in Chatly containing users, sessions, integrations, and settings |

---

### Appendix D: Legal Document Checklist

*Status to be maintained by Legal Lead. All items require qualified attorney review and approval before use.*

| Document | Status | Attorney Reviewed | Effective Date |
|---|---|---|---|
| Privacy Policy v1 | Pending | No | — |
| Terms of Service v1 | Pending | No | — |
| Cookie Policy | Pending | No | — |
| Standard DPA | Pending | No | — |
| Enterprise MSA Template | Pending | No | — |
| HIPAA BAA Template | Pending | No | — |
| Security Addendum | Pending | No | — |
| SLA Addendum | Pending | No | — |
| Employee IP Assignment Agreement | Pending | No | — |
| Contractor IP Assignment Agreement | Pending | No | — |
| NDA / MNDA Template | Pending | No | — |
| Sub-Processor Registry | Pending | No | — |

---

*Document Version: 2.0*
*Last Updated: February 20, 2026*
*Next Review Date: March 20, 2026*
*Prepared by: Kartik Bhalerao*
*Legal content requires qualified attorney review before implementation.*
*Confidential — For Internal Distribution Only*

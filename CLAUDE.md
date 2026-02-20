# CLAUDE.md

This file provides context and instructions for Claude Code when working in this repository.

## Project Overview

- **Product:** Chatly — a messaging/communication platform
- **Repo:** Catley_PRD
- **Author:** Kartik Bhalerao
- **Document Type:** Product Requirements Document (PRD)
- **Current Version:** 2.0 (Draft — Internal Review)
- **Classification:** Confidential — Internal Distribution Only

## Repository Structure

```
Chatly_PRD.md   — Main PRD document (primary file)
README.md       — Repo overview
CLAUDE.md       — This file
```

## Working with the PRD

- The primary file is `Chatly_PRD.md` — all product requirements, legal framework, roadmap, and financials live here.
- The document follows a structured section format (18+ sections). Always maintain this structure when adding or editing content.
- Update the **Version History** table and **Last Updated** date whenever changes are made.
- Do not alter the **Legal Disclaimer** at the top — it must remain unchanged.

## Conventions

- Use Markdown tables for structured data (metrics, timelines, roles, etc.)
- Section headers follow the pattern: `## 1. Section Title`
- Keep writing professional and product-spec style — avoid casual language
- Classification: Confidential — do not add any public-facing or sensitive credentials

## Key Sections in Chatly_PRD.md

| # | Section |
|---|---------|
| 1 | Executive Summary |
| 2 | Problem Statement & Market Opportunity |
| 8 | Data Architecture |
| 13 | Legal & Compliance Framework |
| 18 | Financial Projections |

## Upgrade Notes

- When adding new sections, append to the Table of Contents and maintain sequential numbering.
- When updating roadmap or milestones, cross-check with Section 13 (Legal milestones) for alignment.
- Financial projections (Section 18) should be updated alongside any scope changes.
- Pending approvals (Legal Counsel, CTO, Head of Design, Head of Engineering) should be tracked in the Document Reviewers table.

## Git Workflow

- Do **not** auto-commit unless explicitly asked by the user.
- Do **not** track or commit any OneDrive folders or OS-generated files (e.g., `desktop.ini`).
- Add a `.gitignore` if OS/editor artifacts appear.

## Author Preferences

- Keep solutions simple and minimal — avoid over-engineering.
- Use Unix shell syntax even on Windows.

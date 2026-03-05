# Frontend Estimator — Custom Agents

This directory contains custom GitHub Copilot agents for the Frontend Estimator project.

---

## Available Agents

### 🎨 Frontend Estimator Agent

**File**: `FRONTEND_ESTIMATOR.agent.md`
**Agent Name**: `@frontend_estimator`

A specialized frontend development estimation agent for **Vue.js and React.js** projects.
Produces production-grade, realistic estimates validated against real-world project data.

---

#### 🎯 Scope

- **Technologies**: Vue 3 / Nuxt 3 / React 18 / Next.js
- **Focus**: Frontend UI only (no backend, DevOps, or native mobile)
- **Domain**: Domain-agnostic (works for any industry or project type)
- **Output**: TIME only (hours + timeline — no pricing or cost figures)

---

#### 💡 Key Capabilities

- **Phase 0 — Workspace Scan**: Automatically detects existing codebases before asking any questions
- **Legacy mode**: Links SOW requirements to existing implementation via gap analysis
- **New vs. Existing comparison**: Side-by-side effort and risk comparison when a legacy codebase is present
- **13-question framework**: Covers design assets, device support, RBAC, real-time, WCAG, integrations, and refactoring tolerance (legacy mode)
- **Anti-double-counting validation**: Verifies estimates before output
- **Dual output**: Creates a markdown file in `docs/estimations/` AND displays in chat

---

#### 🚀 Quick Start

```bash
@frontend_estimator [your frontend feature description or SOW]
```

**Examples:**

```bash
# From high-level description
@frontend_estimator Vue 3 admin dashboard with user management and analytics

# From detailed spec
@frontend_estimator
Tech: React 18 + Next.js + Tailwind
Features: E-commerce catalog, cart, checkout, order history
APIs: REST APIs ready

# From pasted SOW document
@frontend_estimator Estimate this SOW:
[paste Statement of Work or requirements]
```

---

#### 📥 Output Formats

| Format | How | Path |
|--------|-----|------|
| **Markdown** | Auto-created by agent | `docs/estimations/[project]-estimation-[date].md` |
| **PDF** | Browser-based, 1-click | Open `docs/estimations/generate-pdf.html`, paste markdown, click Generate |
| **CSV / JSON** | On request | Ask agent to export in that format |

---

#### ⚠️ Known Limitations

- **Scope**: Frontend only — no backend, infrastructure, DevOps, or native mobile estimation
- **Pricing**: Time estimates only — no hourly rates, budget calculations, or cost projections
- **Testing**: Includes automated unit/E2E tests (+20% overhead) — does NOT cover manual QA team time
- **Assumptions**: Estimates assume senior/mid-level developers with 3+ years of framework experience

---

## Knowledge Base Modules

All modules are in `knowledge-base/`. They are numbered in the order the agent loads them:

| File | Purpose |
|------|---------|
| `00_QUICK_START.md` | 5-step formula, common pattern hours, quick examples |
| `01_estimation_methods.md` | PERT, T-shirt sizing, story points, velocity |
| `02_scope_dependencies.md` | Frontend vs backend boundaries, scope exclusion rules |
| `03_technology_reference.md` | Vue/React component estimates, framework-specific patterns |
| `04_output_templates.md` | CSV/JSON/PDF export structures |
| `05_common_patterns.md` | CRUD, auth, dashboards, tables — reusable base estimates |
| `06_rapid_estimation.md` | T-shirt sizing, 5–30 min quick methods |
| `07_document_parsing.md` | SOW/PRD analysis and extraction strategies |
| `08_senior_architect_analysis.md` | Architecture review, tech-choice tradeoffs |
| `09_project_type_detection.md` | Greenfield vs legacy heuristics |
| `10_WORKED_EXAMPLES.md` | End-to-end worked estimation walkthroughs |
| `11_legacy_project_analysis.md` | Codebase scanning, tech debt scoring, SOW gap analysis, new-vs-existing comparison *(conditional — loaded in legacy mode only)* |

---

## Adding New Agents

To add a new agent to this directory:

1. Create a new `.agent.md` file here
2. Use this frontmatter format:

```markdown
---
name: agent_name
description: Brief description of what the agent does
tools: ['search/codebase', 'edit/editFiles', 'web/fetch']
---

# Agent Name

Agent instructions here...
```

3. Invoke with: `@agent_name [your query]`
4. Add an entry to this README under "Available Agents"

---

**Last Updated**: 2026-03-05

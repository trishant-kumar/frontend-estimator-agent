# GitHub Copilot Setup Guide

This guide covers how to set up and use the **Frontend Estimator Agent** (`@frontend_estimator`) in VS Code with GitHub Copilot.

---

## Setup

### 1. Install Required VS Code Extensions

These extensions are recommended for the best experience:

- **GitHub Copilot** — Core AI assistant
- **GitHub Copilot Chat** — Chat interface for agents
- **Markdown Preview Enhanced** — Preview estimation output files
- **Markdown All in One** — Editing markdown estimation documents

### 2. Activate the Agent

Once GitHub Copilot Chat is open, call the agent with:

```bash
@frontend_estimator [your project description or pasted SOW]
```

### 3. Agent File Location

The agent definition is at:

```
.github/agents/FRONTEND_ESTIMATOR.agent.md
```

If the agent is not responding, verify this file exists and that GitHub Copilot extensions are active.

---

## How the Agent Works

The agent runs in 6 phases every time it is invoked:

| Phase | What Happens |
|-------|-------------|
| **Phase 0** | Scans the workspace for an existing codebase. Confirms whether estimation is for legacy or new project. |
| **Phase 1** | Asks up to 13 clarifying questions (only relevant ones based on auto-detected complexity). |
| **Phase 2** | Breaks requirements into modules, assigns base hours. In legacy mode, runs SOW gap analysis. |
| **Phase 3–5** | Applies reusability reduction, strategic multipliers, RBAC/real-time/integration overheads, and confidence buffer. |
| **Phase 5.5** | *Legacy mode only* — Produces new-project vs. existing-project comparison table with recommended path. |
| **Phase 6** | Creates `docs/estimations/[project]-estimation-[date].md` AND displays the estimate in chat. |

---

## Generating a PDF

1. Open the created `.md` file in `docs/estimations/`
2. Copy all content (Ctrl+A → Ctrl+C)
3. Open `docs/estimations/generate-pdf.html` in your browser
4. Paste the markdown and click **Generate Preview**
5. Click **Generate PDF** → browser print dialog → **Save as PDF**

No installation required — the HTML generator works fully offline.

---

## Troubleshooting

### Agent Not Responding

- **Check agent name**: Use `@frontend_estimator` (not `@frontend-estimator` with a hyphen)
- **Verify file exists**: Confirm `.github/agents/FRONTEND_ESTIMATOR.agent.md` is present
- **Restart editor**: Restart VS Code and reload the GitHub Copilot extension
- **Check Copilot status**: Ensure GitHub Copilot is signed in and active (check bottom status bar)

### PDF Generator Not Working

- **File missing**: Verify `docs/estimations/generate-pdf.html` exists in the project
- **Browser compatibility**: Use a modern browser (Chrome, Firefox, Edge, or Safari — current versions)
- **JavaScript errors**: Open browser DevTools (F12) → Console tab to check for errors
- **Print dialog**: Ensure the browser print dialog opens when clicking "Generate PDF"
- **Offline mode**: The generator works without internet — no external dependencies

### Estimates Seem Too High

- Agent uses **production-grade estimates** — not best-case scenarios
- Includes **+20% overhead** for testing (unit + E2E), edge cases, code review, and rework buffer
- Based on **senior developer velocity** (3+ years experience with the framework)
- Includes all professional practices: validation, loading states, error handling, responsive design

### Estimates Seem Too Low

- Verify **RBAC, real-time features, WCAG compliance, and third-party integrations** are mentioned in requirements — agent detects these automatically from keywords
- Check that all modules/features are included in the requirements
- Remember that backend, DevOps, infrastructure, and manual QA are excluded from scope

### Estimation File Not Created

- Check `docs/estimations/` folder — the file is saved there automatically
- File naming format: `[project-name]-estimation-[YYYY-MM-DD].md`
- Ensure the agent has the `edit/editFiles` tool enabled in the agent frontmatter

### Agent Asks Too Many Questions

- Provide comprehensive requirements upfront to skip obvious questions
- Mention the framework explicitly (Vue 3 / React 18 / Nuxt 3 / Next.js)
- State API readiness, design completeness, and device targets in the initial request
- Attach or paste the full SOW/PRD document for complex projects

### Legacy Mode Not Triggering

- The agent auto-scans the workspace in Phase 0 — open the project that contains the legacy codebase in VS Code before invoking the agent
- If the scan misses it, provide the project details directly: framework, approximate component count, TypeScript usage, test coverage

---

## Knowledge Base Files

The agent uses these reference modules (located in `.github/agents/knowledge-base/`):

| # | File | When It Is Used |
|---|------|----------------|
| 00 | `00_QUICK_START.md` | Quick pattern hours reference |
| 01 | `01_estimation_methods.md` | PERT calculations, detailed methodology |
| 02 | `02_scope_dependencies.md` | Scope boundary questions |
| 03 | `03_technology_reference.md` | Framework-specific component estimates |
| 04 | `04_output_templates.md` | CSV/JSON export formatting |
| 05 | `05_common_patterns.md` | Standard module pattern lookup |
| 06 | `06_rapid_estimation.md` | Fast T-shirt sizing |
| 07 | `07_document_parsing.md` | SOW/PRD document analysis |
| 08 | `08_senior_architect_analysis.md` | Architecture and tech-choice review |
| 09 | `09_project_type_detection.md` | Greenfield vs legacy detection |
| 10 | `10_WORKED_EXAMPLES.md` | Reference examples |
| 11 | `11_legacy_project_analysis.md` | *Loaded only in legacy mode* — codebase scanning, tech debt scoring, gap analysis, new-vs-existing comparison |

---

**Last Updated**: 2026-03-05

# CareLink360 Custom Agents

This directory contains custom GitHub Copilot agents for specialized tasks in the CareLink360 project.

## Available Agents

### 🎨 Frontend Estimator Agent

**File**: `frontend_estimator.agent.md`  
**Agent Name**: `@frontend_estimator`

A specialized frontend development estimation agent for **Vue.js and React.js** projects.

#### 🎯 Scope

- **Technologies**: Vue.js and React.js ONLY
- **Focus**: Frontend development ONLY
- **Domain**: Domain-agnostic (works for any industry)
- **Estimates**: TIME ONLY (no budget, pricing, or cost)

#### 💡 Smart Features

✨ **Framework Clarification**: Asks which framework you prefer (Vue 3 / Nuxt 3 / React / Next.js) if not specified

✨ **Raw Requirement Interpretation**: Handles vague descriptions like:

- \"Dashboard page with statistics\" → Breaks down into specific components, charts, widgets
- \"User management screen\" → Interprets as table, forms, modals, actions
- \"Settings page\" → Translates into tabs, forms, toggles

✨ **Smart Questions**: Asks 3-5 clarifying questions to understand your needs better

✨ **Document Export**: After estimation, offers to generate downloadable documents in:

- 📄 **PDF** - Professional report for stakeholders/clients
- 📝 **Word (DOCX)** - Editable document for internal reviews
- 📋 **Markdown** - Plain text format for developers/version control

#### Quick Start

```bash
@frontend_estimator [your frontend feature description]
```

**Examples:**

```bash
# Raw/vague requirement (agent will ask for framework & details)
@frontend_estimator Need a dashboard page where users can see statistics

# Specific requirement
@frontend_estimator Vue 3 dashboard with user stats, sales charts, and activity feed

# With framework
@frontend_estimator Using React - build admin panel with user management
@frontend_estimator Design system with 20 components in Vue 3 + Tailwind CSS

# Next.js e-commerce UI
@frontend_estimator Next.js e-commerce: product catalog, cart, checkout (APIs provided)
```

#### 📥 Getting Estimation Documents

**What the Agent Creates Automatically:**
✅ **Markdown (.md)** - Complete estimation with all details
✅ **CSV (.csv)** - Tabular data for Excel/Google Sheets import
✅ **JSON (.json)** - Machine-readable format for tools/automation

**Manual Conversion (Browser-Based, 1-Click):**
⚠️ **PDF (.pdf)** - Use built-in `docs/estimations/generate-pdf.html` (open in browser, paste, generate)
⚠️ **Word (.docx)** - Use Pandoc CLI: `pandoc estimation.md -o estimation.docx` or copy/paste to Word

**Why?** The agent has file creation tools but cannot run browser automation or terminal commands. The included HTML generator makes PDF creation instant without any software installation!

#### 📚 Example Output

Want to see what the agent produces? Check out:
- **[Example CRM Estimation](../../docs/estimations/example-estimation-crm-dashboard.md)** - Complete estimation with RBAC, real-time, multi-language features

#### Supported: Vue 3, Nuxt 3, React 18+, Next.js, TypeScript, Tailwind, Material-UI, Vuetify

#### ⚠️ Known Limitations

- **PDF Generation**: Agent creates markdown, you convert to PDF using `docs/estimations/generate-pdf.html` (browser-based, no installation, 1-click)
- **Word Export**: Agent creates markdown, use Pandoc (`pandoc file.md -o file.docx`) or copy/paste to Word/Google Docs
- **Scope**: Frontend ONLY - no backend, infrastructure, DevOps, or native mobile estimation
- **Pricing**: Time estimates ONLY - no budget calculations, hourly rates, or cost projections
- **Testing**: Includes automated unit/E2E tests (+20%) - does NOT include manual QA team time
- **Assumptions**: Estimates assume senior/mid-level developers (3+ years experience) with framework expertise

---

## Usage

```bash
@frontend_estimator [describe your frontend feature or paste requirements]
```

Outputs: Executive summary, technical breakdown, and JSON format.

---

## 🚀 First-Time User Guide

### 1. Activate the Agent
```bash
@frontend_estimator [your requirement]
```

### 2. Provide Requirements (Choose One)

**Option A: High-Level Description** (Agent will ask clarifying questions)
```bash
@frontend_estimator Build a CRM dashboard with user management, analytics, and reports
```

**Option B: Detailed Requirements**
```bash
@frontend_estimator

Tech Stack: Vue 3 + Nuxt 3 + Vuetify
Modules:
- User Management (CRUD, roles, permissions - RBAC with 5 roles)
- Dashboard (charts, KPIs, real-time updates via WebSocket)
- Reports (export PDF/CSV, filters by date range)
- Settings (multi-language EN/ES/FR, user preferences)

APIs: Not ready, frontend-first approach
Design: Figma mockups complete
Devices: Desktop + mobile responsive
```

**Option C: Attach Document/Paste SOW**
```bash
@frontend_estimator Estimate this project:

[Paste Statement of Work, PRD, or requirements document]
```

### 3. Get Estimation Output

Agent provides:
- 📊 Module breakdown with hours
- 📈 Timeline with team size recommendations
- ⚠️ Risk analysis and assumptions
- 📄 Markdown, CSV, JSON files in `docs/estimations/`

### 4. Generate PDF (Optional)

1. Copy markdown from agent response
2. Open `docs/estimations/generate-pdf.html` in browser
3. Paste → Generate Preview → Generate PDF → Save (Ctrl+P)

---

**Last Updated**: February 2026

This directory contains custom GitHub Copilot agents for specialized tasks in the CareLink360 project.

## Available Agents

### 🚀 Project Estimator Agent

**File**: `project_estimator.agent.md`  
**Agent Name**: `@project_estimator`

A comprehensive project estimation agent that provides accurate effort estimation, resource planning, risk analysis, and complexity scoring for any software project.

#### Quick Start

```bash
@project_estimator [your project description or SOW]
```

#### What It Does

✅ **Analyzes**: SOW documents, PRD, feature specs, module specifications  
✅ **Provides**:

- ⏱ Effort estimation (hours / days / weeks)
- 👨‍💻 Resource planning (team composition & allocation)
- 🧩 Module-wise breakdown (granular task lists)
- ⚠ Risk analysis (technical, timeline, resource risks)
- 📊 Complexity scoring (1-100 scale with detailed factors)

✅ **Outputs**: Three formats

- Executive Summary (stakeholder-friendly)
- Detailed Technical Breakdown (developer-focused)
- Machine-Readable JSON (for tooling integration)

#### Example Usage

```bash
# Analyze a complete SOW
@project_estimator Analyze this SOW for e-commerce platform with auth, catalog, cart, and payments

# Estimate a specific feature
@project_estimator Estimate real-time chat feature with WebSocket and file sharing

# Mobile app estimation
@project_estimator React Native app with camera, offline storage, and push notifications

# CareLink360-specific features
@project_estimator Add bulk import for caregiver schedules with Zod validation

# Infrastructure estimation
@project_estimator AWS setup with ECS, RDS, S3, CloudFront, and CI/CD pipeline
```

#### Key Features

- **Universal**: Works with any tech stack, any project type
- **Comprehensive**: Considers compliance, security, scalability
- **Detailed**: Module-by-module breakdown with granular tasks
- **Risk-Aware**: Identifies and mitigates technical, resource, and timeline risks
- **Context-Aware**: Adapts to project-specific patterns (e.g., CareLink360 conventions)
- **Multi-Format**: Outputs for different audiences (executives, developers, tools)

#### Outputs Include

1. **Effort Estimation**

   - Story points and hours
   - Development days and weeks
   - Sprint planning estimates

2. **Resource Planning**

   - Team composition (roles & counts)
   - Skill requirements
   - FTE allocation by phase
   - Ramp-up timeline

3. **Module Breakdown**

   - Each major module with sub-tasks
   - Dependencies and critical paths
   - Priority levels (P0-P3)
   - Delivery sequence

4. **Risk Analysis**

   - Technical risks with mitigations
   - Resource risks (skills, availability)
   - Timeline risks (dependencies, blockers)
   - Compliance/security risks

5. **Complexity Scoring**
   - Overall score (1-100)
   - Per-module scores
   - Factor breakdown (technical, UI/UX, security, etc.)
   - Confidence level

#### Best Practices

- Provide detailed requirements for accurate estimates
- Mention tech stack preferences (or let agent suggest)
- Include any constraints (timeline, budget, team size)
- Specify compliance requirements (HIPAA, PCI-DSS, etc.)
- State whether it's new development, enhancement, or migration

#### Integration with CareLink360

When used within CareLink360 project, the agent:

- Follows Atomic Design patterns (atoms/molecules/organisms/templates)
- Uses Pinia store conventions
- Applies Zod validation patterns
- Considers Nuxt 3 + Vue 3 architecture
- Includes HIPAA compliance considerations
- References existing services and utilities

---

## Adding New Agents

To create a new custom agent:

1. Create a new `.agent.md` file in this directory
2. Follow the agent configuration format:

```markdown
---
name: agent_name
description: Brief description of what the agent does
tools: ['search', 'fetch', 'changes']
model: Claude Sonnet 4.5
---

# Agent Name

Your agent instructions and prompt here...
```

3. Test the agent with: `@agent_name [your query]`
4. Document it in this README

---

## Agent Development Tips

- **Be Specific**: Clear instructions = better results
- **Use Examples**: Provide example inputs and outputs
- **Define Scope**: What the agent does and doesn't do
- **Format Output**: Specify exact output format needed
- **Handle Edge Cases**: Include error handling and edge cases
- **Reference Context**: Link to relevant project files/docs

---

## Support

For issues or improvements:

1. Test the agent with different inputs
2. Check agent configuration syntax
3. Review agent instructions for clarity
4. Provide feedback with specific examples

---

**Last Updated**: February 2026  
**Maintained by**: CareLink360 Development Team

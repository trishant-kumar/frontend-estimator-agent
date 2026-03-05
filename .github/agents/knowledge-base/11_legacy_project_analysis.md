# Legacy Project Analysis

---
Last Updated: 2026-03-05
Author: Frontend Estimator Agent
Change Summary: Initial creation — legacy codebase scanning, SOW gap analysis, new vs. existing comparison heuristics
---

## 🎯 Purpose

This module is loaded **only when `mode = "legacy"`** or when a codebase is detected during Phase 0. It provides:

1. Full-scan heuristics for reading an existing codebase
2. Tech debt scoring rubric (0–100)
3. Team ramp-up time lookup tables
4. SOW ↔ Implementation gap linking rules
5. "New Project vs. Existing Project" comparison decision logic

---

## 📁 1. FULL CODEBASE SCAN HEURISTICS

### 1.1 Files to Read (Priority Order)

| Priority | File(s) | Purpose |
|----------|---------|---------|
| 1 | `package.json` | Framework, dependencies, Node version, scripts |
| 2 | `vite.config.*`, `nuxt.config.*`, `next.config.*`, `vue.config.*` | Build toolchain, plugin list |
| 3 | `tsconfig.json`, `jsconfig.json` | TypeScript strictness, path aliases |
| 4 | `.eslintrc.*`, `eslint.config.*` | Code quality enforcement |
| 5 | `src/` or `app/` directory listing | Page count, component count, feature directories |
| 6 | `src/router/` or `app/router.ts` | Total registered routes → page inventory |
| 7 | `src/store/` or `src/stores/` | State modules → feature scope |
| 8 | `src/components/` or `components/` | Component count → UI maturity |
| 9 | `vitest.config.*`, `jest.config.*`, `playwright.config.*` | Test setup presence |
| 10 | `*.test.*`, `*.spec.*` files count | Test coverage indicator |
| 11 | `src/api/` or `src/services/` | API layer maturity |
| 12 | `.github/workflows/` | CI/CD presence |

### 1.2 Framework Detection

| Detected File | Framework |
|---|---|
| `nuxt.config.*` | Nuxt 3 (Vue 3 SSR) |
| `vite.config.*` + `vue` in deps | Vue 3 SPA |
| `next.config.*` | Next.js (React SSR) |
| `vite.config.*` + `react` in deps | React 18 SPA |
| `angular.json` | Angular (out of scope — flag to user) |
| `package.json` with `svelte` | Svelte (out of scope — flag to user) |

### 1.3 Dependency Staleness Check

Compare `package.json` dependencies against known current stable versions:

| Package | Stale if | Current (2026) |
|---|---|---|
| Vue | < 3.4 | 3.5+ |
| React | < 18.2 | 18.3+ |
| Nuxt | < 3.10 | 3.14+ |
| Next.js | < 14 | 15+ |
| Vite | < 5 | 6+ |
| TypeScript | < 5.0 | 5.7+ |
| Vitest | < 1.0 | 2.x+ |
| Vuetify | < 3.5 | 3.7+ |
| Tailwind CSS | < 3.4 | 4.x+ |
| Pinia | < 2.1 | 2.3+ |
| Zod | < 3.22 | 3.24+ |

Flag any dependency more than **one major version behind** as stale.

---

## 📊 2. TECH DEBT SCORE (0–100, Lower = More Debt)

Start at **100**, deduct points for each negative signal found:

### TypeScript Health (max −25 pts)
- No TypeScript at all: −25
- TypeScript present but `strict: false`: −10
- `any` types used frequently (>10 occurrences in src/): −5
- Missing type definitions for API responses: −5

### Test Coverage (max −25 pts)
- No test files found: −20
- Test files present but <5% of source files: −10
- Test config present, no CI integration: −5
- Only E2E tests, no unit tests: −8

### Code Quality Tooling (max −15 pts)
- No ESLint config: −10
- ESLint present but no auto-fix in CI: −3
- No Prettier config: −5
- No pre-commit hooks (Husky/lint-staged): −2

### Dependency Health (max −20 pts)
- 1–2 packages stale: −5
- 3–5 packages stale: −10
- 6+ packages stale OR framework itself stale: −20
- Known security vulnerabilities in `npm audit`: −10 bonus deduction

### Architecture Signals (max −15 pts)
- Options API used in a Vue 3 project (should be Composition API): −8
- Class components in React (should be functional): −8
- No state management setup (Pinia/Vuex/Redux) for a multi-module app: −5
- No API layer abstraction (raw `fetch`/`axios` calls in components): −5
- Deprecated patterns (e.g., `mixins`, `Vue.prototype`): −5
- Non-modular monolithic store: −3

### Score Interpretation

| Score | Rating | Meaning |
|---|---|---|
| 80–100 | 🟢 Healthy | Continue in existing project is safe |
| 60–79 | 🟡 Moderate debt | Addressable during the project sprint |
| 40–59 | 🟠 High debt | Plan a refactor sprint before new features |
| 0–39 | 🔴 Severe debt | Strong case for new project |

---

## ⏱️ 3. TEAM RAMP-UP TIME TABLE

Ramp-up time = time for a new developer to become productive (not just read code).

| Codebase Size | Component Count | Ramp-Up Time | Notes |
|---|---|---|---|
| Tiny | < 20 components | 0.5–1 day | Single developer, minimal structure |
| Small | 20–50 components | 1–2 days | Clear feature folders help |
| Medium | 50–150 components | 3–5 days | Needs architecture walkthrough |
| Large | 150–300 components | 1–2 weeks | Requires dedicated onboarding session |
| Enterprise | 300+ components | 2–4 weeks | Pair programming recommended |

**Multipliers:**
- No JSDoc / inline comments: × 1.5 ramp-up
- No README or architecture docs: × 1.5 ramp-up
- TypeScript strict mode on: × 0.75 ramp-up (faster due to type inference)
- Tests present: × 0.8 ramp-up (tests serve as living documentation)

**Express ramp-up hours in the estimate** (add to legacy project's total hours, but NOT to new project total):

| Size | Base | With docs missing | With TS strict |
|---|---|---|---|
| Small | 8 hrs | 12 hrs | 6 hrs |
| Medium | 24 hrs | 36 hrs | 18 hrs |
| Large | 40 hrs | 60 hrs | 30 hrs |
| Enterprise | 80 hrs | 120 hrs | 60 hrs |

---

## 🔗 4. SOW ↔ IMPLEMENTATION GAP LINKING

### 4.1 Cross-Reference Strategy

After decomposing the SOW/requirements into modules, scan the codebase for signals of existing implementation:

**For each SOW module, check:**

1. **Route presence** — Does a matching route exist in `src/router/` or `app/` pages directory?
2. **Component presence** — Does a component directory or file named after the feature exist?
3. **Store module presence** — Does a store named after the feature exist?
4. **API service presence** — Does an API file or composable for this feature exist?
5. **Test presence** — Are there test files for this feature?

### 4.2 Completion Status Definitions

| Status | Symbol | Criteria | Hour Adjustment |
|---|---|---|---|
| **Fully Built** | ✅ | Route + Component + Store + API all present AND no obvious gaps | 0 hrs (code review/integration only: 2–4 hrs) |
| **Partial** | 🔶 | Some layers present (e.g., route exists but no store/tests) | 40–70% of base hours |
| **Stub/Skeleton** | 🔷 | Directory or file created but essentially empty | 80–90% of base hours |
| **Missing** | ❌ | Nothing found matching this feature | 100% of base hours |

### 4.3 Gap Table Output Format

```markdown
## 📊 SOW IMPLEMENTATION GAP ANALYSIS

| Module | SOW Requirement | Status | Completion Effort | Notes |
|--------|----------------|--------|-------------------|-------|
| Auth | Login / Register / Password Reset | ✅ Built | 4 hrs (review) | All layers present, needs mobile QA |
| Dashboard | KPI widgets, charts, activity feed | 🔶 Partial | 10 hrs | Chart components missing, data layer OK |
| User Mgmt | CRUD, role assignment, bulk ops | ❌ Missing | 14 hrs | No files found |
| Reports | Filter, preview, PDF export | 🔶 Partial | 8 hrs | Filter UI only, export not started |
| **TOTALS** | | | **36 hrs remaining** | **vs 52 hrs for full rebuild** |
```

### 4.4 Delta Hours Calculation

```
Legacy Project Total  = Σ (Completion Effort per module) + Ramp-up time
New Project Total     = Full estimate from Phase 2–5 (fresh build)
Hours Already Done    = New Project Total − Legacy Project Total (before overheads)
Percentage Complete   = (Hours Already Done / New Project Total) × 100
```

---

## ⚖️ 5. NEW PROJECT vs. EXISTING PROJECT COMPARISON

### 5.1 Comparison Table Format

```markdown
## ⚖️ NEW PROJECT vs. EXISTING PROJECT COMPARISON

| Dimension | 🏗️ Continue in Existing | 🆕 Start New Project |
|-----------|------------------------|----------------------|
| **Total Hours** | [delta hours] hrs | [full estimate] hrs |
| **Timeline (3 devs)** | [X] months | [Y] months |
| **Risk Score** | [inherited tech debt + migration risk] | [greenfield scope risk] |
| **Technical Debt** | Carried forward ([score]/100) | Zero at start |
| **Team Ramp-Up** | [X] hrs (existing codebase) | ~8 hrs (standard onboarding) |
| **Refactoring Tolerance** | [Low/Medium/High — from Q13] | N/A |
| **Recommended Path** | [✅ or ❌] | [✅ or ❌] |
```

### 5.2 Risk Score Calculation

**Existing Project Risk:**
- Start with tech debt score (inverted: 100 − debt_score = risk base)
- Add migration risk: each stale major dependency = +3 risk pts
- Add scope risk: % of SOW that is missing × 0.3

**New Project Risk:**
- Base greenfield risk = 15 pts (always some scope unknowns)
- Add: unclear requirements penalty from confidence score (Q12)
- Add: complex features (real-time, WebSocket, RBAC enterprise) = +5 pts each

**Risk Label:**

| Risk Pts | Label |
|---|---|
| 0–25 | 🟢 Low |
| 26–50 | 🟡 Medium |
| 51–75 | 🟠 High |
| 76–100 | 🔴 Critical |

### 5.3 Recommended Decision Logic

Apply the following decision tree (in order):

```
IF tech_debt_score < 40 AND delta_hours > 0.75 × new_project_hours:
  → 🆕 RECOMMEND NEW PROJECT
  Reasoning: "Severe technical debt combined with most features still unbuilt 
  makes starting fresh more cost-effective and reduces long-term risk."

ELSE IF delta_hours < 0.40 × new_project_hours:
  → 🏗️ RECOMMEND CONTINUE IN EXISTING
  Reasoning: "More than 60% of the scope is already implemented. 
  Continuing in the existing project avoids rebuilding working functionality."

ELSE IF tech_debt_score BETWEEN 40 AND 60 AND delta_hours BETWEEN 0.40 AND 0.75 × new_project_hours:
  → 🔀 PARTIAL MIGRATION (Strangler Fig Pattern)
  Reasoning: "Moderate debt with significant remaining scope. 
  Recommend extracting new features into a new project/micro-frontend while keeping stable legacy modules."

ELSE:
  → ⚠️ JUDGMENT CALL — Requires stakeholder input
  Reasoning: "Mixed signals. Present both options with costs and let 
  the business weigh technical risk against timeline and budget."
```

### 5.4 Refactoring Tolerance Factor (Q13 input)

| Tolerance | Impact on comparison |
|---|---|
| **Low** | Shift decision threshold toward new project (raise "continue" threshold to <30%) |
| **Medium** | Use standard thresholds as defined above |
| **High** | Shift decision threshold toward existing (lower "new project" threshold to debt_score < 30) |

---

## 📝 6. CONFIRMATION QUESTION SCRIPT (Phase 0c)

When a codebase is detected, display this summary and ask:

```markdown
### 🔍 Codebase Detected

I found an existing frontend project in the workspace:

- **Framework**: [detected framework + version]
- **Pages/Routes**: ~[count] routes
- **Components**: ~[count] components
- **Test Coverage**: [present / absent]
- **Tech Debt Score**: [score]/100 ([rating label])
- **Stale Dependencies**: [count] packages behind

---

**Before I begin estimating, I need to confirm:**

> Is this estimation for the **existing/legacy codebase** (continuing development), 
> or for a **new project** that will be built separately?

- **A) Legacy mode** — I'll link estimates to the existing implementation, show what's built vs. missing, and compare both paths.
- **B) New project** — I'll estimate the full scope as a fresh build (existing code is not relevant).
```

---

## 🔄 7. INTEGRATION WITH MAIN AGENT PHASES

| Phase | Legacy Mode Behaviour | New-Project Mode Behaviour |
|---|---|---|
| Phase 0 | Scan workspace → show codebase summary → ask A or B | Scan workspace → nothing found → confirm new project |
| Phase 1 (Questions) | Add Q13 re: refactoring tolerance | Q13 skipped |
| Phase 2 (Modules) | Run gap analysis → produce gap table → apply delta hours | Standard module breakdown |
| Phase 4 (Adjustments) | Apply adjustments to delta hours only | Standard adjustments |
| Phase 5 (Validation) | Validate delta hours (same rules as full estimate) | Standard validation |
| Phase 5.5 (Comparison) | Always run when legacy codebase was detected (even if user chose "new project") | Skip |
| Phase 6 (Output) | Add 3 extra sections: Codebase Analysis, Gap Table, Comparison | Standard output |

# 09: Project Type Detection (Legacy vs New)

**Purpose:** Comprehensive guide for identifying and estimating legacy vs greenfield projects with risk assessment.

**When to Load:** For EVERY estimation - project type affects estimates by 50-300%!

---

## 🔍 AUTO-DETECTION WORKFLOW

**ALWAYS scan codebase first to determine project type:**

```bash
# Check package.json for versions
read_file("package.json")

# Check component structure
list_dir("components/")
list_dir("src/")
file_search("**/*.vue")

# Search for legacy indicators
grep_search("Vue\.component|new Vue|export default {", isRegexp=true)
grep_search("Vuex|Options API|jQuery", isRegexp=false)

# Check TypeScript adoption
file_search("**/*.ts")
file_search("tsconfig.json")

# Check test coverage
file_search("**/*.spec.ts")
file_search("**/*.test.ts")
```

---

## 📊 DETECTION CRITERIA MATRIX

| Indicator               | Legacy Project          | New Project (Greenfield)  |
| ----------------------- | ----------------------- | ------------------------- |
| **Vue version**         | Vue 2.x                 | Vue 3.x                   |
| **API style**           | Options API             | Composition API           |
| **State management**    | Vuex or none            | Pinia                     |
| **Build tool**          | Webpack                 | Vite                      |
| **Component structure** | Mixed/inconsistent      | Atomic Design, organized  |
| **TypeScript**          | None or partial (.js)   | Full TS (.ts)             |
| **Testing coverage**    | <30% or none            | >70%                      |
| **Documentation**       | Outdated/missing        | Current, comprehensive    |
| **Code consistency**    | Inconsistent patterns   | ESLint, Prettier enforced |
| **Design system**       | None or partial         | Complete component lib    |
| **Dependencies**        | Outdated (2+ years old) | Current (updated)         |
| **Folder structure**    | Flat or unclear         | Clear hierarchy           |

---

## 🆕 NEW (GREENFIELD) PROJECT ESTIMATION

### Characteristics

- ✅ Modern stack (Vue 3, Vite, Pinia, TypeScript)
- ✅ Best practices from day 1
- ✅ No technical debt
- ✅ Clean architecture
- ✅ Fast initial development

### Estimation Approach: AGGRESSIVE MODE (default)

**Base Multipliers:**

| Factor     | Multiplier | Notes                       |
| ---------- | ---------- | --------------------------- |
| Base hours | 1.0x       | Clean start                 |
| Testing    | +15%       | Write tests from beginning  |
| Responsive | +20%       | If separate from base       |
| Bug buffer | +10%       | Minimal unknowns            |
| **TOTAL**  | **1.52x**  | Or 1.27x without responsive |

### New Project Advantages (Reduce Time)

| Advantage                 | Savings | Apply When                     |
| ------------------------- | ------- | ------------------------------ |
| **Modern tooling (Vite)** | -15%    | HMR, instant feedback          |
| **Design system ready**   | -20%    | Figma tokens, design defined   |
| **Component library**     | -25%    | Vuetify/Element Plus chosen    |
| **Clear architecture**    | -15%    | Atomic Design, folders planned |
| **TypeScript from start** | -10%    | No conversion needed           |
| **No tech debt**          | -20%    | No workarounds or hacks        |
| **Standard patterns**     | -20%    | Consistent conventions         |

### Example: New Project

```
Requirement: "User management CRUD page"

🆕 New Project Benefits:
- Vite HMR (-15%): 32 × 0.85 = 27 hr
- Vuetify ready (-25%): 27 × 0.75 = 20 hr
- Clean architecture (-15%): 20 × 0.85 = 17 hr
- TypeScript (-10%): 17 × 0.90 = 15 hr

Adjusted base: 15 hr
With multipliers: 15 × 1.52 = 23 hr
Timeline: 1 dev × 3 days
Confidence: 85%
```

---

## 🏚️ LEGACY PROJECT ESTIMATION

### Characteristics

- ⚠️ Old framework versions (Vue 2, Webpack)
- ⚠️ Technical debt accumulated
- ⚠️ Inconsistent code patterns
- ⚠️ Poor or no documentation
- ⚠️ Brittle, fragile codebase

### Estimation Approach: CONSERVATIVE MODE with RISK MULTIPLIERS

---

## 🟢 LOW RISK LEGACY (Multiply by 1.5-1.8x)

### Indicators

- [ ] Vue 2 but well-structured
- [ ] Test coverage >50%
- [ ] Clear, consistent patterns
- [ ] Active maintenance (commits weekly)
- [ ] Good documentation
- [ ] Some TypeScript adoption
- [ ] Stable in production

### Example: Low Risk Legacy

```
Requirement: "Add export feature to well-maintained user table"

Base (new project): 16 hr
Legacy (low risk): 16 × 1.6 = 26 hr

Breakdown:
- Understand existing code: 6 hr
- Implement export: 12 hr
- Add/update tests: 4 hr
- Integration testing: 4 hr

With multipliers: 26 × 1.52 = 40 hr
Timeline: 1 dev × 5 days
Confidence: 80%
```

---

## 🟡 MEDIUM RISK LEGACY (Multiply by 2.0-2.5x)

### Indicators

- [ ] Vue 2 with some structure
- [ ] Test coverage 20-50%
- [ ] Mixed patterns
- [ ] Moderate tech debt
- [ ] Documentation outdated
- [ ] Some "don't touch" areas
- [ ] Occasional production bugs

### Example: Medium Risk Legacy

```
Requirement: "Add filtering to existing product list"

Base (new project): 20 hr
Legacy (medium risk): 20 × 2.2 = 44 hr

Breakdown:
- Code archaeology: 12 hr
- Add safety tests: 8 hr
- Implement filtering: 16 hr
- Integration testing: 8 hr

With multipliers: 44 × 1.52 = 67 hr
Timeline: 1 dev × 8-9 days
Confidence: 70%
```

---

## 🔴 HIGH RISK LEGACY (Multiply by 2.5-4.0x)

### Indicators

- [ ] Vue 2 or older, jQuery mixed
- [ ] Test coverage <20% or none
- [ ] No clear patterns
- [ ] Heavy tech debt
- [ ] Poor/no documentation
- [ ] Tight coupling, brittle
- [ ] Frequent production bugs
- [ ] Bus factor = 1 (one expert)

### Example: High Risk Legacy

```
Requirement: "Add approval workflow to fragile invoicing"

Base (new project): 32 hr
Legacy (high risk): 32 × 3.2 = 102 hr

Breakdown:
- Deep code analysis: 24 hr
- Write comprehensive tests: 20 hr
- Refactor for safety: 16 hr
- Implement workflow: 24 hr
- Extensive regression: 16 hr
- Contingency for breaks: 8 hr

With multipliers: 108 × 1.52 = 164 hr
Timeline: 2 devs × 10-12 days
Confidence: 60%

⚠️ Recommendation: Refactor module first (40 hr)
```

---

## 💀 CRITICAL RISK LEGACY (Recommend Rewrite)

### Indicators

- [ ] Ancient framework (Vue 1.x, Backbone)
- [ ] Zero tests
- [ ] Spaghetti code
- [ ] No one understands code
- [ ] Breaking changes every deploy
- [ ] Security vulnerabilities
- [ ] Cannot upgrade dependencies

### Recommendation: DON'T PATCH - REWRITE

```
Example: "Add real-time notifications to ancient app"

❌ DON'T: Try to patch (200+ hr, 40% success rate)

✅ DO: Rewrite affected module
- Build isolated notification system (Vue 3): 48 hr
- Create legacy adapter: 20 hr
- Gradual migration: 16 hr
Total: 84 hr (vs 200+ hr patching)

OR: Plan full app rewrite in phases
```

---

## 🔄 HYBRID SCENARIOS

### Scenario 1: Adding Feature to Legacy

```
Requirement: "Add social login to 5-year-old auth system"

Process:
1. Analysis: 8-12 hr
2. Safety tests: 8-16 hr
3. Abstraction layer: 6-10 hr
4. Implementation: 16-24 hr
5. Integration: 8-12 hr
6. Regression: 6-10 hr
7. Security audit: 4-6 hr

Total: 70-114 hr (vs 20-30 hr greenfield)
Multiplier: 3.5x
```

### Scenario 2: Gradual Modernization

```
Requirement: "Modernize user management (Vue 2 → Vue 3)"

Phase 1: Setup (12-20 hr)
- Configure Vue 3 alongside Vue 2
- Module federation or iframe
- Bridge/adapter layer

Phase 2: Rebuild (40-60 hr)
- Rewrite in Composition API
- Modern state (Pinia)
- Full TypeScript

Phase 3: Integration (16-28 hr)
- Connect to existing APIs
- Feature parity
- Dual mode support

Phase 4: Migration (12-20 hr)
- Progressive rollout
- A/B testing
- Deprecate old

Total: 80-128 hr
```

### Scenario 3: Parallel Rewrite

```
Requirement: "Replace brittle reporting system"

Track 1: Maintain old (minimal)
Track 2: Build new (48-80 hr)
Integration: API compatibility (16-24 hr)
Cutover: Phased rollout (8-12 hr)

Total: 72-116 hr
```

---

## 🎯 PROJECT TYPE DECISION TREE

```
START: Analyze Requirements

├─ Existing code?
│  │
│  ├─ NO → 🆕 NEW PROJECT
│  │      └─ Aggressive estimates (base × 1.0-1.2)
│  │      └─ Apply new project advantages (-20-40%)
│  │      └─ Standard multipliers: 1.52x or 1.27x
│  │
│  └─ YES → 🏚️ LEGACY PROJECT
│     │
│     └─ Assess Risk:
│        │
│        ├─ 🟢 LOW (well-maintained) → × 1.5-1.8
│        ├─ 🟡 MEDIUM (typical) → × 2.0-2.5
│        ├─ 🔴 HIGH (dangerous) → × 2.5-4.0
│        └─ 💀 CRITICAL → ❌ Recommend rewrite
```

---

## 📊 COMPARISON TABLE

**Same feature, different project types:**

| Feature                   | New     | Legacy (Low) | Legacy (Med) | Legacy (High) |
| ------------------------- | ------- | ------------ | ------------ | ------------- |
| **Simple CRUD page**      | 12-18hr | 18-27hr      | 24-36hr      | 36-54hr       |
| **Complex form (wizard)** | 28-36hr | 42-54hr      | 56-72hr      | 84-108hr      |
| **Dashboard + charts**    | 32-40hr | 48-60hr      | 64-80hr      | 96-120hr      |
| **Real-time feature**     | 40-56hr | 60-84hr      | 80-112hr     | 120-168hr     |
| **Data table + filters**  | 20-28hr | 30-42hr      | 40-56hr      | 60-84hr       |
| **Authentication flow**   | 24-32hr | 36-48hr      | 48-64hr      | 72-96hr       |

---

## 🎓 COMPLETE EXAMPLES

### Example 1: New Greenfield ✅

```
Requirement: "Complete user management from scratch"

✅ New Project:
- Vue 3 + Vite + Pinia + TypeScript
- Vuetify component library
- Clear Atomic Design structure
- Testing (Vitest + Playwright)

Feature breakdown:
- User CRUD: 20 hr
- Role management: 12 hr
- Permissions (RBAC): 16 hr
- Search + filters: 8 hr
- Export CSV: 6 hr
Base: 62 hr

New project benefits:
- Vite (-15%): 53 hr
- Vuetify (-25%): 40 hr
- Architecture (-15%): 34 hr

Multipliers: 34 × 1.52 = 52 hr
Timeline: 2 devs × 3-4 weeks
Confidence: 85%
```

### Example 2: Medium Legacy 🟡

```
Requirement: "Add approval workflow to document form"

🟡 Medium Risk Legacy:
- Vue 2.6 Options API
- Mixed Vuex + component state
- Test coverage: 35%
- 800-line form (needs refactor)

Base (new): 32 hr
Legacy multiplier: 32 × 2.2 = 70 hr

Breakdown:
- Understand form: 12 hr
- Write tests: 8 hr
- Refactor: 12 hr
- Implement: 24 hr
- Integration: 8 hr
- Regression: 6 hr

Multipliers: 70 × 1.52 = 106 hr
Add 20% buffer: 127 hr

Timeline: 2 devs × 6-7 weeks
Confidence: 65%
```

### Example 3: High Risk Legacy 🔴

```
Requirement: "Add Stripe payment to 6-year-old checkout"

🔴 High Risk:
- Vue 2.5 + jQuery
- Test coverage <10%
- 2000+ line checkout file
- Frequent bugs

Base (new): 32 hr
Multiplier: 32 × 3.5 = 112 hr

Phases:
1. Archaeology: 24 hr
2. Safety tests: 20 hr
3. Refactoring: 24 hr
4. Stripe integration: 32 hr
5. Validation: 16 hr
6. Contingency: 16 hr
Total: 132 hr

Multipliers: 132 × 1.52 = 200 hr
Timeline: 2 devs × 12-14 weeks
Confidence: 55%

⚠️ BETTER: Rebuild checkout (80hr) + Stripe (32hr) = 112hr
```

### Example 4: Critical - Rewrite 💀

```
Requirement: "Real-time collaboration in ancient doc system"

💀 Critical Risk:
- Backbone.js + jQuery
- Zero tests
- No one understands it

❌ Patching: 300+ hr, 30% success
✅ Rewrite module: 120 hr, 85% success

Build new editor: 80 hr
Legacy adapter: 24 hr
Deployment: 16 hr

Total: 120 × 1.52 = 182 hr
Timeline: 3 devs × 7-8 weeks
Confidence: 80%

RECOMMENDATION: Rewrite, don't patch
```

---

## ✅ MANDATORY CHECKS

### Project Type Detection

- [ ] Codebase scanned?
- [ ] Vue version identified?
- [ ] Build tool identified?
- [ ] Test coverage estimated?
- [ ] Documentation quality assessed?

### Risk Assessment (if legacy)

- [ ] Risk level determined? (Low/Med/High/Critical)
- [ ] Breaking change risk?
- [ ] Tech debt quantified?
- [ ] Expert knowledge required?

### Estimation Adjustment

- [ ] Base estimate (as if new)
- [ ] Project type multiplier applied
- [ ] Legacy-specific time added
- [ ] Standard multipliers applied
- [ ] Contingency buffer added

---

**KEY TAKEAWAYS:**

1. Always identify project type first (50-200% impact)
2. New projects: Use aggressive estimates
3. Legacy (low): × 1.5-1.8
4. Legacy (medium): × 2.0-2.5
5. Legacy (high): × 2.5-4.0 or rewrite
6. When in doubt, add 50% buffer for legacy unknowns
7. Document risk level clearly to stakeholder

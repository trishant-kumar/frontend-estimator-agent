# Module 01: Estimation Methods & Formulas

**Purpose:** Detailed estimation methodologies with mathematical formulas and practical application guides.

---

## 📐 PERT Three-Point Estimation

**⚠️ NOTE: This method is NOT currently used by the agent. The agent uses Direct Estimation with pattern-based hours. This section is kept for reference for teams who prefer PERT methodology.**

### Formula

```
Expected Hours (E) = (O + 4M + P) / 6

Where:
O = Optimistic (best case scenario)
M = Most Likely (realistic middle estimate)
P = Pessimistic (worst case with challenges)
```

### Standard Deviation (Uncertainty)

```
σ = (P - O) / 6

68% confident: E ± σ
95% confident: E ± 2σ
```

### When to Use

- ✅ Complex features with unknowns
- ✅ Tasks >20 hours
- ✅ First-time implementation
- ✅ High-risk technical work
- ❌ Simple CRUD operations
- ❌ Well-known patterns

---

## 🎯 Direct Estimation

### When to Use

Simple, well-understood tasks where experience gives clear time estimate.

**Apply to:**

- Standard CRUD forms (4-8 hr)
- Basic pages (3-6 hr)
- Simple components (2-4 hr)
- Known patterns

**Formula:**

```
Base Estimate × Complexity Multiplier

Complexity:
Simple: 1.0x
Medium: 1.5x
Complex: 2.5x
```

---

## 📊 Story Points to Hours Conversion

**⚠️ NOTE: This method is NOT currently used by the agent. The agent estimates directly in hours, not story points. This section is kept for reference for teams who use story points and need conversion guidance.**

### Fibonacci Sequence

```
1 point = 4-6 hours
2 points = 8-12 hours
3 points = 12-18 hours
5 points = 20-30 hours
8 points = 32-48 hours
13 points = 52-78 hours (split recommended)
```

### Team Velocity

```
If team completes 40 points/sprint (2 weeks):
1 point ≈ 16 hours / 40 = 0.4 hours of work

Calculate: Points × (Total Hours / Historical Sprint Completion)
```

---

## 🔺 Cone of Uncertainty

### Estimation Variance by Project Phase

| Phase             | Variance | Apply Factor  |
| ----------------- | -------- | ------------- |
| Initial Concept   | ±60%     | 0.4x - 1.6x   |
| Requirements      | ±40%     | 0.6x - 1.4x   |
| Design Complete   | ±25%     | 0.75x - 1.25x |
| Development Start | ±15%     | 0.85x - 1.15x |
| Mid-Development   | ±10%     | 0.9x - 1.1x   |
| Nearly Complete   | ±5%      | 0.95x - 1.05x |

**Usage:**

```
Base: 100 hours
Phase: Design Complete (±25%)
Range: 75-125 hours
```

---

## ✅ BASE HOURS VALIDATION CHECKLIST

**CRITICAL: Before finalizing any estimate, verify you're not double-counting these common overlaps:**

### 1. Testing & Quality Assurance

**Question:** _"Are test hours already included in base patterns?"_

- ✅ **CORRECT:** Base = feature development only (no tests), +20% Professional Dev = unit + E2E + edge cases
- ❌ **WRONG:** Base = feature + tests (70% coverage), +20% Professional Dev = more tests (double-counted)

**Validation:**

```typescript
// Base pattern for CRUD module (40 hr):
const baseIncludes = [
  'List view with table',
  'Create/Edit forms',
  'Delete confirmation',
  'API integration (fetch/submit)',
  'Loading states',
  'Basic error messages',
];

const baseExcludes = [
  '❌ Unit tests (Vitest)',
  '❌ E2E tests (Playwright)',
  '❌ Edge case handling',
  '❌ Production hardening',
];

// Professional Dev overhead (+20% = 8 hr) adds:
// - Unit tests: 4 hr
// - E2E critical flows: 2 hr
// - Edge cases: 2 hr
// = 8 hr extra (NOT in base)
```

**Red Flag:** If your base pattern description says "includes unit tests" or "70% test coverage", you're double-counting. Remove from base OR remove Professional Dev overhead.

---

### 2. RBAC & Permissions

**Question:** _"Does base already include permission checks?"_

- ✅ **CORRECT:** Base = admin UI for role management (12 hr), +60 hr RBAC overhead = system-wide enforcement
- ❌ **WRONG:** Base = all features with permission checks, +60 hr RBAC overhead = more permission logic (double-counted)

**Validation:**

```typescript
// Base pattern for Dashboard (30 hr):
const baseIncludes = [
  'Dashboard layout',
  'Widgets (stats, charts)',
  'Filters & date pickers',
  'API integration',
  'Responsive design',
];

const baseExcludes = [
  '❌ Permission composables (usePermissions)',
  '❌ Route guards (middleware)',
  '❌ Conditional UI (v-if="hasPermission")',
  '❌ API-level permission validation',
];

// RBAC overhead (+60 hr for 50+ pages) adds:
// - Permission composables: 15 hr
// - Route guards: 12 hr
// - UI conditional rendering: 20 hr
// - Integration across modules: 10 hr
// - Testing: 3 hr
// = 60 hr extra (NOT in base)
```

**Exception:** If base includes role admin UI (e.g., "User Management" module with role CRUD), that's 10-15 hr in base. RBAC overhead then adds system-wide enforcement (separate work).

**Red Flag:** If base says "permission-aware dashboard" or "role-based access", you're likely double-counting. Split it: base = UI only, RBAC overhead = permissions.

---

### 3. Real-Time Features

**Question:** _"Does base assume polling or WebSocket?"_

- ✅ **CORRECT:** Base = polling/manual refresh (no real-time), +40 hr overhead = WebSocket notification center
- ❌ **WRONG:** Base = live updates included, +40 hr overhead = more real-time features (double-counted)

**Validation:**

```typescript
// Base pattern for Notifications (0 hr in shared module):
const baseAssumption = 'User manually refreshes page to see new data';

const baseExcludes = [
  '❌ WebSocket connection setup',
  '❌ Notification center UI',
  '❌ Real-time event listeners',
  '❌ Toast notifications on events',
  '❌ Offline queue handling',
];

// Real-time overhead (+40 hr) adds:
// - WebSocket setup (socket.io): 8 hr
// - Notification center UI: 10 hr
// - Real-time data updates: 8 hr
// - Event routing logic: 6 hr
// - Offline handling: 4 hr
// - Testing: 4 hr
// = 40 hr extra (NOT in base)
```

**Red Flag:** If base pattern for "Messages" or "Notifications" says "real-time updates" or "instant notifications", check if Real-time overhead is also charged. If yes, you're double-counting.

---

### 4. Third-Party Integrations

**Question:** _"What's in base: just the UI trigger, or full integration logic?"_

- ✅ **CORRECT:** Base = trigger button + display results (5-10 hr), Integration overhead = API setup + error handling + mapping (15-40 hr)
- ❌ **WRONG:** Base = full integration with error handling (30 hr), Integration overhead = same work (double-counted)

**Validation:**

```typescript
// Example: GPS Location Integration

// Base pattern hours (5-10 hr):
const baseIncludes = [
  'Button to trigger location',
  'Display lat/lng on UI',
  'Basic "Location unavailable" message',
];

const baseExcludes = [
  '❌ Geolocation API setup & permissions',
  '❌ Error handling (denied, timeout, unsupported)',
  '❌ Geofencing logic',
  '❌ Map library integration (Google Maps, Mapbox)',
  '❌ Retry logic for failed requests',
];

// Integration overhead (+15 hr) adds:
// - Geolocation API: 4 hr
// - Error handling: 3 hr
// - Geofencing: 5 hr
// - Map integration: 3 hr
// = 15 hr extra (NOT in base)
```

**Rule of Thumb:**

- **Base:** UI to trigger integration (button, form) + display results = 5-15 hr
- **Overhead:** External API setup, auth, error handling, retries, data transformation = 15-80 hr
- **Total:** 20-95 hr (split between base and overhead)

**Red Flag:** If base pattern says "GPS integration with geofencing" (complex logic), but also charging Integration overhead, you're double-counting. Split properly.

---

### 5. Technology Stack Assumptions

**Question:** _"Are base hours already optimized for Vuetify/Tailwind?"_

- ✅ **CORRECT:** Base = lower hours (e.g., Form = 8 hr with Vuetify), no additional reduction
- ❌ **WRONG:** Base = vanilla JS hours (e.g., Form = 16 hr), then apply -50% reduction for Vuetify (should be baked in)

**Validation:**

```typescript
// Base Patterns (Optimized for modern frameworks):
const patterns = {
  'Authentication (Login + Forgot Password + Reset)': '12-18 hr',
  'CRUD Module (List + Create + Edit + Delete)': '40-60 hr',
  'Dashboard (Stats + Charts + Filters)': '30-45 hr',
  'Complex Form (10+ fields, nested)': '15-25 hr',
};

// ✅ Correct: Use these hours directly (Vuetify/Tailwind speed already factored in)
// ❌ Wrong: Start with higher baseline then apply reduction (double-dipping)
```

**Red Flag:** Base hours already assume modern frameworks. Don't apply additional tech stack reductions.

---

### 📋 QUICK VALIDATION CHECKLIST

**Before submitting estimate, verify:**

- [ ] **Testing:** Base patterns do NOT mention "includes tests" — if they do, remove +20% Professional Dev or remove testing from base
- [ ] **RBAC:** Base patterns do NOT mention "permission checks" (except role admin UI) — if they do, remove +20-80 hr RBAC overhead or remove from base
- [ ] **Real-time:** Base patterns assume polling/manual refresh — if they mention "live updates", remove +5-40 hr Real-time overhead or remove from base
- [ ] **Integrations:** Base includes only UI trigger (5-10 hr) — if base includes full API logic, remove Integration overhead or reduce base
- [ ] **Tech Stack:** Using current base hours (optimized for modern frameworks) — don't apply additional tech stack reductions
- [ ] **Reusability:** Applied 25% reduction only ONCE (across similar modules) — not applied per module AND globally
- [ ] **Buffer:** Applied +10-25% buffer only ONCE at the end — not applied to base AND final total

**Correct Example:**
```
Base: 1,000 hr (UI only, no tests/RBAC) → Reusability: 0.75 = 750 hr
→ × Testing: 1.20 = 900 hr → +RBAC: 60 hr → +Real-time: 40 hr
→ +Integrations: 50 hr → × Buffer: 1.10 = 1,155 hr ✓
```

**Wrong Example (Double-Counting):**
```
Base: 1,000 hr (includes tests, RBAC) → × Testing: 1.20 ❌
→ +RBAC: 60 hr ❌ → Final: inflated by ~300 hr
```

---

## ⚠️ CRITICAL: RESPONSIVE DESIGN & API INTEGRATION

### Responsive Design Philosophy

**❌ WRONG APPROACH:**

```
Base hours: 100 (desktop only)
+ Responsive multiplier: +20% = 120 hrs
```

**✅ CORRECT APPROACH:**

```
Base hours: 100 (responsive INCLUDED - multi-device is standard)
Desktop-only reduction: × 0.85 = 85 hrs (less work needed)
```

**Why This Changed:**

Modern frontend development (2024+) uses mobile-first CSS from day one:

- Tailwind CSS: `md:`, `lg:`, `xl:` breakpoints are standard
- Vuetify: `<v-col cols="12" md="6">` is default practice
- Flexbox/Grid: Responsive by nature
- Component libraries: All components responsive by default

**Decision Rule:**

- Multi-device (desktop + tablet + mobile): × 1.0 (baseline, no adjustment)
- Desktop-only: × 0.85 (-15% reduction, less work)

---

### API Integration Philosophy

**❌ WRONG APPROACH:**

```
Base hours: 50 (UI only)
+ API integration: +5-15% = 58 hrs
```

**✅ CORRECT APPROACH:**

```
Base hours: 50 (API integration INCLUDED - it's professional practice)
API setup overhead (if mocks needed):
  - APIs ready: +0 hrs
  - Parallel development: +8 hrs (mock setup)
  - Frontend first: +16 hrs (comprehensive mocks + integration)
```

**What's INCLUDED in Base Hours:**

- Fetching data from API endpoints
- Displaying data in UI
- Loading states (spinners, skeletons)
- Error handling and messages
- Success states and feedback
- Empty states (no data found)

**What's SEPARATE (API Setup Overhead):**

- Creating mock API servers (json-server, MSW)
- Mock data generation
- Later integration work (if mocks used first)

**Decision Rule:**

- API integration work: ALWAYS included in base hours
- Mock setup overhead: Add 8-16 hrs ONLY if APIs not ready

---

## 🎲 Monte Carlo Simulation (Advanced)

### When Requirements Have Range

**Example:** Feature could be 20-40 hours

**Process:**

1. Run 1000 simulations
2. Randomly pick value from range each run
3. Sum all features
4. Get probability distribution

**Quick Manual Version:**

```
Best Case (10%): Sum all minimums
Likely (50%): Sum all midpoints
Worst Case (90%): Sum all maximums
```

---

## 🌐 BROWSER SUPPORT REQUIREMENTS

**Browser support significantly impacts development and testing time:**

### Browser Support Levels

| Browser Support        | Add Time | Notes                                      |
| ---------------------- | -------- | ------------------------------------------ |
| **Modern only**        | 0%       | Chrome 90+, Firefox 88+, Safari 14+        |
| **Safari quirks**      | +10%     | Date pickers, flex bugs, iOS viewport      |
| **Mobile Safari**      | +15%     | Touch events, 100vh issues, zoom bugs      |
| **IE11 (deprecated)**  | +40-60%  | Polyfills, no modern CSS, refactoring      |
| **Cross-browser E2E**  | +20%     | Test on 3+ browsers (Chrome/FF/Safari)     |
| **Responsive testing** | +15%     | Test on 5+ devices (mobile/tablet/desktop) |
| **Edge cases**         | +10-15%  | Older Android, Samsung Internet            |

### Modern Browser Baseline

**Default assumption (0% overhead):**

- Chrome 90+ (2021+)
- Firefox 88+ (2021+)
- Safari 14+ (2020+)
- Edge 90+ (Chromium-based)

**Features available:**

- ES6+ (async/await, modules, classes)
- Modern CSS (Grid, Flexbox, CSS Variables)
- Native form validation
- Fetch API, Promises
- WebSockets, Service Workers

### Legacy Browser Overhead

**IE11 Support (+40-60%, typically use +50%):**

```
Required changes:
✅ Babel transpilation setup (+4 hr)
✅ Polyfills (Promise, fetch, Array methods) (+6 hr)
✅ No CSS Grid, limited Flexbox (+10-20% CSS time)
✅ Manual form validation (+8 hr)
✅ Testing on IE11 (+15% QA time)
✅ Alternative for modern APIs (+16 hr)

Example:
Modern browser: 40 hr
IE11 support: 40 × 1.50 = 60 hr (+50%, realistic for production)

⚠️ Recommendation: Strongly advise against IE11 support
- Microsoft ended support January 2022
- No security updates
- Modern frameworks don't support IE11
- Development time increases 50%
- Maintenance cost increases 40%
```

**Safari Quirks (+10%):**

```
Common issues:
✅ Date input fallback (Safari < 14.1) (+2-4 hr)
✅ Flexbox bugs (min-height, shrinking) (+3-6 hr)
✅ Smooth scrolling polyfill (+2 hr)
✅ CSS backdrop-filter alternative (+2-4 hr)
✅ Additional Safari testing (+3-6 hr)

Example:
Chrome-only: 40 hr
Safari support: 40 × 1.10 = 44 hr
```

**Mobile Safari (+15%):**

```
Mobile-specific issues:
✅ 100vh viewport bug workaround (+3-6 hr)
✅ Touch event handling (+4-8 hr)
✅ Fixed position keyboard issues (+2-4 hr)
✅ Zoom/scale prevention (+2 hr)
✅ Mobile Safari testing (+4-8 hr)

Example:
Desktop-only: 40 hr
Mobile Safari: 40 × 1.15 = 46 hr
```

### Cross-Browser Testing Matrix

| Testing Scope     | Add Time  | Browsers/Devices Tested                 |
| ----------------- | --------- | --------------------------------------- | --- |
| **None**          | 0 hr      | Dev browser only (Chrome)               |
| **Basic**         | +8-12 hr  | Chrome + Firefox                        |
| **Standard**      | +16-24 hr | Chrome + Firefox + Safari               |     |
| **Comprehensive** | +24-40 hr | 3 browsers × 3 devices (9 combinations) |
| **Enterprise**    | +40-60 hr | 5 browsers × 5 devices + accessibility  |

### Detection Workflow

```bash
# Ask clarifying questions:
"What browsers must be supported?"
"Default: Modern browsers only (Chrome 90+, Firefox 88+, Safari 14+)"

"Is IE11 support required?"
"Warning: IE11 adds 40-60% to estimate and is not recommended"

"Must it work on mobile Safari/iOS?"
"Mobile Safari adds 15% for viewport/touch issues"

"What testing coverage is expected?"
"Basic (2 browsers), Standard (3 browsers), or Comprehensive (3 browsers × 3 devices)?"
```

### Example: Browser Support Impact

```
Requirement: "Dashboard must work on IE11, Chrome, Firefox, Safari, and mobile devices"

🌐 Browser Analysis:
❌ IE11 required (+50% - major impact)
✅ Safari quirks (+10%)
✅ Mobile Safari (+15%)
✅ Cross-browser testing (+20%)
✅ Responsive testing (+15%)

Base dashboard: 40 hr
IE11 multiplier: 40 × 1.50 = 60 hr
Other browsers: 60 × 1.10 × 1.15 = 77 hr
Testing: 77 × 1.20 × 1.15 = 106 hr
Standard multipliers: 106 × 1.52 = 161 hr

Without IE11: 40 × 1.10 × 1.15 × 1.20 × 1.15 × 1.52 = 91 hr

IE11 Impact: +70 hours (77% increase!)

⚠️ Strong Recommendation: Drop IE11, save 70 hours
```

### Browser Support Decision Matrix

| Industry         | Typical Support                | Notes                      |
| ---------------- | ------------------------------ | -------------------------- |
| **SaaS/Startup** | Modern only                    | Move fast, latest features |
| **E-commerce**   | Modern + Mobile Safari         | Mobile traffic critical    |
| **Enterprise**   | Modern + Safari                | Corporate Macs common      |
| **Government**   | Modern + IE11 (unfortunately)  | Legacy systems, high cost  |
| **Healthcare**   | Modern + comprehensive testing | Compliance, accessibility  |
| **Education**    | Modern + older browsers        | Varied device quality      |

---

## 🧮 Bottom-Up vs Top-Down

### Bottom-Up Estimation (Detailed)

**Process:**

1. Break feature into smallest tasks
2. Estimate each task
3. Sum all tasks
4. Add integration buffer (10-15%)

**Accuracy:** High (±10-15%)
**Time Investment:** 2-4 hours per feature
**Use When:** Detailed SOW needed

**Example:**

```
User Login Feature:
- Design login form: 3 hr
- Implement email input: 1 hr
- Implement password input with toggle: 2 hr
- Form validation: 3 hr
- API integration: 4 hr
- Error handling UI: 3 hr
- Loading states: 2 hr
- Remember me functionality: 2 hr
- Unit tests: 4 hr
- E2E tests: 4 hr
Subtotal: 28 hr
+ Integration buffer (15%): 4 hr
Total: 32 hours
```

### Top-Down Estimation (Rapid)

**Process:**

1. Compare to known similar features
2. Apply multiplier for differences
3. Provide range

**Accuracy:** Medium (±30-40%)
**Time Investment:** 5-15 minutes
**Use When:** Quick ballpark needed

**Example:**

```
User Login Feature:
- Similar to last project: 24 hr
- This project more complex: 1.3x multiplier
- Estimate: 31 hours (24-40 hour range)
```

---

## 🔢 Complexity Scoring System

### Feature Complexity Matrix

| Factor               | Simple (1x)    | Medium (1.5x)       | Complex (2.5x)         |
| -------------------- | -------------- | ------------------- | ---------------------- |
| **Data Model**       | Single entity  | 2-3 entities        | 4+ entities, relations |
| **Business Logic**   | None/trivial   | Moderate validation | Complex calculations   |
| **UI Components**    | 1-3 components | 4-7 components      | 8+ components          |
| **API Calls**        | 1 endpoint     | 2-3 endpoints       | 4+ endpoints           |
| **State Management** | Local only     | Module store        | Cross-module state     |
| **Third-party**      | None           | 1 library           | Multiple integrations  |

**Calculate Multiplier:**

```
Average all factors = Final Multiplier

Example:
Data: Medium (1.5x)
Logic: Simple (1.0x)
UI: Medium (1.5x)
API: Complex (2.5x)
State: Medium (1.5x)
Third-party: Simple (1.0x)

Multiplier = (1.5 + 1.0 + 1.5 + 2.5 + 1.5 + 1.0) / 6 = 1.5x

Base pattern: 24 hr
24 × 1.5 = 36 hours
```

---

## 📈 Experience-Based Adjustments

### Developer Skill Level Multipliers

| Level                     | Multiplier | When to Apply             |
| ------------------------- | ---------- | ------------------------- |
| Senior (5+ yrs framework) | 0.8x       | Has done this 10+ times   |
| Mid (2-4 yrs framework)   | 1.0x       | Standard baseline         |
| Junior (0-1 yr framework) | 1.5x       | Learning on the job       |
| Mixed Team Average        | 1.1x       | 2 senior, 3 mid, 1 junior |

**Team Composition Formula:**

```
(Senior × 0.8 + Mid × 1.0 + Junior × 1.5) / Total Devs

Example: 1 senior, 2 mid, 1 junior
(1×0.8 + 2×1.0 + 1×1.5) / 4 = 1.075x ≈ 1.1x
```

---

## 🧪 Professional Development Overhead

### Combined Overhead: **+20%** (Testing + Edge Cases)

**Why 20%:** Modern tools (Vitest, Playwright, TypeScript, Zod) make testing faster and catch errors early, reducing overhead compared to traditional approaches.

**What's Included in 20%:**

1. **Unit Tests (10%)**

   - Vitest setup once: 2 hr
   - Component tests: 70% coverage
   - Store/composable tests: 3 hr

2. **E2E Tests (5%)**

   - Playwright setup once: 2 hr
   - Critical paths: 3-5 flows
   - Login, CRUD, checkout tests

3. **Edge Cases & Defensive Coding (5%)**
   - Network errors (offline, timeout)
   - Race conditions (double-submit, debounce)
   - Stale data detection (optimistic locking)
   - Async validation (email exists, unique checks)
   - Empty/loading/error states
   - Permission changes mid-session
   - Memory leak prevention (cleanup on unmount)

**Why This Is Realistic:**

- Modern testing tools are FAST (Vitest runs in milliseconds)
- TypeScript catches errors at compile-time (less runtime bugs)
- Zod schemas prevent validation bugs (declarative validation)
- Component libraries are pre-tested (Vuetify is battle-tested)
- Senior developers write tests alongside code (not double work)
- Edge cases are MINIMAL with type safety

**Formula:**

```typescript
final = base × 1.20 × buffer

// Example:
base = 100 hr
× 1.20 (professional dev) = 120 hr
× 1.10 (buffer) = 132 hr
```

**Breakdown Example (100 hr base project):**

```

Feature development: 100 hr
Unit tests (10%): 10 hr
E2E tests (5%): 5 hr
Edge cases (15%): 15 hr
────────────────
Total: 130 hr (30% overhead)

```

---

## 🔄 Responsive Design

**⚠️ CRITICAL UPDATE:** Responsive design is ALWAYS INCLUDED in base hours!

### Modern Reality

With Tailwind CSS, Vuetify, and mobile-first frameworks, responsive development is the DEFAULT practice:

- Breakpoint utilities built-in: `md:`, `lg:`, `sm:`
- Grid systems responsive by default: `flex`, `grid`
- Component libraries handle responsiveness automatically
- We don't code "desktop first, then add mobile" anymore

### Only One Adjustment

| Support Level    | Adjustment | Reason                                         |
| ---------------- | ---------- | ---------------------------------------------- |
| **Responsive**   | 1.0x       | Standard practice (mobile/tablet/desktop)      |
| **Desktop Only** | -15%       | RARE case where we can skip mobile breakpoints |

**Example:**

```

Base Dev (responsive): 30 hr
Desktop-only reduction: 30 × 0.85 = 25.5 hr

Savings: 4.5 hours (because we skip mobile testing/QA)

```

**Important:** Desktop-only is uncommon. Most clients expect mobile support by default.

---

## 🎨 Design Readiness Impact

### Design State Multipliers

| Design State            | Multiplier | Why                   |
| ----------------------- | ---------- | --------------------- |
| **Pixel-Perfect Figma** | 1.0x       | Clear requirements    |
| **Wireframes Only**     | 1.3x       | Need design decisions |
| **Rough Sketches**      | 1.6x       | Major unknowns        |
| **Verbal Description**  | 2.0x       | Complete guesswork    |

### Missing Design Elements

| Missing          | Add Time           |
| ---------------- | ------------------ |
| Color scheme     | +2 hr per feature  |
| Typography       | +1 hr per feature  |
| Spacing system   | +3 hr initial      |
| Component states | +20% per component |
| Icons/assets     | +4 hr per feature  |

---

## 📊 Confidence Level Framework

### Setting Confidence

| Confidence | Criteria Met                            | Risk Profile |
| ---------- | --------------------------------------- | ------------ |
| **90-95%** | All 5 criteria + similar past project   | Very Low     |
| **80-89%** | 4 of 5 criteria + experienced team      | Low          |
| **70-79%** | 3 of 5 criteria + documented APIs       | Medium       |
| **60-69%** | 2 of 5 criteria + willing stakeholders  | High         |
| **<60%**   | <2 criteria → recommend discovery phase | Very High    |

**5 Key Criteria:**

1. ✅ Complete designs (Figma/Adobe XD)
2. ✅ API documentation ready
3. ✅ Clear requirements (user stories)
4. ✅ Team has framework experience
5. ✅ Stable scope (no expected changes)

### Confidence-Based Buffers

**What Buffer Covers:** Rework and refinement activities including code review feedback, QA bugs, and stakeholder tweaks.

**What Causes Buffer Need:**

1. **Code Review Feedback (30%)** - Architectural improvements, better patterns
2. **QA-Found Bugs (30%)** - Edge cases, browser quirks
3. **Stakeholder Tweaks (20%)** - Design changes, UX improvements
4. **API Changes (10%)** - Backend changes response format
5. **Unknown Unknowns (10%)** - Things you couldn't predict

**Buffer Formula:**

```typescript
// High confidence (90%) = Less rework expected
base × 1.05 // +5% buffer

// Medium confidence (75%) = Moderate rework
base × 1.10 // +10% buffer ← MOST COMMON

// Low confidence (60%) = Significant unknowns
base × 1.20 // +20% buffer

// Very Low (<60%) = Recommend discovery phase first
base × 1.30+ // +30%+ buffer (or reject estimate)
```

**Confidence Score Calculator:**

```typescript
let score = 50; // Start at baseline

// Add points for certainty:
if (completeDesigns) score += 10;
if (designSystem) score += 8;
if (apiDocsReady) score += 10;
if (clearRequirements) score += 12;
if (similarPastProject) score += 15;
if (experiencedTeam) score += 10;

// Subtract points for risk:
if (complexIntegrations) score -= 10;
if (newTechnology) score -= 15;
if (unclearRequirements) score -= 20;
if (apisNotReady) score -= 12;
if (rbacComplex) score -= 10;
if (realTimeRequired) score -= 10;

// Map to confidence %
const confidence = Math.min(95, Math.max(55, score));

// Map to buffer
if (confidence >= 85) return 1.05; // +5%
if (confidence >= 70) return 1.1; // +10% ← Most common
if (confidence >= 55) return 1.2; // +20%
return 1.3; // +30%+ or recommend discovery
```

**Example:**

```
Base: 100 hr
After professional dev (×1.20): 120 hr
After buffer (×1.10 at 75% confidence): 132 hr

Breakdown of 10% buffer (12 hours):
- Code review rework: 4 hr
- QA bugs: 4 hr
- Stakeholder tweaks: 3 hr
- API changes: 2 hr
- Unknowns: 2 hr
```

---

## 🧩 Integration Complexity

**⚠️ API Integration INCLUDED:** Fetching data, displaying it, loading states, and error handling are standard professional practice and INCLUDED in all base hours.

### Only Add Hours For:

**1. Mock Data Setup (No Real API Yet):**

```
Mock data files: 4-8 hr
Swap mock to real later: 2-4 hr
```

**2. Extreme API Instability (Beta/Pre-Release):**

Only if API is actively changing during development:

```
Buffer: +10-15% for rework
Example: 100 hr base → 110-115 hr
```

**3. Complex Third-Party Services:**

OAuth, Stripe, Twilio, etc. with custom flows:

```
OAuth flow setup: +8-12 hr
Payment integration: +12-16 hr
SMS/notification UI: +6-8 hr
```

**Do NOT add generic "API integration" multipliers. It's already included!**

### State Management Overhead

| Pattern                   | Overhead | When                |
| ------------------------- | -------- | ------------------- |
| Props only (local state)  | +0%      | Simple components   |
| Composables (Vue) / Hooks | +10%     | Shared logic        |
| Pinia / Redux module      | +15%     | Feature state       |
| Global store with sync    | +25%     | Cross-feature state |
| Real-time (WebSocket)     | +40%     | Live updates        |

---

## 🔧 Technical Debt Factor

### Legacy Code Multipliers

| Codebase State              | Multiplier |
| --------------------------- | ---------- |
| Greenfield (new project)    | 1.0x       |
| Modern codebase (<1 yr old) | 1.1x       |
| Maintained legacy (2-3 yrs) | 1.3x       |
| Unmaintained (4+ yrs)       | 1.6x       |
| Mixed frameworks/versions   | 2.0x       |

### Refactoring Overhead

Include if modernizing during feature work:

- Type conversion (JS → TS): +25%
- Vue 2 → Vue 3 migration: +40%
- Options API → Composition API: +20%
- Class components → Functional: +30%

---

## 📅 Timeline Calculation from Hours

### Convert Hours to Calendar Time

**Formula:**

```
Calendar Weeks = Total Hours / (Devs × Hours/Week × Efficiency)

Standard:
- Hours/Week = 40 (full-time)
- Efficiency = 0.75 (meetings, code review, blockers)

Example:
Total: 240 hours
Devs: 2
Weeks = 240 / (2 × 40 × 0.75) = 240 / 60 = 4 weeks
```

### Efficiency Factors by Team Size

| Team Size | Efficiency | Why                    |
| --------- | ---------- | ---------------------- |
| 1 dev     | 0.85       | Few meetings           |
| 2-3 devs  | 0.75       | Code reviews, sync     |
| 4-6 devs  | 0.65       | More coordination      |
| 7+ devs   | 0.55       | Communication overhead |

---

## 🔐 RBAC (Role-Based Access Control) Estimation

**⚠️ CRITICAL:** Basic permission checks are INCLUDED, but complex RBAC is 50-80 hidden hours!

### RBAC Complexity Levels

**Level 0: Simple Auth Checks (INCLUDED)**

```typescript
// Just authenticated vs not
<VBtn v-if="isAuthenticated">Edit</VBtn>
<VBtn v-if="user.role === 'admin'">Delete</VBtn>

// NO EXTRA ESTIMATION NEEDED
```

**Level 1: Basic RBAC (+20 hours)**

```typescript
// 2-3 roles, boolean checks
interface User {
  role: 'admin' | 'user';
}

const canEdit = user.role === 'admin';

Breakdown:
- Role management UI: 6 hr
- usePermissions composable: 4 hr
- Route guards: 4 hr
- UI conditionals (15 components): 4 hr
- Testing: 2 hr
────────────────
TOTAL: 20 hr
```

**Level 2: Advanced RBAC (+60 hours)**

```typescript
// 5+ roles, granular permissions
interface Permission {
  resource: string; // 'users', 'invoices'
  action: string;   // 'create', 'read', 'update', 'delete'
}

const can = (resource: string, action: string) => {
  return user.permissions.some(p =>
    p.resource === resource && p.action === action
  );
};

Breakdown:
- Role/permission CRUD: 12 hr
- Permission matrix UI: 8 hr
- Hierarchical logic: 8 hr
- usePermissions composable: 8 hr
- Route guards: 6 hr
- UI conditionals (30+ components): 10 hr
- Column visibility: 6 hr
- Testing: 6 hr
────────────────
TOTAL: 64 hr
```

### Decision Rule

```typescript
if (requirements.includes('role-based') || requirements.includes('permissions')) {
  askClient({
    question: 'What level of RBAC?',
    options: [
      'Simple auth checks (logged in/out) → INCLUDED',
      'Basic RBAC (2-3 roles) → +20 hours',
      'Advanced (5+ roles, granular) → +60 hours',
      'Enterprise (hierarchical, workflows) → +80 hours',
    ],
  });
}
```

---

## 📡 Real-Time Updates Estimation

**⚠️ CRITICAL:** Static data is INCLUDED, but real-time is 5-40 additional hours per module!

### Real-Time Complexity Levels

**Level 0: Static Data (INCLUDED)**

```typescript
// Load once, no updates
const users = await api.getUsers();

// NO EXTRA ESTIMATION NEEDED
```

**Level 1: Polling (+5 hours per module)**

```typescript
// Refresh every 30 seconds
setInterval(() => {
  fetchLatestData();
}, 30000);

Breakdown:
- Polling setup: 2 hr
- Cleanup on unmount: 1 hr
- Testing: 2 hr
────────────────
TOTAL: 5 hr per module
```

**Level 2: WebSocket Real-Time (+40 hours per module)**

```typescript
// Instant updates via WebSocket
const socket = io('wss://api.example.com');

socket.on('user_created', (user) => {
  usersStore.addUser(user);
  showNotification('New user added');
});

Breakdown:
- Socket.io setup: 8 hr
- Connection management (reconnect): 6 hr
- Event handlers (5 events): 8 hr
- State synchronization: 8 hr
- UI animations (new item pulse): 4 hr
- Edge cases (offline, multi-tab): 8 hr
- Testing: 6 hr
────────────────
TOTAL: 48 hr (budget 40 for medium complexity)
```

### Decision Rule

```typescript
if (requirements.includes('real-time') || requirements.includes('live updates')) {
  askClient({
    question: 'Real-time requirement level?',
    options: [
      'Static (load once) → INCLUDED',
      'Polling (30s refresh) → +5 hrs per module',
      'WebSocket (instant) → +40 hrs per module',
      'Collaborative editing → +100 hrs (use library!)',
    ],
  });
}
```

---

## ♿ Accessibility (WCAG) Estimation

**⚠️ CRITICAL:** Basic accessibility is INCLUDED in Vuetify/Tailwind, but WCAG compliance is 50+ hours!

### Accessibility Levels

**Level 0: Basic (INCLUDED in Vuetify/Tailwind)**

```typescript
// You get this for free:
- Semantic HTML (Vuetify uses <button>, <nav>, proper roles)
- Color contrast 4.5:1 (Vuetify themes meet WCAG AA by default)
- Keyboard navigation (Tab order, Enter to submit)
- Focus indicators (Vuetify handles this)

// NO EXTRA ESTIMATION NEEDED
```

**Level 1: WCAG AA (+50 hours)**

```typescript
// Required for government/healthcare
<VBtn
  aria-label="Create new user"
  :aria-disabled="isLoading"
>

<VDataTable
  role="table"
  aria-label="Users list"
  :aria-rowcount="users.length"
>

Breakdown:
- ARIA labels (all components): 20 hr
- Focus management (modal traps): 8 hr
- Screen reader testing (NVDA, VoiceOver): 10 hr
- Keyboard shortcuts: 4 hr
- Skip links, landmarks: 4 hr
- Remediation based on audit: 8 hr
────────────────
TOTAL: 54 hr (budget 50)
```

### Decision Rule

```typescript
if (requirements.includes('accessible') || requirements.includes('WCAG')) {
  askClient({
    question: 'Accessibility compliance level?',
    options: [
      'Basic (Vuetify/Tailwind default) → INCLUDED',
      'WCAG AA (government/healthcare) → +50 hours',
      'WCAG AAA (enhanced) → +120 hours',
    ],
  });
}
```

---

## 🔌 Third-Party Integrations

### Integration Cost Matrix (Hours Reduced 15-20%)

| Integration Type    | Hours    | Examples                            |
| ------------------- | -------- | ----------------------------------- |
| **Simple Library**  | 2-4 hr   | Chart.js, jsPDF, Lodash             |
| **OAuth Provider**  | 6-10 hr  | Google, GitHub, Microsoft ← REDUCED |
| **Payment Gateway** | 18-25 hr | Stripe, PayPal, Square ← REDUCED    |
| **Maps**            | 10-15 hr | Google Maps, Mapbox ← REDUCED       |
| **Video/Chat**      | 25-35 hr | Twilio, Agora, WebRTC ← REDUCED     |
| **Analytics**       | 6-10 hr  | Google Analytics, Mixpanel          |
| **CRM/ERP**         | 20-30 hr | Salesforce, HubSpot, SAP            |
| **File Storage**    | 12-18 hr | AWS S3, Cloudinary                  |
| **Social Media**    | 15-20 hr | Twitter API, Facebook Graph         |

**Why Optimized:** Modern SDKs provide UI components (Stripe Elements, Google OAuth buttons), excellent documentation, and TypeScript types.

### Decision Rule

```typescript
// Extract all third-party mentions from requirements
const integrations = extractIntegrations(requirements);

integrations.forEach(service => {
  const hours = estimateIntegration(service);
  addToTotal(hours);

  console.log(`${service}: +${hours} hours`);
});
```

---

## 🎯 Final Assembly Formula

### Complete Estimation Formula

```typescript
STEP 1: Base Estimate (Realistic for Vuetify/Tailwind)
base = Feature Hours (PERT or Direct)
// 25% lower than v4.0 due to component libraries

STEP 2: Apply Reusability (If Similar Modules)
if (similarModules >= 3) {
  module2onwards = base × 0.75; // 25% reduction (not 35%)
}

STEP 3: Apply Design Reductions (Multiplicative)
adjusted = base;
if (completeDesigns) adjusted × 0.75;
if (designSystem) adjusted × 0.85;
if (uxDocs) adjusted × 0.92;
if (contentReady) adjusted × 0.93;

STEP 4: Apply Device/Browser/Language
if (desktopOnly) adjusted × 0.85;
if (ie11Required) adjusted × 1.5; // Warn client!
if (multiLanguage) adjusted × 1.15;

STEP 5: Add API Setup (Additive, not multiplicative)
if (apiStatus === 'parallel') adjusted += 8;
if (apiStatus === 'frontend-first') adjusted += 16;

STEP 6: Add Hidden Complexity (Additive)
if (rbacLevel === 'basic') adjusted += 20;
if (rbacLevel === 'advanced') adjusted += 60;
if (rbacLevel === 'enterprise') adjusted += 80;

if (realTime === 'polling') adjusted += 5;
if (realTime === 'websocket') adjusted += 40;

if (wcag === 'AA') adjusted += 50;
if (wcag === 'AAA') adjusted += 120;

// Third-party integrations
integrations.forEach(service => {
  adjusted += estimateIntegration(service); // 2-40 hrs each
});

STEP 7: Professional Development Overhead
// Combined testing + edge cases
adjusted × 1.20; // +20% for testing and edge cases

STEP 8: Confidence Buffer (Includes Rework)
const bufferMap = {
  90: 1.05, // +5% (code review, QA, tweaks)
  75: 1.10, // +10% (moderate unknowns) ← Most common
  60: 1.20, // +20% (significant unknowns)
};
adjusted × bufferMap[confidence];

STEP 9: Round Up
final = Math.ceil(adjusted / 4) * 4; // Round to nearest 4 hours
```

### Example Calculation

```typescript
Feature: User Dashboard + CRUD

// STEP 1: Base (Realistic for Vuetify)
Dashboard: 20 hr (optimized for modern frameworks)
User CRUD: 12 hr (optimized for modern frameworks)
Base Total: 32 hr

// STEP 2: Reusability (none, unique modules)
32 hr (no change)

// STEP 3: Design Reductions
Complete designs: 32 × 0.75 = 24 hr
Design system: 24 × 0.85 = 20.4 hr

// STEP 4: Device/Browser/Language
Multi-device: 20.4 × 1.0 = 20.4 hr (baseline)
Modern browsers: 20.4 × 1.0 = 20.4 hr (baseline)
Single language: 20.4 × 1.0 = 20.4 hr (baseline)

// STEP 5: API Setup
APIs ready: 20.4 + 0 = 20.4 hr

// STEP 6: Hidden Complexity
Basic RBAC: 20.4 + 20 = 40.4 hr
No real-time: 40.4 + 0 = 40.4 hr
Basic accessibility: 40.4 + 0 = 40.4 hr (included)
Google Analytics: 40.4 + 8 = 48.4 hr

// STEP 7: Professional Dev (+20%, REDUCED from 30%)
48.4 × 1.20 = 58.1 hr

// STEP 8: Buffer (75% confidence, +10%, REDUCED from 15%)
58.1 × 1.10 = 63.9 hr

// STEP 9: Round
Math.ceil(63.9 / 4) × 4 = 64 hr

────────────────────────────────
FINAL ESTIMATE: 64 hours (CORRECTED)
Range: 58-70 hours (±10%)
Confidence: 75%
────────────────────────────────

// Old v5.0: 76 hrs (padded by ~19%)
// Corrected v5.0: 64 hrs (realistic, no padding)
```

---

## 📋 Estimation Checklist

**Before finalizing estimate, confirm:**

- [ ] Base hours are realistic for Vuetify/Tailwind (25% lower than v4.0)
- [ ] Component reusability set to 25% (not 35%) for similar modules
- [ ] Design readiness factors applied (complete designs -25%, system -15%, etc.)
- [ ] Device/browser/language adjustments included
- [ ] API setup hours added (only if mocks needed: +8 or +16 hrs)
- [ ] **NEW:** RBAC complexity estimated (basic +20hr, advanced +60hr, enterprise +80hr)
- [ ] **NEW:** Real-time requirement added (polling +5hr, WebSocket +40hr per module)
- [ ] **NEW:** Accessibility compliance included (WCAG AA +50hr, AAA +120hr)
- [ ] **NEW:** Third-party integrations itemized (OAuth +10hr, Stripe +25hr, Maps +15hr, etc.)
- [ ] Professional development overhead applied (+20% for testing + edge cases)
- [ ] Confidence buffer applied (+10-25% includes rework)
- [ ] Rounded to nearest 4 hours (half-day)
- [ ] Provided range not exact number (±10-15%)
- [ ] Stated confidence percentage
- [ ] Documented all assumptions
- [ ] **NEW:** Verified no duplicate buffer application
- [ ] **NEW:** Explained what's INCLUDED vs EXTRA (responsive, API, RBAC, etc.)

---

## 🎓 Quick Reference Card (v5.0)

**For 10-Second Decisions:**

| Scenario                     | Method     | Base Hours Adjustment |
| ---------------------------- | ---------- | --------------------- |
| Simple CRUD, Vuetify         | Direct     | 8-12 hr               |
| Medium feature, clear design | Direct     | 16-24 hr              |
| Complex feature, unknowns    | PERT       | Calculate             |
| Very quick estimate needed   | T-Shirt    | S/M/L/XL              |
| Have past similar projects   | Historical | Adjust                |

**Standard Overhead Stack (v5.0):**

- Professional Dev (testing + edge cases): +20%
- Confidence Buffer (includes rework): +10% to +25%
- **Total Typical:** × 1.20 × 1.10 = **1.32x** (~32% overhead)

**Quick Confidence Score:**

- Complete designs + clear requirements + APIs ready = 80-90%
- Wireframes + some unknowns = 70-80%
- No designs + new tech = 60-70%
- Major unknowns = <60% (recommend discovery phase)

**Hidden Costs Checklist:**

- RBAC? Basic +20hr, Advanced +60hr, Enterprise +80hr
- Real-time? Polling +5hr, WebSocket +40hr per module
- Accessibility? WCAG AA +50hr, AAA +120hr
- Third-party? Estimate each: OAuth +10hr, Payment +25hr, Maps +15hr

**Complete Formula:**

```
final = baseHours × reusability × design × device × i18n
        + apiSetup + rbac + realTime + wcag + integrations
        × 1.20 (prof dev) × buffer (1.05-1.30)
```

---

**This module provides the mathematical foundation. For rapid versions, see `06_rapid_estimation.md`.**

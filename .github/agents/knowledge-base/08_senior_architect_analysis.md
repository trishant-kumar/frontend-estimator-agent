# 08: Senior Architect Analysis Module

**Purpose:** Deep technical analysis including component reusability, feature assessment, and architectural decisions.

**When to Load:** For any non-trivial estimation requiring technical deep-dive.

**PHILOSOPHY:** Edge cases, workflows, and integration UIs are standard professional development - INCLUDED in base hours, not charged as extras.

---

## 🏗️ COMPONENT REUSABILITY SCANNER

**Scan codebase BEFORE estimating - Vue components are highly reusable!**

### Scanning Commands

```bash
# Scan existing Vue components
file_search("components/**/*.vue")
read_file("components/atoms/")
read_file("components/molecules/")
read_file("components/organisms/")
list_dir("components/")

# Check for similar pages
file_search("pages/**/*.vue")
grep_search("similar feature keyword", isRegexp=false)

# Check composables
file_search("composables/**/*.ts")
```

### Reusability Calculation Rules

| Component Level | Reuse Reduction | Example                                     |
| --------------- | --------------- | ------------------------------------------- |
| **Atoms**       | 40-50%          | Button, Input, Badge, Icon, DatePicker      |
| **Molecules**   | 30-40%          | Card, Modal, SearchBar, UserCard, FormField |
| **Organisms**   | 20-30%          | DataTable, Header, Sidebar, MultiStepForm   |
| **Templates**   | 50-60%          | Similar page (copy & modify pattern)        |
| **Composables** | 30-40%          | useAuth, useTable, useForm, useApi          |

### Component Reuse Decision Tree

```
For each required component:

Does exact component exist?
├─ YES → Use as-is (0 hr, just import)
│
└─ NO → Does similar component exist?
    ├─ YES → Customize existing (-40-60% time)
    │    └─ Small changes: -60%
    │    └─ Moderate changes: -40%
    │
    └─ NO → Build from scratch (100% time)
         └─ But add to reusable library for future!
```

### Example: Heavy Component Reuse

```
Requirement: "User management page with data table, search, and filters"

✅ Component Scan Results:
- ✓ components/organisms/DataTable.vue EXISTS → Reuse (-40%)
- ✓ components/molecules/SearchBar.vue EXISTS → Reuse (-35%)
- ✓ components/molecules/FilterPanel.vue EXISTS → Reuse (-30%)
- ✓ pages/agencies/index.vue is SIMILAR → Template (-50%)
- ✓ composables/useTable.ts EXISTS → Reuse (-30%)

Original estimate (from scratch): 32 hr
After component reuse: 32 × 0.60 × 0.65 × 0.70 × 0.50 × 0.70 = 6 hr
Realistic with customization: 12 hr (63% time saved)
```

---

## 🎯 EDGE CASE CHECKLIST (INCLUDED IN BASE)

**Edge cases are NOT extras - they're standard professional development practices!**

**When you see these keywords, ensure base hours INCLUDE these practices:**

| Keyword/Pattern         | What to INCLUDE in Base (No Extra Charge)             | Detection                      |
| ----------------------- | ----------------------------------------------------- | ------------------------------ |
| **"user input"**        | Validation, XSS prevention, max length, unique checks | Any form, input, textarea      |
| **"file upload"**       | Size limits, type validation, preview, error messages | upload, file, image, document  |
| **"pagination"**        | Empty state, single page, first/last, per-page        | pagination, page, limit        |
| **"search/filter"**     | No results, special chars, debounce, clear all        | search, filter, query          |
| **"date/time"**         | Timezones, DST, formats, invalid dates, ranges        | date, time, calendar, schedule |
| **"multi-select"**      | Select all, deselect all, indeterminate state         | multi-select, checkbox, bulk   |
| **"permissions/roles"** | No access, partial access, disabled states            | permission, role, access, auth |
| **"email/SMS"**         | Delivery failure, retry, templates, validation        | email, sms, notification       |
| **"export/import"**     | Large files, formats, validation, error parsing       | export, import, csv, excel     |
| **"sorting"**           | Multiple columns, null values, custom sort            | sort, order by                 |
| **"drag & drop"**       | Touch support, snap, validation, undo                 | drag, drop, sortable           |

**These are NOT complexity multipliers - they're basic professional practices INCLUDED in base!**

### Edge Case Checklist Example

```
Requirement: "Upload profile pictures and filter users by role and date range"

✅ Edge Cases INCLUDED in Base Hours:
- File upload: Size validation, type checking, preview, error messages
- Filter: No results state, clear filters, loading states
- Roles: Permission checks, disabled states for restricted roles
- Date range: Invalid date handling, format validation

Base estimate: 24 hr (INCLUDES all edge cases above)
NO ADDITIONAL MULTIPLIER - these are standard practices!
```

---

## 🔄 WORKFLOW ASSESSMENT (INCLUDED IN BASE)

**Workflows are requirements the client asked for - INCLUDED in base hours, not extras!**

**When you see these keywords, workflows are PART OF the feature, not "complexity":**

| Workflow Pattern         | Detection Keywords                           | What's INCLUDED in Base                     |
| ------------------------ | -------------------------------------------- | ------------------------------------------- |
| **Approval Flow**        | approve, reject, review, pending, escalate   | Multi-level chains, status tracking, emails |
| **Multi-Step Wizard**    | step, wizard, progress, next, previous       | Progress indicator, validation per step     |
| **Draft/Publish**        | draft, publish, schedule, version, unpublish | Auto-save, status transitions               |
| **Bulk Actions**         | bulk, select all, batch, mass update         | Multi-select, progress, partial failures    |
| **Import/Export**        | import, export, CSV, Excel, PDF, download    | Parsing, validation, format conversion      |
| **Audit Trail/History**  | history, log, audit, activity, changelog     | Track changes, who/when timestamps          |
| **Notification System**  | notify, alert, email, push, reminder, bell   | In-app + email notifications                |
| **State Transitions**    | status, workflow, transition, lifecycle      | State machine logic, transitions            |
| **Scheduling/Recurring** | schedule, cron, recurring, repeat, frequency | Date logic, recurrence patterns             |
| **Templates/Presets**    | template, preset, save as, clone, duplicate  | Copy logic, customization                   |

**These are NOT add-ons - the client is asking for these features in requirements!**

### Workflow Assessment Example

```
Requirement: "Invoice system with draft, manager approval, auto-send to clients"

✅ Workflows INCLUDED in Base Hours:
- Draft/Publish workflow: Auto-save, status management
- 2-step approval flow: Manager review, status tracking
- State transitions: Draft → Pending → Approved → Sent
- Auto-send: Trigger logic, email integration UI

Base estimate for invoice module: 48 hr (INCLUDES all workflows above)
NO ADDITIONAL MULTIPLIER - these are the features requested!
```

---

## 🔌 INTEGRATION UI ASSESSMENT (INCLUDED IN BASE)

**Integration UI (displaying external data) is INCLUDED in base - NOT a separate charge!**

**When you see these keywords, integration UI is PART OF the feature:**

| Integration Type       | Detection Keywords                         | What's INCLUDED in Base                           |
| ---------------------- | ------------------------------------------ | ------------------------------------------------- |
| **Payment Display**    | stripe, paypal, payment status, checkout   | Payment history UI, transaction list, receipts    |
| **Auth UI**            | oauth, sso, saml, login redirect           | Login redirect, OAuth flow UI, connect accounts   |
| **Calendar Display**   | google calendar, outlook, ical, events     | Calendar view, event list UI, availability        |
| **Maps Display**       | google maps, mapbox, location display      | Map embed, location picker, address autocomplete  |
| **Email/SMS UI**       | sendgrid status, email logs, sms delivery  | Notification history UI, delivery status display  |
| **Cloud Storage UI**   | s3 files, image gallery, file browser      | File picker UI, upload progress, preview          |
| **Analytics Display**  | google analytics, charts, metrics          | Dashboard charts, metrics display                 |
| **Social Display**     | facebook login, google login, github auth  | Social login buttons, account linking UI          |
| **Document Preview**   | docusign status, pdf preview, signature    | Document viewer, signature status UI              |
| **Biometric UI**       | fingerprint data, attendance logs          | Biometric data display, device status UI          |
| **Push Notifications** | firebase, notification list, alerts        | Notification center UI, bell icon, mark as read   |
| **Export/Download**    | CSV export, PDF download, Excel generation | Export button, format selection, download trigger |
| **Tally Export**       | tally format, accounting export            | Export to Tally button, format data client-side   |

**ONLY charge extra for truly complex integrations:**

- Building custom video calling UI (WebRTC): +32-48 hr
- Real-time collaboration features: +35-50 hr
- Custom payment gateway UI with webhooks: +40-60 hr
- Advanced CRM integration with bidirectional sync: +40-60 hr

**Standard integration UI is INCLUDED in feature base hours!**

### Integration UI Assessment Example

```
Requirement: "Dashboard showing Stripe payment history, export to CSV, and Google Maps location"

✅ Integration UI INCLUDED in Base Hours:
- Stripe payment history: Display transaction list, status badges, date filters
- CSV export: Export button, format data, trigger download
- Google Maps: Embed map, display location markers

Base estimate for dashboard: 32 hr (INCLUDES all integration UI above)
NO ADDITIONAL CHARGE - these are standard UI features!

NOTE: Backend API integration is excluded (backend team scope)
```

Base booking UI: 32 hr
Integrations total: +102 hr
Total: 134 hr × 1.52 = 204 hr

⚠️ Warning: 5 integrations = high complexity

```

---

## 🏗️ ARCHITECTURAL DECISION FRAMEWORK

**Think like a senior architect - assess these critical questions:**

### Assessment Questions

**State Management:**

- Global state (Pinia/Vuex) or component state?
- Shared across routes?
- Complex state logic?

**Performance:**

- 100+ items? 1000+ items? 10,000+ items?
- Virtual scrolling needed?
- Initial load time requirement? (<3s critical)
- Web workers for heavy compute?

**Security:**

- Sensitive data (PII, payment)?
- Encryption needed (at rest, in transit)?
- RBAC required?
- Audit logging for compliance?

**Scalability:**

- Future features planned?
- Multiple teams working?
- Internationalization now or later?

**Offline/PWA:**

- Must work offline?
- Service workers needed?
- Background sync?

**Real-Time:**

- WebSocket connections?
- Optimistic UI updates?
- Conflict resolution?

### Architectural Complexity Multipliers

| Architecture Need            | When to Apply                     | Add Time | Multiplier |
| ---------------------------- | --------------------------------- | -------- | ---------- |
| **Micro-frontend**           | Multiple teams, 3+ domains        | +40-60hr | +40%       |
| **Complex State Management** | Deep nesting, real-time, sync     | +20-32hr | +25%       |
| **Performance Optimization** | 1000+ items, <1s load time        | +16-28hr | +20%       |
| **Offline-First PWA**        | Full offline with sync            | +28-48hr | +35%       |
| **Advanced Security**        | Encryption, CSP, audit trails     | +20-32hr | +25%       |
| **Multi-Tenancy**            | Organization contexts, isolation  | +24-40hr | +30%       |
| **Real-Time Sync**           | WebSocket, CRDT, conflict resolve | +28-48hr | +35%       |
| **Advanced Caching**         | Service worker, IndexedDB, CDN    | +20-32hr | +25%       |
| **Internationalization**     | 5+ languages, RTL, localization   | +16-28hr | +20%       |
| **Accessibility (WCAG AA)**  | Screen reader, keyboard nav       | +12-24hr | +15%       |
| **E2E Test Suite**           | Comprehensive Playwright/Cypress  | +16-28hr | +20%       |

### Architectural Analysis Example

```

Requirement: "Real-time collaborative document editor"

🏗️ Architectural Requirements:
✅ Real-Time: WebSocket + OT algorithm (+35%)
✅ Performance: Virtual scrolling, text diffing (+20%)
✅ Offline PWA: IndexedDB + sync queue (+35%)
✅ Conflict Resolution: Manual merge UI (+20%)

Base editor: 40 hr
Architecture: 40 × 1.35 × 1.20 × 1.35 × 1.20 = 105 hr
With multipliers: 105 × 1.52 = 160 hr

Recommendation: Consider using Yjs library to reduce by 40%

````

### 🎨 DESIGN SYSTEM MATURITY ASSESSMENT

**Auto-detect design readiness:**

| Design State              | Time Impact | Questions to Ask                      |
| ------------------------- | ----------- | ------------------------------------- |
| **None (wireframes)**     | +40-60%     | Devs must design + iterate            |
| **Basic mockups**         | +20-30%     | Missing states, interactions          |
| **Complete designs**      | Baseline    | Happy/error/loading states defined    |
| **Design system (Figma)** | -15-25%     | Tokens, variants, components          |
| **Storybook library**     | -25-35%     | Dev-ready components with props/slots |

**Detection:**

```bash
# Ask client:
"Do you have a design system? (Figma, Storybook, or style guide)"
"Are design tokens (colors, spacing, typography) documented?"
"Do designs include error/loading/empty states?"

# If no designs:
Add design discovery phase: +40-60% to estimate
````

**Example:**

```
Requirement: "User dashboard with 5 widgets"

No design system: 40 hr × 1.40 = 56 hr
Complete Figma with tokens: 40 hr × 0.85 = 34 hr
Difference: 22 hr (39% variance!)

Conclusion: Design system maturity is CRITICAL to estimate accuracy
```

---

## 🎬 ANIMATION & MOTION DETECTION

**Complex animations significantly impact development time - detect and add accordingly:**

### Animation Keyword Detection

| Animation Type           | Keywords                              | Add Time  | Complexity |
| ------------------------ | ------------------------------------- | --------- | ---------- |
| **Page transitions**     | transition, fade, slide, route        | +8-16 hr  | Medium     |
| **Scroll animations**    | scroll, parallax, reveal, animate     | +12-20 hr | Medium     |
| **Micro-interactions**   | hover, click, ripple, feedback, pulse | +8-12 hr  | Low        |
| **Complex timelines**    | gsap, timeline, sequence, stagger     | +20-40 hr | High       |
| **Lottie animations**    | lottie, json animation, after effects | +12-24 hr | Medium     |
| **Loading animations**   | skeleton, shimmer, spinner, progress  | +4-8 hr   | Low        |
| **Drag animations**      | drag, drop, reorder, snap, sort       | +16-28 hr | High       |
| **Chart animations**     | animated charts, transitions, d3      | +8-16 hr  | Medium     |
| **3D/Canvas animations** | three.js, canvas, webgl, 3d           | +40-80 hr | Very High  |
| **SVG animations**       | svg animate, morph, path, stroke      | +12-20 hr | Medium     |

### Animation Libraries Time Impact

| Library              | Purpose                | Learning Curve | Setup Time | Per Animation |
| -------------------- | ---------------------- | -------------- | ---------- | ------------- |
| **CSS Transitions**  | Simple effects         | Low            | 0 hr       | +1-2 hr       |
| **Vue Transition**   | Built-in transitions   | Low            | 0 hr       | +2-4 hr       |
| **Framer Motion**    | React animations       | Medium         | +4 hr      | +4-8 hr       |
| **GSAP**             | Complex timelines      | High           | +8 hr      | +6-12 hr      |
| **Lottie**           | JSON animations        | Medium         | +4 hr      | +8-16 hr      |
| **AOS (Animate On)** | Scroll animations      | Low            | +2 hr      | +3-6 hr       |
| **Three.js**         | 3D graphics            | Very High      | +16 hr     | +20-40 hr     |
| **Anime.js**         | Lightweight animations | Medium         | +4 hr      | +4-8 hr       |
| **Motion One**       | Web Animations API     | Medium         | +6 hr      | +5-10 hr      |

### Detection Workflow

```bash
# Scan requirements for animation keywords
grep_search("animation|animated|transition|gsap|lottie|scroll", isRegexp=true)

# Ask clarifying questions:
"Are animations simple (CSS) or complex (GSAP/Lottie)?"
"Do you have design animations to reference? (After Effects, Figma prototypes)"
"Is performance critical? (60fps requirement adds +20%)"
```

### Example: Animation-Heavy Project

```
Requirement: "Landing page with scroll animations and interactive 3D product viewer"

🎬 Animation Analysis:
✅ Scroll animations: parallax, fade-in (+16 hr)
✅ 3D viewer: Three.js integration (+48 hr)
✅ Micro-interactions: hover effects (+8 hr)
✅ Loading animations: skeleton screens (+6 hr)

Base landing page: 32 hr
Animations total: +78 hr
Total: 110 hr × 1.52 = 167 hr

⚠️ Recommendation: Consider using pre-built 3D viewer lib to reduce by 30 hr
```

---

## 🗄️ STATE MANAGEMENT COMPLEXITY

**State complexity is often underestimated - assess carefully:**

### Complexity Levels

| Level         | Indicators                                  | Add Time  | Multiplier |
| ------------- | ------------------------------------------- | --------- | ---------- |
| **Simple**    | Component state only (useState, ref)        | 0 hr      | +0%        |
| **Medium**    | 3-5 stores, basic CRUD                      | +8-12 hr  | +15%       |
| **Complex**   | 10+ stores, normalized state, relationships | +16-24 hr | +25%       |
| **Very High** | Real-time sync, CRDT, OT, offline-first     | +28-48 hr | +40%       |
| **Critical**  | Distributed state, blockchain, consensus    | +60+ hr   | +60%       |

### State Management Patterns (Vue)

| Pattern                 | Setup Time | Complexity | When to Use                   |
| ----------------------- | ---------- | ---------- | ----------------------------- |
| **Component State**     | 0 hr       | Low        | Single component, no sharing  |
| **Props/Emits**         | +1-2 hr    | Low        | Parent-child only             |
| **Provide/Inject**      | +2-4 hr    | Medium     | Deep prop drilling            |
| **Pinia Store**         | +4-8 hr    | Medium     | Global state, 3-5 stores      |
| **Pinia + Persistence** | +8-12 hr   | Medium     | LocalStorage sync             |
| **Normalized State**    | +12-20 hr  | High       | Relational data (users/posts) |
| **Real-time Sync**      | +24-40 hr  | Very High  | WebSocket + optimistic UI     |
| **Offline-First**       | +32-48 hr  | Very High  | IndexedDB + sync queue        |

### State Management Patterns (React)

| Pattern                  | Setup Time | Complexity | When to Use                 |
| ------------------------ | ---------- | ---------- | --------------------------- |
| **useState**             | 0 hr       | Low        | Component-local only        |
| **Context API**          | +3-6 hr    | Medium     | Small shared state          |
| **Redux Toolkit**        | +8-16 hr   | High       | Complex global state        |
| **Zustand**              | +4-8 hr    | Medium     | Simple global state         |
| **Jotai/Recoil**         | +6-12 hr   | Medium     | Atomic state management     |
| **TanStack Query**       | +8-12 hr   | Medium     | Server state caching        |
| **Real-time (Firebase)** | +16-24 hr  | High       | Live updates, collaboration |

### Detection Questions

```bash
# Ask to determine complexity:
"How many entities/resources does the app manage? (users, posts, comments, etc.)"
"Do entities have relationships? (posts belong to users, comments belong to posts)"
"Is real-time sync needed? (multiple users seeing live updates)"
"Must app work offline? (queue actions, sync when online)"
"Any collaborative editing? (Google Docs-style)"
```

### Example: Complex State Management

```
Requirement: "Multi-tenant SaaS dashboard with real-time notifications"

🗄️ State Analysis:
✅ Entities: Users, Organizations, Projects, Tasks, Comments (5+ entities)
✅ Relationships: Normalized state needed (+20 hr)
✅ Real-time: WebSocket for notifications (+24 hr)
✅ Multi-tenancy: Organization context switching (+12 hr)
✅ Persistence: LocalStorage for preferences (+6 hr)

Base dashboard: 40 hr
State complexity: +62 hr
Total: 102 hr × 1.52 = 155 hr

Complexity Level: VERY HIGH
State Multiplier: +40%
```

---

## 📝 CONTENT MANAGEMENT COMPLEXITY

**CMS integration and dynamic content add significant overhead:**

### Content Type Detection

| Content Type             | Keywords                       | Add Time  | Complexity |
| ------------------------ | ------------------------------ | --------- | ---------- |
| **Static content**       | hardcoded, json, yaml          | 0 hr      | None       |
| **CMS integration**      | contentful, strapi, sanity     | +12-24 hr | Medium     |
| **Headless CMS**         | api, cms, content delivery     | +12-20 hr | Medium     |
| **Rich text editor**     | wysiwyg, markdown, editor      | +12-20 hr | Medium     |
| **Preview mode**         | draft, preview, unpublished    | +8-16 hr  | Medium     |
| **Multi-language**       | i18n, translations, locales    | +16-28 hr | High       |
| **Media management**     | dam, cloudinary, upload        | +12-20 hr | Medium     |
| **SEO metadata**         | meta tags, og, schema, sitemap | +8-12 hr  | Low        |
| **Content versioning**   | revisions, history, rollback   | +16-24 hr | High       |
| **Scheduled publishing** | cron, schedule, publish date   | +12-20 hr | Medium     |

### CMS Platform Setup Time

| Platform           | Integration Time | Learning Curve | Frontend Impact  |
| ------------------ | ---------------- | -------------- | ---------------- |
| **Contentful**     | +12-16 hr        | Medium         | +GraphQL (+4 hr) |
| **Strapi**         | +10-14 hr        | Low            | +REST API        |
| **Sanity**         | +14-20 hr        | Medium         | +GROQ (+6 hr)    |
| **WordPress REST** | +8-12 hr         | Low            | +REST API        |
| **Prismic**        | +10-14 hr        | Medium         | +Slices (+8 hr)  |
| **Ghost**          | +8-12 hr         | Low            | +REST API        |
| **Custom CMS**     | +20-40 hr        | High           | Custom API       |

### Rich Text Rendering

| Format               | Rendering Lib     | Add Time  | Complexity |
| -------------------- | ----------------- | --------- | ---------- |
| **Markdown**         | marked, remark    | +4-6 hr   | Low        |
| **HTML (sanitized)** | DOMPurify         | +2-4 hr   | Low        |
| **Portable Text**    | @portabletext/vue | +8-12 hr  | Medium     |
| **Draft.js**         | draft-js (React)  | +12-16 hr | High       |
| **Slate.js**         | slate (React)     | +16-24 hr | High       |
| **TipTap**           | tiptap (Vue)      | +12-16 hr | Medium     |
| **ProseMirror**      | prosemirror       | +20-32 hr | Very High  |

### Multi-Language (i18n) Impact

| Languages | Add Time  | Considerations                           |
| --------- | --------- | ---------------------------------------- |
| **2-3**   | +12-16 hr | vue-i18n/react-i18next setup             |
| **4-6**   | +20-28 hr | + Language switcher, locale routing      |
| **7-10**  | +28-40 hr | + RTL support (Arabic, Hebrew)           |
| **10+**   | +40-60 hr | + Translation management tool, fallbacks |

### Detection Workflow

```bash
# Scan for CMS keywords
grep_search("cms|contentful|strapi|sanity|rich text|i18n", isRegexp=true)

# Ask clarifying questions:
"Is content hardcoded or managed through a CMS?"
"What CMS platform? (Contentful, Strapi, WordPress, etc.)"
"How many languages need to be supported?"
"Is rich text editing required? What format? (Markdown, WYSIWYG)"
"Do you need preview mode for draft content?"
```

### Example: Content-Heavy Application

```
Requirement: "Multi-language blog with Contentful CMS and rich text editing"

📝 Content Analysis:
✅ CMS: Contentful integration (+16 hr)
✅ Rich text: @portabletext/vue rendering (+10 hr)
✅ i18n: 5 languages with routing (+24 hr)
✅ SEO: Meta tags, sitemap, schema (+10 hr)
✅ Preview mode: Draft content preview (+12 hr)

Base blog UI: 32 hr
Content features: +72 hr
Total: 104 hr × 1.52 = 158 hr

⚠️ Recommendation: Use Contentful's preview API to reduce preview mode work by -4 hr
```

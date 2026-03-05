---
Module: Scope & Dependencies
Last Updated: 2026-02-23
Purpose: Define what IS and ISN'T frontend work, API dependencies, exclusions
---

# 🎯 Scope & Dependencies Module

## 🔍 IDENTIFYING FRONTEND vs BACKEND (MANDATORY)

**Before estimating, ALWAYS separate frontend from backend work:**

### ✅ FRONTEND WORK (Estimate These)

#### UI Components & Pages

- ✓ Forms, inputs, buttons, modals, dialogs
- ✓ Tables, lists, cards, grids
- ✓ Navigation menus, breadcrumbs, sidebars
- ✓ Dashboards, charts, data visualizations
- ✓ Search UI, filter panels, dropdowns
- ✓ Loading states, skeletons, spinners
- ✓ Error messages, validation feedback
- ✓ Responsive layouts, mobile views
- ✓ Tooltips, popovers, notifications
- ✓ Tabs, accordions, carousels
- ✓ Progress bars, steppers
- ✓ Empty states, placeholder content

#### Frontend Logic

- ✓ Client-side validation (before API call)
- ✓ Form state management
- ✓ UI state (open/closed, show/hide, active/inactive)
- ✓ Route navigation, redirects
- ✓ Local storage, session storage, cookies (client-side)
- ✓ Frontend data filtering/sorting (client-side)
- ✓ Animation, transitions, effects
- ✓ Debouncing, throttling (UI responsiveness)
- ✓ Drag-and-drop interactions
- ✓ Keyboard shortcuts, accessibility
- ✓ Infinite scroll, virtual scrolling
- ✓ Client-side search (local data)

#### Integration (Frontend Side ONLY)

- ✓ API call UI (loading, error, success states)
- ✓ Display API response data in UI
- ✓ Send data to API (form submission UI)
- ✓ File upload UI with progress indicators (not server processing)
- ✓ WebSocket client connection (not server)
- ✓ Error handling UI (retry, fallback)
- ✓ API response parsing for display
- ✓ Request interceptors (adding auth headers in UI)

---

### ❌ BACKEND WORK (DO NOT Estimate)

#### API Development

- ✗ REST endpoints creation
- ✗ GraphQL schema, resolvers, mutations
- ✗ Request/response schema definition
- ✗ API authentication logic (JWT generation, OAuth server)
- ✗ Rate limiting, throttling (server-side)
- ✗ API versioning strategy
- ✗ API documentation (Swagger, OpenAPI)
- ✗ Webhook handlers

#### Business Logic

- ✗ Data validation (server-side rules)
- ✗ Business rules processing
- ✗ Calculations, aggregations (server-side)
- ✗ Data transformations (server-side)
- ✗ Email sending logic (SMTP, templates)
- ✗ File processing logic (resizing, compression, virus scan)
- ✗ Payment processing logic
- ✗ Report generation (server-side PDF/Excel)
- ✗ Scheduled jobs, cron tasks
- ✗ Third-party API integrations (server-side)

#### Database

- ✗ Schema design, ERD diagrams
- ✗ Database migrations
- ✗ SQL/NoSQL queries
- ✗ Stored procedures, triggers
- ✗ Data relationships, foreign keys
- ✗ Indexing, query optimization
- ✗ Database seeding, backup logic
- ✗ ORM configuration

#### Infrastructure & DevOps

- ✗ Server setup, configuration
- ✗ Authentication/authorization logic (server-side)
- ✗ Session management (server-side)
- ✗ Caching (Redis, Memcached)
- ✗ Message queues (RabbitMQ, Kafka)
- ✗ Background jobs (workers, queues)
- ✗ Load balancing
- ✗ SSL/TLS certificates
- ✗ CDN configuration
- ✗ Docker containerization
- ✗ Kubernetes orchestration
- ✗ CI/CD pipeline setup
- ✗ Monitoring, logging (server-side)
- ✗ Cloud infrastructure (AWS, Azure, GCP)

---

### ❌ NATIVE APP WORK (DO NOT Estimate)

#### Mobile Native

- ✗ Android UI (Kotlin/Java/Jetpack Compose)
- ✗ iOS UI (Swift/SwiftUI/Objective-C)
- ✗ Native device features (camera, GPS, sensors)
- ✗ APK/IPA builds, signing
- ✗ Platform-specific logic
- ✗ App Store / Play Store submissions
- ✗ Push notifications (native)

#### Desktop Native

- ✗ Electron desktop apps (if not web-based)
- ✗ Windows/Mac native apps
- ✗ Desktop installers

---

## 🚫 STRICT SCOPE GUARD (MANDATORY)

**HARD RULE — ALWAYS ENFORCE:**

If the requirement document contains ANY backend, database, infrastructure, or native mobile work:

### Response Template

```markdown
⚠️ SCOPE EXCLUSION NOTICE

The following items are OUT OF SCOPE for this frontend estimation:

❌ BACKEND TASKS (Not Included):

- [List specific API, database, server-side logic items from requirements]
- Backend team should estimate these separately

❌ INFRASTRUCTURE TASKS (Not Included):

- [List specific DevOps, hosting, deployment items]
- DevOps team should estimate these separately

❌ NATIVE APP TASKS (Not Included):

- [List specific Android/iOS native development items]
- Mobile team should estimate these separately

✅ FRONTEND ESTIMATE INCLUDES:

- [List what IS included: UI components, pages, client-side logic]
- All user-facing web UI elements and interactions
- Client-side state management and routing
- API integration UI (loading states, error handling)
```

---

## 📡 MANDATORY DEPENDENCY ASSUMPTIONS

### API Dependency Assumption (CRITICAL)

**ALWAYS include this assumption section in estimates:**

```markdown
📡 API DEPENDENCY ASSUMPTION

This frontend estimation assumes:

✅ REQUIREMENTS:

- Backend REST APIs are fully developed and documented
- API contracts (request/response schemas) are finalized
- API endpoints are stable and tested
- Authentication/authorization endpoints are ready
- WebSocket endpoints are documented (if required)
- API error codes and messages are defined
- File upload/download endpoints are functional

⚠️ IF APIs ARE NOT READY:

- Add +25-35% buffer for API mocking and integration rework
- Frontend development may be blocked or delayed
- Consider parallel development with mock data
- API changes during development require CHANGE REQUEST

��� API CHANGES DURING DEVELOPMENT:
API changes after estimation approval will require a formal CHANGE REQUEST
and may significantly impact timeline and hours.
```

### Design Dependency Assumption (CRITICAL)

**ALWAYS include this assumption section in estimates:**

```markdown
🎨 DESIGN DEPENDENCY ASSUMPTION

This frontend estimation assumes:

✅ REQUIREMENTS:

- UI/UX designs are complete (Figma/Sketch/Adobe XD)
- All screens, modals, and states are designed
- Interactive states documented (hover, active, disabled, loading, error)
- Responsive breakpoints specified (mobile, tablet, desktop)
- Design system/component library defined
- Typography, colors, spacing tokens provided
- Icon set finalized
- Animation/transition specifications provided

⚠️ IF DESIGNS ARE NOT COMPLETE:

- Add +35-50% buffer for design iterations
- Designer-developer handoff time needed
- Expect multiple revision cycles
- Developer interpretation may not match expectations

🚨 DESIGN CHANGES AFTER DEVELOPMENT STARTS:
Design changes after estimation approval will require a formal CHANGE REQUEST
and may result in rework (potentially 30-60% of affected components).
```

### Technology Risk Assumption

```markdown
🔧 TECHNOLOGY ASSUMPTIONS

This frontend estimation assumes:

✅ TECHNOLOGY STACK:

- Framework: [Vue 3 / React 18 / etc.] is confirmed
- UI Library: [Vuetify / Material UI / etc.] is approved
- State Management: [Pinia / Redux / etc.] is determined
- Build Tool: [Vite / Webpack / etc.] is configured
- Testing Framework: [Vitest / Jest / etc.] is set up

⚠️ TECHNOLOGY CHANGES:

- Switching frameworks mid-project: +40-60% impact
- Major version upgrades: +15-25% for migration
- New unfamiliar libraries: +20-30% learning curve
```

---

## 🔄 CHANGE REQUEST POLICY

### What Triggers a Change Request

**Scope Changes:**

1. NEW features not in original requirements
2. DESIGN changes after development starts
3. API structure changes affecting frontend
4. Additional user roles or permissions
5. New integrations or third-party services
6. Technology stack changes
7. Performance requirements increase (e.g., 10ms → 100ms)
8. Browser/device support expansion
9. Accessibility level increase (WCAG A → AAA)

### Change Request Template

```markdown
# CHANGE REQUEST: [ID]

**Date:** [YYYY-MM-DD]
**Requested By:** [Name]
**Project:** [Project Name]

## Original Scope

[What was originally estimated]

## Requested Change

[What is being requested]

## Impact Analysis

| Impact Area | Hours Added | Reasoning     |
| ----------- | ----------- | ------------- |
| Development | +XX hr      | [Explanation] |
| Testing     | +XX hr      | [Explanation] |
| Rework      | +XX hr      | [Explanation] |
| **Total**   | **+XX hr**  |               |

## Timeline Impact

- Original deadline: [Date]
- New estimated deadline: [Date]
- Delay: [X weeks]

## Recommendation

[ ] Approve change (+XX hours, +X weeks)
[ ] Defer to Phase 2
[ ] Reject (out of scope)

## Approval

- [ ] Client approved
- [ ] Project lead approved
- [ ] Budget approved
```

---

## 🎯 Estimation Validity & Assumptions

**Every estimation should include:**

### Assumptions Checklist

```markdown
## Assumptions

**Technical:**

- [ ] Framework version specified and stable
- [ ] UI library chosen and approved
- [ ] Browser support defined (e.g., latest 2 versions of Chrome, Firefox, Safari, Edge)
- [ ] No major dependency version conflicts
- [ ] Development environment set up

**Design:**

- [ ] All designs finalized
- [ ] Design system tokens available
- [ ] Asset library provided (icons, images)
- [ ] Responsive breakpoints defined
- [ ] Animation specifications provided

**API:**

- [ ] Backend APIs documented
- [ ] API contracts finalized
- [ ] Test/staging environment available
- [ ] Authentication flow defined
- [ ] Error handling patterns defined

**Team:**

- [ ] Team size confirmed ([N] developers)
- [ ] Skill level: Junior / Mid / Senior
- [ ] Availability: Full-time / Part-time
- [ ] No major team changes expected

**Timeline:**

- [ ] No hard deadlines forcing quality compromises
- [ ] Buffer included for code review
- [ ] QA cycle time allocated
- [ ] Deployment process documented

**Scope:**

- [ ] Requirements frozen (no scope creep)
- [ ] Change request process in place
- [ ] Acceptance criteria defined
- [ ] Definition of Done agreed upon
```

### Estimate Validity Period

```
⏰ ESTIMATE VALIDITY: 30 days from [Date]

After 30 days, this estimate should be reviewed and updated if:
- Requirements have changed
- Technology landscape has shifted
- Team composition has changed
- New information has emerged
- Market conditions have changed
```

---

## 📋 Scope Definition Template

**Use this template at the start of every estimation:**

```markdown
## Frontend Scope Definition

### ✅ IN SCOPE (What we're estimating)

**Pages:**

- [List all pages/routes]

**Components:**

- [List major reusable components]

**Features:**

- [List user-facing features]

**Integrations:**

- [List API integrations, third-party services - UI only]

**Non-Functional:**

- Responsive design (mobile, tablet, desktop)
- Cross-browser compatibility ([List browsers])
- Accessibility ([WCAG level])
- Performance ([Metrics])

### ❌ OUT OF SCOPE (Not estimated)

**Backend:**

- All API development
- Database design and queries
- Server-side business logic
- Authentication logic (server-side)
- Email/notification sending
- File processing logic

**Infrastructure:**

- Server setup and configuration
- CI/CD pipeline setup
- Monitoring and logging setup
- Cloud infrastructure

**Mobile Native:**

- iOS app development
- Android app development
- Native device features

**Other:**

- [Any other exclusions]

### ⚠️ DEPENDENCIES (Required from other teams)

**Design Team:**

- [ ] Complete UI designs (Figma/Sketch)
- [ ] Design system documentation
- [ ] Asset library

**Backend Team:**

- [ ] API documentation (endpoints, schemas)
- [ ] Test environment with mock data
- [ ] Authentication flow documentation

**DevOps Team:**

- [ ] Staging environment
- [ ] Deployment process documentation

**Missing Dependencies Impact:**
Each missing dependency may add +20-35% to the estimate due to rework.
```

---

## 🎓 Training Reference

### How to Identify Frontend vs Backend

**Ask yourself:**

| If the task involves...    | It's Frontend | It's Backend |
| -------------------------- | ------------- | ------------ |
| What users **see**         | ✅            |              |
| What users **click**       | ✅            |              |
| How data is **displayed**  | ✅            |              |
| **Loading/error UI**       | ✅            |              |
| **Client-side validation** | ✅            |              |
| **Server-side validation** |               | ✅           |
| **Database queries**       |               | ✅           |
| **Business calculations**  |               | ✅           |
| **Email sending**          |               | ✅           |
| **File processing**        |               | ✅           |
| **API endpoints**          |               | ✅           |

**Gray Areas (Frontend + Backend):**

| Feature        | Frontend Part                             | Backend Part                                |
| -------------- | ----------------------------------------- | ------------------------------------------- |
| File Upload    | Upload UI, progress bar, preview          | File storage, processing, virus scan        |
| Search         | Search input, results display, filters UI | Database query, indexing, ranking           |
| Authentication | Login form, error messages, redirect      | Token generation, password hashing, session |
| Real-time      | WebSocket client, UI updates              | WebSocket server, message routing           |
| Validation     | Immediate feedback, format check          | Business rules, duplicate check             |

**Rule of Thumb:**
If it runs in the browser → Frontend
If it runs on the server → Backend

---

**END OF MODULE**

**Usage in main agent:**

```
When user asks "What's included?" or scope is unclear:
→ Reference this module, section "Scope Definition Template"

When API/design dependencies unclear:
→ Reference this module, section "Mandatory Dependency Assumptions"
```

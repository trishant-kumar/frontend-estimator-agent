# CRM Dashboard - Frontend Development Estimation

**Date:** 2026-02-24  
**Framework:** Vue 3 + Nuxt 3 + Vuetify  
**Confidence:** 75%

---

## 📋 PROJECT OVERVIEW

### Technical Stack
- **Framework**: Vue 3.4+ with Composition API
- **Meta-Framework**: Nuxt 3 (SSR, auto-routing, optimization)
- **UI Library**: Vuetify 3 (Material Design components)
- **State Management**: Pinia stores
- **Type Safety**: TypeScript 5+
- **Validation**: Zod schemas
- **Testing**: Vitest (unit) + Playwright (E2E)

### Project Scope
- **Type**: New greenfield development
- **Complexity**: Medium-High (RBAC with 5 roles, real-time updates, multi-language)
- **Team Assumption**: 3 senior/mid-level developers (3+ years Vue.js experience)
- **Devices**: Desktop + Tablet + Mobile (responsive)

---

## 📊 MODULE BREAKDOWN

| Module | Features | Base Hours | Notes |
| ------ | -------- | ---------- | ----- |
| **Authentication** | Login, register, forgot password, reset password, OAuth (Google/Microsoft), session management, route guards | 28 hr | JWT tokens, cookie management, auth middleware |
| **Dashboard Overview** | KPI cards (4), line charts (revenue), bar charts (users), pie chart (categories), date range picker, real-time updates via WebSocket | 48 hr | Recharts/Chart.js, WebSocket connection (+15hr for real-time) |
| **User Management** | User table (search, filter, sort, pagination), CRUD forms, role selector (5 roles), bulk actions (delete, export), modal dialogs | 44 hr | CRUD operations, role selector UI (RBAC logic added separately below) |
| **Contact Management** | Contact table, CRUD forms, tags, notes, import CSV, export CSV/PDF, advanced search, filters | 52 hr | File upload for CSV import, field mapping UI |
| **Reports** | Report builder (filters by date, user, status), table view, chart view, export PDF/CSV, save/bookmark reports | 44 hr | Client-side PDF via jsPDF, CSV generation |
| **Settings** | User profile edit, password change, notification preferences, multi-language switcher (EN/ES/FR), theme toggle (light/dark) | 32 hr | i18n setup +15hr for 3 languages, theme system |
| **Notifications** | Toast notifications, notification bell, notification list (mark as read), real-time via WebSocket | 24 hr | Vuetify snackbar, WebSocket listeners |
| **Navigation & Layout** | Responsive sidebar, header with user menu, breadcrumbs, mobile drawer, loading states, error boundaries | 20 hr | Vuetify navigation components, responsive breakpoints |

**Sub-Total (Base Hours)**: 292 hr

**Note:** RBAC complexity is added separately below as it's a cross-cutting concern affecting ALL modules, not just User Management.

---

## ⚙️ STANDARD ADJUSTMENTS

### 📦 What's Included in Base Hours (FREE)

✅ **Professional Development Practices** (built into modern frameworks):
- Component-level testing (Vitest/Jest - fast, 5 min/component)
- TypeScript type safety (compile-time checks prevent bugs)
- Zod validation schemas (reusable, declarative validation)
- Git commits, code reviews (standard team workflow)
- Basic edge case handling (empty states, loading, errors)
- Client-side form validation (Zod schemas - copy from library)
- Responsive layout (CSS Grid/Flexbox - modern baseline)
- Basic error messages (Vuetify toast/snackbar components)
- Loading states, empty states (built into Vuetify components)

✅ **Modern Framework Efficiency**:
- Vuetify UI components (pre-built, tested, accessible - faster than custom)
- Vue Router (standard navigation with auto-imports)
- Pinia stores (boilerplate-free state management)
- Nuxt 3 (auto-routing, built-in optimization, SSR)
- TypeScript + Volar (IntelliSense catches errors instantly)

**Total Overhead: +20%** (vs +50% in older estimates without modern tooling)

---

### 🎯 Applied Multipliers

**Hidden Complexity Additions:**
- **RBAC (5 roles)**: +20 hr (route guards across ALL modules, permission middleware, role-based UI rendering)
- **Real-time (WebSocket)**: +15 hr (connection management, reconnection, state sync for dashboard & notifications)
- **Multi-language (3 languages)**: +15 hr (i18n setup, translation keys, RTL support if needed)

**After Additions**: 292 hr + 50 hr = **342 hr**

**Professional Development Overhead:**
- **Testing + Edge Cases**: +20% → × 1.20
- Unit tests (Vitest) - 10%
- E2E tests (Playwright) - 5%
- Edge case handling - 5%

**After Testing**: 342 hr × 1.20 = **410 hr**

**Confidence Buffer:**
- **Confidence Level**: 75% (good clarity, standard requirements, proven patterns)
- **Buffer**: +10% → × 1.10

**After Buffer**: 410 hr × 1.10 = **451 hr**

**API Setup Overhead:**
- **Scenario**: APIs in parallel development with frontend
- **Overhead**: +8 hr (mock data setup, API integration coordination)

**Grand Total**: 451 hr + 8 hr = **459 hr**

---

## 🎯 TOTAL ESTIMATION

| Category | Hours |
| -------- | ----- |
| **Base Hours** (8 functional modules) | 292 hr |
| **Hidden Complexity** (RBAC 5 roles, real-time, multi-language) | +50 hr |
| **Professional Dev** (+20%: unit tests, E2E tests, edge cases) | +68 hr |
| **Confidence Buffer** (+10%: moderate unknowns, standard patterns) | +41 hr |
| **API Setup** (parallel development, mocks) | +8 hr |
| **Grand Total** | **459 hr** |

**Key Changes from Double-Counting Fix:**
- User Management reduced from 64 hr → 44 hr (removed embedded RBAC)
- RBAC kept as +20 hr cross-cutting addition (affects ALL modules, not just User Mgmt)
- This prevents counting RBAC work twice

---

## 📅 TIMELINE

**With 3 developers:**
- **Total Duration**: ~1.5 months (6.5 weeks)
- **Calculation**: 459 hr ÷ (3 devs × 35 productive hrs/week) = 4.37 weeks × 1.5 buffer = 6.5 weeks
- **Sprints**: 3-4 × 2-week sprints

**Timeline Options:**
- **2 developers**: 2.4 months (11 weeks) - smaller team, longer timeline
- **3 developers**: 1.6 months (7 weeks) ⭐ **RECOMMENDED** - balanced approach
- **4 developers**: 1.2 months (5+ weeks) - faster delivery, coordination overhead
- **5+ developers**: <1 month - diminishing returns, high coordination cost

---

## ⚠️ ASSUMPTIONS & RISKS

### Assumptions

1. **APIs**: Backend APIs documented and available for parallel development (using OpenAPI/Swagger)
2. **UI/UX Designs**: Complete Figma mockups with interactions, states, and responsive breakpoints
3. **Content**: All UI copy, labels, and messages provided by client or placeholder text accepted
4. **Team**: Developers familiar with Vue 3 Composition API, Pinia, and Vuetify 3
5. **Browser Support**: Modern browsers only (Chrome 90+, Firefox 88+, Safari 14+, Edge 90+) - NO IE11
6. **Infrastructure**: Authentication service (JWT tokens), WebSocket server, file storage (S3/CDN) provided by backend team
7. **Third-party Services**: Google/Microsoft OAuth credentials and configuration provided

### Risks

| Risk | Impact | Likelihood | Mitigation |
| ---- | ------ | ---------- | ---------- |
| API delays block frontend | High | Medium | Use mock data (MockService Worker) during development |
| Scope creep (new features mid-sprint) | High | Medium | Strict change request process, defer to Phase 2 |
| Design changes during development | Medium | High | Freeze designs before sprint start, limit revisions |
| WebSocket server instability | Medium | Medium | Build with fallback to polling mechanism |
| RBAC complexity increases | Medium | Low | Define permission matrix upfront, validate in sprint 0 |
| Translation quality/completeness | Low | Medium | Use English keys as fallback, professional translation service |

---

## 🚀 RECOMMENDED APPROACH

### Phase 1: Foundation (Sprint 1-2, ~240 hr)
1. **Sprint 1**: Setup (Nuxt 3, Vuetify, Pinia, i18n, routing), authentication module, navigation layout
2. **Sprint 2**: Dashboard overview, user management (basic CRUD without RBAC)

### Phase 2: Core Features (Sprint 3-4, ~245 hr)
3. **Sprint 3**: Contact management, RBAC implementation (5 roles), real-time notifications
4. **Sprint 4**: Reports module, settings, multi-language, testing, bug fixes

---

## 📋 SCOPE EXCLUSIONS (NOT INCLUDED)

### ❌ Backend & Infrastructure
- API development, database design, business logic
- Server-side authentication/authorization
- Email/SMS sending (backend service)
- File processing (image resize, video encoding)
- Scheduled jobs, cron tasks

### ❌ DevOps & Deployment
- CI/CD pipeline setup (charge +12-16 hr if needed)
- Cloud deployment config (+12-36 hr if needed)
- Monitoring/logging setup (+8-12 hr if needed)

### ❌ Mobile Native Apps
- iOS/Android native apps (requires separate estimate)
- React Native/Flutter (different tech stack)

### ❌ Manual QA & Testing
- Manual QA team time (not developer work)
- Dedicated accessibility audits (charge +50-120 hr for WCAG AA if needed)
- Performance optimization beyond basics (charge per requirement)
- Security penetration testing (not frontend scope)

---

## 📥 EXPORT OPTIONS

### ✅ Available Immediately
- **Markdown (.md)**: This file! Copy to your project documentation
- **CSV (.csv)**: Import module breakdown into Excel/Google Sheets
- **JSON (.json)**: Machine-readable for tools/integrations

### 📄 Manual Conversion (Browser-Based, 1-Click)
1. **Copy** this entire markdown estimation
2. **Open** `docs/estimations/generate-pdf.html` in any browser
3. **Paste** into left panel → Click "Generate Preview" (or Ctrl+Enter)
4. **Click** "Generate PDF" → Save via browser print dialog (Ctrl+P)

**✨ No installation required!** Works offline in Chrome, Firefox, Safari, Edge.

---

## 📝 NEXT STEPS

1. ✅ **Review assumptions** with stakeholders and backend team
2. ✅ **Validate API documentation** availability and completeness
3. ✅ **Confirm design status** (Figma mockups complete? Interactive prototype?)
4. ✅ **Define RBAC permission matrix** (5 roles: what can each role access/edit?)
5. ✅ **Setup development environment** (Nuxt 3, Vuetify, Pinia, mock API)
6. ✅ **Plan sprint 0** (architecture decisions, component library audit, team onboarding)

---

**Prepared by**: Frontend Estimator Agent  
**Date**: 2026-02-24  
**Confidence Level**: 75%  
**Revision**: 1.0

---

## 📞 QUESTIONS OR CHANGES?

If requirements change or you need to adjust scope:
- ➕ **Add features**: Re-run estimation with updated requirements
- ➖ **Remove features**: Clearly mark excluded modules
- 🔄 **Change tech stack**: Specify React/Next.js for re-estimation
- 📊 **Split phases**: Identify MVP vs. Phase 2 features

**Contact me**: `@frontend_estimator [your updated requirements]`

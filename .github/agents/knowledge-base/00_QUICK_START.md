# 🚀 Quick Start Guide - Frontend Estimation

**Purpose:** Get 90% of estimates right in 5 minutes. Use this for standard Vue/React projects.

---

## ⚡ The 5-Step Formula

```
1. List features → Match patterns → Sum BASE hours
2. Apply reusability reduction (25% for similar modules)
3. Add cross-cutting features (RBAC, Real-time, WCAG)
4. Apply multipliers (Design × Testing × Buffer)
5. Validate against sanity checks
```

---

## 📊 Common Pattern Hours (90% Use Cases)

### Authentication & User Management
- **Login/Register page:** 18-22 hrs (forms + validation + API + error handling)
- **Password reset:** 8-12 hrs (email flow + new password form)
- **User profile page:** 12-18 hrs (view + edit + avatar upload)
- **User list (CRUD):** 14-20 hrs (table + filters + create/edit modals)

### Data Display & Management
- **Simple data table:** 8-14 hrs (VDataTable + filters + pagination)
- **Complex data table:** 16-24 hrs (advanced filters + sorting + export + actions)
- **Dashboard:** 60-100 hrs (multiple widgets + charts + filters + responsive)
- **Simple form:** 8-14 hrs (5-10 fields + validation + submit)
- **Complex form:** 18-28 hrs (15+ fields + multi-step + dependent fields)

### Navigation & Layout
- **Sidebar navigation:** 8-12 hrs (menu + routing + responsive + permissions)
- **Top navbar:** 6-10 hrs (logo + menu + user dropdown + notifications)
- **Breadcrumbs:** 3-5 hrs (dynamic routing + click navigation)

### Common Features
- **Search functionality:** 6-10 hrs (input + debounce + API + results)
- **File upload:** 10-16 hrs (drag-drop + preview + validation + progress)
- **Modal/Dialog:** 4-7 hrs (open/close + content + actions)
- **Notifications/Toasts:** 5-8 hrs (success/error/info + auto-dismiss)
- **Settings page:** 12-18 hrs (tabs + forms + save/cancel)

---

## 🎯 Cross-Cutting Features (Add AFTER Base)

### RBAC (Role-Based Access Control)
- **Simple auth checks:** Included in base (no extra cost)
- **Basic RBAC (2-3 roles):** +20 hrs
- **Advanced RBAC (5+ roles, granular):** +60 hrs
- **Enterprise RBAC (hierarchical):** +80 hrs

**When to use:** Requirements mention "admin/user roles", "permissions", "access control"

### Real-Time Features
- **Polling (manual refresh):** Included in base (no extra cost)
- **Simple notifications:** +5-10 hrs (toast on events)
- **Notification center:** +20-30 hrs (UI + history + read/unread)
- **WebSocket full module:** +40 hrs (first module), +20 hrs (additional modules)

**When to use:** Requirements mention "real-time", "live updates", "instant", "WebSocket"

### Accessibility (WCAG)
- **Basic semantic HTML:** Included in base (no extra cost)
- **WCAG 2.1 AA compliance:** +50-80 hrs
- **WCAG 2.1 AAA compliance:** +100-120 hrs

**When to use:** Requirements mention "accessible", "WCAG", "508", "screen reader", "ARIA"

### Third-Party Integrations
- **OAuth (Google/Facebook):** +10-15 hrs
- **Payment (Stripe/PayPal):** +20-30 hrs
- **Maps (Google Maps):** +12-18 hrs
- **Analytics (Google Analytics):** +5-8 hrs
- **Email (SendGrid/Twilio):** +8-12 hrs

---

## 🔧 Standard Multipliers

### 1. Design Completeness Factor (Apply FIRST)
- **Complete designs (Figma/XD):** ×0.75 (25% faster)
- **Wireframes only:** ×0.88 (12% slower)
- **No designs:** ×1.0 (baseline)

### 2. Professional Development Overhead (Apply SECOND)
- **Production-grade (+20%):** ×1.20 (ALWAYS for client work)
  - Includes: Unit tests, E2E tests, edge cases, error handling, code review time

### 3. Confidence Buffer (Apply LAST)
- **High confidence (clear requirements):** ×1.05 (+5%)
- **Medium confidence (standard project):** ×1.10 (+10%) ← **Most common**
- **Low confidence (many unknowns):** ×1.20 (+20%)

**Formula:**
```
TOTAL = (Base × Reusability × Design × Testing × Buffer) + RBAC + Real-time + WCAG + Integrations
```

---

## ✅ Sanity Check Validation

**Per-Component Checks:**
- Login page > 30 hrs → 🚨 TOO HIGH
- CRUD page > 25 hrs → 🚨 TOO HIGH
- Dashboard > 120 hrs → 🚨 TOO HIGH
- Data table > 30 hrs → 🚨 TOO HIGH
- Simple form < 4 hrs → 🚨 TOO LOW
- Complex feature < 10 hrs → 🚨 TOO LOW

**Total Estimate Checks:**
- Average hrs/screen > 40 hrs → 🚨 VERIFY (likely overestimating)
- Average hrs/screen < 8 hrs → 🚨 VERIFY (missing testing/RBAC)
- RBAC > 100 hrs → 🚨 VERIFY (unless 8+ modules)
- Total multiplier > 2.0x → 🚨 VERIFY (check for double-counting)

---

## 🎓 Quick Examples

### Example 1: Simple CRUD App
**Requirements:** User management with login, user list, create/edit users

```
BASE:
- Login page: 20 hrs
- User list (table): 12 hrs
- Create/Edit user (form): 16 hrs
──────────────
Subtotal: 48 hrs

CROSS-CUTTING:
- RBAC: None (single user type)
- Real-time: None
──────────────
Subtotal: 48 hrs

MULTIPLIERS:
× Design (complete Figma): 0.75 = 36 hrs
× Testing (+20%): 1.20 = 43 hrs
× Buffer (high confidence): 1.05 = 45 hrs
──────────────
FINAL: 45 hours (40-50 hrs range)
```

### Example 2: Medium Dashboard Project
**Requirements:** Analytics dashboard with charts, filters, user management, admin/user roles

```
BASE:
- Login/Register: 20 hrs
- Dashboard (4 widgets): 80 hrs
- User management: 18 hrs
- Settings page: 14 hrs
──────────────
Subtotal: 132 hrs

CROSS-CUTTING:
- Basic RBAC (admin/user): +20 hrs
- Real-time: None
──────────────
Subtotal: 152 hrs

MULTIPLIERS:
× Design (wireframes): 0.88 = 134 hrs
× Testing (+20%): 1.20 = 161 hrs
× Buffer (medium confidence): 1.10 = 177 hrs
──────────────
FINAL: 177 hours (165-190 hrs range)
```

### Example 3: Complex Project with Real-Time
**Requirements:** Task management system, 5 modules, real-time notifications, advanced RBAC

```
BASE:
- Authentication: 20 hrs
- Task board (Kanban): 160 hrs
- Project management: 80 hrs
- Team management: 40 hrs
- Reports: 60 hrs
──────────────
Subtotal: 360 hrs

REUSABILITY:
× 0.75 (similar modules): 270 hrs

CROSS-CUTTING:
- Advanced RBAC (5+ roles): +60 hrs
- Real-time notifications: +40 hrs
──────────────
Subtotal: 370 hrs

MULTIPLIERS:
× Design (complete Figma): 0.75 = 278 hrs
× Testing (+20%): 1.20 = 334 hrs
× Buffer (medium confidence): 1.10 = 367 hrs
──────────────
FINAL: 367 hours (340-395 hrs range)
```

---

## 🚨 Common Mistakes to Avoid

❌ **Double-counting responsive design** → It's ALWAYS included in base
❌ **Applying reusability per module** → Apply 25% reduction ONCE across all similar modules
❌ **Adding RBAC when base already has permissions** → Base should be UI only
❌ **Forgetting testing overhead** → ALWAYS +20% for production work
❌ **Using outdated base hours** → These are for 2024+ frameworks (Vuetify/Tailwind)
❌ **Estimating backend work** → Frontend estimates only (exclude API development)

---

## 📚 Need More Detail?

- **Complex RBAC scenarios:** See `01_estimation_methods.md` lines 1023-1100
- **Real-time patterns:** See `01_estimation_methods.md` lines 1110+
- **All common patterns:** See `05_common_patterns.md`
- **Output templates:** See `04_output_templates.md`
- **Full methodology:** See `FRONTEND_ESTIMATOR.agent.md`

---

**Last Updated:** February 2026 | **Version:** 1.0

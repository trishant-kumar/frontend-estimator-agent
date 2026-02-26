# 💼 Worked Examples - Complete Estimation Process

**Purpose:** Step-by-step walkthroughs showing the full estimation process from requirements to final estimate.

---

## Example 1: E-Commerce Product Catalog

### Client Requirements
> "We need a product catalog website where users can browse products, filter by category and price, view product details, and add items to a shopping cart. Users should be able to register, login, and view their order history. Admin users need to manage products (CRUD) and view sales reports."

---

### Step 1: Smart Questions (12-Question Framework)

**Q1: Tech stack?**
Answer: Vue 3 + Vuetify + TypeScript

**Q2: Design assets?**
Answer: Complete Figma designs with design system

**Q3: Scope?**
Answer: Frontend only (API already exists)

**Q4: Pages/features list?**
- Product listing page with filters
- Product detail page
- Shopping cart
- User registration/login
- User profile + order history
- Admin: Product CRUD
- Admin: Sales reports dashboard

**Q5: Complexity level?**
- Product listing: Medium (filters, pagination, API)
- Product detail: Simple (display + add to cart)
- Cart: Medium (add/remove, quantity, total calculation)
- Auth: Simple (standard login/register)
- Profile: Simple (view + edit basic info)
- Order history: Simple (table with past orders)
- Product CRUD: Medium (form with images)
- Sales reports: Medium (charts + date filters)

**Q6: RBAC?**
Answer: Yes - Basic RBAC with 2 roles (customer, admin)

**Q7: Component reusability?**
Answer: 40% similarity (product cards, forms reused across 3+ pages)

**Q8: Confidence level?**
- Complete designs: ✅
- API documentation: ✅
- Requirements clear: ✅
- Tech stack proven: ✅
- Team experienced: ✅
→ **HIGH CONFIDENCE** (×1.05 buffer)

**Q9: Testing requirements?**
Answer: Yes, production-grade (unit + E2E tests required)

**Q10: Real-time features?**
Answer: No real-time needed

**Q11: WCAG compliance?**
Answer: Basic semantic HTML only (no WCAG AA/AAA)

**Q12: Third-party integrations?**
Answer: None (payment handled by backend)

---

### Step 2: Base Hours Calculation

| Feature | Complexity | Base Hours | Reasoning |
|---------|-----------|------------|-----------|
| Product listing page | Medium | 28 hrs | VDataTable (10) + Filters (8) + Pagination (4) + API (6) |
| Product detail page | Simple | 16 hrs | Layout (6) + Image gallery (6) + Add to cart (4) |
| Shopping cart | Medium | 22 hrs | Cart UI (8) + Quantity controls (6) + Total calc (4) + Checkout button (4) |
| Login/Register | Standard | 20 hrs | 2 forms (10) + Validation (4) + API (4) + Error handling (2) |
| User profile | Simple | 14 hrs | Display (4) + Edit form (6) + API (4) |
| Order history | Simple | 12 hrs | VDataTable (8) + Date filters (4) |
| Product CRUD (Admin) | Medium | 32 hrs | Table (10) + Create form (10) + Edit (6) + Delete (2) + Image upload (4) |
| Sales reports (Admin) | Medium | 28 hrs | Charts (12) + Date filters (8) + Export (4) + API (4) |

**Subtotal:** 172 hrs

---

### Step 3: Apply Reusability Reduction

**Analysis:**
- Product card component used in: listing, search results, related products (3 places)
- Forms pattern used in: login, register, profile, product CRUD (4 places)
- VDataTable used in: product listing, order history, product CRUD (3 places)
- Filter components reused across 2+ pages

**Similarity:** 40% of components are reusable
**Reduction:** 25% (standard for medium reusability)

```
172 hrs × 0.75 = 129 hrs
```

---

### Step 4: Add Cross-Cutting Features

**RBAC (Basic - 2 roles):**
- Permission composable: 4 hrs
- Route guards (admin pages): 6 hrs
- UI conditionals (hide admin menu for customers): 6 hrs
- Testing: 2 hrs
**Total RBAC:** +18 hrs (rounded from standard +20 hrs, adjusted for small app)

**Real-time:** None (+0 hrs)

**WCAG:** None (+0 hrs)

**Integrations:** None (+0 hrs)

```
129 hrs + 18 hrs RBAC = 147 hrs
```

---

### Step 5: Apply Multipliers

**1. Design Completeness Factor:**
Complete Figma designs = ×0.75

```
147 hrs × 0.75 = 110 hrs
```

**2. Professional Development (+20% testing):**
Production-grade = ×1.20

```
110 hrs × 1.20 = 132 hrs
```

**3. Confidence Buffer:**
High confidence (all boxes checked) = ×1.05

```
132 hrs × 1.05 = 139 hrs
```

---

### Step 6: Sanity Check Validation

✅ Product listing (28 hrs) < 30 hrs → PASS
✅ Product detail (16 hrs) within typical range → PASS
✅ Cart (22 hrs) < 25 hrs → PASS
✅ Login (20 hrs) < 30 hrs → PASS
✅ Product CRUD (32 hrs) > 25 hrs but justified (includes image upload) → PASS
✅ Average hrs/screen = 139 hrs ÷ 8 screens = 17.4 hrs/screen → PASS
✅ RBAC (18 hrs) < 100 hrs → PASS
✅ Total multiplier = (0.75 × 0.75 × 1.20 × 1.05) = 0.71x from initial base → PASS

**All checks passed!**

---

### Final Estimate

**Base Hours (before reductions):** 172 hrs
**After Reusability (×0.75):** 129 hrs
**After RBAC (+18 hrs):** 147 hrs
**After Design (×0.75):** 110 hrs
**After Testing (×1.20):** 132 hrs
**After Buffer (×1.05):** 139 hrs

**FINAL ESTIMATE: 139 hours**
**Range (±10%):** 125-153 hours
**Recommended:** 140 hours (rounded)

---

## Example 2: Internal HR Management System

### Client Requirements
> "We need an internal HR system for managing employees, departments, leave requests, and performance reviews. The system needs 5 user roles: Employee, Manager, HR Admin, Department Head, and Super Admin. Real-time notifications for leave approvals are required. The system should support 15 departments with ~200 employees."

---

### Step 1: Smart Questions

**Q1: Tech stack?**
Answer: React + Material-UI + TypeScript

**Q2: Design assets?**
Answer: Wireframes only (no design system)

**Q3: Scope?**
Answer: Frontend + API integration (backend team building in parallel)

**Q4: Pages/features list?**
- Dashboard (different views for each role)
- Employee directory (search, filter by department)
- Employee profile (view + edit)
- Leave request system (request, approve, calendar view)
- Performance review system (create, submit, view history)
- Department management
- Reporting (attendance, leave analytics)

**Q5: Complexity level?**
- Dashboard: High (role-based widgets, 5 different views)
- Employee directory: Medium (search, advanced filters, export)
- Employee profile: Medium (complex form with 20+ fields)
- Leave requests: High (calendar view, approval workflow, notifications)
- Performance reviews: High (multi-step form, rating system, comments)
- Department management: Simple (CRUD)
- Reporting: Medium (charts, date filters)

**Q6: RBAC?**
Answer: Yes - Advanced RBAC with 5 roles and hierarchical permissions

**Q7: Component reusability?**
Answer: 35% similarity (forms, tables, modals reused)

**Q8: Confidence level?**
- Wireframes only (no complete designs): ❌
- API in parallel (not ready): ⚠️
- Requirements detailed: ✅
- Tech stack proven: ✅
- Complex RBAC (first time): ⚠️
→ **MEDIUM CONFIDENCE** (×1.10 buffer)

**Q9: Testing requirements?**
Answer: Yes, production-grade

**Q10: Real-time features?**
Answer: Yes - Real-time notifications for leave approvals and system announcements

**Q11: WCAG compliance?**
Answer: No (internal tool)

**Q12: Third-party integrations?**
Answer: Google Calendar integration for leave sync

---

### Step 2: Base Hours Calculation

| Feature | Complexity | Base Hours |
|---------|-----------|------------|
| Dashboard (5 role variants) | High | 140 hrs |
| Employee directory | Medium | 32 hrs |
| Employee profile | Medium | 28 hrs |
| Leave request UI | High | 60 hrs |
| Leave calendar view | High | 44 hrs |
| Leave approval workflow | High | 36 hrs |
| Performance review creation | High | 52 hrs |
| Performance review viewing | Medium | 24 hrs |
| Department CRUD | Simple | 18 hrs |
| Reporting dashboard | Medium | 36 hrs |
| Notification UI | Medium | 16 hrs |

**Subtotal:** 486 hrs

---

### Step 3: Apply Reusability Reduction

Similar modules share form patterns, table layouts, modal structures.
Reusability: 35% but only first occurrence, then 25% reduction for similar modules.

```
486 hrs × 0.75 = 365 hrs
```

---

### Step 4: Add Cross-Cutting Features

**RBAC (Advanced - 5 roles, hierarchical):**
- Role/permission CRUD: 12 hrs
- Permission matrix UI: 8 hrs
- Hierarchical permission logic: 8 hrs
- usePermissions composable: 8 hrs
- Route guards (30+ routes): 8 hrs
- UI conditionals (40+ components): 12 hrs
- Testing: 4 hrs
**Total RBAC:** +60 hrs

**Real-time (Notification center):**
- WebSocket setup: 8 hrs
- Notification center UI: 12 hrs
- Real-time event routing: 8 hrs
- Badge counters: 4 hrs
- Testing: 4 hrs
**Total Real-time:** +36 hrs

**WCAG:** None (+0 hrs)

**Integrations (Google Calendar):**
- OAuth setup: 8 hrs
- Calendar sync logic: 10 hrs
- UI integration: 6 hrs
- Testing: 4 hrs
**Total Integrations:** +28 hrs

```
365 hrs + 60 hrs RBAC + 36 hrs Real-time + 28 hrs Integrations = 489 hrs
```

---

### Step 5: Apply Multipliers

**1. Design Completeness Factor:**
Wireframes only = ×0.88

```
489 hrs × 0.88 = 430 hrs
```

**2. Professional Development (+20% testing):**
Production-grade = ×1.20

```
430 hrs × 1.20 = 516 hrs
```

**3. Confidence Buffer:**
Medium confidence = ×1.10

```
516 hrs × 1.10 = 568 hrs
```

---

### Step 6: Sanity Check Validation

✅ Dashboard (140 hrs) > 120 hrs → ⚠️ VERIFY: Justified (5 different role views × 28 hrs each = 140 hrs reasonable)
✅ Leave system total (140 hrs) → PASS (complex workflow justifies high hours)
✅ Average hrs/screen = 568 hrs ÷ 11 features = 52 hrs/feature → ⚠️ SLIGHTLY HIGH but acceptable for complex system
✅ RBAC (60 hrs) < 100 hrs → PASS (standard for advanced RBAC)
✅ Real-time (36 hrs) < 60 hrs → PASS
✅ Integrations (28 hrs) reasonable for Google Calendar → PASS

**All checks passed with justified high complexity!**

---

### Final Estimate

**Base Hours (before reductions):** 486 hrs
**After Reusability (×0.75):** 365 hrs
**After Cross-cutting (+124 hrs):** 489 hrs
**After Design (×0.88):** 430 hrs
**After Testing (×1.20):** 516 hrs
**After Buffer (×1.10):** 568 hrs

**FINAL ESTIMATE: 568 hours**
**Range (±12%):** 500-636 hours
**Recommended:** 570 hours (rounded)

**Timeline (2 developers):** ~14-15 weeks
**Timeline (3 developers):** ~10-11 weeks

---

## Example 3: Simple Landing Page + Form

### Client Requirements
> "We need a marketing landing page with a hero section, features section, pricing table, and a contact form. It should be responsive and work on all modern browsers."

---

### Step 1: Smart Questions

**Q1: Tech stack?**
Answer: Vue 3 + Tailwind CSS

**Q2: Design assets?**
Answer: Complete Figma designs

**Q3: Scope?**
Answer: Single landing page (no backend, form submits to third-party API)

**Q4: Pages/features list?**
- Hero section (headline, subheadline, CTA button)
- Features section (3-column grid)
- Pricing table (3 tiers)
- Contact form (name, email, message, submit)
- Footer

**Q5: Complexity level?**
All sections are Simple (static content + one form)

**Q6: RBAC?**
Answer: No (public page)

**Q7: Component reusability?**
Answer: Minimal (single page, few components)

**Q8: Confidence level?**
All requirements clear, simple project → **HIGH CONFIDENCE** (×1.05)

**Q9: Testing requirements?**
Answer: Yes, production-grade

**Q10-12: No additional features**

---

### Step 2: Base Hours Calculation

| Feature | Base Hours |
|---------|------------|
| Hero section | 6 hrs |
| Features section | 8 hrs |
| Pricing table | 10 hrs |
| Contact form | 12 hrs |
| Footer | 4 hrs |
| Responsive layout | Included |
| API integration (form) | Included |

**Subtotal:** 40 hrs

---

### Step 3: Apply Multipliers

No reusability reduction (single page).
No cross-cutting features.

**1. Design (complete):** 40 hrs × 0.75 = 30 hrs
**2. Testing (+20%):** 30 hrs × 1.20 = 36 hrs
**3. Buffer (high confidence):** 36 hrs × 1.05 = 38 hrs

---

### Final Estimate

**FINAL ESTIMATE: 38 hours**
**Range (±10%):** 34-42 hours
**Recommended:** 40 hours (rounded)

**Timeline:** ~1 week (1 developer)

---

## Key Takeaways

1. **Always start with smart questions** - Missing RBAC or real-time can add 50-100 hrs
2. **Validate base hours** - Use pattern libraries as reference (don't guess)
3. **Apply reusability carefully** - Only when 40%+ similarity exists
4. **Cross-cutting features are ADDITIVE** - Never multiply RBAC or real-time
5. **Sanity check every estimate** - Catch errors before sending to client
6. **Provide ranges** - Gives client flexibility and sets expectations

---

**Last Updated:** February 2026 | **Version:** 1.0

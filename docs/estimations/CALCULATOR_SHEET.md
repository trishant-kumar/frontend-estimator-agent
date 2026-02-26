# Estimation Calculator Sheet

**Project Name:** \***\*\*\*\*\***\*\*\***\*\*\*\*\***\_\_\_\***\*\*\*\*\***\*\*\***\*\*\*\*\***  
**Client:** \***\*\*\*\*\***\*\*\***\*\*\*\*\***\_\_\_\***\*\*\*\*\***\*\*\***\*\*\*\*\***  
**Estimator:** \***\*\*\*\*\***\*\*\***\*\*\*\*\***\_\_\_\***\*\*\*\*\***\*\*\***\*\*\*\*\***  
**Date:** \***\*\*\*\*\***\*\*\***\*\*\*\*\***\_\_\_\***\*\*\*\*\***\*\*\***\*\*\*\*\***

**Purpose:** Step-by-step worksheet for consistent and transparent estimation

**Key Features:** Optimized base hours, Combined testing+edges (+20%), Comprehensive complexity coverage, Buffer includes rework

---

## 📊 QUICK REFERENCE: 12-QUESTION ESTIMATION

**Complete ALL 12 questions, then calculate hours step-by-step.**

---

## STEP 1: ANSWER 12 QUESTIONS

### Q1: Design Assets (Check ALL that apply)

**Complete Designs:**

- [ ] Complete designs (Figma/XD) → Factor: **0.75**
- [ ] Wireframes only → Factor: **0.88**
- [ ] NO designs (build from scratch) → Factor: **1.00** ✓ Default

**Additional Assets (can combine):**

- [ ] Design system available → Additional Factor: **0.85**
- [ ] UX documentation provided → Additional Factor: **0.92**
- [ ] Content ready → Additional Factor: **0.93**

**Your Factors:** \_\_\_\_ × \_\_\_\_ × \_\_\_\_ × \_\_\_\_ = **\_\_\_\_** (combined)

---

### Q2: Device Support

- [ ] Desktop only → Factor: **0.85**
- [ ] Desktop + Tablet + Mobile → Factor: **1.00** ✓ Default

**Selected Factor:** **\_\_\_\_**

**Note:** Responsive design for multi-device is INCLUDED in base hours.

---

### Q3: Browser Support

- [ ] Modern browsers only → Factor: **1.00** ✓ Default
- [ ] Include IE11 → Factor: **1.50** ⚠️ Strongly discourage

**Selected Factor:** **\_\_\_\_**

---

### Q4: Multi-Language Support

- [ ] Single language → Factor: **1.00** ✓ Default
- [ ] 2+ languages (i18n) → Factor: **1.15**

**Selected Factor:** **\_\_\_\_**

---

### Q5: API Readiness

- [ ] APIs ready with docs → Hours: **0** ✓ Default
- [ ] Parallel development (mock setup) → Hours: **8**
- [ ] Frontend first (full mocks) → Hours: **16**

**Additional Hours:** **\_\_\_\_**

**Note:** API integration (loading/error states) is INCLUDED in base hours.

---

### Q6: Professional Development Overhead

- [ ] Quick prototype (no testing) → Factor: **1.00** (not recommended)
- [ ] Production-grade (testing + edge cases) → Factor: **1.20** ✓ Recommended

**Selected Factor:** **\_\_\_\_**

**Includes:** Unit tests (10%), E2E tests (5%), edge case handling (5%)

---

### Q7: Component Reusability

- [ ] 3+ similar modules → **25% reduction** on 2nd+ modules
- [ ] 2 similar modules → **20% reduction** on 2nd module
- [ ] All unique → **No reduction**

**Reusability:** **\_\_\_\_\_\_\_\_\_\_\_\_\_\_**

---

### Q8: Confidence Level (Calculate score)

**Score Factors:**

- ✅ Complete designs: +10
- ✅ API docs ready: +8
- ✅ Clear requirements: +10
- ✅ Similar past project: +12
- ❌ Complex integrations: -10
- ❌ New technology: -15
- ❌ Unclear requirements: -20

**Your Score:** \_\_\_\_\_ points

**Confidence Mapping (includes rework):**

- [ ] 85-100 points = 90% → Buffer: **1.05** (+5%) (high confidence)
- [ ] 65-84 points = 75% → Buffer: **1.10** (+10%) ✓ Common (most cases)
- [ ] 45-64 points = 60% → Buffer: **1.20** (+20%) (significant unknowns)
- [ ] <45 points → **Discovery phase recommended**

**Selected Buffer:** **\_\_\_\_**

**Includes:** Code review fixes, QA bugs, stakeholder feedback, integration surprises

---

### Q9: RBAC Complexity

- [ ] No RBAC → Hours: **0** ✓ Default
- [ ] Basic (2-3 roles, show/hide) → Hours: **20**
- [ ] Advanced (4-6 roles, permissions UI) → Hours: **60**
- [ ] Enterprise (dynamic roles, audit logs) → Hours: **80**

**Additional Hours:** **\_\_\_\_**

---

### Q10: Real-Time Updates

- [ ] No real-time → Hours: **0** ✓ Default
- [ ] Polling (1-2 modules) → Hours: **5 per module** = \_\_\_\_
- [ ] WebSocket (first module) → Hours: **40**
- [ ] WebSocket (each additional) → Hours: **20 each** × \_\_ = \_\_\_\_

**Additional Hours:** **\_\_\_\_**

---

### Q11: WCAG Accessibility

- [ ] Basic (semantic HTML) → Hours: **0** ✓ Default (included)
- [ ] WCAG AA compliance → Hours: **50**
- [ ] WCAG AAA compliance → Hours: **120**

**Additional Hours:** **\_\_\_\_**

---

### Q12: Third-Party Integrations

**Check ALL that apply:**

| Integration  | Hours Each | Count | Subtotal |
| ------------ | ---------- | ----- | -------- |
| OAuth/SSO    | 10         | \_    | \_\_\_   |
| Payments     | 25         | \_    | \_\_\_   |
| Maps         | 15         | \_    | \_\_\_   |
| Analytics    | 8          | \_    | \_\_\_   |
| File Storage | 12         | \_    | \_\_\_   |
| Email        | 6          | \_    | \_\_\_   |
| SMS          | 8          | \_    | \_\_\_   |
| Video        | 35         | \_    | \_\_\_   |
| Search       | 20         | \_    | \_\_\_   |
| CMS          | 15         | \_    | \_\_\_   |
| Other        | \_         | \_    | \_\_\_   |

**Total Integration Hours:** **\_\_\_\_**

---

## STEP 2: LIST MODULES & CALCULATE BASE HOURS

**⚠️ IMPORTANT: Base hours INCLUDE responsive design and API integration!**

| #   | Module Name | Complexity | Hours | Notes |
| --- | ----------- | ---------- | ----- | ----- |
| 1   |             | L / M / H  |       |       |
| 2   |             | L / M / H  |       |       |
| 3   |             | L / M / H  |       |       |
| 4   |             | L / M / H  |       |       |
| 5   |             | L / M / H  |       |       |
| 6   |             | L / M / H  |       |       |
| 7   |             | L / M / H  |       |       |
| 8   |             | L / M / H  |       |       |
| 9   |             | L / M / H  |       |       |
| 10  |             | L / M / H  |       |       |

**Complexity Reference:**

- **L** (Low): 20-40 hrs - Simple CRUD, lists, static pages (includes validation, API, loading states)
- **M** (Medium): 60-120 hrs - Tables, multi-step forms, dashboards (includes sorting, pagination, filters)
- **H** (High): 140-300 hrs - Complex workflows, visualizations, real-time (includes advanced interactions)

**TOTAL BASE HOURS:** **\*\***\_\_\_\_**\*\*** (Responsive + API integration INCLUDED)

---

## STEP 3: APPLY REUSABILITY (Q7)

**If 3+ similar modules (25% reusability reduction):**

| Module           | Calculation       | Hours    |
| ---------------- | ----------------- | -------- |
| Module 1 (first) | Full hours × 1.00 | \_\_\_\_ |
| Module 2         | Hours × 0.75      | \_\_\_\_ |
| Module 3         | Hours × 0.75      | \_\_\_\_ |
| Module 4+        | Hours × 0.75 each | \_\_\_\_ |

**If 2 similar modules:**

| Module           | Calculation       | Hours    |
| ---------------- | ----------------- | -------- |
| Module 1 (first) | Full hours × 1.00 | \_\_\_\_ |
| Module 2         | Hours × 0.80      | \_\_\_\_ |

**If all unique:** Use base hours (no adjustment)

**ADJUSTED BASE HOURS:** **\*\***\_\_\_\_**\*\***

---

## STEP 4: APPLY ADJUSTMENTS SEQUENTIALLY

### A. Design Assets (Q1)

**Start:** \_\_\_\_\_ hrs

**Apply factors multiplicatively:**

```
After Complete Designs (0.75): _____ × 0.75 = _____ hrs
After Design System (0.85):    _____ × 0.85 = _____ hrs
After UX Docs (0.92):           _____ × 0.92 = _____ hrs
After Content (0.93):           _____ × 0.93 = _____ hrs
```

**Result after Design Assets:** **\*\***\_\_\_\_**\*\*** hrs

---

### B. Device Support (Q2)

| Calculation                | Result                                   |
| -------------------------- | ---------------------------------------- |
| Prev. result × (Q2 factor) | \_\_\_\_\_ × \_\_\_\_\_ = \_\_\_\_\_ hrs |

**Result after Device Support:** **\*\***\_\_\_\_**\*\*** hrs

---

### C. Browser Support (Q3)

| Calculation                | Result                                   |
| -------------------------- | ---------------------------------------- |
| Prev. result × (Q3 factor) | \_\_\_\_\_ × \_\_\_\_\_ = \_\_\_\_\_ hrs |

**Result after Browser Support:** **\*\***\_\_\_\_**\*\*** hrs

---

### D. Multi-Language (Q4)

| Calculation                | Result                                   |
| -------------------------- | ---------------------------------------- |
| Prev. result × (Q4 factor) | \_\_\_\_\_ × \_\_\_\_\_ = \_\_\_\_\_ hrs |

**Result after Multi-Language:** **\*\***\_\_\_\_**\*\*** hrs

---

### E. API Setup (Q5)

| Calculation               | Result                                   |
| ------------------------- | ---------------------------------------- |
| Prev. result + (Q5 hours) | \_\_\_\_\_ + \_\_\_\_\_ = \_\_\_\_\_ hrs |

**Result after API Setup:** **\*\***\_\_\_\_**\*\*** hrs

---

### F. Professional Development (Q6)

| Calculation                | Result                                   |
| -------------------------- | ---------------------------------------- |
| Prev. result × (Q6 factor) | \_\_\_\_\_ × \_\_\_\_\_ = \_\_\_\_\_ hrs |

**Result after Professional Dev:** **\*\***\_\_\_\_**\*\*** hrs

---

### G. Add RBAC Hours (Q9)

| Calculation               | Result                                   |
| ------------------------- | ---------------------------------------- |
| Prev. result + (Q9 hours) | \_\_\_\_\_ + \_\_\_\_\_ = \_\_\_\_\_ hrs |

**Result after RBAC:** **\*\***\_\_\_\_**\*\*** hrs

---

### H. Add Real-Time Hours (Q10)

| Calculation                | Result                                   |
| -------------------------- | ---------------------------------------- |
| Prev. result + (Q10 hours) | \_\_\_\_\_ + \_\_\_\_\_ = \_\_\_\_\_ hrs |

**Result after Real-Time:** **\*\***\_\_\_\_**\*\*** hrs

---

### I. Add WCAG Hours (Q11)

| Calculation                | Result                                   |
| -------------------------- | ---------------------------------------- |
| Prev. result + (Q11 hours) | \_\_\_\_\_ + \_\_\_\_\_ = \_\_\_\_\_ hrs |

**Result after WCAG:** **\*\***\_\_\_\_**\*\*** hrs

---

### J. Add Integration Hours (Q12)

| Calculation                | Result                                   |
| -------------------------- | ---------------------------------------- |
| Prev. result + (Q12 hours) | \_\_\_\_\_ + \_\_\_\_\_ = \_\_\_\_\_ hrs |

**Result after Integrations:** **\*\***\_\_\_\_**\*\*** hrs

---

### K. Confidence Buffer (Q8)

| Calculation                | Result                                   |
| -------------------------- | ---------------------------------------- |
| Prev. result × (Q8 buffer) | \_\_\_\_\_ × \_\_\_\_\_ = \_\_\_\_\_ hrs |

**Result after Buffer:** **\*\***\_\_\_\_**\*\*** hrs

---

### L. Round to Nearest Half-Day

**Formula:** Round up to nearest 4 hours

**Raw:** \_\_\_\_\_ hrs → **Rounded:** **\*\***\_\_\_\_**\*\*** hrs

---

## STEP 5: FINAL TOTAL

```
┌────────────────────────────────────────────────────────────┐
│                                                            │
│  💰 TOTAL ESTIMATED HOURS:  _________ hours                │
│                                                            │
└────────────────────────────────────────────────────────────┘
```

---

## STEP 6: CALCULATE TIMELINE

### Team Efficiency Formula

**Monthly Hours Per Developer:** 6 hrs/day × 22 days × 0.75 efficiency = **99 hrs/mo**

| Team Size        | Hours/Month | Your Timeline                   |
| ---------------- | ----------- | ------------------------------- |
| **2 developers** | 198 hrs/mo  | \_\_\_\_ ÷ 198 = \_\_\_\_ mo    |
| **3 developers** | 297 hrs/mo  | \_\_\_\_ ÷ 297 = \_\_\_\_ mo    |
| **4 developers** | 396 hrs/mo  | \_\_\_\_ ÷ 396 = \_\_\_\_ mo ⭐ |
| **5 developers** | 495 hrs/mo  | \_\_\_\_ ÷ 495 = \_\_\_\_ mo    |
| **6 developers** | 594 hrs/mo  | \_\_\_\_ ÷ 594 = \_\_\_\_ mo    |

**RECOMMENDED:** **\_\_\_\_** developers for **\_\_\_\_** months

---

## STEP 7: DELIVERABLES CHECKLIST

### ✅ INCLUDED (Frontend Only)

**Code:**

- [ ] Production-ready Vue 3/React 18 app
- [ ] **\_\_\_\_** reusable components
- [ ] **\_\_\_\_** pages/screens
- [ ] State management (Pinia/Redux)
- [ ] Form validation (Zod/Yup)
- [ ] TypeScript interfaces
- [ ] Responsive layouts (Q2)
- [ ] Multi-language (if Q4)
- [ ] Automated tests (if Q6)

**Documentation:**

- [ ] Setup guide
- [ ] API integration docs
- [ ] Component docs
- [ ] Deployment instructions

**Professional Practices (in base hours):**

- ✅ Form validation, error handling
- ✅ Loading states, empty states
- ✅ API integration (fetch/display)
- ✅ Responsive design
- ✅ Search, pagination, sorting
- ✅ Route guards, basic permissions
- ✅ Basic accessibility (semantic HTML)

**Explicit Complexity Requirements:**

- [ ] RBAC implementation (Q9): \_\_\_\_ hrs
- [ ] Real-time updates (Q10): \_\_\_\_ hrs
- [ ] WCAG compliance (Q11): \_\_\_\_ hrs
- [ ] Third-party integrations (Q12): \_\_\_\_ hrs

---

### ❌ EXCLUDED (Not Frontend)

- ❌ Backend API development
- ❌ Database design
- ❌ Server-side logic
- ❌ Authentication logic (JWT)
- ❌ Email/SMS backend
- ❌ CI/CD setup
- ❌ Cloud deployment
- ❌ Mobile native apps

---

## STEP 8: CONFIDENCE & ASSUMPTIONS

### Confidence Level: \_\_\_\_% (from Q8)

**Key Assumptions:**

1. Framework: Vue 3.4+ / React 18+ with TypeScript
2. Component library: Vuetify 3 / Material-UI / Tailwind UI
3. Team: **\_\_\_\_** senior/mid developers (3+ years)
4. API status: **\_\_\_\_** (Q5)
5. Design delivery: **\_\_\_\_** (Q1)
6. Requirements: **\_\_\_\_** (Clear / Unclear)
7. Responsive design: **Included in base hours**
8. API integration: **Included in base hours**

**Additional:**

- ***
- ***

---

### Risks & Mitigation

| Risk           | Impact | Mitigation                       |
| -------------- | ------ | -------------------------------- |
| API delays     | High   | Use mock data during development |
| Design changes | Medium | Change request process           |
| Scope creep    | High   | Formal approval for new features |
| \*\*\*         | \*\*\* | \*\*\*                           |

---

## STEP 9: FINAL SUMMARY BOX

```
┌────────────────────────────────────────────────────────────┐
│                                                            │
│  PROJECT:   _________________________________________      │
│                                                            │
│  💰 HOURS:      _________ hours                            │
│  📅 TIMELINE:   _________ months                           │
│  👥 TEAM:       _________ developers                       │
│  🎯 CONFIDENCE:  _________% │
│                                                            │
│  Prepared by: _______________    Date: ___________        │
│                                                            │
└────────────────────────────────────────────────────────────┘
```

---

## ✅ CHECKLIST BEFORE SENDING

- [ ] All 12 questions answered
- [ ] Base hours calculated per module
- [ ] Reusability applied (Q7)
- [ ] All adjustments applied sequentially (A-L)
- [ ] RBAC hours added (Q9)
- [ ] Real-time hours added (Q10)
- [ ] WCAG hours added (Q11)
- [ ] Integration hours added (Q12)
- [ ] Timeline calculated
- [ ] Deliverables listed
- [ ] Exclusions stated
- [ ] Assumptions documented
- [ ] Confidence level assigned
- [ ] Reviewed by senior developer

---

## 📊 QUICK COMPARISON (300 base hrs)

| Scenario                    | Result  |
| --------------------------- | ------- |
| **Best Case**               | 283 hrs |
| **Standard**                | 348 hrs |
| **Full Build**              | 685 hrs |
| **With RBAC + Real-time**   | 448 hrs |

---

## 📋 FORMULA REFERENCE

```typescript
// Complete estimation formula
final =
  (baseHours *              // Optimized for modern frameworks
    reusabilityFactor *     // 0.75-1.0 (Q7) - max 25% reduction
    designFactor *          // 0.75-1.0 (Q1)
    deviceFactor *          // 0.85-1.0 (Q2)
    browserFactor *         // 1.0-1.5 (Q3)
    i18nFactor +            // 1.0-1.15 (Q4)
  apiSetupHours) *          // 0-16 hrs (Q5)
  professionalDevFactor +   // 1.20 (Q6) - testing + edge cases
  rbacHours +               // 0-80 hrs (Q9) - role-based access
  realTimeHours +           // 0-XX hrs (Q10) - real-time updates
  wcagHours +               // 0-120 hrs (Q11) - accessibility
  integrationHours) *       // 0-XX hrs (Q12) - third-party services
  bufferFactor;             // 1.05-1.20 (Q8) - confidence buffer

roundedFinal = Math.ceil(final / 4) * 4;
```

```typescript
finalEstimate =
  baseHours * // Step 2 (responsive INCLUDED)
    reusabilityFactor * // Step 3: 0.65-1.0
    designFactor * // Step 4A: 0.75-1.0 (additive)
    deviceFactor * // Step 4B: 0.85-1.0
    browserFactor * // Step 4C: 1.0-1.5
    i18nFactor * // Step 4D: 1.0-1.15
    testingMultiplier * // Step 4F: 1.15
    bufferMultiplier + // Step 4G: 1.05-1.20
  apiSetupHours; // Step 4E: 0-16 hrs

roundedEstimate = Math.ceil(finalEstimate / 4) * 4;
```

---

**Estimated By:** \***\*\*\*\*\***\*\*\***\*\*\*\*\***\_\_\_\***\*\*\*\*\***\*\*\***\*\*\*\*\***  
**Reviewed By:** \***\*\*\*\*\***\*\*\***\*\*\*\*\***\_\_\_\***\*\*\*\*\***\*\*\***\*\*\*\*\***  
**Date:** \***\*\*\*\*\***\*\*\***\*\*\*\*\***\_\_\_\***\*\*\*\*\***\*\*\***\*\*\*\*\***

**Save this completed sheet for project records**

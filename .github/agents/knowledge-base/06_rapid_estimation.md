---
Module: Rapid Estimation Techniques
Version: 1.0
Last Updated: 2026-02-23
Purpose: Fast estimation methods for quick turnaround (5-30 minutes)
---

# ⚡ Rapid Estimation Module

**Use these methods when time is limited or requirements are early-stage.**

---

## 🎯 Method Selection Guide

| Time Available | Method           | Accuracy | Best For                  |
| -------------- | ---------------- | -------- | ------------------------- |
| **5-10 min**   | T-Shirt Sizing   | ±50%     | Initial calls, ballpark   |
| **10-20 min**  | Story Points     | ±30%     | Agile teams with velocity |
| **20-30 min**  | Pattern Matching | ±25%     | Similar to past work      |
| **30-45 min**  | Component Count  | ±25%     | Have component list       |
| **45-60 min**  | Hybrid Approach  | ±20%     | ⭐ Best balance           |

---

## 1️⃣ T-SHIRT SIZING (Fastest - 5-10 minutes)

**Use when:** Initial concept, ballpark needed, discovery phase, unclear requirements

### Feature-Level Sizing (AGGRESSIVE MODE)

| Size    | Hours    | Description       | Examples                                                      |
| ------- | -------- | ----------------- | ------------------------------------------------------------- |
| **XS**  | 3-6 hr   | Trivial component | Button, badge, icon, simple text input                        |
| **S**   | 6-12 hr  | Simple feature    | Basic form (3-5 fields), card, list item                      |
| **M**   | 12-24 hr | Standard feature  | CRUD page, search with 3-5 filters, simple dashboard          |
| **L**   | 24-48 hr | Complex feature   | Multi-tab interface, workflow (3-5 steps), advanced dashboard |
| **XL**  | 48-96 hr | Major module      | Admin panel, user management system, reporting dashboard      |
| **XXL** | 96+ hr   | Complete section  | Full role interface, analytics system, comprehensive HRMS     |

### Quick Process (5 minutes)

```markdown
1. List major features (2 min)
2. Assign T-shirt size to each (2 min)
3. Sum midpoint hours (30 sec)
4. Add multipliers (30 sec)

Example (AGGRESSIVE):

- Authentication: M (18 hr midpoint)
- User Profile: L (36 hr midpoint)
- Dashboard: M (18 hr midpoint)
  Subtotal: 72 hr

* Testing (15%): 11 hr
* Responsive (20%): 14 hr
* Buffer (10%): 7 hr
  Total: ~104 hours (was 156 with conservative)

Confidence: 60% (±30 hrs range: 74-134 hr)
```

### T-Shirt Size Converter (AGGRESSIVE)

```
Aggressive (Recommended for Experienced Teams):
XS → 4 hr
S → 9 hr
M → 18 hr
L → 36 hr
XL → 72 hr
XXL → 150 hr

Conservative (Junior Teams):
XS → 8 hr
S → 16 hr
M → 40 hr
L → 80 hr
XL → 160 hr
XXL → 300 hr

**DEFAULT MODE: Aggressive (use these for experienced teams)**
```

### Mode Selection Guide

| Team Profile             | Mode         | XS  | S    | M    | L    | XL    |
| ------------------------ | ------------ | --- | ---- | ---- | ---- | ----- |
| **Experienced (3+ yrs)** | Aggressive   | 4hr | 9hr  | 18hr | 36hr | 72hr  |
| **Mid-level (1-3 yrs)**  | Moderate     | 5hr | 12hr | 24hr | 48hr | 96hr  |
| **Junior (<1 yr)**       | Conservative | 6hr | 16hr | 32hr | 64hr | 128hr |

**This agent defaults to AGGRESSIVE mode for experienced teams.**

---

## 2️⃣ STORY POINTS WITH VELOCITY (10-20 minutes)

**Use when:** Team has historical velocity, Agile environment

### Fibonacci Story Points → Hours (AGGRESSIVE MODE)

| Points | Aggressive | Conservative | Complexity | Examples                             |
| ------ | ---------- | ------------ | ---------- | ------------------------------------ |
| **1**  | 3-4 hr     | 4-6 hr       | Trivial    | Style update, text change            |
| **2**  | 4-6 hr     | 6-10 hr      | Simple     | Simple component, basic form field   |
| **3**  | 6-10 hr    | 10-16 hr     | Small      | Form with 5-8 fields, list page      |
| **5**  | 10-16 hr   | 16-24 hr     | Medium     | CRUD operations, search with filters |
| **8**  | 16-26 hr   | 26-40 hr     | Large      | Multi-step form, data table          |
| **13** | 26-42 hr   | 42-65 hr     | Complex    | User management, dashboard           |
| **21** | 42-68 hr   | 68-105 hr    | Epic       | Complete module, admin section       |

### Quick Process (15 minutes)

```markdown
1. Break down into user stories (5 min)
2. Assign story points (5 min)
3. Convert to hours using aggressive table (2 min)
4. Sum and add multipliers (3 min)

Example (AGGRESSIVE):

- User login: 5 points = 13 hr
- User registration: 5 points = 13 hr
- Password reset: 3 points = 8 hr
- User profile: 8 points = 21 hr
  Subtotal: 21 points = 55 hr base

* Testing (15%): 8 hr
* Responsive (20%): 11 hr
* Buffer (10%): 6 hr
  Total: ~80 hours (vs 105 conservative)

Confidence: 75% (team has velocity history)
```

### Velocity-Based Timeline

```
Experienced team velocity = 25 points per 2-week sprint:
Total 60 points / 25 points per sprint = 2.4 sprints ≈ 5 weeks
```

---

## 3️⃣ REFERENCE PATTERN MATCHING (20-30 minutes)

**Use when:** Project uses common patterns, similar to previous work

### Common Frontend Patterns Library

| Pattern                        | Base Hours | Notes                                             |
| ------------------------------ | ---------- | ------------------------------------------------- |
| **Auth Suite (Full)**          | 24-40 hr   | Login, logout, forgot/reset password, remember me |
| **Auth (Basic)**               | 16-24 hr   | Just login/logout                                 |
| **2FA Addition**               | 12-20 hr   | Add to existing auth                              |
| **OAuth Integration**          | 16-24 hr   | Google/GitHub login                               |
| **User CRUD (Simple)**         | 20-32 hr   | List, create, edit, delete                        |
| **User CRUD (Complex)**        | 32-48 hr   | + Filters, export, bulk actions                   |
| **User Profile (Basic)**       | 16-24 hr   | Single form, avatar upload                        |
| **User Profile (Multi-tab)**   | 24-40 hr   | Multiple sections, file uploads                   |
| **Role Management**            | 20-32 hr   | Assign roles, permissions UI                      |
| **Data Table (Basic)**         | 12-16 hr   | Display data, pagination                          |
| **Data Table (Standard)**      | 16-24 hr   | + Sort, filter, search                            |
| **Data Table (Advanced)**      | 28-40 hr   | + Inline edit, bulk ops, export                   |
| **Dashboard (Basic)**          | 16-24 hr   | 4-6 widgets, static                               |
| **Dashboard (Standard)**       | 28-40 hr   | 8-10 widgets, charts, filters                     |
| **Dashboard (Advanced)**       | 48-80 hr   | Real-time, drill- down, complex charts            |
| **Multi-Step Form (3 steps)**  | 20-32 hr   | Stepper, validation, draft                        |
| **Multi-Step Form (5+ steps)** | 32-48 hr   | Complex logic, branching                          |
| **File Upload (Single)**       | 8-12 hr    | Basic upload, validation                          |
| **File Upload (Multiple)**     | 12-20 hr   | Drag-drop, preview, progress                      |
| **File Manager**               | 32-48 hr   | Browse, upload, organize, preview                 |
| **Search (Basic)**             | 8-12 hr    | Text search, results                              |
| **Search (Advanced)**          | 16-24 hr   | Filters, facets, autocomplete                     |
| **Notification Dropdown**      | 12-16 hr   | In-app notifications, mark read                   |
| **Real-Time Notifications**    | 24-32 hr   | + WebSocket, push updates                         |
| **Report (Single)**            | 12-20 hr   | One chart/table, date filter, export              |
| **Report Dashboard**           | 32-48 hr   | Multiple reports, tabs                            |
| **Settings Page**              | 16-24 hr   | Multi-section settings, save                      |
| **Activity Log**               | 12-16 hr   | Timeline, filters                                 |

### Standard Multipliers (ALWAYS ADD)

```
Testing: +15%
Responsive: +20% (OPTIONAL - ask user if responsive is separate or included in base)
Integration overhead: +15%
Bug buffer: +10%
─────────────────────────
Total multiplier: 1.52x

Quick calc: Pattern sum × 1.52 = Total
```

### Pattern Matching Example (25 minutes)

```markdown
Requirements: User management CRM

Pattern Identification (10 min):
✓ Auth Suite (Full): 32 hr
✓ User CRUD (Complex): 40 hr
✓ User Profile (Multi-tab): 32 hr
✓ Role Management: 26 hr
✓ Activity Log: 14 hr
Base sum: 144 hr

Apply Multipliers (5 min):
Testing (+15%): +22 hr
Responsive (+20%): +29 hr
Integration (+15%): +22 hr
Buffer (+10%): +14 hr
Subtotal: 231 hr

Round up (1 min):
Total: 235 hours

Timeline (2 min):
2 devs × 270 / (2 × 160) = 0.84 → 3.5 weeks

Output (7 min):
Confidence: 75% (using proven patterns)
Range: 220-320 hours (±20%)
```

---

## 4️⃣ COMPONENT COUNT ESTIMATION (30-45 minutes)

**Use when:** Have component breakdown, design system defined

### Atomic Design Multipliers

| Level         | Avg Hours | Range    | Examples                           |
| ------------- | --------- | -------- | ---------------------------------- |
| **Atoms**     | 2 hr      | 1-3 hr   | Button, input, icon, badge         |
| **Molecules** | 6 hr      | 4-8 hr   | Search bar, card, form field group |
| **Organisms** | 18 hr     | 12-24 hr | Data table, nav bar, form section  |
| **Templates** | 12 hr     | 8-16 hr  | Page layout, dashboard shell       |
| **Pages**     | 26 hr     | 12-40 hr | Complete page with all logic       |

### Quick Formula

```
Total = (Atoms × 2) + (Molecules × 6) + (Organisms × 18) + (Templates × 12) + (Pages × 26)

Example:
- 20 atoms × 2 = 40 hr
- 15 molecules × 6 = 90 hr
- 8 organisms × 18 = 144 hr
- 5 templates × 12 = 60 hr
- 12 pages × 26 = 312 hr
Base: 646 hr

+ Testing (15%): 97 hr
+ Responsive (20%): 129 hr
Total: ~872 hours
```

### Component Counting Process (35 minutes)

```markdown
1. List all atoms (5 min)
2. List all molecules (8 min)
3. List all organisms (10 min)
4. List templates (5 min)
5. List pages (5 min)
6. Calculate (2 min)
```

---

## 5️⃣ HYBRID APPROACH (45-60 minutes) ⭐ RECOMMENDED

**Best balance of speed and accuracy**

### Process

```markdown
1. Identify major modules (5 min)
2. T-shirt size each module (10 min)
3. Apply reference patterns to key features (20 min)
4. Add standard multipliers (5 min)
5. Apply confidence buffer (5 min)
6. Document (15 min)
```

### Example Workflow

```markdown
**Step 1: Major Modules**

- Authentication
- User Management
- Dashboard
- Reporting
- File Management

**Step 2: T-Shirt Size**

- Authentication: M (28 hr)
- User Management: L (60 hr)
- Dashboard: M (28 hr)
- Reporting: L (60 hr)
- File Management: M (28 hr)
  Subtotal: 204 hr

**Step 3: Pattern Refinement**
Look at User Management more closely:

- User CRUD (Complex): 40 hr
- User Profile: 32 hr
- Role Management: 26 hr
  Refined: 98 hr (vs 60 hr T-shirt)

Adjusted total: 242 hr

**Step 4: Multipliers**

- Testing (15%): 36 hr
- Responsive (20%): 48 hr
- Integration (15%): 36 hr
  Subtotal: 362 hr

**Step 5: Confidence Buffer**
Medium confidence → +20%
Total: 434 hr → Round to 440 hr

**Step 6: Document**
2 devs × 500 hr / 320 hr = 1.56 months → 6-7 weeks
Confidence: 70%
Range: 400-600 hr
```

---

## 6️⃣ HISTORICAL DATA LOOKUP (5 minutes)

**Use when:** Have similar past projects with actuals

### Process

```markdown
1. Identify similar project (2 min)
2. Note actual hours from that project (1 min)
3. Calculate adjustment factors (1 min)
4. Apply adjustments (1 min)
```

### Example

```markdown
**Similar Project:**
Customer Portal (2024): 1,200 hr actual (2 devs, 4 months)

**Adjustments:**
Current project scope: +15% (more features)
Team experience: -10% (team is more experienced now)
Technology change: +5% (new framework)
Net adjustment: +10%

**Calculation:**
Base: 1,200 hr
Adjustment: +10% = +120 hr
Estimate: 1,320 hours

**Confidence:** 80% (based on actual data)
```

---

## 🎯 QUICK OUTPUT TEMPLATES

### 5-Minute Estimate Template

```markdown
## Quick Estimate: [Project Name]

**Method:** T-Shirt Sizing
**Time to Estimate:** 5 minutes

### Sizing

| Module   | Size | Hours |
| -------- | ---- | ----- |
| Module 1 | M    | 28 hr |
| Module 2 | L    | 60 hr |
| Module 3 | S    | 12 hr |

**Base:** 100 hr
**+ Multipliers (85%):** 85 hr
**Total: 185 hours**

### Timeline

- 2 developers: ~5 weeks

### Confidence

50% - Very rough estimate for discovery phase

### Next Steps

Need 1-2 hours for detailed breakdown
```

### 15-Minute Estimate Template

```markdown
## Quick Estimate: [Project Name]

**Method:** Story Points / Pattern Matching
**Time to Estimate:** 15 minutes

### Features

| Feature         | Pattern/Points     | Hours |
| --------------- | ------------------ | ----- |
| Authentication  | Auth Suite         | 32 hr |
| User Management | CRUD + Profile     | 72 hr |
| Dashboard       | Standard Dashboard | 34 hr |

**Base:** 138 hr
**+ Testing (15%):** 21 hr
**+ Responsive (20%):** 28 hr
**Total: 187 hours**

### Timeline

- 2 developers: 5-6 weeks

### Confidence

65% - Pattern-based, medium confidence

### Assumptions

- API ready
- Designs complete
- Standard Vue 3 stack
```

---

## 📊 Rapid Estimation Decision Tree

```
Need estimate in...

5 minutes?
  ↓
  T-Shirt Sizing
  → Module-level, ±50%

15 minutes?
  ↓
  Have past project?
    ↓ YES → Historical Data
    ↓ NO → Story Points
  → Feature-level, ±30%

30 minutes?
  ↓
  Have component list?
    ↓ YES → Component Count
    ↓ NO → Pattern Matching
  → Component-level, ±25%

45-60 minutes?
  ↓
  Hybrid Approach
  → Balanced, ±20%
```

---

## 💡 Pro Tips for Rapid Estimation

### DO:

✅ State your method clearly
✅ Provide a range, not exact number
✅ Document assumptions
✅ State confidence level
✅ Offer more detailed estimate later
✅ Round up to nearest 5 or 10
✅ Add buffer for unknowns

### DON'T:

❌ Give single precise number (e.g., "exactly 247 hours")
❌ Skip multipliers (testing, responsive)
❌ Forget to mention it's a rough estimate
❌ Promise detailed breakdown without time
❌ Ignore past project data if available
❌ Underestimate to please client

### Quick Quality Checks

Before finalizing rapid estimate:

- [ ] Did I add testing time? (+15%)
- [ ] Did I add responsive design? (+20%)
- [ ] Did I state confidence level?
- [ ] Did I provide a range?
- [ ] Did I list key assumptions?
- [ ] Did I round up, not down?

---

## 🔧 Rapid Estimation Cheat Codes

### Ultra-Fast Multiplier

```
For "I need a number RIGHT NOW":

Count features → × 25 hours average → × 1.8 multiplier

Example:
8 features × 25 hr × 1.8 = 360 hours
"Roughly 350-450 hours with 2 devs taking 2-3 months"

Confidence: 40% (but you gave an answer in 30 seconds)
```

### Page Count Method

```
Count total pages → × 20 hours average → × 2.0 multiplier

Example:
15 pages × 20 hr × 2.0 = 600 hours

Confidence: 45%
```

### Feature Point Method

```
Simple feature = 1 point
Medium feature = 3 points
Complex feature = 5 points

Total points × 12 hours × 1.5 multiplier

Example:
5 simple + 3 medium + 2 complex = 5 + 9 + 10 = 24 points
24 × 12 × 1.5 = 432 hours

Confidence: 55%
```

---

**END OF MODULE**

**Usage in main agent:**

```
When user says "quick estimate" or "ballpark":
→ Use T-Shirt Sizing (Section 1)

When user says "we need it fast, under 30 minutes":
→ Use Hybrid Approach (Section 5)

When user has past project data:
→ Use Historical Data (Section 6)
```

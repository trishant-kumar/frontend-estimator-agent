# Estimation Template - Quick Reference Guide

## 🚀 How to Use the Template in 5 Steps

### Step 1️⃣: Ask ALL Questions First (Section 1)

**DO NOT start estimating until you have answers to all 12 questions!**

Send these questions to client:

- Q1-Q4: Design assets
- Q5-Q6: Responsive requirements
- Q7: Browser support
- Q8: Internationalization
- Q9-Q10: API readiness
- Q11: Testing level
- Q12: Infrastructure needs

**Time required:** 15-30 min client call or email questionnaire

---

### Step 2️⃣: Calculate Base Hours (Section 2)

Break down project into modules:

- **Low complexity:** 20-40 hrs (simple CRUD, lists)
- **Medium complexity:** 60-120 hrs (tables, multi-step forms, dashboards)
- **High complexity:** 140-300+ hrs (workflows, real-time, visualizations)

**Apply reusability:** If modules share components, reduce by 20-35%

---

### Step 3️⃣: Apply Adjustment Factors (Section 3)

Based on client answers, multiply hours by factors:

**Common Scenarios:**

- Complete designs provided → × 0.60-0.75
- No designs (we build UI) → × 1.00
- Desktop + Tablet + Mobile → × 1.00
- Modern browsers only → × 1.00
- Single language → × 1.00
- APIs ready → × 1.00
- Unit + E2E tests → × 1.18

---

### Step 4️⃣: Calculate Final Estimate (Section 4)

```
Base Hours
× Design Factor
× Responsive Factor
× Browser Factor
× i18n Factor
× API Factor
× Testing Factor
+ Infrastructure Hours
+ 10% Buffer
─────────────────────
= FINAL ESTIMATE
```

---

### Step 5️⃣: Convert to Timeline (Section 5)

**Formula:**

```
Total Hours ÷ (Team Size × 6 hrs/day × 22 days/month) = Months
```

**Example:**

- 1,000 hours
- 5 developers
- 5 × 6 × 22 = 660 hrs/month
- 1,000 ÷ 660 = **1.5 months**

---

## 📊 Real-World Example: Vista Software

### Client Answers:

- Q1: NO designs (we build UI)
- Q2: Use Vuetify (standard library)
- Q3: NO UX docs
- Q4: Placeholder content
- Q5: Desktop + Tablet + Mobile
- Q6: N/A
- Q7: Modern browsers
- Q8: Single language
- Q9: Parallel API development
- Q10: Basic documentation
- Q11: Unit + E2E tests
- Q12: NO infrastructure

### Calculation:

```
Base: 860 hrs (7 modules with reusability)
× 1.00 (no designs)
× 1.00 (responsive included)
× 1.00 (modern browsers)
× 1.00 (single language)
× 1.06 (parallel APIs)
× 1.18 (testing)
+ 0 hrs (no infra)
+ 100 hrs (10% buffer)
─────────────────
= 1,075 hours
= 8-10 months with 5-6 developers
```

---

## ⚠️ Common Mistakes to Avoid

### ❌ Don't Do This:

1. **Estimating before asking questions** → 30-60% variance
2. **Assuming designs will be provided** → Can add 400+ hours
3. **Forgetting responsive design** → Can add 150+ hours
4. **Ignoring API readiness** → Can add delays
5. **Not including testing** → Can add 150-200 hours
6. **Forgetting 10% buffer** → No room for unknowns

### ✅ Do This:

1. **Ask ALL 12 questions first**
2. **Document client answers**
3. **Apply factors methodically**
4. **Show calculation breakdown**
5. **Add assumptions section**
6. **Include 10% buffer always**

---

## 🎯 Estimate Ranges by Scenario

### Scenario A: Best Case (Everything Provided)

- Complete Figma designs + design system + UX docs + ready APIs
- **Factor:** 0.60-0.75 of base
- **Example:** 1,000 base hrs → **600-750 hours**

### Scenario B: Standard Case (Partial Assets)

- Wireframes + standard library + parallel APIs
- **Factor:** 0.85-1.00 of base
- **Example:** 1,000 base hrs → **850-1,000 hours**

### Scenario C: Full Build (Nothing Provided)

- No designs + we build UI + parallel APIs + testing
- **Factor:** 1.10-1.25 of base
- **Example:** 1,000 base hrs → **1,100-1,250 hours**

---

## 📋 Pre-Estimation Checklist

Before sending estimate to client:

- [ ] All 12 questions answered and documented
- [ ] Base hours calculated per module
- [ ] Reusability factor applied (if applicable)
- [ ] All adjustment factors applied correctly
- [ ] 10% buffer added
- [ ] Timeline calculated with team size
- [ ] Deliverables list customized
- [ ] Assumptions clearly stated
- [ ] Exclusions explicitly listed
- [ ] Confidence level assigned (60-95%)
- [ ] Next steps defined

---

## 🔢 Quick Factor Reference Table

| Question | Scenario                  | Factor/Impact |
| -------- | ------------------------- | ------------- |
| Q1       | Complete designs          | × 0.75-0.80   |
| Q1       | Wireframes                | × 0.88-0.90   |
| Q1       | No designs                | × 1.00        |
| Q2       | Design system ready       | × 0.65-0.75   |
| Q2       | Standard library          | × 1.00        |
| Q2       | Build from scratch        | × 1.25        |
| Q3       | UX docs provided          | × 0.90-0.92   |
| Q3       | No UX docs                | × 1.00        |
| Q5       | Desktop only              | × 0.82        |
| Q5       | Desktop + Tablet + Mobile | × 1.00        |
| Q7       | Modern browsers           | × 1.00        |
| Q7       | IE11 support              | × 1.18        |
| Q8       | Single language           | × 1.00        |
| Q8       | 2-3 languages             | × 1.14        |
| Q8       | 5+ languages              | × 1.22        |
| Q9       | APIs ready                | × 1.00        |
| Q9       | Parallel dev              | × 1.06        |
| Q9       | Frontend first            | × 1.15        |
| Q11      | Manual testing            | × 1.00        |
| Q11      | Unit + E2E                | × 1.18        |
| Q11      | Comprehensive             | × 1.35        |
| Q12      | No infra                  | +0 hrs        |
| Q12      | Basic CI/CD               | +20 hrs       |
| Q12      | Full setup                | +50 hrs       |

---

## 💡 Pro Tips

### Tip 1: Always Start Conservative

- First estimate? Add 15-20% confidence buffer
- Complex integrations? Add 10-15% per integration
- New tech stack? Add 20-25% learning curve

### Tip 2: Break Down Large Projects

- Over 1,000 hours? Split into phases
- Phase 1: MVP (most critical features)
- Phase 2: Standard features
- Phase 3: Nice-to-have features

### Tip 3: Document Everything

- Keep copy of client's answers
- Show calculation breakdown
- Update estimates if scope changes
- Track actual vs estimated for future projects

### Tip 4: Set Expectations

- Clearly state what's included/excluded
- Define "done" criteria per feature
- Explain impact of scope changes
- Schedule regular checkpoints

---

## 📧 Template Usage Workflow

```
1. Receive project requirements
   ↓
2. Send Section 1 questions to client
   ↓
3. Schedule 30-min call to review answers
   ↓
4. Calculate base hours (Section 2)
   ↓
5. Apply all factors (Section 3)
   ↓
6. Generate final estimate (Section 4)
   ↓
7. Convert to timeline (Section 5)
   ↓
8. Customize deliverables (Section 6)
   ↓
9. Create summary (Section 7)
   ↓
10. Send estimate to client with assumptions
    ↓
11. Update template for your records
```

---

## 🎓 Confidence Level Guidelines

**90-95% Confidence:**

- Client provided complete designs & docs
- Similar project done before
- Standard tech stack
- Clear requirements

**75-89% Confidence:**

- Most questions answered clearly
- Some unknowns remain
- Moderately complex features
- Standard approach

**60-74% Confidence:**

- Several unanswered questions
- Complex/novel features
- Multiple integrations
- Unclear requirements

**Below 60%:**

- **Don't estimate yet!**
- Get more information first
- Consider paid discovery phase

---

## 📞 When to Update This Template

Update the template when:

- You discover better estimation methods
- Project actual hours differ significantly from estimates
- New technology/framework changes development speed
- Team feedback suggests adjustments
- Industry best practices evolve

**Review quarterly and update factors based on historical data**

---

**Created:** 24 February 2026  
**For:** Reusable across all frontend projects  
**Maintained by:** Engineering/Estimations Team

# Frontend Estimation System

**Version:** 1.0  
**Created:** 24 February 2026  
**Purpose:** Reusable estimation framework for accurate, realistic project quotes

---

## 📚 Overview

This folder contains a comprehensive estimation system that helps you provide **accurate frontend development estimates** based on client-specific requirements. The system eliminates the common 30-60% estimate variance by asking critical questions **before** estimating.

---

## 🎯 The Problem We're Solving

**Common Estimation Mistakes:**

- ❌ Assuming designs will be provided (can add 400+ hours)
- ❌ Not clarifying responsive requirements (can add 150+ hours)
- ❌ Overlooking testing needs (can add 150-200 hours)
- ❌ Forgetting about API readiness (can add delays + hours)
- ❌ Not accounting for browser compatibility (can add 100+ hours)

**Result:** 30-60% variance between estimate and actual hours

**This System Fixes That ✅**

---

## 📂 What's in This Folder

### 1. **FRONTEND_ESTIMATION_TEMPLATE.md** (Master Template)

- **Use:** Complete estimation template with all questions and calculations
- **Sections:** 7 comprehensive sections from questions to final estimate
- **Best for:** Detailed estimates with full documentation
- **Time to complete:** 45-60 minutes

### 2. **CALCULATOR_SHEET.md** (Quick Calculator)

- **Use:** Fill-in-the-blank worksheet for fast estimates
- **Format:** Step-by-step with checkboxes and calculation fields
- **Best for:** Quick estimates with clear inputs
- **Time to complete:** 20-30 minutes

### 3. **QUICK_REFERENCE_GUIDE.md** (How-to Guide)

- **Use:** Instructions on using the estimation system
- **Includes:** Examples, pro tips, common mistakes, factor tables
- **Best for:** Learning the system, training new estimators
- **Time to read:** 10-15 minutes

### 4. **README.md** (This File)

- **Use:** Overview and navigation for the estimation system
- **Best for:** Understanding what's available and how to start

---

## 🚀 How to Use This System (3 Options)

### Option A: Full Detailed Estimate (Recommended for Complex Projects)

**Use:** `FRONTEND_ESTIMATION_TEMPLATE.md`

1. Copy the template for your project
2. Send Section 1 questions to client
3. Complete all 7 sections step-by-step
4. Generate comprehensive estimate with assumptions

**Best for:**

- Large projects (1000+ hours)
- Multiple modules
- Need detailed documentation
- Formal proposals

**Time:** 45-60 minutes

---

### Option B: Quick Calculate (Recommended for Simple Projects)

**Use:** `CALCULATOR_SHEET.md`

1. Print or copy calculator sheet
2. Check boxes for each question
3. Fill in hours and multiply factors
4. Get final estimate

**Best for:**

- Small/medium projects (200-800 hours)
- Quick turnaround needed
- Simple scope
- Internal estimates

**Time:** 20-30 minutes

---

### Option C: Learn the System First

**Use:** `QUICK_REFERENCE_GUIDE.md` → Then Template or Calculator

1. Read the Quick Reference Guide
2. Understand the methodology
3. Choose Template or Calculator
4. Complete your estimate

**Best for:**

- First time using system
- Training new estimators
- Understanding the "why" behind questions

**Time:** 10-15 min study + 20-60 min estimating

---

## 🎓 The 12 Critical Questions

**Before estimating ANY project, answer these:**

### Design & Assets (4 questions)

1. Are complete visual designs (Figma/XD) provided?
2. Is a component library or design system available?
3. Is UX documentation provided?
4. Who provides content (labels, messages, text)?

### Technical Requirements (4 questions)

5. Which devices must be supported? (desktop/tablet/mobile)
6. If designs provided, do they include responsive layouts?
7. Which browsers must be supported?
8. Is multi-language support required?

### Backend & APIs (2 questions)

9. Will backend APIs be ready at project start?
10. Is API documentation available?

### Quality & Infrastructure (2 questions)

11. What testing level is required?
12. Do you need DevOps/deployment setup?

**Impact:** These 12 questions can change your estimate by **400-600 hours** ⚠️

---

## 📊 Understanding Estimate Variance

### Example: 1,000 Base Hours Project

**Scenario A: Everything Provided**

- Complete designs + component library + UX docs + ready APIs
- **Total:** 600-750 hours (40% reduction)
- **Timeline:** 4-5 months with 5 devs

**Scenario B: Standard Build**

- Wireframes + standard library + parallel APIs
- **Total:** 850-1,000 hours (15% reduction)
- **Timeline:** 6-7 months with 5 devs

**Scenario C: Full Build**

- No designs + we build everything + testing
- **Total:** 1,100-1,250 hours (10-25% increase)
- **Timeline:** 8-10 months with 5 devs

**Difference between A and C: 400-500 hours (2-3 months)**

---

## 🎯 Quick Start Guide

### For Your First Estimate:

1. **Read This:** `QUICK_REFERENCE_GUIDE.md` (10 mins)
2. **Copy This:** `CALCULATOR_SHEET.md`
3. **Send Questions:** Email/call client with the 12 questions
4. **Calculate:** Fill out calculator with their answers
5. **Review:** Check assumptions and exclusions
6. **Send:** Deliver estimate with confidence level

### For Subsequent Estimates:

1. **Copy:** `CALCULATOR_SHEET.md` (you know the drill now)
2. **Ask:** The 12 questions
3. **Calculate:** Fill in factors
4. **Send:** Estimate

---

## 📏 Factor Reference (Quick Lookup)

### Design Assets

- Complete designs provided: **× 0.75**
- Wireframes only: **× 0.88**
- No designs (we build): **× 1.00**
- Custom from scratch: **× 1.25**

### Responsive

- Desktop only: **× 0.82**
- Desktop + Tablet: **× 0.90**
- All devices: **× 1.00**

### Browsers

- Modern only: **× 1.00**
- Include IE11: **× 1.18**

### Languages

- Single language: **× 1.00**
- 2-3 languages: **× 1.14**
- 5+ languages: **× 1.22**

### API Status

- Ready with docs: **× 1.00**
- Parallel development: **× 1.06**
- Frontend first: **× 1.15**

### Testing

- Manual only: **× 1.00**
- Unit + E2E: **× 1.18**
- Comprehensive: **× 1.35**

### Infrastructure

- Client handles: **+0 hrs**
- Basic CI/CD: **+20 hrs**
- Full setup: **+50 hrs**

---

## 🎯 Real-World Examples

### Example 1: Enterprise Platform (Vista Software)

- **Base:** 860 hours (7 modules)
- **Questions:** No designs, standard library, responsive, modern browsers, single language, parallel APIs, unit+E2E tests
- **Factors:** 1.00 × 1.00 × 1.00 × 1.00 × 1.06 × 1.18 = **1,075 hours**
- **Timeline:** 8-10 months with 5-6 developers

### Example 2: Dashboard with Designs

- **Base:** 400 hours (3 modules)
- **Questions:** Complete designs, design system, UX docs, desktop+mobile, modern browsers, APIs ready, unit tests
- **Factors:** 0.75 × 1.00 × 1.00 × 1.00 × 1.18 = **354 hours**
- **Timeline:** 3-4 months with 3 developers

### Example 3: Simple CRUD App

- **Base:** 200 hours (2 modules)
- **Questions:** Wireframes, standard library, desktop only, modern browsers, APIs ready, manual testing
- **Factors:** 0.88 × 0.82 × 1.00 × 1.00 = **144 hours**
- **Timeline:** 1-2 months with 2-3 developers

---

## ✅ Best Practices

### DO:

- ✅ Ask ALL 12 questions before estimating
- ✅ Document client answers in writing
- ✅ Show calculation breakdown to client
- ✅ Include 10% buffer always
- ✅ List assumptions and exclusions clearly
- ✅ Assign realistic confidence level
- ✅ Track actual vs estimated for future accuracy

### DON'T:

- ❌ Estimate before asking questions
- ❌ Assume designs will be provided
- ❌ Forget responsive design impact
- ❌ Skip the testing factor
- ❌ Promise aggressive timelines
- ❌ Ignore API readiness
- ❌ Estimate without buffer

---

## 🔄 System Maintenance

### Update This System When:

- [ ] Historical actuals differ from estimates by >20%
- [ ] New framework/tools change development speed
- [ ] Team feedback suggests adjustments
- [ ] Industry practices evolve
- [ ] Discovery of better estimation methods

**Review:** Quarterly (every 3 months)  
**Owner:** Engineering Manager / Tech Lead

---

## 📈 Tracking Accuracy

**Keep a log of your estimates vs actuals:**

| Project   | Estimated | Actual   | Variance | Lessons        |
| --------- | --------- | -------- | -------- | -------------- |
| Project A | 800 hrs   | 850 hrs  | +6%      | Good           |
| Project B | 1200 hrs  | 1000 hrs | -17%     | Over-estimated |
| Project C | 600 hrs   | 900 hrs  | +50%     | Missed scope   |

**Target Accuracy:** ±20% variance

---

## 🎓 Training New Estimators

### Week 1: Learn the System

- Read all 3 documents
- Review example estimates
- Shadow senior estimator

### Week 2: Practice

- Complete 2-3 practice estimates
- Get feedback from senior estimator
- Compare with actual project outcomes

### Week 3: Live Estimates

- Estimate real project with supervision
- Present to team for review
- Refine based on feedback

### Week 4: Independent

- Estimate projects independently
- Peer review before sending to client

---

## 📞 Questions or Feedback?

**System Maintainer:** **\*\***\*\*\*\***\*\***\_**\*\***\*\*\*\***\*\***  
**Email:** **\*\***\*\*\*\***\*\***\_**\*\***\*\*\*\***\*\***  
**Last Updated:** 24 February 2026

---

## 📝 Version History

| Version | Date        | Changes                | Author |
| ------- | ----------- | ---------------------- | ------ |
| 1.0     | 24 Feb 2026 | Initial system created | -      |
|         |             |                        |        |

---

## 🎯 Remember

> **"The 15 minutes you spend asking questions will save you 50+ hours of estimate corrections and scope discussions."**

**Always ask first, estimate second. Never the other way around.**

---

**Built for Simform Engineering Team**  
**Making estimates predictable and realistic**

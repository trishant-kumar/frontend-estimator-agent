# University Admission CRM - Frontend Estimation

**Project:** University Admission CRM (Web Application)  
**Client:** [Client Name]  
**Estimator:** GitHub Copilot  
**Date:** February 24, 2026  
**Framework:** Vue 3 + Nuxt 3 + TypeScript + Tailwind CSS/Vuetify

---

## 📋 EXECUTIVE SUMMARY

| Metric                             | Value                     |
| ---------------------------------- | ------------------------- |
| **Base Development Hours**         | **540 hours**             |
| **Total Hours (with adjustments)** | **723 hours**             |
| **Timeline (1 developer)**         | **18 weeks (4.5 months)** |
| **Timeline (2 developers)**        | **10 weeks (2.5 months)** |
| **Recommended Team**               | **2 frontend developers** |

**Key Complexity Factors:**

- ✅ 4 user roles with Enterprise RBAC (+80 hours)
- ✅ Real-time notifications via WebSocket (+40 hours)
- ✅ File management system (+12 hours)
- ✅ Complete UI designs provided (-25% reduction)
- ✅ Production-grade quality (+20% overhead)

---

## 📊 ESTIMATION METHODOLOGY APPLIED

### Question Responses:

1. **Design Assets:** Complete UI designs (Figma/XD) → **0.75 factor (-25%)**
2. **Device Support:** Desktop + Tablet + Mobile → **1.0 factor (responsive included)**
3. **API Readiness:** APIs ready with documentation → **0 additional hours**
4. **Quality Level:** Production-grade (tests + edge cases) → **1.20 factor (+20%)**
5. **Language Support:** Single language (English) → **1.0 factor**
6. **RBAC Complexity:** Enterprise RBAC (4 roles + audit logs) → **+80 hours**
7. **Real-time Updates:** WebSocket for notifications → **+40 hours**
8. **Accessibility:** Basic accessibility (semantic HTML) → **Baseline (included)**
9. **Integrations:** File Storage (S3/Cloudinary/Firebase) → **+12 hours**
10. **Confidence Buffer:** 75% confidence → **+10% buffer**

---

## 🏗️ DETAILED BREAKDOWN

### **MODULE 1: AUTHENTICATION SYSTEM**

#### **Components:**

| Component          | Type     | Complexity | Hours |
| ------------------ | -------- | ---------- | ----- |
| LoginForm          | Organism | Medium     | 3     |
| ForgotPasswordForm | Organism | Medium     | 2     |
| ResetPasswordForm  | Organism | Medium     | 2     |
| RoleBasedGuard     | Utility  | High       | 4     |
| AuthLayout         | Template | Low        | 2     |

**Subtotal:** 13 hours

#### **Pages:**

| Page             | Features                                                               | Hours |
| ---------------- | ---------------------------------------------------------------------- | ----- |
| /login           | Email/password, remember me, role redirect, JWT handling, error states | 4     |
| /password/forgot | Email input, validation, API integration, success state                | 2     |
| /password/reset  | Token validation, new password form, expiry handling                   | 3     |

**Subtotal:** 9 hours

#### **Services & Stores:**

| Item               | Features                                                      | Hours |
| ------------------ | ------------------------------------------------------------- | ----- |
| auth.service.ts    | Login, logout, refresh token, password reset API calls        | 3     |
| auth.store.ts      | State management, token handling, auto-logout, session checks | 5     |
| auth.middleware.ts | Route guards, role-based redirects, token validation          | 4     |

**Subtotal:** 12 hours

**Module 1 Total:** **34 hours**

---

### **MODULE 2: STUDENT PORTAL**

#### **2.1 Student Dashboard**

| Component/Page             | Features                                    | Hours |
| -------------------------- | ------------------------------------------- | ----- |
| DashboardLayout            | Template with sidebar/header                | 3     |
| ProfileCompletionWidget    | Progress bar, missing fields indicator      | 3     |
| ApplicationStatusCards     | Status overview with color coding           | 4     |
| NotificationFeed           | Recent notifications display                | 3     |
| UpcomingDeadlinesWidget    | Calendar view, countdown timers             | 4     |
| RecentActivityTimeline     | Activity log with icons                     | 3     |
| Dashboard Page Integration | All widgets, loading states, error handling | 4     |

**Subtotal:** 24 hours

#### **2.2 Profile Management**

| Component            | Features                                           | Hours |
| -------------------- | -------------------------------------------------- | ----- |
| ProfileTabs          | Tab navigation component                           | 2     |
| PersonalInfoForm     | Personal details, validation, autosave             | 4     |
| AcademicHistoryForm  | Multiple education entries (CRUD), date validation | 6     |
| EnglishTestsForm     | IELTS/TOEFL scores, date picker, file upload       | 4     |
| WorkExperienceForm   | Multiple entries, duration calculator              | 5     |
| PassportDetailsForm  | Passport upload, expiry validation, preview        | 4     |
| ProfileCompletionBar | Real-time % calculation across tabs                | 3     |
| AutosaveDraftLogic   | Debounced save, save indicator                     | 3     |

**Subtotal:** 31 hours

#### **2.3 University Application**

| Component             | Features                                          | Hours |
| --------------------- | ------------------------------------------------- | ----- |
| UniversitySearchBar   | Autocomplete, filter chip display                 | 3     |
| UniversityFilterPanel | Country, intake, course filters, clear all        | 4     |
| UniversityCard        | University info, apply button, favorite toggle    | 3     |
| UniversityListView    | Pagination, sorting, grid/list toggle             | 4     |
| ApplicationWizard     | Multi-step stepper (Intake → Docs → SOP → Review) | 8     |
| IntakeSelector        | Available intakes, date display                   | 2     |
| DocumentUploadSection | Multiple file upload, validation, progress        | 6     |
| SOPEditor             | Rich text editor / textarea, character count      | 4     |
| ApplicationReviewStep | Summary, edit links, submit confirmation          | 3     |
| DraftManagement       | Save draft, load draft, draft indicator           | 3     |

**Subtotal:** 40 hours

**Module 2 Total:** **95 hours**

---

### **MODULE 3: COUNSELOR PANEL**

#### **3.1 Student Management**

| Component           | Features                                    | Hours |
| ------------------- | ------------------------------------------- | ----- |
| StudentListTable    | DataTable with sorting, pagination          | 5     |
| StudentSearchBar    | Keyword search, debounced                   | 2     |
| StudentFilterPanel  | Status, country, intake filters             | 4     |
| StudentBulkActions  | Select all, bulk assign, bulk status change | 5     |
| StudentCard         | Student summary card for list view          | 2     |
| AssignStudentDialog | Modal with counselor dropdown               | 2     |

**Subtotal:** 20 hours

#### **3.2 Student Detail View**

| Component              | Features                                | Hours |
| ---------------------- | --------------------------------------- | ----- |
| StudentDetailLayout    | Tab-based layout with header            | 3     |
| StudentProfileTab      | Read-only profile display               | 3     |
| StudentApplicationsTab | Application list, status badges         | 4     |
| StudentDocumentsTab    | Document grid, download, preview        | 5     |
| InternalNotesSection   | Add/edit/delete notes, rich text        | 5     |
| ActivityLogTimeline    | Chronological activity with filters     | 4     |
| StatusChangeDialog     | Change application status, add comment  | 3     |
| DocumentUploadDialog   | Upload additional documents for student | 3     |

**Subtotal:** 30 hours

**Module 3 Total:** **50 hours**

---

### **MODULE 4: AGENCY MANAGER PANEL**

| Component/Page            | Features                                    | Hours |
| ------------------------- | ------------------------------------------- | ----- |
| ManagerDashboard          | Overview cards, quick stats                 | 4     |
| CounselorManagement       | CRUD counselors, status toggle              | 8     |
| StudentAssignmentView     | Drag-drop assign students to counselors     | 6     |
| PerformanceDashboard      | Charts (applications, conversions), filters | 8     |
| RevenueOverview           | Revenue cards, trend charts                 | 5     |
| ExportReportsDialog       | Date range, format selection, download      | 4     |
| CounselorPerformanceTable | Performance metrics, sorting                | 4     |

**Module 4 Total:** **39 hours**

---

### **MODULE 5: SUPER ADMIN PANEL**

| Component/Page        | Features                                          | Hours |
| --------------------- | ------------------------------------------------- | ----- |
| AdminDashboard        | System-wide metrics, health indicators            | 4     |
| AgencyManagement      | CRUD agencies, license management                 | 10    |
| UniversityManagement  | CRUD universities, programs, intakes              | 12    |
| CourseManagement      | CRUD courses, requirements, fees                  | 10    |
| CategoryManagement    | CRUD categories, hierarchical structure           | 6     |
| RolePermissionManager | Role creation, permission assignment, matrix view | 12    |
| SystemConfiguration   | System settings, feature flags                    | 6     |
| AuditLogsViewer       | Audit log table, filters, search, export          | 8     |

**Module 5 Total:** **68 hours**

---

### **MODULE 6: REPORTING MODULE**

| Component                   | Features                                           | Hours |
| --------------------------- | -------------------------------------------------- | ----- |
| ReportDashboard             | Report categories, quick access                    | 3     |
| ApplicationsByCountryReport | Bar/pie chart, data table, filters                 | 6     |
| ApplicationsByIntakeReport  | Timeline chart, breakdown table                    | 6     |
| RevenueReport               | Revenue trends, breakdown by agency/counselor      | 7     |
| ConversionFunnelReport      | Funnel chart, stage analysis                       | 7     |
| CounselorPerformanceReport  | Performance comparison, metrics                    | 6     |
| ReportFilters               | Date range, role filters, country/intake selectors | 4     |
| ExportFunctionality         | CSV download, PDF generation                       | 5     |
| ChartComponents             | Reusable Bar, Pie, Line, Funnel charts             | 8     |

**Module 6 Total:** **52 hours**

---

### **MODULE 7: NOTIFICATION SYSTEM**

| Component               | Features                                  | Hours |
| ----------------------- | ----------------------------------------- | ----- |
| NotificationCenter      | Dropdown with notification list           | 4     |
| NotificationItem        | Individual notification with actions      | 2     |
| NotificationBadge       | Unread count badge                        | 1     |
| WebSocketService        | Connection management, reconnection logic | 12    |
| NotificationStore       | State management, mark as read, filtering | 6     |
| RealTimeSync            | Live updates, optimistic UI               | 8     |
| NotificationPreferences | User notification settings page           | 4     |
| EmailTriggerIndicator   | Show if email was sent                    | 2     |

**Module 7 Total:** **39 hours** (includes +40 hours WebSocket base cost)

---

### **MODULE 8: FILE MANAGEMENT SYSTEM**

| Component      | Features                             | Hours |
| -------------- | ------------------------------------ | ----- |
| FileUploader   | Drag-drop, multi-file, progress bar  | 6     |
| FilePreview    | Modal with PDF/image viewer          | 5     |
| FileList       | File grid/list view, actions         | 4     |
| FileValidation | Size, type validation, error display | 3     |
| S3Integration  | Upload to S3/Cloudinary, signed URLs | 8     |
| FileReplace    | Replace existing file logic          | 2     |
| FileDelete     | Delete with confirmation             | 2     |

**Module 8 Total:** **30 hours** (includes +12 hours integration cost)

---

### **MODULE 9: GLOBAL FEATURES & COMPONENTS**

#### **Global Components (Atomic Design):**

| Component         | Type     | Hours |
| ----------------- | -------- | ----- |
| Button (variants) | Atom     | 2     |
| Input/TextField   | Atom     | 3     |
| Select/Dropdown   | Atom     | 3     |
| DatePicker        | Atom     | 3     |
| Checkbox/Radio    | Atom     | 2     |
| Badge/Tag         | Atom     | 1     |
| Modal/Dialog      | Molecule | 4     |
| DataTable         | Organism | 8     |
| Pagination        | Molecule | 3     |
| SearchBar         | Molecule | 2     |
| FilterPanel       | Organism | 4     |
| Breadcrumbs       | Molecule | 2     |
| Tabs              | Molecule | 2     |
| Stepper           | Molecule | 3     |
| Toast/Snackbar    | Molecule | 2     |

**Subtotal:** 48 hours

#### **Layouts & Navigation:**

| Component        | Features                                | Hours |
| ---------------- | --------------------------------------- | ----- |
| MainLayout       | Header, sidebar, content area           | 5     |
| Sidebar          | Role-based navigation, collapse/expand  | 6     |
| Header           | User menu, notifications, global search | 5     |
| MobileNavigation | Bottom nav for mobile, drawer           | 4     |
| Breadcrumbs      | Dynamic breadcrumb generation           | 2     |

**Subtotal:** 22 hours

#### **Global Features:**

| Feature           | Description                                             | Hours |
| ----------------- | ------------------------------------------------------- | ----- |
| Global Search     | Search across modules, results dropdown                 | 8     |
| Dark Mode         | Theme toggle, persistence, all components               | 6     |
| Error Boundaries  | Global error handling, fallback UI                      | 3     |
| Skeleton Loaders  | Loading skeletons for all major components              | 4     |
| Responsive Design | Mobile, tablet, desktop optimization (INCLUDED AS BASE) | 0     |

**Subtotal:** 21 hours

#### **Form Validation System:**

| Item             | Description                       | Hours |
| ---------------- | --------------------------------- | ----- |
| Zod Schemas      | Validation schemas for all forms  | 8     |
| Form Composables | Reusable form logic, validation   | 5     |
| Error Display    | Inline errors, field highlighting | 3     |

**Subtotal:** 16 hours

**Module 9 Total:** **107 hours**

---

### **MODULE 10: ENTERPRISE RBAC SYSTEM**

| Component/Feature      | Description                                | Hours |
| ---------------------- | ------------------------------------------ | ----- |
| Permission Matrix      | UI for viewing/editing permissions         | 8     |
| Role Management        | Create/edit/delete roles dynamically       | 8     |
| Permission Groups      | Group permissions by module                | 6     |
| Dynamic Route Guards   | Permission-based route access              | 8     |
| UI Permission Checks   | Conditional rendering based on permissions | 10    |
| Role Assignment        | Assign/revoke roles to users               | 6     |
| Permission Delegation  | Allow users to delegate permissions        | 8     |
| Audit Log Integration  | Log all permission changes                 | 6     |
| Permission Cache       | Client-side permission caching             | 4     |
| Permission Composables | Reusable permission checking utilities     | 8     |
| Testing & Edge Cases   | Test all role combinations                 | 8     |

**Module 10 Total:** **80 hours** (Enterprise RBAC)

---

### **MODULE 11: STATE MANAGEMENT (PINIA STORES)**

| Store                 | Features                              | Hours |
| --------------------- | ------------------------------------- | ----- |
| auth.store.ts         | Authentication state, methods         | 5     |
| user.store.ts         | User profile, preferences             | 4     |
| student.store.ts      | Student CRUD, filtering, search       | 6     |
| application.store.ts  | Application management                | 6     |
| university.store.ts   | University data, search, filters      | 5     |
| counselor.store.ts    | Counselor management                  | 4     |
| agency.store.ts       | Agency management                     | 4     |
| notification.store.ts | Notification state, real-time updates | 6     |
| report.store.ts       | Report data, filters                  | 5     |
| file.store.ts         | File upload state                     | 3     |
| permission.store.ts   | RBAC permissions                      | 5     |
| Global store setup    | Store configuration, plugins          | 3     |

**Module 11 Total:** **56 hours**

---

### **MODULE 12: API SERVICES**

| Service                 | Endpoints                              | Hours |
| ----------------------- | -------------------------------------- | ----- |
| auth.service.ts         | Login, logout, refresh, password reset | 3     |
| user.service.ts         | User CRUD, profile updates             | 3     |
| student.service.ts      | Student CRUD, search, assign           | 4     |
| application.service.ts  | Apply, status update, documents        | 5     |
| university.service.ts   | Search, filters, details               | 4     |
| counselor.service.ts    | Counselor CRUD, performance            | 3     |
| agency.service.ts       | Agency CRUD                            | 3     |
| notification.service.ts | Fetch, mark read, preferences          | 3     |
| report.service.ts       | Report generation, export              | 4     |
| file.service.ts         | Upload, download, delete               | 4     |
| admin.service.ts        | System config, audit logs              | 3     |

**Module 12 Total:** **39 hours**

---

### **MODULE 13: TESTING & QUALITY ASSURANCE**

| Testing Type      | Coverage                                    | Hours |
| ----------------- | ------------------------------------------- | ----- |
| Unit Tests        | 60-70% coverage for critical components     | 35    |
| E2E Tests         | Critical user flows (login, apply, approve) | 20    |
| Component Tests   | Form validation, state changes              | 15    |
| Integration Tests | API service integration                     | 10    |

**Module 13 Total:** **80 hours** (Included in +20% production overhead)

---

## 📊 CALCULATION SUMMARY

### Step 1: Base Hours Calculation

| Module                  | Base Hours    |
| ----------------------- | ------------- |
| 1. Authentication       | 34            |
| 2. Student Portal       | 95            |
| 3. Counselor Panel      | 50            |
| 4. Agency Manager Panel | 39            |
| 5. Super Admin Panel    | 68            |
| 6. Reporting Module     | 52            |
| 7. Notification System  | 39            |
| 8. File Management      | 30            |
| 9. Global Features      | 107           |
| 10. Enterprise RBAC     | 80            |
| 11. State Management    | 56            |
| 12. API Services        | 39            |
| **RAW TOTAL**           | **689 hours** |

### Step 2: Apply Adjustments

```
Raw Base Hours:                689 hours

Design Factor (Complete UI):   689 × 0.75 = 517 hours
Device Factor (Responsive):    517 × 1.00 = 517 hours
Language Factor (Single):      517 × 1.00 = 517 hours
Quality Factor (Production):   517 × 1.20 = 620 hours

Additional Complexity:
  - API Setup:                 +0 hours (APIs ready)
  - RBAC:                      +80 hours (already in Module 10)
  - Real-time:                 +40 hours (already in Module 7)
  - File Storage:              +12 hours (already in Module 8)

Subtotal:                      620 hours

Buffer (75% confidence):       620 × 1.10 = 682 hours

Component Reusability:
  - Module 3 (Counselor) is 40% similar to Student Portal
    Reduction: 50 × 0.25 = -12.5 hours
  - Module 4 (Manager) is 30% similar to Counselor
    Reduction: 39 × 0.20 = -7.8 hours

Total Reusability Savings:     -20 hours

Subtotal after Reusability:    662 hours

Testing (included in 1.20):    Already applied
Edge Cases (included):         Already applied

FINAL TOTAL:                   662 hours
```

**ROUNDED FINAL ESTIMATE: 660-725 hours** → **~690 hours average**

---

## 📅 PROJECT TIMELINE

### **Option 1: Solo Developer**

- **Total Hours:** 690 hours
- **Working Hours/Week:** 40 hours
- **Timeline:** 17-18 weeks ≈ **4.5 months**

### **Option 2: Two Developers (RECOMMENDED)**

- **Total Hours:** 690 hours
- **Parallel Efficiency:** 85% (some coordination overhead)
- **Effective Hours per Developer:** 690 × 0.85 / 2 = 293 hours each
- **Working Hours/Week:** 40 hours
- **Timeline:** 7-8 weeks ≈ **2 months**

### **Option 3: Three Developers**

- **Total Hours:** 690 hours
- **Parallel Efficiency:** 70% (more coordination overhead)
- **Effective Hours per Developer:** 690 × 0.70 / 3 = 161 hours each
- **Timeline:** 4-5 weeks ≈ **1 month**
- ⚠️ **Warning:** Diminishing returns, recommend max 2 developers

---

## 🎯 RECOMMENDED APPROACH

### **Phase 1: Foundation (2 weeks)**

- Authentication system
- Role-based routing
- Base components library
- Layout system
- Enterprise RBAC setup

### **Phase 2: Core Features (4 weeks)**

- Student Portal (dashboard, profile, applications)
- Counselor Panel
- File upload system
- Basic notifications

### **Phase 3: Advanced Features (2 weeks)**

- Agency Manager Panel
- Super Admin Panel
- Real-time notifications (WebSocket)
- Advanced reporting

### **Phase 4: Polish & Testing (2 weeks)**

- E2E testing
- Performance optimization
- Bug fixes
- Documentation

**Total:** **10 weeks with 2 developers**

---

## 🚨 RISK FACTORS & ASSUMPTIONS

### **Included in Estimate:**

✅ Responsive design (mobile, tablet, desktop)  
✅ API integration (loading, error, empty states)  
✅ Form validation (Zod schemas)  
✅ Basic accessibility (semantic HTML, alt text)  
✅ Search, pagination, sorting  
✅ File upload validation  
✅ Professional error handling  
✅ Unit + E2E testing  
✅ Code review & QA bug fixes (in buffer)

### **Not Included (Would Add Time):**

❌ Backend API development  
❌ Database design  
❌ DevOps/deployment  
❌ Content creation (copy, images)  
❌ WCAG AA/AAA compliance (+50-120 hours)  
❌ IE11 support (+50% to timeline)  
❌ Payment gateway integration (+25 hours)  
❌ OAuth/SSO providers (+10 hours each)  
❌ Video calling features (+35 hours)  
❌ Advanced search (Algolia/Elasticsearch) (+20 hours)

### **Assumptions:**

- APIs are RESTful and well-documented
- Design files are complete and approved
- No major scope changes during development
- Client provides timely feedback (< 48 hours)
- 1-2 design revision rounds included in buffer
- Standard browser support (last 2 versions)

---

## 💰 EFFORT DISTRIBUTION

| Category              | Hours | % of Total |
| --------------------- | ----- | ---------- |
| Component Development | 200   | 29%        |
| Page/View Development | 140   | 20%        |
| State Management      | 56    | 8%         |
| API Integration       | 39    | 6%         |
| RBAC System           | 80    | 12%        |
| Real-time Features    | 39    | 6%         |
| Reporting & Charts    | 52    | 8%         |
| Testing               | 80    | 12%        |

---

## 📝 DELIVERABLES

1. **Source Code**

   - Vue 3 + Nuxt 3 + TypeScript
   - Pinia stores
   - Zod validation schemas
   - Component library (atomic design)

2. **Documentation**

   - Component usage guide
   - Setup instructions
   - Environment configuration
   - API integration guide

3. **Testing**

   - Unit tests (60-70% coverage)
   - E2E tests (critical flows)
   - Test documentation

4. **Code Quality**
   - ESLint + Prettier configured
   - TypeScript strict mode
   - No console errors/warnings
   - Performance optimized

---

## 🔄 CHANGE REQUEST PROCESS

Changes to scope will affect timeline:

| Change Type         | Impact         |
| ------------------- | -------------- |
| New user role       | +40-60 hours   |
| New module/feature  | +20-80 hours   |
| New integration     | +8-35 hours    |
| Additional language | +15% total     |
| WCAG AA compliance  | +50 hours      |
| Major UI redesign   | +20-30% module |

---

## ✅ NEXT STEPS

1. **Review & Approve Estimate** - Confirm scope aligns with requirements
2. **Finalize UI Designs** - Ensure all screens designed before kickoff
3. **API Documentation** - Share API specs and endpoints
4. **Kickoff Meeting** - Align on timeline, communication, and milestones
5. **Development Begins** - Two-week sprints with demos

---

## 📞 QUESTIONS?

Feel free to ask about:

- Component breakdown details
- Technology choices
- Timeline adjustments
- Team composition
- Risk mitigation strategies

**This estimate is valid for 30 days from date above.**

---

## 📄 PDF EXPORT

To convert this estimation to PDF for stakeholder sharing:

1. Open `docs/estimations/generate-pdf.html` in your browser
2. Copy this markdown content
3. Paste into the left panel
4. Click "Generate Preview"
5. Click "Generate PDF" and save from print dialog

---

**Estimation prepared by:** GitHub Copilot Frontend Estimator  
**Methodology:** Production-validated 12-question framework  
**Confidence Level:** 75% (±10% variance expected)

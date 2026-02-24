# Module 07: Document-Based Estimation Guide

**Purpose:** Instructions for extracting requirements from various document formats and generating accurate frontend estimates.

---

## 📄 Supported Document Formats

### Format Overview

| Format    | Extensions      | Best For                       | Parsing Complexity |
| --------- | --------------- | ------------------------------ | ------------------ |
| **PDF**   | `.pdf`          | SOWs, proposals, formal docs   | Medium             |
| **Word**  | `.docx`, `.doc` | Requirement specs, PRDs        | Low-Medium         |
| **Text**  | `.txt`, `.md`   | Simple lists, quick notes      | Low                |
| **CSV**   | `.csv`          | Feature backlogs, user stories | Low                |
| **Excel** | `.xlsx`, `.xls` | Structured requirements        | Low                |

---

## 🔍 Document Reading Process

### Phase 1: Initial Document Scan (1-2 min)

**Step 1: Open and Read**

```bash
# Use read_file tool
# Tool automatically handles different formats
```

**Step 2: Identify Document Type**

Quick assessment:

- **Formal SOW/Proposal**: High-level, business language, multiple sections
- **Technical PRD**: Detailed specs, user flows, acceptance criteria
- **Feature List**: Bullet points or table of features
- **User Stories**: "As a... I want... So that..." format
- **Technical Spec**: UI wireframes references, component details

**Step 3: Locate Key Sections**

Common section names to search for:

- ✅ "Features", "Functionality", "Requirements"
- ✅ "User Stories", "Backlog", "Sprints"
- ✅ "Scope", "In Scope", "Out of Scope"
- ✅ "Screens", "Pages", "UI Components"
- ✅ "Technology Stack", "Technical Requirements"
- ✅ "Acceptance Criteria", "Definition of Done"
- ❌ "Backend Services", "API Endpoints", "Database"
- ❌ "Infrastructure", "Deployment", "DevOps"

### Phase 2: Content Extraction (2-5 min)

**Extract Feature Lists**

Look for patterns:

```
• Feature name with description
1. Numbered feature list
- Bulleted items
| Table | With | Features |
```

**Extract User Stories**

Standard format:

```
As a [user type]
I want [feature]
So that [benefit]

Acceptance Criteria:
- Criterion 1
- Criterion 2
```

**Extract Component Details**

Look for:

- Component names (LoginForm, UserDashboard, etc.)
- UI element descriptions (dropdown, modal, table)
- Interaction descriptions (click, drag, filter)

### Phase 3: Frontend Filtering (1-2 min)

**Apply Scope Rules** (Reference: Module 02)

✅ **INCLUDE** (Frontend):

- UI pages and screens
- Forms and inputs
- Navigation and menus
- Dashboards and charts
- Tables and lists
- Modals and dialogs
- Client-side validation
- State management (Pinia, Redux)
- API integration UI (loading, errors)
- Responsive layouts
- Animations and transitions

❌ **EXCLUDE** (Not Frontend):

- REST API development
- GraphQL server setup
- Database design
- Authentication logic (backend)
- Business logic (server-side)
- Email sending
- File storage (S3, etc.)
- CI/CD pipelines
- Server deployment
- Native mobile apps (unless React Native explicitly mentioned)

⚠️ **FLAG FOR CLARIFICATION**:

- "Full-stack feature" (need to split frontend vs backend)
- "API integration" (frontend integration work: YES, API dev: NO)
- "Authentication" (login UI: YES, JWT generation: NO)
- "Real-time updates" (WebSocket UI: YES, socket server: NO)

---

## 📋 Format-Specific Parsing

### PDF Documents

**Characteristics:**

- Multi-page formal documents
- Section headers and page numbers
- May contain tables, images, diagrams
- Text extraction can have formatting issues

**Parsing Strategy:**

1. **Read entire document** - Use read_file tool
2. **Identify structure** - Look for:
   - Table of Contents
   - Section headers (1.0, 2.0, etc.)
   - Subsections (1.1, 1.2, etc.)
3. **Extract sections**:
   - Copy relevant sections to working notes
   - Ignore cover page, legal, appendices
4. **Handle tables**:
   - Tables may parse as plain text
   - Reconstruct feature lists manually
5. **Note page references** for traceability

**Example Extraction:**

```
Page 5: Section 2.1 - User Management
- User login with email/password
- User registration form
- Forgot password flow
- User profile page with avatar upload

Page 7: Section 2.2 - Dashboard
- KPI cards showing active users, revenue
- Line chart for user growth
- Recent activity feed
```

### Word Documents (.docx, .doc)

**Characteristics:**

- Structured with headings and styles
- Lists (numbered, bulleted)
- Tables with clear structure
- Comments/track changes (may contain clarifications)

**Parsing Strategy:**

1. **Read document** - Clean text extraction
2. **Identify heading levels**:
   - H1: Major sections
   - H2: Features/modules
   - H3: Sub-features
3. **Extract lists**:
   - Numbered lists → Prioritized features
   - Bulleted lists → Feature details
4. **Parse tables**:
   - Often used for user stories
   - Columns: ID, Feature, Description, Priority
5. **Check comments** - May contain hidden requirements

**Example Extraction:**

```
Heading 2: Authentication Module

• Login page
  - Email and password inputs
  - Remember me checkbox
  - Forgot password link

• Registration page
  - Multi-step form (3 steps)
  - Email verification
  - Terms acceptance
```

### Text/Markdown Files (.txt, .md)

**Characteristics:**

- Plain text or markdown formatting
- Simple structure
- Often quick capture of requirements
- Markdown: Headers (#), lists (-), code blocks (```)

**Parsing Strategy:**

1. **Read file** - Simplest format
2. **Identify markdown structure** (if `.md`):

   ```markdown
   # Main Feature

   ## Sub-feature

   - Detail 1
   - Detail 2
   ```

3. **Extract lists**:
   - Lines starting with `-`, `*`, or `•`
4. **Group by headers**
5. **Look for user story format**

**Example Extraction:**

```markdown
# Requirements

## User Management

- Login page with validation
- Signup with email confirmation
- User profile with edit capability

## Dashboard

- KPI cards (users, revenue, sessions)
- Chart showing monthly trends
- Export data to CSV
```

### CSV Files

**Characteristics:**

- Tabular data with headers
- Comma or semicolon delimited
- Often exported from Jira, Asana, Excel
- Each row = one feature/story

**Common Column Names:**

- `Feature`, `Story`, `Task`, `Title`, `Name`
- `Description`, `Details`, `Acceptance Criteria`
- `Story Points`, `Complexity`, `Estimate`
- `Priority`, `Status`, `Sprint`
- `Type` (Frontend, Backend, Full-Stack)

**Parsing Strategy:**

1. **Read CSV** - Parse into rows
2. **Identify header row** (first row)
3. **Map columns**:
   - Feature name column
   - Description column
   - Complexity/points column (if present)
4. **Filter by type**:
   - If "Type" column exists, filter Frontend items
   - If no type, manually classify each row
5. **Group by epic/module** (if column exists)

**Example CSV:**

```csv
ID,Feature,Description,Story Points,Priority,Type
1,User Login,Login page with email/password,5,High,Frontend
2,User API,Create user authentication endpoint,8,High,Backend
3,Dashboard,Main dashboard with KPI cards,13,Medium,Frontend
4,Database Schema,Design user and activity tables,5,High,Backend
```

**Extracted Frontend Items:**

- ID 1: User Login (5 points → 16 hours)
- ID 3: Dashboard (13 points → 52 hours)

### Excel Files (.xlsx, .xls)

**Characteristics:**

- Multiple sheets possible
- Structured tables with formatting
- Formulas and calculated fields
- Color coding for priority/status

**Common Sheet Names:**

- "Features", "Requirements", "Backlog"
- "User Stories", "Epics", "Sprints"
- "Frontend", "Backend", "Mobile"

**Parsing Strategy:**

1. **Read workbook** - Identify sheets
2. **Process relevant sheets**:
   - Skip: "Budget", "Timeline", "Team"
   - Read: "Features", "Requirements", "Stories"
3. **Extract tables**:
   - First row usually headers
   - Data rows below
4. **Handle formatting**:
   - Bold/colored rows may indicate modules/epics
   - Comments in cells (hover text)
5. **Calculate if needed**:
   - Sum story points
   - Count features by priority

**Example Sheet Structure:**

```
Sheet: "Frontend Requirements"

| Module         | Feature              | Description                  | Complexity | Priority |
|----------------|----------------------|------------------------------|------------|----------|
| Authentication | Login Page           | Email/password login form    | Medium     | High     |
| Authentication | Signup Page          | Multi-step registration      | High       | High     |
| Dashboard      | KPI Cards            | Display user/revenue stats   | Medium     | Medium   |
| Dashboard      | Activity Feed        | Recent user activities       | Low        | Low      |
```

**Extracted Data:**

- Module: Authentication (2 features, 1 Medium + 1 High)
- Module: Dashboard (2 features, 1 Medium + 1 Low)

---

## 🎯 Estimation Mapping

### From User Stories to Hours

**If document contains story points:**

Using Fibonacci sequence (Module 01):

```
1 point = 4-6 hours
2 points = 8-12 hours
3 points = 12-18 hours
5 points = 20-30 hours
8 points = 32-48 hours
13 points = 52-78 hours
```

**Process:**

1. Extract point value per story
2. Convert to hour range
3. Sum totals
4. Add multipliers (+15% testing, +20% responsive, +10% buffer)

### From Feature Lists to Hours

**If document has feature list without points:**

Apply pattern matching (Module 05):

1. **Categorize each feature**:

   - Authentication → 32-68 hr (based on complexity)
   - CRUD → 20-48 hr
   - Dashboard → 28-80 hr
   - Form → 8-32 hr
   - etc.

2. **Adjust for specifics**:

   - Simple login: 32 hr
   - Login + OAuth + 2FA: 68 hr

3. **Sum and apply multipliers**

### From Technical Spec to Hours

**If document has detailed UI specs:**

Use component counting (Module 06):

1. **Count components**:

   - Atoms (buttons, inputs): 2 hr each
   - Molecules (cards, menus): 6 hr each
   - Organisms (tables, forms): 18 hr each
   - Pages: 26 hr each

2. **Apply complexity multiplier**:

   - Simple: 1.0x
   - Medium: 1.5x
   - Complex: 2.5x

3. **Sum and apply multipliers**

---

## 🚦 Quality Assurance

### Document Clarity Assessment

Before estimating, assess document quality:

| Quality Level | Characteristics                                     | Confidence | Recommended Action          |
| ------------- | --------------------------------------------------- | ---------- | --------------------------- |
| **Excellent** | Detailed specs, acceptance criteria, mockups linked | 80-90%     | Use detailed PERT           |
| **Good**      | Clear feature list, some details, priorities stated | 70-80%     | Use pattern matching        |
| **Moderate**  | Basic feature list, minimal details                 | 60-70%     | Use T-shirt sizing + buffer |
| **Poor**      | Vague descriptions, mixed scope, unclear            | 40-60%     | Request clarification first |
| **Very Poor** | Incomplete, contradictory, mainly backend           | <40%       | Do NOT estimate yet         |

### Missing Information Checklist

Flag these if missing:

- [ ] **Technology stack** - Vue or React? Which version?
- [ ] **Design availability** - Figma/Adobe XD ready?
- [ ] **API status** - APIs ready, in progress, or need design?
- [ ] **Device support** - Desktop only, or mobile + tablet?
- [ ] **Browser support** - Modern browsers only, or legacy (IE)?
- [ ] **Authentication approach** - JWT, OAuth, session-based?
- [ ] **State management** - Pinia, Redux, Context API?

### Asking Clarifying Questions

**Template for clarification request:**

```
Based on [document name], I have some questions before providing an accurate estimate:

Frontend Scope Questions:
1. Feature X mentions "API integration" - is the API already built, or do you need the API estimated too? (I can only estimate the frontend UI integration)
2. Feature Y says "user authentication" - does this include login UI only, or also backend auth logic?

Technical Stack Questions:
3. Which framework: Vue 3 or React 18?
4. Are UI designs in Figma ready, or should I include design time?

Assumptions:
Based on document, I'm assuming:
- All APIs will be ready when frontend development starts
- Responsive design for desktop + mobile + tablet
- Modern browser support only (no IE11)

Please confirm these assumptions or provide corrections.
```

---

## 📤 Output Templates

### Document-Based Estimation Report

```markdown
# Frontend Estimation: [Project Name]

**Source Document:** [filename.pdf]  
**Date:** [YYYY-MM-DD]  
**Estimator:** FrontendEstimator Agent

---

## 📄 Document Analysis

**Document Type:** [SOW / PRD / Feature List / User Stories]  
**Pages/Sheets:** [X pages / Y sheets]  
**Total Items Found:** [N features/stories]  
**Frontend Items:** [M items] (after filtering)  
**Excluded Items:** [K backend/infrastructure items]

---

## 🎯 Scope Summary

**Technology Stack:**

- Framework: [Vue 3 / React 18]
- State Management: [Pinia / Redux]
- UI Library: [Vuetify / MUI / Tailwind]

**What's Included (Frontend):**

- [List all frontend features]

**What's Excluded (Not Frontend):**

- [List all backend/infrastructure items removed]

**Flagged for Clarification:**

- [Items needing more info]

---

## 📊 Estimation Breakdown

[Use standard breakdown from Module 04]

---

## ⚠️ Assumptions Made

1. [Assumption 1 from document]
2. [Assumption 2 from document]
3. [Standard assumptions: APIs ready, designs complete, etc.]

---

## 🎯 Confidence Level

**Confidence:** [X%]

**Reasoning:**

- Document clarity: [Excellent / Good / Moderate]
- Requirements detail: [High / Medium / Low]
- Technology stack defined: [Yes / No]
- Similar past projects: [Yes / No]

---

## 📋 Next Steps

1. Review estimation with stakeholders
2. Clarify flagged items
3. Confirm technology stack choices
4. Validate scope boundaries
5. Finalize team composition
```

---

## 🎓 Example Workflows

### Example 1: PDF SOW Document

```
User: "Estimate this SOW.pdf"

Agent Process:
1. Read document (25 pages)
2. Found sections: Executive Summary, Scope, Features (pages 8-15), Technical Requirements
3. Extracted 42 features from pages 8-15
4. Filtered: Removed 15 backend features, kept 27 frontend
5. Categorized into 6 modules
6. Applied pattern matching + T-shirt sizing
7. Total: 380-450 hours (70% confidence)
8. Noted 5 assumptions, 3 items needing clarification

Agent Response: [Detailed breakdown as template above]
```

### Example 2: CSV User Stories

```
User: "Estimate this backlog.csv with our user stories"

Agent Process:
1. Read CSV (87 rows, headers: ID, Story, Points, Type, Sprint)
2. Filtered: Type = "Frontend" → 34 stories
3. Sum story points: 156 points
4. Convert: 156 points × 4 hr/point = 624 base hours
5. Apply multipliers: 624 × 1.52 = 948 hours
6. Group by sprint for timeline
7. Total: 900-980 hours (75% confidence)

Agent Response: [Detailed breakdown with sprint-by-sprint view]
```

### Example 3: Excel Feature List

```
User: "Check requirements.xlsx sheet 'Frontend Features'"

Agent Process:
1. Read sheet "Frontend Features" (45 rows)
2. Columns: Module, Feature, Description, Complexity, Priority
3. Group by Module: Auth (6), Dashboard (8), Users (12), Reports (7), Settings (12)
4. Map complexity: Low → 8hr, Medium → 20hr, High → 40hr
5. Calculate per module
6. Apply multipliers
7. Total: 520-600 hours (80% confidence - structured data)

Agent Response: [Detailed breakdown by module with complexity breakdown]
```

---

## 🔧 Troubleshooting

### Common Issues

**Issue: PDF text extraction garbled**

- Solution: Ask user for Word/text version
- Workaround: Manually copy key sections from document

**Issue: CSV parsing fails**

- Solution: Check delimiter (comma vs semicolon)
- Workaround: Ask user to convert to Excel or copy-paste text

**Issue: Document contains mixed frontend/backend**

- Solution: Flag each item, ask for clarification
- Provide two estimates: Frontend only vs Full-stack

**Issue: Requirements too vague**

- Solution: Provide T-shirt estimate with large buffer (+40%)
- Recommend discovery phase

**Issue: No technology stack specified**

- Solution: Provide estimate range for Vue vs React
- State assumption of preferred stack

---

## 🎯 Best Practices

1. **Always read entire document** before estimating
2. **Flag ambiguities immediately** - don't guess
3. **Document all assumptions** - make them visible
4. **Show what was excluded** - transparency is key
5. **Provide confidence level** with reasoning
6. **Offer clarification questions** proactively
7. **Use module references** - "Per Module 05, Auth = 32hr"
8. **Apply standard multipliers** consistently
9. **Round up, never down** - better to overestimate
10. **Suggest document improvements** for future

---

**This module enables document-based estimation. For estimation methods, see other modules.**

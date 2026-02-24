# Module 05: Common Patterns & Reusable Estimates

**Purpose:** Pre-calculated estimates for experienced teams with proven velocity.

**⚠️ Base hours optimized for modern frameworks (Vuetify/Tailwind). ALL estimates INCLUDE responsive design and API integration!**

**Assumption:** Senior/Mid-level developers, modern tooling (Vite, Vuetify/Tailwind), component library available, clear requirements.

**What's INCLUDED in ALL base hour estimates:**

- ✅ Responsive design (mobile/tablet/desktop breakpoints)
- ✅ API integration (loading, errors, data display)
- ✅ Form validation
- ✅ Error handling
- ✅ Loading states
- ✅ Empty states

**Standard Multipliers:**

- Professional dev (testing + edge cases): +20%
- Confidence buffer (includes rework): +5% to +20%
- **Total typical:** × 1.20 × 1.10 = 1.32x (~32% overhead)

---

## 🔐 Authentication Patterns

### Login/Signup Suite (10-16 hours base)

**What's Included:\*\***

- Login page with email/password
- Signup/registration page
- Forgot password flow
- Reset password page
- Form validation with Zod
- Error messages
- Loading states
- Remember me functionality
- Social login buttons (UI only)
- **Responsive design (INCLUDED)**
- **API integration (INCLUDED)**

**Breakdown (Base Hours - Responsive + API INCLUDED):**

| Component               | Hours        | Notes                                                |
| ----------------------- | ------------ | ---------------------------------------------------- |
| Login form              | 2-3 hr       | Email, password, Zod validation (copy from library)  |
| Signup form             | 3-5 hr       | More fields, terms acceptance                        |
| Forgot password         | 1-2 hr       | Email input, success message                         |
| Reset password          | 1-2 hr       | New password, confirmation                           |
| Validation logic        | 1-2 hr       | Zod schemas (reusable)                               |
| API integration         | 2-3 hr       | Login, signup, password endpoints with loading/error |
| Error handling          | 1-2 hr       | Invalid credentials, server errors                   |
| Loading/disabled states | 1 hr         | Button states, spinners                              |
| **Base Total**          | **10-17 hr** | Responsive + API INCLUDED (no separate charges)      |

**With Standard Adjustments:**

- Professional dev (+20%): 2-3 hr
- Confidence buffer (+10% typical): 1-2 hr
- **Final Total: 13-22 hours** (depending on confidence level)

**Complexity Adjustments:**

- **Simple** (email/pass only): 10 hr base → 13 hr final
- **Medium** (+ social buttons, remember me): 13 hr base → 17 hr final
- **Complex** (+ 2FA, OAuth, passwordless): 16 hr base → 21 hr final

**Dependencies:**

- API: `/auth/login`, `/auth/register`, `/auth/forgot-password`, `/auth/reset-password`
- Email service: For reset password emails

---

## 👤 User Management CRUD (7-14 hours base)

### Standard User CRUD (7-10 hours base)

**What's Included:**

- User list/table page with Vuetify DataTable
- Create user form
- Edit user form
- Delete confirmation
- Search & filters
- Pagination
- Sorting
- **Responsive design (INCLUDED)**
- **API integration (INCLUDED)**

**Breakdown (Base Hours - Responsive + API INCLUDED):**

| Component              | Hours        | Notes                                               |
| ---------------------- | ------------ | --------------------------------------------------- |
| User list table        | 2-3 hr       | Vuetify v-data-table (pre-built sorting/pagination) |
| Create form            | 1-2 hr       | Name, email, role fields with Zod                   |
| Edit form              | 1-2 hr       | Same as create, pre-filled                          |
| Delete modal           | 1 hr         | Vuetify confirmation dialog                         |
| Search bar             | 1 hr         | Real-time search with debounce                      |
| Filters (role, status) | 1-2 hr       | Vuetify dropdowns, apply/clear                      |
| API integration        | 2-3 hr       | CRUD endpoints with error handling                  |
| Error handling         | 1 hr         | Validation, server errors, toasts                   |
| **Base Total**         | **10-16 hr** | Responsive + API INCLUDED                           |

**With Standard Adjustments (v5.0):**

- Professional dev (+20%): 2-3 hr
- Confidence buffer (+10% typical): 1-2 hr
- **Final Total: 13-19 hours**

**Complexity Adjustments:**

- **Simple** (basic fields, no filters): 8-10 hr base → 10-13 hr final
- **Medium** (standard CRUD + search/filter): 10-14 hr base → 13-18 hr final
- **Complex** (+ permissions, bulk actions, export): 15-21 hr base → 19-28 hr final

**Dependencies:**

- API: `/users` (GET, POST, PUT, DELETE)
- Permissions: Role-based access control

### User Profile Page (6-12 hours base)

**What's Included:**

- Profile view page
- Edit profile form
- Avatar upload
- Password change
- Account settings

**Breakdown:**

| Component        | Hours     | Notes                         |
| ---------------- | --------- | ----------------------------- |
| Profile view     | 1-2 hr    | Display user info, avatar     |
| Edit form        | 3 hr      | Name, email, bio, phone       |
| Avatar upload    | 3 hr      | File picker, preview, crop    |
| Change password  | 2 hr      | Current, new, confirm         |
| Settings toggles | 1 hr      | Email notifications, etc.     |
| API integration  | 2 hr      | Update profile, upload avatar |
| Validation       | 1 hr      | Email, password rules         |
| **Base Total**   | **13 hr** | Responsive + API INCLUDED     |

**With Standard Adjustments (v5.0):**

- Professional dev (+20%): 3 hr
- Confidence buffer (+10%): 1 hr
- **Final Total: 17 hours**

**Simplified Version** (no avatar upload): 10 hr base → 13 hr final

---

## 📊 Data Table/List Patterns (9-21 hours base)

### Simple Table (9-14 hours base)

**What's Included:**

- Table with columns
- Pagination
- Sorting (1 column)
- Basic search

**Breakdown:**

| Component       | Hours       | Notes                     |
| --------------- | ----------- | ------------------------- |
| Table component | 3 hr        | Headers, rows, styling    |
| Data fetching   | 2 hr        | API call, loading state   |
| Pagination      | 1-2 hr      | Page numbers, prev/next   |
| Sorting         | 1 hr        | Single column, icons      |
| Search          | 1-2 hr      | Input, debounce, filter   |
| Error states    | 1 hr        | No data, error message    |
| **Base Total**  | **9-11 hr** | Responsive + API INCLUDED |

**With Standard Adjustments (v5.0):**

- Professional dev (+20%): 2-3 hr
- Confidence buffer (+10%): 1 hr
- **Final Total: 12-15 hours**

**Complexity Adjustments:**

- **Simple** (display only, no interactions): 9 hr base → 12 hr final
- **Medium** (sorting, pagination, search): 12 hr base → 16 hr final
- **Complex** (filters, bulk actions, column config): 21 hr base → 27 hr final

### Complex Data Table (15-21 hours base)

**Additional Features:**

- Multi-column sorting
- Advanced filters (date range, multi-select)
- Bulk actions (select all, delete multiple)
- Export to CSV
- Column visibility toggle
- Row expansion (details view)

**Additional Hours:** +9 hr base → +14 hr final

**Dependencies:**

- API: Pagination params, filter support, bulk operations

---

## 📈 Dashboard Patterns (15-42 hours base)

### Simple Dashboard (15-23 hours base)

**What's Included:**

- 4-6 KPI cards (e.g., total users, revenue)
- 2 simple charts (line, bar)
- Recent activity list
- Quick actions

**Breakdown:**

| Component            | Hours     | Notes                             |
| -------------------- | --------- | --------------------------------- |
| Dashboard layout     | 2 hr      | Grid, responsive                  |
| KPI cards (×6)       | 5 hr      | ~45min each: fetch, display, icon |
| Line chart           | 3 hr      | Chart library integration         |
| Bar chart            | 2 hr      | Similar to line                   |
| Activity list        | 2 hr      | Fetch, display, styling           |
| Quick action buttons | 1 hr      | Icons, links                      |
| API integration      | 2 hr      | Multiple endpoints                |
| Loading states       | 2 hr      | Skeletons for cards/charts        |
| **Base Total**       | **19 hr** | Responsive + API INCLUDED         |

**With Standard Adjustments (v5.0):**

- Professional dev (+20%): 4 hr
- Confidence buffer (+10%): 2 hr
- **Final Total: 25 hours**

**Simplified** (2 charts, 4 cards): 15 hr base → 20 hr final

### Complex Dashboard (30-42 hours base)

**Additional Features:**

- 8-10 KPI cards
- 4-6 different chart types
- Real-time updates (WebSocket)
- Date range filter
- Export dashboard to PDF
- Customizable layout (drag-drop)

**Additional Hours:** +21 hr base → +32 hr final

**Chart Library Recommendations:**

- Chart.js: Simple, lightweight
- D3.js: Complex, custom charts (+30% time)
- Recharts (React): Declarative, easy (+0% time)

**Dependencies:**

- API: Multiple analytics endpoints
- WebSocket: Real-time data (if applicable)

---

## 📝 Form Patterns (5-18 hours base)

### Simple Form (5-8 hours base)

**What's Included:**

- 3-5 input fields
- Basic validation
- Submit button
- Success/error messages

**Breakdown:**

| Component         | Hours      | Notes                     |
| ----------------- | ---------- | ------------------------- |
| Form layout       | 1 hr       | Fields, labels, spacing   |
| Input fields (×5) | 2-3 hr     | Text, email, select       |
| Validation        | 1-2 hr     | Required, email, min/max  |
| Submit logic      | 1 hr       | API call, loading state   |
| Error handling    | 1 hr       | Display errors, toast     |
| **Base Total**    | **6-8 hr** | Responsive + API INCLUDED |

**With Standard Adjustments (v5.0):**

- Professional dev (+20%): 1-2 hr
- Confidence buffer (+10%): 1 hr
- **Final Total: 8-11 hours**

**Simplified** (3 fields, minimal validation): 5 hr base → 7 hr final

### Multi-Step Form (11-18 hours base)

**What's Included:**

- 3-5 steps
- Progress indicator
- Previous/Next navigation
- Step validation
- Review step
- Submit

**Breakdown:**

| Component              | Hours     | Notes                         |
| ---------------------- | --------- | ----------------------------- |
| Stepper component      | 2 hr      | Progress bar, step labels     |
| Step 1 form (5 fields) | 3 hr      | Personal info                 |
| Step 2 form (5 fields) | 3 hr      | Address, contact              |
| Step 3 form (5 fields) | 3 hr      | Preferences, settings         |
| Review step            | 2 hr      | Display all data              |
| Navigation logic       | 2 hr      | Next, back, validation checks |
| State management       | 2 hr      | Store data across steps       |
| Submit logic           | 2 hr      | Combine data, API call        |
| **Base Total**         | **19 hr** | Responsive + API INCLUDED     |

**With Standard Adjustments (v5.0):**

- Professional dev (+20%): 4 hr
- Confidence buffer (+10%): 2 hr
- **Final Total: 25 hours**

**Simplified** (2 steps, 3 fields each): 14 hr base → 18 hr final

---

## 🔍 Search & Filter Patterns (6-18 hours base)

### Simple Search (6-9 hours base)

**What's Included:**

- Search input with icon
- Debounced search
- Clear button
- Loading indicator
- No results message

**Breakdown:**

| Component       | Hours    | Notes                        |
| --------------- | -------- | ---------------------------- |
| Search input UI | 1 hr     | Input, icon, clear button    |
| Debounce logic  | 1 hr     | 500ms delay, cancel previous |
| API integration | 2 hr     | Search endpoint, params      |
| Results display | 2 hr     | Highlight matches, count     |
| Loading state   | 1 hr     | Spinner during search        |
| Empty state     | 1 hr     | No results found message     |
| **Base Total**  | **8 hr** | Responsive + API INCLUDED    |

**With Standard Adjustments (v5.0):**

- Professional dev (+20%): 2 hr
- Confidence buffer (+10%): 1 hr
- **Final Total: 11 hours**

### Advanced Filters (9-18 hours base)

**What's Included:**

- Multiple filter types (dropdown, date, checkbox)
- Filter panel (collapsible)
- Apply/Clear buttons
- Active filters display
- Filter persistence (URL params)

**Breakdown:**

| Component             | Hours     | Notes                      |
| --------------------- | --------- | -------------------------- |
| Filter panel UI       | 2 hr      | Layout, collapse animation |
| Dropdown filters (×3) | 3 hr      | Options, selection         |
| Date range filter     | 2 hr      | Date pickers, validation   |
| Checkbox filters (×5) | 2 hr      | Multi-select               |
| Apply/Clear logic     | 2 hr      | Combine filters, reset     |
| URL params sync       | 2 hr      | Read/write to URL          |
| Active filters chips  | 2 hr      | Display, remove individual |
| API integration       | 2 hr      | Build query params         |
| **Base Total**        | **17 hr** | Responsive + API INCLUDED  |

**With Standard Adjustments (v5.0):**

- Professional dev (+20%): 3 hr
- Confidence buffer (+10%): 2 hr
- **Final Total: 22 hours**

**Medium Complexity** (3 filters, no URL sync): 12 hr base → 16 hr final

---

## 📁 File Upload Patterns (6-15 hours base)

### Simple Upload (6-9 hours base)

**What's Included:**

- File picker button
- Single file upload
- Progress bar
- Success/error message
- File size/type validation

**Breakdown:**

| Component       | Hours    | Notes                         |
| --------------- | -------- | ----------------------------- |
| File input UI   | 1 hr     | Button, hidden input          |
| File validation | 2 hr     | Size, type, extension checks  |
| Upload logic    | 2 hr     | FormData, API call            |
| Progress bar    | 1 hr     | Show upload percentage        |
| Error handling  | 1 hr     | Too large, wrong type, failed |
| Success message | 1 hr     | File uploaded, preview        |
| **Base Total**  | **8 hr** | Responsive + API INCLUDED     |

**With Standard Adjustments (v5.0):**

- Professional dev (+20%): 2 hr
- Confidence buffer (+10%): 1 hr
- **Final Total: 11 hours**

### Advanced Upload (11-15 hours base)

**Additional Features:**

- Multiple file upload
- Drag & drop zone
- File preview (image, PDF)
- Remove before upload
- Chunked upload (large files)

**Additional Hours:** +6 hr base → +9 hr final

**Dependencies:**

- API: File upload endpoint, multipart/form-data support
- Storage: S3, Cloudinary, or backend storage

---

## 📢 Notification/Toast Patterns (5-9 hours base)

### Toast Notification System (5-6 hours base)

**What's Included:**

- Success toast
- Error toast
- Warning toast
- Info toast
- Auto-dismiss
- Queue management (multiple toasts)

**Breakdown:**

| Component       | Hours    | Notes                        |
| --------------- | -------- | ---------------------------- |
| Toast component | 2 hr     | Styled for 4 types           |
| Toast container | 2 hr     | Position, stacking           |
| Queue logic     | 2 hr     | Show multiple, dismiss order |
| Auto-dismiss    | 1 hr     | Timeout, manual close        |
| Animation       | 1 hr     | Slide in/out                 |
| **Base Total**  | **8 hr** | Before multipliers           |

**With Standard Adjustments (v5.0):**

- Professional dev (+20%): 2 hr
- Confidence buffer (+10%): 1 hr
- **Final Total: 11 hours**

**Simplified** (no queue, single toast): 5 hr base → 7 hr final

---

## 🗺️ Navigation Patterns (5-12 hours base)

### Top Navigation (5-8 hours base)

**What's Included:**

- Logo
- Navigation links (5-7)
- User menu dropdown
- Mobile hamburger menu
- Active link highlighting

**Breakdown:**

| Component        | Hours    | Notes                     |
| ---------------- | -------- | ------------------------- |
| Nav bar layout   | 1 hr     | Logo, links, user menu    |
| Navigation links | 1 hr     | Routing, active state     |
| User dropdown    | 2 hr     | Profile, settings, logout |
| Mobile menu      | 2 hr     | Hamburger, slide panel    |
| Responsive       | 1 hr     | Breakpoints, hide/show    |
| **Base Total**   | **7 hr** | Responsive INCLUDED       |

**With Standard Adjustments (v5.0):**

- Professional dev (+20%): 1 hr
- Confidence buffer (+10%): 1 hr
- **Final Total: 9 hours**

### Sidebar Navigation (6-9 hours base)

**What's Included:**

- Collapsible sidebar
- Nested menu items
- Icons for each item
- Active highlighting
- Mobile overlay

**Breakdown:**

| Component       | Hours     | Notes                   |
| --------------- | --------- | ----------------------- |
| Sidebar layout  | 2 hr      | Fixed position, width   |
| Menu items      | 2 hr      | Icons, labels, routing  |
| Nested items    | 2 hr      | Expand/collapse logic   |
| Collapse button | 1 hr      | Toggle width, icon only |
| Mobile overlay  | 2 hr      | Full screen, backdrop   |
| Active state    | 1 hr      | Highlight current page  |
| **Base Total**  | **10 hr** | Responsive INCLUDED     |

**With Standard Adjustments (v5.0):**

- Professional dev (+20%): 2 hr
- Confidence buffer (+10%): 1 hr
- **Final Total: 13 hours**

---

## 🎨 Page Layout Patterns (2-9 hours base)

### Simple Page (2-4 hours base)

**What's Included:**

- Page container
- Header with title
- Content area
- Basic styling

**Breakdown:**

| Component        | Hours    | Notes                 |
| ---------------- | -------- | --------------------- |
| Layout component | 1 hr     | Container, padding    |
| Page header      | 1 hr     | Title, breadcrumbs    |
| Content area     | 1 hr     | Max width, responsive |
| **Base Total**   | **3 hr** | Responsive INCLUDED   |

**With Standard Adjustments (v5.0):**

- Professional dev (+30%): 1 hr
- Confidence buffer (+10%): 0.5 hr
- **Final Total: 5 hours**

### Complex Page Layout (6-9 hours base)

**Additional Features:**

- Breadcrumbs
- Page actions (buttons)
- Tabs
- Split panels
- Sticky header

**Additional Hours:** +5 hr base → +7 hr final

---

## 🔔 Real-Time Features (9-21 hours base)

### WebSocket Integration (9-14 hours base)

**What's Included:**

- WebSocket connection setup
- Connection state management
- Reconnection logic
- Message parsing
- Update UI on message

**Breakdown:**

| Component         | Hours     | Notes                          |
| ----------------- | --------- | ------------------------------ |
| WebSocket service | 3 hr      | Connect, disconnect, reconnect |
| Connection status | 1 hr      | Online, offline, reconnecting  |
| Message handling  | 2 hr      | Parse, dispatch to components  |
| Component updates | 3 hr      | Update state on new data       |
| Error handling    | 2 hr      | Connection failed, retry       |
| **Base Total**    | **11 hr** | Responsive + API INCLUDED      |

**With Standard Adjustments (v5.0):**

- Professional dev (+20%): 2 hr
- Confidence buffer (+10%): 1 hr
- **Final Total: 14 hours**

**Dependencies:**

- Backend: WebSocket server (Socket.IO, native WS)

---

## 🎯 Modal/Dialog Patterns (3-8 hours base)

### Simple Modal (3-5 hours base)

**What's Included:**

- Modal component
- Open/close logic
- Backdrop click to close
- ESC key to close
- Content slot

**Breakdown:**

| Component         | Hours    | Notes                     |
| ----------------- | -------- | ------------------------- |
| Modal component   | 2 hr     | Position, animation       |
| Backdrop          | 1 hr     | Dark overlay, click close |
| Close button      | 1 hr     | X icon, functionality     |
| ESC key handler   | 1 hr     | Event listener            |
| Content rendering | 1 hr     | Slot/children prop        |
| **Base Total**    | **6 hr** | Responsive INCLUDED       |

**With Standard Adjustments (v5.0):**

- Professional dev (+30%): 2 hr
- Confidence buffer (+10%): 1 hr
- **Final Total: 9 hours**

### Confirmation Modal (5-8 hours base)

**Additional Features:**

- Title, message, icon
- Confirm/Cancel buttons
- Async confirm action
- Loading state
- Success/error feedback

**Additional Hours:** +3 hr base → +4 hr final

---

## 📊 Quick Reference Table (v5.0 - Recalibrated)

### Pattern Estimates Summary

**ALL estimates include responsive design and API integration in base hours!**
**v5.0 Standard adjustments: +20% professional dev, +10% buffer = ×1.32 typical**

| Pattern             | Base Hours | With Adjustments (v5.0) |
| ------------------- | ---------- | ----------------------- |
| **Authentication**  | 12-18 hr   | 18-27 hr                |
| **User CRUD**       | 8-12 hr    | 12-18 hr                |
| **User Profile**    | 6-12 hr    | 9-18 hr                 |
| **Data Table**      | 9-14 hr    | 14-21 hr                |
| **Dashboard**       | 15-23 hr   | 23-35 hr                |
| **Form**            | 5-8 hr     | 8-12 hr                 |
| **Multi-Step Form** | 11-18 hr   | 17-27 hr                |
| **Search**          | 6-9 hr     | 9-14 hr                 |
| **Filters**         | 9-18 hr    | 14-27 hr                |
| **File Upload**     | 6-9 hr     | 9-14 hr                 |
| **Toast System**    | 5-6 hr     | 8-9 hr                  |
| **Top Nav**         | 5-8 hr     | 8-12 hr                 |
| **Sidebar Nav**     | 6-9 hr     | 9-14 hr                 |
| **Simple Page**     | 2-4 hr     | 3-6 hr                  |
| **Modal**           | 3-5 hr     | 5-8 hr                  |
| **WebSocket**       | 9-14 hr    | 14-21 hr                |

_Note: These are BASE hours with standard multipliers applied. Additional RBAC (+20-80hr), Real-time (+5-40hr), WCAG (+50-120hr), or Third-party integrations (+2-40hr each) calculated separately._

---

## 🧮 Quick Estimation Formula (v5.0)

```
1. Identify patterns from user requirements
2. Match to complexity level from table above
3. Sum all BASE pattern hours
4. Add custom feature hours (if any)
5. Add hidden complexity costs:
   - RBAC: Basic +20hr, Advanced +60hr, Enterprise +80hr
   - Real-time: Polling +5hr, WebSocket +40hr per module
   - WCAG: AA +50hr, AAA +120hr
   - Third-party: OAuth +10hr, Payment +25hr, Maps +15hr, etc.
6. Apply standard multipliers:
   - Professional dev (testing + edge cases): × 1.30
   - Confidence buffer (includes rework): × 1.10-1.25
7. Provide range: ±15%

Example (v5.0):
- Auth (Medium): 15 hr base
- User CRUD (Medium): 10 hr base
- Dashboard (Simple): 19 hr base
- Data Table (Medium): 12 hr base
Base Total: 56 hours

+ RBAC (Basic): +20 hr
Subtotal: 76 hours

× Professional dev (1.30): 99 hours
× Confidence buffer (1.15): 114 hours

Final Range: 97-131 hours (±15%)

Compare to v4.0 (same scope without RBAC would be ~95hr)
```

---

## 🎓 Usage Tips

**When to Use Patterns:**

- ✅ Requirements match 80%+ of pattern
- ✅ Need quick estimate (10-15 min)
- ✅ User wants ballpark range

**When NOT to Use Patterns:**

- ❌ Highly custom/unique feature
- ❌ Pattern match <60%
- ❌ Need detailed task breakdown

**Adjusting Patterns:**

- Add 20% if design is wireframe-only
- Subtract 10% if using robust component library
- Add 15% if integrating third-party service
- Add 30% if team is junior

### Component Reusability Multiplier (v5.0 - More Realistic)

**Apply these reductions for similar components:**

| Instance         | Reduction | Example (Base: 20 hr) |
| ---------------- | --------- | --------------------- |
| First instance   | 0%        | 20 hr                 |
| Second instance  | -20%      | 16 hr                 |
| Third instance   | -25%      | 15 hr                 |
| Fourth+ instance | -30%      | 14 hr                 |

**Total time for 4 CRUD pages:** 20 + 16 + 15 + 14 = 65 hr (vs 80 hr without reusability)

**Note:** v5.0 uses more conservative reusability estimates (max 30% vs old 40%) based on real project data showing each instance still requires unique business logic, validation, and edge cases.

---

**This module provides reusable patterns. For detailed calculation methods, see `01_estimation_methods.md`.**

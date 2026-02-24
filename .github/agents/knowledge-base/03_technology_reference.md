# Module 03: Technology Reference - Vue.js & React.js

**Purpose:** Framework-specific estimation patterns, component libraries, and technology multipliers.

---

## 🎨 Vue.js 3 Estimation Patterns

### Core Vue 3 Features

| Feature                         | Base Hours | Complexity Factors                           |
| ------------------------------- | ---------- | -------------------------------------------- |
| **Composition API Component**   | 3-6 hr     | + Props/emits (+1 hr), + Composables (+2 hr) |
| **Options API Component**       | 4-8 hr     | Legacy pattern, +20% vs Composition          |
| **Pinia Store Module**          | 4-8 hr     | + Actions (+2 hr), + Getters (+1 hr)         |
| **Vue Router Route**            | 2-4 hr     | + Guards (+2 hr), + Params (+1 hr)           |
| **Composable (reusable logic)** | 2-6 hr     | + TypeScript (+30%), + Tests (+50%)          |
| **Custom Directive**            | 4-8 hr     | Rarely needed, complex                       |
| **Plugin Integration**          | 4-12 hr    | Depends on plugin complexity                 |

### Vue 3 Component Complexity

**Simple Component (3-5 hr):**

```vue
<script setup lang="ts">
// 1-2 props, local state only
// No API calls, minimal logic
</script>
```

**Example:** Button, Badge, Icon wrapper

**Medium Component (6-12 hr):**

```vue
<script setup lang="ts">
// 3-5 props, emits
// Local + composable state
// 1-2 API calls
// Form validation
</script>
```

**Example:** Search bar, User card, Date picker

**Complex Component (16-32 hr):**

```vue
<script setup lang="ts">
// 6+ props, multiple emits
// Store integration
// Multiple API calls
// Complex state management
// Error boundaries
</script>
```

**Example:** Data table, Rich text editor, Calendar

---

## 📚 LIBRARY LEARNING CURVE

**When team must learn a NEW library, add time for learning, setup, and mistakes:**

### Learning Curve Categories

| Library Complexity | Learning Time | Add to Estimate | Examples                          |
| ------------------ | ------------- | --------------- | --------------------------------- |
| **Simple**         | 2-4 hr        | +10%            | Chart.js, date-fns, lodash        |
| **Medium**         | 4-8 hr        | +20%            | TanStack Table, VeeValidate, Zod  |
| **Complex**        | 8-16 hr       | +30%            | D3.js, ProseMirror, GSAP          |
| **Very Complex**   | 16-32 hr      | +40%            | Three.js, WebRTC, Blockchain libs |

### Library-Specific Learning Times

**Vue Ecosystem:**

| Library           | Complexity | First-time Add | Subsequent Uses |
| ----------------- | ---------- | -------------- | --------------- |
| **VeeValidate**   | Medium     | +20% (+8 hr)   | 0%              |
| **Vue I18n**      | Medium     | +20% (+6 hr)   | 0%              |
| **VueUse**        | Simple     | +10% (+2 hr)   | 0%              |
| **TipTap**        | Complex    | +30% (+12 hr)  | +5%             |
| **Vue Flow**      | Complex    | +30% (+16 hr)  | +10%            |
| **FullCalendar**  | Medium     | +20% (+10 hr)  | 0%              |
| **Vue Draggable** | Simple     | +10% (+3 hr)   | 0%              |
| **Vue ChartJS**   | Simple     | +10% (+4 hr)   | 0%              |

**React Ecosystem:**

| Library             | Complexity   | First-time Add | Subsequent Uses |
| ------------------- | ------------ | -------------- | --------------- |
| **React Hook Form** | Medium       | +20% (+6 hr)   | 0%              |
| **TanStack Table**  | Medium       | +20% (+12 hr)  | +5%             |
| **TanStack Query**  | Medium       | +20% (+8 hr)   | 0%              |
| **Framer Motion**   | Medium       | +20% (+8 hr)   | +5%             |
| **React DnD**       | Complex      | +30% (+12 hr)  | +10%            |
| **React Flow**      | Complex      | +30% (+16 hr)  | +10%            |
| **Slate.js**        | Very Complex | +40% (+24 hr)  | +15%            |
| **Recharts**        | Simple       | +10% (+4 hr)   | 0%              |

**Shared Libraries:**

| Library            | Complexity   | First-time Add | Subsequent Uses |
| ------------------ | ------------ | -------------- | --------------- |
| **D3.js**          | Complex      | +30% (+20 hr)  | +15%            |
| **Three.js**       | Very Complex | +40% (+32 hr)  | +20%            |
| **GSAP**           | Complex      | +30% (+12 hr)  | +10%            |
| **Socket.io**      | Medium       | +20% (+8 hr)   | 0%              |
| **Stripe**         | Medium       | +20% (+12 hr)  | 0%              |
| **Auth0**          | Medium       | +20% (+10 hr)  | 0%              |
| **MapBox/Leaflet** | Medium       | +20% (+12 hr)  | +5%             |
| **PDF.js**         | Complex      | +30% (+12 hr)  | +5%             |
| **Video.js**       | Medium       | +20% (+8 hr)   | 0%              |

### Detection Workflow

```bash
# ALWAYS ASK:
"Has your team used [library] before?"

# If YES:
- No learning curve overhead
- Standard implementation time

# If NO (first time):
- Add learning curve multiplier
- Add setup/configuration time
- Add "figuring it out" buffer
- Consider mistakes/refactoring time
```

### Learning Curve Components

**What's included in learning time:**

1. **Reading docs** (2-8 hr depending on complexity)
2. **Setup/configuration** (1-4 hr)
3. **Trial and error** (2-12 hr - mistakes, refactoring)
4. **Best practices discovery** (1-6 hr - finding optimal patterns)
5. **Debugging unfamiliar errors** (2-8 hr)

### Example: First-Time Library Usage

```
Requirement: "Data table with sorting, filtering, pagination (team never used TanStack Table)"

📚 Library Analysis:
✅ Library: TanStack Table (medium complexity)
✅ Team experience: NONE (first time)
✅ Learning curve: +20%

Base table: 16 hr
Learning overhead: 16 × 0.20 = +3.2 hr
Subtotal: 19.2 hr

Learning breakdown:
- Read docs: 3 hr
- Setup: 2 hr
- Trial/error: 4 hr
- Best practices: 2 hr
- Refactoring: 3 hr
Total learning: ~14 hr actual (but we spread it across the work)

With multipliers: 19.2 × 1.52 = 29 hr

💡 Next time they use TanStack Table: Only +5% overhead (proficiency)
```

### Example: Comparison (Known vs Unknown Library)

```
Same requirement: "Implement interactive charts"

Scenario A: Team knows Chart.js
- Base charts: 12 hr
- Learning curve: 0% (experienced)
- Total: 12 × 1.52 = 18 hr

Scenario B: Team learning D3.js (complex)
- Base charts: 16 hr (D3 more complex)
- Learning curve: +30% (+5 hr)
- Total: 21 × 1.52 = 32 hr

Difference: 14 hours (78% more!) just for learning curve

🎯 Recommendation: Use Chart.js (known), save 14 hours
```

### When to Recommend Alternatives

**Red Flags (suggest simpler alternative):**

- Team has 0 experience with complex library
- Timeline is tight
- Budget is limited
- Simpler alternative exists and meets 90% of needs

**Examples:**

```
❌ Don't: "Use D3.js for simple bar chart" (complex, 30 hr)
✅ Do: "Use Chart.js instead" (simple, 12 hr) - Save 18 hr

❌ Don't: "Use ProseMirror for basic text input" (very complex, 40 hr)
✅ Do: "Use TipTap (wraps ProseMirror)" (medium, 20 hr) - Save 20 hr

❌ Don't: "Build custom drag-drop from scratch" (50 hr)
✅ Do: "Use Vue Draggable" (10% overhead, 16 hr) - Save 34 hr
```

### Team Experience Matrix

| Experience Level  | Learning Multiplier | Notes                        |
| ----------------- | ------------------- | ---------------------------- |
| **Expert**        | +0%                 | Used extensively (50+ hours) |
| **Proficient**    | +5%                 | Used before (10-50 hours)    |
| **Familiar**      | +10%                | Tried once (2-10 hours)      |
| **Beginner**      | +20-30%             | Never used, reading docs     |
| **No Experience** | +30-40%             | Complex lib, steep curve     |

---

## ⚛️ React 18 Estimation Patterns

### Core React Features

| Feature                   | Base Hours | Complexity Factors                      |
| ------------------------- | ---------- | --------------------------------------- |
| **Functional Component**  | 3-6 hr     | + Hooks (+1-2 hr), + Context (+3 hr)    |
| **Class Component**       | 4-8 hr     | Legacy, avoid if possible               |
| **Custom Hook**           | 3-7 hr     | + TypeScript (+30%), + Tests (+50%)     |
| **Context Provider**      | 4-8 hr     | + Reducer (+3 hr), + TypeScript (+2 hr) |
| **Redux Slice**           | 6-12 hr    | + Thunks (+4 hr), + Saga (+8 hr)        |
| **React Router v6 Route** | 2-4 hr     | + Loader (+2 hr), + Protected (+3 hr)   |
| **HOC (Higher-Order)**    | 6-12 hr    | Usually overkill, use hooks             |
| **Error Boundary**        | 4-6 hr     | Per boundary group                      |

### React Component Complexity

**Simple Component (3-5 hr):**

```typescript
// 1-2 props, useState only
// No side effects, pure rendering
```

**Example:** Button, Label, Avatar

**Medium Component (6-12 hr):**

```typescript
// 3-5 props, useState + useEffect
// 1 API call, conditional rendering
// Form validation
```

**Example:** Login form, Profile card, Search

**Complex Component (16-32 hr):**

```typescript
// 6+ props, multiple hooks
// useReducer, context, custom hooks
// Multiple API calls, error handling
// Memoization (useMemo, useCallback)
```

**Example:** Data grid, Kanban board, Chart dashboard

---

## 📚 UI Component Library Adjustments

### Vuetify 3 (Vue)

| Component Type              | Base vs Custom | Reason                    |
| --------------------------- | -------------- | ------------------------- |
| **Simple (Button, Input)**  | -30%           | Pre-styled, just config   |
| **Medium (Card, List)**     | -20%           | Structure provided        |
| **Complex (Table, Dialog)** | -10%           | Still need custom logic   |
| **Custom Theming**          | +4 hr          | Initial setup             |
| **Override Styles**         | +15%           | Fighting library defaults |

**Vuetify Estimation:**

```
Custom component: 8 hr
With Vuetify: 8 × 0.80 = 6.4 hr (save 20%)
Override styles: 6.4 × 1.15 = 7.4 hr

Net savings: 8 - 7.4 = 0.6 hr (minimal)
```

**Bottom Line:** Vuetify saves ~10-15% if used as-is, but custom styling reduces benefits.

### Material-UI / MUI (React)

| Component Type                | Base vs Custom | Reason                     |
| ----------------------------- | -------------- | -------------------------- |
| **Simple (Button, Input)**    | -35%           | Excellent defaults         |
| **Medium (Card, List)**       | -25%           | Good structure             |
| **Complex (Table, Dialog)**   | -15%           | Still complex logic        |
| **Custom Theme**              | +6 hr          | More involved than Vuetify |
| **Override Styles (sx prop)** | +10%           | Easier than Vuetify        |

**MUI Estimation:**

```
Custom component: 8 hr
With MUI: 8 × 0.75 = 6 hr (save 25%)
Theme setup: +6 hr (one-time)
Override: 6 × 1.10 = 6.6 hr

For 10+ components: Net savings significant
```

### Tailwind CSS (Both)

| Component Type        | vs Traditional CSS | Reason                        |
| --------------------- | ------------------ | ----------------------------- |
| **All components**    | -20%               | Faster styling, utility-first |
| **Custom Components** | -15%               | Still need structure          |
| **Responsive**        | -25%               | Built-in breakpoints          |
| **Initial Setup**     | +3 hr              | Config, purge setup           |

**Tailwind Benefit:**

- Fastest for greenfield projects
- Save 15-20% on styling time
- Responsive design easier

**Tailwind + Component Library:**

- Tailwind + Headless UI: Best of both worlds
- Tailwind + Vuetify: Conflicts, don't mix
- Tailwind + MUI: Possible but awkward

---

## 🎯 Framework Version Multipliers

### Vue 2 vs Vue 3

| Aspect               | Vue 2               | Vue 3                          |
| -------------------- | ------------------- | ------------------------------ |
| **Component Dev**    | 1.0x (baseline)     | 0.85x (Composition API faster) |
| **State Management** | Vuex: 1.2x          | Pinia: 1.0x (simpler)          |
| **TypeScript**       | 1.4x (poor support) | 1.1x (native support)          |
| **Testing**          | 1.0x                | 0.9x (better test utils)       |
| **Overall**          | **1.15x**           | **1.0x** (preferred)           |

**Bottom Line:** Vue 3 is 15% faster to develop with proper Composition API usage.

### React 16 vs React 18

| Aspect                   | React 16       | React 18                    |
| ------------------------ | -------------- | --------------------------- |
| **Component Dev**        | 1.0x           | 0.95x (concurrent features) |
| **Class vs Functional**  | 1.2x (classes) | 1.0x (hooks)                |
| **State Management**     | Redux: 1.2x    | Context/hooks: 1.0x         |
| **Suspense/Transitions** | n/a            | +3 hr initial learning      |
| **Overall**              | **1.1x**       | **1.0x** (preferred)        |

**Bottom Line:** React 18 with hooks is 10% faster than class-based React 16.

---

## 🧩 State Management Patterns

### Vue State Options

| Pattern                  | Setup | Per Feature | When to Use                  |
| ------------------------ | ----- | ----------- | ---------------------------- |
| **Local (ref/reactive)** | 0 hr  | +0%         | Component-only state         |
| **Composables**          | 0 hr  | +10%        | Shared logic, 2-3 components |
| **Pinia Store**          | 2 hr  | +15%        | Global state, 4+ components  |
| **Pinia + Persistence**  | 4 hr  | +20%        | LocalStorage sync            |

**Pinia Store Breakdown:**

```typescript
// Simple store: 4-6 hr
export const useUserStore = defineStore('user', () => {
  const user = ref(null)
  const fetchUser = async () => { ... }
  return { user, fetchUser }
})

// Complex store: 8-12 hr
- Multiple state pieces
- 5+ actions
- Computed getters
- Error handling
- TypeScript types
```

### React State Options

| Pattern           | Setup | Per Feature | When to Use            |
| ----------------- | ----- | ----------- | ---------------------- |
| **useState**      | 0 hr  | +0%         | Simple local state     |
| **useReducer**    | 0 hr  | +15%        | Complex local state    |
| **Context API**   | 2 hr  | +20%        | Cross-component state  |
| **Redux Toolkit** | 6 hr  | +25%        | Large app, time travel |
| **Zustand**       | 2 hr  | +12%        | Simpler than Redux     |

**Redux Slice Breakdown:**

```typescript
// Simple slice: 6-8 hr
const userSlice = createSlice({
  name: 'user',
  initialState,
  reducers: { ... }
})

// Complex slice: 12-16 hr
- Async thunks
- Normalized state
- Selectors with reselect
- TypeScript
```

---

## 📡 API Integration Patterns

### Vue 3 + Axios/Fetch

**Pattern 1: Composable (Recommended)**

```typescript
// Setup: 6-8 hr (one-time service layer)
// Per endpoint: 2-3 hr

export const useUserApi = () => {
  const { api } = useApi()
  const fetchUsers = async () => { ... }
  return { fetchUsers }
}
```

**Pattern 2: Pinia Actions**

```typescript
// Setup: Included in store setup
// Per endpoint: 3-4 hr (more boilerplate)

export const useUserStore = defineStore('user', () => {
  const fetchUsers = async () => {
    try {
      const response = await api.get('/users')
      users.value = response.data
    } catch (error) { ... }
  }
})
```

### React + Axios/Fetch

**Pattern 1: Custom Hook (Recommended)**

```typescript
// Setup: 6-8 hr (one-time)
// Per endpoint: 2-3 hr

const useUsers = () => {
  const [users, setUsers] = useState([])
  const [loading, setLoading] = useState(false)

  const fetchUsers = async () => { ... }

  return { users, loading, fetchUsers }
}
```

**Pattern 2: React Query / SWR**

```typescript
// Setup: 4 hr (library config)
// Per endpoint: 1-2 hr (fastest)

const { data, isLoading } = useQuery('users', fetchUsers);
```

**React Query Benefits:**

- Caching: -30% redundant API calls
- Optimistic updates: +2 hr setup, -20% ongoing
- Refetch logic: Built-in

**React Query Overhead:**

- Initial setup: +4 hr
- Learning curve: +8 hr (first project)
- Break-even point: 10+ API endpoints

---

## 🔧 TypeScript Overhead

### Type Definition Time

| Scenario               | Overhead | Example                   |
| ---------------------- | -------- | ------------------------- |
| **Simple Props**       | +10%     | 2-3 props, basic types    |
| **Complex Interfaces** | +20%     | Nested objects, generics  |
| **API Response Types** | +15%     | Full type coverage        |
| **Generic Components** | +30%     | Reusable with type params |
| **Strict Mode**        | +25%     | No `any`, full coverage   |

### TypeScript Benefits (Long-term)

| Benefit                    | Savings            | When           |
| -------------------------- | ------------------ | -------------- |
| **Fewer Runtime Errors**   | -15% bug fixing    | After 3 months |
| **Better Autocomplete**    | -10% dev time      | Immediate      |
| **Refactoring Confidence** | -25% refactor time | Large changes  |

**Break-Even Analysis:**

```
Initial overhead: +20% (~10 hr on 50 hr project)
Benefits kick in: 3 months
Long-term savings: ~15%

For 6+ month projects: TypeScript worth it
For <3 month projects: Debatable
```

---

## 🎨 Styling Approaches

### CSS-in-JS (Styled Components, Emotion)

| Aspect                  | Time Impact              |
| ----------------------- | ------------------------ |
| **Initial Setup**       | +4 hr                    |
| **Per Component**       | +15% (vs regular CSS)    |
| **Theme System**        | +6 hr (one-time)         |
| **Dynamic Styles**      | -20% (vs class toggling) |
| **Bundle Size Concern** | +2 hr optimization       |

### CSS Modules

| Aspect            | Time Impact                   |
| ----------------- | ----------------------------- |
| **Initial Setup** | +1 hr (usually built-in)      |
| **Per Component** | +5% (minimal overhead)        |
| **Scoped Styles** | Built-in (Vue), +2 hr (React) |
| **Global Styles** | +1 hr (theme setup)           |

### Utility-First (Tailwind)

| Aspect             | Time Impact                    |
| ------------------ | ------------------------------ |
| **Initial Setup**  | +3 hr (config, purge)          |
| **Per Component**  | -20% (faster than writing CSS) |
| **Custom Theme**   | +4 hr (tailwind.config.js)     |
| **Learning Curve** | +8 hr (first week)             |
| **Responsive**     | -25% (built-in breakpoints)    |

**Recommendation Matrix:**

| Project Size               | Best Approach                | Why                 |
| -------------------------- | ---------------------------- | ------------------- |
| **Small (<10 components)** | CSS Modules                  | Simple, no overhead |
| **Medium (10-50)**         | Tailwind                     | Fastest development |
| **Large (50+)**            | Tailwind + Component Library | Consistency + speed |
| **Design System**          | CSS-in-JS                    | Dynamic theming     |

---

## 🧪 Testing Framework Impact

### Vue Testing

| Framework                    | Setup | Per Component | Coverage           |
| ---------------------------- | ----- | ------------- | ------------------ |
| **Vitest + Testing Library** | 4 hr  | +15%          | Unit + Integration |
| **Playwright (E2E)**         | 6 hr  | +15 min/test  | Full flow          |
| **Cypress**                  | 5 hr  | +20 min/test  | E2E                |

**Vue Component Test:**

```javascript
// Simple test: 2-3 hr per component
test('renders username', () => {
  render(UserCard, { props: { user } })
  expect(screen.getByText('John')).toBeInTheDocument()
})

// Complex test: 6-8 hr per component
- User interactions
- API mocking
- State changes
- Error scenarios
```

### React Testing

| Framework            | Setup | Per Component | Coverage           |
| -------------------- | ----- | ------------- | ------------------ |
| **Jest + RTL**       | 4 hr  | +15%          | Unit + Integration |
| **Playwright (E2E)** | 6 hr  | +15 min/test  | Full flow          |
| **Cypress**          | 5 hr  | +20 min/test  | E2E                |

**React Component Test:**

```javascript
// Simple: 2-3 hr per component
test('button click', () => {
  const handleClick = jest.fn()
  render(<Button onClick={handleClick} />)
  fireEvent.click(screen.getByRole('button'))
  expect(handleClick).toHaveBeenCalled()
})

// Complex: 6-8 hr per component
- Async rendering
- Hook testing
- Context providers
- Integration scenarios
```

---

## 📦 Build & Tooling

### Build Tool Impact

| Tool                 | Initial Setup | Build Time | Dev Experience           |
| -------------------- | ------------- | ---------- | ------------------------ |
| **Vite (Vue/React)** | 2 hr          | Fast       | Excellent (HMR)          |
| **Webpack 5**        | 6 hr          | Medium     | Good                     |
| **Create React App** | 0 hr          | Slow       | Okay (opinionated)       |
| **Nuxt 3 (Vue)**     | 3 hr          | Fast       | Excellent (conventions)  |
| **Next.js (React)**  | 3 hr          | Fast       | Excellent (SSR built-in) |

### Meta-Framework Overhead

**Nuxt 3 (Vue):**

- Initial setup: +3 hr (vs Vite)
- File-based routing: -2 hr (vs manual Vue Router)
- SSR/SSG: +8 hr (if needed)
- Auto-imports: -10% boilerplate
- **Net:** +3 hr initial, -15% ongoing

**Next.js (React):**

- Initial setup: +3 hr (vs Vite)
- File-based routing: -2 hr (vs React Router)
- SSR/SSG/ISR: +12 hr (if needed)
- API routes: +4 hr (if used)
- **Net:** +3 hr initial, -15% ongoing

---

## 🎯 Framework-Specific Multipliers Summary

### Quick Reference: Project-Level Multipliers

| Tech Stack                       | Multiplier | Reason                    |
| -------------------------------- | ---------- | ------------------------- |
| **Vue 3 + Pinia + Tailwind**     | 0.85x      | Modern, streamlined       |
| **Vue 3 + Vuetify**              | 0.95x      | Component library savings |
| **Vue 2 + Vuex**                 | 1.15x      | Legacy, more boilerplate  |
| **React 18 + Hooks + Tailwind**  | 0.90x      | Modern, efficient         |
| **React + MUI + TypeScript**     | 1.00x      | Library + types balance   |
| **React 16 + Classes + Redux**   | 1.25x      | Legacy, verbose           |
| **React + Next.js + TypeScript** | 1.05x      | Framework overhead        |
| **Vue + Nuxt 3 + TypeScript**    | 1.00x      | Framework offset by DX    |

### Component Estimate Cheat Sheet

**Simple Component (Button, Input, Label):**

- Vue 3: 3 hr
- React: 3.5 hr
- With UI lib: 2 hr
- With TypeScript: +0.5 hr

**Medium Component (Form, Card, List):**

- Vue 3: 8 hr
- React: 9 hr
- With UI lib: 6 hr
- With TypeScript: +1.5 hr

**Complex Component (Table, Dashboard, Editor):**

- Vue 3: 24 hr
- React: 28 hr
- With UI lib: 20 hr
- With TypeScript: +4 hr

---

## 🚀 Performance Optimization Time

### Common Optimizations

| Optimization              | Time               | Impact                |
| ------------------------- | ------------------ | --------------------- |
| **Code Splitting**        | 4-8 hr             | Reduce initial bundle |
| **Lazy Loading Routes**   | 2-4 hr             | Faster first load     |
| **Image Optimization**    | 4-6 hr             | Lazy load, WebP       |
| **Memoization (useMemo)** | 2 hr per component | Prevent re-renders    |
| **Virtual Scrolling**     | 8-12 hr            | Large lists           |
| **PWA (Service Worker)**  | 12-16 hr           | Offline support       |
| **Lighthouse 90+ Score**  | 8-16 hr            | Full optimization     |

---

## 📱 Mobile-First Considerations

### Framework Choices

| Approach                | Time Multiplier | Trade-offs                     |
| ----------------------- | --------------- | ------------------------------ |
| **Responsive Web Only** | 1.0x            | Limited native features        |
| **PWA**                 | 1.3x            | Better offline, no app store   |
| **Ionic (Vue/React)**   | 1.6x            | Hybrid app, slower performance |
| **React Native**        | 2.5x            | True native, separate project  |
| **NativeScript**        | 2.5x            | True native, smaller community |

**Recommendation:** Start with responsive web + PWA (1.3x), migrate to native if needed.

---

**Use this module for framework-specific estimates. For general patterns, see `05_common_patterns.md`.**

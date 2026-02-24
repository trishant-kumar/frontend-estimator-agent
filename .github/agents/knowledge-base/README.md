# Frontend Estimator Knowledge Base

This directory contains modular knowledge bases for the Frontend Estimator agent.

## 📁 Module Structure

| Module                         | Purpose                                             | Size   | Priority   |
| ------------------------------ | --------------------------------------------------- | ------ | ---------- |
| **01_estimation_methods.md**   | PERT, T-shirt sizing, story points, velocity        | Medium | Core       |
| **02_scope_dependencies.md**   | Frontend vs backend, API dependencies, exclusions   | Small  | Critical   |
| **03_technology_reference.md** | Vue/React patterns, component estimates, frameworks | Large  | Reference  |
| **04_output_templates.md**     | CSV/JSON/PDF formats, export structures             | Medium | Tooling    |
| **05_common_patterns.md**      | CRUD, auth, dashboards, tables - reusable estimates | Large  | Reference  |
| **06_rapid_estimation.md**     | T-shirt sizing, quick methods, 5-30 min estimates   | Medium | Time-Saver |

## 🎯 Design Principles

### Modular Architecture Benefits

1. **Performance** - Load only what's needed for each estimation type
2. **Maintainability** - Update one module without affecting others
3. **Readability** - Each module has single responsibility
4. **Reusability** - Modules can be referenced by other agents
5. **Scalability** - Easy to add new estimation methods or patterns

### Module Loading Strategy

**The main agent (orchestrator) should:**

- Contain core workflow and decision logic
- Reference modules by name when deep knowledge needed
- Keep frequently-used info in main file (reduces lookups)
- Use modules for detailed reference data

**When to load a module:**

- User asks for specific methodology (load corresponding method module)
- Need technology-specific patterns (load tech reference)
- Generating output files (load template module)
- Complex scope questions (load scope/dependency module)

## 📝 Usage in Agent

```markdown
When user needs X, reference module Y:

User needs: Detailed PERT calculation
→ "Refer to knowledge-base/01_estimation_methods.md section 'PERT Three-Point'"

User asks: "Is API development included?"
→ "Refer to knowledge-base/02_scope_dependencies.md section 'Scope Exclusions'"

User needs: Vue 3 component estimates
→ "Refer to knowledge-base/03_technology_reference.md section 'Vue 3 Patterns'"

User asks: "Quick 5-minute estimate"
→ "Refer to knowledge-base/06_rapid_estimation.md section 'T-Shirt Sizing'"
```

## 🔄 Maintenance Guidelines

### When to Update Modules

- **01_estimation_methods.md**: New estimation technique added
- **02_scope_dependencies.md**: Scope clarification needed after confusion
- **03_technology_reference.md**: New framework support, updated estimates
- **04_output_templates.md**: New export format requested
- **05_common_patterns.md**: New common pattern identified (3+ uses)
- **06_rapid_estimation.md**: Faster methods discovered

### Version Control

Each module should include:

```markdown
---
Last Updated: YYYY-MM-DD
Version: X.Y
Author: [Name]
Change Summary: [What changed]
---
```

## 🚀 Quick Start

1. **Main agent** loads first (fast, core logic only)
2. **Agent determines** what user needs
3. **Loads specific module(s)** as needed
4. **Processes** using module knowledge
5. **Returns** estimation to user6. **User feedback** → Update relevant module

## 📊 Module Metrics

Target sizes:

- Small: < 500 lines
- Medium: 500-1000 lines
- Large: 1000-2000 lines

If module > 2000 lines → Consider splitting further.

---

**For agent developers:** When adding new features, ask "Which module does this belong to?" before adding to main agent.

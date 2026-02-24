# GitHub Copilot Configuration

This project includes comprehensive GitHub Copilot instructions to provide the best AI-assisted development experience for the CareLink360 web admin application.

## Setup

1. **Install Required Extensions** (automatically prompted when opening the project):

   - GitHub Copilot
   - GitHub Copilot Chat
   - Vue Language Features (Volar)
   - TypeScript Vue Plugin
   - ESLint
   - Prettier
   - Tailwind CSS IntelliSense

2. **VSCode Configuration**: The project includes optimized VSCode settings for:

   - Copilot integration
   - Vue/Nuxt development
   - TypeScript support
   - Auto-formatting and linting
   - File nesting and organization

3. **Available Tasks** (Ctrl+Shift+P → "Tasks: Run Task"):
   - `dev` - Start development server
   - `build` - Build for production
   - `lint` - Run ESLint
   - `lint:fix` - Fix ESLint issues
   - `type-check` - Run TypeScript checks
   - `preview` - Preview production build
   - `clean` - Clean build artifacts

## Copilot Instructions

The Copilot instructions file (`.github/copilot-instructions.md`) includes:

- **Project Overview**: Framework, architecture, and key technologies
- **Authentication Patterns**: Dual auth system (main app + reports)
- **Validation with Zod**: Form validation and TypeScript integration
- **Component Architecture**: Atomic Design patterns
- **Store Patterns**: Pinia state management
- **Common Utilities**: Date handling, error handling, API services
- **Code Style Guidelines**: TypeScript interfaces, props/emits, error handling

## Key Features

### Authentication Context

- Main app routes use `useAuthStore()`
- Reports routes use `useReportStore()`
- Global auth middleware handles route protection

### Form Validation

- Zod schemas for all form validation
- TypeScript interfaces derived from Zod schemas
- Proper error handling and user feedback

### Component Structure

```
components/
  atoms/        # Basic UI elements
  molecules/    # Simple combinations
  organisms/    # Complex sections
  templates/    # Page layouts
```

### Development Best Practices

- Type safety with Zod validation
- Proper error handling
- Loading states for async operations
- Responsive design with Tailwind
- Accessibility considerations
- XML response handling with xmlToObj utility

## Usage Tips

1. **Chat with Context**: Use Copilot Chat to ask questions about the project structure, patterns, and conventions
2. **Code Generation**: Copilot will generate code following project patterns automatically
3. **Validation**: Always use Zod schemas for form validation and API responses
4. **Authentication**: Check which auth store to use based on route context
5. **Components**: Follow atomic design principles when creating new components

The configuration ensures Copilot understands your project's specific patterns and will provide suggestions that align with your existing codebase.

---

## Troubleshooting

### Agent Not Responding

- **Check agent name**: Use `@frontend_estimator` (not `@frontend-estimator`)
- **Verify file exists**: Ensure `.github/agents/FRONTEND_ESTIMATOR.agent.md` is present
- **Restart editor**: Restart VS Code and reload GitHub Copilot extension
- **Check Copilot status**: Ensure GitHub Copilot is logged in and active

### PDF Generator Not Working

- **File missing**: Ensure `docs/estimations/generate-pdf.html` exists in your project
- **Browser compatibility**: Use modern browser (Chrome 90+, Firefox 88+, Safari 14+, Edge 90+)
- **JavaScript errors**: Open browser DevTools (F12) → Console to check for errors
- **Print dialog**: Ensure browser print dialog appears when clicking "Generate PDF"
- **Offline mode**: Generator works offline - no internet connection required

### Estimations Seem High

- **Realistic estimates**: Agent uses production-grade estimates (not "best case" scenarios)
- **Includes overhead**: Testing (+20%), edge cases, code review, and rework buffer
- **Senior velocity**: Based on experienced developers (3+ years), not junior developers
- **Professional quality**: Includes proper error handling, loading states, validation, responsive design
- **Compare baseline**: Check base hours before overhead (buffer may be confidence-related)

### Estimations Seem Low

- **Hidden complexity**: Verify RBAC, real-time features, WCAG compliance, integrations are included
- **Check assumptions**: Confirm APIs ready, designs complete, team has framework experience
- **Missing modules**: Ensure all features/modules are listed in requirements
- **Scope exclusions**: Remember backend, DevOps, manual QA, infrastructure are NOT included
- **Framework efficiency**: Modern frameworks (Vue 3, React 18) with UI libraries are faster to develop

### Export Files Not Generated

- **Check directory**: Files are saved to `docs/estimations/` folder
- **Permissions**: Ensure write permissions for the workspace directory
- **File naming**: Look for `estimation_[ProjectName]_[Date].md/csv/json`
- **Agent tools**: Verify agent has `create_file` tool enabled in configuration

### PDF Output Formatting Issues

- **Markdown syntax**: Ensure proper markdown formatting (tables need pipes `|`, headers need `#`)
- **Browser zoom**: Reset browser zoom to 100% before generating PDF
- **Print margins**: Adjust print margins in browser print dialog if content is cut off
- **Page breaks**: For long documents, check "Background graphics" option in print settings

### Agent Asks Too Many Questions

- **Provide more details**: Give comprehensive requirements upfront to reduce clarification questions
- **Specify framework**: Mention Vue/React explicitly to skip framework selection
- **Include tech stack**: List UI library (Vuetify/Tailwind) and state management approach
- **Attach designs**: Reference design completeness, API readiness, and device targets

### Validation or Zod Issues

- **Schema definition**: Ensure Zod schemas are defined before TypeScript interfaces
- **Import statement**: Check `import { z } from 'zod'` is present
- **Type inference**: Use `z.infer<typeof schema>` for TypeScript types
- **Error messages**: Provide user-friendly error messages in schema definitions
- **Async validation**: Use `.refine()` for custom async validation logic

---

## Getting Help

If issues persist:

1. **Check documentation**: Review `.github/agents/README.md` and knowledge base files
2. **Test with simple example**: Try `@frontend_estimator Vue 3 admin panel with user CRUD`
3. **Verify setup**: Confirm all VSCode extensions are installed and active
4. **Review agent logs**: Check VS Code Output panel → GitHub Copilot for errors
5. **Provide feedback**: Report issues with specific examples and error messages

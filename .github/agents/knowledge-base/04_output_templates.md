# Module 04: Output Templates & File Generation

**Purpose:** Standard formats for estimation exports (CSV, JSON, Markdown, PDF, Word) with automation scripts.

---

## 📄 File Naming Convention

```
docs/estimations/estimation_[ProjectName]_[YYYY-MM-DD].[ext]

Examples:
- estimation_UserDashboard_2025-03-15.csv
- estimation_EcommercePlatform_2025-03-15.pdf
- estimation_CRMSystem_2025-03-15.json
```

**Project Name Rules:**

- PascalCase (no spaces)
- Alphanumeric only
- Max 30 characters
- Descriptive but concise

---

## 📊 CSV Export Template

### Structure

```csv
Module,Task,Description,Optimistic,MostLikely,Pessimistic,Expected,Complexity,Priority,Dependencies
Authentication,Login Page,User login form with validation,8,12,20,12.7,Medium,High,API: /auth/login
Authentication,Signup Page,User registration with validation,10,16,24,16.3,Medium,High,"API: /auth/register, Email service"
```

### Column Definitions

| Column           | Type   | Description                       | Example                         |
| ---------------- | ------ | --------------------------------- | ------------------------------- |
| **Module**       | String | Feature/module name               | Authentication                  |
| **Task**         | String | Specific task/component           | Login Page                      |
| **Description**  | String | Detailed description              | User login form with validation |
| **Optimistic**   | Number | Best case hours                   | 8                               |
| **MostLikely**   | Number | Realistic hours                   | 12                              |
| **Pessimistic**  | Number | Worst case hours                  | 20                              |
| **Expected**     | Number | PERT calculated: (O+4M+P)/6       | 12.7                            |
| **Complexity**   | Enum   | Simple \| Medium \| Complex       | Medium                          |
| **Priority**     | Enum   | Low \| Medium \| High \| Critical | High                            |
| **Dependencies** | String | APIs, services, libraries needed  | API: /auth/login                |

### CSV Generation Code

```javascript
// Use create_file tool with this template
const generateCSV = modules => {
  const headers =
    'Module,Task,Description,Optimistic,MostLikely,Pessimistic,Expected,Complexity,Priority,Dependencies\n';

  const rows = modules
    .flatMap(module =>
      module.tasks.map(task => {
        const expected = (task.optimistic + 4 * task.mostLikely + task.pessimistic) / 6;
        return [
          module.name,
          task.name,
          `"${task.description}"`, // Quote to handle commas
          task.optimistic,
          task.mostLikely,
          task.pessimistic,
          expected.toFixed(1),
          task.complexity,
          task.priority,
          `"${task.dependencies}"`, // Quote to handle commas
        ].join(',');
      }),
    )
    .join('\n');

  return headers + rows;
};
```

---

## 🗂️ JSON Export Template

### Structure

```json
{
  "project": {
    "name": "University Admission CRM",
    "date": "2025-03-15",
    "framework": "Vue 3",
    "confidenceLevel": "70%"
  },
  "summary": {
    "totalHours": 1277,
    "totalTasks": 107,
    "totalModules": 16,
    "estimatedWeeks": 16,
    "recommendedTeamSize": 4
  },
  "multipliers": {
    "testing": 1.15,
    "responsive": 1.2,
    "buffer": 1.1,
    "total": 1.52
  },
  "modules": [
    {
      "id": 1,
      "name": "Authentication",
      "totalHours": 82,
      "priority": "High",
      "tasks": [
        {
          "id": 1,
          "name": "Login Page",
          "description": "User login form with validation",
          "estimates": {
            "optimistic": 8,
            "mostLikely": 12,
            "pessimistic": 20,
            "expected": 12.7
          },
          "complexity": "Medium",
          "priority": "High",
          "dependencies": ["API: /auth/login"],
          "assumptions": ["API returns JWT token", "Validation rules provided"]
        }
      ]
    }
  ],
  "risks": [
    {
      "risk": "API delays",
      "impact": "High",
      "mitigation": "Use mock data during development"
    }
  ],
  "assumptions": [
    "All designs available in Figma",
    "Backend APIs documented",
    "Team familiar with Vue 3"
  ]
}
```

### JSON Generation Code

```javascript
const generateJSON = projectData => {
  return JSON.stringify(
    {
      project: {
        name: projectData.name,
        date: new Date().toISOString().split('T')[0],
        framework: projectData.framework,
        confidenceLevel: projectData.confidence,
      },
      summary: {
        totalHours: projectData.modules.reduce((sum, m) => sum + m.totalHours, 0),
        totalTasks: projectData.modules.reduce((sum, m) => sum + m.tasks.length, 0),
        totalModules: projectData.modules.length,
        estimatedWeeks: Math.ceil(totalHours / (teamSize * 40 * 0.75)),
        recommendedTeamSize: projectData.teamSize,
      },
      multipliers: projectData.multipliers,
      modules: projectData.modules,
      risks: projectData.risks,
      assumptions: projectData.assumptions,
    },
    null,
    2,
  );
};
```

---

## 📝 Markdown Export Template

### Structure

```markdown
# Frontend Estimation: [Project Name]

**Date:** [YYYY-MM-DD]  
**Framework:** [Vue 3 / React 18]  
**Confidence Level:** [X%]

---

## Executive Summary

| Metric                    | Value          |
| ------------------------- | -------------- |
| **Total Estimated Hours** | [X] hours      |
| **Number of Tasks**       | [X] tasks      |
| **Number of Modules**     | [X] modules    |
| **Recommended Team Size** | [X] developers |
| **Estimated Duration**    | [X] weeks      |
| **Confidence Level**      | [X%]           |

---

## 📊 Breakdown by Module

### Module 1: [Module Name] ([X] hours)

**Priority:** [High/Medium/Low]  
**Risk Level:** [High/Medium/Low]

| Task        | Description   | Optimistic | Most Likely | Pessimistic | Expected | Complexity |
| ----------- | ------------- | ---------- | ----------- | ----------- | -------- | ---------- |
| [Task Name] | [Description] | [X] hr     | [X] hr      | [X] hr      | [X] hr   | [Level]    |

**Dependencies:**

- [Dependency 1]
- [Dependency 2]

**Assumptions:**

- [Assumption 1]
- [Assumption 2]

---

## 🎯 Technology Stack

- **Framework:** [Vue 3 / React 18]
- **State Management:** [Pinia / Redux Toolkit]
- **UI Library:** [Vuetify / MUI / Tailwind]
- **Testing:** [Vitest / Jest + Testing Library]
- **Build Tool:** [Vite / Next.js / Nuxt]

---

## ⚙️ Estimation Methodology

**Method Used:** PERT Three-Point Estimation

**Formula:** Expected Hours = (Optimistic + 4 × Most Likely + Pessimistic) / 6

**Multipliers Applied:**

- Testing overhead: +15% (always included)
- Responsive design: +20% (OPTIONAL - only if not already in base hours)
- Risk buffer: +10% (always included)
- **Total multiplier:** ~1.52x (with responsive) or ~1.27x (without responsive)

**Note:** API integration work (loading states, error handling, data fetching) is included in base hours, not a separate multiplier.

**Note:** Responsive multiplier is optional. Ask user if responsive design is part of base developer workflow or needs to be estimated separately.

---

## 🚨 Risks & Mitigation

| Risk     | Likelihood     | Impact         | Mitigation Strategy |
| -------- | -------------- | -------------- | ------------------- |
| [Risk 1] | [High/Med/Low] | [High/Med/Low] | [Strategy]          |

---

## 📋 Key Assumptions

1. [Assumption 1]
2. [Assumption 2]
3. [Assumption 3]

---

## 📅 Timeline Recommendation

**With [X] developers:**

- **Sprint Duration:** 2 weeks
- **Total Sprints:** [X]
- **Total Duration:** [X] weeks
- **Expected Delivery:** [Date]

**Milestones:**

- Week [X]: [Milestone 1]
- Week [X]: [Milestone 2]
- Week [X]: [Milestone 3]

---

## 🔄 Next Steps

1. Review and validate assumptions with stakeholders
2. Confirm API documentation availability
3. Verify design completion status
4. Finalize team composition
5. Plan sprint breakdown

---

**Prepared by:** FrontendEstimator Agent  
**Confidence Basis:** [Explanation of confidence level]
```

---

## 📕 PDF Generation (Chrome Headless)

### Node.js Conversion Script

**File:** `docs/estimations/convert-to-pdf.js`

```javascript
import fs from 'fs';
import { spawn } from 'child_process';
import path from 'path';
import { fileURLToPath } from 'url';

// ES module __dirname workaround
const __filename = fileURLToPath(import.meta.url);
const __dirname = path.dirname(__filename);

/**
 * Convert Markdown to PDF using Chrome headless
 * @param {string} mdFile - Path to markdown file
 * @param {string} outputFile - Path to output PDF
 */
async function convertMarkdownToPDF(mdFile, outputFile) {
  try {
    // Read markdown file
    const markdown = fs.readFileSync(mdFile, 'utf8');

    // Convert markdown to HTML (simple conversion)
    const html = markdownToHTML(markdown);

    // Write temporary HTML file
    const htmlFile = mdFile.replace('.md', '.html');
    fs.writeFileSync(htmlFile, html);

    // Convert HTML to PDF using Chrome
    const chrome = spawn('google-chrome-stable', [
      '--headless',
      '--disable-gpu',
      '--no-sandbox',
      '--disable-dev-shm-usage',
      `--print-to-pdf=${path.resolve(outputFile)}`,
      `file://${path.resolve(htmlFile)}`,
    ]);

    chrome.on('close', code => {
      // Clean up temporary HTML
      fs.unlinkSync(htmlFile);

      if (code === 0) {
        console.log(`✅ PDF generated: ${outputFile}`);
      } else {
        console.error(`❌ Chrome exited with code ${code}`);
      }
    });
  } catch (error) {
    console.error('Error converting to PDF:', error);
  }
}

/**
 * Simple markdown to HTML converter
 */
function markdownToHTML(markdown) {
  let html = markdown
    // Headers
    .replace(/^### (.*$)/gim, '<h3>$1</h3>')
    .replace(/^## (.*$)/gim, '<h2>$1</h2>')
    .replace(/^# (.*$)/gim, '<h1>$1</h1>')
    // Bold
    .replace(/\*\*(.*?)\*\*/gim, '<strong>$1</strong>')
    // Italic
    .replace(/\*(.*?)\*/gim, '<em>$1</em>')
    // Links
    .replace(/\[(.*?)\]\((.*?)\)/gim, '<a href="$2">$1</a>')
    // Lists
    .replace(/^\* (.*$)/gim, '<li>$1</li>')
    // Tables (basic support)
    .replace(/\|/g, '</td><td>')
    // Paragraphs
    .split('\n\n')
    .map(para => `<p>${para}</p>`)
    .join('\n');

  return `
    <!DOCTYPE html>
    <html>
    <head>
      <meta charset="UTF-8">
      <style>
        body {
          font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
          line-height: 1.6;
          max-width: 900px;
          margin: 0 auto;
          padding: 2rem;
          color: #333;
        }
        h1 { color: #2563eb; border-bottom: 3px solid #2563eb; padding-bottom: 0.5rem; }
        h2 { color: #3b82f6; margin-top: 2rem; border-bottom: 2px solid #e5e7eb; padding-bottom: 0.3rem; }
        h3 { color: #60a5fa; margin-top: 1.5rem; }
        table { 
          width: 100%; 
          border-collapse: collapse; 
          margin: 1rem 0; 
          font-size: 0.9rem;
        }
        th, td { 
          border: 1px solid #e5e7eb; 
          padding: 0.75rem; 
          text-align: left; 
        }
        th { 
          background: #f3f4f6; 
          font-weight: 600;
        }
        tr:nth-child(even) { background: #f9fafb; }
        code {
          background: #f3f4f6;
          padding: 0.2rem 0.4rem;
          border-radius: 3px;
          font-family: 'Courier New', monospace;
          font-size: 0.9em;
        }
        strong { color: #1f2937; }
        a { color: #2563eb; text-decoration: none; }
        a:hover { text-decoration: underline; }
        ul, ol { margin-left: 1.5rem; }
        li { margin: 0.5rem 0; }
        @media print {
          body { padding: 1rem; }
          h1, h2, h3 { page-break-after: avoid; }
          table { page-break-inside: avoid; }
        }
      </style>
    </head>
    <body>
      ${html}
    </body>
    </html>
  `;
}

// Export for use
export { convertMarkdownToPDF };

// CLI usage
if (process.argv[2] && process.argv[3]) {
  convertMarkdownToPDF(process.argv[2], process.argv[3]);
}
```

### Usage

```bash
# Terminal command to generate PDF
node docs/estimations/convert-to-pdf.js \
  docs/estimations/estimation_ProjectName_2025-03-15.md \
  docs/estimations/estimation_ProjectName_2025-03-15.pdf
```

### run_in_terminal Tool Usage

```javascript
// In agent code
await runInTerminal({
  command: `node docs/estimations/convert-to-pdf.js docs/estimations/${filename}.md docs/estimations/${filename}.pdf`,
  explanation: 'Converting markdown estimation to PDF using Chrome headless',
  goal: 'Generate PDF',
  isBackground: false,
  timeout: 10000,
});
```

---

## 📘 Word (.docx) Generation (Pandoc)

### Installation

```bash
# Ubuntu/Debian
sudo apt-get install -y pandoc

# macOS
brew install pandoc

# Verify
pandoc --version
```

### Conversion Command

```bash
# Markdown to Word
pandoc estimation_ProjectName_2025-03-15.md \
  -o estimation_ProjectName_2025-03-15.docx \
  --highlight-style=tango \
  --reference-doc=custom-reference.docx  # Optional: custom styling
```

### run_in_terminal Tool Usage

```javascript
// In agent code
await runInTerminal({
  command: `pandoc docs/estimations/${filename}.md -o docs/estimations/${filename}.docx --highlight-style=tango`,
  explanation: 'Converting markdown estimation to Word document',
  goal: 'Generate Word file',
  isBackground: false,
  timeout: 8000,
});
```

### Custom Word Template (Optional)

**Create custom-reference.docx:**

1. Generate default: `pandoc -o custom-reference.docx --print-default-data-file reference.docx`
2. Open in Word, modify styles (headings, tables, fonts)
3. Save and reference in command: `--reference-doc=custom-reference.docx`

---

## 🎯 Complete File Generation Workflow

### Step-by-Step Process

**Step 1: Generate Markdown (Base Format)**

```javascript
// Create markdown file first (human-readable base)
await create_file({
  filePath: `docs/estimations/estimation_${projectName}_${date}.md`,
  content: markdownContent,
});
```

**Step 2: Generate CSV (PM Tools)**

```javascript
// For import into Jira, Asana, etc.
await create_file({
  filePath: `docs/estimations/estimation_${projectName}_${date}.csv`,
  content: csvContent,
});
```

**Step 3: Generate JSON (API/Structured Data)**

```javascript
// For programmatic access
await create_file({
  filePath: `docs/estimations/estimation_${projectName}_${date}.json`,
  content: jsonContent,
});
```

**Step 4: Generate PDF (Stakeholder Reports)**

```javascript
// Pretty, printable version
await runInTerminal({
  command: `node docs/estimations/convert-to-pdf.js docs/estimations/estimation_${projectName}_${date}.md docs/estimations/estimation_${projectName}_${date}.pdf`,
  explanation: 'Generating PDF report',
  goal: 'Create PDF file',
  isBackground: false,
  timeout: 10000,
});
```

**Step 5: Generate Word (Editable Version)**

```javascript
// For stakeholders who want to edit
await runInTerminal({
  command: `pandoc docs/estimations/estimation_${projectName}_${date}.md -o docs/estimations/estimation_${projectName}_${date}.docx`,
  explanation: 'Generating Word document',
  goal: 'Create Word file',
  isBackground: false,
  timeout: 8000,
});
```

**Step 6: Verify Files Created**

```javascript
// Check files exist
await runInTerminal({
  command: `ls -lh docs/estimations/estimation_${projectName}_${date}.*`,
  explanation: 'Verifying all estimation files were created',
  goal: 'Verify files',
  isBackground: false,
  timeout: 2000,
});
```

---

## 📦 Complete Agent Response Template

### When User Requests Export

```
I've generated your estimation in all formats:

📄 **Files Created:**
- 📗 Markdown: docs/estimations/estimation_[Project]_[Date].md (19 KB)
- 📊 CSV: docs/estimations/estimation_[Project]_[Date].csv (12 KB)
- 📝 JSON: docs/estimations/estimation_[Project]_[Date].json (9.7 KB)
- 📕 PDF: docs/estimations/estimation_[Project]_[Date].pdf (788 KB)
- 📘 Word: docs/estimations/estimation_[Project]_[Date].docx (19 KB)

**Summary:**
- Total Hours: [X] hours
- Total Tasks: [X] tasks
- Modules: [X] modules
- Timeline: [X] weeks with [N] developers

**Next Steps:**
1. Review markdown for detailed breakdown
2. Import CSV into your PM tool (Jira/Asana)
3. Share PDF with stakeholders
4. Edit Word doc if adjustments needed

Need any changes to the estimates?
```

---

## 🚀 Quick Export Templates

### 5-Minute Rapid Export (Email Format)

```markdown
**Subject:** Quick Estimate - [Project Name]

## Estimate Summary

- **Total Hours:** [X-Y hours] (range)
- **Timeline:** [Z] weeks with [N] devs
- **Confidence:** [X%]

## Breakdown

1. [Module 1]: [X] hours
2. [Module 2]: [Y] hours
3. [Module 3]: [Z] hours

## Key Assumptions

- [Assumption 1]
- [Assumption 2]

Need detailed breakdown? (2 hours for full PERT analysis)
```

### 15-Minute Pattern-Based Export

```markdown
## [Project Name] Estimate

**Method:** Pattern Matching  
**Total:** [X-Y] hours

| Pattern      | Hours      |
| ------------ | ---------- |
| Auth Suite   | 32 hr      |
| User CRUD    | 28 hr      |
| Dashboard    | 40 hr      |
| **Subtotal** | **100 hr** |

**Multipliers:**

- Testing: +15% = 15 hr
- Responsive: +20% = 20 hr
- Buffer: +10% = 10 hr
- **Total: 145 hours**

Timeline: [X] weeks with [N] devs
```

---

## 🔧 Troubleshooting File Generation

### PDF Generation Issues

**Issue: Chrome not found**

```bash
# Install Chrome
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo apt install ./google-chrome-stable_current_amd64.deb

# Or use chromium
sudo apt-get install chromium-browser
```

**Issue: PDF blank or malformed**

- Check HTML temp file is created
- Verify markdown→HTML conversion
- Try adding `--print-to-pdf-no-header` flag

### Word Generation Issues

**Issue: Pandoc not found**

```bash
# Install pandoc
sudo apt-get update
sudo apt-get install -y pandoc

# Verify
pandoc --version
```

**Issue: Word formatting poor**

- Use `--reference-doc` with custom template
- Add `--toc` for table of contents
- Use `--highlight-style=tango` for code blocks

### General Issues

**Issue: File path errors**

```javascript
// Always use absolute paths
const absolutePath = path.resolve(__dirname, 'docs/estimations', filename);

// Create directory if not exists
fs.mkdirSync('docs/estimations', { recursive: true });
```

---

## 📋 Export Checklist

**Before generating files:**

- [ ] Project name is PascalCase (no spaces)
- [ ] Date is YYYY-MM-DD format
- [ ] docs/estimations/ directory exists
- [ ] Markdown content is complete
- [ ] CSV has all required columns
- [ ] JSON is valid (test with JSON.parse)

**After generating files:**

- [ ] All 5 files exist (.md, .csv, .json, .pdf, .docx)
- [ ] File sizes are reasonable (not 0 bytes)
- [ ] PDF opens correctly
- [ ] Word doc opens correctly
- [ ] CSV imports to spreadsheet correctly

---

**This module provides file generation templates. For estimation content, see other modules.**

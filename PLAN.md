# AutoApply OS — Project Plan

> Automated job application system with local LLM, ATS resume customization, and job tracking.
> Built at 1 hour/day. Personal use first, monetizable later.

---

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | React + TypeScript + Vite + Tailwind |
| Backend | NestJS + TypeORM |
| Database | PostgreSQL (via Docker) |
| LLM | Ollama (local, Llama 3 / Mistral) |
| Scraping | Playwright + Stealth Plugin |
| Job Queue | BullMQ + Redis |
| Resume Export | DOCX + PDF generation |
| Email | Gmail API (OAuth2) |
| Payments | Stripe |

---

## Priority Levels

- 🔴 High Priority (must have from day one)
- 🟡 Medium Priority (important for scale)
- 🟢 Low Priority (monetization & polish)

---

## Stage 1 — Foundation & Core Setup (~6–7 weeks)

### 🔴 Module 1.1 — Project Scaffolding
- [x] 1.1.1 Create the monorepo structure
- [x] 1.1.2 Initialize the NestJS backend
- [x] 1.1.3 Initialize the React frontend
- [ ] 1.1.4 Setup Docker Compose for PostgreSQL
- [ ] 1.1.5 Connect NestJS to PostgreSQL via TypeORM
- [ ] 1.1.6 Install and run Ollama locally
- [ ] 1.1.7 Test Ollama via HTTP API

### 🔴 Module 1.2 — Master Profile / Resume Store
- [ ] 1.2.1 Design the master profile JSON schema
- [ ] 1.2.2 Create the Profile TypeORM entity
- [ ] 1.2.3 Build Profile CRUD API — Create & Read
- [ ] 1.2.4 Build Profile CRUD API — Update & Delete
- [ ] 1.2.5 Profile Editor UI — Personal Info & Skills
- [ ] 1.2.6 Profile Editor UI — Work Experience
- [ ] 1.2.7 Profile Editor UI — Education & Certifications
- [ ] 1.2.8 PDF resume import — text extraction
- [ ] 1.2.9 PDF resume import — LLM structuring

### 🔴 Module 1.3 — Basic UI Shell
- [ ] 1.3.1 Build the sidebar navigation layout
- [ ] 1.3.2 Implement JWT authentication — backend
- [ ] 1.3.3 Implement JWT authentication — frontend
- [ ] 1.3.4 Wire Profile page to the API

---

## Stage 2 — Job Discovery Engine (~6–7 weeks)

### 🔴 Module 2.1 — LinkedIn Scraper
- [ ] 2.1.1 Setup Playwright in the backend
- [ ] 2.1.2 Install Playwright stealth plugin
- [ ] 2.1.3 Scrape LinkedIn job search results
- [ ] 2.1.4 Handle LinkedIn login for full access
- [ ] 2.1.5 Scrape individual job description pages
- [ ] 2.1.6 Create Job entity and save to DB
- [ ] 2.1.7 Build scraper service with trigger endpoint

### 🔴 Module 2.2 — Job Filtering & Deduplication
- [ ] 2.2.1 Filter jobs by posting date
- [ ] 2.2.2 Implement duplicate detection
- [ ] 2.2.3 Add job status flags
- [ ] 2.2.4 Add keyword-based job filtering

### 🔴 Module 2.3 — Job Discovery UI
- [ ] 2.3.1 Build the Jobs list page
- [ ] 2.3.2 Add filter controls to the Jobs page
- [ ] 2.3.3 Build the job detail side panel
- [ ] 2.3.4 Add quick action buttons
- [ ] 2.3.5 Setup BullMQ for scheduled scraping

---

## Stage 3 — LLM Resume Engine (~8–9 weeks)

### 🔴 Module 3.1 — LLM Integration Layer
- [ ] 3.1.1 Build the Ollama service wrapper
- [ ] 3.1.2 Build a prompt template system
- [ ] 3.1.3 Add streaming response support
- [ ] 3.1.4 Add error handling and retry logic

### 🔴 Module 3.2 — ATS Keyword Extraction
- [ ] 3.2.1 Write the keyword extraction prompt
- [ ] 3.2.2 Build keyword extraction API endpoint
- [ ] 3.2.3 Cross-match keywords against master profile
- [ ] 3.2.4 Display keyword match analysis in UI

### 🔴 Module 3.3 — Resume Customization
- [ ] 3.3.1 Write the bullet point rewriting prompt
- [ ] 3.3.2 Write the resume summary generation prompt
- [ ] 3.3.3 Build resume customization API endpoint
- [ ] 3.3.4 Convert resume JSON to DOCX
- [ ] 3.3.5 Convert resume JSON to PDF
- [ ] 3.3.6 Build resume preview in the UI

### 🔴 Module 3.4 — Cover Letter Generation
- [ ] 3.4.1 Write the cover letter generation prompt
- [ ] 3.4.2 Add tone configuration
- [ ] 3.4.3 Build the cover letter API endpoint
- [ ] 3.4.4 Build cover letter editor in the UI

---

## Stage 4 — Application Workflow (~4–5 weeks)

### 🔴 Module 4.1 — Resume Versioning
- [ ] 4.1.1 Create the ResumeVersion entity
- [ ] 4.1.2 Auto-increment version numbers per job
- [ ] 4.1.3 Build version history UI
- [ ] 4.1.4 Add version tagging and download

### 🔴 Module 4.2 — Application Status Tracker
- [ ] 4.2.1 Create the Application entity
- [ ] 4.2.2 Build the Kanban board UI — layout
- [ ] 4.2.3 Add drag-and-drop to the Kanban board
- [ ] 4.2.4 Build the application detail view
- [ ] 4.2.5 Add dashboard summary widget

### 🟡 Module 4.3 — Anti-Bot & Rate Limiting
- [ ] 4.3.1 Add randomized delays to the scraper
- [ ] 4.3.2 Configure Playwright stealth settings
- [ ] 4.3.3 Implement session cookie persistence
- [ ] 4.3.4 Add exponential backoff on failure

---

## Stage 5 — Intelligence & Multi-Source (~6–8 weeks)

### 🟡 Module 5.1 — Multi-Board Scraping
- [ ] 5.1.1 Build the Indeed scraper
- [ ] 5.1.2 Build the Glassdoor scraper
- [ ] 5.1.3 Normalize all sources to unified schema
- [ ] 5.1.4 Add per-source toggle in Settings UI

### 🟡 Module 5.2 — Job Relevance Scoring
- [ ] 5.2.1 Write the relevance scoring prompt
- [ ] 5.2.2 Build the scoring API endpoint
- [ ] 5.2.3 Display scores in the job list

### 🟡 Module 5.3 — Skills Gap Analysis
- [ ] 5.3.1 Aggregate missing keywords across all jobs
- [ ] 5.3.2 Build the Skills Gap report page
- [ ] 5.3.3 Add a bar chart visualization

### 🟡 Module 5.4 — Email / Response Monitoring
- [ ] 5.4.1 Setup Gmail API OAuth2
- [ ] 5.4.2 Write email classification prompt
- [ ] 5.4.3 Build the email monitoring service
- [ ] 5.4.4 Add dashboard notifications for new replies

---

## Stage 6 — Polish, Scale & Monetize (~8–10 weeks)

### 🟢 Module 6.1 — Analytics Dashboard
- [ ] 6.1.1 Application volume chart
- [ ] 6.1.2 Response rate by resume variant
- [ ] 6.1.3 Top companies and roles applied to
- [ ] 6.1.4 Average time to response

### 🟢 Module 6.2 — Company Blacklist / Whitelist
- [ ] 6.2.1 Build company list management UI
- [ ] 6.2.2 Integrate lists into scraper and job feed

### 🟢 Module 6.3 — Browser Auto-Submit
- [ ] 6.3.1 Map LinkedIn Easy Apply form fields
- [ ] 6.3.2 Build the auto-fill service
- [ ] 6.3.3 Add human-in-loop confirmation step

### 🟢 Module 6.4 — Multi-User & Monetization
- [ ] 6.4.1 Add user accounts and roles
- [ ] 6.4.2 Add usage limits per tier
- [ ] 6.4.3 Integrate Stripe for subscription billing
- [ ] 6.4.4 Build a public landing page
```

Press `Cmd + S` to save.

**What the `- [ ]` and `- [x]` mean:**
These are GitHub's checkbox syntax in Markdown. On GitHub they render as actual interactive-looking checkboxes. `- [ ]` means not done, `- [x]` means done. We already marked 1.1.1 and 1.1.2 as done.

---

### Step 2 — Create the GitHub repository

Go to **github.com** in your browser. Make sure you're logged into your **personal account (Sanaan7788)**.

Click the **"+"** button in the top right → **"New repository"**

Fill in:
- **Repository name:** `autoapply`
- **Description:** `Automated job application system with local LLM and ATS resume customization`
- **Visibility:** Select **Private** for now (you can make it public later when it's more built out)
- **DO NOT** check "Add a README file" — we already have our own files
- **DO NOT** check "Add .gitignore" — we already have one
- Click **"Create repository"**

GitHub will show you a page with setup instructions. **Don't follow their instructions** — we'll do it our own way below.

---

### Step 3 — Connect your local project to GitHub

Copy the repository URL from GitHub. It will look like:
```
git@github.com:Sanaan7788/autoapply.git
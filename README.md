# Job Search — Deep Research
Batea: a pan used in mining gold. JoBatea is an app that helps users sift through the seemingly infinite and slop filled job postings that are returned by most job search engines. This is not where it ends either, Jobatea can check out the Workday and Greenhouse pages to get the *exact* posting date from the company. You get to control the parameters. You get to define the areas you are flexible on and the ones that are must-haves in your job search. The agent will return the best results for you while you focus on preparing for the next steps in your career journey.

A full-stack web app for managing AI-driven job searches. Built with:

- **Frontend** — Vite + React + Tailwind CSS + Recharts
- **Backend** — Node.js + Express + Prisma ORM
- **Database** — PostgreSQL

---

## Screenshots

| Deep Job Search | Dashboard | Stats |
| --- | --- | --- |
| ![Deep Job Search](docs/screenshots/deep-search.png) | ![Dashboard](docs/screenshots/dashboard.png) | ![Stats](docs/screenshots/stats.png) |

*(Images are overwritten in place as the UI evolves — filenames stay fixed, so this section never needs edits.)*

---

## Project Structure

```
job_search_deep_research/
├── frontend/          # React SPA (Vite)
└── backend/           # Express API + Prisma
```

---

## Prerequisites

| Tool | Version |
|------|---------|
| Node.js | ≥ 20 |
| PostgreSQL | ≥ 16 |
| npm | ≥ 10 |

---

## Getting Started

### 1 — Backend

```bash
cd backend
npm install
```

Copy the example env file and fill in your values:

```bash
cp .env.example .env
```

Required variables in `.env`:

```env
DATABASE_URL="postgresql://USER:PASSWORD@localhost:5432/job_search_db?schema=public"
DIRECT_URL="postgresql://USER:PASSWORD@localhost:5432/job_search_db?schema=public"
JWT_SECRET=any_long_random_string
GEMINI_API_KEY=your_gemini_api_key
TAVILY_API_KEY=your_tavily_api_key
# Optional: defaults to 5 and cannot exceed 10 results per query.
TAVILY_MAX_RESULTS=5
# Optional: defaults to 12 seconds for Greenhouse public posting requests.
GREENHOUSE_TIMEOUT_MS=12000
```

Create the database (once):

```sql
CREATE DATABASE job_search_db;
```

Run migrations and generate the Prisma client:

```bash
npm run db:migrate    # runs prisma migrate dev
npm run db:generate   # generates @prisma/client
```

Start the dev server (port 3001):

```bash
npm run dev
```

---

### 2 — Frontend

```bash
cd frontend
npm install
npm run dev           # starts Vite on http://localhost:5173
```

The Vite dev server proxies all `/api/*` requests to `http://localhost:3001`, so no CORS config is needed during development.

---

## Pages

| Route | Description |
|-------|-------------|
| `/login` | Login / Sign-up, optional OpenAI API key entry |
| `/dashboard` | Manage resume, prompt guidance, prompt history, and job list |
| `/stats` | Charts: jobs retrieved, applied vs not applied, match score distribution |

---

## API Overview

| Method | Path | Description |
|--------|------|-------------|
| POST | `/api/auth/signup` | Create account |
| POST | `/api/auth/login` | Obtain JWT |
| GET | `/api/user/me` | Fetch profile + assets |
| PUT | `/api/user/me` | Update name / OpenAI key |
| GET/PUT | `/api/user/resume` | Manage resume text |
| GET/PUT | `/api/user/guidance` | Manage prompt guidance sheet |
| GET | `/api/user/prompt-history` | List past prompts |
| GET | `/api/jobs` | List jobs |
| GET | `/api/jobs/stats` | Aggregate stats for charts |
| POST | `/api/jobs` | Add a job |
| PATCH | `/api/jobs/:id/applied` | Toggle applied status |
| DELETE | `/api/jobs/:id` | Remove a job |
| POST | `/api/search-runs` | Create and queue a search run; accepts target, freshness, and validated scoring policies; returns `202 Accepted` |
| GET | `/api/search-runs`, `/api/search-runs/history` | View recent or paginated search runs |
| GET | `/api/search-runs/:id/results` | View paginated results for one run |
| GET/PATCH | `/api/search-runs/:id/cold-leads` | View cold leads or promote one |

---

## Design & Architecture

Design and planning docs live in [diagrams/](diagrams/), with a running [design changelog](diagrams/design-changelog.md):

- [Agentic Job Search Loop v1](diagrams/agentic-job-search-loop-v1.md) — the planned bounded research/verification/scoring loop
- [Deep Job Search Workflow v1](diagrams/deep-job-search-workflow-v1.md) — screen inventory, states, and UI requirements
- [Deep Job Search Visual System v1](diagrams/deep-job-search-hifi-v1.md) — the flagship screen's visual design system
- [Job Seeker Profiles](diagrams/user_profiles/job-seeker-profiles.md) — draft user personas

---

## Next Steps

- Add file upload for resume (multer is already installed)
- Configure `TAVILY_API_KEY` to enable bounded Tavily discovery; Greenhouse public API verification is enabled for recognized Greenhouse URLs, while other employer/ATS sources and scoring remain in progress
- Add pagination for jobs and prompt history
- Add email/password reset flow

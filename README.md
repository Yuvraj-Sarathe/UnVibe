# 🧠 UnVibe

> **"Don't use AI as a crutch. Use it as a benchmark."**

UnVibe is an AI-powered web platform that trains developers to deeply understand code — not just generate it. Built around the **Decode → Rebuild → Defend** loop, UnVibe prepares developers to be irreplaceable in a job market dominated by AI tools.

---

## 📋 Table of Contents

- [Philosophy](#-philosophy)
- [Versioning Roadmap](#-versioning-roadmap)
- [Full Feature List](#-full-feature-list)
- [System Architecture](#-system-architecture)
- [Tech Stack](#-tech-stack)
- [Team Responsibilities](#-team-responsibilities)
- [Project Structure](#-project-structure)
- [Environment Setup](#-environment-setup)
- [Contributing](#-contributing)
- [License](#-license)

---

## 🎯 Philosophy

Most developers today **vibe code** — they prompt AI, paste output, and ship without understanding. UnVibe exists to reverse that.

The platform gives AI the hardest version of a problem. Then it makes *you* understand it, rebuild it simpler, and defend it under pressure. The goal is not to compete with AI — it's to **understand what AI cannot explain about itself**, making you the person no company can replace with a prompt.

---

## 🗺️ Versioning Roadmap

### Version 1.0 — The Foundation *(MVP)*

**Goal:** Core learning loop is live. Users can sign up, pick a learning track, go through the Decode → Rebuild → Defend cycle for at least one language (JavaScript/Python).

**Features:**
- User authentication (email + OAuth)
- 3 learning tracks: Web Dev, Backend Dev, DSA
- AI Code Generator — Claude generates production-grade solutions to real problems
- Decode Phase: line-by-line annotation editor + comprehension quiz auto-generated from code
- Rebuild Phase: in-browser code editor (Monaco) with live diff engine comparing user's solution to AI's
- Basic Defend Phase: async text-based Q&A generated from the user's own rebuilt code
- Personal Dashboard: streak tracker, modules completed, current track progress
- 10 starter modules per track (30 total at launch)
- Light/Dark mode

**Tech focus:** Stability, core UX, low latency code evaluation.

---

### Version 1.1 — The Score *(Differentiation)*

**Goal:** Introduce the **Irreplaceability Score (IRS)** — UnVibe's core differentiator.

**Features:**
- IRS algorithm v1: calculated from Decode accuracy, Rebuild quality, Defend performance
- IRS public profile card (shareable link)
- Employer-facing IRS report (PDF export)
- Code quality scoring: readability, simplicity, correctness weighted separately
- Notification system (email digest: weekly progress, upcoming Defend sessions)
- Expanded module library: 25 modules per track (75 total)
- Module difficulty tags: Foundational / Practitioner / Expert

---

### Version 1.2 — The Community *(Retention)*

**Goal:** Add social and competitive mechanics to drive retention.

**Features:**
- **War Rooms**: weekly group challenges — AI solves a problem, teams have 48 hrs to write the best human version
- War Room leaderboard (judged on clarity + correctness + simplicity)
- Peer review system: review a teammate's rebuild, leave structured feedback
- User profiles with activity feed
- Comment threads on modules
- Referral system: invite a friend, unlock bonus modules
- Mobile-responsive UI overhaul

---

### Version 1.5 — The Interview Layer *(Career Utility)*

**Goal:** Make UnVibe the go-to interview prep platform for AI-era engineering roles.

**Features:**
- **Concept Autopsies**: deep visual breakdowns of why AI wrote what it wrote — tradeoffs, edge cases, failure points
- **Live Defend Sessions**: scheduled video/audio interrogation rooms powered by AI voice interviewer
- Rebuild-under-pressure mode: timed challenges with a broken version of your own past code
- Interview simulation: mock technical interviews based on your IRS weak spots
- **Blindspot Map**: personal dashboard showing concepts seen vs. truly understood
- Company-specific prep tracks: target interview styles of top companies
- Resume integration: link IRS score + War Room results to LinkedIn / resume

---

### Version 2.0 — The Platform *(Scale)*

**Goal:** Open UnVibe to instructors, companies, and multiple languages.

**Features:**
- Instructor portal: external educators can publish their own Decode → Rebuild → Defend modules
- Company portal: orgs can run internal UnVibe bootcamps with private War Rooms and custom tracks
- Multi-language support: TypeScript, Go, Rust, Java, C++
- AI tutoring layer: "Why did AI do this?" — on-demand explanations mid-session
- Offline mode (PWA): continue modules without internet
- Localization: support for 5 languages (Hindi, Spanish, Portuguese, French, Mandarin)
- API access for partner integrations (job boards, hiring platforms)
- Advanced analytics for company accounts: team IRS trends, blindspot aggregation, module completion rates

---

### Version 2.5 — The Ecosystem *(Monetization at Scale)*

**Goal:** Full enterprise product + creator economy.

**Features:**
- UnVibe Marketplace: buy/sell community-built module packs
- Verified Instructor badges
- White-label option for coding bootcamps and universities
- Cohort-based learning: synchronous groups with shared War Rooms and Defend schedules
- AI code evolution tracker: see how AI approaches the same problem as models improve over time
- Plugin system: VS Code + JetBrains extensions for practice mid-development
- B2B licensing for enterprise onboarding programs

---

## 📦 Full Feature List

| Feature | Version | Tier |
|---|---|---|
| Authentication (Email + OAuth) | 1.0 | Free |
| Learning Tracks (Web, Backend, DSA) | 1.0 | Free |
| AI Code Generator | 1.0 | Free |
| Decode Phase (Annotation + Quiz) | 1.0 | Free |
| Rebuild Phase (Editor + Diff Engine) | 1.0 | Free |
| Defend Phase (Async Text Q&A) | 1.0 | Free |
| Personal Dashboard + Streak | 1.0 | Free |
| Irreplaceability Score (IRS) | 1.1 | Free |
| Employer IRS Report (PDF) | 1.1 | Pro |
| Shareable IRS Profile | 1.1 | Free |
| War Rooms (Weekly Challenges) | 1.2 | Free |
| Peer Review System | 1.2 | Free |
| Concept Autopsies | 1.5 | Pro |
| Live Defend (AI Voice Interviewer) | 1.5 | Pro |
| Blindspot Map | 1.5 | Pro |
| Interview Simulation | 1.5 | Pro |
| Company-Specific Prep Tracks | 1.5 | Pro |
| Instructor Portal | 2.0 | Instructor |
| Company Portal + Private War Rooms | 2.0 | Enterprise |
| Multi-language (Go, Rust, Java etc.) | 2.0 | Free/Pro |
| PWA / Offline Mode | 2.0 | Pro |
| Localization (5 languages) | 2.0 | Free |
| Marketplace | 2.5 | Marketplace |
| VS Code / JetBrains Plugin | 2.5 | Pro |
| White-label | 2.5 | Enterprise |

---

## 🏗️ System Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│                          CLIENT LAYER                               │
│                                                                     │
│   ┌──────────────┐   ┌──────────────┐   ┌──────────────────────┐   │
│   │  Next.js App  │   │ Monaco Editor│   │  War Room Real-time  │   │
│   │  (React/TSX)  │   │  (Code IDE)  │   │  (WebSocket Client)  │   │
│   └──────┬───────┘   └──────┬───────┘   └──────────┬───────────┘   │
└──────────┼─────────────────┼──────────────────────┼───────────────┘
           │                 │                       │
           ▼                 ▼                       ▼
┌─────────────────────────────────────────────────────────────────────┐
│                           API GATEWAY                               │
│                     (Next.js API Routes / tRPC)                     │
│              Rate Limiting · Auth Middleware · Logging              │
└───────────────────────────┬─────────────────────────────────────────┘
                            │
          ┌─────────────────┼──────────────────┐
          ▼                 ▼                  ▼
┌──────────────────┐ ┌─────────────┐  ┌──────────────────┐
│  Core API Server │ │  AI Service  │  │  Real-time Server │
│  (Node/Express)  │ │  (Python)    │  │  (Socket.io)      │
│                  │ │             │  │                   │
│  - Auth          │ │ - Code Gen  │  │ - War Rooms       │
│  - Modules       │ │ - Diff Eval │  │ - Live Defend     │
│  - IRS Engine    │ │ - Quiz Gen  │  │ - Notifications   │
│  - Profiles      │ │ - IRS Algo  │  │                   │
└────────┬─────────┘ └──────┬──────┘  └────────┬──────────┘
         │                  │                   │
         ▼                  ▼                   │
┌──────────────────┐ ┌─────────────┐           │
│    PostgreSQL    │ │    Redis     │◄──────────┘
│  (Primary DB)    │ │  (Cache +    │
│                  │ │   Pub/Sub)   │
│  - Users         │ └─────────────┘
│  - Modules                │
│  - Submissions   ┌────────┘
│  - IRS History   ▼
│  - War Rooms  ┌─────────────────┐
└──────────────►│   Object Store  │
                │  (S3 / R2)      │
                │                 │
                │ - Code snapshots│
                │ - PDF reports   │
                │ - Media assets  │
                └─────────────────┘
                        │
                        ▼
                ┌───────────────┐
                │  Anthropic    │
                │  Claude API   │
                │  (External)   │
                └───────────────┘
```

### Data Flow — Decode → Rebuild → Defend

```
User selects module
        │
        ▼
AI Service calls Claude API
→ Generates production-grade code solution
→ Stores code + metadata in PostgreSQL
        │
        ▼
[DECODE PHASE]
User opens Annotation Editor
→ Line-by-line notes saved in real time (debounced PATCH)
→ Quiz auto-generated from annotations via Claude
→ Quiz score stored, threshold required to proceed
        │
        ▼
[REBUILD PHASE]
User writes solution in Monaco Editor
→ On submit: code sent to AI Service
→ Diff Engine compares user code vs AI code
→ Scores: Correctness · Readability · Simplicity
→ Score + submission stored in PostgreSQL
        │
        ▼
[DEFEND PHASE]
Defend session scheduled (async or live)
→ Random past rebuild selected
→ AI generates targeted questions based on user's own code
→ User answers → AI evaluates understanding depth
→ Defend score updates IRS
        │
        ▼
IRS Engine recalculates score
→ Updates Blindspot Map
→ Pushes updated IRS to profile
```

---

## 🛠️ Tech Stack

### Frontend

| Layer | Technology | Why |
|---|---|---|
| Framework | **Next.js 14** (App Router) | SSR/SSG for performance, file-based routing, API routes co-located |
| Language | **TypeScript** | Type safety across the full stack |
| Styling | **Tailwind CSS** | Utility-first, consistent design system |
| Component Library | **shadcn/ui** | Accessible, customizable, unstyled base |
| Code Editor | **Monaco Editor** (React wrapper) | Same engine as VS Code — familiar for developers |
| Animations | **Framer Motion** | Smooth micro-interactions, phase transitions |
| State Management | **Zustand** | Lightweight, no boilerplate |
| Data Fetching | **TanStack Query** | Server state, caching, background refetch |
| Real-time Client | **Socket.io Client** | War Rooms, Live Defend sessions |
| Forms | **React Hook Form + Zod** | Type-safe form handling and validation |
| Charts & Viz | **Recharts** | IRS trend graphs, Blindspot Map |
| Diff Viewer | **react-diff-viewer-continued** | Visual diff between user code and AI code |

---

### Backend

| Layer | Technology | Why |
|---|---|---|
| API Framework | **Node.js + Express** | Familiar, well-supported, fast for I/O |
| API Style | **tRPC** | End-to-end type safety between Next.js and Node |
| Authentication | **NextAuth.js v5** | OAuth (GitHub, Google), email magic link |
| Real-time | **Socket.io** | War Rooms, Live Defend WebSocket rooms |
| Job Queue | **BullMQ** (Redis-backed) | Async defend session scheduling, report generation |
| PDF Generation | **Puppeteer** | IRS employer report PDF export |

---

### AI Service

| Layer | Technology | Why |
|---|---|---|
| Language | **Python 3.12** | Best ecosystem for AI/ML tooling |
| Framework | **FastAPI** | Async-first, auto-generates OpenAPI docs |
| LLM | **Anthropic Claude API** (claude-sonnet-4) | Code generation, quiz generation, defend Q&A |
| Code Execution | **Judge0** (self-hosted) | Sandboxed code execution for correctness testing |
| Diff Engine | **difflib (Python)** + custom AST scorer | Structural diff beyond text — compares logic, not just lines |

---

### Data Layer

| Layer | Technology | Why |
|---|---|---|
| Primary Database | **PostgreSQL 16** | Relational, ACID-compliant, ideal for modules/submissions/IRS |
| ORM | **Prisma** | Type-safe queries, auto-generated types, easy migrations |
| Cache + Pub/Sub | **Redis 7** | Session caching, real-time pub/sub for War Rooms |
| Object Storage | **Cloudflare R2** (S3-compatible) | Code snapshots, PDF reports, media — cheap egress |
| Search | **PostgreSQL Full-Text Search** (v1.x) → **Typesense** (v2.0) | Module/concept search |

---

### DevOps & Infrastructure

| Layer | Technology | Why |
|---|---|---|
| Hosting (Frontend) | **Vercel** | Zero-config Next.js deployment, edge network |
| Hosting (Backend) | **Railway** or **Render** | Simple Node + Python containerized services |
| Container | **Docker + Docker Compose** | Local dev parity, easy multi-service orchestration |
| CI/CD | **GitHub Actions** | Automated tests, linting, deploy on merge to main |
| Monitoring | **Sentry** | Error tracking frontend + backend |
| Logging | **Pino** (Node) + **Loguru** (Python) | Structured JSON logs |
| Analytics | **PostHog** | Product analytics, feature flags, session replay |
| Email | **Resend** | Transactional emails (magic links, weekly digest) |

---

## 👥 Team Responsibilities

### 🎨 UI / Design

**Owns:** Visual design system, component library, user experience flows, brand identity

**Responsible for:**
- Figma design system (tokens, components, screens)
- UnVibe brand — typography, color palette, iconography
- Responsive design specs (mobile, tablet, desktop)
- Accessibility audit (WCAG 2.1 AA compliance)
- Micro-interaction specs (loading states, transitions, empty states)
- User journey maps for each phase (Decode, Rebuild, Defend)
- Dark/Light mode token system

**Deliverables:** Figma file, design tokens exported to Tailwind config, component documentation

---

### 💻 Frontend

**Owns:** Next.js application, component implementation, client-side state, real-time UI

**Responsible for:**
- Implementing all UI from design specs in React/TypeScript
- Monaco Editor integration (syntax highlighting, language configs, line annotations)
- Diff viewer component (Rebuild phase)
- Real-time War Room UI (Socket.io client, live participant tracking)
- IRS visualizations (Recharts: radar chart for Blindspot Map, line graph for score history)
- TanStack Query setup — all server state, mutations, optimistic updates
- Form handling (auth, module submissions, peer review)
- PWA manifest + service worker (v2.0)
- Performance: Core Web Vitals, lazy loading, code splitting
- Frontend error tracking (Sentry)

**Key pages:**
```
/                        → Landing page
/dashboard               → Personal hub (streak, IRS, recent modules)
/tracks                  → Learning track browser
/tracks/[track]/[module] → Module player (Decode → Rebuild → Defend)
/war-room                → Active War Room
/war-room/[id]           → War Room detail + leaderboard
/profile/[username]      → Public profile + IRS card
/defend/[sessionId]      → Live Defend session room
/blindspot               → Blindspot Map full view
```

---

### ⚙️ Backend

**Owns:** Core API, authentication, database, business logic, job scheduling

**Responsible for:**
- tRPC router definitions (typed API contract shared with frontend)
- Auth system: NextAuth.js setup, session management, OAuth providers
- Database schema design and Prisma migrations
- IRS Engine: algorithm that calculates score from Decode + Rebuild + Defend inputs
- Module CRUD: track/module structure, user progress persistence
- Submission storage: code saves, annotations, quiz responses
- Defend session scheduler (BullMQ): queuing async sessions, triggering at right time
- PDF generation service: IRS employer report via Puppeteer
- Peer review system API
- War Room orchestration: team formation, submission deadlines, result aggregation
- WebSocket server (Socket.io): room management, event broadcasting
- Rate limiting, input validation, API security
- Logging (Pino) and alerting

---

### 🤖 AI Service

**Owns:** Python FastAPI service, all Claude API integrations, code evaluation

**Responsible for:**
- Code generation endpoint: given a problem statement → Claude generates production code
- Quiz generation: given annotated code → generates comprehension questions
- Defend Q&A generation: given a user's rebuild → generates personalized interrogation questions
- Defend answer evaluation: scores user's text/voice answers for understanding depth
- Diff Engine: structural AST-based comparison of user rebuild vs AI solution
- Code quality scorer: readability, simplicity, correctness weighted output
- Judge0 integration: sandboxed execution to verify code correctness
- Concept Autopsy generator: produces tradeoff/failure analysis of AI solutions (v1.5)
- Prompt versioning: all prompts version-controlled, A/B testable
- Caching hot prompts in Redis to reduce Claude API calls

---

### 🚀 DevOps / Infrastructure

**Owns:** CI/CD, environments, deployment, monitoring, secrets management

**Responsible for:**
- Docker Compose setup for local development (all services in one command)
- GitHub Actions pipelines: lint → test → build → deploy
- Vercel project config (frontend)
- Railway/Render service config (backend, AI service)
- PostgreSQL provisioning + automated backups
- Redis provisioning
- Cloudflare R2 bucket setup + access policies
- Secrets management (.env structure, production secrets rotation)
- Sentry project setup (frontend + backend)
- PostHog setup + event taxonomy
- Domain + SSL config
- Uptime monitoring

---

## 📁 Project Structure

```
unvibe/
├── apps/
│   ├── web/                        # Next.js frontend
│   │   ├── app/                    # App Router pages
│   │   │   ├── (auth)/
│   │   │   ├── (dashboard)/
│   │   │   ├── tracks/
│   │   │   ├── war-room/
│   │   │   ├── profile/
│   │   │   └── defend/
│   │   ├── components/
│   │   │   ├── ui/                 # shadcn base components
│   │   │   ├── editor/             # Monaco wrapper, diff viewer
│   │   │   ├── decode/             # Annotation editor, quiz UI
│   │   │   ├── rebuild/            # Code editor, submission UI
│   │   │   ├── defend/             # Q&A interface, live room
│   │   │   ├── war-room/           # Real-time challenge UI
│   │   │   ├── irs/                # Score card, radar chart, profile
│   │   │   └── dashboard/          # Streak, blindspot map, progress
│   │   ├── lib/
│   │   │   ├── trpc/               # tRPC client setup
│   │   │   ├── auth/               # NextAuth client config
│   │   │   └── store/              # Zustand stores
│   │   └── public/
│   │
│   ├── api/                        # Node.js + Express backend
│   │   ├── src/
│   │   │   ├── routers/            # tRPC routers
│   │   │   │   ├── auth.ts
│   │   │   │   ├── modules.ts
│   │   │   │   ├── submissions.ts
│   │   │   │   ├── irs.ts
│   │   │   │   ├── warRoom.ts
│   │   │   │   └── profile.ts
│   │   │   ├── services/
│   │   │   │   ├── irs-engine.ts
│   │   │   │   ├── defend-scheduler.ts
│   │   │   │   ├── pdf-generator.ts
│   │   │   │   └── socket-server.ts
│   │   │   ├── db/
│   │   │   │   ├── schema.prisma
│   │   │   │   └── migrations/
│   │   │   └── middleware/
│   │   │       ├── auth.ts
│   │   │       ├── rate-limit.ts
│   │   │       └── logger.ts
│   │   └── Dockerfile
│   │
│   └── ai-service/                 # Python FastAPI AI service
│       ├── app/
│       │   ├── routes/
│       │   │   ├── generate.py     # Code generation
│       │   │   ├── quiz.py         # Quiz generation
│       │   │   ├── defend.py       # Defend Q&A
│       │   │   ├── diff.py         # Diff engine
│       │   │   └── autopsy.py      # Concept autopsies (v1.5)
│       │   ├── prompts/            # Versioned prompt templates
│       │   │   ├── v1/
│       │   │   └── v2/
│       │   ├── services/
│       │   │   ├── claude_client.py
│       │   │   ├── judge0_client.py
│       │   │   └── ast_differ.py
│       │   └── main.py
│       ├── requirements.txt
│       └── Dockerfile
│
├── packages/
│   ├── types/                      # Shared TypeScript types
│   ├── config/                     # Shared ESLint, Prettier, TS config
│   └── ui/                         # Shared UI primitives (optional)
│
├── infra/
│   ├── docker-compose.yml          # Local dev: all services
│   ├── docker-compose.prod.yml
│   └── scripts/
│       ├── seed.ts                 # DB seed (modules, tracks)
│       └── migrate.sh
│
├── .github/
│   └── workflows/
│       ├── ci.yml                  # Lint + test on PR
│       └── deploy.yml              # Deploy on merge to main
│
├── .env.example
├── turbo.json                      # Turborepo config
└── package.json                    # Root workspace
```

---

## ⚙️ Environment Setup

### Prerequisites

- Node.js 20+
- Python 3.12+
- Docker + Docker Compose
- pnpm 9+

### Quick Start (Local Dev)

```bash
# Clone the repo
git clone https://github.com/your-org/unvibe.git
cd unvibe

# Install all dependencies
pnpm install

# Copy environment variables
cp .env.example .env
# → Fill in: DATABASE_URL, REDIS_URL, ANTHROPIC_API_KEY, NEXTAUTH_SECRET, R2 credentials

# Start all infrastructure (Postgres, Redis)
docker-compose up -d

# Run database migrations and seed
pnpm db:migrate
pnpm db:seed

# Start all apps in dev mode
pnpm dev
```

Services will be available at:

| Service | URL |
|---|---|
| Web App | http://localhost:3000 |
| API Server | http://localhost:3001 |
| AI Service | http://localhost:8000 |
| API Docs (FastAPI) | http://localhost:8000/docs |

### Required Environment Variables

```env
# Database
DATABASE_URL=postgresql://user:password@localhost:5432/unvibe

# Redis
REDIS_URL=redis://localhost:6379

# Auth
NEXTAUTH_SECRET=your-secret
NEXTAUTH_URL=http://localhost:3000
GITHUB_CLIENT_ID=
GITHUB_CLIENT_SECRET=
GOOGLE_CLIENT_ID=
GOOGLE_CLIENT_SECRET=

# AI
ANTHROPIC_API_KEY=your-key

# Storage
R2_ACCOUNT_ID=
R2_ACCESS_KEY_ID=
R2_SECRET_ACCESS_KEY=
R2_BUCKET_NAME=

# Email
RESEND_API_KEY=

# Monitoring
SENTRY_DSN_WEB=
SENTRY_DSN_API=
NEXT_PUBLIC_POSTHOG_KEY=
```

---

## 🤝 Contributing

1. Fork the repo and create a branch: `git checkout -b feature/your-feature`
2. Follow the commit convention: `feat:`, `fix:`, `chore:`, `docs:`
3. Ensure tests pass: `pnpm test`
4. Ensure linting passes: `pnpm lint`
5. Open a pull request to `main` — fill out the PR template

All PRs require one review. The CI pipeline runs lint, type-check, and tests automatically.

---

## 📄 License

MIT License — see [LICENSE](./LICENSE) for details.

---

<div align="center">

**Built for developers who want to be irreplaceable.**

*UnVibe — Stop vibing. Start understanding.*

</div>

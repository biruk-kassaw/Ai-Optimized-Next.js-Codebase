<div align="center">

# 🤖 Next.js AI Coding Starter

**Production-ready Next.js SaaS starter optimized for AI-assisted development with Bun, Supabase, and strict TypeScript.**

[![Next.js](https://img.shields.io/badge/Next.js-16-black?logo=next.js)](https://nextjs.org/)
[![Bun](https://img.shields.io/badge/Bun-Fast-black?logo=bun)](https://bun.sh/)
[![Supabase](https://img.shields.io/badge/Supabase-Auth-black?logo=supabase)](https://supabase.com/)
[![Drizzle](https://img.shields.io/badge/Drizzle-ORM-blue?logo=drizzle)](https://orm.drizzle.team/)
[![Biome](https://img.shields.io/badge/Biome-Linter-yellow)](https://biomejs.dev/)

*Build faster with AI coding agents using a strict, predictable, and highly-typed foundation.*

[🛠️ Tech Stack](#-tech-stack--ai-benefits) · [🚀 Quick Start](#-quick-start) · [🏗️ Architecture](#-architecture) · [🔄 AI Feedback Loop](#-ai-feedback-loop)

</div>

---

> 📖 **New to AI-optimized codebases?** 
> Check out the [Codebase Guide](./CODEBASE-GUIDE.md) for a comprehensive walkthrough of the patterns and principles used in this template.

---

## 🛠️ Tech Stack & AI Benefits

Every tool in this stack was chosen to maximize the efficiency of AI coding assistants (like Claude Code, Cursor, and Copilot) by providing strict contracts and clear, machine-readable feedback.

| Technology | Choice | AI Agent Benefit |
|------------|--------|------------------|
| **Runtime** | Bun | Faster iteration cycles |
| **Framework** | Next.js 16 | Predictable file conventions |
| **Linting** | Biome | 10-25x faster feedback loop |
| **Type Safety** | TS strict | Unambiguous errors, types as docs |
| **Database** | Drizzle ORM | Can't write invalid queries |
| **Auth** | Supabase Auth | Clear errors, 50K MAU free |
| **Validation** | Zod | Structured errors, self-documenting |
| **Logging** | Pino | Machine-readable debugging context |
| **Testing** | Bun test | 10x faster than Jest |
| **UI** | shadcn/ui | Agent can read/modify components |

---

## 🚀 Quick Start

### Installation & Setup

1. **Install dependencies**
   ```bash
   bun install
   ```

2. **Set up environment**
   Copy the example environment file and add your Supabase credentials:
   ```bash
   cp .env.example .env
   ```

3. **Push database schema**
   ```bash
   bun run db:push
   ```

4. **Start development server**
   ```bash
   bun run dev
   ```

---

## 💻 Commands

```bash
bun run dev          # Start development server
bun run build        # Production build
bun run lint         # Check for lint/format errors
bun run lint:fix     # Auto-fix lint/format issues
bun test             # Run tests with coverage
bun run db:studio    # Open Drizzle Studio GUI
```

---

## 🏗️ Architecture

The codebase follows a modular, feature-driven architecture that keeps related concerns collocated, giving AI agents full context without needing to hunt across the project.

```text
src/
├── app/                    # Next.js App Router
│   ├── (auth)/             # Auth pages (login, register)
│   ├── (dashboard)/        # Protected pages
│   └── api/                # API routes
├── core/                   # Shared infrastructure
│   ├── config/             # Environment validation
│   ├── database/           # Drizzle client & schema
│   ├── logging/            # Pino structured logging
│   └── supabase/           # Supabase clients
├── features/               # Vertical slices
│   ├── auth/               # Auth actions & hooks
│   └── projects/           # Example feature slice
├── shared/                 # Cross-feature utilities
│   ├── schemas/            # Pagination, errors
│   └── utils/              # Date, format helpers
└── components/             # UI components
    └── ui/                 # shadcn/ui components
```

### Vertical Slice Pattern

Each feature in the `features/` directory is self-contained. This isolation ensures that AI agents can confidently make changes without unintended side effects.

```text
src/features/{feature}/
├── models.ts      # Drizzle types
├── schemas.ts     # Zod validation
├── repository.ts  # Database queries
├── service.ts     # Business logic
├── errors.ts      # Custom errors
├── index.ts       # Public API
└── tests/         # Feature tests
```

---

## 🔄 AI Feedback Loop

The stack is inherently optimized for AI agents to self-correct autonomously:

```mermaid
graph LR
    A[Generate Code] --> B[Run Checks]
    B --> C[Parse Errors]
    C --> D[Fix Code]
    D --> A
```

Checks produce highly targeted, machine-readable feedback:
- **TypeScript**: Type errors with exact `file:line` locations.
- **Biome**: Lint errors coupled with actionable suggestions.
- **Tests**: Failed assertions with clear `expected/actual` diffs.
- **Logs**: Structured JSON with complete execution context.

---

## 🔐 Environment Variables

Ensure your `.env` file is properly configured. If you are deploying serverless functions, make sure to use the transaction pooler for your database URL.

```bash
# Supabase Configuration
NEXT_PUBLIC_SUPABASE_URL=https://your-project.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY=your-anon-key

# Database Connection
# Note: Use transaction pooler for serverless environments (Port 6543)
DATABASE_URL=postgresql://postgres.[ref]:[password]@aws-0-[region].pooler.supabase.com:6543/postgres
```

---
<div align="center">
  Built with ❤️ for modern, AI-driven development workflows.
</div>

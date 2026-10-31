# Workspace

## Overview

pnpm workspace monorepo using TypeScript. Each package manages its own dependencies.

## Stack

- **Monorepo tool**: pnpm workspaces
- **Node.js version**: 24
- **Package manager**: pnpm
- **TypeScript version**: 5.9
- **API framework**: Express 5
- **Database**: PostgreSQL + Drizzle ORM
- **Validation**: Zod (`zod/v4`), `drizzle-zod`
- **API codegen**: Orval (from OpenAPI spec)
- **Build**: esbuild (CJS bundle)

## Key Commands

- `pnpm run typecheck` — full typecheck across all packages
- `pnpm run build` — typecheck + build all packages
- `pnpm --filter @workspace/api-spec run codegen` — regenerate API hooks and Zod schemas from OpenAPI spec
- `pnpm --filter @workspace/db run push` — push DB schema changes (dev only)
- `pnpm --filter @workspace/api-server run dev` — run API server locally

See the `pnpm-workspace` skill for workspace structure, TypeScript setup, and package details.

## Artifacts

### GrowthFlow AI (`artifacts/growthflow-ai`)
- **Framework**: Next.js 15 App Router + TypeScript
- **Styling**: Tailwind CSS v4 + shadcn/ui
- **Theme**: Dark/light mode via `next-themes`
- **Preview path**: `/`
- **Port**: 20807
- **Output**: Static export (`output: 'export'`, `distDir: 'dist/public'`)

#### Folder Structure
```
src/
├── app/
│   ├── layout.tsx              # Root layout with ThemeProvider + metadata
│   ├── page.tsx                # Landing page (hero, features, pricing, CTA)
│   ├── globals.css             # Tailwind + CSS design tokens (light/dark)
│   └── (dashboard)/
│       ├── layout.tsx          # Dashboard shell (sidebar + header)
│       ├── dashboard/page.tsx  # Overview with metrics, charts, AI recs
│       ├── analytics/page.tsx  # Traffic, sessions, conversion funnel
│       ├── customers/page.tsx  # Customer table with plan/status badges
│       ├── campaigns/page.tsx  # Campaign list with performance metrics
│       └── settings/page.tsx   # Profile, team, notifications, danger zone
├── components/
│   ├── layout/
│   │   ├── navbar.tsx          # Marketing navbar (responsive, theme toggle)
│   │   ├── sidebar.tsx         # Collapsible dashboard sidebar with active state
│   │   └── dashboard-header.tsx # Search bar + notifications + user avatar
│   ├── providers/
│   │   └── theme-provider.tsx  # next-themes wrapper
│   └── ui/
│       └── theme-toggle.tsx    # Sun/moon toggle button
├── lib/
│   └── utils.ts                # cn(), formatNumber(), formatCurrency(), etc.
└── hooks/                      # Ready for custom hooks
```

#### Design Tokens (globals.css)
- **Primary**: Violet/indigo (`hsl(258 90% 66%)`)
- **Light bg**: White with light gray sidebar
- **Dark bg**: Deep navy (`hsl(224 71% 4%)`) with darker sidebar
- **Charts**: 5-color palette (violet, teal, rose, amber, green)

### API Server (`artifacts/api-server`)
- Express 5 + TypeScript
- Preview path: `/api`
- Port: 8080

### Canvas / Mockup Sandbox (`artifacts/mockup-sandbox`)
- Vite + React design sandbox
- Preview path: `/__mockup`
- Port: 8081

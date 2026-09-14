# Smart Resume Analyzer

A dark-mode resume intelligence tool that compares a resume with one target job description and turns the gaps into prioritized edits.

## Run & Operate

- `pnpm --filter @workspace/api-server run dev` — run the API server (port 5000)
- `pnpm run typecheck` — full typecheck across all packages
- `pnpm run build` — typecheck + build all packages
- `pnpm --filter @workspace/api-spec run codegen` — regenerate API hooks and Zod schemas from the OpenAPI spec
- `pnpm --filter @workspace/db run push` — push DB schema changes (dev only)
- Required env: `DATABASE_URL` — Postgres connection string

## Stack

- pnpm workspaces, Node.js 24, TypeScript 5.9
- API: Express 5
- DB: PostgreSQL + Drizzle ORM
- Validation: Zod (`zod/v4`), `drizzle-zod`
- API codegen: Orval (from OpenAPI spec)
- Build: esbuild (CJS bundle)

## Where things live

- `artifacts/smart-resume-analyzer/src/App.tsx` — single-page analyzer flow and local scoring logic
- `artifacts/smart-resume-analyzer/src/index.css` — dark-only theme, typography, surfaces, and motion
- `artifacts/smart-resume-analyzer` — runnable web artifact at the root preview path

## Architecture decisions

- The first build is client-only so resume text stays in the browser and the core read is instant.
- The score is directional: it combines target-language overlap with lightweight context signals rather than presenting a hiring verdict.
- The UI is dark-only by product requirement, with chartreuse as the action signal and coral as the gap signal.

## Product

- Paste or attach resume material and a target job description.
- Choose a full analysis, keyword scan, or impact pass.
- Review match score, keyword coverage, matched language, missing keywords, strengths, and three prioritized improvements.
- Mark improvement items complete, copy the result summary, edit inputs, or start a new analysis.

## User preferences

_Populate as you build — explicit user instructions worth remembering across sessions._

## Gotchas

_Populate as you build — sharp edges, "always run X before Y" rules._

## Pointers

- See the `pnpm-workspace` skill for workspace structure, TypeScript setup, and package details

# Aurelium

Aurelium is a premium concept SaaS website and application for product decision intelligence. It
turns customer signals into evidence-backed recommendations, includes a secure workspace and admin
console, and is designed as a deployable Next.js product sample.

## Product Surface

- Marketing site with hero visualization, platform, workflow, security, pricing, stories, FAQ,
  contact conversion flow, and light/dark themes.
- Authenticated decision dashboard with ranked insights and notification state.
- Search workspace for indexed evidence and operating guidance.
- Role-gated administration for leads and analytics totals.
- SEO metadata, generated Open Graph image, JSON-LD, sitemap, robots policy, and web manifest.

## Stack

- Next.js 16 App Router, React 19, TypeScript, Tailwind CSS 4, Framer Motion
- shadcn-style UI primitives using Radix Slot and class-variance-authority
- PostgreSQL with Prisma 7 and the PostgreSQL driver adapter
- Signed HTTP-only session cookies, CSRF tokens, Zod request validation, bcrypt password hashing,
  database-backed rate limiting, and administrator authorization checks
- Vitest validation tests and ESLint quality checks

## Environment

Create `.env` from `.env.example` and provide production-grade secrets:

```bash
DATABASE_URL="postgresql://..."
AUTH_SECRET="generate-a-random-value-at-least-32-characters"
RATE_LIMIT_SALT="generate-an-independent-random-value"
NEXT_PUBLIC_SITE_URL="https://your-live-domain.example"
SEED_ADMIN_EMAIL="your-admin-email@example.com"
SEED_ADMIN_PASSWORD="a-strong-initial-admin-password"
```

`DATABASE_URL`, `AUTH_SECRET`, and `RATE_LIMIT_SALT` are required in production. Use an independent
managed PostgreSQL database for preview and production environments.

## Development

```bash
npm install
npm run db:generate
npm run db:migrate
npm run db:seed
npm run dev
```

The seed task requires an explicit `SEED_ADMIN_PASSWORD` of at least 12 characters. It provisions
the first administrator, decision insight examples, searchable operating resources, and an initial
workspace notification.

## Verification

```bash
npm audit --audit-level=moderate
npm run lint
npm run test
npm run build
```

The lockfile pins patched transitive overrides for disclosed PostCSS and Prisma development-server
advisories.

## Vercel Deployment

1. Create a managed PostgreSQL database and set all environment variables in the Vercel project.
2. Apply the committed schema with `npm run db:deploy` against the production `DATABASE_URL`.
3. Seed once with secure administrator credentials using `npm run db:seed`.
4. Deploy the repository with the Vercel Next.js preset.
5. Set `NEXT_PUBLIC_SITE_URL` to the final assigned domain and redeploy so canonical and sitemap
   URLs point at the public host.

The product names, customer narratives, plan details, and operational claims in this sample are
fictional authored content for demonstration and should be replaced or approved before commercial
use.

# 05 Tech Stack

> **TL;DR:** Template for defining technology choices and justifications across frontend, backend, database, auth, billing, and infrastructure.
> **Covers:** frontend, backend, database, auth, billing, hosting, storage, email, jobs, analytics | **Phase:** 2

## Instructions

Fill in each section with the specific technology choice and a brief justification. The defaults below reflect the framework's assumed stack — override any section as needed for your project.

## Frontend

> Default: Next.js 14+ (app router) with TypeScript and Tailwind CSS. React Server Components where possible, client components for interactive UI.
>
> Justification: App router provides file-based routing, server components reduce bundle size, Tailwind enables rapid UI development with design tokens.

## Backend

> Default: Next.js API routes and Server Actions. For complex background work, separate serverless functions.
>
> Justification: Co-located with frontend, reduces deployment complexity. Server Actions simplify form handling and mutations.

## Database

> Default: PostgreSQL with Prisma ORM.
>
> Justification: Relational data model fits SaaS multi-tenancy (User → Organization → Membership). Prisma provides type-safe queries, migrations, and schema management.

## Auth

> Default: NextAuth.js (Auth.js) with email/password credentials provider. Optional: Google OAuth, magic link via email.
>
> Justification: Integrates natively with Next.js. Supports multiple providers. Session management via JWT or database sessions.

## Billing

> Default: Stripe with Checkout for payment collection and Customer Portal for self-service billing management. Webhooks for subscription lifecycle events.
>
> Justification: Industry standard for SaaS billing. Handles proration, dunning, invoicing, and tax calculation.

## Hosting

> Default: Vercel for frontend and API routes. Database hosted on Supabase, Neon, or Railway (managed PostgreSQL).
>
> Justification: Zero-config deployment for Next.js. Preview deployments for PRs. Edge functions for middleware.

## File Storage

> Default: AWS S3 or Vercel Blob for user-uploaded files (avatars, attachments). Signed URLs for secure access.
>
> Justification: Scalable object storage with CDN integration.

## Email

> Default: SendGrid or Resend for transactional email (verification, password reset, invoice delivery, notifications).
>
> Justification: High deliverability, template support, webhook tracking for delivery status.

## Queue Or Jobs

> Default: Inngest or Trigger.dev for background jobs (webhook processing, email sends, analytics aggregation). For simpler needs, Vercel Cron Jobs.
>
> Justification: Serverless-compatible job processing without managing infrastructure.

## Analytics

> Default: PostHog for product analytics (event tracking, funnels, feature flags). Custom analytics dashboard built from Usage Event and Analytics Summary entities.
>
> Justification: Self-hostable, privacy-friendly, integrates with Next.js.

## Constraints

> Example: Must deploy to Vercel (team already has a plan). Database must be PostgreSQL (existing data migration requirement). No self-hosted infrastructure — all managed services.

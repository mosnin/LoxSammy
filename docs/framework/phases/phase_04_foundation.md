# Phase 4 — Foundation

## Trigger
Architecture plan confirmed. No source code exists yet.

## Files to Read
- `docs/framework/internal/09_build_rules_internal.md` — Phase 1 section

## What to Build

### Project Setup
- Initialize Next.js with app router, TypeScript, Tailwind CSS
- Configure Prisma with PostgreSQL
- Set up project structure per architecture plan

### Database Schema
- Create Prisma schema from entity plan
- Include all canonical entities (User, Organization, Membership, Subscription, etc.)
- Add app-specific entities
- Set up relationships and indexes

### Shared Infrastructure
- Types and interfaces
- Constants and configuration
- Utility functions
- API route helpers
- Error handling utilities

### Verify
- Project builds without errors
- Database migrates successfully
- Dev server starts cleanly

## Exit Condition
Foundation is running. Summarize what was set up and ask user to continue to **Phase 5**.

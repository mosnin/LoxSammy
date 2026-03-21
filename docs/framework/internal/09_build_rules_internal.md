# 09 Build Rules Internal

## Purpose

Define how the internal framework must be used during implementation. This is the authoritative reference for build order, coding standards, and quality gates.

## Core Rule

Read the framework first. Generate the project docs next. Build only after both layers exist.

## Source Of Truth Hierarchy

1. docs/project/* (app-specific decisions override everything)
2. docs/framework/internal/* (authenticated product rules)
3. docs/framework/website/* (marketing site rules)
4. docs/framework/templates/* (document shape reference)

## Build Phases

Build in this exact order. Do not skip ahead.

### Phase 1: Foundation
- Initialize project (Next.js app router, TypeScript, Tailwind)
- Configure database (PostgreSQL + Prisma schema for core entities from `07_data_models.md`)
- Set up environment variables and config
- Create shared utility functions (date formatting, currency, validation helpers)

### Phase 2: Auth
- Implement auth routes: /login, /signup, /forgot-password, /reset-password, /verify-email
- Auth page layout per `02_auth_and_onboarding.md` (split layout desktop, single column mobile)
- Session management and middleware for protected routes
- Email verification flow

### Phase 3: Onboarding
- Multi-step onboarding flow per `02_auth_and_onboarding.md`
- Progress persistence (user can leave and return)
- Skip logic for optional steps
- First value event delivery

### Phase 4: App Shell
- Read the internal visual pack (`10_design_tokens_internal.md`, `11_internal_screen_archetypes.md`, `12_internal_component_specs.md`, `13_internal_data_display_rules.md`) before building any authenticated pages
- Configure Tailwind theme with design tokens from `10_design_tokens_internal.md`
- Build the authenticated shell per `01_app_shell.md`: top bar, sidebar, mobile drawer, main content area
- Page header component (title, context, primary action, secondary actions)
- User menu (profile, settings, billing, logout)
- Role-aware sidebar (hide items user cannot access)

### Phase 5: Dashboard
- Dashboard page per `03_dashboard_system.md`: summary row, main work area, secondary insights
- All four states: loading skeleton, empty state with CTA, success with data, error with retry
- Mobile responsive layout (stacked cards, no horizontal scroll)

### Phase 6: Core Features
- Product-specific feature modules from `docs/project/02_feature_spec.md`
- Each feature uses the shared page header and shell layout
- CRUD operations with confirmation dialogs for destructive actions
- List views with search, sort, and pagination

### Phase 7: Settings and Billing
- Settings pages per `05_settings_billing_admin.md`: profile, workspace, billing, security, notifications
- Stripe integration: Checkout for upgrades, Customer Portal for billing management
- Webhook endpoint for subscription lifecycle events
- Permission enforcement (workspace/billing restricted to admin+)

### Phase 8: Admin
- Admin panel per `05_settings_billing_admin.md`: user management, billing overview, usage, logs
- Role-gated access (admin and owner only)
- All admin actions logged to Admin Record entity
- Search and filter on user list

### Phase 9: Marketing Site
- Build public pages per `docs/framework/website/` specs
- Home page with conversion funnel per `saas_home_page_system.md`
- Additional pages per `saas_website_page_system.md` as scoped
- Design tokens from `design_system_tokens.md`, components from `component_library_spec.md`

### Phase 10: Edge Cases and Polish
- Implement edge cases from `docs/project/04_edge_cases.md`
- Run through QA checklist from `docs/project/08_qa_checklist.md`
- Verify acceptance criteria from `docs/project/07_acceptance_criteria.md`
- Dark mode pass, mobile pass, error handling pass

## Reuse Rules

- Reuse existing shell — never create a second shell layout
- Reuse existing page header component on every authenticated page
- Reuse common settings framing (left nav + right content panel)
- Reuse common admin framing (same layout as settings)
- Reuse components from `08_ui_system_internal.md` before creating new ones
- Follow visual specs from `12_internal_component_specs.md` for all component dimensions, spacing, and states
- Follow screen archetypes from `11_internal_screen_archetypes.md` for page composition
- Follow data display rules from `13_internal_data_display_rules.md` for tables, charts, and metric presentation
- Extract shared patterns only when used in 3+ places

## Responsive Rules

- Mobile responsiveness is required from the first page built
- Desktop-only assumptions are not allowed
- Dense data views (tables, grids) need explicit mobile behavior defined
- Minimum touch target: 44x44px
- Test at 375px width (iPhone SE) as the baseline

## State Handling Rules

Every major page or module must account for:

- **Loading**: Skeleton placeholder matching the layout shape
- **Empty**: Helpful message with CTA to create first item (not a blank page)
- **Success**: Data rendered correctly with all interactions available
- **Validation failure**: Inline field errors, form-level summary if needed
- **System failure**: User-friendly error message with retry action
- **Permission denied**: Clear message, no raw 403 codes, link back to accessible area
- **Feature unavailable**: Upgrade prompt when feature requires a higher plan

## Coding Standards

- Use TypeScript strict mode — no `any` types in production code
- Server Components by default, Client Components only when interactivity requires it
- Colocate related files (component, styles, types, tests in the same directory)
- API routes and Server Actions validate input and check permissions independently
- Database queries always filter by organization_id for multi-tenancy isolation
- Sensitive data (tokens, secrets) stored encrypted, never logged or exposed in responses
- Use Prisma transactions for operations that modify multiple tables

## Quality Gates

Before marking any build phase complete:

1. All pages in the phase handle loading, empty, success, and error states
2. All pages are mobile responsive at 375px
3. Permissions are enforced at middleware, API, and UI layers
4. No TypeScript errors, no console warnings in production build
5. Navigation between pages works correctly (no dead ends, no broken links)

## Final Principle

The framework exists to reduce ambiguity, reduce drift, and reduce bugs. Build inside it first. Extend it only when the product actually requires extension.

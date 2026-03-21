# 00 Kickoff System

## Purpose

Define the initialization sequence for any new project that uses this framework repository.

## Core Rule

Do not start coding immediately.

First:
1. Read the framework docs
2. Read the template docs
3. Create project docs
4. Synthesize the implementation plan
5. Then build

## Source Of Truth Hierarchy

1. `docs/project/*` (app-specific, highest priority)
2. `docs/framework/internal/*`
3. `docs/framework/website/*`
4. `docs/framework/templates/*` (lowest priority)

If project docs conflict with framework docs, project docs win.

## Required Startup Sequence

### Step 1 — Read Framework

Read all files in:

- `docs/framework/website/` — public site specs, design tokens, component specs, page archetypes, copy rules
- `docs/framework/internal/` — authenticated app specs (shell, auth, dashboard, features, settings, routes, data models, UI system, design tokens, screen archetypes, component specs, data display rules, email system, breakpoints, dashboard archetypes, error taxonomy, testing strategy, i18n posture)
- `docs/framework/templates/` — blank templates with examples for project docs
- `docs/framework/prompts/` — this file and the master execution prompt

### Step 2 — Infer Product

Use the app idea from the conversation as the raw product input.

Infer:
- Target user
- Core problem
- First value event
- Dashboard shape (reference `16_dashboard_archetypes.md` for type)
- Onboarding logic
- Feature modules (reference `04_feature_modules.md` for available types)
- Roles
- Entities (reference `07_data_models.md` for core entities)
- v1 scope
- Non-goals
- Technical constraints

### Step 3 — Create Project Directory

Create `docs/project/` if it does not exist.

### Step 4 — Generate Project Files

Generate these files inside `docs/project/` using the template files:

- `00_app_idea.md`
- `01_project_brief.md`
- `02_feature_spec.md`
- `03_user_flows.md`
- `04_edge_cases.md`
- `05_tech_stack.md`
- `06_permissions_matrix.md`
- `07_acceptance_criteria.md`
- `08_qa_checklist.md`

### Step 5 — Populate with Concrete Content

Fill those files with concrete app-specific content. Do not leave them generic. Use the template examples as reference for tone and depth.

### Step 6 — Plan Implementation

Infer the implementation plan:
- Routes (reference `06_routes_and_permissions.md`)
- Modules (reference `04_feature_modules.md`)
- Entities (reference `07_data_models.md`)
- Onboarding flow
- Dashboard type and layout
- Settings and billing structure
- Admin needs
- Build phases

### Step 7 — Build

Build in this order (detailed in `09_build_rules_internal.md`):

1. **Foundation** — project setup, database schema, utilities
2. **Auth** — login, signup, password flows, email verification
3. **Onboarding** — multi-step setup, first value event
4. **Shell** — top bar, sidebar, drawer, page header, user menu. Configure design tokens from `10_design_tokens_internal.md`. Follow breakpoints from `15_canonical_breakpoints.md`.
5. **Dashboard** — summary row, main work area, analytics. Use appropriate dashboard archetype from `16_dashboard_archetypes.md`.
6. **Core features** — product-specific modules from project docs. Follow screen archetypes from `11_internal_screen_archetypes.md` and component specs from `12_internal_component_specs.md`.
7. **Settings and billing** — profile, workspace, Stripe integration
8. **Admin** — user management, billing overview, logs
9. **Email templates** — auth, billing, onboarding, notification emails per `14_email_system.md`
10. **Marketing site** — public pages from `docs/framework/website/` using public design tokens, component specs, page archetypes, and copy rules
11. **Edge cases and polish** — error states per `17_error_state_taxonomy.md`, QA checklist, acceptance criteria, dark mode, testing per `18_testing_strategy.md`

## Build Constraints

- Build only v1 scope unless the user explicitly requests otherwise
- Reuse shared patterns from `08_ui_system_internal.md` and component specs before creating new components
- Follow the canonical breakpoint scale from `15_canonical_breakpoints.md` for all responsive behavior
- Keep responsive from the start — test at 375px width
- Follow build rules from `09_build_rules_internal.md`
- Handle loading, empty, success, and error states on every page and component (see `17_error_state_taxonomy.md`)
- Enforce auth and permissions at middleware, API, and UI layers per `06_routes_and_permissions.md`
- Do not invent unrelated modules or features outside the v1 scope
- Follow coding standards from `09_build_rules_internal.md`
- English-first per `19_i18n_posture.md`, use Intl API for formatting

## Final Principle

The framework layer provides reusable defaults. The project layer provides instantiated truth. Always generate the project layer first, then build from both layers together.

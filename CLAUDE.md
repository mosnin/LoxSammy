# CLAUDE.md

## What This Repository Is

This is a reusable SaaS framework pack. It contains no code — only structured documentation that guides Claude Code through planning and building SaaS products. It is designed to be cloned into `docs/framework/` of any new project repository.

## How To Use This Repository

### For New Projects

1. Create your new project repository
2. Clone this repo into `docs/framework/` of that project
3. Provide your app idea as a detailed prompt
4. Claude will follow the kickoff sequence automatically

### Startup Sequence

When this framework is present in a project, follow this exact order:

1. **Read all framework docs** — `docs/framework/website/`, `docs/framework/internal/`, `docs/framework/templates/`, `docs/framework/prompts/`
2. **Infer the product** from the user's app idea — target user, core problem, first value event, dashboard shape, onboarding logic, feature modules, roles, entities, v1 scope
3. **Create `docs/project/`** in the target repository
4. **Generate 9 project files** from the templates, populated with concrete app-specific content:
   - `00_app_idea.md`
   - `01_project_brief.md`
   - `02_feature_spec.md`
   - `03_user_flows.md`
   - `04_edge_cases.md`
   - `05_tech_stack.md`
   - `06_permissions_matrix.md`
   - `07_acceptance_criteria.md`
   - `08_qa_checklist.md`
5. **Summarize the architecture** before writing any code — routes, modules, entities, implementation order
6. **Build in this order**: foundation → auth → onboarding → shell → dashboard → core features → settings/billing → admin → edge cases/polish

## Source of Truth Hierarchy

When docs conflict, follow this priority:

1. `docs/project/*` (app-specific, highest priority)
2. `docs/framework/internal/*`
3. `docs/framework/website/*`
4. `docs/framework/templates/*` (lowest priority)

## Default Tech Stack

Unless the user specifies otherwise, assume:

- **Frontend**: Next.js (app router) with TypeScript and Tailwind CSS
- **Auth**: Email/password with optional social OAuth and magic links
- **Database**: PostgreSQL with Prisma ORM
- **Billing**: Stripe (Checkout + Customer Portal)
- **Hosting**: Vercel
- **State**: React Context for auth/theme, server components where possible
- **UI**: Custom component library following `docs/framework/internal/08_ui_system_internal.md`

## Build Rules

- Do not start coding until project docs are generated and populated
- Build only v1 scope unless explicitly asked otherwise
- Reuse shared patterns from the framework before creating new ones
- Every page must be mobile responsive from the start
- Every data-driven view must handle four states: loading, empty, success, error
- Permissions must be enforced at both the routing layer and the UI layer
- Do not add features outside the defined v1 scope
- Do not modify files in `docs/framework/` — those are reusable defaults

## Repository Structure

```
docs/
  framework/
    website/        # Public marketing site specs (home page, pages, design tokens, components, sitemap, folder structure)
    internal/       # Authenticated app specs (shell, auth, dashboard, features, settings, routes, data models, UI, build rules)
    templates/      # Blank templates with examples for generating project-specific docs
    prompts/        # Kickoff sequence and master execution prompt
```

## Key Files To Read First

1. `docs/framework/prompts/00_kickoff_system.md` — the initialization protocol
2. `docs/framework/internal/09_build_rules_internal.md` — build order and constraints
3. `docs/framework/internal/07_data_models.md` — core entity definitions with fields
4. `docs/framework/internal/01_app_shell.md` — authenticated app frame structure
5. `docs/framework/website/saas_home_page_system.md` — marketing site conversion funnel

## Important Conventions

- File numbering indicates read/build order within each directory
- Template files contain example entries — use them as reference for tone and depth when generating project docs
- The framework philosophy: website docs govern acquisition, internal docs govern the product, templates define document shape, prompts define execution sequence
- This repo should remain static and reusable — never commit app-specific content here

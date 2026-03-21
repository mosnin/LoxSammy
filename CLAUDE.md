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
6. **Build in this order** (detailed in `docs/framework/internal/09_build_rules_internal.md`): foundation → auth → onboarding → shell → dashboard → core features → settings/billing → admin → email templates → marketing site → edge cases/polish

**Project docs must be generated before implementation begins.**

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
- **Email**: Resend or SendGrid for transactional email

## Build Rules

- Do not start coding until project docs are generated and populated
- Build only v1 scope unless explicitly asked otherwise
- Reuse shared patterns from the framework before creating new ones
- Every page must be mobile responsive from the start using `docs/framework/internal/15_canonical_breakpoints.md`
- Every data-driven view must handle four states: loading, empty, success, error
- Handle all error types per `docs/framework/internal/17_error_state_taxonomy.md`
- Permissions must be enforced at both the routing layer and the UI layer
- Do not add features outside the defined v1 scope
- Do not modify files in `docs/framework/` — those are reusable defaults
- English-first for v1 per `docs/framework/internal/19_i18n_posture.md`

## Repository Structure

```
docs/
  framework/
    website/
      saas_home_page_system.md        # Home page conversion funnel
      saas_website_page_system.md      # Multi-page site structure
      design_system_tokens.md          # Public site visual tokens (light + dark mode)
      component_library_spec.md        # Component inventory and rules
      public_screen_archetypes.md      # Canonical page patterns for public pages
      public_component_specs.md        # Visual specs for website components
      public_copy_conversion_rules.md  # Copy, CTA, and conversion rules
      nextjs_folder_structure.md       # Recommended folder structure
      sitemap_diagram.md               # Information architecture
    internal/
      01_app_shell.md                  # Authenticated app frame
      02_auth_and_onboarding.md        # Auth flows and activation
      03_dashboard_system.md           # Dashboard framework
      04_feature_modules.md            # Optional module specs (analytics, integrations, API, MCP, webhooks, notifications, usage, activity logs)
      05_settings_billing_admin.md     # Settings, billing, admin
      06_routes_and_permissions.md     # Route system and roles
      07_data_models.md                # Core entity definitions
      08_ui_system_internal.md         # Component behavior system
      09_build_rules_internal.md       # Build order and constraints
      10_design_tokens_internal.md     # Internal visual tokens
      11_internal_screen_archetypes.md # Canonical page patterns
      12_internal_component_specs.md   # Component visual specs
      13_internal_data_display_rules.md # Data presentation rules
      14_email_system.md               # Email templates and rules
      15_canonical_breakpoints.md      # Unified responsive breakpoints
      16_dashboard_archetypes.md       # Concrete dashboard patterns
      17_error_state_taxonomy.md       # Error handling patterns
      18_testing_strategy.md           # Testing expectations
      19_i18n_posture.md               # Internationalization stance
    templates/                         # Blank templates with examples for project docs
    prompts/                           # Kickoff sequence and master execution prompt
```

## Key Files To Read First

### Initialization
1. `docs/framework/prompts/00_kickoff_system.md` — the initialization protocol
2. `docs/framework/internal/09_build_rules_internal.md` — build order and constraints

### Internal Product
3. `docs/framework/internal/07_data_models.md` — core entity definitions with fields
4. `docs/framework/internal/01_app_shell.md` — authenticated app frame structure
5. `docs/framework/internal/10_design_tokens_internal.md` — internal product visual tokens
6. `docs/framework/internal/11_internal_screen_archetypes.md` — canonical page patterns for authenticated views
7. `docs/framework/internal/12_internal_component_specs.md` — component visual specs
8. `docs/framework/internal/04_feature_modules.md` — optional module specs with full layout guidance
9. `docs/framework/internal/16_dashboard_archetypes.md` — concrete dashboard patterns
10. `docs/framework/internal/17_error_state_taxonomy.md` — error handling for every error type

### Public Website
11. `docs/framework/website/saas_home_page_system.md` — marketing site conversion funnel
12. `docs/framework/website/design_system_tokens.md` — public site visual tokens
13. `docs/framework/website/public_screen_archetypes.md` — page patterns for public pages
14. `docs/framework/website/public_component_specs.md` — website component visual specs

### Cross-Cutting
15. `docs/framework/internal/15_canonical_breakpoints.md` — unified responsive breakpoints
16. `docs/framework/internal/14_email_system.md` — email templates and rules
17. `docs/framework/internal/18_testing_strategy.md` — testing expectations

## Important Conventions

- File numbering indicates read/build order within each directory
- Template files contain example entries — use them as reference for tone and depth when generating project docs
- The framework philosophy: website docs govern acquisition, internal docs govern the product, templates define document shape, prompts define execution sequence
- Internal and website use separate design tokens (different visual density) but share the same breakpoint scale and primary color
- This repo should remain static and reusable — never commit app-specific content here

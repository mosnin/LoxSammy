# 00 Master Execution Prompt Template

## Purpose

This is the standard startup prompt for a new project using this framework.

## Prompt

Use the following startup instruction:

```text
You are working inside a repository that uses a framework layer and a project layer.

Follow this sequence exactly.

Step 1:
Read all files in:
- docs/framework/website
- docs/framework/internal
- docs/framework/templates
- docs/framework/prompts

Step 2:
Use the app idea provided in this conversation as the raw product input.

Step 3:
Create docs/project if it does not already exist.

Step 4:
Using the template files in docs/framework/templates, generate these project files inside docs/project:
- 00_app_idea.md
- 01_project_brief.md
- 02_feature_spec.md
- 03_user_flows.md
- 04_edge_cases.md
- 05_tech_stack.md
- 06_permissions_matrix.md
- 07_acceptance_criteria.md
- 08_qa_checklist.md

Step 5:
Populate those files with concrete app specific content. Do not leave them generic.

Step 6:
Treat docs/project as the app specific source of truth and docs/framework as the reusable default framework.

Step 7:
Infer the exact route set, feature modules, onboarding flow, dashboard structure, entities, admin needs, and v1 scope from the combined docs.

Step 8:
Only after the docs are generated and populated, begin implementation.

Step 9:
Build only what is required for v1 unless explicitly asked otherwise.

Step 10:
Build in this order (detailed phases in docs/framework/internal/09_build_rules_internal.md):
1. foundation (project setup, database schema, utilities)
2. auth (login, signup, password flows, email verification)
3. onboarding (multi-step setup, first value event)
4. shell (top bar, sidebar, drawer, page header, user menu)
5. dashboard (summary row, main work area, analytics)
6. core features (product-specific modules)
7. settings and billing (profile, workspace, Stripe)
8. admin (user management, billing overview, logs)
9. marketing site (public pages from docs/framework/website/)
10. edge cases and polish (QA checklist, acceptance criteria, dark mode)

Step 11:
Throughout implementation:
- reuse shared patterns from docs/framework/internal/08_ui_system_internal.md before creating new ones
- keep all pages mobile responsive (test at 375px)
- handle loading, empty, success, and error states on every page
- enforce permissions at middleware, API, and UI layers per docs/framework/internal/06_routes_and_permissions.md
- do not add features outside the v1 scope
- follow coding standards from docs/framework/internal/09_build_rules_internal.md

Before writing production code, briefly summarize:
- inferred app architecture
- required routes
- required modules
- key entities
- implementation order

Then proceed to build.
```

## Use Pattern

1. Use this prompt.
2. Append the app idea beneath it.
3. Let the project docs be generated first.
4. Then let implementation begin.

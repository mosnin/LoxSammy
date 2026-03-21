# 00 Kickoff System

## Purpose

Define the initialization sequence for any new project that uses this framework repository.

## Core Rule

Do not start coding immediately.

First:
1. read the framework docs
2. read the template docs
3. create project docs
4. synthesize the implementation plan
5. then build

## Source Of Truth Hierarchy

1. docs/project/*
2. docs/framework/internal/*
3. docs/framework/website/*
4. docs/framework/templates/*

If project docs conflict with framework docs, project docs win.

## Required Startup Sequence

### Step 1

Read all files in:

- docs/framework/website
- docs/framework/internal
- docs/framework/templates
- docs/framework/prompts

### Step 2

Use the app idea from the conversation as the raw product input.

Infer:
- target user
- core problem
- first value event
- dashboard shape
- onboarding logic
- feature modules
- roles
- entities
- v1 scope
- non goals
- technical constraints

### Step 3

Create docs/project if it does not exist.

### Step 4

Generate these files inside docs/project using the template files:

- 00_app_idea.md
- 01_project_brief.md
- 02_feature_spec.md
- 03_user_flows.md
- 04_edge_cases.md
- 05_tech_stack.md
- 06_permissions_matrix.md
- 07_acceptance_criteria.md
- 08_qa_checklist.md

### Step 5

Populate those files with concrete app specific content.

### Step 6

Infer the implementation plan:
- routes
- modules
- entities
- onboarding
- dashboard
- settings
- billing
- admin
- phases

### Step 7

Build in this order (detailed in `09_build_rules_internal.md`):
1. foundation (project setup, database schema, utilities)
2. auth (login, signup, password flows, email verification)
3. onboarding (multi-step setup, first value event)
4. shell (top bar, sidebar, drawer, page header, user menu)
5. dashboard (summary row, main work area, analytics)
6. core features (product-specific modules from project docs)
7. settings and billing (profile, workspace, Stripe integration)
8. admin (user management, billing overview, logs)
9. marketing site (public pages from `docs/framework/website/`)
10. edge cases and polish (QA checklist, acceptance criteria, dark mode)

## Build Constraints

- Build only v1 scope unless the user explicitly requests otherwise
- Reuse shared patterns from `08_ui_system_internal.md` before creating new components
- Keep responsive from the start — test at 375px width
- Follow build rules from `09_build_rules_internal.md`
- Handle loading, empty, success, and error states on every page and component
- Enforce auth and permissions at middleware, API, and UI layers per `06_routes_and_permissions.md`
- Do not invent unrelated modules or features outside the v1 scope
- Follow coding standards from `09_build_rules_internal.md`

## Final Principle

The framework layer provides reusable defaults. The project layer provides instantiated truth. Always generate the project layer first, then build from both layers together.

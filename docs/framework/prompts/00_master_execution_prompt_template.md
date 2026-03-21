# 00 Master Execution Prompt Template

## Purpose

This is the standard startup prompt for a new project using this framework. Paste this into the conversation along with your app idea.

For the full initialization protocol and source of truth hierarchy, see `00_kickoff_system.md`.

## Prompt

Use the following startup instruction:

```text
You are working inside a repository that uses a framework layer and a project layer.

Follow the initialization sequence defined in docs/framework/prompts/00_kickoff_system.md.

In summary:

1. Read all files in docs/framework/ (website, internal, templates, prompts)
2. Use the app idea provided in this conversation as the raw product input
3. Create docs/project/ and generate the 9 project files from templates
4. Populate those files with concrete app-specific content — do not leave them generic
5. Treat docs/project/ as the app-specific source of truth, docs/framework/ as reusable defaults
6. Infer the route set, feature modules, onboarding flow, dashboard structure, entities, admin needs, and v1 scope
7. Only after docs are generated, begin implementation
8. Build in the order defined in docs/framework/internal/09_build_rules_internal.md:
   foundation → auth → onboarding → shell → dashboard → core features → settings/billing → admin → marketing site → polish

Throughout implementation:
- Follow the visual design pack (files 10-13) for all authenticated pages
- Follow website specs (design_system_tokens.md, public_component_specs.md, public_screen_archetypes.md) for marketing pages
- Follow the canonical breakpoint scale (15_canonical_breakpoints.md) for all responsive behavior
- Follow the email system (14_email_system.md) for all transactional and product emails
- Follow the error state taxonomy (17_error_state_taxonomy.md) for all error handling
- Reuse shared patterns before creating new ones
- Keep all pages mobile responsive
- Handle loading, empty, success, and error states on every page
- Enforce permissions at middleware, API, and UI layers
- Do not add features outside the v1 scope

Before writing production code, briefly summarize:
- inferred app architecture
- required routes
- required modules
- key entities
- implementation order

Then proceed to build.
```

## Use Pattern

1. Paste this prompt into a new conversation.
2. Append your app idea beneath it.
3. Let the project docs be generated first.
4. Then let implementation begin.

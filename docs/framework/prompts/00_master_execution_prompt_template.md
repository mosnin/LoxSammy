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
Throughout implementation:
- reuse shared patterns before creating new ones
- keep all pages mobile responsive
- handle loading, empty, success, and error states
- enforce permissions on protected and admin routes
- do not add features outside scope
- keep the product aligned with the app idea

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

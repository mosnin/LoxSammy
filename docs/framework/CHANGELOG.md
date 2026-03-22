# Changelog

All notable changes to this framework are documented here. Format follows [Keep a Changelog](https://keepachangelog.com/).

Each entry specifies: which files were added/changed/removed, what the change means for downstream projects, and whether it is **breaking** or **non-breaking**.

## [1.2.0] - 2026-03-22

### Added (non-breaking)
- **Modaf naming** — framework now has an official name. Added to CLAUDE.md, README.md, and MANIFEST.md so Claude recognizes "Modaf" as a reference to this framework.
- `docs/framework/internal/25_doctor_mode.md` — Safe diagnostic and repair system for framework and project docs. Runs 9 structural checks (file inventory, cross-references, internal links, manifest accuracy, phase coverage, required sections, table integrity, project doc completeness, CLAUDE.md consistency). Hard safety constraints: never deletes files, never rewrites content, never creates framework files, always diagnoses before repairing, logs every change.

### Changed (non-breaking)
- `CLAUDE.md` — Added Modaf name, doctor mode activation section, file 25 to repo structure
- `README.md` — Renamed from "SaaS Framework Repository" to "Modaf"
- `docs/framework/MANIFEST.md` — Added Modaf name, entry for file 25
- `docs/framework/VERSION.md` — Bumped to 1.2.0

## [1.1.0] - 2026-03-22

### Added (non-breaking)
- `docs/framework/internal/23_escape_hatches.md` — Technology swap guide for replacing default auth, billing, database, tenancy, email, and hosting choices
- `docs/framework/internal/24_error_recovery.md` — Phase re-run protocol with detection triggers, diagnosis, three recovery tiers, cascade analysis, and git safety
- `docs/framework/VERSION.md` — Semver versioning policy and merge strategy for downstream consumers
- `docs/framework/CHANGELOG.md` — This file

### Changed (non-breaking)
- `CLAUDE.md` — Added tech constraints to Phase 1 discovery interview, framework version reference, error recovery to global build rules, escape hatches reference in default tech stack
- `docs/framework/MANIFEST.md` — Added entries for files 23, 24, VERSION.md, and CHANGELOG.md
- `docs/framework/internal/09_build_rules_internal.md` — Added recovery protocol reference after quality gates section
- `docs/framework/internal/21_validation_gates.md` — Added escape hatch cross-reference for inapplicable gates, error recovery cross-reference in gate escalation
- `docs/framework/templates/05_tech_stack_template.md` — Added swap notes pointing to escape hatches per technology category
- `docs/framework/phases/phase_01_discovery.md` — Added tech constraints to interview coverage
- `docs/framework/phases/phase_03_architecture.md` — Added escape hatch reading step when defaults are overridden
- `docs/framework/prompts/00_kickoff_system.md` — Added error recovery to global build rules

## [1.0.0] - 2026-03-01

### Added
- Initial framework release
- 22 internal product docs (`docs/framework/internal/01–22`)
- 9 website docs (`docs/framework/website/`)
- 9 project doc templates (`docs/framework/templates/`)
- 15 phase index files (`docs/framework/phases/`)
- 2 prompt files (`docs/framework/prompts/`)
- MANIFEST.md file index
- CLAUDE.md master instruction file

# Phase 7 — App Shell

## Trigger
Onboarding (Phase 6) is complete.

## Files to Read
- `docs/framework/internal/01_app_shell.md` — shell structure
- `docs/framework/internal/10_design_tokens_internal.md` — visual tokens
- `docs/framework/internal/15_canonical_breakpoints.md` — responsive breakpoints

## What to Build

### Shell Components
- **Top bar**: logo, search, notifications, user menu
- **Sidebar**: navigation links, workspace switcher (if applicable), collapse behavior
- **Page header**: title, breadcrumbs, action buttons
- **User menu**: profile, settings, logout
- **Mobile drawer**: responsive sidebar replacement

### Design System Setup
- Configure design tokens (colors, spacing, typography, shadows, radii)
- Light and dark mode token sets
- Tailwind theme extension with token values

### Responsive Layout
- Sidebar visible at lg+ (1024px), drawer below
- Content area adapts across all 6 breakpoints
- Mobile-first implementation

### Navigation
- Route-based active states
- Role-aware nav items (hide items user can't access)
- Workspace switching (if multi-tenant)

### Verify
- Shell renders correctly at all breakpoints (375px → 1536px+)
- Sidebar collapses to drawer on mobile
- Dark mode toggles correctly
- Navigation highlights active route

## Exit Condition
App shell is responsive and functional. Summarize and ask user to continue to **Phase 8**.

# 08 UI System Internal

## Purpose

Define the internal product design system so that authenticated views remain polished, coherent, and usable. Every component below should be built once and reused across all feature modules.

## Core UI Principles

- Clarity over decoration — remove anything that does not serve the user's task
- Consistency over novelty — same patterns everywhere, no per-page inventions
- Reusable patterns over one-off layouts — extract after 3+ uses
- Explicit state handling — every component must account for its possible states
- Responsive behavior by default — mobile is not an afterthought
- Accessible interactions — keyboard navigable, screen reader friendly, sufficient contrast

## Canonical Internal Components

### App Shell
The persistent frame wrapping all authenticated pages. Contains top bar, sidebar/drawer, and main content area. Defined in detail in `01_app_shell.md`.

### Page Header
Appears at the top of every authenticated page inside the main content area.
- **Required**: Page title, primary action button (e.g., "New Invoice", "Add Client")
- **Optional**: Breadcrumbs, description text, secondary actions, filters, date range selector
- **Behavior**: Sticky on scroll (optional per product). Primary action always visible on mobile.

### Sidebar Nav
Desktop navigation panel. Rendered inside the shell.
- **Sections**: Core features (top), optional modules (middle), Settings and Admin (bottom)
- **Active state**: Highlight current route, support nested items with expand/collapse
- **Role filtering**: Hide items the user's role cannot access — do not show disabled items

### Mobile Drawer
Replaces sidebar on screens under 768px. Triggered by hamburger icon in top bar.
- **Behavior**: Slides in from left with backdrop overlay. Closes on backdrop tap, nav item selection, or swipe.
- **Content**: Same items as sidebar plus logout, billing shortcut, and user info header.

### Card
General-purpose content container.
- **Variants**: Default (bordered), elevated (shadow), interactive (hover state + click handler)
- **Structure**: Optional header (title + action), body content, optional footer
- **Sizing**: Full-width on mobile, grid-based on desktop (2-col, 3-col, 4-col)

### Stat Card
Specialized card for displaying a single metric in summary rows.
- **Structure**: Label, value (large text), optional trend indicator (up/down arrow with percentage), optional comparison period
- **Sizing**: Fixed height, equal width in a row. Stack vertically on mobile.

### Table
For displaying lists of structured data (invoices, clients, users, logs).
- **Features**: Sortable columns (click header), row actions (edit, delete, view), bulk select (optional), pagination
- **States**: Loading (skeleton rows), empty (message + CTA), error (retry prompt)
- **Mobile**: Switch to card layout below 768px — each row becomes a stacked card with key fields visible

### List
Simpler alternative to table for non-tabular data (activity feeds, notifications, search results).
- **Structure**: Avatar/icon + primary text + secondary text + timestamp + optional action
- **Behavior**: Click to navigate to detail. Infinite scroll or "Load more" for pagination.

### Form
Standard form layout for create/edit operations.
- **Layout**: Single column, label above input. Group related fields with section headers.
- **Validation**: Inline errors below each field on blur or submit. Required fields marked with asterisk.
- **Actions**: Primary submit button (right-aligned), secondary cancel button. Disable submit while loading.
- **States**: Default, loading (spinner on submit button), success (toast notification), error (inline + optional banner)

### Modal / Dialog
For confirmations, quick actions, and focused input that does not warrant a full page.
- **Variants**: Confirm (destructive action warning), form (quick create/edit), info (detail view)
- **Behavior**: Backdrop click closes (unless form has unsaved changes). Escape key closes. Focus trapped inside modal.
- **Sizing**: Small (confirm), medium (form), large (detail). Max-width on desktop, full-width on mobile.

### Tabs
For switching between views within a single page context.
- **Behavior**: Content changes without page navigation. Active tab is visually distinct. URL updates with tab ID for deep linking.
- **Mobile**: Horizontal scroll if tabs overflow. Do not wrap to multiple lines.

### Badge
Inline status indicator.
- **Variants**: Status (active/green, warning/yellow, error/red, neutral/gray), count (notification count), label (category tag)
- **Sizing**: Small (inline with text), default (standalone)

### Empty State
Displayed when a list, table, or dashboard section has no data.
- **Structure**: Illustration or icon (optional), heading ("No invoices yet"), description ("Create your first invoice to get started"), primary CTA button
- **Rule**: Never show a blank area. Every empty state must explain what goes here and how to populate it.

### Loading Skeleton
Placeholder shown while data loads. Must match the shape of the content it replaces.
- **Types**: Text lines (paragraph skeleton), table rows (row skeleton), cards (card skeleton), stat values (number skeleton)
- **Animation**: Subtle pulse or shimmer. No spinning loaders except on buttons.

### Error Block
Displayed when a page or section fails to load.
- **Structure**: Error icon, heading ("Something went wrong"), description (user-friendly, not a stack trace), retry button
- **Placement**: Replaces the content area that failed. Does not replace the entire shell.

### Action Bar
Fixed bar at the bottom of the page for bulk operations or unsaved changes.
- **Trigger**: Appears when user selects multiple items (bulk) or modifies a form (unsaved changes)
- **Structure**: Count/status text (left), action buttons (right: Save, Discard, Delete Selected)
- **Behavior**: Sticky to bottom of viewport. Disappears when action completes or selection is cleared.

## Component Composition Rules

1. Components nest but do not duplicate — a Page Header inside a Modal is wrong.
2. State handling is per-component — a Table inside a Card can be loading while the Card header is visible.
3. Mobile behavior is defined per-component — each component knows how it degrades.
4. Interactive components (buttons, links, form inputs) must have visible focus states for keyboard navigation.
5. Destructive actions (delete, remove, disconnect) always require a confirmation Modal.

## Final Principle

The internal UI system should create a stable visual and interaction language so the product feels like one system regardless of how many modules it includes.

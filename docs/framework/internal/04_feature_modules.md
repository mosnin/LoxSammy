# 04 Feature Modules

## Purpose

Define the reusable module types that may be attached to different SaaS applications. Each module is optional — only include what the product requires.

## Core Principle

Modules plug into the shared shell. They must not invent unrelated navigation or UI systems. Every module uses the shared page header, sidebar navigation placement, and state handling patterns.

## Canonical Optional Modules

### Analytics

Purpose: Show product usage data and business metrics to the user.
Typical views: Overview dashboard with charts, date range selector, metric cards, exportable reports.
Data source: Reads from Analytics Summary entity (pre-aggregated) and optionally Usage Event for drill-downs.
Access: Typically available to all roles, with admin seeing org-wide data and members seeing their own.

### Integrations

Purpose: Connect third-party services to the product.
Typical views: Integration marketplace (grid of available providers), connected integrations list, per-integration config panel.
Pattern: Each integration has a status (active, disconnected, error), a connect/disconnect action, and a settings panel for provider-specific configuration.
Data source: Integration entity.
Access: Admin and owner only for connecting/disconnecting. Members may view connected integrations.

### API

Purpose: Allow users to programmatically access product features.
Typical views: API key management (create, revoke, copy), usage stats per key, documentation link.
Pattern: Keys are scoped to the organization. Show last used timestamp. Require confirmation before revocation.
Access: Admin and owner only.

### Webhooks

Purpose: Push event notifications to external URLs.
Typical views: Webhook endpoint list, create/edit form (URL, events, secret), delivery log with retry status.
Pattern: Each webhook has a URL, subscribed event types, a signing secret, and a delivery history. Failed deliveries show error details and allow manual retry.
Access: Admin and owner only.

### Notifications

Purpose: In-app and email notification preferences and history.
Typical views: Notification center (bell icon dropdown or page), preference settings per notification type.
Pattern: Notifications have read/unread state, a link to the relevant resource, and a timestamp. Preferences control which notifications generate email vs in-app only.
Data source: Notification records linked to User and Organization.
Access: All authenticated users see their own notifications. Preferences are per-user.

### Usage

Purpose: Show resource consumption against plan limits.
Typical views: Usage meter bars, current period stats, historical usage chart, limit warnings.
Pattern: Pull from Usage Event aggregations. Show percentage of plan limit consumed. Trigger upgrade prompts at 80% and 100%.
Access: All roles can view their own usage. Admin sees org-wide usage.

### Activity Logs

Purpose: Audit trail of actions taken within the product.
Typical views: Chronological log with actor, action, target, and timestamp. Filterable by user, action type, and date range.
Data source: Usage Event and Admin Record entities.
Access: Admin and owner only for org-wide logs. Members may see their own activity.

## Shared Module Rules

1. Only include modules relevant to the product.
2. Module pages must use the same page header and layout framing as all other app pages.
3. Every module must support loading, empty, success, and error states.
4. Technical configuration pages (API, webhooks, integrations) need helper text, input validation, and confirmation dialogs for destructive actions.
5. Module navigation items appear in the sidebar below core product features and above Settings.
6. Modules must respect the permissions matrix — hide navigation items for unauthorized roles, enforce at the API layer.

## Final Principle

Modules should be optional but standardized. If a module exists, it should feel like part of the product, not a bolted on control panel.

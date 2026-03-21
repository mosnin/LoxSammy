# Phase 11 — Admin

## Trigger
Settings & billing (Phase 10) are complete.

## Files to Read
- `docs/framework/internal/05_settings_billing_admin.md` — admin sections

## What to Build

### Admin Dashboard
- Platform-wide metrics (total users, orgs, revenue, active subscriptions)
- Recent signups, recent activity
- System health indicators (if applicable)

### User Management
- User list with search, filter, pagination
- User detail view (profile, org membership, subscription, activity)
- Impersonate user (if in v1 scope)
- Suspend/unsuspend, delete user

### Billing Overview
- Revenue summary, MRR/ARR
- Subscription list by plan
- Failed payments, past-due accounts

### System Logs
- Admin action log (who did what)
- Error log summary (if applicable)

### Permission Enforcement
- Admin routes only accessible to admin role
- Middleware-level protection (not just UI hiding)
- Audit logging for admin actions

### Verify
- Admin dashboard shows correct platform metrics
- User management CRUD works
- Admin routes are inaccessible to non-admin users
- Admin actions are logged

## Exit Condition
Admin panel is functional. Summarize and ask user to continue to **Phase 12**.

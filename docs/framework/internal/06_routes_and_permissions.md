# 06 Routes And Permissions

## Purpose

Define the canonical route system, role visibility logic, and permission rules for the application layer.

## Route Categories

- public routes
- auth routes
- protected routes
- admin routes
- error or utility routes

## Public Or Auth Routes

Typical routes:

- /login
- /signup
- /forgot-password
- /reset-password
- /verify-email
- /invite

## Protected Routes

Typical routes:

- /dashboard
- /analytics
- /features
- /integrations
- /api
- /mcp
- /webhooks
- /settings/profile
- /settings/workspace
- /settings/billing
- /settings/security
- /settings/notifications

## Admin Routes

Typical routes:

- /admin
- /admin/users
- /admin/users/[id]
- /admin/billing
- /admin/usage
- /admin/system
- /admin/logs
- /admin/flags

## Canonical Roles

- guest
- member
- manager when relevant
- admin
- owner

## Access Rules

1. Public pages redirect authenticated users away when appropriate.
2. Protected pages require authentication.
3. Admin pages require admin level access.
4. Module pages require both feature availability and permission.

## Final Principle

Permissions must be enforced in both routing and UI visibility. Hiding a button is not real access control.

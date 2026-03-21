# 07 Data Models

## Purpose

Define the canonical core entities for SaaS products so that data modeling stays stable and consistent across projects. Product specific entities attach to these — they do not replace them.

## Canonical Core Entities

### User

| Field | Type | Notes |
|-------|------|-------|
| id | uuid | primary key |
| email | string | unique, required |
| name | string | display name |
| avatar_url | string | nullable |
| email_verified | boolean | default false |
| password_hash | string | nullable if social auth only |
| last_login_at | timestamp | nullable |
| created_at | timestamp | |
| updated_at | timestamp | |

### Organization

| Field | Type | Notes |
|-------|------|-------|
| id | uuid | primary key |
| name | string | workspace display name |
| slug | string | unique, used in URLs |
| logo_url | string | nullable |
| plan | enum | free, starter, pro, enterprise |
| created_by | uuid | FK to User |
| created_at | timestamp | |
| updated_at | timestamp | |

### Membership

Joins User to Organization with a role. A user can belong to multiple organizations.

| Field | Type | Notes |
|-------|------|-------|
| id | uuid | primary key |
| user_id | uuid | FK to User |
| organization_id | uuid | FK to Organization |
| role | enum | member, manager, admin, owner |
| status | enum | active, invited, suspended |
| invited_email | string | nullable, for pending invites |
| invited_at | timestamp | nullable |
| joined_at | timestamp | nullable |
| created_at | timestamp | |

Unique constraint on (user_id, organization_id).

### Subscription

| Field | Type | Notes |
|-------|------|-------|
| id | uuid | primary key |
| organization_id | uuid | FK to Organization |
| stripe_customer_id | string | from billing provider |
| stripe_subscription_id | string | from billing provider |
| plan | enum | free, starter, pro, enterprise |
| status | enum | active, trialing, past_due, canceled, paused |
| current_period_start | timestamp | |
| current_period_end | timestamp | |
| cancel_at_period_end | boolean | default false |
| created_at | timestamp | |
| updated_at | timestamp | |

### Settings

Per-organization configuration. Key-value or structured JSON depending on product needs.

| Field | Type | Notes |
|-------|------|-------|
| id | uuid | primary key |
| organization_id | uuid | FK to Organization, unique |
| preferences | jsonb | notification prefs, feature toggles, defaults |
| onboarding_completed | boolean | default false |
| onboarding_step | string | nullable, tracks progress |
| created_at | timestamp | |
| updated_at | timestamp | |

### Integration

| Field | Type | Notes |
|-------|------|-------|
| id | uuid | primary key |
| organization_id | uuid | FK to Organization |
| provider | string | e.g. slack, github, stripe |
| status | enum | active, disconnected, error |
| access_token | string | encrypted |
| refresh_token | string | encrypted, nullable |
| config | jsonb | provider-specific settings |
| connected_by | uuid | FK to User |
| connected_at | timestamp | |
| created_at | timestamp | |

### Usage Event

Append-only log for metering and analytics.

| Field | Type | Notes |
|-------|------|-------|
| id | uuid | primary key |
| organization_id | uuid | FK to Organization |
| user_id | uuid | FK to User, nullable for system events |
| event_type | string | e.g. api_call, message_sent, file_uploaded |
| metadata | jsonb | event-specific data |
| created_at | timestamp | immutable |

Index on (organization_id, event_type, created_at) for queries.

### Analytics Summary

Pre-aggregated rollups computed from Usage Events. Avoids expensive queries on raw events.

| Field | Type | Notes |
|-------|------|-------|
| id | uuid | primary key |
| organization_id | uuid | FK to Organization |
| period | enum | daily, weekly, monthly |
| period_start | date | |
| metric | string | e.g. total_api_calls, active_users, storage_used |
| value | numeric | |
| created_at | timestamp | |

Unique constraint on (organization_id, period, period_start, metric).

### Admin Record

System-level audit trail for admin actions.

| Field | Type | Notes |
|-------|------|-------|
| id | uuid | primary key |
| actor_id | uuid | FK to User (admin who performed action) |
| target_type | string | e.g. user, organization, subscription |
| target_id | uuid | |
| action | string | e.g. suspended_user, changed_plan, toggled_flag |
| details | jsonb | before/after state or context |
| created_at | timestamp | immutable |

## Relationships

```
User 1──M Membership M──1 Organization
Organization 1──1 Subscription
Organization 1──1 Settings
Organization 1──M Integration
Organization 1──M Usage Event
Organization 1──M Analytics Summary
User 1──M Admin Record (as actor)
```

## Extending With Product Entities

Product specific entities should reference Organization (for multi-tenancy) and optionally User (for ownership). Example pattern:

```
Project (product entity)
├── id: uuid
├── organization_id: uuid (FK to Organization)
├── created_by: uuid (FK to User)
├── name: string
├── status: enum
├── created_at: timestamp
└── updated_at: timestamp
```

## Core Principle

Use a small set of stable core entities, then attach product specific entities to them. Never reinvent user, organization, membership, or billing models per project.

## Final Principle

Core entities should remain stable across projects. Product specific entities should extend them cleanly rather than reinventing account and permission logic every time.

# 05 Settings Billing Admin

> **TL;DR:** Defines the canonical settings sections, billing capabilities, security controls, admin panel areas, and user management features.
> **Covers:** profile settings, workspace settings, billing, security, admin overview, user management | **Depends on:** None | **Used by:** 06, 09, 11 | **Phase:** 10, 11

## Purpose

Define the canonical account control surfaces for SaaS applications.

## Settings Areas

### Canonical Settings Sections

- profile
- workspace or organization
- billing
- security
- notifications
- integrations settings when relevant

## Billing

### Required Billing Capabilities

- current plan
- billing interval
- next invoice visibility when relevant
- payment method
- invoice history
- upgrade or downgrade
- cancellation path
- usage when pricing is usage based

## Security

### Typical Capabilities

- password update
- active sessions
- two factor auth when supported
- session revocation
- audit visibility when relevant

## Admin System

Admin must be role gated and separated from normal user space.

### Canonical Admin Areas

- admin overview
- user management
- billing visibility
- usage visibility
- system health
- logs
- feature flags when relevant

## User Management

### Required Capabilities

- search users
- filter by role or status
- view detail
- edit role when allowed
- suspend or deactivate
- view onboarding state
- view subscription state

## Final Principle

Settings, billing, and admin are leverage systems. They should be first class parts of the product, not afterthoughts hidden behind awkward menus.

# 07 Data Models

## Purpose

Define the canonical core entities for SaaS products so that data modeling stays stable and consistent across projects.

## Canonical Core Entities

- User
- Organization
- Membership
- Subscription
- Settings
- Integration
- Usage Event
- Analytics Summary
- Admin Record

## Core Principle

Use a small set of stable core entities, then attach product specific entities to them.

## Final Principle

Core entities should remain stable across projects. Product specific entities should extend them cleanly rather than reinventing account and permission logic every time.

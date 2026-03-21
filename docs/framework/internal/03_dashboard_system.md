# 03 Dashboard System

## Purpose

Define the canonical dashboard framework for authenticated SaaS users.

## Dashboard Principle

The dashboard must answer:

1. what is happening
2. what needs attention
3. what should happen next
4. what value is being created

## Canonical Dashboard Anatomy

1. page header
2. summary row
3. main work area
4. secondary insights
5. recent activity
6. alerts or recommendations
7. empty states when no data exists

## Summary Row

Use summary cards for meaningful metrics or statuses.

## Main Work Area

The main work area is the product core.

### Example Patterns

- queue
- pipeline
- inbox
- workflow runner
- content workspace
- feed
- calendar
- task board
- report view

## Analytics Requirement

Most products should have an analytics page or analytics section.

### Standard Analytics Contents

- overview metrics
- trends
- segments
- funnel or flow analysis when relevant
- top entities
- date filters

## Role Aware Logic

Dashboard composition may vary by:

- role
- plan
- setup state
- module access
- data availability

## Required States

Every dashboard must support:

- loading
- empty
- zero data
- partial data
- error
- restricted access
- offline or sync failure when relevant

## Mobile Rules

- stack summary cards predictably
- avoid unnecessary horizontal scroll
- collapse tables intelligently
- keep actions visible

## Final Principle

A dashboard is not a wall of charts. It is an operational control surface centered around the core job the user is trying to accomplish.

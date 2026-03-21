# 04 Feature Modules

## Purpose

Define the reusable module types that may be attached to different SaaS applications.

## Core Principle

Modules plug into the shared shell. They must not invent unrelated navigation or UI systems.

## Canonical Optional Modules

- analytics
- integrations
- API
- MCP
- webhooks
- notifications
- usage
- activity logs
- external API configuration

## Shared Module Rules

1. Only include modules relevant to the product.
2. Module pages must use the same page header and layout framing.
3. Every module must support loading, empty, success, and error states.
4. Technical configuration pages need helper text and validation.

## Final Principle

Modules should be optional but standardized. If a module exists, it should feel like part of the product, not a bolted on control panel.

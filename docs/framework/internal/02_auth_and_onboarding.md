# 02 Auth And Onboarding

> **TL;DR:** Defines the canonical auth routes, page layouts, email verification, onboarding sequence, and first value event delivery for user activation.
> **Covers:** login, signup, password reset, email verification, invite flow, onboarding steps, first value event | **Depends on:** None | **Used by:** 06, 09 | **Phase:** 5, 6

## Purpose

Define the canonical user entry and activation flow for SaaS applications.

## Auth Routes

### Required Routes

- login
- sign up
- forgot password
- reset password
- verify email
- invite acceptance when relevant

### Optional Routes

- magic link
- social auth
- SSO
- two factor challenge

## Auth Page Layout

### Desktop

Use a split layout.

Left:
- form
- page heading
- support copy
- auth options

Right:
- branded visual
- testimonial
- trust statement

### Mobile

- single column
- form first
- reduce visual clutter
- prioritize fast completion

## Auth Rules

1. All forms need validation.
2. All forms need loading and error states.
3. Success states must clearly explain what happens next.
4. Login and sign up should link to each other.
5. Sensitive changes may require reauthentication.

## Invite Flow

If team invites exist, invite acceptance must show:

- invited workspace or team
- inviter identity when available
- accept and continue path
- clean merge into signup or login

## Email Verification Rules

1. Make verification state visible when it matters.
2. Support resend actions.
3. Do not create dead end screens.

## Onboarding Purpose

The purpose of onboarding is to get the user to first value quickly.

It is not a dumping ground for every possible preference.

## Required Onboarding Goals

- identify user type or use case
- capture required setup inputs
- connect required services or data
- establish defaults
- deliver first useful output

## Canonical Onboarding Sequence

1. role or use case
2. required configuration
3. integrations or data connection if needed
4. preferences or defaults
5. first output or first workspace

## Branching Logic

Onboarding may branch by:

- role
- use case
- plan
- technical sophistication
- whether data connection is mandatory
- whether team or solo workflow applies

## First Value Event

Every product must define a first value event.

## Onboarding Rules

1. Each step should have one clear objective.
2. Users should understand progress.
3. Skip optional setup when possible.
4. Preserve progress if the flow is interrupted.
5. Support validation, loading, success, and failure states.
6. Route users to the most relevant first destination after completion.

## Incomplete Setup Handling

If a user leaves onboarding early:

- preserve progress
- show setup checklist
- keep required next steps obvious
- do not block all usage unless necessary

## Final Principle

Onboarding should be dynamic to the app, but the system around it should remain reusable and activation focused.

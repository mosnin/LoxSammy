# Public Website Next.js Folder Structure

## Purpose

Define a clean recommended folder structure for building the public SaaS website in Next.js.

## Recommended Root Structure

```text
app/
components/
lib/
hooks/
public/
styles/
types/
```

## App Directory

```text
app/
  layout.tsx
  page.tsx
  product/
    page.tsx
  pricing/
    page.tsx
  solutions/
    page.tsx
  case-studies/
    page.tsx
  features/
    page.tsx
  integrations/
    page.tsx
  security/
    page.tsx
  docs/
    page.tsx
  blog/
    page.tsx
  about/
    page.tsx
  contact/
    page.tsx
  privacy/
    page.tsx
  terms/
    page.tsx
```

## Components Directory

```text
components/
  layout/
  navigation/
  sections/
  cards/
  forms/
  ui/
```

## Public Assets

```text
public/
  images/
  logos/
  icons/
```

## Naming Rules

- use lowercase folders
- use hyphen separated route names
- avoid deeply nested route complexity unless necessary

## Final Principle

Folder structure should support clarity and reuse. Public site sections should be organized by component type and route intent, not by random page one offs.

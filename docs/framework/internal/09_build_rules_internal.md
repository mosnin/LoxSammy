# 09 Build Rules Internal

## Purpose

Define how the internal framework must be used during implementation.

## Core Rule

Read the framework first. Generate the project docs next. Build only after both layers exist.

## Source Of Truth Hierarchy

1. docs/project/*
2. docs/framework/internal/*
3. docs/framework/website/*
4. docs/framework/templates/*

## Reuse Rules

- reuse existing shell
- reuse existing page header
- reuse common settings framing
- reuse common admin framing
- reuse components before creating new ones

## Responsive Rules

- mobile responsiveness is required
- desktop only assumptions are not allowed
- dense data views need mobile behavior defined

## State Handling Rules

Every major page or module must account for:

- loading
- empty
- success
- validation failure
- system failure
- permission denied
- feature unavailable when relevant

## Final Principle

The framework exists to reduce ambiguity, reduce drift, and reduce bugs. Build inside it first. Extend it only when the product actually requires extension.

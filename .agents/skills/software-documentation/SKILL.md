---
name: software-documentation
description: Modular, component-driven software documentation protocol ensuring each component, module, and service maintains its own isolated documentation.
---

# Software Component Documentation Skill

## Purpose
In modern software engineering, monolithic documentation quickly degrades and becomes unmaintainable. This skill enforces modular, component-level documentation: **if a part, module, or component of the software system has a distinct responsibility, it must maintain its own dedicated documentation file or section**.

## Core Principles
1. **Single Responsibility per Document**: Each component document describes one well-bounded software module (UI component, backend service, API router, data model, or background worker).
2. **Interface First**: Always define input contracts (props, parameters, payloads) and output contracts (return types, events, side effects).
3. **Internal State & Invariants**: Document state machines, reactivity, caches, and assumptions.
4. **Error Handling & Failure Modes**: Detail how edge cases, validation errors, and network timeouts are handled.
5. **Cross-Linking**: Link directly to dependent modules and tests.

## File Organization Structure
Organize software documentation under `.agents/wiki/pages/` or alongside the source code in `docs/components/`:
```
docs/
├── architecture-overview.md
└── components/
    ├── auth-service.md
    ├── database-connector.md
    ├── ui-navigation-bar.md
    └── payment-processor.md
```

## Available Templates
* UI / Functional Component: `.agents/skills/software-documentation/templates/COMPONENT_TEMPLATE.md`
* Service / Backend Module: `.agents/skills/software-documentation/templates/SERVICE_MODULE_TEMPLATE.md`

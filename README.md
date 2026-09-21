# LabDraft

> AI-assisted lab manual and practical write-up workspace for engineering and science students.

[Visit LabDraft](https://labdraft.in)

Current public release: **v2.0.2 — Reliability & Responsive Polish**

## About

LabDraft helps students turn a practical aim or syllabus into a structured laboratory write-up. It supports engineering and general science workflows, guided configuration, bulk drafting, document export, and an integrated coding workspace.

This repository is a **public product showcase**. The production application, prompts, infrastructure configuration, security controls, database implementation, and deployment source remain private.

## Product capabilities

- Engineering and general science practical drafting
- Single-practical and bulk-manual workflows
- Structured sections such as aim, theory, procedure, algorithm, code, observations, results, and conclusion
- PDF and DOCX export with institution branding options
- Code Studio for code generation and output workflows
- Subject search and guided configuration
- Optional accounts and a private saved-practicals library
- Responsive interfaces for compact phones, tablets, and desktop workstations
- Multiple AI providers with health-aware failover and a free-only production cost policy

## Public architecture summary

```text
Student experience
        ↓
Server-side application services
        ↓
Protected AI orchestration and validation
        ↓
Structured practical result
        ↓
Browser preview, document export, and optional private cloud library
```

A deliberately high-level architecture description is available in [ARCHITECTURE.md](ARCHITECTURE.md). Operational endpoints, prompts, schemas, provider configuration, and security implementation details are intentionally excluded.

## Release highlights — v2.0.2

- Stronger free-only AI routing and graceful temporary-capacity handling
- Improved provider health and bulk-generation reliability
- Protected read-only database activity monitoring
- Collision-free homepage, header, card, and feedback layouts from compact 320px phones upward
- Improved feedback controls, touch targets, and accessibility states

## Project status

LabDraft is an actively developed Kaizun Labs product. This public repository is informational and is not an open-source distribution of the production application.

## Security

Please do not publish suspected vulnerabilities in a public issue. See [SECURITY.md](SECURITY.md) for responsible disclosure guidance.

## Ownership

Copyright © 2026 Kaizun Labs. All rights reserved.

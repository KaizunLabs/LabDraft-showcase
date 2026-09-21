# LabDraft — Public Architecture Overview

This document describes LabDraft at a product-system level. It intentionally omits production source code, internal prompts, API paths, model identifiers, database schemas, environment variables, deployment configuration, and defensive implementation details.

## System view

```text
┌──────────────────────────────────────────┐
│ Student experience                       │
│ Guided forms · preview · export · library│
└────────────────────┬─────────────────────┘
                     │ validated requests
┌────────────────────▼─────────────────────┐
│ Application services                     │
│ Access control · validation · rate limits│
└───────────────┬─────────────────┬────────┘
                │                 │
┌───────────────▼──────────┐  ┌──▼────────────────────┐
│ AI orchestration         │  │ Private user data     │
│ Health-aware free routing│  │ Authenticated storage │
│ Structured output checks │  │ Ownership boundaries  │
└───────────────┬──────────┘  └──┬────────────────────┘
                │                 │
┌───────────────▼─────────────────▼────────┐
│ Practical result and document pipeline   │
│ Reviewable content · PDF · DOCX · figures│
└───────────────────────────────────────────┘
```

## Major responsibilities

### Student experience

The responsive web application provides guided input, subject selection, generation progress, result review, document customization, and export. Engineering, general science, and coding workflows share a consistent design system while retaining workflow-specific controls.

### Application services

Server-side services validate untrusted input, apply request and usage controls, enforce access boundaries, and coordinate longer-running generation work. Credentials and privileged logic stay outside browser code.

### AI orchestration

LabDraft uses an internal provider abstraction with health-aware failover, bounded retries, structured-output validation, and task context. Production routing is intentionally restricted to approved free capacity and returns a temporary-capacity response instead of silently selecting paid inference.

### Data and identity

Optional accounts provide a private saved-practicals library and revision history. Authorization is enforced at both the application and data layers so one user cannot access another user's records.

### Documents

Generated content is normalized into structured practical sections before preview and export. PDF and DOCX documents are produced from reviewed result data and user-selected branding options.

## Trust boundaries

- User text and uploaded files are treated as untrusted input.
- Model output is treated as untrusted until parsed and validated.
- Secrets and provider credentials remain server-side.
- Authentication and authorization are enforced independently of visible UI state.
- Operational diagnostics avoid prompts, credentials, and sensitive user content.
- Scheduled database activity is protected, minimal, and read-only.

## Intentionally private

The following are not published in this showcase:

- Source code and internal component structure
- Prompt templates and output-repair logic
- Provider and model configuration
- API routes and request contracts
- Database tables, policies, and migrations
- Environment-variable names or deployment configuration
- Rate-limit thresholds and security-control implementation
- Telemetry formats and operational runbooks

This boundary allows the product architecture and engineering intent to be visible without turning the showcase into a map of the production system.

# Technical Case Study

## Product Context

SolPro Platform is designed for real estate agencies operating in premium coastal and investment markets. The main users are agents, agency owners, and platform administrators.

The operational goal is simple: when an agent opens the dashboard, they should understand which leads need attention, why those leads matter, and what action should happen next.

## System Boundaries

The platform separates two major experiences:

- Public portal: buyer-facing property discovery and lead capture.
- Agent dashboard: authenticated CRM, property management, lead workflows, and admin operations.

This separation keeps buyer interactions lightweight while preserving richer operational workflows for agency users.

## Backend Design

The backend is organized around a layered architecture:

- API layer for HTTP controllers, contracts, OpenAPI, CORS, and auth wiring.
- Application layer for use cases and workflow orchestration.
- Domain layer for entities, business rules, scoring concepts, and tenant ownership.
- Infrastructure layer for Entity Framework Core, database configuration, and external provider implementations.

Core domains include agencies, users, properties, leads, notes, activities, pipeline stages, reports, audit logs, and AI analyses.

## Multi-Tenant Model

Agency ownership is a key design constraint. Tenant-owned records must include an agency boundary, and backend endpoints must enforce access on the server side.

Important rules:

- Never trust frontend agency or role values.
- Restrict agency-owned records by authenticated membership.
- Keep public listing visibility separate from private agency drafts.
- Treat listing ownership and lead assignment as related but separate concerns.

## Frontend Design

The dashboard is designed as a work-focused CRM, not a marketing page. It prioritizes density, scanability, clear status signals, and fast repeated actions.

The public portal focuses on trust, premium property presentation, and clear conversion paths for qualified buyer leads.

## Production Readiness Planning

The private project includes planning for:

- Database migrations
- Environment-specific secrets
- Custom domains
- Email delivery
- Image storage
- AI provider configuration
- Pre-pilot verification steps
- Build/test checks before agency pilots

## Lessons Learned

- A portfolio project is stronger when it models real users and operational workflows.
- Multi-tenant systems require authorization rules at the backend, not only in UI state.
- Documentation matters when a project grows beyond a simple demo.
- Recruiters can understand impact faster through a case study than through raw code alone.
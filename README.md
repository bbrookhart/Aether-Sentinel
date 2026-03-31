# AetherSentinel

**Secure agentic triage and decision support for high-trust environments**

AetherSentinel is a secure, tool-using AI platform designed to help analysts review documents, query structured records, answer grounded questions, and propose controlled actions in regulated or high-risk environments. The system is built around explicit approval gates, strong auditability, and bounded tool use so that useful AI assistance does not become unsafe autonomy.

## Core Features

- Document ingestion and retrieval
- Structured record lookup
- Grounded question answering
- Action proposal workflow
- Approval gates for write-capable actions
- Audit logging for key decisions and tool activity

## Non-Goals (v1)

AetherSentinel v1 is not:
- a fully autonomous agent
- a multi-agent swarm platform
- a production SIEM/SOAR replacement
- a generalized workflow automation engine
- a real-time operations platform
- a full identity and access management system

## Architecture

See [`docs/architecture.md`](docs/architecture.md) for the initial system design.

## Initial Stack

- **Backend:** Python, FastAPI
- **Frontend:** Next.js, TypeScript
- **Database:** PostgreSQL
- **Containerization:** Docker Compose
- **Agent Layer:** tool-using bounded workflow
- **Observability:** structured application logs + audit events
- **Interoperability:** MCP server for controlled tool exposure

## Local Setup

Setup instructions will be added as the local development environment is finalized.

## Roadmap

- Phase 1: Repository and control plane foundation
- Phase 2: Document and structured data workflows
- Phase 3: Approval-gated action proposals
- Phase 4: Evaluation, guardrails, and hardening

## Status

Early build. Architecture and initial control-plane scaffolding in progress.

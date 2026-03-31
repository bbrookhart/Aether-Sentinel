# AetherSentinel

**Secure agentic triage and decision support for high-trust environments**

AetherSentinel is a secure, tool-using AI platform designed to help analysts review documents, query structured records, answer grounded questions, and propose controlled actions in regulated or high-risk environments. The system is intentionally built around bounded tool use, explicit approval gates, and full auditability so that useful AI assistance does not become unsafe autonomy.

## Why This Exists

Most AI demos optimize for capability before control. AetherSentinel takes the opposite approach.

This project is a controlled agentic workflow for environments where trust, traceability, and safe execution matter. It is designed to prove that AI systems can be useful without being loosely governed, opaque, or over-privileged.

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
- a polished enterprise product

## Initial Users

AetherSentinel is being designed for analyst-style workflows in high-trust environments, including:

- healthcare operations
- cybersecurity operations
- regulated enterprise workflows
- media integrity and provenance review
- critical infrastructure support functions

## Architecture

See [`docs/architecture.md`](docs/architecture.md) for the initial system design.

## Initial Stack

- **Backend:** Python, FastAPI
- **Frontend:** Next.js, TypeScript
- **Database:** PostgreSQL
- **Containerization:** Docker Compose
- **Agent Layer:** bounded tool-using workflow
- **Observability:** structured application logs and audit events
- **Interoperability:** MCP server for controlled tool exposure

## Repository Structure

```text
aethersentinel/
├── README.md
├── .gitignore
├── .env.example
├── LICENSE
├── docker-compose.yml
├── Makefile
├── docs/
│   ├── architecture.md
│   └── decision-log.md
├── app/
│   ├── backend/
│   ├── frontend/
│   └── mcp-server/
├── evals/
└── scripts/

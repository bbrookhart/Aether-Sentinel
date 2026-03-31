
---

## `docs/architecture.md`

```markdown
# AetherSentinel Architecture

## Purpose

AetherSentinel is a secure agentic triage and decision-support platform for high-trust environments. It is designed to help users review documents, query structured records, answer grounded questions, and propose controlled actions while enforcing approval gates and maintaining a complete audit trail.

## System Goals

- provide useful AI-assisted triage without unsafe autonomy
- ground responses in approved data sources
- enforce approval before write-capable actions
- preserve traceability for important decisions and tool use
- maintain a modular architecture that can expand across multiple regulated domains

## Non-Goals (v1)

AetherSentinel v1 will not attempt to provide:

- fully autonomous task execution
- broad multi-agent orchestration
- real-time streaming operations
- deep predictive analytics
- production-grade enterprise IAM
- general-purpose workflow automation
- unrestricted tool execution

## High-Level Components

### Frontend

The frontend provides the user-facing interface for:

- submitting questions
- reviewing documents
- viewing grounded answers
- inspecting proposed actions
- approving or rejecting controlled actions
- reviewing audit history

Planned implementation:
- Next.js
- TypeScript
- simple analyst-oriented UI

### Backend

The backend is the central application service responsible for:

- API routing
- authentication and authorization
- orchestration of agent workflows
- tool mediation
- persistence of approvals and audit events
- enforcement of execution boundaries

Planned implementation:
- FastAPI
- Python
- structured logging
- role-aware service layer

### Database

The database stores:

- users and roles
- document metadata
- structured records
- approvals
- audit events
- minimal state needed for bounded workflows

Planned implementation:
- PostgreSQL

### Agent Layer

The agent layer is intentionally bounded.

Responsibilities:
- interpret user requests
- choose from approved tools
- answer grounded questions
- propose actions rather than directly execute write-capable operations

Key design rule:
- agent intelligence must remain subordinate to policy and approval controls

### Tools

Initial tool surface will be narrow.

Planned v1 tools:
- document search
- structured record lookup
- controlled action proposal interface

Tool design principles:
- least privilege
- explicit schemas
- auditable usage
- no hidden writes

### Audit Trail

A persistent audit layer will record:

- user requests
- route access
- tool invocations
- important system events
- approvals and rejections
- execution outcomes

Audit requirements:
- append-friendly
- queryable
- role-aware
- useful for review and debugging

### Approvals

Any write-capable or state-changing action must pass through an approval service before execution.

Approval workflow goals:
- separate analysis from execution
- prevent silent writes
- create a human checkpoint for risky actions
- ensure review events are logged

### MCP Server

A controlled MCP server will expose selected safe tools for future interoperability.

Purpose:
- support external agent/tool integration patterns
- maintain explicit authorization boundaries
- keep tool exposure consistent with policy

This is included in the architecture early to future-proof the design, but it is not a Day 1 implementation priority.

## Initial Request Flow

### Read-Only Question Flow

1. user submits a question
2. backend authenticates the user and resolves role context
3. agent layer interprets the request
4. agent invokes one or more approved read tools
5. backend returns a grounded answer with source references
6. all material steps are recorded in the audit trail

### Proposed Action Flow

1. user submits a task that implies action
2. backend authenticates the user and resolves permissions
3. agent evaluates the task and forms a proposed action
4. proposed action is not executed directly
5. action is routed to approval review
6. reviewer approves or rejects
7. decision and resulting outcome are recorded in the audit trail

## Trust Boundaries

The system should preserve the following trust boundaries:

- users do not directly access backend tools
- agent tool use is mediated by backend policy controls
- write-capable actions require approval
- sensitive activity is logged
- access is role-aware and bounded

## Security Principles

AetherSentinel v1 will follow these principles:

- least privilege by default
- no implicit write execution
- fail closed when authorization is unclear
- audit important actions and decisions
- separate read workflows from write workflows
- keep tool exposure narrow
- prefer deterministic controls over prompt-only controls

## Initial Data Model Categories

Planned core entities:

- User
- Role
- Document
- StructuredRecord
- Approval
- AuditEvent
- ChatSession
- ProposedAction

The exact schema can evolve, but these categories define the initial architecture boundary.

## Initial Deployment Model

Planned local development model:

- frontend container
- backend container
- postgres container
- optional local MCP service

Production hosting is out of scope for Day 1.

## Open Questions

- how much workflow state is actually needed in v1?
- should retrieval remain keyword-based initially or include embeddings early?
- what approval schema is sufficient for v1 without overengineering?
- how much structured memory should the agent retain across sessions?
- what is the minimum viable audit schema that still supports review?

## Summary

AetherSentinel is being built as a controlled agentic system with safe defaults. The architecture prioritizes governed execution, traceability, and bounded tool use before sophistication or scale.

**AetherSentinel v1 is a governed assistant, not an autonomous operator.**

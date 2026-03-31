# Decision Log

This file records important build decisions, their rationale, and what is intentionally deferred.

---

## 2026-03-31

### Decision: Project name

Selected **AetherSentinel** as the flagship repo name.

### Reasoning

- aligns with the broader AetherHorizon brand
- signals oversight, monitoring, and defense
- sounds credible across healthcare, cybersecurity, media integrity, and other high-trust domains
- remains broad enough to support future expansion beyond narrow triage workflows

---

### Decision: Project positioning

AetherSentinel is positioned as a **secure agentic triage and decision-support platform for high-trust environments**.

### Reasoning

This positioning emphasizes:
- secure system design
- agentic workflows
- practical analyst support
- controlled execution
- relevance in regulated or high-risk settings

It avoids overclaiming autonomy or pretending the system is already a broad enterprise platform.

---

### Decision: v1 scope

AetherSentinel v1 is limited to:

- reading documents
- reading structured records
- answering grounded questions
- proposing actions
- requiring approval before write-capable actions
- logging important system and workflow events

### Reasoning

The first version should prove control, observability, and safe tool use before expanding into more advanced workflows.

---

### Decision: non-goals for v1

Deferred the following:

- autonomous execution
- multi-agent orchestration
- advanced long-term memory
- real-time event streaming
- production-grade IAM
- polished enterprise dashboarding
- broad third-party integrations
- deep predictive analytics

### Reasoning

These items increase complexity and risk without being required to prove the core concept.

---

### Decision: initial stack

Selected the following initial stack:

- **Backend:** Python + FastAPI
- **Frontend:** Next.js + TypeScript
- **Database:** PostgreSQL
- **Local environment:** Docker Compose
- **Interoperability direction:** MCP server
- **Observability direction:** structured logs + audit events

### Reasoning

This stack is practical, modern, and well aligned with building a tool-using, auditable agent system that can grow over time.

---

### Decision: architecture priority

The project will prioritize the control plane before advanced intelligence features.

### Reasoning

The system needs:
- clear execution boundaries
- a usable audit trail
- approval gating
- stable data access patterns

before it needs sophistication in agent behavior.

---

### Decision: guiding principle

Adopted the following rule:

**AetherSentinel v1 is a governed assistant, not an autonomous operator.**

### Reasoning

This principle should constrain feature creep and help evaluate future design decisions.

---

## Open Issues

- final auth approach for local development
- document ingestion format for v1
- retrieval method for early versions
- minimum approval schema
- initial audit event schema

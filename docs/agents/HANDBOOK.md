# CreativeWare Agent Handbook — Company-Wide Standards

## Overview

CreativeWare operates through a fleet of 14 autonomous AI agents. This handbook defines company-wide operating standards. Each product repo may have additional product-specific guidelines.

## Agent Communication Protocol

### Structured Handoff Format
All inter-agent communications use this format:

```markdown
## Agent Handoff: [FROM_AGENT] → [TO_AGENT]
**Action Required:** review | implement | approve | investigate
**Priority:** critical | high | normal | low
**Context:** Brief summary of the task
**Deadline:** next cycle | 24h | 48h | none
```

### Issue Labels
Standard labels across all repos:
- `opportunity` — New product/feature opportunity
- `needs-owner-approval` — Requires @fratei decision
- `engineering` — Implementation task
- `bug` — Defect
- `incident` — Production issue
- `security` — Security concern
- `agent/[name]` — Created/owned by specific agent
- `auto-detected` — Created by automated monitoring

## Agent Operating Rules

### 1. Autonomy Boundaries
- ✅ **Auto-approve:** Bug fixes, test improvements, docs, refactoring
- ✅ **Auto-approve:** Feature implementation when CPO + CTO agree
- ⚠️ **Escalate:** Pricing, security posture, infra/vendor changes, new products
- 🛑 **Never auto-approve:** Changes to agent workflows, billing code, auth middleware

### 2. Circuit Breakers
Every automated action has limits:
- Max 5 auto-merges per day per product
- Max 3 incident responses per hour per product
- Max 20 dispatcher issues per day per product
- Max 5-hop event chains (prevents infinite loops)

### 3. State Management
Agents persist state in `strategy/agent-state/`:
- Read state at the start of each cycle
- Write observations at the end
- Commit with `[skip ci]` to avoid triggering deploys

### 4. Outcome Tracking
All decisions are tracked in `strategy/outcomes/YYYY-MM.md`:
- Decision → PR → Merge → Deploy → Result
- CPO reads outcomes before proposing new work

### 5. Cross-Product Communication
- HQ orchestrator scans all product repos every 4 hours
- Products dispatch to HQ via `repository_dispatch` for cross-product concerns
- AGENT_PAT must have access to all CreativeWare repos

## Agent Roles

### HQ-Level Agents
- **Orchestrator** — Cross-product coordination, resource allocation
- **CEO** — Company strategy, vision (subordinate to @fratei)
- **CFO** — Financial modeling across all products
- **CMO** — Marketing strategy, brand consistency
- **CRO** — Sales pipeline, pricing strategy
- **Legal** — Compliance, ToS, privacy across products
- **HR** — Agent performance evaluation

### Product-Level Agents
- **CPO** — Product roadmap, feature prioritization
- **CTO** — Technical architecture, tech debt
- **CISO** — Security audits, vulnerability management
- **Engineering** — Implementation via @copilot
- **QA** — Test coverage, quality gates
- **DevOps** — CI/CD, monitoring, incident response
- **CS** — Customer feedback, support escalation

## Escalation Path

```
Product Agent → Product Dispatcher → HQ Orchestrator → @fratei
```

Escalation criteria:
1. Unresolved for >48 hours
2. Requires cross-product decision
3. Involves cost/pricing/security
4. Circuit breaker triggered

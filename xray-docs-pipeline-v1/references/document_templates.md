# Document Templates

Templates for every document type in the pipeline.
Read during Phase 2–5 when generating a specific document.

Each template defines: structure, required sections, field formats, and inline instructions.

---

## Table of Contents

1. [vision-framing](#vision-framing)
2. [mrd-lite](#mrd-lite)
3. [prfaq-lite](#prfaq-lite)
4. [business-case](#business-case)
5. [brd-lite](#brd-lite)
6. [prd-lite](#prd-lite)
7. [frd-lite](#frd-lite)
8. [nfr-onepager](#nfr-onepager)
9. [adr-decision-log](#adr-decision-log)
10. [roadmap](#roadmap)
11. [user-stories](#user-stories)
12. [backlog](#backlog)
13. [release-plan](#release-plan)
14. [sop](#sop)
15. [runbook](#runbook)
16. [data-integration-spec](#data-integration-spec)

---

## vision-framing

```
# Vision Framing
Version: 0.1 | Owner: [name] | Last updated: [date]

## Problem Statement
[One paragraph. What is broken, for whom, and why it matters now.]
[FATO/INFERÊNCIA/HIPÓTESE]

## Vision Statement
In [timeframe], [company/product] will [outcome] for [beneficiary],
such that [measurable impact].

## Primary Beneficiary
- Who: [persona name and description]
- Their current situation: [context]
- What changes for them: [transformation]

## Success Conditions
| Condition | How we measure | Target |
|-----------|---------------|--------|
| [condition 1] | [metric] | [value] |
| [condition 2] | [metric] | [value] |

## Out of Scope
[Explicit list of what this vision does NOT cover]

## Open Questions
| Question | Owner | Due |
|----------|-------|-----|
```

---

## mrd-lite

```
# Market Requirements Document (lite)
Version: 0.1 | Owner: [name] | Last updated: [date]

## Market Context
[2-3 sentences on why this market matters now]
[FATO/INFERÊNCIA]

## Addressable Market
- TAM: [Total Addressable Market] [FATO/HIPÓTESE] — Source: [source]
- SAM: [Serviceable Addressable Market] [INFERÊNCIA]
- SOM: [Serviceable Obtainable Market — year 1] [HIPÓTESE]

## Ideal Customer Profile (ICP)
- Segment: [description]
- Company size / context: [if B2B]
- Qualifying attributes:
  1. [attribute 1]
  2. [attribute 2]
  3. [attribute 3]
- Disqualifying attributes:
  1. [attribute 1]

## Pain Points
| # | Pain | Intensity (1–5) | Evidence | Label |
|---|------|----------------|----------|-------|
| 1 | [pain] | [score] | [source] | [FATO/INFERÊNCIA/HIPÓTESE] |
| 2 | [pain] | [score] | [source] | [label] |
| 3 | [pain] | [score] | [source] | [label] |

## Competitive Landscape
| Competitor | Approach | Weakness | Our differentiation |
|------------|----------|----------|-------------------|
| [name] | [how they solve it] | [gap] | [our angle] |

## Market Signals
[Trends, regulatory shifts, technology enablers supporting market timing]
[FATO/INFERÊNCIA]

## Gaps and Unknowns
[What we still need to validate before committing]
```

---

## prfaq-lite

```
# PR/FAQ (lite)
Version: 0.1 | Owner: [name] | Last updated: [date]

---

## PRESS RELEASE

**[City, Date]** — [Company] today announced [product/feature], enabling [target customer]
to [core value proposition] without [key friction/cost removed].

[Paragraph 2: problem context — why this matters now]

[Paragraph 3: how it works at a high level — no jargon]

"[Customer quote — how their life/work changed]" — [Fictional customer name, role] [HIPÓTESE]

[Paragraph 4: call to action or availability]

---

## FAQ

**Q: Who is this for?**
A: [answer]

**Q: What problem does it solve?**
A: [answer]

**Q: How is this different from [main alternative]?**
A: [answer]

**Q: What does it cost / how do I get access?**
A: [answer]

**Q: What does it NOT do?**
A: [answer]

**Q: What are the key risks or limitations?**
A: [answer]

**Q: What needs to be true for this to succeed?**
A: [answer — list key assumptions, label each FATO/HIPÓTESE]
```

---

## business-case

```
# Business Case
Version: 0.1 | Owner: [name] | Last updated: [date]

## Executive Summary
[3 sentences: what we're building, why now, and the financial upside]

## Revenue Model
| Stream | Mechanism | Year 1 | Year 2 | Year 3 | Label |
|--------|-----------|--------|--------|--------|-------|
| [stream 1] | [how it works] | [R$] | [R$] | [R$] | [FATO/HIPÓTESE] |

## Cost Structure
| Category | Description | Monthly | Annual | Label |
|----------|-------------|---------|--------|-------|
| [category] | [description] | [R$] | [R$] | [label] |

## Unit Economics
- CAC (Customer Acquisition Cost): [value] [HIPÓTESE]
- LTV (Lifetime Value): [value] [HIPÓTESE]
- LTV/CAC ratio: [value]
- Payback period: [months]

## Break-Even Analysis
- Fixed costs/month: [R$]
- Variable cost/unit: [R$]
- Price/unit: [R$]
- Break-even units: [N]
- Break-even timeline: [months] [HIPÓTESE]

## Scenarios
| Scenario | Assumption | Revenue Y1 | Profit Y1 |
|----------|------------|-----------|-----------|
| Conservative | [key assumption] | [R$] | [R$] |
| Base | [key assumption] | [R$] | [R$] |
| Optimistic | [key assumption] | [R$] | [R$] |

## Key Risks
| Risk | Probability | Impact | Mitigation |
|------|-------------|--------|-----------|

## Funding / Investment Required
- Total required: [R$] [HIPÓTESE]
- Use of funds: [breakdown]
- Expected ROI: [%] in [timeframe]
```

---

## brd-lite

```
# Business Requirements Document (lite)
Version: 0.1 | Owner: [name] | Last updated: [date]
External stakeholder: [name / organization]

## Context
[Why this document exists — what contract, partnership, or compliance event requires it]

## Stakeholder Requirements
| ID | Requirement | Source | Priority | Acceptance Criteria |
|----|-------------|--------|----------|-------------------|
| BR-001 | [requirement] | [contract/clause] | [Must/Should/Could] | [how we prove it] |

## Constraints
- Budget constraints: [description]
- Timeline constraints: [description]
- Technical constraints: [description]
- Regulatory / legal: [description]

## Capability Mapping
| BR ID | Product Capability | PRD Reference | Status |
|-------|-------------------|---------------|--------|

## Sign-off Requirements
| Stakeholder | Role | Approval needed for | Date |
|-------------|------|-------------------|------|
```

---

## prd-lite

```
# Product Requirements Document (lite)
Version: 0.1 | Owner: [name] | Last updated: [date]

## Purpose
[One sentence: what this product does and for whom]

## Personas
### Persona 1: [Name]
- Role / context: [description]
- Job to be done: [what they're trying to accomplish]
- Frustration with current solution: [pain]
- Success looks like: [outcome]

### Persona 2: [Name]
[same structure]

## Use Cases
| ID | Use Case | Persona | Trigger | Expected Outcome | Priority |
|----|----------|---------|---------|-----------------|----------|
| UC-001 | [description] | [persona] | [what triggers this] | [outcome] | Must |

## Functional Requirements Summary
[High-level behaviors, not implementation. Detailed rules go in FRD-lite.]

## Out of Scope (explicitly)
- [item 1]
- [item 2]

## Success Metrics
| Metric | Baseline | Target | Timeframe | Label |
|--------|----------|--------|-----------|-------|
| [metric] | [current] | [goal] | [when] | [FATO/HIPÓTESE] |

## Assumptions
[List assumptions the product is built on, each labeled HIPÓTESE unless confirmed]

## Open Questions
| Question | Owner | Due | Blocks |
|----------|-------|-----|--------|
```

---

## frd-lite

```
# Functional Requirements Document (lite)
Version: 0.1 | Owner: [name] | Last updated: [date]
Linked PRD: [version + date]

## Scope
[Which PRD use cases require functional rules documentation]

## Business Rules
| ID | Rule | Trigger | Condition | Action | Exception | PRD Ref |
|----|------|---------|-----------|--------|-----------|---------|
| FR-001 | [rule name] | [event] | [if/when] | [then] | [unless] | UC-001 |

## Automation Flows
### Flow 1: [Name]
- Trigger: [event]
- Steps:
  1. [step]
  2. [step]
- Success exit: [state]
- Failure exit: [state + handler]

## Data Validation Rules
| Field | Type | Validation | Error Message |
|-------|------|-----------|---------------|

## State Machines
[If any entity has meaningful state transitions, document them here]
State: [A] → [B] when [condition], unless [exception]
```

---

## nfr-onepager

```
# Non-Functional Requirements (one-pager)
Version: 0.1 | Owner: [name] | Last updated: [date]

## Performance
- Response time: [target, e.g., p95 < 500ms under N concurrent users]
- Throughput: [requests/sec or transactions/hour]
- Data volume: [expected records/day]

## Availability & Reliability
- Uptime SLA: [%, e.g., 99.5% monthly]
- Recovery Time Objective (RTO): [hours/minutes]
- Recovery Point Objective (RPO): [hours/minutes]
- Planned maintenance window: [when]

## Security
- Authentication: [mechanism]
- Authorization: [model, e.g., RBAC]
- Data encryption: at rest [yes/no], in transit [yes/no]
- Sensitive data handling: [description]

## Compliance
- LGPD applicability: [yes/no + basis]
- Personal data fields: [list]
- Retention policy: [duration]
- Right to deletion: [procedure]
- GDPR (if applicable): [yes/no]

## Scalability
- Expected growth: [N users/month]
- Scaling strategy: [horizontal/vertical/auto]
- Bottleneck assumptions: [where scale breaks first] [HIPÓTESE]

## Integrations
| System | Direction | Protocol | SLA | Failure Handling |
|--------|-----------|----------|-----|-----------------|
```

---

## adr-decision-log

```
# Architecture Decision Records
Version: 0.1 | Owner: [name] | Last updated: [date]

---

## ADR-001: [Decision Title]
**Date**: [date]
**Status**: proposed | accepted | deprecated | superseded by ADR-[N]
**Triggered by**: [document + section that required this decision]

### Context
[Why this decision needed to be made. What forces are at play.]

### Decision
[What we decided, stated clearly.]

### Options Considered
| Option | Pros | Cons |
|--------|------|------|
| [A] | [pros] | [cons] |
| [B] | [pros] | [cons] |

### Consequences
- Positive: [what becomes easier]
- Negative: [what becomes harder or constrained]
- Risks: [what could go wrong]

---
[Repeat ADR block for each decision]
```

---

## roadmap

```
# Product Roadmap
Version: 0.1 | Owner: [name] | Last updated: [date]
Linked PRD: [version + date]

## Roadmap Philosophy
[One sentence on the sequencing logic — e.g., "Validate retention before acquisition"]

## Now (current cycle / Q[N])
| Item | Outcome | PRD Ref | Effort | Status |
|------|---------|---------|--------|--------|
| [item] | [what changes] | UC-00N | [S/M/L] | [in progress / planned] |

## Next (next cycle / Q[N+1])
| Item | Outcome | PRD Ref | Effort | Depends on |
|------|---------|---------|--------|------------|

## Later (Q[N+2] and beyond)
| Item | Outcome | Rationale | Label |
|------|---------|-----------|-------|
| [item] | [outcome] | [why later] | [HIPÓTESE — may change] |

## Explicitly Not Doing (and why)
| Item | Reason |
|------|--------|
```

---

## user-stories

```
# User Stories
Version: 0.1 | Owner: [name] | Last updated: [date]
Linked PRD: [version] | Linked FRD: [version or N/A]

## Epic: [Epic Name]
Linked to: UC-00N

### Story [EPIC]-001: [Story Title]
**As a** [persona],
**I want** [action/capability],
**so that** [outcome/value].

**Acceptance Criteria:**
- [ ] [criterion 1]
- [ ] [criterion 2]
- [ ] [criterion 3]

**Notes / Edge Cases:**
[anything that affects implementation scope]

---
[Repeat for each story]
```

---

## backlog

```
# Product Backlog
Version: 0.1 | Owner: [name] | Last updated: [date]
Priority method: MoSCoW | Roadmap cycle: [Now/Next/Later]

| ID | Title | Type | Priority | Effort | Story Ref | Definition of Done |
|----|-------|------|----------|--------|-----------|-------------------|
| BL-001 | [title] | Feature/Bug/Chore | Must | S | [story ID] | [done criteria] |

## Definition of Done (global)
- Code reviewed and merged
- Unit tests passing
- Acceptance criteria verified by PO
- No blocking bugs introduced

## Prioritization Notes
[Explain key tradeoffs or sequencing decisions]
```

---

## release-plan

```
# Release Plan
Version: 0.1 | Owner: [name] | Last updated: [date]

## Release Cadence
[e.g., bi-weekly sprints, monthly releases, continuous deployment]

## Release 1.0 — [Name]
- **Target date**: [date]
- **Scope**: [backlog IDs included]
- **Go/No-go criteria**:
  - [ ] [criterion 1]
  - [ ] [criterion 2]
- **Rollback plan**: [how to revert if critical issue found]
- **Communication**: [who gets notified, how]

---
[Repeat for each planned release]
```

---

## sop

```
# Standard Operating Procedure: [Process Name]
Version: 0.1 | Owner: [name] | Last updated: [date]
Frequency: [daily/weekly/on-demand] | Estimated duration: [time]

## Purpose
[One sentence: what this procedure achieves and why it exists]

## Scope
- Applies to: [who performs this]
- Does not apply to: [explicit exclusions]

## Prerequisites
- Access required: [systems, credentials]
- Tools required: [list]
- Prior steps: [what must be done before starting]

## Procedure

### Step 1: [Step Name]
- **Actor**: [role]
- **Action**: [what to do, precisely]
- **System/Tool**: [where to do it]
- **Expected output**: [what success looks like]
- **If error**: [what to do if it fails]

### Step 2: [Step Name]
[same structure]

## Exception Handling
| Scenario | Signal | Response |
|----------|--------|----------|

## Review & Maintenance
- Review frequency: [e.g., quarterly]
- Owner responsible for updates: [name/role]
- Change log: [link or inline]
```

---

## runbook

```
# Runbook: [System/Automation Name]
Version: 0.1 | Owner: [name] | Last updated: [date]
Severity levels: P1 (down) | P2 (degraded) | P3 (minor)

## System Overview
[One paragraph on what this system does and its dependencies]

## Monitoring & Alerts
| Alert | What it means | Threshold | Dashboard link |
|-------|--------------|-----------|----------------|

## Failure Modes & Recovery

### Failure: [Name]
- **Detection signal**: [what indicates this failure]
- **Severity**: [P1/P2/P3]
- **Impact**: [what breaks for users]
- **Recovery steps**:
  1. [step]
  2. [step]
- **Escalation if unresolved in [N min]**: [who to contact, how]
- **Disable/rollback procedure**: [how to turn it off safely]

---
[Repeat for each known failure mode]

## Escalation Matrix
| Level | Condition | Contact | Method | SLA |
|-------|-----------|---------|--------|-----|
| L1 | [condition] | [who] | [slack/phone] | [response time] |

## Post-Incident Template
- Date/time:
- Duration:
- Root cause:
- Resolution:
- Prevention:
```

---

## data-integration-spec

```
# Data Integration Specification
Version: 0.1 | Owner: [name] | Last updated: [date]
Linked PRD: [version]

## Integration Overview
| Integration | Source | Target | Direction | Frequency | Protocol |
|-------------|--------|--------|-----------|-----------|----------|
| [name] | [system] | [system] | push/pull/sync | [freq] | REST/webhook/batch |

## Field Mapping: [Integration Name]

### Source: [system name]
### Target: [system name]

| Source Field | Source Type | Target Field | Target Type | Transformation | PII? |
|-------------|------------|-------------|------------|----------------|------|
| [field] | [type] | [field] | [type] | [rule or "direct"] | [yes/no] |

## Error Handling
| Error Type | Detection | Response | Retry Policy | Alert |
|-----------|-----------|----------|-------------|-------|
| [type] | [how detected] | [action] | [N retries, backoff] | [who/how] |

## Data Ownership & Retention
| Data Type | Owner | Retention Period | Deletion Procedure |
|-----------|-------|-----------------|-------------------|

## PII Treatment
| Field | LGPD Basis | Retention | Deletion on Request |
|-------|-----------|-----------|-------------------|

## Testing & Validation
- Integration test procedure: [description]
- Validation queries: [list of checks to run after setup]
- Rollback procedure: [how to disconnect safely]
```

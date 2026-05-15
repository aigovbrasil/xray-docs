# Document Graph — Dependency Rules

This file defines the dependency graph for all document types in the pipeline.
Read during Phase 1 to build and validate the Document Graph.

---

## Table of Contents

1. [Discovery Layer](#discovery-layer)
2. [Product Layer](#product-layer)
3. [Execution Layer](#execution-layer)
4. [Operations Layer](#operations-layer)
5. [Acceptance Criteria](#acceptance-criteria)

---

## Discovery Layer

### vision-framing
- **required_inputs**: business_objective, founding_hypothesis, target_market
- **upstream_dependencies**: Context Pack (approved)
- **optional**: yes — only in full-corpus profile
- **acceptance_criteria**:
  - Contains a clear problem statement
  - Defines a measurable success condition
  - Names the primary beneficiary (user/customer)
  - Does not contain implementation details

### mrd-lite (Market Requirements Document)
- **required_inputs**: market_segment, pain_points[], ICP_description, competitive_signals
- **upstream_dependencies**: Context Pack (approved); Agent 1 output if market-research profile
- **acceptance_criteria**:
  - Market size estimated with source labeled [FATO] or [INFERÊNCIA]
  - At least 3 distinct pain points identified
  - ICP defined with at least 2 qualifying attributes
  - No product features mentioned — market only
  - All claims epistemically labeled

### prfaq-lite (Press Release / FAQ)
- **required_inputs**: target_customer, core_value_proposition, key_problem
- **upstream_dependencies**: Context Pack (approved)
- **acceptance_criteria**:
  - Written in future-press-release format (product already launched)
  - Contains a customer quote (may be [HIPÓTESE])
  - FAQ section has at least 5 questions
  - No technical implementation details
  - Reviewable in under 3 minutes

### business-case
- **required_inputs**: revenue_model, cost_assumptions, addressable_market
- **upstream_dependencies**: MRD-lite OR PRFAQ-lite (at least one approved)
- **acceptance_criteria**:
  - Contains 3-year projection with labeled assumptions
  - Identifies 2+ revenue streams or pricing scenarios
  - Includes break-even estimate
  - All financial figures labeled [FATO] or [HIPÓTESE]

### brd-lite (Business Requirements Document)
- **required_inputs**: external_stakeholder_name, contract_requirements, compliance_constraints
- **upstream_dependencies**: Business Case (approved)
- **when_to_include**: only if external stakeholder (client, partner, investor) exists
- **acceptance_criteria**:
  - Lists contractual obligations explicitly
  - Maps each requirement to a product capability
  - Defines acceptance criteria for each requirement
  - Signed-off format ready for external review

---

## Product Layer

### prd-lite (Product Requirements Document)
- **required_inputs**: user_personas[], core_use_cases[], success_metrics[]
- **upstream_dependencies**: PRFAQ-lite OR MRD-lite (approved); BRD-lite if commercial layer
- **acceptance_criteria**:
  - Contains at least 2 user personas with jobs-to-be-done
  - Each use case has a measurable outcome
  - Out-of-scope section explicitly defined
  - No wireframes or UI specs — behavior only
  - Version number and owner field populated

### frd-lite (Functional Requirements Document)
- **required_inputs**: business_rules[], automation_triggers[], edge_cases[]
- **upstream_dependencies**: PRD-lite (approved)
- **when_to_include**: only if complex rules, automations, or conditional flows exist
- **acceptance_criteria**:
  - Each rule has a unique ID (FR-001, FR-002...)
  - Each rule has: trigger, condition, action, exception
  - All rules traceable back to a PRD use case
  - No implementation technology specified

### nfr-onepager (Non-Functional Requirements)
- **required_inputs**: performance_sla, data_sensitivity_level, integration_count
- **upstream_dependencies**: PRD-lite (approved)
- **when_to_include**: integrations > 0, or SLA obligations, or LGPD/GDPR risk
- **acceptance_criteria**:
  - Covers: performance, security, availability, scalability, compliance
  - Each NFR has a measurable target (e.g., p95 < 500ms)
  - LGPD/GDPR obligations mapped if personal data involved
  - One page maximum

### adr-decision-log (Architecture Decision Records)
- **required_inputs**: decision_description, options_considered[], rationale
- **upstream_dependencies**: any approved document that triggers an irreversible decision
- **acceptance_criteria**:
  - Each ADR has: context, decision, consequences
  - Status field: proposed | accepted | deprecated | superseded
  - Linked to the document that triggered the decision

---

## Execution Layer

### roadmap
- **required_inputs**: priorities[], estimated_effort[], target_milestones[]
- **upstream_dependencies**: PRD-lite (approved) + business priorities confirmed
- **acceptance_criteria**:
  - Organized in phases (Now / Next / Later or Q1/Q2/Q3)
  - Each item linked to a PRD use case or business objective
  - Effort labeled as [FATO] (estimated by team) or [HIPÓTESE]
  - Does not contain implementation tasks — outcome-level only

### user-stories
- **required_inputs**: personas[], use_cases[], acceptance_criteria_per_story[]
- **upstream_dependencies**: PRD-lite (approved); FRD-lite if hard rules apply
- **acceptance_criteria**:
  - Format: "As a [persona], I want [action] so that [outcome]"
  - Each story has at least 2 acceptance criteria
  - Stories are independently testable
  - No story references implementation technology

### backlog
- **required_inputs**: user_stories[] (approved), priority_method
- **upstream_dependencies**: User Stories (approved)
- **acceptance_criteria**:
  - Items prioritized (MoSCoW or RICE or similar)
  - Each item has effort estimate
  - Definition of Done attached to each item
  - Linked to roadmap phase

### release-plan
- **required_inputs**: backlog (approved), release_cadence, deployment_constraints
- **upstream_dependencies**: Backlog (approved)
- **when_to_include**: optional — only if explicit release sequencing needed
- **acceptance_criteria**:
  - Each release has a clear scope boundary
  - Go/No-go criteria defined per release
  - Rollback path described

---

## Operations Layer

### sop (Standard Operating Procedure)
- **required_inputs**: process_owner, process_steps[], inputs_outputs[], frequency
- **upstream_dependencies**: tested process (minimum 2–3 real repetitions)
- **acceptance_criteria**:
  - Written so a new team member can execute without help
  - Each step has: actor, action, tool/system, expected output
  - Exception handling documented
  - Version and review date fields populated

### runbook
- **required_inputs**: system_name, known_failure_modes[], escalation_path[]
- **upstream_dependencies**: running automations with known failure points
- **acceptance_criteria**:
  - Each failure mode has a detection signal + recovery procedure
  - Escalation matrix defined (who, when, how)
  - Runbook survives a 3am incident — no ambiguity allowed
  - Includes rollback or disable procedure for each automation

### data-integration-spec
- **required_inputs**: source_systems[], target_systems[], field_mapping[], sync_frequency
- **upstream_dependencies**: PRD-lite (approved), at least one confirmed integration
- **acceptance_criteria**:
  - Every field mapped with source name, target name, transformation rule
  - Error handling defined for each integration
  - Data ownership and retention policy included
  - PII fields flagged and LGPD treatment documented

---

## Acceptance Criteria

### Global rules (apply to ALL documents)

1. **Epistemic completeness**: Every significant claim must be labeled [FATO], [INFERÊNCIA], or [HIPÓTESE]
2. **Traceability**: Each document must reference the upstream source it depends on
3. **No scope creep**: Each document type stays within its defined scope boundary
4. **Human-readable**: A non-technical stakeholder must be able to understand the document's purpose in 30 seconds
5. **Version field**: Every document must have a version number and last-updated date

### Propagation rules

- `[FATO]` in upstream → may propagate as `[FATO]` downstream if unchanged
- `[INFERÊNCIA]` in upstream → propagates as `[INFERÊNCIA]` downstream
- `[HIPÓTESE]` in upstream → **must** propagate as `[HIPÓTESE]` downstream with explicit flag
- Any synthesis of multiple sources → labeled `[INFERÊNCIA]` minimum

### Blocking conditions

A document is **blocked** when:
- Any required_input is missing
- Any upstream dependency is not in `approved` state
- The document has failed validation 3+ times on the same criterion

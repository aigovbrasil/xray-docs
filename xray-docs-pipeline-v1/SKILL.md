# X-RAY SUITE · xray-docs-pipeline-v1

---
name: business-docx-pipeline
description: |
  Transforms raw business context (brief, research, idea, notes) into a canonical document corpus
  with dependency validation, epistemic traceability, and human approval gates.

  Trigger this skill whenever the user wants to:
  - turn a raw document, brief or idea into structured business documents
  - generate MRD, BRD, PRD, SOP, Runbook, Roadmap, Backlog or any combination
  - build a complete workbook/playbook from scratch
  - produce a financial spreadsheet, Linear prompt or full folder structure
  - run market research + document pipeline end-to-end
  - audit, refine or extend an existing document corpus

  Also trigger when user says: "cria documentação", "monta o playbook", "gera o corpus",
  "preciso do PRD", "pipeline documental", "transforma esse briefing em docs",
  "estrutura esse projeto", "gera o workbook", "cria a skill de documentos".
---

# Business Document Production Pipeline

A dependency-aware document production engine that converts raw context into a canonical,
auditable corpus. Each document only generates when its upstream dependencies are validated
and approved. Human gates prevent downstream propagation of bad premises.

## Core concept

This skill operates as a **document graph executor**, not a prompt chain.
Each node in the graph is a document with: required inputs, upstream dependencies,
acceptance criteria, epistemic requirements, and a state.

The skill never fills gaps with creativity. It signals gaps and blocks until resolved.

---

## How to start

User provides one of:
- raw text (brief, notes, research, idea dump)
- uploaded file
- structured input via intake questions

The skill responds with a **Context Pack** and proposed **Document Graph** for approval
before generating anything.

---

## Workflow profiles

Read `assets/workflow_profiles.json` to select the appropriate profile.

| Profile | Trigger signal | Chain starts at |
|---|---|---|
| `market-research` | "pesquisa", "mercado", "ICP", "segmento" | Agent 1 → MRD-lite |
| `product` | "produto", "construir", "MVP", "PRD" | PRFAQ-lite → PRD-lite |
| `go-to-market` | "lançar", "campanha", "proposta", "venda" | PRFAQ-lite → BRD-lite |
| `operations` | "processo", "SOP", "operação", "runbook" | Context Pack → SOP |
| `full-corpus` | "corpus completo", "workbook", "playbook" | Agent 1 → full chain |

When the profile is ambiguous, ask one question: "Qual é o objetivo principal — mercado, produto, operação ou proposta comercial?"

---

## Execution phases

### Phase 0 — Intake & Context Pack

Run Agent 1 (market research) if profile is `market-research` or `full-corpus`.
Otherwise, normalize input directly.

Output: **Context Pack** with fields:
- `business_objective`
- `project_type`
- `scope`
- `hypotheses[]` — each labeled as `FATO | INFERÊNCIA | HIPÓTESE`
- `available_data[]`
- `sources[]`
- `gaps[]`
- `requested_deliverables[]`

**Gate 0**: Show Context Pack. Ask user to confirm or correct before proceeding.
Do not proceed without explicit confirmation.

→ See `references/agents.md` for Agent 1 system prompt

---

### Phase 1 — Document Graph Planning

Read `references/document_graph.md` for dependency rules.

Based on the confirmed Context Pack and selected profile, generate the **Document Graph**:
- list of documents in dependency order
- for each: `status`, `required_inputs`, `upstream_dependencies`, `acceptance_criteria`

**Gate 1**: Present the graph as a simple numbered list with dependencies visible.
Ask: "Confirma esse grafo ou quer remover/adicionar algum documento?"

Do not generate any document before Gate 1 is approved.

---

### Phase 2 — Discovery layer

Generate in order (only documents that exist in the approved graph):

1. `vision-framing` (if full-corpus)
2. `mrd-lite` — depends on: Context Pack + research data
3. `prfaq-lite` — depends on: Context Pack (no deep evidence needed)
4. `business-case` — depends on: MRD-lite or PRFAQ-lite
5. `brd-lite` — depends on: Business Case (only if external stakeholder exists)

For each document:
1. Check all `required_inputs` are present
2. If missing → emit **Gap Report** (see Gap Report format below), block generation
3. If present → generate document using template from `references/document_templates.md`
4. Self-validate against `acceptance_criteria` from `references/document_graph.md`
5. Label all claims: `[FATO]` / `[INFERÊNCIA]` / `[HIPÓTESE]`

**Gate 2**: Present Discovery layer outputs. Ask for approval before Phase 3.
Lock approved documents as canonical source for downstream.

---

### Phase 3 — Product layer

Generate in order (only if in approved graph):

1. `prd-lite` — depends on: PRFAQ-lite or MRD-lite; BRD-lite if commercial layer exists
2. `frd-lite` — depends on: PRD-lite (only if automations or complex rules exist)
3. `nfr-onepager` — depends on: PRD-lite (only if integrations, SLA, LGPD risk)
4. `adr-decision-log` — depends on: context of irreversible decisions

**Gate 3**: Present Product layer. Approval required before Phase 4.

---

### Phase 4 — Execution layer

Generate in order:

1. `roadmap` — depends on: PRD-lite + business priorities
2. `user-stories` — depends on: PRD-lite; FRD-lite if hard rules exist
3. `backlog` — depends on: User Stories
4. `release-plan` — depends on: Backlog (optional)

**Gate 4**: Present Execution layer. Approval required before Phase 5.

---

### Phase 5 — Operations layer + Output packaging

Generate:

1. `sop` — depends on: tested process (at least 2–3 repetitions)
2. `runbook` — depends on: running automations and known failure points
3. `data-integration-spec` — depends on: PRD-lite (when APIs, CRM, webhooks exist)

After all gates approved → run Agent 2 for digital ops audit (optional).

**Final output**: trigger `scripts/build_corpus.py` to generate:
- Workbook `.docx` (all approved documents, executive design)
- Folder structure `.zip` (organized by phase)
- `scripts/build_spreadsheet.py` for financial `.xlsx`
- Linear integration prompt from `references/linear_prompt.md`

→ See `references/agents.md` for Agent 2 system prompt

---

## Gap Report format

When inputs are insufficient, emit this block and stop generation:

```
GAP REPORT — [document_type]
Status: BLOCKED
Missing: [what is missing]
Why it matters: [impact on this document]
Unlock options:
  A) [question that unblocks]
  B) [alternative: proceed with provisional hypothesis — label all claims HIPÓTESE]
Decision required from user before proceeding.
```

Never generate a document to fill a gap. Provisional hypotheses are allowed only
when the user explicitly chooses option B and the document labels all claims accordingly.

---

## Epistemic policy

Every significant claim in every document must carry one label:

| Label | Meaning |
|---|---|
| `[FATO]` | Directly provided by user or verified source |
| `[INFERÊNCIA]` | Strong interpretation from credible indirect signals |
| `[HIPÓTESE]` | Plausible but unvalidated — requires field confirmation |

Claims labeled `[HIPÓTESE]` must not propagate to downstream documents as confirmed facts.
They propagate only as `[HIPÓTESE]` with an explicit flag.

→ See `references/evidence_policy.md` for full policy

---

## Document states

Each document in the graph has one of these states at all times:

`not_planned` → `planned` → `blocked_missing_inputs` → `ready_to_generate`
→ `generated_pending_validation` → `failed_validation` → `pending_human_review`
→ `approved` → `archived_superseded`

When a document fails validation, it returns to `ready_to_generate` after correction.
When a document is superseded by a new version, it moves to `archived_superseded`.

→ See `assets/document_states.json` for state machine

---

## Stopping rules

The skill stops and requests input when:
- A required upstream document is not yet approved
- A Gap Report is emitted and no option is chosen
- More than 2 failed validations on the same document
- User explicitly requests halt

The skill does NOT:
- Invent data to fill gaps
- Proceed past a gate without explicit approval
- Generate downstream documents from unapproved sources
- Re-use draft versions as canonical sources

---

## Reference files

| File | When to read |
|---|---|
| `references/document_graph.md` | Phase 1 — building the graph |
| `references/document_templates.md` | Phase 2–5 — generating each document |
| `references/agents.md` | Phase 0 (Agent 1) and Phase 5 (Agent 2) |
| `references/evidence_policy.md` | Any time a claim requires labeling |
| `references/linear_prompt.md` | Final output — Linear integration |
| `assets/workflow_profiles.json` | Intake — profile selection |
| `assets/document_states.json` | Any state transition |

---

## Output contract

The skill always produces these blocks when delivering final output:

```
CORPUS SUMMARY
Project: [name]
Profile: [workflow profile]
Documents generated: [N]
Documents approved: [N]
Provisional hypotheses: [N — list them]
Canonical sources locked: [list]
Next recommended action: [one sentence]
```

Followed by the actual documents in dependency order, then artifact generation.

# Evidence Policy — Epistemic Labeling

Full policy for how claims are classified, labeled, and propagated across documents.

---

## Core Principle

Every significant claim in every document must carry an epistemic label.
This is not optional and cannot be waived.

The label is not a disclaimer — it is a decision-making signal.
A founder reading a business case must know which numbers they can act on
and which require field validation before committing resources.

---

## Label Definitions

### [FATO]
**Definition**: Directly provided by the user, or sourced from a verifiable external reference
with clear provenance.

**Use when**:
- User stated it explicitly ("our current MRR is R$50k")
- Primary source available (government data, signed contract, audited financials)
- Internally verified through process/system (confirmed via CRM, invoices, etc.)

**Examples**:
- "We have 47 paying customers [FATO] — confirmed in Stripe as of 2024-11"
- "The market grew 23% YoY [FATO] — Source: IBGE, 2024"
- "The contract requires 99.5% uptime [FATO] — Clause 4.2, client agreement"

**Propagation rule**: May propagate as [FATO] downstream if the claim is used unchanged.

---

### [INFERÊNCIA]
**Definition**: A strong, well-reasoned interpretation derived from credible indirect signals.
Not directly stated, but highly plausible given available evidence.

**Use when**:
- Multiple secondary sources point in the same direction
- The conclusion follows logically from confirmed facts
- Industry benchmarks are applied to a specific context

**Examples**:
- "CAC is likely under R$200 given organic channel dominance [INFERÊNCIA]"
- "Churn will be higher in SMB than enterprise segment [INFERÊNCIA] — consistent with SaaS benchmarks"
- "Integration will require ~3 weeks based on similar API complexity [INFERÊNCIA]"

**Propagation rule**: Propagates as [INFERÊNCIA] downstream. Cannot be promoted to [FATO]
without new primary evidence.

---

### [HIPÓTESE]
**Definition**: A plausible belief that has not been validated and could be materially wrong.
Requires field confirmation before being used as a basis for resource allocation.

**Use when**:
- No data supports the claim — only intuition or assumption
- The claim is extrapolated beyond available evidence
- It is a founding assumption of the business model

**Examples**:
- "Customers will pay R$300/month for this [HIPÓTESE] — not yet tested"
- "The integration will take 2 hours per customer [HIPÓTESE]"
- "Users will onboard without human support [HIPÓTESE]"

**Propagation rule**: MUST propagate as [HIPÓTESE] downstream with an explicit flag.
Cannot be silently promoted to [INFERÊNCIA] or [FATO].

---

## Propagation Rules (summary)

| Upstream label | Downstream label | Condition |
|---------------|-----------------|-----------|
| [FATO] | [FATO] | Claim used unchanged |
| [FATO] | [INFERÊNCIA] | Claim synthesized or applied to new context |
| [INFERÊNCIA] | [INFERÊNCIA] | Claim used unchanged |
| [INFERÊNCIA] | [HIPÓTESE] | Never downgrade without reason |
| [HIPÓTESE] | [HIPÓTESE] | Always — mandatory with explicit flag |
| Any | [FATO] | Only if new primary evidence provided |

---

## Synthesis Rule

When a claim is derived from combining multiple labeled sources:

- [FATO] + [FATO] → [FATO] (if no transformation)
- [FATO] + [FATO] → [INFERÊNCIA] (if synthesized or projected)
- Any combination including [INFERÊNCIA] → [INFERÊNCIA] minimum
- Any combination including [HIPÓTESE] → [HIPÓTESE] minimum

---

## Forbidden Patterns

### 1. Silent promotion
**Forbidden**: Using a [HIPÓTESE] in Phase 2 and treating it as established in Phase 3
without re-labeling.

**Required**: Carry the label forward. If it has been validated, explain how and promote
with evidence.

### 2. Laundering through synthesis
**Forbidden**: Averaging or combining several [HIPÓTESE] values to produce an [INFERÊNCIA].

**Required**: Keep the label of the weakest source unless new evidence is introduced.

### 3. Source-free claims
**Forbidden**: "The market is growing rapidly" — no label, no source.

**Required**: "The market is growing at ~18% CAGR [INFERÊNCIA] — derived from segment
reports from Gartner 2023 and McKinsey 2024"

### 4. Fabricated precision
**Forbidden**: "TAM = R$4.7B [FATO]" without a real source.

**Required**: Label honestly. An estimate is [HIPÓTESE] or [INFERÊNCIA], not [FATO],
even if it sounds precise.

---

## Gap vs. Hypothesis

When data is missing, the skill has two options:

**Option A — Gap Report**: Signal the missing data, block generation, ask user to provide it.
Use when the missing data is critical to the document's purpose.

**Option B — Provisional Hypothesis**: Proceed with a clearly labeled [HIPÓTESE], document
it in the Gap section, and flag it for validation.
Use only when the user explicitly chooses this option.

A provisional hypothesis must appear in:
- The document body (inline, labeled [HIPÓTESE])
- The document's "Open Questions" or "Assumptions" section
- The Corpus Summary's "Provisional hypotheses" count

---

## Validation Checklist (self-check before delivering a document)

Before delivering any document:

- [ ] Every financial figure has a label
- [ ] Every market size estimate has a label and source
- [ ] Every customer behavior claim has a label
- [ ] No [HIPÓTESE] from upstream has been silently promoted
- [ ] The "Assumptions" or "Open Questions" section lists all [HIPÓTESE] claims
- [ ] No claim is presented as more certain than the evidence supports

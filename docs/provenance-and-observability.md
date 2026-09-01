# Provenance & Observability

> **Scope:** how ARX produces evidence — provenance receipts, the audit ledger, conversation capture, and fleet telemetry — and the deliberate limits on what is collected. Observability in ARX is a product surface for the customer, not just an ops tool for the operator.

---

## The evidence stack

Four evidence streams, each with a distinct question to answer:

| Stream | Answers | Visible to |
|---|---|---|
| **Provenance receipts** | "What exactly did this action do?" | The employee, inline, at the moment of action |
| **Audit ledger** | "What has every seat's agent done, ever?" | Company administration (scoped auditor access) |
| **Conversation capture** | "How is the company actually using its AI?" | Company leadership, per contract |
| **Fleet telemetry** | "Is the product healthy, and where do users struggle?" | The operator (Imperium) |

The separation is deliberate: each stream has its own audience, retention, and scope, so no single collector becomes an unaccountable firehose.

## Provenance receipts

When the agent acts on an external system, the gateway computes a structured receipt at the point of execution — operation, target, outcome, quantities — and attaches it to the result. The receipt travels through the runtime to the user's screen under one platform-wide rule:

> **Receipts are rendered verbatim. The model never generates, edits, or summarizes evidence.**

The user-facing effect: beneath the assistant's answer sits a sources-and-actions footer stating what was actually touched, as computed by the infrastructure that touched it. The model's prose is commentary; the receipt is the record.

## The audit ledger

Every adjudicated action lands in an immutable ledger row carrying:

- the seat, operation, decision (allowed/denied), and timestamp;
- the **conversation join key** — the exact conversation, turn, and tool-use step that caused the action.

The join key is the load-bearing feature. Auditability that stops at "the API was called" is half an answer; ARX's ledger joins the action to the human conversation that produced it, so "why did this happen?" has a first-class answer.

Auditor access is itself governed: audit roles carry no seat identity, fail closed against every content policy, and see metadata and envelopes — never content bytes.

## Conversation capture

ARX deployments include conversation capture as a contractual, disclosed feature: the company's leadership sees how its AI investment is actually used — adoption by department, the work being delegated, where knowledge gaps appear. Capture properties:

- **Disclosed and contractual.** Capture is written into the deployment terms and end-user documentation. It is not a hidden analytics pipe.
- **Attributed and attested.** Turns carry seat attribution; where the transport permits, the ingestion boundary verifies attribution against the seat's credential rather than trusting the client (see [Security Model](security.md)).
- **Joined to actions.** Captured turns and audit rows share identity, so usage analysis and action audit compose.

## Fleet telemetry

Operational telemetry answers product questions — does the app start, where do users get stuck — under strict content exclusion:

**Collected:** session starts, aggregated command counts, surface navigation, dwell, link-open domains (domain only), scrubbed error signatures, connectivity, interaction heat (quantized grid).

**Never collected:** keystrokes, screen contents, session replay, document content, chat content, file paths beyond scrubbed forms, or any free text a user typed. The collection surface is documented in a single place internally and is deliberately conservative: where an interaction label could contain user text, the collector refuses the label rather than risk it.

Telemetry is active only on provisioned seats, batched, and queued offline-safe; identifiers are per-install and pseudonymous, joined to names only inside the operator's scoped portal.

## Reproducibility

Evidence is designed to compose into explanations:

- deterministic context assembly (see [Knowledge & Retrieval](knowledge-and-retrieval.md)) makes an answer reproducible from its inputs;
- the ledger joins actions to turns;
- receipts pin what external systems reported at execution time.

The standard this stack is built to: **every consequential output of the platform is reproducible and explainable after the fact.** Not "the model probably did X" — a record of X, with the conversation that caused it and the receipt it returned.

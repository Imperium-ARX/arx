# Platform Overview

> **Audience:** technical evaluators — CTOs, CIOs, heads of data, security teams.
> **Scope:** what ARX is, the design thesis behind it, and how the pieces relate. For contracts and invariants, see [Architecture](architecture.md).

---

## The problem ARX exists to solve

Every mid-sized company now has access to frontier AI models. Almost none have access to frontier AI *systems*. The gap between the two is everything that surrounds the model:

- **Grounding.** A model that does not know your org chart, your SOPs, your customers, or your terminology produces fluent generalities. Uploading documents into a chat window is not grounding; it is luggage.
- **Identity.** A shared chat account has no concept of who is asking. A head of finance and a new sales hire should not get the same knowledge surface, the same permissions, or the same capabilities.
- **Governance.** The moment an AI system can *act* — send, update, create, book, invoice — someone must be able to answer, precisely: what was it allowed to do, what did it actually do, and how do we know?
- **Continuity.** Work compounds. A system that forgets everything between sessions forces every user to be their own context engineer, forever.

Large enterprises solve this with platform teams and multi-year integrations. Mid-sized companies cannot. ARX packages the entire system — grounding, identity, governance, continuity — into a single governed appliance, deployed per company, operated by Imperium.

## What ARX is

ARX is a desktop-class AI operating system. Each employee ("seat") runs a company-branded application whose primary surface is conversation, backed by:

- a **frontier reasoning core** (Anthropic's Claude 5 model family) running with full agentic capability — documents, files, browsing, connected business systems;
- a **company ontology**: an explicit, versioned model of the organization — departments, roles, people, entities, systems, and the relationships between them — that scopes and grounds every interaction;
- a **two-tier knowledge fabric**: each seat's personal working knowledge, plus an append-only company knowledge layer that compounds as the whole team works;
- an **action plane** that governs every operation against external business systems through four independent enforcement layers, and returns a provenance receipt for each one;
- a **control plane**, operated by Imperium, that provisions seats, distributes policy and signed updates, and collects operational telemetry — while customer content remains in the customer-resident data plane.

The daily experience is deliberately simple: a department head opens ARX, sees their company dashboard, and works by asking. Everything above is what makes the simple experience trustworthy.

## The design thesis

**Thesis 1 — Structure beats scale for business work.** For a department head's real tasks, a model grounded in an accurate organizational ontology and a curated knowledge fabric outperforms a larger model with neither. ARX invests where the leverage is: in the structure around the model.

**Thesis 2 — Trust is an architecture, not a policy document.** Non-technical users will delegate real work only to a system whose behavior is mechanically constrained. ARX's governance is enforced in four independent places, fails closed, and produces evidence. See [Action Governance](action-governance.md).

**Thesis 3 — Deployment is part of the product.** A knowledge fabric assembled by the customer is a knowledge fabric that never gets assembled. ARX ships with a forward-deployed engagement: Imperium builds the ontology, seeds the knowledge fabric, wires the connections, and provisions every seat before first login. The system arrives *already knowing the company*.

## The seat lifecycle in brief

1. **Provisioning.** Imperium models the company (ontology, knowledge, connections, policy) and issues each employee a single-use provisioning credential.
2. **First login.** The employee installs the company's build of ARX, redeems the credential, and lands in a workspace that already carries their identity, their department's context, and their branded environment. Setup burden on the employee: minutes.
3. **Daily operation.** Conversation, documents, dashboard, connected systems — all scoped to the seat's identity and policy. Knowledge the seat produces can be promoted to the company layer; nothing is shared by accident.
4. **Evolution.** The ontology, knowledge fabric, and capability policy are living objects, revised continuously by Imperium as the company changes.

## What ARX is not

- **Not a chatbot with retrieval.** Retrieval is one stage of one plane. The platform is the identity, governance, and data architecture around it.
- **Not a developer tool.** There is no code surface, no configuration surface, no plugin marketplace exposed to the end user.
- **Not multi-tenant SaaS.** Each company receives a dedicated appliance and a customer-resident data plane. See [Data Boundaries](data-boundaries.md).
- **Not self-serve.** ARX without the forward-deployed engagement would be ARX without its grounding. We do not offer it.

## Reading order for evaluators

1. [Architecture](architecture.md) — the planes and the invariants between them.
2. [Security Model](security.md) — trust boundaries and threat model.
3. [Action Governance](action-governance.md) — how external actions are constrained and evidenced.
4. [Data Boundaries](data-boundaries.md) — what lives where.
5. [The Company Ontology](ontology.md) and [Knowledge & Retrieval](knowledge-and-retrieval.md) — how grounding actually works.

---

<sub><b>ARX — the Company AI Operating System by <a href="https://imperium-growth.com">Imperium</a>.</b> <a href="README.md">Documentation index</a> · <a href="overview.md">Overview</a> · <a href="architecture.md">Architecture</a> · <a href="security.md">Security</a> · <a href="faq.md">FAQ</a> · <a href="glossary.md">Glossary</a> · <a href="https://github.com/Imperium-ARX/arx">github.com/Imperium-ARX/arx</a></sub>

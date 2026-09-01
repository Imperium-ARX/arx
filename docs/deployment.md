# Deployment Model

> **Scope:** how ARX reaches a company and stays current — the per-company appliance, the forward-deployed engagement, update integrity, and the operational lifecycle.

---

## The appliance model

ARX is not a URL your employees visit. Each customer receives a **dedicated, branded desktop appliance** for macOS and Windows: the company's name, mark, and theme across the entire shell, from the installer to the desktop's closed state. Under the brand, every appliance runs the same governed platform, so security posture is uniform across the fleet while identity and scope are personal to every seat.

Why an appliance rather than a browser tab:

- **The work is local.** Files, documents, and the seat's working corpus live on the machine the employee already works on; the assistant operates where the work is, offline-tolerant, at native speed.
- **The boundary is real.** A desktop appliance gives the platform an enforceable runtime boundary — interception layer, managed browser, protected binaries — that a browser tab cannot offer.
- **The brand is the company's.** Adoption is a cultural problem before it is a technical one. An employee who opens *their company's* operating system treats it as infrastructure, not as another SaaS trial.

## The forward-deployed engagement

Every deployment is delivered by Imperium engineers working directly with the company. The sequence:

| Phase | What happens | Output |
|---|---|---|
| **1. Modeling** | Leadership sessions to model the organization: departments, seats, entities, systems, metrics, processes | The company ontology, v1 |
| **2. Seeding** | SOPs, playbooks, templates, and department context assembled and structured into the knowledge fabric | A grounded company tier, day one |
| **3. Wiring** | The company's business systems connected and policy written: which seats may do what, with which arguments, on which systems | Capability policy + connections |
| **4. Provisioning** | Branded builds issued; each employee receives a single-use provisioning credential | Seats live, minutes per employee |
| **5. Evolution** | Standing engagement: ontology revisions, knowledge curation, policy changes, new connections, new seats | A system that tracks the company |

Phase 5 is not support; it is the product working as designed. The ontology and policy are living objects, and the engagement is how they stay true.

## Update lifecycle

The fleet stays current through a signed, verified channel:

- Appliances poll the operator's update service; offers are accepted only over TLS from allow-listed origins, and an offer without a cryptographic digest is rejected outright.
- Artifacts are digest-verified before apply; the apply path is designed to survive interrupted downloads and partial states without ever executing unverified code.
- Platform-native signing and notarization apply per OS.
- The reasoning engine ships as a separately pinned, content-addressed artifact — see [Security Model](security.md) — so engine upgrades carry the same hard-fail verification as application updates.

Policy, branding, and capability changes travel outside the binary channel entirely: they are control-plane pushes, effective fleet-wide without reinstallation.

## Operational posture

- **One binary per company, many seats.** A single build serves the whole company; identity arrives at provisioning time. Rebuild events (rebrand-level changes) are rare and operator-managed.
- **Self-healing by default.** Credential rotation, connection refresh, and auth recovery are automatic or one-click; the design goal is that a non-technical employee is never stranded by infrastructure state.
- **Fleet observability.** The operator sees health and adoption (see [Provenance & Observability](provenance-and-observability.md)); the customer sees usage and audit. Both see what their role justifies, neither more.

## Requirements

| Item | Requirement |
|---|---|
| Employee hardware | Standard company laptops/desktops, macOS or Windows |
| Employee IT effort | Install one application, redeem one credential |
| Customer-side infrastructure | None to operate; the customer-resident data plane is provisioned and managed as part of the engagement |
| Network | Standard outbound TLS |
| Model access | Provisioned per deployment as part of the engagement |

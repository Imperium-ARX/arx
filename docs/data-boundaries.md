# Data Boundaries

> **Scope:** exactly which data lives where, which boundaries it can cross, and which crossings are impossible by construction. This is the document to read with your data-protection officer.

---

## The residency map

| Data class | Resides in | Crosses to | Never crosses to |
|---|---|---|---|
| Personal working files & seat memory | Employee device + versioned replication (seat-private) | — | Other seats; other companies; operator content stores |
| Company knowledge tier | Customer-resident data plane | Read-only distribution to the company's own seats | Other companies; operator content stores |
| Seat-to-seat shared files | Customer-resident data plane (secure exchange) | The addressed recipient, on accept | Unaddressed seats; other companies |
| Conversation capture | Operator evidence store (contractual) | Company leadership reporting | Other companies; model training |
| Audit ledger & receipts | Operator evidence store + inline to the acting seat | Company audit surface (scoped) | Other companies |
| Fleet telemetry (content-free) | Operator telemetry store | — | Anyone as content — it contains none |
| Capability policy, ontology, branding | Control plane (per company) | The company's own appliances | Other companies |
| Connection credentials for business systems | Server-side, brokered by the action gateway | — | The device; the model's context; the workspace |
| Seat tokens | OS secret storage on the seat's device | — | Files; environment; replication |

## Boundary rules

**Company ↔ company.** No shared application tier, corpus, embedding space, index, or memory. Deployments are parallel, not pooled. Nothing learned in one deployment — content, embeddings, ontology, or model adaptation — is an input to any other.

**Seat ↔ seat.** Three crossings exist, all explicit: (1) promotion to the append-only company tier, attributed; (2) the secure exchange, addressed and accepted; (3) audit metadata to scoped auditors. There is no fourth path. Retrieval cannot cross seats because scope precedes ranking; storage cannot cross seats because rows carry seat claims the device's own token cannot forge.

**Customer ↔ operator.** The operator's planes carry policy, evidence, and telemetry. The company's knowledge fabric — the files, documents, SOPs, and working corpus — resides in the customer-resident data plane and does not transit the operator's content stores. Conversation capture is the one contractual, disclosed evidence stream that crosses, and it exists precisely so leadership can see its investment working.

**Everyone ↔ model training.** Customer data is not used to train models. Not ARX's, not anyone's. Grounding is retrieval at inference time against the customer's own fabric; it leaves no residue in weights.

## Retention and revocation

- **Seat revocation** ends data-plane access immediately (claims invalidated), while preserving the append-only company tier and the audit ledger — the company keeps its knowledge and its history; the departed seat keeps nothing.
- **Company offboarding** returns the knowledge fabric to the customer in portable form and decommissions the deployment; evidence-stream retention follows the deployment terms.
- **Quarantine over deletion for credentials.** Invalidated credentials are quarantined with timestamps rather than silently destroyed, preserving the forensic trail.

## Questions we expect from data-protection review

**Where is the data plane hosted?** Per deployment, in the customer's chosen jurisdiction; residency options are part of the engagement's provisioning conversation.

**Can Imperium read our company knowledge?** The forward-deployed engagement involves working with your knowledge — that is the service. Operationally, access is engagement-scoped and attributable; architecturally, your fabric lives in your data plane, not our content stores.

**Can one of our employees read another's workspace?** No path exists: retrieval scope is resolved before ranking, rows are seat-claimed, and the device holds no cross-seat credential. Sharing requires the sender to send and the recipient to accept.

**What does the model provider see?** Inference traffic under the deployment's model-provisioning terms. Customer data is not training input.

**What happens to conversation capture if we end the contract?** It follows the retention schedule in your deployment terms, like every evidence stream.

---

<sub><b>ARX — the Company AI Operating System by <a href="https://imperium-growth.com">Imperium</a>.</b> <a href="README.md">Documentation index</a> · <a href="overview.md">Overview</a> · <a href="architecture.md">Architecture</a> · <a href="security.md">Security</a> · <a href="faq.md">FAQ</a> · <a href="glossary.md">Glossary</a> · <a href="https://github.com/Imperium-ARX/arx">github.com/Imperium-ARX/arx</a></sub>

# FAQ — Technical Evaluators

> The questions CTOs, CIOs, heads of data, and security leads ask first, answered directly. Where an answer has depth behind it, the link goes to the canonical document.

---

### Is this a wrapper around a chat API?

No. The reasoning core is one component of one plane. The platform is the ontology that grounds it, the identity system that scopes it, the enforcement lattice that constrains it, the data plane that isolates it, and the deployment model that makes all of that arrive configured. Remove the model and swap in a better one next year; the platform is the part that persists. See [Architecture](architecture.md).

### Which models does ARX run?

Frontier models from Anthropic's Claude 5 family, routed per seat under policy. Model routing is a control-plane decision, so the fleet moves to newer models without reinstallation.

### Is our data used to train models?

No — not ARX's and not the model provider's. Grounding is inference-time retrieval against your own fabric. See [Data Boundaries](data-boundaries.md).

### How is this different from Microsoft Copilot / ChatGPT Enterprise?

Three structural differences. **Grounding:** ARX resolves every interaction against a curated company ontology, not a search index over whatever the crawler reached. **Governance:** actions clear four independent enforcement layers and return infrastructure-computed receipts; suite assistants largely trust the model's own narration. **Deployment:** ARX arrives as a per-company appliance with the ontology, knowledge, and policy already built by forward-deployed engineers — the work that enterprise AI rollouts usually leave to the customer, which is why they stall.

### What can the agent actually do to our systems?

Exactly what the seat's capability policy materializes, bounded to the argument level, adjudicated server-side per call, and receipted. The complete answer for any seat is a finite, inspectable policy — not "whatever the integrations permit." See [Action Governance](action-governance.md).

### What happens when someone tries to prompt-inject it?

An injected instruction can influence the model's intent; it cannot mint capabilities (layer 1), evade the in-process guard (layer 2), or change the gateway's server-side decision (layer 3) — and the attempt is in the ledger (layer 4). Inbound content is additionally sanitized at trust boundaries. See [Security Model](security.md).

### Can employees see each other's data?

Only through the three explicit channels: append-only promotion to the company tier, the accepted secure exchange, and scoped audit metadata. Retrieval scope is resolved from identity before ranking, and storage rows carry per-seat claims. See [Data Boundaries](data-boundaries.md).

### What do you collect about usage?

Two disclosed streams with different scopes: contractual conversation capture (so leadership sees how the investment is used) and content-free product telemetry (so we see whether the product is healthy). Telemetry never contains keystrokes, content, or free text. See [Provenance & Observability](provenance-and-observability.md).

### What does our IT team have to run?

Nothing. Install one signed application per employee, redeem one single-use credential each. The data plane is provisioned and operated as part of the engagement; updates arrive through a digest-verified channel. See [Deployment](deployment.md).

### How do you handle a departing employee?

Revoke the seat: data-plane claims die immediately, capabilities dematerialize, the company keeps everything promoted to the shared tier plus the full audit history. See [Identity & Provisioning](identity-and-provisioning.md).

### Why is there no self-serve tier?

Because the product's value is the grounded system, and grounding is work. A self-serve ARX would be an empty shell with excellent governance — governing answers grounded in nothing. The forward-deployed engagement is not our sales model; it is how the product comes to exist for each customer.

### Can our security team review the platform?

Yes — deployment-specific security brief, data-processing terms, and customer-led review under NDA, including walking any documented control against its implementation. Coordinated disclosure for researchers: [SECURITY.md](../SECURITY.md).

### Who is behind ARX?

[Imperium](https://imperium-growth.com). ARX is operated under a forward-deployed model: the engineers who build the platform are the engineers who deploy it.

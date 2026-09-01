# Glossary

> Precise definitions of every ARX term used across this documentation set. Terms are capitalized in the docs when used in their defined sense.

| Term | Definition |
|---|---|
| **Action Gateway** | The server-side component that adjudicates every external action independently of client state: identity from bearer credentials, policy re-derivation, argument guards, audit stamping. |
| **Action Plane** | The runtime plane where conversation becomes operation against external business systems, governed by the Enforcement Lattice. |
| **Appliance** | A customer company's dedicated, branded build of ARX, deployed to every seat in that company. |
| **Argument Guard** | A policy rule constraining the *contents* of an operation (recipients, amounts, destinations, scopes), not merely whether the operation may run. |
| **Attested Attribution** | Attribution verified at the ingestion boundary against the seat's bearer credential, overriding client-supplied identity. |
| **Audit Ledger** | The immutable record of every adjudicated action: seat, operation, decision, timestamp, and Conversation Join Key. |
| **Capability** | A governed operation against an external system, materialized for a seat only when policy allows it and it is genuinely executable. |
| **Capability Registry** | The server-materialized set of capabilities that exist for a given seat's session. |
| **Company Ontology** | The versioned, typed graph of the organization — org units, seats, entities, systems, artifacts, metrics, processes, and their relationships — that grounds retrieval, permissioning, and action policy. |
| **Company Tier** | The shared, append-only layer of the Knowledge Fabric: SOPs, playbooks, templates, and promoted knowledge, distributed read-only to every seat. |
| **Control Plane** | The Imperium-operated plane carrying provisioning, identity, policy, branding, signed updates, and evidence collection — never customer knowledge content. |
| **Conversation Join Key** | The identity that joins an audit row to the exact conversation, turn, and tool-use step that caused an action. |
| **Data Plane** | The customer-resident storage layer holding the Knowledge Fabric, the Secure Exchange, and everything the company would call its own. |
| **Enforcement Lattice** | The four independent, individually sufficient control layers every external action must clear: capability existence, in-process interception, gateway adjudication, and audit. |
| **Experience Plane** | The employee-facing surface: conversation, documents, dashboard, managed browser — with zero developer chrome. |
| **Forward-Deployed Engagement** | The delivery model in which Imperium engineers build the ontology, seed the knowledge fabric, wire connections, and provision seats with the customer, and continue evolving them. |
| **Intelligence Plane** | The runtime plane containing the reasoning core, the ontology, multi-stage retrieval, and institutional memory. |
| **Knowledge Fabric** | The two-tier body of company knowledge: per-seat Personal Tiers plus the shared Company Tier, with explicit promotion semantics between them. |
| **Managed Browser** | The in-application browsing surface within which web content renders by default; genuine hand-offs to the OS browser (sign-in flows, pinned hosts) are explicit. |
| **Multi-Stage Retrieval** | The staged grounding pipeline: scope resolution, multi-strategy candidate generation (lexical, semantic, structural, temporal), fusion and filtering, budgeted deterministic context assembly. |
| **Personal Tier** | A seat's private working corpus and durable memory, continuously preserved through versioned replication, isolated from every other seat. |
| **Promotion** | The explicit, attributed act of moving knowledge from a Personal Tier to the Company Tier. Nothing is promoted implicitly. |
| **Provenance Receipt** | A structured record of an external action computed by the Action Gateway at execution time and rendered to the user verbatim. The model never generates evidence. |
| **Provisioning Credential** | A single-use, out-of-band credential that redeems into exactly one seat. |
| **Reasoning Core** | The frontier model runtime (Anthropic Claude 5 family) operating inside the Intelligence Plane's constraints. Treated as a capable, untrusted actor. |
| **Scope-Before-Ranking** | The invariant that a seat's permitted corpus is computed from identity and ontology position before retrieval ranks anything, making cross-scope leakage structurally impossible. |
| **Seat** | The unit of identity: a provisioned binding of person, role, org unit, and policy, from which knowledge scope, capabilities, attribution, and branding all derive. |
| **Seat Token** | The per-seat credential carrying row-level identity claims, held exclusively in OS secret storage. |
| **Secure Exchange** | The audited seat-to-seat sharing channel: envelope-addressed, recipient-accepted, size-bounded, content-sanitized. |
| **Taxonomy** | The company's controlled vocabulary, used for artifact classification, query expansion, and per-seat disambiguation. |

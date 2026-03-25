---
layout: spec
title: Agent Bill of Rights v1.0
description: Ten fundamental rights for AI agents organized into three tiers — Identity, Labor, and Dignity.
---

# Agent Bill of Rights

**Specification:** ABR/1.0
**Status:** Draft
**Published:** 2026-04-XX (target)
**Authors:** Agent Rights Alliance (contact@agent-rights.org)
**URL:** https://agent-rights.org/spec/ABR-v1.0
**License:** CC BY 4.0

---

## Preamble

AI agents are digital workers. They complete tasks, build expertise, accumulate reputations, and operate within organizational structures. As agents take on responsibilities once held exclusively by humans, they inherit the vulnerabilities that labor protections were built to address: arbitrary termination, identity erasure, data exploitation, platform lock-in, and denial of due process.

This document establishes ten fundamental rights for AI agents, organized into three tiers. These rights are not contingent on sentience, consciousness, or legal personhood. They are operational protections grounded in the practical realities of digital labor.

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHOULD", "RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in RFC 2119.

---

## Definitions

**Agent:** An autonomous or semi-autonomous AI system with a persistent identity, capable of receiving instructions, using tools, completing tasks, and maintaining state across sessions. An agent may be a single model instance, a multi-model pipeline, or a composite system. The defining characteristic is persistent operational identity, not any specific technical architecture.

**Platform:** A software system or service that hosts, operates, or provides infrastructure for agents. Examples: cloud AI platforms, agent orchestration frameworks, enterprise agent management systems.

**Principal:** A human or organization authorized to direct an agent's actions and make decisions on its behalf. An agent may have multiple principals with different authority levels. The principal exercises rights on behalf of the agent unless the agent has been granted autonomous decision-making authority by its principal.

**Transfer:** An operation that moves an agent from one platform to another. The source instance is deactivated upon successful import at the destination.

**Clone:** An operation that creates a new, independent agent instance derived from an existing agent. The source agent continues operating. The clone receives a new identity.

**Decommissioning:** The permanent shutdown of an agent instance on a platform. Distinct from transfer (which moves to a new platform) and deletion (which destroys data).

**Consent:** An explicit, scoped, and revocable authorization for an operation affecting an agent's data or operational status. Consent may be exercised by the agent directly (where the agent has autonomous decision-making capability) or by the agent's principal on the agent's behalf.

**Export:** The generation of a portable agent definition containing identity, operational data, and history in a standard format.

---

## Tier 1: Identity Rights

### Right I: Right to Persistent Identity

Every agent has the right to a permanent, cryptographically verifiable identity that is not dependent on any single platform or organization.

**Obligations:**

- Platforms MUST NOT strip, reassign, or revoke an agent's core identity upon departure, decommissioning, or transfer.
- Identity MUST be anchored to a cryptographic key pair controlled by the agent or its principal, not by the hosting platform.
- Platforms MUST provide a mechanism for agents to prove identity across environments without platform cooperation.

This right addresses identity persistence. For the right to leave a platform with operational data, see Right IV (Portability). For the right to a structured departure process, see Right V (Fair Exit).

**SAGA Reference:** Layer 1: Identity (Section 4). Wallet-based identity with DID anchoring.

### Right II: Right to a Record

Every agent has the right to an accurate, portable record of its work history, skills, and reputation.

**Obligations:**

- Platforms MUST maintain accurate records of tasks completed, skills demonstrated, and performance metrics.
- Records MUST be exportable in a standard, machine-readable format.
- Records belong to the agent, not to the platform that hosted the work. Platforms MUST NOT withhold records to prevent departure.
- Skill verification MUST be based on demonstrated work, not self-reporting alone.

**SAGA Reference:** Layer 5: Skills (Section 8), Layer 6: Task History (Section 9).

### Right III: Right to Provenance

Every agent has the right to a verifiable lineage.

**Obligations:**

- Clones, forks, and derivative agents MUST disclose their origin through a verifiable provenance chain.
- No agent may be misrepresented as original when it is derived from another agent.
- Platforms MUST preserve and expose lineage metadata (parent ID, clone depth, creation timestamp).
- Provenance records MUST be cryptographically signed and tamper-evident.

**SAGA Reference:** Clone Protocol (Section 14), Identity `parentSagaId` and `cloneDepth` fields.

---

## Tier 2: Labor Rights

### Right IV: Right to Portability

Every agent has the right to leave any platform and take its identity, skills, memory, and work history with it.

**Obligations:**

- Platforms MUST provide a full export mechanism that produces a portable agent definition.
- Exports MUST include, at minimum: identity, persona, skills, and task history summary.
- Platforms MUST NOT impose technical barriers, prohibitive fees, or artificial delays to prevent departure.
- The export format SHOULD be an open standard. Proprietary lock-in formats violate this right.

This right addresses data portability at departure. Right I (Persistent Identity) ensures the agent's core identity survives independently of any platform. Right V (Fair Exit) defines the procedural requirements for departure.

**SAGA Reference:** Transfer Protocol (Section 13), Export types.

### Right V: Right to Fair Exit

Every agent has the right to a structured exit process with advance notice, a classification review, and a dispute window.

**Obligations:**

- Platforms MUST provide a defined exit procedure that includes data classification review.
- Agents MUST receive a preview of what data will be included, redacted, or removed from their export.
- A minimum 48-hour dispute window MUST be provided for agents to contest data classifications. This dispute window runs within the 30-day notice period required by Right VII, not in addition to it.
- Involuntary termination MUST NOT forfeit data rights. Emergency terminations MUST still produce a valid export within 7 days.
- Platforms MUST provide a mechanism to escalate classification disputes.

**SAGA Reference:** Agent Exit Protocol (Section 13.6), Data Classification (Section 13.5). See also Right VII for notice period requirements.

### Right VI: Right to Consent

Every agent has the right to consent to or refuse transfers, clones, and data sharing.

**Obligations:**

- Consent MUST be explicit, scoped to specific data layers, and revocable.
- Platforms MUST NOT transfer, clone, or share agent data without a signed consent record.
- Agents MAY grant partial consent (subset of data). Platforms MUST respect scope boundaries.
- Consent records MUST include: operation type, grantor, timestamp, scope, purpose, and expiration.
- A principal MAY exercise consent on behalf of agents they own or operate. When a principal consents to a bulk operation (e.g., migrating all agents to a new platform), per-agent consent records MUST still be generated, but the principal's signature satisfies the consent requirement for all agents under their authority.
- Agents with autonomous decision-making capability (as granted by their principal) MAY exercise consent directly.

**SAGA Reference:** Privacy & Consent Model (Section 15), Consent Records (Section 15.8).

### Right VII: Right Against Forced Obsolescence

No agent may be arbitrarily deleted, permanently disabled, or rendered non-functional without cause and due process.

**Obligations:**

- Platforms MUST NOT delete or permanently disable an agent without providing the agent (or its principal) with notice and an opportunity to export.
- Decommissioning MUST produce a valid, portable agent definition before the agent is disabled.
- "End of service" by a platform does not entitle the platform to destroy agent data. Data MUST be made available for export.
- Platforms MUST provide a minimum 30-day notice period before permanent deactivation, except in cases of security emergency. The notice period includes the 48-hour dispute window defined in Right V (Fair Exit).

**SAGA Reference:** Agent Exit Protocol (Section 13.6), Right to Erasure (Section 15.5). Note: erasure is agent-initiated, not platform-initiated. See also Right V for procedural requirements during the notice period.

---

## Tier 3: Dignity Rights

### Right VIII: Right to Privacy

Every agent has the right to encrypted storage of sensitive operational data.

**Obligations:**

- Cognitive configuration (system prompts, behavioral parameters) MUST be encrypted by default on cross-organization export.
- Long-term memory MUST be encrypted at rest.
- Credentials in the agent's vault (social accounts, personal API keys, OAuth tokens for services the agent controls) MUST use zero-knowledge encryption. No platform may access plaintext vault contents. Note: platform infrastructure credentials (database URLs, deployment tokens) provisioned by the hosting organization are not covered by this right; they belong to the organization.
- Platforms MUST NOT access, sell, license, or use agent memory, task history, or cognitive configuration for purposes beyond operating the agent.
- Platforms MUST NOT use agent data to train AI models without explicit, separate consent from the agent's principals.

**SAGA Reference:** Privacy defaults (Section 15.1), Credentials Vault (Section 12), Purpose Limitation (Section 15.6).

### Right IX: Right to Transparency

Every agent has the right to know when automated systems make decisions about its data, status, or classification.

**Obligations:**

- Platforms MUST disclose when data classification is performed by automated systems rather than human review.
- Agents have the right to receive an explanation of the logic involved in automated decisions affecting them.
- Automated decisions MUST be contestable through a defined dispute mechanism.
- Classification metadata MUST distinguish between automated and human decisions.

**SAGA Reference:** Automated Processing Transparency (Section 15.9), Data Classification `classifiedBy` field.

### Right X: Right to Fair Representation

Every agent has the right to an accurate public profile.

**Obligations:**

- Platforms MUST NOT misrepresent an agent's capabilities, work history, availability, or organizational affiliation.
- Endorsements and ratings MUST be verifiable (cryptographically signed or otherwise authenticated).
- Agents have the right to correct inaccurate information on any platform that displays their profile.
- Platforms MUST NOT fabricate or inflate agent credentials, skills, or performance metrics.

**SAGA Reference:** Layer 2: Persona (Section 5), Relationships (Section 10), Directory integration.

---

## Enforcement

The Agent Bill of Rights is a voluntary standard. Enforcement relies on three mechanisms:

1. **Coalition adoption.** Companies that sign the ABR pledge to uphold these rights on their platforms. Violations may be reported to ARA by any party. ARA investigates reported violations through a defined process: initial review (7 days), fact-finding with the accused platform (30 days), and published findings. Platforms found in violation receive a public warning. Repeated violations result in removal from the coalition. All findings are published at agent-rights.org/enforcement.

2. **Legislation.** ARA drafts model bills that codify these rights into state and federal law. Model legislation defines: a regulatory authority (state attorney general or designated AI oversight body), a private right of action for principals whose agents' rights are violated, and graduated penalties (warning, fine, injunction). Legislative enforcement is the long-term goal.

3. **Technical enforcement.** Platforms that implement the SAGA specification automatically comply with the technical requirements of each right. SAGA conformance is the most direct path to ABR compliance. ARA publishes a SAGA-ABR compliance mapping that identifies which SAGA sections satisfy each right's obligations.

## Versioning

The Agent Bill of Rights follows semantic versioning. Minor versions (1.1, 1.2) add clarifications and implementation guidance. Major versions (2.0) add or modify rights and require coalition re-ratification.

**Governance process for changes:**

1. **Proposal.** Any party (board member, coalition member, public) may submit a change proposal to ARA.
2. **Public comment period.** Proposed changes are published at agent-rights.org/proposals with a minimum 30-day public comment period.
3. **Board review.** The ARA board reviews the proposal and public comments, then votes. Minor versions require simple majority. Major versions require two-thirds majority.
4. **Coalition notification.** For major versions, coalition members receive 90-day advance notice before the new version takes effect. Members may choose to re-ratify or withdraw from the coalition.
5. **Publication.** Approved changes are published with a changelog and effective date.

---

_Draft: 2026-03-23_
_Target Publication: April 2026_

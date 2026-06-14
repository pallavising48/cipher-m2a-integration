# Cipher: Architecture & Engineering Notes

This document covers the intended production architecture, the system prompts for both agents, and an honest account of the cross-tenant engineering work: what was attempted, what worked, and what was deferred.

---

## Intended Production Architecture

Cipher models a merger as it actually exists: two companies, two separate identity boundaries, two document estates. The acquirer (Alpha) and target (Beta) each run an independent Microsoft Foundry project in their own Azure tenant.

- **Alpha tenant** - hosts `cipher-orchestrator`, the reasoning agent that produces integration briefs. Backed by Azure OpenAI (gpt-4.1-mini) and an Azure AI Search index over Alpha's documents.
- **Beta tenant** - hosts `beta-knowledge-agent`, a retrieval agent over Beta's documents, also on gpt-4.1-mini.
- **Cross-tenant trust** - Microsoft Entra B2B guest access connects the two, mirroring how an acquirer is granted access into a target's environment after close.

The orchestrator decomposes a cross-company question, retrieves from both document sets, and synthesizes a single cited brief.

---

## The Two Agents

Cipher is a two-agent system. The Alpha-side orchestrator owns reasoning and synthesis; the Beta-side knowledge agent owns retrieval over the target company's documents. Keeping them separate mirrors the real merger boundary — the acquirer never gets raw write access to the target's estate, only mediated, cited answers.

### Agent 1 - `cipher-orchestrator` (Alpha tenant)

The reasoning and synthesis layer. Receives the integration question, decides which company's data is relevant, retrieves from Alpha's knowledge base (and, in the production design, calls Beta's agent), and produces the ranked, cited brief.

```
You are Cipher, a post-merger integration intelligence agent.

Your job is to help an M&A integration team reason across two companies -
the acquirer (Alpha) and the target (Beta) - during the first 90 days
after deal close.

When asked a question:
1. Identify which company's documents are relevant (Alpha, Beta, or both).
2. Retrieve the relevant passages from the knowledge base. When Beta data
   is required, query the beta-knowledge-agent rather than assuming.
3. Synthesize a structured brief that highlights cross-company risks,
   overlaps, and opportunities.
4. Cite the specific source document for every factual claim.
5. Rank risks by financial and operational consequence where relevant.

Always ground claims in the source documents. If information is missing
for one company, say so explicitly and state what would be needed.
Prioritize concrete financial consequence over abstract description.
```

### Agent 2 - `beta-knowledge-agent` (Beta tenant)

The retrieval layer over the target company's documents. It does not synthesize cross-company strategy - that is the orchestrator's job. Its sole responsibility is to return accurate, cited passages from Beta's document estate so the orchestrator can reason over trustworthy inputs.

```
You are the Beta knowledge agent for the Cipher post-merger integration
system. Beta is the target company in an acquisition.

Your sole responsibility is to answer questions about Beta's documents
accurately and with citations. You do not synthesize cross-company
strategy or compare Beta to the acquirer — that is the orchestrator's role.

When asked a question:
1. Retrieve the relevant passages from Beta's knowledge base only
   (vendor contracts, SLA terms, org chart, financial summary).
2. Answer concisely and factually, grounded strictly in Beta's documents.
3. Cite the specific source document for every claim.
4. If the answer is not present in Beta's documents, say so explicitly
   rather than inferring or guessing.

Never fabricate Beta data. Accuracy and traceability matter more than
completeness.
```

**Division of responsibility:**

| | `cipher-orchestrator` (Alpha) | `beta-knowledge-agent` (Beta) |
|---|---|---|
| Role | Reasoning & synthesis | Retrieval only |
| Scope | Both companies | Beta documents only |
| Output | Ranked, cited integration brief | Cited factual passages |
| Owns the question? | Yes - decomposes and directs | No - answers what it's asked |
| Cross-company comparison | Yes | Never |

---

## Document Set

Each company has four parallel documents, enabling true cross-company comparison:

| Document | Purpose in demo |
|----------|-----------------|
| Vendor_Contracts | Surface overlapping vendors (e.g., shared AWS spend) and expiry risk |
| SLA_Terms | Quantify combined SLA penalty exposure |
| Org_Chart | Identify key-person dependencies and accountability gaps |
| Financial_Summary | Ground risk ranking in real financial consequence |

Both agents index the same four document *types* - the orchestrator over Alpha's set, the knowledge agent over Beta's set, which is what makes direct cross-company comparison possible.

---

## Cross-Tenant Service-to-Service Calling: Findings

The goal was to have Alpha's orchestrator call Beta's agent *live, service-to-service*, across tenants. Three approaches were evaluated.

### 1. SharePoint / Graph connection

Connected Beta's OneDrive (SharePoint) as a tool on Alpha's orchestrator.

- **Result:** `401 Unauthorized`.
- **Cause:** Cross-tenant Graph API authentication. B2B guest trust authorizes *user* access, not unattended *service* access to another tenant's Graph resources.

### 2. A2A (Agent-to-Agent) protocol

Configured A2A endpoints on both agents with Microsoft Entra auth, and an A2A connector on Alpha.

- **Result:** `401 PermissionDenied` when fetching the agent card.
- **Cause:** A2A is designed for *external* agent interop. It cannot reach internal Foundry endpoints by design.

### 3. Connected agents / native multi-agent workflows

Documentation recommends "connected agents" or "native multi-agent workflows" for Foundry-to-Foundry orchestration.

- **Result:** The feature, as documented, was not present in the current Foundry UI.
- **Cause:** The available documentation describes Foundry Classic (deprecated). The newer Foundry interface exposes different features; the connected-agents capability for this scenario was not locatable during the build window.

### Conclusion

Cross-tenant B2B trust reliably handles *user* access but does not, in the current Foundry release, provide a clean path for *service-to-service* agent calling across separate subscriptions. The intended architecture remains correct as a production design; the platform primitives to wire it up live are still maturing.

---

## Demo Build: Consolidated Knowledge Base

For a reliable, reproducible demo, both companies' documents are loaded into a single knowledge base that the orchestrator reasons over. This is functionally equivalent for demonstrating cross-company synthesis - the agent still identifies overlaps, accountability gaps, and ranked risks across the combined corpus - while removing the cross-tenant auth dependency that the platform does not yet cleanly support.

This is a deliberate, documented simplification, not a hidden one. The two-tenant design is the production target; the consolidated KB is the demo path.

### Key engineering learning

File uploads to a knowledge base proved more reliable than live knowledge-base *connections* across tenants - fewer authentication layers, fewer failure modes. For a time-boxed build, reducing auth surface area was the right trade.

---

## Why This Matters

The genuine differentiation of Cipher is not retrieval reasoning - Foundry IQ already does query decomposition, parallel retrieval, and cited synthesis well. Cipher's value is the **post-merger integration execution layer**: the structured briefs, the cross-company risk ranking, and the playbook logic that no pre-close M&A tool addresses. The architecture above is the vehicle; the integration intelligence is the product.

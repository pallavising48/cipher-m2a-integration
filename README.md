# Cipher: Post-Merger Integration Intelligence Agent

Post-merger integration intelligence agent using Microsoft Foundry

<img width="1536" height="1024" alt="ChatGPT Image Jun 13, 2026, 11_53_25 PM" src="https://github.com/user-attachments/assets/a4a9000a-af41-4330-a6d7-4b53db2272cd" />


## The Problem

When two companies merge, the integration team inherits a fragmented information landscape. The acquirer's vendor contracts, SLA commitments, and org structure live in one set of systems; the target company's equivalent data lives in an entirely separate tenant. 

In the critical first 90 days after close, integration teams need to answer cross-company questions fast: Where do our vendor commitments overlap? Who owns the relationships we can't afford to lose? What's our combined SLA penalty exposure? Today, answering these requires manual review across two disconnected environments - slow, error-prone, and expensive.

Existing M&A tools (Harvey, Hebbia, Datasite, DealRoom, Midaxo) focus on the pre-close deal phase: due diligence, the data room, document review. They stop at the deal close. The post-close execution gap — where integration value is actually won or lost - remains unaddressed.

## The Solution

Cipher is a post-merger integration intelligence agent that queries both companies' documents simultaneously and synthesizes the cross-company risks and opportunities integration teams care about. Every answer is grounded in cited source documents.

## Architecture

Cipher mirrors the real cross-company structure of a merger using two independent Microsoft Foundry projects across separate Azure tenants:

- **Alpha (acquirer)** - Foundry project with orchestrator agent, Azure OpenAI, Azure AI Search
- **Beta (target)** - Foundry project with knowledge agent over Beta's documents
- **Cross-tenant trust** - B2B guest access established between tenants

The Alpha orchestrator synthesizes M&A integration briefs, reasoning across both document sets and returning structured, cited results.

<img width="822" height="612" alt="image" src="https://github.com/user-attachments/assets/41ac15fd-edd6-4c22-aeed-9d3773d15a85" />

<img width="1906" height="937" alt="image" src="https://github.com/user-attachments/assets/661af4f2-7d00-46bb-add1-debd7e74e1b2" />


## Key Features

- **Cross-company reasoning** - queries acquirer and target data in a single synthesis
- **Cited results** - every claim traces to a source document
- **M&A risk synthesis** - ranks financial, operational, and people risks for the first 90 days
- **Ecosystem-neutral design** - built to extend beyond Microsoft to cross-platform integration (e.g., Microsoft-native acquirer + Google Workspace target)

## Demo

📹 [5-minute demo video](YOUR_YOUTUBE_LINK)

Three scenarios:
1. Vendor overlap & expiry risk
2. People & accountability gaps
3. 90-day financial & operational risk synthesis

## Technical Stack

- Microsoft Foundry (agent orchestration)
- gpt-4.1-mini
- Azure OpenAI
- Azure AI Search
- Microsoft Entra (cross-tenant B2B)

## How to Run

These steps let a judge reproduce Cipher against the sample documents using the consolidated knowledge base (the demo configuration).

### Prerequisites

- An Azure subscription with access to **Azure AI Foundry**
- **Azure OpenAI** access with a `gpt-4.1-mini` deployment
- An **Azure AI Search** resource
- Permission to create a Foundry project and upload documents

### Steps

1. **Clone the repo**
```bash
   git clone https://github.com/pallavising48/cipher-m2a-integration.git
   cd cipher-m2a-integration
```

2. **Create a Foundry project** in the Azure AI Foundry portal and deploy a `gpt-4.1-mini` model.

3. **Create an Azure AI Search resource** and connect it to your Foundry project as a knowledge source.

4. **Upload the sample documents.** Load all eight files from `data/sample-documents/` — both the Alpha set and the Beta set (Vendor_Contracts, SLA_Terms, Org_Chart, Financial_Summary for each) — into the same knowledge base. This consolidated KB is what lets the orchestrator reason across both companies.

5. **Create the orchestrator agent.** Add a new agent named `cipher-orchestrator`, paste the system prompt from [`docs/architecture.md`](docs/architecture.md), and attach the knowledge base (and the web search tool, if desired).

6. **Run the three demo queries** and confirm Cipher returns cited, cross-company briefs:
   - *"What cloud vendor contracts do Alpha and Beta have, and where are there duplicate commitments or expiry risks?"*
   - *"Who owns Customer Success at Beta, and have they been included in Alpha's integration planning?"*
   - *"What are the top 3 financial and operational risks in the first 90 days?"*

### Reproducing the two-tenant architecture (optional)

The full cross-tenant design - two separate Foundry projects, two Azure tenants, Microsoft Entra B2B trust, and the `beta-knowledge-agent` - is documented in [`docs/architecture.md`](docs/architecture.md), including the service-to-service calling approaches that were evaluated and why the consolidated KB is used for the demo.

## Team

- Pallavi Singh - pallavi.singh.career@gmail.com
- Ayushi Walia - ayushiwalia14@gmail.com

## License

MIT

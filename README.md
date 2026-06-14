# Cipher: Post-Merger Integration Intelligence Agent

Post-merger integration intelligence agent using Microsoft Foundry

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

[To be completed — judge reproduction steps]

## Team

- Pallavi Singh - pallavi.singh.career@gmail.com
- Ayushi Walia - ayushiwalia14@gmail.com

## License

MIT

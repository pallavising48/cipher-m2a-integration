# DELTA CORP — Customer SLA Commitments & Performance Report

**Q4 2025** | Document Date: January 10, 2026 | Prepared by: Engineering & Customer Success

## 1. SLA Commitments to Customers

Alpha Corp commits to the following service levels in all Enterprise customer agreements. These obligations are binding and subject to financial penalties as described below.

| SLA Metric | Committed Level | Measurement Window | Penalty if Breached |
|---|---|---|---|
| Platform Uptime | 99.9% | Monthly rolling | 5% credit per 0.1% below threshold |
| API Response Time (P95) | < 300ms | Weekly average | 10% credit if avg exceeds 500ms |
| Data Processing Latency | < 4 hours for batch jobs | Per job | Credit per hour of delay beyond SLA |
| Support Response — P1 Issues | < 1 hour acknowledgment | Per incident | $5,000 penalty per breach |
| Support Response — P2 Issues | < 4 hours acknowledgment | Per incident | $1,000 penalty per breach |
| Data Export Availability | 99.5% monthly | Monthly | 3% credit per 0.5% below threshold |

## 2. Q4 2025 Performance vs. SLA

| Month | Uptime | API P95 (ms) | P1 Response | SLA Status | Credits Issued |
|---|---|---|---|---|---|
| October 2025 | 99.94% | 278ms | 42 min avg | COMPLIANT | $0 |
| November 2025 | 99.87% | 312ms | 58 min avg | BREACH — API | $48,000 |
| December 2025 | 99.91% | 291ms | 38 min avg | COMPLIANT | $0 |

November 2025 SLA breach was caused by a database migration incident affecting the EU-West region. Root cause analysis completed. Remediation implemented December 3, 2025. Three enterprise customers received credits totaling $48,000.

## 3. Top 5 Enterprise Customers by SLA Sensitivity

| Customer | ARR | SLA Tier | Custom Terms | Renewal Date |
|---|---|---|---|---|
| Meridian Financial | $1,200,000 | Platinum | 99.95% uptime, 4hr P1 response | June 2026 |
| Arctus Health | $890,000 | Platinum | 99.9%, HIPAA BAA included | September 2026 |
| Vortex Logistics | $740,000 | Gold | 99.9% standard terms | March 2027 |
| ClearBridge Capital | $620,000 | Gold | 99.9%, financial data SLA addendum | November 2026 |
| Pinnacle Retail Group | $510,000 | Gold | 99.9% standard, dedicated CSM required | August 2026 |

## 4. SLA Risk Post-Acquisition

The proposed acquisition of Beta Technologies introduces the following SLA risks that must be assessed during integration planning:

| Risk | Impact | Priority |
|---|---|---|
| Beta customers have different SLA tiers — harmonization needed | Contract renegotiation required for ~40 Beta accounts | HIGH |
| Shared infrastructure post-migration may strain Alpha uptime commitments | Potential breach risk for Meridian Financial and Arctus Health | HIGH |
| Beta P1 response SLA is 2 hours vs Alpha's 1 hour standard | CS team must be trained and scaled before Beta tickets route to Alpha queue | MEDIUM |
| Beta has no financial penalty clauses — Alpha does | Legal review needed before any customer communication about combined platform | MEDIUM |

---
*DELTA CORP — CONFIDENTIAL | SLA Report | Q4 2025*

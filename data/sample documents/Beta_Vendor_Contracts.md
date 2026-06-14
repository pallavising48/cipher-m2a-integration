# GAMMA TECHNOLOGIES — Vendor Contract Summary

**Confidential** | Document Date: January 20, 2026 | Classification: Internal Use Only

## 1. Overview

Beta Technologies is a B2B SaaS company headquartered in Austin, Texas, with approximately $43M ARR and 83 employees. This document summarizes all active vendor contracts as of Q1 2026. Beta was acquired by Alpha Corp on January 31, 2026. This document is provided to Alpha's integration team for vendor consolidation planning.

## 2. Cloud Infrastructure Vendors

### 2.1 Amazon Web Services (AWS)

| Field | Details |
|---|---|
| Contract ID | GAMMA-AWS-2023-001 |
| Contract Type | Standard On-Demand + 1-Year Reserved Instances |
| Annual Spend | $780,000 (est. FY2025) |
| Contract Start | July 1, 2023 |
| Contract End | June 30, 2026 |
| Auto-Renewal | YES — 30-day opt-out only |
| SLA Uptime Guarantee | 99.99% for EC2 and RDS |
| Penalty Clause | Service credits only — no cash penalties |
| Primary Contact | James Rodriguez, AWS SMB Team |
| WARNING | Contract expires June 2026 — consolidation with Alpha AWS account recommended before renewal |

Beta's AWS footprint runs on separate account from Alpha (Account ID: 482910374821). Primary workloads: EC2 (product), RDS MySQL, S3, SES for email. Overlap with Alpha's AWS usage is significant — consolidation could yield $320,000 in annual savings per Alpha CFO estimate.

### 2.2 Databricks

| Field | Details |
|---|---|
| Contract ID | GAMMA-DBX-2025-002 |
| Contract Type | Annual Premium Subscription |
| Annual Commitment | $240,000 |
| Contract Start | March 1, 2025 |
| Contract End | February 28, 2027 |
| Auto-Renewal | Yes — 60-day opt-out |
| SLA | 99.9% platform availability |
| Usage | ML pipeline, customer churn prediction, product usage analytics |
| Note | Alpha uses Snowflake — platform decision required by March 30, 2026 |

### 2.3 Grafana Cloud

| Field | Details |
|---|---|
| Contract ID | GAMMA-GRF-2025-005 |
| Contract Type | Pro Plan — Annual |
| Annual Commitment | $36,000 |
| Contract Start | January 1, 2025 |
| Contract End | December 31, 2025 — EXPIRED |
| Renewal Status | Month-to-month since Jan 2026 — no auto-renewal signed |
| Usage | Infrastructure dashboards, on-call alerting |
| Note | Can be cancelled with 30 days notice. Alpha uses Datadog — migrate and cancel. |

## 3. Business Software Vendors

### 3.1 HubSpot

| Field | Details |
|---|---|
| Contract ID | GAMMA-HB-2024-003 |
| Contract Type | Marketing Hub + Sales Hub Enterprise — 83 seats |
| Annual Commitment | $96,000 |
| Contract Start | August 1, 2024 |
| Contract End | July 31, 2026 |
| Auto-Renewal | Yes — 60-day opt-out |
| Admin Owner | Clara Wong, Marketing Ops — cwong@betatech.io |
| Note | Alpha uses Salesforce. CRM migration decision required before July 2026 renewal. |

### 3.2 Microsoft 365

| Field | Details |
|---|---|
| Contract ID | GAMMA-M365-2024-001 |
| Contract Type | Microsoft 365 Business Premium — 83 seats |
| Annual Commitment | $48,000 |
| Contract Start | February 1, 2024 |
| Contract End | January 31, 2027 |
| Auto-Renewal | Yes — 60-day opt-out |
| Admin Owner | Vikram Reddy, IT Manager — vreddy@betatech.io |
| Note | Tenant merger with Alpha M365 required. Cross-tenant migration estimated at 6-8 weeks. |

## 4. Contract Risk Summary

| Vendor | Annual Value | Urgency | Action Required |
|---|---|---|---|
| AWS | $780,000 | HIGH — expires June 2026 | Consolidate into Alpha AWS account before June 30 |
| Databricks | $240,000 | HIGH — decision by Mar 30 | Evaluate vs Snowflake — pick one platform |
| Grafana Cloud | $36,000 | IMMEDIATE | Cancel — already month-to-month, migrate to Datadog |
| HubSpot | $96,000 | HIGH — expires July 2026 | CRM decision: migrate to Salesforce or negotiate |
| Microsoft 365 | $48,000 | MEDIUM — expires Jan 2027 | Plan tenant merger — 6-8 week migration |

**TOTAL ANNUAL VENDOR SPEND (Beta): $1,200,000**

---
*GAMMA TECHNOLOGIES — CONFIDENTIAL | Vendor Contracts | Q1 2026*

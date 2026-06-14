# DELTA CORP — Vendor Contract Summary

**Confidential** | Document Date: January 15, 2026 | Classification: Internal Use Only

## 1. Overview

Alpha Corp is a B2B SaaS company headquartered in San Francisco, California, with approximately $210M ARR and 340 employees. This document summarizes all active vendor contracts as of Q1 2026, including cloud infrastructure, software, and professional services agreements.

## 2. Cloud Infrastructure Vendors

### 2.1 Amazon Web Services (AWS)

| Field | Details |
|---|---|
| Contract ID | DELTA-AWS-2024-001 |
| Contract Type | Enterprise Reserved Instance + Savings Plan |
| Annual Commitment | $2,400,000 |
| Contract Start | March 1, 2024 |
| Contract End | February 28, 2027 |
| Auto-Renewal | Yes — 60-day opt-out window |
| SLA Uptime Guarantee | 99.99% for EC2, RDS, S3 |
| Penalty Clause | Service credits up to 30% of monthly spend if SLA breached |
| Primary Contact | Sarah Chen, AWS Enterprise Account Manager |
| Account Manager Email | s.chen@aws-enterprise.com |

Alpha's AWS environment hosts the core product infrastructure including compute (EC2), database (RDS PostgreSQL), object storage (S3), and CDN (CloudFront). The current reserved instance commitment covers 18 r5.2xlarge instances and 12 m5.xlarge instances.

### 2.2 Snowflake

| Field | Details |
|---|---|
| Contract ID | DELTA-SNOW-2025-003 |
| Contract Type | On-Demand + Annual Capacity Commitment |
| Annual Commitment | $480,000 |
| Contract Start | June 1, 2025 |
| Contract End | May 31, 2027 |
| Auto-Renewal | Yes — 90-day opt-out window |
| SLA Uptime Guarantee | 99.9% availability |
| Penalty Clause | Service credits of 10% monthly if uptime falls below 99% |
| Primary Contact | Marcus Williams, Snowflake Strategic Accounts |
| Usage | Data warehouse for product analytics, customer reporting, finance BI |

### 2.3 Datadog

| Field | Details |
|---|---|
| Contract ID | DELTA-DD-2025-007 |
| Contract Type | Annual Enterprise License |
| Annual Commitment | $190,000 |
| Contract Start | September 1, 2025 |
| Contract End | August 31, 2026 |
| Auto-Renewal | Yes — 30-day opt-out window |
| SLA | 99.9% platform availability |
| Usage | Infrastructure monitoring, APM, log management for all production services |
| Penalty Clause | None — credit-based compensation only |

## 3. Business Software Vendors

### 3.1 Salesforce

| Field | Details |
|---|---|
| Contract ID | DELTA-SF-2024-002 |
| Contract Type | Enterprise Edition — 340 seats |
| Annual Commitment | $612,000 |
| Contract Start | January 1, 2024 |
| Contract End | December 31, 2026 |
| Auto-Renewal | Yes — 90-day opt-out window |
| Modules | Sales Cloud, Service Cloud, Revenue Intelligence |
| Admin Owner | Jake Patel, Salesforce Admin — jpatel@alphacorp.com |
| Note | Seats licensed for full company. Acquisition will require seat review. |

### 3.2 Microsoft 365

| Field | Details |
|---|---|
| Contract ID | DELTA-M365-2025-001 |
| Contract Type | Microsoft 365 E3 — 340 seats |
| Annual Commitment | $204,000 |
| Contract Start | April 1, 2025 |
| Contract End | March 31, 2027 |
| Auto-Renewal | Yes — 60-day opt-out window |
| Modules | Teams, SharePoint, OneDrive, Exchange, Office Apps |
| Admin Owner | IT Operations — itops@alphacorp.com |

## 4. Contract Risk Summary

| Vendor | Annual Value | Renewal Risk | Integration Note |
|---|---|---|---|
| AWS | $2,400,000 | LOW — 2027 expiry | Beta also uses AWS — review for duplicate commitments |
| Snowflake | $480,000 | MEDIUM — 2027 expiry | Beta uses Databricks — data platform consolidation needed |
| Datadog | $190,000 | HIGH — Aug 2026 renewal | 30-day opt-out window approaching — decision needed Q2 2026 |
| Salesforce | $612,000 | MEDIUM — 2026 expiry | Beta uses HubSpot — CRM consolidation is a major integration task |
| Microsoft 365 | $204,000 | LOW — 2027 expiry | Beta also on M365 — tenant merger required post-close |

**TOTAL ANNUAL VENDOR SPEND (Alpha): $3,886,000**

---
*DELTA CORP — CONFIDENTIAL | Vendor Contracts | Q1 2026*

# Awesome-SaaS-Usage-Metering-Analytics

# Awesome SaaS Usage & Metering Analytics

> A curated list of top SaaS Usage and Metering Analytics platforms — both SaaS/Hosted commercial solutions and open-source alternatives for tracking consumption, enforcing entitlements, and billing customers based on what they actually use.
> 🌟 Star this repo if you find it useful! 🌟

---

## 📋 Table of Contents

- [SaaS / Hosted Platforms](#-saas--hosted-platforms)
  - [Metronome (Stripe)](#metronome-stripe)
  - [Orb (Adyen)](#orb-adyen)
  - [m3ter (Salesforce)](#m3ter-salesforce)
  - [Amberflo](#amberflo)
  - [Togai (Zuora)](#togai-zuora)
  - [Chargebee Usage Billing](#chargebee-usage-billing)
  - [Zuora](#zuora)
- [Open-Source Software](#-open-source-software)
  - [OpenMeter](#openmeter)
  - [Lago](#lago)
  - [Flexprice](#flexprice)
  - [Lotus](#lotus)
- [Comparison at a Glance](#-comparison-at-a-glance)
- [Contributing](#-contributing)

---

## 🟦 SaaS / Hosted Platforms

Commercial, cloud-hosted SaaS Usage and Metering Analytics platforms. The standalone metering category consolidated dramatically in 2026 — Stripe acquired Metronome, Salesforce acquired m3ter, Adyen acquired Orb, and Zuora had already absorbed Togai [citation:1][citation:15]. These are not open-source but are included as reference points for feature comparison.

### Metronome (Stripe)
**Type:** High-volume usage metering and rating engine, acquired by Stripe
Metronome was the most searched usage-based billing platform globally in August 2026, with 32.8% share of search [citation:9]. It specializes in high-volume event rating and pricing logic, making it a strong choice when the difficult part is turning raw usage into billable line items [citation:3]. Stripe acquired Metronome to bring real-time metering into its billing stack [citation:1][citation:15]. **Important consideration:** Metronome is now one engine inside Stripe, so the meter and billing are two systems mid-integration rather than a single native record [citation:1]. Enterprise pricing with no published figures.
**Best for:** Teams already deeply in the Stripe ecosystem with complex rating requirements, accepting that metering and billing may be separate layers.

### Orb (Adyen)
**Type:** Multi-dimensional pricing and invoice detail, acquired by Adyen
Orb was known for compelling multi-dimensional pricing and detailed invoice line items [citation:3]. Adyen acquired Orb for a reported $335 million (closed July 2026), with multi-PSP support continuing "initially" [citation:15]. **Consideration:** The acquisition introduces uncertainty about processor neutrality — Orb's independence as a neutral metering layer is now contingent on Adyen's strategy.
**Best for:** Organizations wanting rich pricing dimensions and invoice transparency, with awareness of the Adyen ownership context.

### m3ter (Salesforce)
**Type:** Metering and rating for Salesforce/ERP stacks, acquired by Salesforce
m3ter specializes in the middle layer between raw usage and downstream systems — normalizing usage, applying rates, and handing clean data to CRM and ERP [citation:3]. Salesforce completed its acquisition in July 2026, with plans to integrate m3ter's high-volume metering into Agentforce Revenue Management [citation:3]. Pricing combines a core platform fee with add-ons for capacity, integrations, and implementation.
**Best for:** Enterprises already anchored in Salesforce and ERP stacks where the usage layer is the missing piece between contract and invoice.

### Amberflo
**Type:** High-frequency event metering with cost governance
Amberflo is the notable **corporately independent** commercial vendor remaining after the 2026 acquisition wave [citation:15]. It is strongest when accurate event-level metering is the first problem — metering tokens, API calls, GPU seconds, and custom events, then applying pricing and generating invoices [citation:3]. The architecture is metering-first, with customer-level cost visibility alongside billing. Pricing is usage-based tied to event ingestion volume and invoiced amount, quote-only.
**Best for:** AI and API products needing current, attributable usage data first, with billing built directly on top and no acquisition-related uncertainty today.

### Togai (Zuora)
**Type:** Visual pricing configuration, absorbed by Zuora
Togai emphasized pricing configurability without code, with a visual price plan builder supporting 100+ configurations and a rules engine for custom billing logic [citation:14]. Zuora absorbed Togai, folding its capabilities into the enterprise billing incumbent's platform [citation:1].
**Best for:** Product and finance teams wanting no-code pricing configuration, within the Zuora ecosystem.

### Chargebee Usage Billing
**Type:** Hybrid subscription-plus-usage within Chargebee suite
Chargebee provides usage billing as part of its broader subscription management platform, supporting hybrid models that blend base subscriptions with metered charges, credits, and overages on a single invoice [citation:1]. It is strongest when subscription logic is the core and usage layers on top, rather than usage-first architecture.
**Best for:** Existing Chargebee customers wanting usage billing without adopting a separate metering vendor.

### Zuora
**Type:** Enterprise monetization with usage rating and revenue recognition
Zuora is the enterprise incumbent for subscription and usage billing, with deep revenue recognition (ASC 606/IFRS 15), multi-entity structures, and CPQ workflows [citation:14]. It is built for large organizations with complex billing operations and dedicated RevOps teams. Implementation timelines span months, not days.
**Best for:** Large enterprises needing usage rating integrated with revenue recognition and multi-entity billing.

---

## 🟩 Open-Source Software

Self-hosted, community-driven SaaS Usage and Metering Analytics tools. The open-source ecosystem is anchored by **OpenMeter** (Apache 2.0, acquired by Kong) and **Lago** (AGPL), with newer entrants targeting developer experience.

### OpenMeter
**Stack:** Go / PostgreSQL / ClickHouse / Kafka | **License:** Apache-2.0
OpenMeter is the leading open-source metering and billing engine for AI, API, and DevTool monetization, now part of Kong [citation:2][citation:15]. It ingests CloudEvents, defines meters with flexible aggregations (SUM, COUNT, AVG, MIN, MAX), and connects usage to billing, entitlements, and customer dashboards [citation:2]. Key capabilities include usage-based billing with tiered/graduated/flat-fee pricing, **prepaid credits** with priority-based burn-down, a customer portal for self-service usage visibility, and **first-class LLM token cost tracking** [citation:2]. Architecture uses Kafka for streaming, ClickHouse for real-time aggregation, and PostgreSQL for billing [citation:2]. Deploys via Docker Compose or Kubernetes Helm chart. **Important:** Releases are beta and can include breaking changes, though the metering engine has run in production for years processing billions of events [citation:6].
**Best for:** Teams wanting a genuinely open-source (Apache 2.0) metering engine with real-time aggregation, prepaid credits, and LLM token tracking, accepting beta-stage release stability.

### Lago
**Stack:** Ruby / PostgreSQL / Redis / ClickHouse | **License:** AGPL-3.0
Lago is the most established open-source usage metering and billing platform, with 6,983+ GitHub stars [citation:8]. It ingests events via REST, batch API, or streaming connectors (Kafka, Kinesis, S3), aggregates them into billable metrics using seven aggregation types (COUNT, COUNT UNIQUE, LATEST, MAX, SUM, WEIGHTED SUM, CUSTOM), and applies plan pricing [citation:10]. It handles **late events** by assigning them to the correct billing period using the event's own timestamp, and **deduplicates on transaction_id** so retried events are never double-billed [citation:10]. Supports hybrid plans combining subscriptions with usage, prepaid credits, and usage allowances. **Trade-off:** AGPL licensing and the operational burden of running the full stack.
**Best for:** Teams wanting a proven, feature-rich open-source billing engine with genuine usage metering and hybrid pricing, accepting AGPL obligations and operational overhead.

### Flexprice
**Stack:** Go / TypeScript / Docker | **License:** AGPL-3.0
Flexprice is an open-source usage-based pricing and billing platform for developers, with 6,883+ GitHub stars and active development [citation:13]. It provides real-time usage metering, credits and top-ups, feature access control, a no-code UI, and cloud or self-hosted deployment. SDKs are available for Python, Go, and JavaScript, along with an MCP server for AI agent integration [citation:13]. Positioned as a developer-friendly alternative with a modern Go backend.
**Best for:** Developers wanting a modern, actively developed open-source metering platform with SDKs and a no-code UI, accepting AGPL licensing.

### Lotus
**Stack:** Python / Docker | **License:** Open Source (per project)
Lotus (uselotus/lotus) is an open-source pricing and packaging infrastructure platform with 1,727+ GitHub stars, positioned as a foundation for usage-based pricing [citation:8]. It provides the pricing and packaging layer, with usage tracking and subscription management capabilities. Less established than OpenMeter or Lago, but active in the open-source billing ecosystem.
**Best for:** Teams exploring open-source pricing infrastructure as an alternative foundation to OpenMeter or Lago, with awareness of a smaller ecosystem.

---

## 📊 Comparison at a Glance

| Software | License | Stack | Real-Time Metering | Prepaid Credits | LLM Token Tracking | Self-Hosted | Best For |
|----------|---------|-------|-------------------|-----------------|-------------------|-------------|----------|
| **Metronome** | Proprietary | Cloud | ✅ High-volume | (Check) | (Check) | ❌ | Stripe ecosystem rating |
| **Orb** | Proprietary | Cloud | ✅ Multi-dimensional | (Check) | (Check) | ❌ | Adyen ecosystem pricing |
| **m3ter** | Proprietary | Cloud | ✅ Rating focus | (Check) | ❌ | ❌ | Salesforce/ERP middle layer |
| **Amberflo** | Proprietary | Cloud | ✅ Event-first | ✅ | ✅ | ❌ | Independent metering-first |
| **Chargebee** | Proprietary | Cloud | (Add-on) | ✅ | (Via events) | ❌ | Existing Chargebee users |
| **OpenMeter** | Apache-2.0 | Go/ClickHouse | ✅ Real-time | ✅ Burn-down | ✅ First-class | ✅ | OSS metering + LLM |
| **Lago** | AGPL-3.0 | Ruby/Postgres | ✅ Real-time | ✅ | (Via events) | ✅ | Proven OSS billing |
| **Flexprice** | AGPL-3.0 | Go/TypeScript | ✅ Real-time | ✅ | (Check) | ✅ | Developer-friendly OSS |

---

## 🤝 Contributing

Contributions are welcome! If you know of an open-source SaaS Usage or Metering Analytics tool that should be listed here, please open a pull request with:

- Project name and URL
- Brief description (1–2 sentences)
- Stack and license
- Why it stands out

Please ensure the project is actively maintained (releases within the last 12 months) and genuinely open-source. Note that the **commercial landscape shifted dramatically in 2026**: the major independent metering vendors were acquired — Stripe took Metronome, Salesforce took m3ter, Adyen took Orb, and Kong took OpenMeter [citation:1][citation:15]. This makes **licence independence** the most durable form of control: OpenMeter (Apache 2.0) and Lago (AGPL) cannot be revoked by acquisition, even if their commercial stewards change [citation:15]. OpenMeter is the strongest choice for AI/LLM token metering with first-class support [citation:2][citation:6], while Lago offers the most mature open-source billing engine with proven deduplication and late-event handling [citation:10]. Amberflo remains the notable independent commercial option for metering-first architectures [citation:15].

---

## 📄 License

This list is released under CC0 1.0 Universal (Public Domain). The software projects listed retain their respective licenses.

---

⭐ **If this list helped you discover a useful tool, please star the repo!** ⭐

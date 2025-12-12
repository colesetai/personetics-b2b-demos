# Vision to MVP Roadmap

**Version:** 1.3 | **Date:** December 2025 | **Status:** Strategic Guide

---

## 🎯 Vision

> **Give every banker the ability to understand any customer in seconds, not minutes.**

---

## 🏛️ Three Pillars → Products

| Pillar | What It Delivers | Primary Product |
|--------|-----------------|-----------------|
| **Preparation** | Customer context before interactions | Banker Intelligence Suite |
| **Recommendation** | AI-driven next-best-actions | PrimacyEdge Platform |
| **Explanation** | Plain language "why" answers | GenAI Enhancement Layer |

---

## ☁️ Delivery Platform: Salesforce

**All MVP capabilities delivered via Salesforce Financial Services Cloud.**

| Aspect | Approach |
|--------|----------|
| **UI** | Salesforce native (Lightning components, related lists) |
| **Data** | Pushed to Salesforce custom objects via managed package |
| **Custom FE** | ❌ Not required |

---

## 🚀 MVP Scope (Salesforce)

### Phase 1a: True MVP (First)
| Capability | Data Source | Status | Rationale |
|------------|-------------|--------|-----------|
| **Primacy Indicators (40+)** | Primacy Indicators | ✅ Available | Highest revenue potential ($15-50M), unique differentiator |

### Phase 1b: Fast Follow
| Capability | Data Source | Status | Rationale |
|------------|-------------|--------|-----------|
| **Consumer Insights Mirror** | Insight Engine | ✅ Available | Aligns banker with customer |
| **Customer Snapshot** | EDM | ✅ Available | Foundation for context |

### Phase 2: Expansion
| Capability | Data Source | Status | Rationale |
|------------|-------------|--------|-----------|
| Income & Spending Trends | EDM | ✅ Available | Enhances conversations |
| External Relationships | External Relationships Model | ✅ Available | Competitive visibility |
| Daily Call Sheet | Insight Engine | ✅ Available | Workflow optimization (view on insights) |

### Future
| Capability | Status | Rationale |
|------------|--------|-----------|
| PRISM Score (aggregated) | ❌ Not yet available | Awaiting data availability |
| GenAI Explainers | Phase 3 | Enhancement layer |
| Next-Best-Action | Phase 3 | Requires GenAI |

> **Principle:** "Better to do ONE thing properly." — Start with Primacy Indicators (highest revenue), prove value, then expand.

---

## 📦 Top 3 Sellable Products

| Rank | Product | Bank Revenue | GenAI Required |
|------|---------|-------------|----------------|
| #1 | **PrimacyEdge Platform** | $15-50M | ❌ No |
| #2 | **Banker Intelligence Suite** | $5-15M | ❌ No |
| #3 | **Contact Center Suite** | $2-8M | ❌ No |

→ Details: [Top_3_Sellable_Products_Strategy.md](./Top_3_Sellable_Products_Strategy.md)

---

## 📅 Phased Approach

```
Phase 1a (MVP)          Phase 1b (Fast Follow)    Phase 2              Phase 3 (GenAI)
────────────────────    ──────────────────────    ──────────────────   ──────────────────
• Primacy Indicators    • Insights Mirror         • Trends             • GenAI Explainers
  (40+)                 • Customer Snapshot       • External Rels      • Next-Best-Action
                                                  • Daily Call Sheet   • PRISM Score
                                                                       • Marketing Cloud

Salesforce FSC          +4-6 weeks                +8-12 weeks          TBD
4-6 weeks            
```

→ Strategy: [Strategic_Guidance_Salesforce_GenAI.md](./Strategic_Guidance_Salesforce_GenAI.md)

---

## 🧭 Strategic Principles

From conversation with Einat (Dec 2025):

| Principle | Guidance |
|-----------|----------|
| **Start small** | One polished integration first |
| **Plugin positioning** | Enrich existing systems, don't replace |
| **Salesforce focus** | Align with AgentForce direction |
| **Discipline** | "Better to do ONE thing properly" |

---

## 🎯 RM Priority Framework (MVP Prioritization)

*Source: Research conversation, December 2025*

> **"RMs do not lack motivation. They lack signal clarity."**

### RM Priority Hierarchy

All MVP features should align to this priority order:

| Priority | RM Goal | MVP Feature Focus |
|----------|---------|-------------------|
| **#1 Retention** | Retain existing customers (non-negotiable) | Primacy Risk Alerts, At-Risk Signals, Churn Detection |
| **#2 Growth** | Grow existing relationships | Deposit Consolidation, Cross-Sell Opportunities, Credit Usage Signals |
| **#3 Acquisition** | Acquire new customers | Lower priority, often separate roles |

### What RMs Need (Not Dashboards)

| Need | Description | MVP Feature |
|------|-------------|-------------|
| **Which customers need attention now?** | Prioritized, actionable list | Daily Call Sheet (B-17) |
| **Who is quietly disengaging?** | Early warning signals | Primacy Risk Alerts (B-05) |
| **Where is real growth potential?** | Concrete signals, not noise | Deposit Consolidation (B-07) |

### Design Principle

> **Dashboards show data. We deliver decisions.**
> - Who to call
> - Why to call them
> - What to discuss

This principle should guide all feature design and prioritization.

---

## 🔗 Primacy Indicators = Signal Clarity Engine

The 40+ Primacy Indicators are the foundation that solves the RM signal clarity gap:

| Indicator Category | What It Detects | RM Priority |
|--------------------|-----------------|-------------|
| **Deposit behavior** | Outflows, balance drops | #1 Retention |
| **Salary stability** | Payroll changes, income shifts | #1 Retention |
| **Competitive leakage** | External institution activity | #1 Retention |
| **Transaction flows** | Spending pattern changes | #2 Growth |
| **Engagement patterns** | App usage, login frequency | Both |
| **External relationships** | Money going to competitors | #1 Retention |

### How Primacy Indicators Enable RM Needs

```
Primacy Indicators (40+)          →  Signals
         ↓
PRISM Score                       →  Aggregated risk/opportunity score
         ↓
Features (B-05, B-07, B-17...)    →  Actions for RMs
         ↓
"Who to call, why, what to discuss"
```

### Why Phase 1a (Primacy Indicators) Is the Right MVP

1. **Foundation** - Enables all four RM capabilities
2. **Revenue** - Highest potential ($15-50M)
3. **Differentiation** - Competitors don't have this
4. **Signal Clarity** - Directly solves the core RM problem

---

## 🔗 Related Documents

| Document | Purpose |
|----------|---------|
| [Banker_Products_Core.md](./Banker_Products_Core.md) | Full vision & pillars |
| [Top_3_Sellable_Products_Strategy.md](./Top_3_Sellable_Products_Strategy.md) | Revenue analysis & MVP details |
| [Strategic_Guidance_Salesforce_GenAI.md](./Strategic_Guidance_Salesforce_GenAI.md) | Partnership & go-to-market |
| [Salesforce SOW](../07_Integrations/Salesforce_CRM_Insights_SOW_Overview.md) | Integration implementation |

---

**Owner:** Director of AI Product Management

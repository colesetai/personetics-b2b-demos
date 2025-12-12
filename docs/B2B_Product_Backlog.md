# B2B Product Backlog for Banking Personas
## Bankers | Tellers | RMs | Commercial RMs | Contact Center Agents | Bank Product Teams

**Version:** 1.0  
**Date:** December 2026  
**Owner:** Director of AI Product Management  
**Status:** Draft for Review

---

# Table of Contents

1. [Executive Summary](#executive-summary)
2. [Strategic Architecture Questions](#strategic-architecture-questions)
3. [Full Backlog Table](#full-backlog-table)
4. [Summary by Persona and Priority](#summary-by-persona-and-priority)
5. [P0 Executive View](#p0-executive-view)
6. [Pivot Table: Priority → Persona](#pivot-table-priority--persona)
7. [2x2 Priority vs Excitement Matrix](#2x2-priority-vs-excitement-matrix)
8. [2x2 Value vs Effort Matrix](#2x2-value-vs-effort-matrix)
9. [Recommended Roadmap Path](#recommended-roadmap-path)
10. [Capability Mapping](#capability-mapping)

---

# Executive Summary

## RM Priority Framework

*Source: Research conversation, December 2025*

> **"RMs do not lack motivation. They lack signal clarity."**

### RM Priority Hierarchy (Shapes All Feature Prioritization)

| Priority | Goal | Non-Negotiable? |
|----------|------|-----------------|
| **#1** | Retain existing customers | Yes. Losing a good commercial client is a failure. |
| **#2** | Grow existing relationships | Main way RMs hit targets. |
| **#3** | Acquire new customers | Secondary. Often separate hunting roles. |

### What RMs Cannot Answer Today

1. **Which customers need attention right now?**
2. **Who is quietly disengaging?**
3. **Where is there real growth potential, not just noise?**

### MVP Design Principle

> **Dashboards show data. We deliver decisions.**
> - Who to call
> - Why to call them
> - What to discuss

### Feature Alignment to RM Priorities

| RM Priority | Features That Deliver |
|-------------|----------------------|
| **#1 Retention** | B-05 (Primacy Risk Alerts), B-15 (Competitive Intelligence), CC-05 (At-Risk Alert) |
| **#2 Growth** | B-07 (Deposit Consolidation), B-14 (Proactive Outreach), B-11 (Cross-Sell Score) |
| **#1 + #2** | B-17 (Daily Call Sheet), B-04 (Next-Best-Action), B-18 (Conversation Starters) |

---

## Strategic Overview

This backlog defines **60 product capabilities** for B2B banking personas, designed to:
- Reduce banker preparation time from **15 minutes to 15 seconds**
- Increase cross-sell conversion through AI-powered opportunity detection
- Prevent churn through proactive primacy intelligence
- Enable self-service insight creation for bank product teams
- Deliver real-time customer context across all banker touchpoints
- Provide **daily call sheets** for structured sales workflows
- Offer **CEO dashboards** for executive visibility into portfolio health

## Key Metrics

| Metric | Current State | Target State |
|--------|--------------|--------------|
| Time to understand customer | 15+ minutes | < 15 seconds |
| Cross-sell opportunity detection | Manual | Automated + Explained |
| Churn prediction accuracy | Limited | 85%+ (PRISM-powered) |
| Insight creation time | Days/weeks | Hours |
| Banker confidence in recommendations | Low | High (explainable AI) |

## Investment Thesis

**93% of items leverage existing Personetics capabilities** (EDM, Insight Engine, PrimacyEdge, PRISM, MCP, BAIQS). This backlog prioritizes:

1. **Quick Wins** (High Value, Low Effort) — 14 items, immediate ROI
2. **Strategic Bets** (High Value, High Effort) — 22 items, competitive moat
3. **Foundation Items** (Lower Value, Low Effort) — 12 items, platform enablers
4. **Future Vision** (Lower Value, High Effort) — 10 items, 2027+ roadmap

*Note: Items B-17, B-18, B-19, EX-01 added based on Scott McQuilkin's feedback from prior banker project*

## Roadmap Summary

| Phase | Timeline | Focus | Key Deliverables |
|-------|----------|-------|------------------|
| **Phase 1** | Q1-Q2 | Foundation + Quick Wins | Customer Snapshot, Real-time Context, Basic NBA |
| **Phase 2** | Q2-Q3 | AI Intelligence Layer | GenAI Explainability, Opportunity Engine, PRISM Integration |
| **Phase 3** | Q3-Q4 | Scale + Advanced AI | Multi-channel, B2A2C, Commercial RM Suite |
| **Phase 4** | 2027+ | Visionary | Predictive Workflows, Autonomous Agents |

---

# Strategic Architecture Questions

## ⚠️ Critical Decisions Required Before Implementation

### 1. Engage Insights: Consumer vs. Banker

**Context:** Personetics Engage insights are designed for **end-consumers** (retail banking customers). They receive these insights in their mobile/web banking apps.

**Key Questions:**

| Question | Options | Implications |
|----------|---------|--------------|
| **Should bankers see the same insights the consumer received?** | Yes / No / Subset | If Yes: Enables banker to reference what customer saw, builds trust. Requires surfacing consumer insight history to banker interface. |
| **Should we create banker-specific insights?** | Yes / No | If Yes: New insight logic needed, different triggers, different actions. Bankers need operational insights (e.g., "Customer hasn't logged in for 30 days") vs. consumer insights (e.g., "Your spending increased"). |
| **If banker insights: Same tech stack or different?** | Engage Engine / New Engine / Hybrid | Same: Leverage existing investment, faster. New: Optimized for banker workflows, different cadence, different logic. |
| **API approach: New APIs or MCP/Tools?** | New APIs / MCP Server + Tools / Both | MCP: Aligns with agentic architecture, flexible, enables bank customization. New APIs: Traditional integration, may be required for CRM embedding. |

**Recommendation Framework:**

```
┌─────────────────────────────────────────────────────────────────────┐
│                    BANKER INSIGHT STRATEGY                          │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│  OPTION A: "Mirror Mode"                                            │
│  ─────────────────────                                              │
│  • Expose consumer Engage insights to banker                        │
│  • Banker sees what customer saw                                    │
│  • No new insight logic                                             │
│  • Implementation: API to fetch customer's insight history          │
│  • Effort: LOW                                                      │
│                                                                     │
│  OPTION B: "Banker-Native Insights"                                 │
│  ─────────────────────────────────                                  │
│  • Create new insight types for bankers                             │
│  • Different triggers (portfolio-level, operational)                │
│  • Uses Engage Engine with banker-specific rules                    │
│  • Implementation: New insight definitions in Engagement Builder    │
│  • Effort: MEDIUM                                                   │
│                                                                     │
│  OPTION C: "MCP-Powered Intelligence"                               │
│  ────────────────────────────────────                               │
│  • Build banker intelligence as MCP tools                           │
│  • Dynamic, conversational, real-time                               │
│  • No pre-generated insights, on-demand analysis                    │
│  • Implementation: MCP Server + Tools + EDM grounding               │
│  • Effort: MEDIUM-HIGH                                              │
│                                                                     │
│  OPTION D: "Hybrid" (RECOMMENDED)                                   │
│  ────────────────────────────────                                   │
│  • Mirror consumer insights (Option A) +                            │
│  • MCP-powered real-time intelligence (Option C)                    │
│  • Best of both: context + flexibility                              │
│  • Implementation: API for insight history + MCP for analysis       │
│  • Effort: MEDIUM                                                   │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

**Impact on Backlog Items:**

| Item | If Option A | If Option B | If Option C | If Option D |
|------|-------------|-------------|-------------|-------------|
| B-01 Customer Snapshot | Includes insight list | Includes banker insights | Dynamic MCP query | Both |
| CC-03 Insight Explainer | Explains consumer insights | Explains banker insights | MCP explains on-demand | Both |
| B-10 Conversational Q&A | Limited | Limited | Core capability | Core capability |

---

### 2. PRISM / PrimacyEdge Availability

**Context:** 
- **PRISM** = Primacy Score (AI model output) — a score each consumer gets based on financial indicators
- **PrimacyEdge** = The product offering that includes PRISM + External Relationships Model + 40+ Indicators
- **Status:** ⚠️ **NOT YET AVAILABLE** — planned for 2026 productization

**Backlog Impact:**

| Item | PRISM/PrimacyEdge Dependency | Risk | Mitigation |
|------|------------------------------|------|------------|
| B-05 | Primacy Risk Alerts | HIGH | Requires PRISM scores to function |
| B-06 | External Financial Relationships | HIGH | Requires External Relationships Model |
| B-07 | Deposit Consolidation Detector | HIGH | Requires primacy indicators |
| CC-05 | At-Risk Customer Alert | HIGH | Requires PRISM score |
| B-13 | Customer Health Score | MEDIUM | Can work with partial indicators |
| B-15 | Competitive Intelligence Alerts | HIGH | Requires External Relationships Model |
| BUD-02 | Priority Customer Identification | MEDIUM | Can use engagement signals initially |

**Recommendation:**
- **Phase 1** items dependent on PrimacyEdge should be **gated on PrimacyEdge availability**
- Build **fallback logic** using available EDM indicators for initial release
- Update roadmap to show PrimacyEdge as a **dependency milestone**

---

### 3. Summary: Decisions Needed

| # | Decision | Owner | Due Date | Options |
|---|----------|-------|----------|---------|
| 1 | Banker insight strategy (A/B/C/D) | CPO / Dir. AI PM | TBD | Mirror, Native, MCP, Hybrid |
| 2 | PrimacyEdge availability date | PrimacyEdge PM | TBD | Q1/Q2/Q3 2026 |
| 3 | MCP vs. API approach for CRM integration | Architecture | TBD | MCP-first, API-first, Both |
| 4 | Banker-specific insight definitions | Insight PM + Dir. AI PM | TBD | Use existing, Create new |

---

# Full Backlog Table

## Legend

| Field | Description |
|-------|-------------|
| **ID** | Unique identifier |
| **Pain** | Core problem being solved |
| **Value** | Business/user outcome |
| **Persona** | Primary user(s) |
| **Description** | Short capability summary |
| **Pain Category** | Problem domain |
| **Priority** | P0 (Critical) / P1 (High) / P2 (Medium) |
| **Excitement** | Must Have / Important / Visionary |
| **Value Score** | 1-10 (10 = highest business impact) |
| **Effort Score** | 1-10 (10 = highest development effort) |
| **Capabilities** | Existing Personetics capabilities leveraged |
| **Roadmap** | Recommended placement on Value/Effort 2x2 |

---

## Banker / Relationship Manager Items (B-01 to B-16)

### B-01: 15-Second Customer Snapshot
| Field | Value |
|-------|-------|
| **Pain** | Takes 15+ minutes to understand customer before meeting |
| **Value** | Instant customer understanding, higher banker confidence |
| **Persona** | Banker, RM |
| **Description** | AI-generated summary: key changes, primacy signals, opportunities, risks—all in one view |
| **Pain Category** | Meeting Preparation |
| **Priority** | P0 |
| **Excitement** | Must Have |
| **Value Score** | 10 |
| **Effort Score** | 5 |
| **Capabilities** | ✅ EDM, Insight Engine, PRISM, MCP Server |
| **Roadmap** | Quick Win |

---

### B-02: Income & Spending Trend Analysis
| Field | Value |
|-------|-------|
| **Pain** | Can't quickly see what changed in customer's financial life |
| **Value** | Visual trends enable informed conversations |
| **Persona** | Banker, RM |
| **Description** | Interactive trend views: income changes, spending patterns, anomaly detection |
| **Pain Category** | Information Gathering |
| **Priority** | P0 |
| **Excitement** | Must Have |
| **Value Score** | 9 |
| **Effort Score** | 4 |
| **Capabilities** | ✅ EDM, Insight Engine |
| **Roadmap** | Quick Win |

---

### B-03: GenAI "What Changed?" Explainer
| Field | Value |
|-------|-------|
| **Pain** | Hard to explain why customer's situation changed |
| **Value** | Natural language explanations build trust |
| **Persona** | Banker, RM |
| **Description** | GenAI explains recent changes: "Income dropped 15% due to fewer direct deposits" |
| **Pain Category** | Explanation & Trust |
| **Priority** | P0 |
| **Excitement** | Must Have |
| **Value Score** | 10 |
| **Effort Score** | 6 |
| **Capabilities** | ✅ EDM, MCP Server, BAIQS |
| **Roadmap** | Strategic Bet |

---

### B-04: Next-Best-Action Recommendations
| Field | Value |
|-------|-------|
| **Pain** | Don't know what to recommend or when |
| **Value** | AI-driven product suggestions increase conversion |
| **Persona** | Banker, RM |
| **Description** | Contextual recommendations: consolidation, savings, product adoption—with reasoning |
| **Pain Category** | Opportunity Identification |
| **Priority** | P0 |
| **Excitement** | Must Have |
| **Value Score** | 10 |
| **Effort Score** | 7 |
| **Capabilities** | ✅ Insight Engine, PRISM, Segmentation |
| **Roadmap** | Strategic Bet |

---

### B-05: Primacy Risk Alerts
| Field | Value |
|-------|-------|
| **Pain** | Can't identify which customers are at risk of leaving |
| **Value** | Proactive retention before churn happens |
| **Persona** | Banker, RM |
| **Description** | Real-time alerts when PRISM score detects competitive leakage or primacy decline |
| **Pain Category** | Customer Retention |
| **Priority** | P0 |
| **Excitement** | Must Have |
| **Value Score** | 10 |
| **Effort Score** | 5 |
| **Capabilities** | ⏳ PrimacyEdge (PRISM score), Workflows |
| **Roadmap** | Quick Win |
| **⚠️ Dependency** | **Requires PrimacyEdge availability (PRISM score not yet available)** |

---

### B-06: External Financial Relationships View
| Field | Value |
|-------|-------|
| **Pain** | No visibility into customer's external banking activity |
| **Value** | Understand full financial picture, identify consolidation opps |
| **Persona** | Banker, RM |
| **Description** | PrimacyEdge-powered view showing external institution signals (external relationships model) |
| **Pain Category** | Opportunity Identification |
| **Priority** | P0 |
| **Excitement** | Must Have |
| **Value Score** | 9 |
| **Effort Score** | 4 |
| **Capabilities** | ⏳ PrimacyEdge (External Relationships Model), EDM |
| **Roadmap** | Quick Win |
| **⚠️ Dependency** | **Requires PrimacyEdge availability (External Relationships Model)** |

---

### B-07: Deposit Consolidation Opportunity Detector
| Field | Value |
|-------|-------|
| **Pain** | Missing opportunities to grow deposits |
| **Value** | Automated identification of consolidation targets |
| **Persona** | Banker, RM |
| **Description** | AI identifies customers with external deposits likely to consolidate (uses primacy indicators) |
| **Pain Category** | Revenue Growth |
| **Priority** | P0 |
| **Excitement** | Must Have |
| **Value Score** | 9 |
| **Effort Score** | 5 |
| **Capabilities** | ⏳ PrimacyEdge (Primacy Indicators), Insight Engine, Segmentation |
| **Roadmap** | Quick Win |
| **⚠️ Dependency** | **Requires PrimacyEdge availability (Primacy Indicators)** |

---

### B-08: Meeting Preparation Summary
| Field | Value |
|-------|-------|
| **Pain** | Scrambling to prepare before customer meetings |
| **Value** | Structured prep reduces cognitive load |
| **Persona** | Banker, RM |
| **Description** | Auto-generated meeting brief: key talking points, opportunities, recent changes |
| **Pain Category** | Meeting Preparation |
| **Priority** | P1 |
| **Excitement** | Important |
| **Value Score** | 8 |
| **Effort Score** | 5 |
| **Capabilities** | ✅ EDM, MCP Server, BAIQS |
| **Roadmap** | Quick Win |

---

### B-09: CRM-Embedded Intelligence Panel
| Field | Value |
|-------|-------|
| **Pain** | Switching between CRM and analytics tools wastes time |
| **Value** | Intelligence in the banker's existing workflow |
| **Persona** | Banker, RM |
| **Description** | Salesforce/Dynamics embedded panel with customer context + recommendations |
| **Pain Category** | Operational Efficiency |
| **Priority** | P1 |
| **Excitement** | Important |
| **Value Score** | 8 |
| **Effort Score** | 6 |
| **Capabilities** | ✅ MCP Server, MCP Tools |
| **Roadmap** | Strategic Bet |

---

### B-10: Conversational Q&A About Customer
| Field | Value |
|-------|-------|
| **Pain** | Can't ask questions about customer in natural language |
| **Value** | "Why did spending increase?" answered in seconds |
| **Persona** | Banker, RM |
| **Description** | GenAI chat interface to query customer data conversationally |
| **Pain Category** | Information Gathering |
| **Priority** | P1 |
| **Excitement** | Important |
| **Value Score** | 8 |
| **Effort Score** | 7 |
| **Capabilities** | ✅ MCP Server, EDM, BAIQS |
| **Roadmap** | Strategic Bet |

---

### B-11: Cross-Sell Opportunity Score
| Field | Value |
|-------|-------|
| **Pain** | Hard to prioritize which products to recommend |
| **Value** | Data-driven product matching increases conversion |
| **Persona** | Banker, RM |
| **Description** | AI-scored opportunities ranked by likelihood to convert |
| **Pain Category** | Revenue Growth |
| **Priority** | P1 |
| **Excitement** | Important |
| **Value Score** | 8 |
| **Effort Score** | 6 |
| **Capabilities** | ✅ Insight Engine, Segmentation, PRISM |
| **Roadmap** | Strategic Bet |

---

### B-12: Post-Meeting Summary Generator
| Field | Value |
|-------|-------|
| **Pain** | Manual note-taking and CRM updates after meetings |
| **Value** | Automated documentation, better follow-through |
| **Persona** | Banker, RM |
| **Description** | GenAI generates meeting summary, action items, follow-up recommendations |
| **Pain Category** | Operational Efficiency |
| **Priority** | P2 |
| **Excitement** | Important |
| **Value Score** | 7 |
| **Effort Score** | 6 |
| **Capabilities** | ✅ MCP Server, BAIQS |
| **Roadmap** | Foundation |

---

### B-13: Customer Health Score Dashboard
| Field | Value |
|-------|-------|
| **Pain** | No single metric for customer relationship health |
| **Value** | Quick prioritization of customer portfolio |
| **Persona** | Banker, RM |
| **Description** | Composite score combining engagement, primacy, activity, and opportunity signals |
| **Pain Category** | Customer Engagement |
| **Priority** | P1 |
| **Excitement** | Important |
| **Value Score** | 7 |
| **Effort Score** | 5 |
| **Capabilities** | ✅ PrimacyEdge, PRISM, Insight Engine |
| **Roadmap** | Quick Win |

---

### B-14: Proactive Outreach Triggers
| Field | Value |
|-------|-------|
| **Pain** | Don't know when to reach out to customers |
| **Value** | Right-time engagement improves response rates |
| **Persona** | Banker, RM |
| **Description** | AI triggers alerts when optimal outreach moment detected (life event, opportunity) |
| **Pain Category** | Opportunity Identification |
| **Priority** | P1 |
| **Excitement** | Important |
| **Value Score** | 8 |
| **Effort Score** | 6 |
| **Capabilities** | ✅ Insight Engine, Workflows |
| **Roadmap** | Strategic Bet |

---

### B-15: Competitive Intelligence Alerts
| Field | Value |
|-------|-------|
| **Pain** | No visibility into competitor activity affecting my customers |
| **Value** | Proactive response to competitive threats |
| **Persona** | Banker, RM |
| **Description** | Alerts when customers show signs of competitor engagement (external relationships detected) |
| **Pain Category** | Customer Retention |
| **Priority** | P1 |
| **Excitement** | Important |
| **Value Score** | 8 |
| **Effort Score** | 5 |
| **Capabilities** | ⏳ PrimacyEdge (External Relationships Model) |
| **Roadmap** | Quick Win |
| **⚠️ Dependency** | **Requires PrimacyEdge availability** |

---

### B-16: Personalized Email Drafts
| Field | Value |
|-------|-------|
| **Pain** | Writing personalized customer emails takes time |
| **Value** | Faster outreach with relevant context |
| **Persona** | Banker, RM |
| **Description** | GenAI drafts personalized email based on customer context and opportunity |
| **Pain Category** | Operational Efficiency |
| **Priority** | P2 |
| **Excitement** | Visionary |
| **Value Score** | 6 |
| **Effort Score** | 5 |
| **Capabilities** | ✅ MCP Server, BAIQS |
| **Roadmap** | Foundation |

---

### B-17: Daily Call Sheet / Prioritized Outreach List
| Field | Value |
|-------|-------|
| **Pain** | No structured daily view of who to call and why |
| **Value** | Optimized banker time, higher contact-to-conversion rates |
| **Persona** | Banker, RM |
| **Description** | Daily prioritized list: account name, top insight, insight count, sorted by opportunity/urgency. Enables structured sales and relationship-building workflow |
| **Pain Category** | Opportunity Identification |
| **Priority** | P0 |
| **Excitement** | Must Have |
| **Value Score** | 10 |
| **Effort Score** | 4 |
| **Capabilities** | ✅ Insight Engine, PRISM, Segmentation, Workflows |
| **Roadmap** | Quick Win |

*Source: Scott McQuilkin feedback from banker project*

---

### B-18: Conversation Starters / Talking Points
| Field | Value |
|-------|-------|
| **Pain** | Don't know how to open customer conversations meaningfully |
| **Value** | Higher engagement, relevant first touch |
| **Persona** | Banker, RM |
| **Description** | AI-generated conversation starters based on customer's recent insights, life events, and opportunities |
| **Pain Category** | During Interactions |
| **Priority** | P1 |
| **Excitement** | Important |
| **Value Score** | 8 |
| **Effort Score** | 4 |
| **Capabilities** | ✅ Insight Engine, EDM, MCP Server |
| **Roadmap** | Quick Win |

*Source: Scott McQuilkin feedback from banker project*

---

### B-19: Individual Customer Deep Dive with Chat
| Field | Value |
|-------|-------|
| **Pain** | Need to ask follow-up questions about specific customer |
| **Value** | Instant answers without system switching |
| **Persona** | Banker, RM |
| **Description** | Conversational interface to explore individual customer: "Why did their deposit change?" "What's their risk tolerance?" |
| **Pain Category** | Information Gathering |
| **Priority** | P1 |
| **Excitement** | Important |
| **Value Score** | 8 |
| **Effort Score** | 6 |
| **Capabilities** | ✅ MCP Server, EDM, BAIQS |
| **Roadmap** | Strategic Bet |

*Source: Scott McQuilkin feedback from banker project*

---

### B-20: Consumer Engage Insights Mirror (Banker View)
| Field | Value |
|-------|-------|
| **Pain** | Banker doesn't know what insights the consumer received in their app |
| **Value** | Aligned conversations—banker references what customer saw |
| **Persona** | Banker, RM, Contact Center Agent |
| **Description** | Show bankers the Engage insights the consumer received (same insights, banker-formatted). Enables "I see you received an alert about X..." conversations. |
| **Pain Category** | Information Gathering |
| **Priority** | P0 |
| **Excitement** | Must Have |
| **Value Score** | 9 |
| **Effort Score** | 4 |
| **Capabilities** | ✅ Insight Engine (read-only), EDM |
| **Roadmap** | Quick Win |
| **📝 Note** | **Uses existing Engage insights—no new insight logic needed. Requires API to fetch customer's insight history.** |

---

### B-21: Banker-Specific Operational Insights
| Field | Value |
|-------|-------|
| **Pain** | Bankers need different signals than consumers |
| **Value** | Relevant triggers for banker workflows (not consumer-facing) |
| **Persona** | Banker, RM |
| **Description** | Insights designed for bankers: "Customer hasn't logged in 30 days", "Large balance sitting in low-yield account", "Salary deposit stopped". Not shown to consumer. |
| **Pain Category** | Opportunity Identification |
| **Priority** | P1 |
| **Excitement** | Important |
| **Value Score** | 8 |
| **Effort Score** | 7 |
| **Capabilities** | ✅ Insight Engine (new insight definitions), EDM, Engagement Builder |
| **Roadmap** | Strategic Bet |
| **📝 Note** | **Requires decision: Use Engage Engine with banker-specific rules OR build MCP-powered on-demand analysis. See Strategic Architecture Questions.** |

---

## Executive / Leadership Items (EX-01 to EX-03)

### EX-01: CEO Dashboard – Customer Portfolio Health
| Field | Value |
|-------|-------|
| **Pain** | Executives lack high-level visibility into customer base health |
| **Value** | Strategic decision-making based on portfolio intelligence |
| **Persona** | Bank Executive, CEO |
| **Description** | Executive dashboard: primacy trends, churn risk distribution, opportunity pipeline, segment health metrics |
| **Pain Category** | Decision Making |
| **Priority** | P1 |
| **Excitement** | Important |
| **Value Score** | 8 |
| **Effort Score** | 6 |
| **Capabilities** | ✅ PrimacyEdge, PRISM, Segmentation, Data Quality |
| **Roadmap** | Strategic Bet |

*Source: Scott McQuilkin feedback from banker project*

---

### EX-02: Branch/Team Performance Analytics
| Field | Value |
|-------|-------|
| **Pain** | No visibility into how different teams leverage intelligence |
| **Value** | Optimize training, identify best practices |
| **Persona** | Bank Executive, Branch Manager |
| **Description** | Analytics on banker adoption, insight usage, conversion rates by team/branch |
| **Pain Category** | Measurement |
| **Priority** | P2 |
| **Excitement** | Important |
| **Value Score** | 6 |
| **Effort Score** | 5 |
| **Capabilities** | ✅ Data Quality, Workflows |
| **Roadmap** | Foundation |

---

### EX-03: Portfolio-Level Opportunity Sizing
| Field | Value |
|-------|-------|
| **Pain** | Can't quantify total opportunity across customer base |
| **Value** | Data-driven resource allocation and goal setting |
| **Persona** | Bank Executive |
| **Description** | Aggregate view of deposit consolidation potential, cross-sell pipeline, retention opportunity value |
| **Pain Category** | Decision Making |
| **Priority** | P2 |
| **Excitement** | Visionary |
| **Value Score** | 7 |
| **Effort Score** | 6 |
| **Capabilities** | ✅ PrimacyEdge, Insight Engine, Segmentation |
| **Roadmap** | Foundation |

---

## Contact Center Agent Items (CC-01 to CC-10)

### CC-01: Real-Time Customer Context Panel
| Field | Value |
|-------|-------|
| **Pain** | No context when customer calls—cold start every time |
| **Value** | Instant understanding during live calls |
| **Persona** | Contact Center Agent |
| **Description** | Live panel showing customer profile, recent activity, insights, alerts |
| **Pain Category** | Information Gathering |
| **Priority** | P0 |
| **Excitement** | Must Have |
| **Value Score** | 10 |
| **Effort Score** | 5 |
| **Capabilities** | ✅ EDM, Insight Engine, MCP Server |
| **Roadmap** | Quick Win |

---

### CC-02: Transaction Explanation Engine
| Field | Value |
|-------|-------|
| **Pain** | Can't explain unfamiliar transactions to customers |
| **Value** | Confident answers reduce call escalations |
| **Persona** | Contact Center Agent |
| **Description** | GenAI explains any transaction: merchant, category, pattern, anomaly flag |
| **Pain Category** | During Interactions |
| **Priority** | P0 |
| **Excitement** | Must Have |
| **Value Score** | 9 |
| **Effort Score** | 4 |
| **Capabilities** | ✅ EDM, MCP Server, BAIQS |
| **Roadmap** | Quick Win |

---

### CC-03: Insight Trigger Explainer
| Field | Value |
|-------|-------|
| **Pain** | Customer asks "why did I get this alert?" and agent can't explain |
| **Value** | Trust-building through transparent explanations |
| **Persona** | Contact Center Agent |
| **Description** | GenAI explains why any insight was triggered for this customer |
| **Pain Category** | Explanation & Trust |
| **Priority** | P0 |
| **Excitement** | Must Have |
| **Value Score** | 9 |
| **Effort Score** | 5 |
| **Capabilities** | ✅ Insight Engine, MCP Server, BAIQS |
| **Roadmap** | Quick Win |

---

### CC-04: Suggested Response Scripts
| Field | Value |
|-------|-------|
| **Pain** | Difficult conversations with angry or confused customers |
| **Value** | Consistent, compliant responses reduce stress |
| **Persona** | Contact Center Agent |
| **Description** | AI-suggested phrasing for common scenarios, compliant and contextual |
| **Pain Category** | During Interactions |
| **Priority** | P1 |
| **Excitement** | Important |
| **Value Score** | 7 |
| **Effort Score** | 5 |
| **Capabilities** | ✅ MCP Server, BAIQS |
| **Roadmap** | Quick Win |

---

### CC-05: At-Risk Customer Alert
| Field | Value |
|-------|-------|
| **Pain** | No warning when talking to high-churn-risk customer |
| **Value** | Opportunity to save relationship during interaction |
| **Persona** | Contact Center Agent |
| **Description** | Visual alert when customer has elevated churn risk (based on PRISM primacy score) |
| **Pain Category** | Customer Retention |
| **Priority** | P0 |
| **Excitement** | Must Have |
| **Value Score** | 8 |
| **Effort Score** | 3 |
| **Capabilities** | ⏳ PrimacyEdge (PRISM score) |
| **Roadmap** | Quick Win |
| **⚠️ Dependency** | **Requires PrimacyEdge availability (PRISM score not yet available)** |

---

### CC-06: Quick Q&A Knowledge Base
| Field | Value |
|-------|-------|
| **Pain** | Searching multiple systems for answers during calls |
| **Value** | Single source of truth reduces handle time |
| **Persona** | Contact Center Agent |
| **Description** | Conversational search across customer data, products, policies |
| **Pain Category** | Information Gathering |
| **Priority** | P1 |
| **Excitement** | Important |
| **Value Score** | 7 |
| **Effort Score** | 6 |
| **Capabilities** | ✅ MCP Server, MCP Tools |
| **Roadmap** | Strategic Bet |

---

### CC-07: Call Outcome Predictor
| Field | Value |
|-------|-------|
| **Pain** | No guidance on likely call resolution path |
| **Value** | Optimized call routing and preparation |
| **Persona** | Contact Center Agent |
| **Description** | AI predicts call intent and likely resolution based on customer profile |
| **Pain Category** | Operational Efficiency |
| **Priority** | P2 |
| **Excitement** | Visionary |
| **Value Score** | 6 |
| **Effort Score** | 7 |
| **Capabilities** | 🆕 Requires new development |
| **Roadmap** | Future Vision |

---

### CC-08: Upsell Opportunity Prompt
| Field | Value |
|-------|-------|
| **Pain** | Missing service-to-sales opportunities during calls |
| **Value** | Incremental revenue from inbound interactions |
| **Persona** | Contact Center Agent |
| **Description** | Contextual prompt when opportunity exists based on customer profile |
| **Pain Category** | Revenue Growth |
| **Priority** | P1 |
| **Excitement** | Important |
| **Value Score** | 7 |
| **Effort Score** | 4 |
| **Capabilities** | ✅ Insight Engine, Segmentation |
| **Roadmap** | Quick Win |

---

### CC-09: Post-Call Summary Auto-Generation
| Field | Value |
|-------|-------|
| **Pain** | Manual call logging reduces efficiency |
| **Value** | Automated documentation frees agent time |
| **Persona** | Contact Center Agent |
| **Description** | GenAI generates call summary for CRM from conversation context |
| **Pain Category** | Operational Efficiency |
| **Priority** | P2 |
| **Excitement** | Important |
| **Value Score** | 6 |
| **Effort Score** | 6 |
| **Capabilities** | ✅ MCP Server, BAIQS |
| **Roadmap** | Foundation |

---

### CC-10: Sentiment-Aware Guidance
| Field | Value |
|-------|-------|
| **Pain** | No real-time guidance when customer is frustrated |
| **Value** | Better handling of difficult conversations |
| **Persona** | Contact Center Agent |
| **Description** | AI detects sentiment and suggests de-escalation approaches |
| **Pain Category** | During Interactions |
| **Priority** | P2 |
| **Excitement** | Visionary |
| **Value Score** | 5 |
| **Effort Score** | 8 |
| **Capabilities** | 🆕 Requires new development |
| **Roadmap** | Future Vision |

---

## Commercial RM Items (CRM-01 to CRM-08)

### CRM-01: Business Cashflow Intelligence
| Field | Value |
|-------|-------|
| **Pain** | Limited visibility into SMB/commercial customer health |
| **Value** | Deeper understanding of business financial patterns |
| **Persona** | Commercial RM |
| **Description** | Business-specific cashflow analysis: seasonality, working capital, receivables |
| **Pain Category** | Information Gathering |
| **Priority** | P0 |
| **Excitement** | Must Have |
| **Value Score** | 9 |
| **Effort Score** | 7 |
| **Capabilities** | ✅ EDM, Insight Engine |
| **Roadmap** | Strategic Bet |

---

### CRM-02: Business Growth/Decline Indicators
| Field | Value |
|-------|-------|
| **Pain** | Can't predict which businesses are growing or struggling |
| **Value** | Proactive engagement based on trajectory |
| **Persona** | Commercial RM |
| **Description** | AI-detected growth/decline signals from transaction patterns |
| **Pain Category** | Opportunity Identification |
| **Priority** | P0 |
| **Excitement** | Must Have |
| **Value Score** | 9 |
| **Effort Score** | 6 |
| **Capabilities** | ✅ Insight Engine, Segmentation |
| **Roadmap** | Strategic Bet |

---

### CRM-03: Credit Risk Early Warning
| Field | Value |
|-------|-------|
| **Pain** | Credit issues surface too late |
| **Value** | Earlier intervention reduces defaults |
| **Persona** | Commercial RM |
| **Description** | Predictive signals for credit deterioration based on behavior changes |
| **Pain Category** | Risk Management |
| **Priority** | P1 |
| **Excitement** | Important |
| **Value Score** | 8 |
| **Effort Score** | 7 |
| **Capabilities** | ✅ Insight Engine, PRISM |
| **Roadmap** | Strategic Bet |

---

### CRM-04: Industry Benchmarking
| Field | Value |
|-------|-------|
| **Pain** | No context for how business compares to peers |
| **Value** | More relevant advice and recommendations |
| **Persona** | Commercial RM |
| **Description** | Compare customer metrics to industry peers (anonymized benchmarks) |
| **Pain Category** | Customer Engagement |
| **Priority** | P2 |
| **Excitement** | Visionary |
| **Value Score** | 6 |
| **Effort Score** | 8 |
| **Capabilities** | 🆕 Requires new development + Segmentation |
| **Roadmap** | Future Vision |

---

### CRM-05: Treasury/Cash Management Opportunities
| Field | Value |
|-------|-------|
| **Pain** | Missing treasury product cross-sell signals |
| **Value** | Higher product penetration in commercial relationships |
| **Persona** | Commercial RM |
| **Description** | AI detects opportunities for treasury products based on cashflow patterns |
| **Pain Category** | Revenue Growth |
| **Priority** | P1 |
| **Excitement** | Important |
| **Value Score** | 8 |
| **Effort Score** | 6 |
| **Capabilities** | ✅ Insight Engine, Segmentation |
| **Roadmap** | Strategic Bet |

---

### CRM-06: Multi-Entity Relationship View
| Field | Value |
|-------|-------|
| **Pain** | Fragmented view of complex business relationships |
| **Value** | Holistic understanding of commercial customer ecosystem |
| **Persona** | Commercial RM |
| **Description** | Unified view across related business entities and owners |
| **Pain Category** | Information Gathering |
| **Priority** | P1 |
| **Excitement** | Important |
| **Value Score** | 7 |
| **Effort Score** | 7 |
| **Capabilities** | ✅ EDM |
| **Roadmap** | Strategic Bet |

---

### CRM-07: Supplier/Vendor Analysis
| Field | Value |
|-------|-------|
| **Pain** | No insight into business supplier relationships |
| **Value** | Identify supply chain risks and opportunities |
| **Persona** | Commercial RM |
| **Description** | Analysis of payment patterns to suppliers for risk and opportunity signals |
| **Pain Category** | Risk Management |
| **Priority** | P2 |
| **Excitement** | Visionary |
| **Value Score** | 5 |
| **Effort Score** | 7 |
| **Capabilities** | ✅ EDM, Insight Engine |
| **Roadmap** | Future Vision |

---

### CRM-08: Loan Utilization Intelligence
| Field | Value |
|-------|-------|
| **Pain** | Limited visibility into how credit facilities are used |
| **Value** | Better portfolio management and upsell timing |
| **Persona** | Commercial RM |
| **Description** | Track and analyze credit line utilization patterns and triggers |
| **Pain Category** | Opportunity Identification |
| **Priority** | P1 |
| **Excitement** | Important |
| **Value Score** | 7 |
| **Effort Score** | 5 |
| **Capabilities** | ✅ EDM, Insight Engine |
| **Roadmap** | Quick Win |

---

## Teller Items (T-01 to T-06)

### T-01: Customer Quick View
| Field | Value |
|-------|-------|
| **Pain** | Limited context when customer approaches teller |
| **Value** | Personalized service from first moment |
| **Persona** | Teller |
| **Description** | Simplified customer snapshot: recent activity, alerts, opportunities |
| **Pain Category** | Information Gathering |
| **Priority** | P1 |
| **Excitement** | Important |
| **Value Score** | 7 |
| **Effort Score** | 3 |
| **Capabilities** | ✅ EDM, Insight Engine |
| **Roadmap** | Quick Win |

---

### T-02: Opportunity Handoff to RM
| Field | Value |
|-------|-------|
| **Pain** | Spotted opportunities but no easy way to refer to RM |
| **Value** | Higher lead quality for RMs |
| **Persona** | Teller |
| **Description** | One-click handoff of detected opportunity to RM with context |
| **Pain Category** | Opportunity Identification |
| **Priority** | P1 |
| **Excitement** | Important |
| **Value Score** | 6 |
| **Effort Score** | 4 |
| **Capabilities** | ✅ Workflows, Insight Engine |
| **Roadmap** | Quick Win |

---

### T-03: Product Eligibility Check
| Field | Value |
|-------|-------|
| **Pain** | Can't quickly verify if customer qualifies for products |
| **Value** | Faster service and accurate referrals |
| **Persona** | Teller |
| **Description** | Instant eligibility check for common products based on customer profile |
| **Pain Category** | During Interactions |
| **Priority** | P2 |
| **Excitement** | Important |
| **Value Score** | 5 |
| **Effort Score** | 4 |
| **Capabilities** | ✅ EDM, Segmentation |
| **Roadmap** | Foundation |

---

### T-04: Transaction Pattern Alerts
| Field | Value |
|-------|-------|
| **Pain** | Miss unusual transaction patterns during service |
| **Value** | Proactive fraud prevention and customer protection |
| **Persona** | Teller |
| **Description** | Alert when transaction deviates from customer's normal pattern |
| **Pain Category** | Risk Management |
| **Priority** | P2 |
| **Excitement** | Important |
| **Value Score** | 6 |
| **Effort Score** | 5 |
| **Capabilities** | ✅ Insight Engine, EDM |
| **Roadmap** | Foundation |

---

### T-05: Service Queue Intelligence
| Field | Value |
|-------|-------|
| **Pain** | No insight into who's waiting and their needs |
| **Value** | Better resource allocation and service prioritization |
| **Persona** | Teller |
| **Description** | Queue view showing customer context and likely transaction type |
| **Pain Category** | Operational Efficiency |
| **Priority** | P2 |
| **Excitement** | Visionary |
| **Value Score** | 4 |
| **Effort Score** | 6 |
| **Capabilities** | 🆕 Requires new development |
| **Roadmap** | Future Vision |

---

### T-06: Digital Channel Promotion Nudge
| Field | Value |
|-------|-------|
| **Pain** | Missed opportunities to drive digital adoption |
| **Value** | Shift routine transactions to lower-cost channels |
| **Persona** | Teller |
| **Description** | Prompt suggesting digital alternatives for customer's transaction type |
| **Pain Category** | Customer Engagement |
| **Priority** | P2 |
| **Excitement** | Important |
| **Value Score** | 5 |
| **Effort Score** | 3 |
| **Capabilities** | ✅ Insight Engine, Segmentation |
| **Roadmap** | Foundation |

---

## Bank Product Team Items (PT-01 to PT-08)

### PT-01: Insight Copilot Builder
| Field | Value |
|-------|-------|
| **Pain** | Creating insights requires deep technical knowledge |
| **Value** | Democratize insight creation, faster time-to-market |
| **Persona** | Bank Product Team |
| **Description** | Natural language to insight logic: "Alert users when rent increases 10%" |
| **Pain Category** | Operational Efficiency |
| **Priority** | P0 |
| **Excitement** | Must Have |
| **Value Score** | 10 |
| **Effort Score** | 8 |
| **Capabilities** | ✅ Insight Engine, EDM, BAIQS |
| **Roadmap** | Strategic Bet |

---

### PT-02: Insight Reach Simulator
| Field | Value |
|-------|-------|
| **Pain** | Can't predict insight impact before deployment |
| **Value** | Data-driven prioritization and ROI estimation |
| **Persona** | Bank Product Team |
| **Description** | Estimate user reach, segment breakdown, and business impact before launch |
| **Pain Category** | Decision Making |
| **Priority** | P0 |
| **Excitement** | Must Have |
| **Value Score** | 9 |
| **Effort Score** | 6 |
| **Capabilities** | ✅ EDM, Segmentation |
| **Roadmap** | Strategic Bet |

---

### PT-03: A/B Testing Framework for Insights
| Field | Value |
|-------|-------|
| **Pain** | No structured way to test insight variations |
| **Value** | Optimized engagement through experimentation |
| **Persona** | Bank Product Team |
| **Description** | Built-in A/B testing for insight content, timing, and targeting |
| **Pain Category** | Optimization |
| **Priority** | P1 |
| **Excitement** | Important |
| **Value Score** | 7 |
| **Effort Score** | 6 |
| **Capabilities** | ✅ Insight Engine, Workflows |
| **Roadmap** | Strategic Bet |

---

### PT-04: Insight Performance Dashboard
| Field | Value |
|-------|-------|
| **Pain** | Hard to track insight effectiveness across segments |
| **Value** | Continuous improvement through visibility |
| **Persona** | Bank Product Team |
| **Description** | Real-time metrics: reach, engagement, conversion, by segment |
| **Pain Category** | Measurement |
| **Priority** | P1 |
| **Excitement** | Important |
| **Value Score** | 7 |
| **Effort Score** | 5 |
| **Capabilities** | ✅ Insight Engine, Data Quality |
| **Roadmap** | Quick Win |

---

### PT-05: Segment Builder with AI Recommendations
| Field | Value |
|-------|-------|
| **Pain** | Manual segment creation is time-consuming |
| **Value** | Faster, more accurate segmentation |
| **Persona** | Bank Product Team |
| **Description** | AI-assisted segment definition with reach estimates and recommendations |
| **Pain Category** | Operational Efficiency |
| **Priority** | P1 |
| **Excitement** | Important |
| **Value Score** | 8 |
| **Effort Score** | 6 |
| **Capabilities** | ✅ Segmentation, EDM |
| **Roadmap** | Strategic Bet |

---

### PT-06: Compliance Pre-Check for Insights
| Field | Value |
|-------|-------|
| **Pain** | Compliance review bottlenecks insight deployment |
| **Value** | Faster approval, reduced compliance risk |
| **Persona** | Bank Product Team |
| **Description** | Automated compliance validation before insight goes live |
| **Pain Category** | Regulatory Compliance |
| **Priority** | P1 |
| **Excitement** | Important |
| **Value Score** | 7 |
| **Effort Score** | 7 |
| **Capabilities** | ✅ BAIQS, Data Quality |
| **Roadmap** | Strategic Bet |

---

### PT-07: Multi-Channel Orchestration
| Field | Value |
|-------|-------|
| **Pain** | Inconsistent experience across channels |
| **Value** | Unified customer journey management |
| **Persona** | Bank Product Team |
| **Description** | Coordinate insight delivery across mobile, web, banker, contact center |
| **Pain Category** | Customer Experience |
| **Priority** | P2 |
| **Excitement** | Important |
| **Value Score** | 7 |
| **Effort Score** | 8 |
| **Capabilities** | ✅ Workflows, MCP Server |
| **Roadmap** | Future Vision |

---

### PT-08: Insight Content Analyzer
| Field | Value |
|-------|-------|
| **Pain** | No way to evaluate insight text quality at scale |
| **Value** | Better engagement through optimized content |
| **Persona** | Bank Product Team |
| **Description** | AI analysis of insight content: clarity, tone, compliance, effectiveness |
| **Pain Category** | Optimization |
| **Priority** | P2 |
| **Excitement** | Visionary |
| **Value Score** | 6 |
| **Effort Score** | 5 |
| **Capabilities** | ✅ BAIQS, MCP Server |
| **Roadmap** | Foundation |

---

## Bud-Inspired Capabilities (BUD-01 to BUD-04)

*Inspired by Bud's Assess, Focus, and Drive framework*

### BUD-01: Assess – Financial Health Assessment Engine
| Field | Value |
|-------|-------|
| **Pain** | No standardized way to assess customer financial health |
| **Value** | Consistent, explainable health scoring across portfolio |
| **Persona** | Banker, RM, Contact Center Agent |
| **Description** | Multi-dimensional financial health score: stability, growth, risk, opportunity |
| **Pain Category** | Customer Engagement |
| **Priority** | P1 |
| **Excitement** | Important |
| **Value Score** | 8 |
| **Effort Score** | 6 |
| **Capabilities** | ✅ EDM, Insight Engine, PRISM |
| **Roadmap** | Strategic Bet |

---

### BUD-02: Focus – Priority Customer Identification
| Field | Value |
|-------|-------|
| **Pain** | Can't easily identify which customers need attention |
| **Value** | Optimized banker time allocation |
| **Persona** | Banker, RM, Commercial RM |
| **Description** | AI-ranked customer priority list based on opportunity, risk, and engagement signals |
| **Pain Category** | Opportunity Identification |
| **Priority** | P1 |
| **Excitement** | Important |
| **Value Score** | 8 |
| **Effort Score** | 5 |
| **Capabilities** | ✅ PrimacyEdge, PRISM, Segmentation |
| **Roadmap** | Quick Win |

---

### BUD-03: Drive – Action Orchestration Engine
| Field | Value |
|-------|-------|
| **Pain** | Insights without clear actions don't drive outcomes |
| **Value** | Automated action recommendations and execution |
| **Persona** | Banker, RM, Bank Product Team |
| **Description** | End-to-end workflow from insight detection to action execution |
| **Pain Category** | Operational Efficiency |
| **Priority** | P1 |
| **Excitement** | Important |
| **Value Score** | 9 |
| **Effort Score** | 8 |
| **Capabilities** | ✅ Workflows, Insight Engine, MCP Server |
| **Roadmap** | Strategic Bet |

---

### BUD-04: Connected Intelligence Layer
| Field | Value |
|-------|-------|
| **Pain** | Intelligence siloed between consumer and banker channels |
| **Value** | Unified intelligence across all touchpoints |
| **Persona** | All Personas |
| **Description** | Shared intelligence layer powering consumer app, banker tools, and product teams |
| **Pain Category** | Platform Integration |
| **Priority** | P0 |
| **Excitement** | Must Have |
| **Value Score** | 10 |
| **Effort Score** | 9 |
| **Capabilities** | ✅ MCP Server, EDM, B2A2C Platform |
| **Roadmap** | Strategic Bet |

---

# Summary by Persona and Priority

## Banker / RM

| Priority | Items | Focus |
|----------|-------|-------|
| **P0** | B-01, B-02, B-03, B-04, B-05⚠️, B-06⚠️, B-07⚠️, B-17, **B-20** | Customer snapshot, trends, explainability, NBA, primacy⚠️, daily call sheet, **consumer insights mirror** |
| **P1** | B-08, B-09, B-10, B-11, B-13, B-14, B-15⚠️, B-18, B-19, **B-21** | Meeting prep, CRM integration, conversational Q&A, conversation starters, **banker-specific insights** |
| **P2** | B-12, B-16 | Post-meeting summaries, email drafts |

*⚠️ = Depends on PrimacyEdge availability (PRISM score not yet available)*

## Bank Executive / CEO

| Priority | Items | Focus |
|----------|-------|-------|
| **P1** | EX-01 | CEO dashboard, portfolio health metrics |
| **P2** | EX-02, EX-03 | Team performance, opportunity sizing |

## Contact Center Agent

| Priority | Items | Focus |
|----------|-------|-------|
| **P0** | CC-01, CC-02, CC-03, CC-05 | Real-time context, transaction/insight explanation |
| **P1** | CC-04, CC-06, CC-08 | Response scripts, knowledge base, upsell prompts |
| **P2** | CC-07, CC-09, CC-10 | Call prediction, auto-summaries, sentiment guidance |

## Commercial RM

| Priority | Items | Focus |
|----------|-------|-------|
| **P0** | CRM-01, CRM-02 | Business cashflow intelligence, growth/decline signals |
| **P1** | CRM-03, CRM-05, CRM-06, CRM-08 | Credit risk, treasury opportunities, relationship view |
| **P2** | CRM-04, CRM-07 | Industry benchmarking, supplier analysis |

## Teller

| Priority | Items | Focus |
|----------|-------|-------|
| **P1** | T-01, T-02 | Quick view, opportunity handoff |
| **P2** | T-03, T-04, T-05, T-06 | Eligibility checks, pattern alerts, queue intelligence |

## Bank Product Team

| Priority | Items | Focus |
|----------|-------|-------|
| **P0** | PT-01, PT-02 | Insight Copilot Builder, Reach Simulator |
| **P1** | PT-03, PT-04, PT-05, PT-06 | A/B testing, performance dashboard, compliance |
| **P2** | PT-07, PT-08 | Multi-channel orchestration, content analyzer |

## Cross-Persona (Bud-Inspired)

| Priority | Items | Focus |
|----------|-------|-------|
| **P0** | BUD-04 | Connected intelligence layer |
| **P1** | BUD-01, BUD-02, BUD-03 | Assess, Focus, Drive framework |

---

# P0 Executive View

## Critical Path Items (15 Total)

| ID | Capability | Persona | Value | Effort | Capability Leverage | Dependency |
|----|-----------|---------|-------|--------|-------------------|------------|
| B-01 | 15-Second Customer Snapshot | Banker/RM | 10 | 5 | EDM, Insight Engine | — |
| B-02 | Income & Spending Trend Analysis | Banker/RM | 9 | 4 | EDM, Insight Engine | — |
| B-03 | GenAI "What Changed?" Explainer | Banker/RM | 10 | 6 | EDM, MCP Server, BAIQS | — |
| B-04 | Next-Best-Action Recommendations | Banker/RM | 10 | 7 | Insight Engine, Segmentation | — |
| B-05 | Primacy Risk Alerts | Banker/RM | 10 | 5 | PrimacyEdge, Workflows | ⚠️ **PrimacyEdge** |
| B-06 | External Financial Relationships View | Banker/RM | 9 | 4 | PrimacyEdge, EDM | ⚠️ **PrimacyEdge** |
| B-07 | Deposit Consolidation Detector | Banker/RM | 9 | 5 | PrimacyEdge, Insight Engine | ⚠️ **PrimacyEdge** |
| B-17 | Daily Call Sheet / Prioritized Outreach | Banker/RM | 10 | 4 | Insight Engine, Workflows | — |
| **B-20** | **Consumer Engage Insights Mirror** | Banker/RM/CC | **9** | **4** | **Insight Engine (read-only)** | — |
| CC-01 | Real-Time Customer Context Panel | Contact Center | 10 | 5 | EDM, Insight Engine, MCP Server | — |
| CC-02 | Transaction Explanation Engine | Contact Center | 9 | 4 | EDM, MCP Server, BAIQS | — |
| CC-03 | Insight Trigger Explainer | Contact Center | 9 | 5 | Insight Engine, MCP Server, BAIQS | — |
| CC-05 | At-Risk Customer Alert | Contact Center | 8 | 3 | PrimacyEdge | ⚠️ **PrimacyEdge** |
| CRM-01 | Business Cashflow Intelligence | Commercial RM | 9 | 7 | EDM, Insight Engine | — |
| CRM-02 | Business Growth/Decline Indicators | Commercial RM | 9 | 6 | Insight Engine, Segmentation | — |
| PT-01 | Insight Copilot Builder | Bank Product Team | 10 | 8 | Insight Engine, EDM, BAIQS | — |
| PT-02 | Insight Reach Simulator | Bank Product Team | 9 | 6 | EDM, Segmentation | — |
| BUD-04 | Connected Intelligence Layer | All | 10 | 9 | MCP Server, EDM, B2A2C | — |

### P0 Investment Summary

| Metric | Value |
|--------|-------|
| Total P0 Items | **19** |
| Items with NO dependencies | **14** (can start immediately) |
| Items requiring PrimacyEdge | **5** (gated on availability) |
| Average Value Score | 9.5 |
| Average Effort Score | 5.3 |
| Items Leveraging Existing Capabilities | 19 (100%) |
| Estimated Timeline | Q1-Q2 2026 (non-PrimacyEdge items)

### P0 Value Drivers

1. **Banker Efficiency**: 7 items reducing preparation time by 90%+
2. **Contact Center Enablement**: 4 items reducing handle time and escalations
3. **Commercial Expansion**: 2 items enabling SMB/commercial intelligence
4. **Product Team Velocity**: 2 items accelerating insight creation by 10x
5. **Platform Foundation**: 1 item enabling B2A2C ecosystem

---

# Pivot Table: Priority → Persona

| Priority | Banker/RM | Contact Center | Commercial RM | Teller | Product Team | Executive | Cross-Persona |
|----------|-----------|----------------|---------------|--------|--------------|-----------|---------------|
| **P0** | B-01, B-02, B-03, B-04, B-05⚠️, B-06⚠️, B-07⚠️, B-17, **B-20** | CC-01, CC-02, CC-03, CC-05⚠️ | CRM-01, CRM-02 | — | PT-01, PT-02 | — | BUD-04 |
| **P1** | B-08, B-09, B-10, B-11, B-13, B-14, B-15⚠️, B-18, B-19, **B-21** | CC-04, CC-06, CC-08 | CRM-03, CRM-05, CRM-06, CRM-08 | T-01, T-02 | PT-03, PT-04, PT-05, PT-06 | EX-01 | BUD-01, BUD-02, BUD-03 |
| **P2** | B-12, B-16 | CC-07, CC-09, CC-10 | CRM-04, CRM-07 | T-03, T-04, T-05, T-06 | PT-07, PT-08 | EX-02, EX-03 | — |

*⚠️ = Requires PrimacyEdge (PRISM score not yet available)*

### Summary Counts

| Priority | Banker/RM | Contact Center | Commercial RM | Teller | Product Team | Executive | Cross-Persona | Total |
|----------|-----------|----------------|---------------|--------|--------------|-----------|---------------|-------|
| **P0** | 9 (4⚠️) | 4 (1⚠️) | 2 | 0 | 2 | 0 | 1 | **18** (5⚠️) |
| **P1** | 10 (1⚠️) | 3 | 4 | 2 | 4 | 1 | 3 | **27** |
| **P2** | 2 | 3 | 2 | 4 | 2 | 2 | 0 | **15** |
| **Total** | 21 | 10 | 8 | 6 | 8 | 3 | 4 | **60** |

*⚠️ count = items dependent on PrimacyEdge availability*

---

# 2x2 Priority vs Excitement Matrix

```
                    EXCITEMENT LEVEL
                    
         Must Have          Important          Visionary
    ┌─────────────────┬─────────────────┬─────────────────┐
    │                 │                 │                 │
P0  │  B-01, B-02,    │                 │                 │
    │  B-03, B-04,    │                 │                 │
    │  B-05, B-06,    │                 │                 │
    │  B-07, CC-01,   │                 │                 │
    │  CC-02, CC-03,  │                 │                 │
    │  CC-05, CRM-01, │                 │                 │
    │  CRM-02, PT-01, │                 │                 │
    │  PT-02, BUD-04  │                 │                 │
    │   (16 items)    │                 │                 │
    ├─────────────────┼─────────────────┼─────────────────┤
    │                 │                 │                 │
P1  │                 │  B-08, B-09,    │                 │
    │                 │  B-10, B-11,    │                 │
    │                 │  B-13, B-14,    │                 │
    │                 │  B-15, CC-04,   │                 │
    │                 │  CC-06, CC-08,  │                 │
    │                 │  CRM-03, CRM-05,│                 │
    │                 │  CRM-06, CRM-08,│                 │
    │                 │  T-01, T-02,    │                 │
    │                 │  PT-03, PT-04,  │                 │
    │                 │  PT-05, PT-06,  │                 │
    │                 │  BUD-01, BUD-02,│                 │
    │                 │  BUD-03         │                 │
    │                 │   (23 items)    │                 │
    ├─────────────────┼─────────────────┼─────────────────┤
    │                 │                 │                 │
P2  │                 │  B-12, CC-09,   │  B-16, CC-07,   │
    │                 │  T-03, T-04,    │  CC-10, CRM-04, │
    │                 │  T-06, PT-07    │  CRM-07, T-05,  │
    │                 │   (6 items)     │  PT-08          │
    │                 │                 │   (7 items)     │
    └─────────────────┴─────────────────┴─────────────────┘

P
R
I
O
R
I
T
Y
```

### Interpretation

| Quadrant | Action |
|----------|--------|
| **P0 × Must Have** | Execute immediately (Q1-Q2) |
| **P1 × Important** | Plan for Phase 2 (Q2-Q3) |
| **P2 × Important** | Foundation items (Q3-Q4) |
| **P2 × Visionary** | Future roadmap (2027+) |

---

# 2x2 Value vs Effort Matrix

```
                           EFFORT SCORE
                           
         Low (1-4)        Medium (5-6)        High (7-10)
    ┌─────────────────┬─────────────────┬─────────────────┐
    │                 │                 │                 │
    │  QUICK WINS     │  STRATEGIC      │  MAJOR          │
H   │                 │  BETS           │  INVESTMENTS    │
I   │  B-02, B-06,    │  B-01, B-03,    │  B-04, CRM-01,  │
G   │  CC-02, CC-05,  │  B-05, B-07,    │  PT-01, BUD-04  │
H   │  CC-08, T-01    │  B-08, B-09,    │                 │
    │                 │  B-10, B-11,    │                 │
V   │   (6 items)     │  B-14, B-15,    │   (4 items)     │
A   │                 │  CC-01, CC-03,  │                 │
L   │                 │  CC-04, CC-06,  │                 │
U   │                 │  CRM-02, CRM-03,│                 │
E   │                 │  CRM-05, CRM-08,│                 │
    │                 │  PT-02, PT-03,  │                 │
(   │                 │  PT-04, PT-05,  │                 │
8   │                 │  PT-06, BUD-01, │                 │
-   │                 │  BUD-02, BUD-03 │                 │
1   │                 │   (24 items)    │                 │
0   ├─────────────────┼─────────────────┼─────────────────┤
)   │                 │                 │                 │
    │  FILL-INS       │  CONSIDER       │  DEPRIORITIZE   │
L   │                 │                 │                 │
O   │  T-02, T-06,    │  B-12, B-16,    │  CC-07, CC-10,  │
W   │  CC-09          │  T-03, T-04,    │  CRM-04, CRM-06,│
    │                 │  CRM-07, PT-08  │  CRM-07, PT-07, │
(   │   (3 items)     │   (6 items)     │  T-05           │
1   │                 │                 │                 │
-   │                 │                 │   (6 items)     │
7   │                 │                 │                 │
)   └─────────────────┴─────────────────┴─────────────────┘
```

### Quadrant Recommendations

| Quadrant | Strategy | Items | Action |
|----------|----------|-------|--------|
| **Quick Wins** | Execute first | 6 | Immediate implementation |
| **Strategic Bets** | Plan carefully, high ROI | 24 | Phase 1-2 priorities |
| **Major Investments** | Critical but resource-heavy | 4 | Dedicated investment |
| **Fill-ins** | Low effort, quick value | 3 | Opportunistic |
| **Consider** | Evaluate ROI carefully | 6 | Phase 3 candidates |
| **Deprioritize** | Low value for effort | 6 | 2027+ or descope |

---

# Recommended Roadmap Path

## Phase 1: Foundation + Quick Wins (Q1-Q2 2026)

### Focus: Banker Intelligence MVP + Contact Center Enablement

| ID | Item | Value | Effort | Rationale | Dependency |
|----|------|-------|--------|-----------|------------|
| B-01 | 15-Second Customer Snapshot | 10 | 5 | Anchor product, immediate value | — |
| B-02 | Income & Spending Trend Analysis | 9 | 4 | Quick win, high visibility | — |
| B-17 | Daily Call Sheet / Prioritized Outreach | 10 | 4 | Quick win, sales enablement anchor | — |
| **B-20** | **Consumer Engage Insights Mirror** | **9** | **4** | **Aligns banker with customer experience** | — |
| CC-01 | Real-Time Context Panel | 10 | 5 | Contact center foundation | — |
| CC-02 | Transaction Explanation Engine | 9 | 4 | Quick win, reduces escalations | — |
| CC-03 | Insight Trigger Explainer | 9 | 5 | Trust-building capability | — |
| PT-04 | Insight Performance Dashboard | 7 | 5 | Enables measurement | — |
| B-05 | Primacy Risk Alerts | 10 | 5 | Leverages PrimacyEdge investment | ⚠️ PrimacyEdge |
| B-06 | External Financial Relationships | 9 | 4 | Quick win, unique differentiation | ⚠️ PrimacyEdge |
| B-07 | Deposit Consolidation Detector | 9 | 5 | Direct revenue impact | ⚠️ PrimacyEdge |
| CC-05 | At-Risk Customer Alert | 8 | 3 | Lowest effort, high impact | ⚠️ PrimacyEdge |

**Phase 1 Deliverables:**
- Banker Intelligence MVP deployed (items without dependencies)
- **Consumer Insights Mirror** — banker sees what customer received
- **Daily Call Sheet** for sales workflow
- Contact Center Context Panel live
- Quick Win metrics demonstrated
- Foundation for Phase 2 AI layer

**⚠️ Gated on PrimacyEdge Availability:**
- Primacy Risk Alerts (B-05)
- External Financial Relationships (B-06)
- Deposit Consolidation Detector (B-07)
- At-Risk Customer Alert (CC-05)

---

## Phase 2: AI Intelligence Layer (Q2-Q3 2026)

### Focus: GenAI Explainability + Opportunity Engine + Banker Insights Strategy

| ID | Item | Value | Effort | Rationale |
|----|------|-------|--------|-----------|
| B-03 | GenAI "What Changed?" Explainer | 10 | 6 | Core GenAI capability |
| B-04 | Next-Best-Action Recommendations | 10 | 7 | Revenue driver |
| B-10 | Conversational Q&A | 8 | 7 | GenAI differentiation |
| B-14 | Proactive Outreach Triggers | 8 | 6 | Engagement driver |
| B-18 | Conversation Starters / Talking Points | 8 | 4 | Sales enablement quick win |
| B-19 | Individual Customer Deep Dive Chat | 8 | 6 | Extends Q&A for individual context |
| **B-21** | **Banker-Specific Operational Insights** | **8** | **7** | **Insights designed for bankers, not consumers** |
| CC-04 | Suggested Response Scripts | 7 | 5 | Agent enablement |
| CC-06 | Quick Q&A Knowledge Base | 7 | 6 | Reduces handle time |
| PT-01 | Insight Copilot Builder | 10 | 8 | Product team velocity |
| PT-02 | Insight Reach Simulator | 9 | 6 | Data-driven decisions |
| EX-01 | CEO Dashboard – Portfolio Health | 8 | 6 | Executive visibility, buy-in driver |
| BUD-01 | Financial Health Assessment | 8 | 6 | Competitive parity (Bud Assess) |
| BUD-02 | Priority Customer Identification | 8 | 5 | Competitive parity (Bud Focus) |

**Phase 2 Deliverables:**
- GenAI explainability in production
- Opportunity Engine operational
- **Conversation starters for sales**
- **Customer deep dive chat capability**
- **Banker-specific insights (operational triggers)** — requires architecture decision
- **CEO Dashboard beta**
- Insight Copilot Builder beta
- Bud-competitive capabilities live

**📝 Key Decision Point:**
B-21 (Banker-Specific Insights) requires resolution of **Strategic Architecture Question #1**: 
- Use Engage Engine with banker-specific insight rules? 
- Build MCP-powered on-demand analysis?
- Both?

---

## Phase 3: Scale + Commercial Expansion (Q3-Q4 2026)

### Focus: Multi-Channel + Commercial RM Suite

| ID | Item | Value | Effort | Rationale |
|----|------|-------|--------|-----------|
| B-09 | CRM-Embedded Intelligence Panel | 8 | 6 | Enterprise integration |
| B-11 | Cross-Sell Opportunity Score | 8 | 6 | Revenue optimization |
| B-13 | Customer Health Score Dashboard | 7 | 5 | Portfolio management |
| B-15 | Competitive Intelligence Alerts | 8 | 5 | Retention enablement |
| CRM-01 | Business Cashflow Intelligence | 9 | 7 | Commercial expansion |
| CRM-02 | Business Growth/Decline Indicators | 9 | 6 | Commercial expansion |
| CRM-05 | Treasury Opportunities | 8 | 6 | Cross-sell commercial |
| T-01 | Customer Quick View | 7 | 3 | Branch enablement |
| T-02 | Opportunity Handoff to RM | 6 | 4 | Lead generation |
| BUD-03 | Action Orchestration Engine | 9 | 8 | Competitive parity (Bud Drive) |
| BUD-04 | Connected Intelligence Layer | 10 | 9 | Platform foundation |

**Phase 3 Deliverables:**
- Salesforce/Dynamics integration live
- Commercial RM suite deployed
- Branch/Teller basic enablement
- B2A2C platform foundation

---

## Phase 4: Advanced + Visionary (2027+)

### Focus: Autonomous Intelligence + Future Capabilities

| ID | Item | Value | Effort | Rationale |
|----|------|-------|--------|-----------|
| B-08 | Meeting Preparation Summary | 8 | 5 | Productivity enhancement |
| B-12 | Post-Meeting Summary Generator | 7 | 6 | Automation |
| B-16 | Personalized Email Drafts | 6 | 5 | Agent enablement |
| CC-07 | Call Outcome Predictor | 6 | 7 | Advanced AI |
| CC-09 | Post-Call Summary Auto-Generation | 6 | 6 | Automation |
| CC-10 | Sentiment-Aware Guidance | 5 | 8 | Advanced AI |
| CRM-03 | Credit Risk Early Warning | 8 | 7 | Risk management |
| CRM-04 | Industry Benchmarking | 6 | 8 | Differentiation |
| CRM-06 | Multi-Entity Relationship View | 7 | 7 | Commercial complexity |
| CRM-07 | Supplier/Vendor Analysis | 5 | 7 | Advanced commercial |
| CRM-08 | Loan Utilization Intelligence | 7 | 5 | Portfolio management |
| PT-03 | A/B Testing Framework | 7 | 6 | Optimization |
| PT-05 | Segment Builder with AI | 8 | 6 | Product team velocity |
| PT-06 | Compliance Pre-Check | 7 | 7 | Governance |
| PT-07 | Multi-Channel Orchestration | 7 | 8 | Platform maturity |
| PT-08 | Insight Content Analyzer | 6 | 5 | Content optimization |
| T-03 | Product Eligibility Check | 5 | 4 | Branch enablement |
| T-04 | Transaction Pattern Alerts | 6 | 5 | Risk detection |
| T-05 | Service Queue Intelligence | 4 | 6 | Branch optimization |
| T-06 | Digital Channel Promotion | 5 | 3 | Channel shift |

**Phase 4 Deliverables:**
- Advanced AI capabilities deployed
- Full commercial RM suite
- Autonomous workflow orchestration
- Content optimization tools

---

# Capability Mapping

## Leverages Existing Personetics Capabilities

| Capability | Items Count | Key Items |
|------------|-------------|-----------|
| **EDM** | 28 | B-01, B-02, CC-01, CRM-01, PT-01, PT-02 |
| **Insight Engine** | 30 | B-01, B-04, CC-03, CRM-02, PT-01 |
| **PrimacyEdge** | 10 | B-05, B-06, B-07, CC-05, BUD-02 |
| **PRISM** | 12 | B-01, B-04, B-05, CC-05, BUD-01 |
| **Segmentation** | 14 | B-04, B-07, CRM-02, PT-02, PT-05 |
| **MCP Server** | 16 | B-03, B-09, B-10, CC-01, CC-06 |
| **MCP Tools** | 4 | B-09, CC-06 |
| **BAIQS** | 12 | B-03, CC-02, CC-03, PT-01, PT-06 |
| **Data Quality** | 4 | PT-04, PT-06 |
| **Workflows** | 8 | B-05, B-14, T-02, PT-03, BUD-03 |

## Requires New Development

| Item | Capability Gap | Investment Level |
|------|---------------|------------------|
| CC-07 | Call outcome prediction ML | Medium |
| CC-10 | Real-time sentiment analysis | High |
| CRM-04 | Industry benchmark data | High |
| T-05 | Queue management integration | Medium |

### Summary

| Category | Count | Percentage |
|----------|-------|------------|
| Leverages Existing | 48 | 92% |
| Requires New Dev | 4 | 8% |
| **Total** | 52 | 100% |

---

# Appendix: Scoring Methodology

## Value Score (1-10)

| Score | Definition |
|-------|------------|
| 10 | Game-changing capability, major revenue/retention impact |
| 8-9 | High business impact, clear ROI |
| 6-7 | Meaningful improvement, measurable benefit |
| 4-5 | Nice to have, incremental value |
| 1-3 | Low impact, limited use cases |

## Effort Score (1-10)

| Score | Definition |
|-------|------------|
| 1-3 | Quick implementation, existing components |
| 4-5 | Moderate effort, some new development |
| 6-7 | Significant effort, multiple components |
| 8-9 | Major investment, new capabilities required |
| 10 | Transformational effort, platform-level change |

## Priority Definitions

| Priority | Criteria |
|----------|----------|
| **P0** | Must have for 2026, critical for competitive positioning |
| **P1** | High value, planned for 2026 phases |
| **P2** | Important, scheduled based on resources |

## Excitement Level

| Level | Definition |
|-------|------------|
| **Must Have** | Essential capability, expected by market |
| **Important** | Valuable differentiator, high demand |
| **Visionary** | Future-looking, positions for next wave |

---

# Appendix: Design References

## Scott McQuilkin Feedback (Prior Banker Project)

The following screenshots from Scott's prior banker project inform several backlog items:

### 1. Daily Call Sheet (→ B-17)
**"Top Actionable Insights"** view showing:
- Account name (e.g., Aaron Davies, Andrew Goldberg, James Miller)
- Top insight per account (e.g., "Credit card payment is past due", "Payment from PLLAB has not been deposited")
- Insight count per account (6-15 insights)
- Sorted for sales and relationship building prioritization

### 2. Individual Customer Deep Dive (→ B-19, B-01)
**Account detail view** showing:
- Account Information (Source System ID, Status, Marketing Segment, Category)
- Client Services section
- Know Your Client section  
- **Actionable Insights panel** with:
  - Savings Opportunity
  - Government Deposit Change
  - Higher than usual charge
- Activity section with Next Steps
- Chat capability for deeper exploration

### 3. CEO Dashboard (→ EX-01)
High-level metrics about customer portfolio for executive visibility

---

**Document Version:** 1.1  
**Created:** December 2026  
**Updated:** December 2026 (Scott McQuilkin feedback incorporated)  
**Owner:** Director of AI Product Management  
**Status:** Draft for Review  
**Next Steps:** Review with CPO, validate with design partners, finalize priorities


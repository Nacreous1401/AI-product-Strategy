# AI Product Strategy

> I’m building an AI connectivity copilot for IoT product and operations teams because global device fleets are growing faster than teams can manually monitor, diagnose, and resolve connectivity issues.

---

## Strategy at a Glance

| Component | Module | Status | Key Artifact |
|-----------|--------|--------|-------------|
| **The Bet** | M1 | [x] | `01-the-bet/` |
| **The Moat** | M2 | [x] | `02-the-moat/` |
| **The Margin** | M3 | [x] | `03-the-margin/` |
| **The Contract** | M4 | [x] | `04-the-contract/` |
| **The Guardrails** | M5 | [x] | `05-the-guardrails/` |
| **The Pitch** | M6 | [x] | `06-the-pitch/` |

---

## The Bet (M1)

**What we're building, for whom, why now.**

- **Product:**
- **AI Value Archetype:** Copilot
- **Vulnerability Scores:** Moat 4/5 · Data 3/5 · Platform 2/5
- **Top Risk:** Connectivity management becomes a bundled cloud/carrier feature, reducing standalone CMP differentiation.
- **Confidence:** M
- **Prototype:** https://copilot-connect-insight.lovable.app
- **Kill Criteria:** I would stop if users say the prototype does not reduce investigation time, does not provide more actionable recommendations than existing dashboards, or if teams are unwilling to trust AI-suggested fixes without extensive manual review.

→ Details: [`01-the-bet/`](01-the-bet/)

---

## The Moat (M2)

**Why this won't get copied in 6 months.**

- **Data Flywheel Score:**
- **Weakest Loop:**
- **Top Encroachment Threat:**
- **Encroachment Defense:** Surface fleet benchmarking in the copilot so new customers visibly benefit existing ones
- **Vendor Portability:** Partial

→ Details: [`02-the-moat/`](02-the-moat/)

---

## The Margin (M3)

**Will this make money or bleed it?**

- **Gross Margin (current):**
- **Gross Margin (AI-adjusted):**
- **Pricing Model:** seat-based / usage-based / outcome-based / hybrid
- **Pricing Today → Tomorrow:** Traditional platform pricing based on SIMs, connectivity usage, and enterprise contracts. → AI Copilot premium tier for intelligent operations, diagnostics, and automation.
- **Total AI COGS / unit:**
- **Cascading Strategy:** Triage: Low-cost model for classification, summaries, alerts, and basic troubleshooting.; frontier: Claude Sonnet / GPT-4 class model for deep incident analysis and complex recommendations.; ratio 85% low-cost model / 15% frontier model
- **Net Margin Shift:**
- **Break-even at:**

→ Details: [`03-the-margin/`](03-the-margin/)

---

## The Contract (M4)

**Why users will trust a probabilistic system.**

- **Reliability Target:** >90%
- **Golden Dataset:** 10 rows, 3 adversarial
- **Confidence UX:** Tiered confidence UX with visible uncertainty indicators, supporting evidence, and human-in-the-loop escalation for low-confidence or high-risk connectivity recommendations.
- **HITL Architecture:** ### Trigger — when does a human enter the loop?
- **Failure Mode Coverage:** ### The attack they ran

→ Details: [`04-the-contract/`](04-the-contract/)

---

## The Guardrails (M5)

**What breaks when this scales — and what compounds.**

- **Compounding System:** | Loop | Input | Output | Compounds? | Status | |------|-------|--------|-----------|--------| | Recursive Learning | Operator corrections, rejected AI suggestions, and final incident outcomes | Better golden dataset row…
- **Governance Posture:** AI-assisted detection, diagnosis, prioritization, recommendation, and escalation for SIM/eSIM connectivity incidents.
- **Autonomy Boundaries:** The AI can analyze, summarize, recommend, and draft. It cannot independently switch carriers, change routing, disable or modify SIMs/eSIMs, override customer policies, make billing decisions, or take live customer-impacting action without h…
- **Escalation Triggers:** Confidence below 70%, conflicting telemetry, high-value customer impact, roaming or policy conflict, missing evidence, suspected hallucination, or any action affecting live customer connectivity.
- **Audit Cadence:** Real-time monitoring for confidence, latency, and safety flags. Weekly review of golden dataset results, hallucinations, and failed recommendations.…
- **Shadow AI Audit (user-side):** 3 workarounds found · 2 build candidates · adjacent spend Medium — mostly productivity-tool usage and manual analysis. Risk becomes high if unapproved tools influence live connectivity decisions.
- **Agent Boundaries:** The system may use multiple agents, but customer-impacting actions require human approval.
- **Regulatory Exposure:** EU AI Act, GDPR, telecom operational compliance, customer data protection, and internal security policies. Risk is limited, but controls are needed because the copilot influences operational decisions.

→ Details: [`05-the-guardrails/`](05-the-guardrails/)

---

## The Pitch (M6)

**How you get this funded, shipped, and adopted.**

- **Horizon 1 (Now):**
- **Horizon 2 (Next):**
- **Horizon 3 (Bet):**
- **Board Narrative:** **The case:**
- **Ask:** ## M1 Baseline vs. Now
- **Key Strategic Change:**

→ Details: [`06-the-pitch/`](06-the-pitch/)

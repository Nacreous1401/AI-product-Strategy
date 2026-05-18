# Three-Horizon Roadmap & Board Pitch

## Roadmap

### Horizon 1 — Ship (0–4 weeks)

| Initiative | Strategy Component | Why it ships now | Confidence |
|---|---|---|---|
| AICP-1 — AI incident summary for connectivity issues | Bet | This is the basic copilot experience and can validate whether users understand incidents faster. | H |
| AICP-3 — Confidence score for AI recommendations | Contract | Trust is impossible without visible confidence and uncertainty drivers. | H |
| AICP-4 — Human review queue for low-confidence cases | Contract | Low-confidence outputs already need a safe human path before operational use. | H |
| AICP-5 — Human approval before carrier or routing changes | Guardrails | This directly enforces the stated autonomy boundary. | H |
| AICP-6 — Customer policy guardrail | Guardrails | The AI must not recommend actions that violate customer-specific rules. | H |
| AICP-7 — Golden dataset evaluation dashboard | Contract | A basic eval dashboard is needed before reliability claims can be trusted. | M |
| AICP-12 — Provider abstraction layer | Moat | This supports vendor portability and reduces platform dependency risk. | H |
| AICP-13 — Cascading model routing | Margin | This directly supports the stated 85% low-cost / 15% frontier model strategy. | H |
| AICP-14 — AI usage and cost monitoring | Margin | Cost visibility is required before pricing or margin assumptions are credible. | H |
| AICP-15 — Hallucination audit workflow | Contract | Weekly hallucination review is already part of the stated audit cadence. | H |
| AICP-16 — Conflicting telemetry handling | Contract | Conflicting signals are a known reliability failure mode and must lower confidence. | H |
| AICP-17 — Missing telemetry fallback behavior | Contract | The copilot must show missing evidence instead of pretending certainty. | H |
| AICP-18 — Prompt injection protection | Guardrails | Security controls are required before users can rely on AI recommendations. | H |
| AICP-20 — Shadow AI tool governance | Guardrails | This directly supports the stated shadow AI audit and governance posture. | M |

### Horizon 2 — Validate (1–3 months)

| Initiative | Strategy Component | Hypothesis | Kill Criteria | Confidence |
|---|---|---|---|---|
| AICP-2 — Connectivity incident root-cause recommendation | Bet | If the copilot shows likely root causes with evidence and confidence, operators will reduce investigation time compared with dashboards. | If we don't see at least 30% faster investigation time by week 6, we stop. | M |
| AICP-8 — Operator correction feedback loop | Guardrails | If operator corrections feed into review and evals, the system will improve over time instead of repeating the same mistakes. | If we don't see repeated corrections turning into reusable golden dataset cases by week 6, we stop. | M |
| AICP-11 — Model provider fallback | Moat | If provider abstraction works, fallback will reduce pricing, availability, and lock-in risk without degrading product quality. | If we can't switch providers for one core workflow without product logic changes by week 6, we stop. | M |

### Horizon 3 — Explore (3–6 months)

| Initiative | Strategy Component | What must be true first | Confidence |
|---|---|---|---|
| AICP-9 — Fleet benchmarking for connectivity incidents | Moat | The product must have enough anonymized cross-customer incident data to create meaningful benchmarks. | M |
| AICP-10 — Shared incident intelligence | Moat | The system must reliably detect patterns across fleets without exposing customer-sensitive data. | M |
| AICP-19 — Customer-facing escalation draft | Bet | The diagnostic copilot must first prove that its internal recommendations are trusted by operators. | L |

### Unmapped (cut or rethink)

| Initiative | Why it's unmapped | Recommendation |
|---|---|---|
| None | All initiatives connect to Bet, Moat, Margin, Contract, or Guardrails. | Keep mapped, but deprioritize weak-fit items if capacity is limited. |

### Mapping Disagreements

No disagreements — all user mappings stand.

The roadmap is over-indexed on H1 execution; what is missing is stronger H2 validation around business impact and stronger H3 moat exploration.

The single H3 bet to protect is **AICP-9 — Fleet benchmarking for connectivity incidents**.

The one initiative to kill today is **AICP-19 — Customer-facing escalation draft**. 

## Board Pitch

**Thesis (1 sentence):**
We should fund a connectivity-operations assistant that helps operations teams diagnose incidents faster, with evidence, confidence levels, and human approval before any customer-impacting action.

**The case:**
1. Why now: Connectivity management is at risk of becoming a bundled cloud or carrier feature, so the window is to move from a standalone CMP workflow into a higher-value intelligent operations layer before the core workflow gets commoditized.
2. What's defensible: The defensible moat from M2 is fleet-level incident intelligence: anonymized benchmarking and shared incident patterns that get better as more fleets use the product. This is stronger than a generic AI assistant because the value comes from proprietary connectivity telemetry, operator corrections, rejected recommendations, and final incident outcomes.
3. The economics: 85% of AI tasks should run on low-cost models and only 15% on frontier models, which is the current margin control strategy from M3. The economics are not yet board-ready because current gross margin, AI-adjusted gross margin, AI COGS per unit, net margin shift, and break-even are still missing; the first funded phase must prove cost per incident and willingness to pay before scaling the premium tier.

**The risks:**
1. Trust / failure modes: The main trust failure is an AI recommendation that confidently suggests a wrong carrier, routing, SIM, or customer-policy action and damages live connectivity. The M4 reliability contract catches this through confidence scoring, visible uncertainty, supporting evidence, human review for low-confidence cases, and a reliability target above 90%, but the golden dataset is still too small at 10 rows and needs expansion before broad rollout.
2. Scale / governance: At 10x usage, the risks are inference cost, hallucination volume, unclear autonomy, and unapproved AI usage around live connectivity decisions. M5 addresses this with human approval boundaries, escalation triggers, weekly hallucination audits, shadow AI governance, customer-policy guardrails, and model/provider controls.
3. Competitive: The kill scenario is that cloud or carrier platforms bundle similar connectivity diagnostics before we build a proprietary data loop. If root-cause recommendations do not reduce investigation time by at least 30% by week 6, or if provider abstraction cannot support one core workflow without product logic changes by week 6, we stop or narrow the bet.

**The ask:**
Approve €650k, 3 engineers, and 1 PM for 6 months to ship the H1 trust and governance foundation, validate root-cause recommendations in H2, and protect the H3 fleet-benchmarking moat. In return, we get a measured answer on whether this can become a premium intelligent-operations tier rather than just an expensive feature. If funded, we pause customer-facing escalation drafts and any broad AI productivity work that does not directly improve incident diagnosis, trust, margin control, or fleet intelligence.

## M1 Baseline vs. Now

*Your 3-sentence AI strategy from Module 1 vs. what you'd say now:*

### M1 baseline:

We are building an AI copilot for connectivity operations teams to help them investigate SIM/eSIM connectivity incidents faster.

The copilot summarizes incidents, recommends likely root causes, and shows confidence so users do not need to manually search across logs, tickets, and telemetry.

We would stop if users say it does not reduce investigation time, does not give more actionable recommendations than existing dashboards, or cannot be trusted without heavy manual review.

### Now:

We should fund an AI copilot that helps connectivity operations teams diagnose incidents faster because our differentiation must move from basic connectivity management to trusted network intelligence.

The near-term win is faster, evidence-backed incident diagnosis; the longer-term moat is anonymized fleet benchmarking and shared incident intelligence.

This bet should continue only if we can prove measurable investigation-time reduction, user trust, controlled AI costs, and a clear premium-tier path.

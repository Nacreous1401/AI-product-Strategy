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
We should fund an AI copilot that helps connectivity operations teams diagnose incidents faster, because our differentiation must move from managing SIMs and connectivity to turning our operational data into trusted network intelligence.

**The case:**
1. Why now: The near-term window is defensive: connectivity management risks becoming a bundled cloud or carrier feature, so we need to prove that our advantage is not basic CMP workflow, but faster incident diagnosis, evidence-backed recommendations, and operational intelligence built from our own connectivity context.
2. What's defensible: The moat is shared incident intelligence. M2 is still incomplete, but the strongest defensibility path is clear: fleet benchmarking and anonymized incident patterns that make each new customer improve the copilot for existing customers.
3. The economics: 85% of AI work should run on low-cost models and only 15% on frontier models for deep incident analysis. M3 is not yet board-ready because current gross margin, AI-adjusted margin, total AI COGS, net margin shift, and break-even are still blank; the first 12 months must prove whether the premium copilot tier can support the cost curve.

**The risks:**
1. Trust / failure modes: The front-page failure is an AI recommendation that causes a live customer connectivity incident, such as an unsafe carrier, routing, SIM, or policy change. M4 reduces this risk through confidence UX, evidence display, human-in-the-loop escalation, and a reliability target above 90%, but the current golden dataset of 10 rows is too small to support that promise.
2. Scale / governance: At 10x usage, the likely breakpoints are inference cost, hallucination risk, policy conflicts, latency, and unclear ownership of AI decisions. M5 addresses this with autonomy boundaries, escalation triggers, audit cadence, shadow AI governance, and human approval for customer-impacting actions.
3. Competitive: The competitive kill scenario is that cloud platforms, carriers, or larger connectivity providers bundle comparable diagnostics before we prove a proprietary data loop. We should kill or pause the bet if users say the prototype does not reduce investigation time, does not provide more actionable recommendations than existing dashboards, or is not trusted without extensive manual review.

**The ask:**
We are asking for 1.5 million in funding, 5 engineers, 1 PM, and 12 months to prove the copilot can reduce investigation time, create a premium AI tier, and establish the first version of our shared incident intelligence moat. In return, we will deliver the diagnostic copilot, confidence UX, human review workflow, golden dataset evaluation, cost monitoring, model routing, and the first fleet benchmarking experiments. The tradeoff is that other non-core dashboard improvements and lower-leverage customer communication automation should wait until the diagnostic workflow proves measurable value.

## M1 Baseline vs. Now

*Your 3-sentence AI strategy from Module 1 vs. what you'd say now:*

**M1 baseline:**  
We are building an AI copilot for connectivity operations teams to help them investigate SIM/eSIM connectivity incidents faster.  
The copilot summarizes incidents, recommends likely root causes, and shows confidence so users do not need to manually search across logs, tickets, and telemetry.  
We would stop if users say it does not reduce investigation time, does not give more actionable recommendations than existing dashboards, or cannot be trusted without heavy manual review.

**Now:**  
We should fund an AI copilot that helps connectivity operations teams diagnose incidents faster because our differentiation must move from basic connectivity management to trusted network intelligence.  
The near-term win is faster, evidence-backed incident diagnosis; the longer-term moat is anonymized fleet benchmarking and shared incident intelligence.  
This bet should continue only if we can prove measurable investigation-time reduction, user trust, controlled AI costs, and a clear premium-tier path.

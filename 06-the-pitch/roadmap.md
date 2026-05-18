# Three-Horizon Roadmap & Board Pitch

## Roadmap

### Horizon 1 — Ship (0–4 weeks)

| Initiative | Strategy Component | Why it ships now | Confidence |
|---|---|---|---|
| AICP-1 — AI incident summary for connectivity issues | Bet | It directly supports the core copilot bet by helping users understand incidents faster. | H |
| AICP-3 — Confidence score for AI recommendations | Contract | Trust requires users to see confidence and uncertainty before relying on AI recommendations. | H |
| AICP-4 — Human review queue for low-confidence cases | Contract | Low-confidence outputs need human review before they become operationally risky. | H |
| AICP-5 — Human approval before carrier or routing changes | Guardrails | This directly enforces the autonomy boundary for customer-impacting actions. | H |
| AICP-12 — Provider abstraction layer | Moat | It supports vendor portability and reduces dependency on a single model provider. | M |
| AICP-13 — Cascading model routing | Margin | It directly supports the stated cascading strategy to control AI COGS. | H |
| AICP-14 — AI usage and cost monitoring | Margin | Margin cannot be managed without visibility into usage and cost by model, account, and workflow. | H |
| AICP-15 — Hallucination audit workflow | Contract | It supports the reliability promise by reviewing unsupported or fabricated AI outputs. | H |
| AICP-16 — Conflicting telemetry handling | Contract | It supports trust by lowering confidence when signals conflict. | H |
| AICP-17 — Missing telemetry fallback behavior | Contract | It prevents automation or overconfidence when key evidence is missing. | H |
| AICP-18 — Prompt injection protection | Guardrails | It protects system rules, telemetry, and policy logic from unsafe user instructions. | H |

### Horizon 2 — Validate (1–3 months)

| Initiative | Strategy Component | Hypothesis | Kill Criteria | Confidence |
|---|---|---|---|---|
| AICP-2 — Connectivity incident root-cause recommendation | Bet | Evidence-backed root-cause recommendations reduce investigation time versus existing dashboards. | If we don't see reduced investigation time in user testing by week 6, we stop. | M |
| AICP-6 — Customer policy guardrail | Guardrails | Customer-specific roaming and policy rules can be used to block or escalate risky recommendations. | If we cannot reliably detect policy conflicts in test cases by week 6, we stop. | M |
| AICP-7 — Golden dataset evaluation dashboard | Contract | A dashboard can make accuracy, hallucination rate, drift, and latency measurable against golden cases. | If the dashboard does not expose meaningful reliability trends by week 6, we stop. | M |
| AICP-8 — Operator correction feedback loop | Guardrails | Operator corrections and rejected recommendations can improve the golden dataset review process. | If corrections do not produce reusable review inputs by week 6, we stop. | M |
| AICP-11 — Model provider fallback | Guardrails | Fallback capability can reduce single-provider pricing, availability, and portability risk. | If fallback creates unacceptable quality or latency degradation by week 6, we stop. | M |
| AICP-20 — Shadow AI tool governance | Guardrails | An approved AI tool catalog can reduce unsafe shadow AI usage around live connectivity decisions. | If the audit does not reveal material shadow AI risk by week 6, we stop. | M |

### Horizon 3 — Explore (3–6 months)

| Initiative | Strategy Component | What must be true first | Confidence |
|---|---|---|---|
| AICP-9 — Fleet benchmarking for connectivity incidents | Moat | There must be enough anonymized cross-fleet incident data to create useful benchmarks. | L |
| AICP-10 — Shared incident intelligence | Moat | Similar incident patterns must appear across fleets, roaming partners, or regions often enough to be useful. | L |
| AICP-19 — Customer-facing escalation draft | Bet | The core diagnostic copilot must prove value before customer communication drafts matter. | L |

### Unmapped (cut or rethink)

| Initiative | Why it's unmapped | Recommendation |
|---|---|---|
| None | All listed initiatives connect to Bet, Moat, Margin, Contract, or Guardrails. | No cut required from the unmapped category. |

### Mapping Disagreements

No disagreements — all user mappings stand.

The most over-indexed horizon is H1; H2 needs stronger validation evidence and H3 needs clearer moat experiments.

The single H3 bet to protect if budget gets cut is AICP-9 — Fleet benchmarking for connectivity incidents.

The one initiative to kill today is AICP-19 — Customer-facing escalation draft.  

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

**Now:**

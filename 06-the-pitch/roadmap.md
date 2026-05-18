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

**The case:**
1. Why now:
2. What's defensible:
3. The economics:

**The risks:**
1. Trust / failure modes:
2. Scale / governance:
3. Competitive:

**The ask:**

## M1 Baseline vs. Now
*Your 3-sentence AI strategy from Module 1 vs. what you'd say now:*

**M1 baseline:**

**Now:**

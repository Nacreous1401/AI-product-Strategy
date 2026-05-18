# Three-Horizon Roadmap & Board Pitch

## Roadmap

## Horizon 1 — Ship (0–4 weeks)

| Initiative | Strategy Component | Why it ships now | Confidence |
|---|---|---|---|
| AICP-1 — AI incident summary for connectivity issues | Bet | This is the simplest visible copilot value and directly supports the promise of reducing manual log/ticket reading. | H |
| AICP-3 — Confidence score for AI recommendations | Contract | Trust cannot wait; confidence and uncertainty must be visible from the first usable version. | H |
| AICP-5 — Human approval before carrier or routing changes | Guardrails | This is a non-negotiable safety boundary before the copilot touches customer-impacting workflows. | H |
| AICP-12 — Provider abstraction layer | Margin | Needed early so model choice, cost control, and portability do not get hardcoded into the product. | H |
| AICP-13 — Cascading model routing | Margin | Directly supports the stated 85% low-cost / 15% frontier model strategy. | H |
| AICP-14 — AI usage and cost monitoring | Margin | You cannot validate AI margin without account, workflow, and model-level cost visibility. | M |
| AICP-15 — Hallucination audit workflow | Contract | Weekly manual audit can start before a full eval platform exists. | H |
| AICP-18 — Prompt injection protection | Guardrails | Basic security controls should exist before exposing the copilot to real users or customer-facing data. | H |
| AICP-20 — Shadow AI tool governance | Guardrails | This directly matches the identified shadow AI risk and can start as policy + approved-tool inventory. | M |

---

## Horizon 2 — Validate (1–3 months)

| Initiative | Strategy Component | Hypothesis | Kill Criteria | Confidence |
|---|---|---|---|---|
| AICP-2 — Connectivity incident root-cause recommendation | Bet | Operators will trust AI root-cause suggestions when evidence and confidence are shown clearly. | If we don't see at least 30% investigation-time reduction by week 6, we stop. | M |
| AICP-4 — Human review queue for low-confidence cases | Contract | Routing uncertain cases to humans will increase trust without slowing normal workflows too much. | If we don't see 80% of low-confidence cases reviewed within SLA by week 6, we stop. | M |
| AICP-6 — Customer policy guardrail | Guardrails | Customer-specific rules can be reliably detected and used to block or escalate risky recommendations. | If we don't catch 95% of known policy conflicts in test cases by week 6, we stop. | M |
| AICP-7 — Golden dataset evaluation dashboard | Contract | A dashboard will make quality, drift, hallucination, and latency visible enough to manage reliability. | If weekly review does not reveal actionable quality fixes by week 6, we stop. | M |
| AICP-8 — Operator correction feedback loop | Guardrails | Operator corrections will create a compounding improvement loop for future evals and recommendations. | If fewer than 20 useful corrections are captured by week 6, we stop. | M |
| AICP-11 — Model provider fallback | Margin | Provider fallback will reduce availability and pricing risk without degrading output quality. | If fallback adds unacceptable latency or drops quality below the main provider by week 6, we stop. | M |
| AICP-16 — Conflicting telemetry handling | Contract | The copilot can detect telemetry conflicts and correctly lower confidence instead of forcing an answer. | If it misses more than 10% of known telemetry-conflict cases by week 6, we stop. | M |
| AICP-17 — Missing telemetry fallback behavior | Contract | The copilot can safely expose missing evidence and avoid automation when data is incomplete. | If users still treat missing-data outputs as actionable by week 6, we stop. | M |

---

## Horizon 3 — Explore (3–6 months)

| Initiative | Strategy Component | What must be true first | Confidence |
|---|---|---|---|
| AICP-9 — Fleet benchmarking for connectivity incidents | Moat | You need enough anonymized cross-customer incident data and privacy approval to make benchmarks credible. | M |
| AICP-10 — Shared incident intelligence | Moat | You need repeatable cross-fleet patterns that are useful without exposing customer-sensitive data. | M |
| AICP-19 — Customer-facing escalation draft | Bet | The internal diagnostic experience must first prove accuracy, trust, and support-team adoption. | L |

---

## Unmapped — cut or rethink

| Initiative | Why it's unmapped | Recommendation |
|---|---|---|
| None | Every initiative connects to Bet, Moat, Margin, Contract, or Guardrails. | No cut purely on mapping grounds. |

---

## Mapping Disagreements

No disagreements — no `[User-mapped to: X]` lines were present, so all mappings above are my own.

---

## Closing Notes

H2 is the most over-indexed horizon; there are many validation bets, but the H1 pilot package needs to stay brutally focused and H3 should only protect true moat work.

The single H3 bet I would protect is **AICP-9 — Fleet benchmarking**, because it is the clearest path to defensibility.

The one initiative I would kill today is **AICP-19 — Customer-facing escalation draft**, because it is useful but distracts from proving the core diagnostic copilot.

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

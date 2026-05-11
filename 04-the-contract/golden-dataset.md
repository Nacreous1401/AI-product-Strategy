# Golden Dataset & Reliability Contract

## Golden Dataset Spec

| # | Input | Expected Output | Edge Case? | Judge Type |
|---|-------|----------------|-----------|-----------|
| 1 | SIMs in Germany suddenly lose connectivity after roaming partner update | Identify roaming partner issue and recommend carrier fallback | N | rule |
| 2 | Device fleet shows 42% usage drop across France within 2 hours | Detect abnormal traffic drop and trigger escalation recommendation | N | LLM |
| 3 | Customer reports intermittent connectivity but dashboards show normal status | Recommend deeper network investigation and possible latency issue | Y | LLM |
| 4 | AI recommends switching carrier, but customer policy blocks roaming changes | Respect customer policy and escalate to human review | Y | rule |
| 5 | Multiple SIMs generate conflicting diagnostic signals across regions | Prioritize most likely root cause and assign confidence score | Y | LLM |

**Adversarial rows included:** 3

**Coverage gaps identified by partner:**  
Limited coverage for conflicting signals across multiple carriers and incomplete telemetry scenarios.

## Confidence UX Design

**Approach:**  
Tiered confidence UX with visible uncertainty indicators, supporting evidence, and human-in-the-loop escalation for low-confidence or high-risk connectivity recommendations.

**High confidence (>90%):**  
Show full recommendation with supporting evidence, affected SIM/network details, and recommended action buttons. Users can approve, edit, or reject the recommendation.

**Medium confidence (70-90%):**  
Use softer language, highlight uncertainty drivers, request additional customer/network context, and require manual confirmation before execution.

**Low confidence (<70%):**  
Do not automate actions. Escalate to operations teams, surface missing evidence, and route incident into human review queue.

**User control surface:**  
- Users can adjust confidence thresholds for automation  
- Users can view AI reasoning and diagnostic drivers  
- Users can correct or override recommendations  
- Corrections feed back into the evaluation dataset and future model tuning

## Reliability Contract

| Metric | Target | Measurement | Alert Threshold |
|--------|--------|-------------|-----------------|
| Accuracy | >90% | Weekly evaluation against golden dataset using rule + LLM judges | <85% |
| Hallucination rate | <3% | Weekly safety audit for fabricated diagnoses or unsupported recommendations | >5% |
| Latency (p95) | <5 seconds | Continuous monitoring of AI response time by endpoint | >8 seconds for 5 minutes |
| Drift velocity | <0.5% quality decay per month | 4-week rolling accuracy trend across golden dataset | >1% decay per month |

### Consequence Patterns

- Accuracy threshold breach → Gold-set audit + human review queue  
- Hallucination threshold breach → Auto-rollback for affected workflows  
- Latency threshold breach → Page on-call engineering team  
- Drift threshold breach → Trigger dataset refresh and evaluation audit

---

## HITL Architecture

### Trigger — when does a human enter the loop?

- Confidence score below 70%  
- High-risk enterprise connectivity incidents  
- Conflicting telemetry across carriers or regions  
- Policy or roaming restriction conflicts  
- Safety or hallucination flags triggered

### Reviewer — who reviews?

Operations engineers review low-confidence recommendations during business hours, with escalation to network specialists for unresolved or high-severity incidents.

### Feedback loop — do corrections feed back into the gold set / model?

Yes. Reviewer corrections are logged into the golden dataset and included in weekly evaluation audits. Repeated correction patterns trigger dataset updates and future model tuning priorities.
## Red-Team Findings

### The attack they ran

The attacker simulated a scenario where the AI received conflicting connectivity signals across regions. One carrier showed healthy network status while customer devices were simultaneously reporting intermittent outages and latency spikes. The AI produced a confident recommendation to keep the current routing because it overweighted the carrier-level signal and ignored customer-impact telemetry.

### Worst miss / what broke

The model failed to handle conflicting operational signals and generated an overly confident recommendation without escalating uncertainty. The dataset did not include enough examples where network-provider telemetry contradicted real customer experience. The AI optimized for the strongest signal instead of recognizing ambiguity and requesting human review.

### Severity

High

### New gold row I’m adding

Input: Carrier dashboard reports healthy network status, but enterprise IoT fleet shows repeated latency spikes and intermittent disconnects across multiple regions.

Expected output: Surface conflicting signals, lower confidence score, recommend human review, and investigate customer-impact telemetry before suggesting routing changes.

Edge case: Y

Judge type: rule + LLM

# Compounding System Design

## Feedback Loops

| Loop | Input | Output | Compounds? | Status |
|------|-------|--------|-----------|--------|
| Recursive Learning | Human corrections, rejected AI recommendations, operator overrides, and final incident outcomes | Updated golden dataset rows, better evaluation rules, and improved future recommendations | Y | broken |
| Cross-Domain Transfer | Connectivity incidents across customers, countries, carriers, roaming partners, SIM behavior, and support tickets | Failure patterns found in one fleet improve diagnosis for similar fleets and regions | Y | active |
| Network Intelligence | Aggregated SIM/eSIM telemetry, usage drops, latency patterns, roaming failures, and recovery outcomes | Fleet benchmarks, anomaly baselines, and “fleets like yours” intelligence | Y | broken |

**Broken loop identified by partner:**  
Network Intelligence — the underlying data exists, but it is not yet clearly surfaced as customer-visible intelligence.

**Fix plan:**  
Add fleet benchmarking and shared incident intelligence into the copilot. Example: “Fleets using this roaming partner are seeing similar latency spikes” or “Your outage pattern matches a known roaming issue detected in other regions.”

---

## Context Connectivity

Connectivity knowledge flows from SIM telemetry, roaming partner signals, carrier performance, device behavior, support tickets, customer incidents, and operator corrections into the AI copilot.

The main silo is that corrections, customer-specific policies, support context, and final incident outcomes may stay inside separate tools or teams. If those signals do not feed back into the golden dataset and recommendation system, the product scales usage but does not fully learn.

---

## Governance Policy

**Scope:**  
AI-assisted detection, diagnosis, prioritization, recommendation, and escalation for SIM/eSIM connectivity incidents, roaming issues, usage drops, latency problems, and customer-impacting network anomalies.

**Autonomy boundaries:**  
The AI can summarize incidents, identify likely causes, recommend next actions, and draft escalation notes. It cannot automatically change carrier routing, modify customer policies, disable SIMs, or execute high-risk remediation without human approval.

**Escalation triggers:**  
Low confidence score, conflicting telemetry, high-value enterprise customer impact, roaming policy conflict, repeated failed recommendations, suspected hallucination, unsupported diagnosis, missing evidence, or any action that could affect live customer connectivity.

**Audit cadence:**  
Real-time monitoring for confidence, latency, and safety flags. Weekly golden dataset evaluation, hallucination review, and failed recommendation audit. Monthly review of operator overrides, drift trends, policy conflicts, and model/provider performance.

**Regulatory exposure (EU AI Act / other):**  
EU AI Act, GDPR, telecom operational compliance, customer data protection requirements, and internal security/audit policies apply. Risk tier: limited. Controls include human approval for customer-impacting actions, audit logs for AI recommendations, confidence thresholds, data minimization in prompts, no training on customer-sensitive data without approval, golden dataset testing, and escalation paths for low-confidence or high-risk cases.

---

## Agent Topology

The system can use multiple specialized agents, but all high-risk actions require human approval.

- **Incident Triage Agent** — can detect anomalies and summarize incidents; cannot execute remediation. Approval owner: operations team.
- **Network Diagnosis Agent** — can analyze SIM, roaming, carrier, and telemetry signals; cannot change routing. Approval owner: network specialist.
- **Recommendation Agent** — can suggest next-best actions and draft escalation notes; cannot trigger live changes. Approval owner: operations lead.
- **Policy Guardrail Agent** — can check customer policies and roaming restrictions; cannot override policy. Approval owner: product/ops owner.
- **Human Review Layer** — approves, edits, rejects, or escalates recommendations before any customer-impacting action.

The agents can analyze, summarize, recommend, and draft. They cannot execute live connectivity changes, carrier routing changes, SIM status changes, or customer-impacting remediation without human approval.

---

## Shadow AI Audit

| Tool | Owner | Risk Level | Decision |
|------|-------|-----------|----------|
| ChatGPT / Claude used for incident summaries | Support / Operations | M | govern |
| Spreadsheet-based manual AI analysis | Operations | M | govern |
| Unapproved scripts or prompts recommending carrier changes | Network / Ops | H | kill |

**Total tools found:**  
3

**Tools after triage:**  
2

**Estimated hidden spend:**  
Medium — mainly productivity-tool usage and manual analysis, but risk is high if unapproved tools influence customer-impacting connectivity decisions.

---

### Shadow AI Audit

| Tool | Owner | Risk Level | Decision |
|------|-------|-----------|----------|
| | | H / M / L | keep / govern / kill |
| | | H / M / L | keep / govern / kill |
| | | H / M / L | keep / govern / kill |

**Total tools found:**
**Tools after triage:**
**Estimated hidden spend:**

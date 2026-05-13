# Compounding System Design

## Feedback Loops

| Loop | Input | Output | Compounds? | Status |
|------|-------|--------|-----------|--------|
| Recursive Learning | Operator corrections, rejected AI suggestions, and final incident outcomes | Better golden dataset rows and improved future recommendations | Y | broken |
| Cross-Domain Transfer | Incidents across customers, countries, carriers, roaming partners, and SIM behavior | Patterns from one fleet help diagnose similar issues in other fleets | Y | active |
| Network Intelligence | Aggregated SIM/eSIM telemetry, latency patterns, roaming failures, and recovery outcomes | Benchmarks, anomaly baselines, and “fleets like yours” insights | Y | broken |

**Broken loop identified by partner:**  
Network Intelligence — the copilot can see useful telecom patterns, but those insights are not yet clearly shown back to customers as benchmarking or shared incident intelligence.

**Fix plan:**  
Add anonymized fleet benchmarking and shared incident insights into the copilot. For example: “Fleets using this roaming partner are seeing similar latency spikes” or “Your issue matches a known pattern seen across similar fleets.”

---

## Context Connectivity

Connectivity knowledge should flow from SIM telemetry, roaming partner signals, carrier performance, support tickets, customer incidents, and operator corrections into the AI copilot.

Today, the main risk is that useful knowledge stays in silos. Corrections may remain in tickets, Slack, or an operator’s head instead of improving the golden dataset and future recommendations.

---

## Governance Policy

**Scope:**  
AI-assisted detection, diagnosis, prioritization, recommendation, and escalation for SIM/eSIM connectivity incidents.

**Autonomy boundaries:**  
The AI can analyze, summarize, recommend, and draft. It cannot independently switch carriers, change routing, disable or modify SIMs/eSIMs, override customer policies, make billing decisions, or take live customer-impacting action without human approval.

**Escalation triggers:**  
Confidence below 70%, conflicting telemetry, high-value customer impact, roaming or policy conflict, missing evidence, suspected hallucination, or any action affecting live customer connectivity.

**Audit cadence:**  
Real-time monitoring for confidence, latency, and safety flags. Weekly review of golden dataset results, hallucinations, and failed recommendations. Monthly review of drift, overrides, policy conflicts, and model performance.

**Regulatory exposure (EU AI Act / other):**  
EU AI Act, GDPR, telecom operational compliance, customer data protection, and internal security policies. Risk is limited, but controls are needed because the copilot influences operational decisions.

---

## Agent Topology

The system may use multiple agents, but customer-impacting actions require human approval.

- Incident Triage Agent: detects anomalies and summarizes incidents. Cannot execute remediation.
- Network Diagnosis Agent: analyzes SIM, carrier, roaming, and telemetry signals. Cannot change routing or SIM status.
- Recommendation Agent: suggests next-best actions and drafts escalation notes. Cannot trigger live changes.
- Policy Guardrail Agent: checks customer policies, roaming limits, and automation boundaries. Cannot override policy.
- Human Review Layer: approves, edits, rejects, or escalates AI recommendations before any customer-impacting action.

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
Medium — mostly productivity-tool usage and manual analysis. Risk becomes high if unapproved tools influence live connectivity decisions.

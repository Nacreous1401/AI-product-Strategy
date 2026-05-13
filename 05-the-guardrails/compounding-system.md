# Compounding System Design

## Feedback Loops

| Loop | Input | Output | Compounds? | Status |
|------|-------|--------|-----------|--------|
| Recursive Learning | Operator corrections, rejected AI suggestions, final incident outcomes | Better golden dataset rows and improved future recommendations | Y | broken |
| Cross-Domain Transfer | Incidents across customers, countries, carriers, roaming partners, and SIM behavior | Patterns from one fleet help diagnose similar issues in other fleets | Y | active |
| Network Intelligence | Aggregated SIM/eSIM telemetry, latency patterns, roaming failures, and recovery outcomes | Benchmarks, anomaly baselines, and “fleets like yours” insights | Y | broken |

**Loops mapped:**  
3

**Loops that actually compound:**  
3

**Active / Broken / Missing:**  
1 / 2 / 0

**Broken loop identified by partner:**  
Network Intelligence — the copilot can see useful telecom patterns, but those insights are not yet clearly shown back to customers as benchmarking or shared incident intelligence.

**Fix plan:**  
Add anonymized fleet benchmarking and shared incident insights into the copilot. For example: “Fleets using this roaming partner are seeing similar latency spikes” or “Your issue matches a known pattern seen across similar fleets.” Keep all insights aggregated and anonymized.

---

## Context Connectivity

Connectivity knowledge should flow from SIM telemetry, roaming partner signals, carrier performance, support tickets, customer incidents, and operator corrections into the AI copilot.

Today, the main risk is that useful knowledge stays in silos. Corrections may remain in tickets, Slack, or an operator’s head instead of improving the golden dataset and future recommendations.

**Where knowledge silos:**  
Support tickets, customer policies, operator corrections, final incident outcomes, and roaming partner intelligence may sit in separate tools.

---

## Governance Policy

**Scope:**  
AI-assisted detection, diagnosis, prioritization, recommendation, and escalation for SIM/eSIM connectivity incidents.

**What this policy covers:**  
Incident summaries, diagnostic explanations, anomaly detection, confidence scoring, recommended next actions, escalation drafts, and human review workflows.

**What it excludes:**  
The AI cannot independently switch carriers, change routing, disable or modify SIMs/eSIMs, override customer policies, make billing or contract decisions, make legal/compliance decisions, or take any live customer-impacting action without human approval.

**Autonomy boundaries:**  
The AI can analyze, summarize, recommend, and draft.  
The AI cannot execute live connectivity changes without approval.

**Decision boundaries:**  
- Incident summaries and diagnostics: auto  
- Recommended actions and escalation drafts: human approval  
- Carrier changes, SIM changes, policy exceptions, billing decisions: never auto  

**Escalation triggers:**  
- Confidence below 70%  
- Conflicting telemetry  
- High-value customer impact  
- Roaming or policy conflict  
- Missing evidence  
- Suspected hallucination  
- Any action affecting live customer connectivity  

**Audit cadence:**  
Real-time monitoring for confidence, latency, and safety flags.  
Weekly review of golden dataset results, hallucinations, and failed recommendations.  
Monthly review of drift, overrides, policy conflicts, and model performance.

**Audit ownership:**  
- Real-time safety: engineering / operations  
- Weekly eval review: product + operations  
- Monthly governance review: product + security / compliance  

**Regulatory exposure:**  
EU AI Act, GDPR, telecom operational compliance, customer data protection, and internal security policies.

**Risk tier:**  
Limited

**Controls in place:**  
Human approval for customer-impacting actions, audit logs, confidence thresholds, data minimization, no training on sensitive customer data without approval, golden dataset testing, and escalation paths for risky cases.

---

## Agent Topology

The system may use multiple agents, but customer-impacting actions require human approval.

- **Incident Triage Agent**  
  Detects anomalies and summarizes incidents.  
  Cannot execute remediation.  
  Approval owner: operations team.

- **Network Diagnosis Agent**  
  Analyzes SIM, carrier, roaming, and telemetry signals.  
  Cannot change routing or SIM status.  
  Approval owner: network specialist.

- **Recommendation Agent**  
  Suggests next-best actions and drafts escalation notes.  
  Cannot trigger live changes.  
  Approval owner: operations lead.

- **Policy Guardrail Agent**  
  Checks customer policies, roaming limits, and automation boundaries.  
  Cannot override policy.  
  Approval owner: product / operations owner.

- **Human Review Layer**  
  Approves, edits, rejects, or escalates AI recommendations before any customer-impacting action.

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

---

## Shadow AI Action Plan

**Consolidate:**  
Use the approved AI Connectivity Copilot for incident summaries, diagnostics, and escalation drafts instead of separate ad-hoc tools.

**Approve:**  
Allow ChatGPT/Claude only for low-risk drafting and summarization, with no sensitive customer data and no live operational decisions.

**Block:**  
Remove unapproved scripts or prompts that recommend carrier switching, SIM changes, routing changes, or other customer-impacting actions.

**Policy draft:**  
Maintain an approved AI tool catalog. Allow low-risk AI usage with clear data rules. Govern spreadsheet-based analysis. Block any unapproved AI tool that can affect connectivity, routing, SIM status, billing, customer policy, or customer remediation.

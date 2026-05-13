# Compounding System Design

## Feedback Loops

| Loop | Input | Output | Compounds? | Status |
|------|-------|--------|-----------|--------|
| Recursive Learning | Human corrections, rejected AI recommendations, operator overrides, and final incident outcomes | Updated golden dataset rows, better evaluation rules, and improved future recommendations | Y | broken |
| Cross-Domain Transfer | Connectivity incidents across customers, countries, carriers, roaming partners, SIM behavior, and support tickets | Failure patterns found in one fleet improve diagnosis for similar fleets and regions | Y | active |
| Network Intelligence | Aggregated SIM/eSIM telemetry, usage drops, latency patterns, roaming failures, and recovery outcomes | Fleet benchmarks, anomaly baselines, and “fleets like yours” intelligence | Y | broken |


**Broken loop identified by partner:**  


**Fix plan:**  

---

## Context Connectivity
<!-- How does knowledge flow across teams and domains? Where does it silo? -->


---

## Governance Policy

**Scope:**  
AI-assisted detection, diagnosis, prioritization, recommendation, and escalation for SIM/eSIM connectivity incidents, roaming issues, usage drops, latency problems, and customer-impacting network anomalies.

**What this policy covers:**  
The policy covers AI-generated incident summaries, diagnostic explanations, anomaly detection, confidence scoring, recommended next actions, escalation drafts, and human review workflows for connectivity operations.

**What it excludes:**  
This policy does not allow the AI to independently execute live network changes, switch roaming partners, disable or modify SIMs/eSIMs, override customer-specific policies, make billing or contract decisions, make legal/compliance decisions, or take any action that directly affects customer connectivity without human approval.

**Autonomy boundaries:**  
The AI can summarize incidents, identify likely causes, recommend next actions, and draft escalation notes. It cannot automatically change carrier routing, modify customer policies, disable SIMs, or execute high-risk remediation without human approval.

**Decision boundaries:**  
- Incident summaries and diagnostic explanations: auto  
- Recommended next-best actions or escalation drafts: human approval  
- Carrier routing changes, SIM changes, customer policy exceptions, or billing changes: never auto  

**Escalation triggers:**  
Low confidence score, conflicting telemetry, high-value enterprise customer impact, roaming policy conflict, repeated failed recommendations, suspected hallucination, unsupported diagnosis, missing evidence, or any action that could affect live customer connectivity.

**Audit cadence:**  
Real-time monitoring for confidence, latency, and safety flags. Weekly golden dataset evaluation, hallucination review, and failed recommendation audit. Monthly review of operator overrides, drift trends, policy conflicts, and model/provider performance.

**Audit ownership:**  
- Real-time safety and latency monitoring: engineering / operations  
- Weekly golden dataset review: product + operations  
- Monthly drift and policy review: product + security / compliance  

**Regulatory exposure (EU AI Act / other):**  
EU AI Act, GDPR, telecom operational compliance, customer data protection requirements, and internal security/audit policies apply.

**Risk tier:**  
Limited

**Controls in place:**  
Human approval for customer-impacting actions, audit logs for AI recommendations, confidence thresholds, data minimization in prompts, no training on customer-sensitive data without approval, golden dataset testing, and escalation paths for low-confidence or high-risk cases.

---

## Agent Topology

The system can use multiple specialized agents, but all high-risk actions require human approval.

- **Incident Triage Agent**  
  Can detect anomalies, summarize incidents, and identify abnormal usage, latency, or disconnect patterns.  
  Cannot execute remediation or change customer connectivity.  
  Approval owner: operations team.

- **Network Diagnosis Agent**  
  Can analyze SIM, roaming, carrier, network, and telemetry signals to identify likely root causes.  
  Cannot change routing, switch carriers, or modify SIM status.  
  Approval owner: network specialist.

- **Recommendation Agent**  
  Can suggest next-best actions, escalation paths, and customer communication drafts.  
  Cannot trigger live operational changes or customer-impacting actions.  
  Approval owner: operations lead.

- **Policy Guardrail Agent**  
  Can check customer-specific policies, roaming restrictions, automation boundaries, and compliance rules.  
  Cannot override customer policy or approve exceptions alone.  
  Approval owner: product / operations owner.

- **Human Review Layer**  
  Can approve, edit, reject, or escalate AI recommendations before any customer-impacting action.  
  Owns final decision-making for live connectivity changes.

The agents can analyze, summarize, recommend, and draft. They cannot execute live connectivity changes, carrier routing changes, SIM status changes, billing changes, policy overrides, or customer-impacting remediation without human approval.

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

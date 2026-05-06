# Cost Curve & Pricing Strategy

## Cost Model

| Cost Category | Per-User/Month | Notes |
|--------------|----------------|-------|
| Inference (primary model) |$18 |Used for complex incident analysis, recommendations, and summaries. |
| Inference (cascading/triage) |$6 |Smaller model handles basic queries and filtering before escalating. |
| Infrastructure |$8 |Cloud hosting, APIs, monitoring, and processing pipelines. |
| Data/storage |$4 |Stores connectivity logs, incident history, and AI interaction data. |
| Human-in-the-loop |$10 |Operations teams validate AI recommendations and edge cases. |
| **Total AI COGS** |$46 | |

## Cascading Strategy
<!-- Cheap model → frontier model routing logic -->

**Triage model:**  
Small low-cost model for simple classification and basic troubleshooting.
**Frontier model:**  
GPT-4 class model for deep analysis and complex recommendations.
**Routing rule:**  
Simple incidents go to cheaper model first. Escalate only high-risk or unclear cases to frontier model.
**Expected cascade ratio:**  
70% cheap model / 30% frontier model

## Pricing Model

**Current pricing:**  
Traditional platform pricing based on SIMs, connectivity usage, and enterprise contracts.
**Proposed AI pricing:**  
Add AI Copilot premium tier for operations and product teams.
**Model:** seat-based / usage-based / outcome-based / hybrid  
Hybrid (seat-based + usage-based)

## Stress Tests

| Scenario | Impact on Margin | Response |
|----------|-----------------|----------|
| Inference costs 3x |AI margins drop significantly on heavy users. |Increase routing to cheaper models and limit unnecessary AI calls.|
| Heaviest segment doubles |Enterprise customers generate high compute costs. |Introduce enterprise AI usage tiers and fair usage limits. |
| Model provider raises prices 50% |AI feature profitability reduces quickly. |Shift workloads to backup providers and renegotiate contracts. |

## Board One-Pager
<!-- Before/After: Old SaaS revenue vs. AI usage revenue for your product -->

**Before (traditional SaaS):**  
Revenue mainly came from connectivity subscriptions, SIM usage, and platform access.
**After (AI-enabled):**  
Additional revenue comes from AI-assisted operations, automation, predictive insights, and premium AI workflows.
**Net margin shift:**  
Lower short-term margins due to AI costs, but higher long-term expansion revenue and customer stickiness.

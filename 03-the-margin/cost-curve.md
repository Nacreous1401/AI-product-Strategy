# Cost Curve & Pricing Strategy
## Packaging Decision

| Leader | Filler | Killer | Killer usage % | Bundle or add-on |
|:------:|:------:|:------:|:--------------:|:----------------:|
|AI Connectivity Incident Copilot| AI-generated operational summaries and reports |Automated incident resolution recommendations | 80% | Bundle into enterprise connectivity platform tiers, with premium AI automation add-on for advanced workflows.|

**70% rule:** if Killer usage is <70%, it is probably an add-on.  

## Cost Model

| Cost Category | Per-User/Month | Notes |
|--------------|:--------------:|:-----:|
| Inference (primary model) |$12 |Used for complex incident analysis, recommendations, and summaries. |
| Inference (cascading/triage) |$4 |Smaller model handles basic queries and filtering before escalating. |
| Infrastructure |$8 |Cloud hosting, APIs, monitoring, and processing pipelines. |
| Data/storage |$4 |Stores connectivity logs, incident history, and AI interaction data. |
| Human-in-the-loop |$8|Operations teams validate AI recommendations and edge cases. |
| **Total AI COGS** |$36 | |

## Cascading Strategy
<!-- Cheap model → frontier model routing logic -->

**Triage model:**   
Low-cost model for classification, summaries, alerts, and basic troubleshooting.  
**Frontier model:**  
Claude Sonnet / GPT-4 class model for deep incident analysis and complex recommendations.  
**Routing rule:**  
Simple operational tasks stay on smaller models. Escalate only unclear, high-risk, or enterprise-critical incidents to frontier models.  
**Expected cascade ratio:**  
85% low-cost model / 15% frontier model  

## Pricing Model

**Current pricing:**  
Traditional platform pricing based on SIMs, connectivity usage, and enterprise contracts.  
**Proposed AI pricing:**  
AI Copilot premium tier for intelligent operations, diagnostics, and automation.
**Model:** seat-based / usage-based / outcome-based / hybrid  
Hybrid (seat-based + usage-based)  

## Stress Tests

| Scenario | Impact on Margin | Response |
|----------|:---------------:|:--------:|
| Inference costs 3x |Frontier-model usage quickly reduces margins. |Increase routing to smaller models, reduce unnecessary output generation, and optimize prompts.|
| Heaviest segment doubles |Large enterprise fleets generate higher AI processing costs. |Introduce enterprise AI usage tiers and premium automation packages.|
| Model provider raises prices 50% |AI profitability compresses if dependency remains too high on one provider. |Use multi-model routing, caching, and backup providers to reduce exposure.|

## Board One-Pager
<!-- Before/After: Old SaaS revenue vs. AI usage revenue for your product -->

**Before (traditional SaaS):**  
Revenue mainly came from connectivity subscriptions, SIM lifecycle management, and platform access.  
**After (AI-enabled):**  
Revenue expands through AI-assisted operations, predictive diagnostics, automated incident resolution, and premium AI workflows.  
**Net margin shift:**  
Short-term margins decrease slightly due to inference costs, but long-term expansion revenue and customer stickiness improve significantly.  

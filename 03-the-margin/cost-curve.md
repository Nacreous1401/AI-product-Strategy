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

### Before (traditional SaaS):

- **Current pricing:**  
Enterprise connectivity subscriptions based on SIM volume, connectivity usage, and platform access.

- **Current gross margin:**  
~75%

- **Value framed as:**  
Reliable global IoT connectivity management platform.

---

### After (AI-enabled):

- **Proposed pricing:**  
Hybrid pricing model with a $499/month AI platform fee plus $2 per AI-assisted investigation.

- **AI COGS per user/month:**  
$36

- **Expected gross margin:**  
~68%

- **Value framed as:**  
AI-assisted operational intelligence platform for proactive connectivity management and automated incident investigation.

---

### Net margin shift:

- Margin moves from 75% to 68%.

- Explain why the margin changes:  
Margins decrease because AI introduces variable inference and processing costs that scale with usage. However, the platform captures more operational value, increases customer dependency, and creates new expansion revenue opportunities beyond basic connectivity management.

---

### Why this is still a good business:

The AI layer increases revenue per customer through premium operational workflows while improving customer retention and stickiness. Customers become more dependent on the platform because the AI copilot is integrated into daily troubleshooting and incident management processes. Even with slightly lower gross margins, higher expansion revenue, stronger differentiation, and improved net revenue retention create a stronger long-term business.

---

### Board-ready narrative:

Our traditional SaaS business generates strong margins through connectivity subscriptions, but growth is tied mainly to SIM and usage expansion. The AI layer allows us to monetize operational workflows directly by helping enterprise teams investigate and resolve connectivity issues faster. While AI introduces variable inference costs, we control margin exposure through cascading models, multi-model routing, and selective use of frontier models only for complex investigations. The primary risk is rising model-provider costs or dependency on a single provider, which we mitigate through provider abstraction and fallback routing strategies. We believe the long-term value comes from becoming the operational intelligence layer customers rely on daily, not just the connectivity layer underneath.

**The bet works if...**  
customers adopt AI-assisted operational workflows frequently enough that increased expansion revenue, retention, and platform dependency outweigh the additional AI operating costs.



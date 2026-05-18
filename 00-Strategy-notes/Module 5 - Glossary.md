# Module 5 Glossary

*The terms introduced in Module 5 - The Guardrails. For earlier modules, see [`Module 1 - Glossary.md`](./Module%201%20-%20Glossary.md), [`Module 2 - Glossary.md`](./Module%202%20-%20Glossary.md), [`Module 3 - Glossary.md`](./Module%203%20-%20Glossary.md), and [`Module 4 - Glossary.md`](./Module%204%20-%20Glossary.md). For the full course-wide reference, see [`Glossary.md`](./Glossary.md).*

Two sections:

1. **Compounding & Systems** - the vocabulary for products that learn from use rather than just scale with it.
2. **Governance, Agents & Shadow AI** - everything Module 5 introduces about agents that pick actions, policies that hold up under audit, and tools nobody approved.

---

## 1. Compounding & Systems

### Active / Broken / Missing

The three honest status labels for a feedback loop. **Active** = shipping and learning today. **Broken** = it exists on paper but doesn't actually feed back (corrections logged but never reviewed, retraining "scheduled" but never run). **Missing** = the loop just isn't there. Most rows on a real-product audit come back `missing`, and that *is* the finding.
*Seen in: M5, Slide 8 (Design Your Compounding System).*

### Compounding system

A product whose value grows non-linearly with use because each interaction makes the next one better. Distinct from a product that merely *scales* (more users, same quality). The economic difference is that compounding products have falling cost per win over time; scaling products have linear cost.
*Seen in: M5, Slide 6.*

### Context connectivity

How knowledge flows across teams, products, or domains inside an org - and where it silos. A context-connectivity break is the single most common reason a feedback loop dies: the support team's corrections never reach the eng team's models, so the product never actually learns from real usage. Captured as a one-line field in `compounding-system.md`.
*Seen in: M5, Slide 8.*

### Cross-domain transfer

Compounding mechanism where improvements in one product or feature lift adjacent products or features that share context. ServiceTitan is the anchor: 32 products on one vertical stack, where HVAC scheduling data makes invoicing smarter, which makes dispatching smarter, in a tight loop.
*Seen in: M5, Slide 6.*

### Data flywheel

A specific kind of compounding system where user data feeds a model that produces better outputs, which attracts more users, which produces more data, which improves the model further. Introduced in M2 in the moat context; M5 puts it inside the compounding-systems framework as one of three mechanisms. See [`Module 2 - Glossary.md`](./Module%202%20-%20Glossary.md) for the M2 framing.
*Seen in: M5, Slides 6-8 (re-anchored from M2).*

### Feedback loop

A single learning circuit in your product. The minimal description has four parts: **input** (what data goes in), **output** (what improves), **compounds Y/N** (is it a flywheel or just a feature?), and **status** (active / broken / missing).
*Seen in: M5, Slide 8.*

### Freeze test

The forcing function for telling compounding from scaling. Mentally freeze the product for **3 months** (one frontier-model cycle) - no updates, no model swaps, no improvements. If it's still winning, congratulations, you're scaling, not compounding. The 12-month version that's circulated in other content is too long for an AI cycle; the M5 version uses 3 months on purpose.
*Seen in: M5, Slide 8.*

### Frontier cycle

A rough unit of time in AI - about 3 months between major frontier-model releases (GPT, Claude, Gemini, etc.). Used in the freeze test as a more honest forcing function than the older 12-month version, since 12 months of frozen AI feels like 10 years of frozen anything else.
*Seen in: M5, Slide 8.*

### Network intelligence

Compounding mechanism where patterns across the whole user base or fleet improve individual interactions - privacy-gated, usually anonymized. The aggregate is smarter than any single user's history. Anchor: Duolingo's lesson difficulty adapts based on what stumped learners globally, not just you.
*Seen in: M5, Slide 6.*

### Recursive learning

Compounding mechanism where the product's own outputs (and corrections to them) feed back into the model. The cleanest anchor: every Duolingo learner interaction sharpens lesson difficulty for the next learner.
*Seen in: M5, Slide 6.*

### Scales vs. compounds

The central reframe of the first half of M5. *Scales*: ↑ volume, flat quality, linear cost - a commodity with variable costs. *Compounds*: each touch → smarter next touch, falling cost per win. Most AI products scale without compounding and don't realise it until a competitor's compounding loop eats their lunch.
*Seen in: M5, Slide 6.*

---

## 2. Governance, Agents & Shadow AI

### Agent

An AI system that picks its own actions, chains tools together, and loops until done - rather than producing a single response. Distinct from a chatbot in three ways that matter for governance: authorization scope, persistent memory, and chain-of-action liability. Introduced lightly in M3; M5 is where agent governance lives. See also [`Module 3 - Glossary.md`](./Module%203%20-%20Glossary.md) for the M3 cost framing.
*Seen in: M5, Slides 10-11.*

### Agent topology

A short map of who can do what, drawn at the system level. For each agent: what it can do, what it can't do, and who approves what. Optional block in `compounding-system.md` - skip unless your product actually ships agents.
*Seen in: M5, Slide 14.*

### Allow-list (whitelist)

The explicit list of tools, APIs, or actions an agent is permitted to call. The opposite of a deny-list: everything not on the list is forbidden by default. One of the four agent governance knobs (Tool Calls). Best practice: short list, rate-limited, fully logged.
*Seen in: M5, Slide 10.*

### Audit cadence

How often you review the AI system's outputs and decisions against your golden dataset or live traffic. Real-time / daily / weekly / monthly / quarterly. The M5 governance policy field. Naming the owner matters as much as picking the cadence - "weekly" without an owner is aspirational.
*Seen in: M5, Slides 13-14.*

### Autonomy boundaries

What an agent can do solo vs. what needs a human. Two key splits: **draft ≠ send** (it can write the email; sending requires approval) and **read ≠ write** (it can pull data; modifying or sending it is gated). One of the four agent governance knobs.
*Seen in: M5, Slides 10, 14.*

### Bias posture

Your public stance on how the AI handles fairness, demographic differences, and edge-case populations - and what mitigations you've put in place. Part of the Level-3 (Governance = GTM) maturity story; appears in enterprise procurement questionnaires.
*Seen in: M5, Slide 9.*

### Chain (agent chain)

A sequence of agents where one agent's output is the next agent's input. The governance question: when agent B fails on agent A's output, who owns the handoff? The fourth governance knob is about naming ownership at each handoff and having a "stop the chain" trigger if any agent in the line fails its eval.
*Seen in: M5, Slide 10.*

### DPA (Data Processing Agreement)

A contract between a customer and a vendor that defines how the vendor will handle the customer's data - retention, access, geography, training-data use. Step 2 of the shadow AI audit (Risk) is partly about asking "does this tool have a DPA we've signed?" Many shadow AI tools don't, which is the risk.
*Seen in: M5, Slide 13.*

### Escalation triggers

When the AI must hand off to a human. Common triggers: confidence below threshold, customer-facing novel content, anything legal / financial / medical, anything irreversible, repeated turns in a single conversation. The M5 governance policy field; specifying them is what separates a real policy from a wish-list.
*Seen in: M5, Slide 14.*

### EU AI Act

The European Union's regulation of AI systems by risk tier - minimal, limited, high, and prohibited. Force of law in the EU. Most B2B products land in *limited risk* (chatbots, productivity, customer service); some in *high risk* (employment, credit, biometric). The first thing to reference in the Regulatory Exposure field of your governance policy.
*Seen in: M5, Slides 5, 9, 14.*

### Frontier model

The most powerful (and expensive) model from a provider. Cross-referenced from M3 because M5's "frontier cycle" in the freeze test refers to the ~3-month cadence at which new frontier models ship. See [`Module 3 - Glossary.md`](./Module%203%20-%20Glossary.md) for the M3 cost framing.
*Seen in: M5, Slide 8.*

### GDPR (General Data Protection Regulation)

EU privacy regulation governing personal data of EU residents, regardless of where the data is processed. In an AI context: minimize personal data in prompts, don't train on customer PII without consent, document a lawful basis for processing. Standard line in the Regulatory Exposure field.
*Seen in: M5, Slides 5, 14.*

### Governance = GTM

Level 3 of the Responsible AI Maturity ladder. The reframe that governance done well is a *sales asset*, not a compliance burden. Salesforce's Einstein Trust Layer is the textbook case - they sell governance as part of the product pitch, and enterprise buyers ask for governance artifacts by name in procurement.
*Seen in: M5, Slide 9.*

### Hidden spend

The total monthly AI tool cost that doesn't show up on a sanctioned expense line. The summary stat in the Shadow AI Audit table that lights up CFO eyes - it's the budget for the governed alternative once you consolidate. Often surprisingly large in mid-size orgs.
*Seen in: M5, Slide 19.*

### HIPAA (Health Insurance Portability and Accountability Act)

US healthcare-data privacy law. Relevant for any product that handles patient data; impacts memory class choices (you almost never want long-term or shared memory for PHI), audit cadence, and Business Associate Agreements with vendors.
*Seen in: M5, Slide 10 (memory governance), Slide 14.*

### Keep / Govern / Kill

The three triage decisions for each tool surfaced in a shadow AI audit. **Keep**: safe and useful as-is. **Govern**: useful but needs guardrails (DPA, allow-list, monitoring). **Kill**: the data path is unsafe and there's no realistic fix. "Medium" is the lazy answer in the Risk column; the Decision column should be one of three real options.
*Seen in: M5, Slide 19.*

### Memory (short / long / shared)

What an AI agent remembers between turns and between users. Three explicit classes: **short-term** (just this session, then wiped), **long-term** (persists across sessions for the same user), **shared** (across users - usually a hard no for customer-facing products, because customer A's data leaks to customer B). The third governance knob.
*Seen in: M5, Slide 10.*

### Model card

A short, public-ish document that describes a model's intended use, limitations, evaluation results, and known biases. Originated at Google. A standard Level-3 maturity artifact and a common enterprise-procurement ask.
*Seen in: M5, Slide 9.*

### Prompt injection

An attack where malicious instructions are embedded in a tool's input (a document, a webpage, a customer message) to make the AI ignore its system prompt and do something it shouldn't. The reason rate-limiting and tool whitelisting matter - they cap the blast radius when (not if) an injection lands.
*Seen in: M5, Slide 10.*

### Rate-limiting

A cap on how often an agent can call a particular tool (e.g. 10 refunds per hour). Pairs with allow-listing: even a permitted tool shouldn't be callable infinitely. One of the three sub-controls under the Tool Calls governance knob.
*Seen in: M5, Slide 10.*

### Regulatory exposure

Which legal regimes apply to your AI product - EU AI Act risk tier, plus GDPR / CCPA / HIPAA / SOC 2 / sector-specific (finance, healthcare, education). The M5 governance policy field. Be specific about both the regime *and* the risk tier inside it.
*Seen in: M5, Slide 14.*

### Responsible AI Maturity ladder

The three-level reframe of compliance. **Level 1: Compliance** (EU AI Act, GDPR - minimum bar). **Level 2: Trust Architecture** (evals, confidence UX, reliability contracts - what M4 built). **Level 3: Governance = GTM** (model cards, bias posture, governance as a deal-closer). Most orgs plateau at Level 1 or 2.
*Seen in: M5, Slide 9.*

### Shadow AI

Any AI tool in use inside your org without sanctioned governance, allow-listing, or oversight. Includes both unauthorized external SaaS (ChatGPT, Claude, niche copilots) and employee-paid personal subscriptions used for work. The Samsung case is the canonical "what happens when shadow AI meets real data" story.
*Seen in: M5, Slides 12-13, 19.*

### SOC 2

A widely-used set of security and operational controls audited by an independent firm. Relevant for AI products because log retention, access control, and incident response sit inside the SOC 2 boundary. Often appears in the Regulatory Exposure field alongside (not instead of) EU AI Act and GDPR.
*Seen in: M5, Slide 14.*

### Tool calls

The function calls an agent makes to external systems - search, refund, send email, query database, etc. Every tool call is a potential risk surface, which is why the second governance knob bundles three controls together: allow-list (which tools), rate-limit (how often), log (every call, with reasoning and result).
*Seen in: M5, Slide 10.*

### Traditional RPA (Robotic Process Automation)

Pre-AI workflow automation - UiPath, Automation Anywhere, Blue Prism. Fixed paths, deterministic, breaks on edge cases, linear ROI. M5 contrasts it with agentic automation because finance teams will compare agent investments to the RPA budget line and the economics are completely different.
*Seen in: M5, Slide 11.*

### Trust Architecture

Level 2 of the Responsible AI Maturity ladder. What you built in M4 - golden datasets, confidence UX, reliability contracts, eval dashboards. Trust-as-infrastructure rather than trust-as-marketing. Most teams that take AI seriously land here; the jump to Level 3 (GTM) is what's left undone.
*Seen in: M5, Slide 9.*

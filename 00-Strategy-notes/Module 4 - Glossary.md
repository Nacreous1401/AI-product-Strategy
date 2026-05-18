# Module 4 Glossary

*The terms introduced in Module 4 — The Contract. For earlier modules, see [`Module 1 - Glossary.md`](./Module%201%20-%20Glossary.md), [`Module 2 - Glossary.md`](./Module%202%20-%20Glossary.md), and [`Module 3 - Glossary.md`](./Module%203%20-%20Glossary.md). For the full course-wide reference, see [`Glossary.md`](./Glossary.md).*

Two sections:

1. **AI Trust & Quality** — the technical vocabulary around evaluating, calibrating, and monitoring AI quality.
2. **Product Design & Legal** — how trust decisions show up in product UX and legal obligations.

---

## 1. AI Trust & Quality

### Calibration

The degree to which a model's stated confidence matches its actual accuracy. A well-calibrated model that says "I'm 80% sure" is right about 80% of the time. Poorly calibrated models are confidently wrong — which is worse than being wrong and uncertain.
*Seen in: M4 (confidence UX depends on calibration; without it, confidence scores mislead users).*

### Continuous monitoring

Sampling and scoring live production outputs on an ongoing basis to detect quality degradation before users notice. The defense against drift.
*Seen in: M4 (the highest level of eval maturity — catches problems the golden dataset alone can't).*

### Drift

When AI quality slowly degrades over time — often silently — because the model, the data, or the prompts changed. Quality drops 1% at a time, and by the time someone notices, trust is already damaged. The reason you need ongoing evals, not one-time testing.
*Seen in: M4 (drift is the silent killer of trust; continuous monitoring is the fix).*

### Eval / Eval harness

The automated test suite that scores whether your AI is producing good outputs against the golden dataset. Think of it as CI/CD for AI quality — it runs before every release and blocks bad deployments.
*Seen in: M4 (second level of eval maturity; the highest-leverage move for most teams).*

### Golden dataset

A labeled set of test cases that defines "good" for your specific product. It includes representative inputs, expected outputs, adversarial cases, and a scoring rubric. Versioned like code, used as a release gate — nothing ships unless it passes.
*Seen in: M4 (first artifact — the foundation of every other trust mechanism).*

### Hallucination

When the model produces an answer that sounds confident and is factually wrong. Unlike regular bugs which look wrong, hallucinations look right — the syntax is perfect, the tone is authoritative, the facts are invented. The Air Canada chatbot hallucinated a refund policy; the company paid for it.
*Seen in: M4 (the central risk Module 4 is designed to manage).*

### LLM-as-Judge

Using a model to grade other models' outputs at scale, calibrated against human judgments on the golden dataset. It can check thousands of outputs a day at a fraction of the cost of human review. Requires periodic recalibration to ensure the judge model's biases don't compound.
*Seen in: M4 (the scalable eval approach — used alongside golden datasets for production-grade quality).*

### Prompt rot

When the context around your prompts changes (new features, new data sources, updated model versions) and the old prompts no longer produce the same quality. A common cause of drift.
*Seen in: M4 (one of the mechanisms behind quality degradation over time).*

---

## 2. Product Design & Legal

### Confidence score

A numerical indicator — visible to the user or used internally — of how certain the model is about its output. The building block of confidence UX. Only useful if the model is well-calibrated.
*Seen in: M4 (the 85% legible system shows confidence scores; the 95% black box doesn't).*

### Confidence UX

The visible signals in your product that tell users how sure the AI is. Includes confidence scores, citations, hedged language, "I'm not certain" messages, and override buttons. The product-design expression of the "trust = perceived control" reframe.
*Seen in: M4 (second artifact — designing how the product behaves at different confidence levels).*

### Escalation path

The defined handoff from AI to human (or to a different system) when the AI is uncertain or unable to handle a request. Part of the reliability contract. A good escalation path is a feature; a missing one is an incident report.
*Seen in: M4 (reliability contract — what happens when the AI can't answer).*

### Feedback loop

The mechanism by which user corrections and flagged errors flow back to improve the model or the golden dataset. Without a feedback loop, human-in-the-loop is a one-way cost; with one, it's an investment that compounds.
*Seen in: M4 (reliability contract — how users report problems, and what happens with that feedback).*

### Human-in-the-loop (HITL)

Design pattern where a human reviews AI outputs at certain thresholds. Done well, it's a product feature: the human catches the hard cases, the AI handles the volume. Done badly, it's a crutch: if 50%+ of outputs need review, you haven't built an AI product. The percentage should be **decreasing** over time.
*Seen in: M4 (the line between feature and crutch depends on whether corrections feed back into the model).*

### Legibility

The degree to which a user can see into how and why the AI produced its output. A legible system shows sources, reasoning, and uncertainty. An illegible one gives a confident answer with no explanation. Legibility is what makes the 85% system more trusted than the 95% one.
*Seen in: M4 (the central comparison — legible systems build trust, black boxes destroy it).*

### Reliability contract

The explicit promise your product makes to users about quality, response time, escalation, and feedback loops. Not a legal document in the SLA sense — a product-level commitment that forces the team to decide what happens when things go wrong, before they go wrong.
*Seen in: M4 (third artifact — the capstone deliverable).*

### Separate legal entity defense

The argument that an AI chatbot's statements are not the company's statements — that the bot is a "separate legal entity." Tested in the Air Canada tribunal case. The tribunal rejected it. Your AI's outputs are your company's commitments, period.
*Seen in: M4 (the Air Canada case — the cautionary tale of the module).*

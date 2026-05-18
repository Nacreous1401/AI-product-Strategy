# Module 4 — The Contract

*Shareable companion notes. These walk you back through what the session covered, in case you want to review the arguments, examples, and frameworks at your own pace.*

---

## What this module is about

Module 1 asked what you are betting on. Module 2 asked whether the bet can survive contact with the market. Module 3 asked whether the economics work. Module 4 asks a fundamentally different question: **why will users trust the output enough to pay for it?**

The shift is real. Modules 1–3 were about value, defensibility, and money. Module 4 is about **promises** — specifically, the kind of promises your company is legally on the hook for the moment your AI says them out loud. The "Contract" in the title is not a metaphor.

This is also the most jargon-dense session in the course. Golden datasets, eval harnesses, LLM-as-Judge, human-in-the-loop, confidence UX, reliability contracts. The point is to close that vocabulary gap so the in-room time can be spent on your actual product.

You leave with three artifacts in your repo: a **golden dataset spec**, a **confidence UX design**, and a **reliability contract** (`04-the-contract/`).

---

## The Central Reframe: Trust ≠ Accuracy

This is the single most important idea in Module 4, and it is genuinely counterintuitive.

The instinct most teams build their roadmap around is "more accurate = more trusted." It's wrong.

> **Trust is a function of perceived control, not accuracy percentages.**

An **85% accurate system** that shows confidence scores, cites sources, and lets the user override the answer beats a **95% accurate black box** every single time. Users don't trust what they can't see into. Even when the black box is technically right more often, the moment it's confidently wrong with no warning, trust evaporates — and there's no way to claw it back.

This distinction matters because it changes what you build next. If you believe trust comes from accuracy, your roadmap is about better models and more training data. If you believe trust comes from perceived control, your roadmap is about **confidence UX, escalation paths, and transparency** — which are faster to ship and harder to copy.

### The 95% vs 85% Comparison

| | 95% Black Box | 85% Legible System |
|---|---|---|
| **Accuracy** | Higher | Lower |
| **Signals uncertainty?** | No — confidently wrong 5% of the time | Yes — scores, citations, "I'm not sure" |
| **User can correct?** | No | Yes — override and feedback loops |
| **Trust after a wrong answer** | Destroyed — felt like betrayal | Preserved — the system warned you |
| **Net trust** | Lower | Higher |

The counterintuitive conclusion: **invest in how you signal uncertainty before you invest in reducing it.**

---

## The Air Canada Case

A major airline deployed a customer service chatbot. The chatbot invented a refund policy that didn't exist — specifically, a bereavement fare discount that the airline had never offered. A grieving customer relied on the bot's promise, booked a flight at full price expecting the refund, and then tried to collect. The airline refused.

The customer took it to a tribunal. The airline's legal defense: the chatbot was a **"separate legal entity"** — don't blame us, blame the robot.

The tribunal ruled against the airline. The reasoning: it doesn't matter whether the answer came from a person, a webpage, or a chatbot. **If it's on your platform, under your brand, it's your promise.** The chatbot spoke for the company whether the company intended it to or not.

### What this means for product teams

1. **Your AI's outputs are your company's commitments.** There is no legal firewall between "the model said it" and "the company said it."
2. **Confidence without calibration is a liability.** The chatbot didn't hedge. It didn't say "I'm not sure about this policy." It stated a nonexistent policy as fact. That confidence became a binding promise.
3. **The fix is operational, not legal.** Disclaimers don't protect you — the Air Canada bot had disclaimers. What protects you is building the system so it **doesn't confidently state things it isn't sure about.**

---

## Golden Datasets

A golden dataset is a labeled set of test cases that defines "good" for your specific product. It's versioned like code and used as a release gate — nothing ships unless it passes the golden dataset.

### What makes a golden dataset "golden"

- **Domain-specific.** Generic benchmarks tell you the model is smart. They don't tell you it works for your use case. Your golden dataset is the one that catches the failures your users would actually encounter.
- **Versioned.** The dataset changes as the product evolves. New edge cases get added. Old ones get retired. It's a living artifact, not a one-time test.
- **Used as a gate.** If a new model version, prompt change, or feature update degrades golden dataset performance, it doesn't ship. That's the discipline.

### Minimum viable golden dataset

You don't need thousands of test cases to start. You need:

1. **20–50 representative inputs** covering your core use cases.
2. **Expected outputs** — what "good" looks like for each one.
3. **5–10 adversarial inputs** — the edge cases that would be embarrassing or harmful if the model got them wrong (the "worst thing my AI could say with high confidence" exercise).
4. **A scoring rubric** — pass/fail for each case, or a 1–5 quality scale.

Start small. Run it manually if you have to. Automate later. The discipline of having a golden dataset matters more than its size.

---

## Eval Harnesses and LLM-as-Judge

### Eval harness

The automated test suite that scores whether your AI is producing good outputs against the golden dataset. Think of it as CI/CD for AI quality — it runs before every release and blocks bad deployments.

### LLM-as-Judge

Using a model to grade other models' outputs at scale. Instead of having a human read every AI response, you use a separate model (often a frontier model) to score outputs against the golden dataset criteria.

**Why this works:** Calibrated against human judgments on the golden dataset, an LLM-as-Judge can check thousands of outputs a day at a fraction of the cost of human review.

**Why this is tricky:** The judge model has its own biases. It needs calibration — you periodically check that the judge agrees with human reviewers, and you recalibrate when it drifts.

### The eval maturity spectrum

| Level | What it looks like | Risk |
|---|---|---|
| **No evals** | "We tried 20 prompts and they looked good" | You're flying blind |
| **Manual spot checks** | A PM reviews a sample before release | Better, but doesn't scale |
| **Automated golden dataset** | CI/CD pipeline runs golden dataset on every change | Strong baseline |
| **LLM-as-Judge + golden dataset** | Automated scoring at scale, calibrated against human labels | Production-grade |
| **Continuous monitoring** | Live production outputs get sampled and scored | Catches drift |

Most teams are at level 0 or 1. Getting to level 2 (automated golden dataset) is the highest-leverage move.

---

## Confidence UX

Confidence UX is the visible signals in your product that tell users how sure the AI is. This is the product-design implication of the "trust = perceived control" reframe.

### The confidence spectrum

At different confidence levels, your product should **behave differently**:

| Confidence | Product behavior | Example |
|---|---|---|
| **High (>90%)** | Act directly, show the answer | Autocomplete, auto-classify |
| **Medium (70–90%)** | Show the answer with caveats | "Here's what I found — here are the sources" |
| **Low (50–70%)** | Suggest, don't assert | "I'm not sure, but this might be relevant" |
| **Very low (<50%)** | Escalate or abstain | "I can't answer this confidently — here's who can" |

### Products that do this well

- **Perplexity** — citations on every claim. You can click through to verify.
- **Granola** — confidence indicators on transcription. It hedges where it's uncertain.
- **GitHub Copilot / Cursor** — suggestion style changes with confidence. Bold inline completions vs. softer, shorter suggestions.
- **Tesla Autopilot** — forced handoffs. The system makes you take the wheel when it's not confident. Confidence UX in physical form.

### The design principle

**"I'm not sure" is a feature, not a bug.** A system that says "I don't know" when it doesn't know is more trustworthy than one that always gives an answer. The discipline is building the product to distinguish between the two — and showing that distinction to the user.

---

## Human-in-the-Loop (HITL)

A design pattern where a human reviews AI outputs at certain thresholds.

**Done well:** It's a product feature. The human catches the hard cases, the AI handles the volume, and the user gets the best of both.

**Done badly:** It's a crutch that makes the team broke. If every output needs human review, you haven't built an AI product — you've built a very expensive workflow tool.

### When HITL is a feature vs. a crutch

| Signal | Feature | Crutch |
|---|---|---|
| **Trigger** | Confidence threshold — only low-confidence outputs get reviewed | Everything gets reviewed "just in case" |
| **Volume** | 5–15% of outputs | 50%+ of outputs |
| **Feedback loop** | Human corrections improve the model over time | Corrections go nowhere |
| **Cost trajectory** | Decreasing over time as model improves | Flat or increasing |

The goal is for HITL to be a **decreasing percentage** of total outputs. If it's not decreasing, your model isn't learning from the human input, and you have a scaling problem.

---

## Drift

When AI quality slowly degrades over time, often silently. The model or the inputs changed, and nobody noticed because the outputs still "looked fine" on a casual glance.

### Why drift happens

- **Model updates** — the provider ships a new version and your prompts behave slightly differently.
- **Data distribution shifts** — users start asking questions you didn't train for.
- **Prompt rot** — the context around your prompts changes (new features, new data sources) and the old prompts no longer produce the same quality.
- **Eval decay** — the golden dataset gets stale and stops catching new failure modes.

### Why drift is dangerous

It's silent. Quality drops 1% at a time. No single output is obviously wrong. But over weeks or months, the aggregate quality erodes, user trust decreases, and by the time someone notices, the damage is done.

**The fix:** Continuous monitoring. Sample live production outputs, score them against your golden dataset criteria, and set alerts for quality degradation.

---

## Reliability Contracts

The explicit promise your product makes to users about quality, response time, escalation, and feedback loops. This is the capstone artifact of Module 4.

### What a reliability contract contains

1. **Quality commitment** — what accuracy level you promise, and how you measure it.
2. **Response time** — how fast the AI responds, and what happens when it's slow.
3. **Escalation path** — what happens when the AI can't answer or is uncertain.
4. **Feedback mechanism** — how users report problems, and what happens with that feedback.
5. **Transparency** — what you disclose about how the AI works, its limitations, and when it's been updated.

### Why this matters

A reliability contract turns vague trust into a concrete promise. It forces the team to decide — in advance — what happens when things go wrong. Teams that skip this step discover their escalation path for the first time during an incident, which is exactly when you don't want to be improvising.

---

## Hallucination

When the model produces an answer that sounds confident and is factually wrong. The Air Canada case is a hallucination in the wild — the bot stated a policy that didn't exist, with full confidence, and the company paid for it.

### Why hallucinations are uniquely dangerous

Regular software bugs are usually obvious. The output is wrong in a way that looks wrong — a crash, an error message, garbled text. Hallucinations are wrong in a way that **looks right**. The syntax is perfect. The tone is authoritative. The facts are invented.

**The product implication:** You cannot solve hallucination purely at the model layer. You solve it at the product layer — confidence UX, citations, escalation paths, and golden datasets that specifically test for confident fabrication.

---

## The Three Artifacts

By the end of Module 4, your repo should contain:

```text
04-the-contract/
  golden-dataset-spec.md
  confidence-ux-design.md
  reliability-contract.md
```

1. **Golden dataset spec** — your 20–50 test cases, expected outputs, adversarial cases, and scoring rubric.
2. **Confidence UX design** — how your product behaves at each confidence level (high, medium, low, very low), and what signals users see.
3. **Reliability contract** — the explicit promise: quality commitment, response time, escalation path, feedback mechanism, and transparency.

---

## Bridge to Module 5

Module 4 answers: **Why will users trust the output?**

Module 5 asks: **What breaks at scale?**

You now have a bet, a moat, economics, and a trust architecture. Module 5 is about the things that go wrong when real users hit the system at real volume — governance, compliance, safety, and the operational infrastructure that keeps AI products from becoming liabilities. Everything from Module 4's reliability contract feeds directly into Module 5's governance framework.

---

## Key Takeaways

1. **Trust is perceived control, not accuracy.** An 85% system with transparency beats a 95% black box. Build confidence UX before you optimize accuracy.

2. **Your AI's promises are your company's promises.** There is no legal separation between model output and company commitment. The Air Canada case settled that.

3. **Golden datasets are your release gate.** Nothing ships without passing the golden dataset. Start with 20–50 cases, version it, and grow it. This is CI/CD for AI quality.

4. **"I don't know" is a feature.** Design your product to distinguish between confident answers and uncertain ones, and show that distinction to users. Silence about uncertainty is the source of hallucination damage.

5. **Reliability contracts force hard decisions early.** Deciding what happens when the AI fails — before it fails — is the difference between a managed incident and a reputation crisis.

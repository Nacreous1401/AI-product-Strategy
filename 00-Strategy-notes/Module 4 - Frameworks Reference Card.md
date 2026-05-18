# Module 4 Frameworks Reference Card

*The frameworks introduced in Module 4 — The Contract. For earlier modules see [`Module 1 - Frameworks Reference Card.md`](./Module%201%20-%20Frameworks%20Reference%20Card.md), [`Module 2 - Frameworks Reference Card.md`](./Module%202%20-%20Frameworks%20Reference%20Card.md), and [`Module 3 - Frameworks Reference Card.md`](./Module%203%20-%20Frameworks%20Reference%20Card.md). For the full course-wide reference, see [`Frameworks Reference Card.md`](./Frameworks%20Reference%20Card.md). For term definitions, see [`Module 4 - Glossary.md`](./Module%204%20-%20Glossary.md).*

Each framework gets: what it answers, the structure, and one anchor example.

---

## Trust = Perceived Control (The Central Reframe)

**What it answers:** What should you optimize for to build user trust?
**How to use it:** Before investing in accuracy improvements, ask whether users can see into, verify, and override the AI's outputs. Legibility before precision.

| Factor | Black box (low trust) | Legible system (high trust) |
|---|---|---|
| **Uncertainty signals** | None — always confident | Confidence scores, hedged language |
| **Source attribution** | No citations | Every claim cites a source |
| **User override** | No way to correct | Edit, flag, or reject outputs |
| **Failure mode** | Confidently wrong → trust destroyed | "I'm not sure" → trust preserved |

**Anchor example:** An 85% accurate system with citations and "I'm not sure" messages beats a 95% black box. The lower-accuracy system is more trusted because the user feels in control.

**Lives in:** `04-the-contract/confidence-ux-design.md`.

---

## Confidence UX Spectrum

**What it answers:** How should your product behave at different confidence levels?
**How to use it:** Define four confidence bands and map each to a specific product behavior. The product should act differently when it's sure vs. when it's guessing.

| Confidence | Product behavior | What the user sees |
|---|---|---|
| **High (>90%)** | Act directly | Inline completions, auto-classification, direct answers |
| **Medium (70–90%)** | Show with caveats | Answer + sources, "based on X" qualifiers |
| **Low (50–70%)** | Suggest, don't assert | "I'm not sure, but…", softer suggestions, alternatives |
| **Very low (<50%)** | Escalate or abstain | "I can't answer this confidently — here's who can" |

**Anchor example:** Tesla Autopilot forces a handoff — makes you take the wheel — when confidence drops. That's confidence UX in physical form. GitHub Copilot changes suggestion style: bold inline completions when confident, shorter/softer suggestions when uncertain.

**Caveat:** The thresholds (90%, 70%, 50%) are starting scaffolds. Calibrate to your domain. In healthcare, "medium confidence" might need escalation. In autocomplete, low confidence just means a shorter suggestion.

**Lives in:** `04-the-contract/confidence-ux-design.md`.

---

## Golden Dataset Framework

**What it answers:** How do you define and measure "good" for your AI?
**How to use it:** Build a versioned test set that acts as a release gate. Nothing ships unless it passes.

| Component | What it contains | Minimum viable size |
|---|---|---|
| **Representative inputs** | Core use cases your users actually encounter | 20–50 cases |
| **Expected outputs** | What "good" looks like for each input | One per input |
| **Adversarial inputs** | Edge cases that would be embarrassing or harmful | 5–10 cases |
| **Scoring rubric** | Pass/fail or 1–5 quality scale per case | One rubric |

**Anchor example:** The adversarial cases are the most important part. The exercise is: "What is the worst thing my AI could say with high confidence?" In healthcare, a wrong medication interaction. In finance, a false tax deduction. In legal, a made-up case citation. In support, a refund policy that doesn't exist (Air Canada).

**Caveat:** Start manually if you have to. The discipline of having a golden dataset matters more than its size. Automate when the manual run becomes a bottleneck.

**Lives in:** `04-the-contract/golden-dataset-spec.md`.

---

## Eval Maturity Ladder

**What it answers:** Where does your team sit on the eval spectrum, and what's the next level to aim for?
**How to use it:** Identify your current level. Move up one level at a time — the jump from 0 to 2 is the highest-leverage move.

| Level | What it looks like | Coverage | Cost |
|---|---|---|---|
| **0 — No evals** | "We tried some prompts and they looked good" | None | Free (and expensive) |
| **1 — Manual spot checks** | A PM reviews a sample before release | Partial, slow | Low |
| **2 — Automated golden dataset** | CI/CD pipeline runs golden dataset on every change | Good baseline | Moderate |
| **3 — LLM-as-Judge + golden dataset** | Automated scoring at scale, calibrated against human labels | Strong | Moderate |
| **4 — Continuous monitoring** | Live production outputs sampled and scored in real time | Full production | Higher |

**Anchor example:** Most teams are at level 0 or 1. Getting to level 2 is the single highest-leverage quality investment. It takes a few days to set up and pays for itself the first time it catches a regression before release.

**Lives in:** `04-the-contract/golden-dataset-spec.md` (the dataset) and operational runbooks.

---

## HITL Decision Framework

**What it answers:** Is your human-in-the-loop setup a product feature or an expensive crutch?
**How to use it:** Check four signals. If you're on the "crutch" side for two or more, you have a scaling problem.

| Signal | Feature | Crutch |
|---|---|---|
| **Trigger** | Confidence threshold — only uncertain outputs | Everything reviewed "just in case" |
| **Volume** | 5–15% of outputs | 50%+ of outputs |
| **Feedback loop** | Human corrections improve the model | Corrections go nowhere |
| **Cost trend** | Decreasing over time | Flat or increasing |

**Anchor example:** Intercom Fin escalates to a human when the conversation is ambiguous or the customer is upset — that's a feature. A startup that has a contractor review every AI-generated email before sending — at 100% review rate that never drops — that's a crutch.

**Lives in:** `04-the-contract/reliability-contract.md`.

---

## Reliability Contract Template

**What it answers:** What explicit promise does your product make about AI quality, failure handling, and user recourse?
**How to use it:** Fill in five sections. This forces the team to decide — in advance — what happens when things go wrong.

| Section | Question it answers | Example |
|---|---|---|
| **Quality commitment** | What accuracy/quality do we promise? | "95% of automated responses rated 4+ by users" |
| **Response time** | How fast does the AI respond? What if it's slow? | "< 2s for standard queries; fallback to cached response after 5s" |
| **Escalation path** | What happens when the AI can't answer? | "Low-confidence queries route to support agent within 30s" |
| **Feedback mechanism** | How do users report problems? | "Thumbs down → human review within 24h → golden dataset update" |
| **Transparency** | What do we disclose about how the AI works? | "AI-generated label on all outputs; model version in settings" |

**Anchor example:** Air Canada had no reliability contract. When the chatbot invented a refund policy, there was no escalation path, no confidence threshold, and no feedback mechanism. The tribunal ruled that the company's promises are the chatbot's promises.

**Lives in:** `04-the-contract/reliability-contract.md`.

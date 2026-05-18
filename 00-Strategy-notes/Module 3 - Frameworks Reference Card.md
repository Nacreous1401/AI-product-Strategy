# Module 3 Frameworks Reference Card

*The frameworks introduced in Module 3 - The Margin. For earlier modules see [`Module 1 - Frameworks Reference Card.md`](./Module%201%20-%20Frameworks%20Reference%20Card.md) and [`Module 2 - Frameworks Reference Card.md`](./Module%202%20-%20Frameworks%20Reference%20Card.md). For the full course-wide reference, see [`Frameworks Reference Card.md`](./Frameworks%20Reference%20Card.md). For term definitions, see [`Module 3 - Glossary.md`](./Module%203%20-%20Glossary.md).*

Each framework gets: what it answers, the structure, and one anchor example.

---

## Three Pricing Models

**What it answers:** *How* should you charge? (Not how much.)
**How to use it:** Match the unit of charge to the unit of value the customer recognizes.

| Model | What you charge for | When it fits | Example |
|---|---|---|---|
| **Seat-based access** | Login / per-user license | Pure collaboration tools where access is the value | Most classic SaaS |
| **Hybrid** | Base fee + usage on top | Most AI products today | GitHub Copilot ($19/seat with usage caps) |
| **Outcome-based** | The unit of work itself | When you can cleanly measure the work the customer values | Intercom Fin (per resolved conversation) |

**Market data:** 59% of AI products bundle, 23% sell as add-on, 18% go standalone.

---

## Leader / Filler / Killer + 70% Rule

**What it answers:** What gets bundled into the main plan, and what gets priced separately?
**How to use it:** Apply the 70% rule. If more than 70% of users touch a feature, bundle it. If fewer, price it separately.

| Role | What it is in your product | Big Mac analogy |
|---|---|---|
| **Leader** | Your core intelligence - the reason customers came | The burger |
| **Filler** | Lightweight features that bump value (summaries, suggestions) | Fries and a Coke |
| **Killer** | Heavy inference (image generation, agent workflows) - too expensive to bundle | Coffee - sell separately |

**Caveat:** It's a lens, not a prescription. If your buyer doesn't think about your product as a bundle, this framing isn't the right one.
**Lives in:** Packaging block in `03-the-margin/cost-curve.md`.

---

## Three Pricing Strategies

**What it answers:** What posture should you take in the market?
**How to use it:** Pick one. Then name the unit of work you'd meter, then set the structure.

| Strategy | Posture | Anchor company |
|---|---|---|
| **Skim** | Premium, capture high value from a willing-to-pay segment | Apple |
| **Penetrate** | Lower price to win share quickly | Amazon |
| **Maximize** | Capture the highest value through hybrid or outcome pricing | Microsoft / GitHub Copilot |

**Anchor example:** GitHub Copilot at $19/user is 4.75x a typical SaaS seat - and nobody blinks, because developers complete tasks 55% faster. The price is justified by outcome, not features.
**Lives in:** Pricing block in `03-the-margin/cost-curve.md`.

---

## Model Cascading - 80/20

**What it answers:** How do you protect AI margin without dropping quality?
**How to use it:** Route by task complexity, not by default. Tune the ratio to your domain.

| Tier | Share of requests | What it handles |
|---|---|---|
| **Small / cheap model** | ~80% (starting scaffold) | Simple, common, low-stakes work - autocomplete, lookups, classification |
| **Frontier model** | ~20% (starting scaffold) | Hard reasoning, edge cases, high-stakes outputs |

**Three other margin levers worth knowing:** caching, quantization, prompt optimization.
**Lives in:** Cascading Strategy section of `03-the-margin/cost-curve.md`.

**Caveat:** 80/20 is a starting scaffold. In practice it might be 95/5 or 60/40. Tune to your context.

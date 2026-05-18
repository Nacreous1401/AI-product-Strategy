# Module 3 - The Margin

*Shareable companion notes. These walk you back through what each slide covered, in case you want to review the arguments, examples, and frameworks at your own pace.*

---

## What this module is about

Module 1 asked what you are betting on. Module 2 asked whether the bet can survive contact with the market. Module 3 asks a different question: **does any of this actually make money?**

The vibe shifts here. The first two modules were about threat and defensibility, which gets the adrenaline going. This one is about math, and math creates a different kind of discomfort: the quiet kind where you realize you should probably have looked at these numbers six months ago. Most PMs have never calculated their AI cost per user. The point of today is to close that gap.

You leave with three artifacts in your repo: a **cost curve**, a **pricing strategy**, and a **board-ready one-pager** comparing your current model to the AI-enhanced one. Backed by two interactive tools, the **Margin Calculator** and the **Pricing Strategy Designer**, that do most of the number-crunching for you. The deliverables go in `03-the-margin/cost-curve.md`.

---

### Slide 1 - The Margin

The opening sets the tone for a calmer session than the first two, but warns that the pain is sharper when the math actually lands. This is not "someone could copy me" uncomfortable. This is "wait, am I losing money on every user?" uncomfortable. By the end of the session, you should think differently about your product's economics.

### Slide 2 - Expectations

Same ground rules as the first two sessions: cameras on, Slack for questions, be present. Today is a math-heavy session. The interactive tools do most of the number-crunching, so the math doesn't need to be intimidating.

### Slide 3 - Course Arc

Quick orientation. We are at the halfway point.

- **M1 - The Bet:** What should we build, and how do we know fast?
- **M2 - The Moat:** Why won't this get copied in 6 months?
- **M3 - The Margin:** Will the economics actually work?
- **M4 - The Contract:** Why will users trust it?
- **M5 - The Guardrails:** What breaks at scale?
- **M6 - The Pitch:** How do we get it funded, shipped, and adopted?

After today, the course turns toward trust, governance, and the capstone. Your flywheel scores from M2 and your kill switch audit both show up in the cost model today, so the connection is direct.

### Slide 4 - What You Brought Today

Everything you built in Module 2 - the flywheel, the moat, the kill switch - is meaningless if the economics don't work. You can have the deepest moat in the world and still go broke. The opening warm-up: name one AI call path in your product that could spike costs if usage doubled. Just one. The point is to start thinking about money before any new content lands.

### Slide 5 - Provocation

The opening question: who actually knows their inference cost per user per month? In every cohort, very few hands go up. That gap is exactly the point of the module.

The provocation lists three beliefs PMs carry around like security blankets. None of them are reliably true for AI products:

1. **"Costs will come down."** Model prices probably will keep falling. But cheaper models tempt teams to add more AI calls, longer context windows, richer agents, more retries, more evaluation, more personalization. Unit prices fall, usage intensity rises faster, and total cost goes up. The right question is not "will tokens get cheaper?" The right question is "what does one successful user outcome cost us, and does that cost shrink as the product gets better?"

2. **"Seat pricing works, like always."** Seat pricing charges for access. AI creates value by doing work. One user can summarize ten documents, generate fifty variants, run a workflow overnight, or support a whole team behind the scenes. Another user with the same seat barely touches it. Same revenue, wildly different cost and value. Seat pricing breaks both ways: undercharging the heavy users and overcharging the light ones.

3. **"Scale fixes everything."** This was mostly true in classic SaaS, where adding another customer was almost free. In AI, a lot of the cost is variable - every prompt, retrieval call, model call, eval, and generated answer adds cost. If your unit economics are negative, scale just makes the loss bigger and faster.

The point isn't pessimism. It's economic awareness. AI can absolutely expand revenue and create new willingness to pay, but it usually compresses margin first. The rest of the module is about giving you the controls to see that compression coming.

### Slide 6 - 80% Margins Are Becoming 40%

The core economic argument of the module. Traditional SaaS runs at 80%+ gross margins because infrastructure costs are mostly fixed. Spin up a server, add users, marginal cost is tiny. AI products flip that completely. Variable costs - tokens, inference - scale with usage. Power users can blow up unit economics on their own. One enthusiastic customer running agents all day can cost more than a hundred casual ones.

The napkin math from the slide: a thousand calls at three cents a call is **thirty dollars per user per month** in AI COGS alone. Before engineering. Before support. Before anything else. Seeing that number for the first time hits differently than just hearing "AI is expensive."

### Slide 7 - Model Cascading

If margin compression is the disease, **model cascading is the cure**. The single highest-leverage thing most AI products can do for their margins is an 80/20 split: 80% of requests go to a cheap model, 20% go to a frontier model. This isn't theoretical. Cursor does this. GitHub Copilot does this. When Copilot answers a simple autocomplete, it doesn't need the most powerful model on earth. It needs a fast, cheap one. Save the big guns for the hard stuff.

Three more levers exist alongside routing:

- **Quantization** - shrinking the model so it runs cheaper.
- **Caching** - reusing answers instead of recomputing them.
- **Prompt optimization** - getting the same quality with fewer tokens.

One caveat on the 80/20: it is a starting scaffold, not a rule. In practice it might be 95/5 or 60/40 depending on your domain and your quality bar. Tune the split to your context.

### Slide 8 - Klarna Case

The cautionary tale of the module. Klarna went all-in on AI customer service in early 2024. The headlines were incredible:

- **$40M projected savings for 2024** - the headline that travelled around the world.
- **700 agents avoided** - and this is the part most people miss. That was 700 hires they avoided during a growth phase, not 700 people they laid off. They had been planning to scale from 3,000 to 5,000 agents and instead held the line at around 2,000 with AI doing the rest.
- **The reversal** - by May 2025, about fifteen months after the original headline, Klarna's CEO admitted on Bloomberg: *"cost seems to have been a too predominant evaluation factor… what you end up having is lower quality."* They started rehiring humans for the hard cases.

The punchline: AI was not more expensive than humans on a pure dollar basis - it was cheaper. The cost they actually paid was in **quality and trust**, and you can't put that on the income statement until customers start leaving. The lesson is not that Klarna failed. It's that the business model has to match the work, and "cheap" is not the same as "right."

### Slide 9 - How You Charge > How Much

Most pricing failures happen because teams never figured out **how** to charge, not how much. Those are very different problems and they get confused all the time. You can spend six months optimizing your price point and still lose money because the structure was wrong from the start.

The three pricing models on a spectrum:

| Model | What you charge for | Example |
|---|---|---|
| **Seat-based access** | Login / per-user license | Most classic SaaS |
| **Hybrid** | Base fee + usage on top | Many AI products today |
| **Outcome-based** | The unit of work itself | Intercom Fin (per resolved conversation) |

Intercom Fin is the standout. They charge **per resolved conversation** - not per seat, not per message. It is genuinely the only major pricing-model innovation in AI right now, and it works because the unit of charge matches the unit of value. Customers only pay when they get what they came for.

Some market data: 59% of AI products bundle, 23% sell as an add-on, 18% go standalone.

The cautionary tale: a $200/month AI subscription let users run third-party agent harnesses. A single agent running for one day burned $1,000 to $5,000 in API-equivalent costs on a flat $200 plan. Every AI subscription is a bet on average usage, and tools that let power users blow past that average forced the provider to shut down third-party access entirely within four months.

### Slide 10 - Access or Outcome?

A quick whole-room exercise. Point left if your product should price on access. Point right if it should price on outcome.

The interesting follow-up: most people point left because that's the default. But if your product is doing work for users - completing tasks, resolving tickets, generating output - why are you pricing access? If your AI writes a report that saves someone three hours, and you charge $20 a month for access, you are leaving massive value on the table.

### Slide 11 - Leaders, Fillers & Killers

A bundling framework, told through the Big Mac analogy:

- **The Leader** - what you come for. The burger. Nobody walks into McDonald's craving a medium Sprite.
- **The Filler** - bumps the average order. Fries and a Coke.
- **The Killer** - too different from the moment, sell it separately. Coffee.

Applied to AI:

- **Leader** = your core intelligence.
- **Filler** = lightweight features (summaries, suggestions).
- **Killer** = heavy inference work (image generation, agent workflows). Price as add-ons.

The **70% rule** gives you a concrete threshold: if more than 70% of users touch a feature, bundle it. If fewer, price it separately.

Caveat: Leaders/Fillers/Killers is a lens for thinking about value capture, not a prescription. If your buyer has never thought about your product as a bundle, this framing might not be the right one. Use what fits.

### Slide 12 - Name Your Leader, Filler & Killer

The exercise. In `03-the-margin/cost-curve.md`, create a small packaging decision block: Leader, Filler, Killer, percentage of users using the Killer, and a bundle-or-add-on decision.

The follow-up question that changes a lot of people's pricing strategies: if you bundled your "killer" into the main plan, what percentage of users actually use it? If it's under 70%, it's an add-on. You might be subsidizing your heaviest users with everyone else's subscription.

### Slide 13 - The Margin Calculator

The first interactive tool. Open the **Margin Calculator** linked from the slide, plug in your numbers, and it auto-calculates the basic margin picture. Six inputs, live calculation, exportable results.

Below the inputs is a **Scenario Lab** with three sliders:

- **Inference cost multiplier** - what if model prices change?
- **Usage volume multiplier** - what if usage doubles?
- **Cascading ratio** - what percentage routes to the cheap model?

A live chart shows your margin curve across different assumptions, with your current position marked by a dot. The chart makes the economic argument for model routing visceral - you don't need anyone to convince you, the math does it.

This is the warm-up before the deeper Cost Curve lab. Get your cost categories, COGS per user, and cascade ratio onto the page in `03-the-margin/cost-curve.md`. Don't try to perfect the board story yet.

### Slide 14 - Break

Five-minute break. Before coming back, pull up your AI provider's pricing page - you'll need it for the cost curve exercise.

### Slide 15 - Cameras On

Welcome back. The whole next stretch is hands-on - cost curves, pricing design, and a board one-pager. Keep your repo open and your Margin Calculator numbers handy.

### Slide 16 - Cost Curve Lab

The applied block. Everything from the first half - margin compression, model cascading, pricing models - now gets applied to your actual product. First up: mapping your cost curve.

### Slide 17 - Build Your Cost Curve

Fifteen minutes of solo work. Map every AI feature in your product to a model tier and estimate the cost. The goal is **honest tiering**. Most people's instinct is to say "we use frontier for everything," and this exercise usually shows that's a 3x cost difference that isn't sustainable. Frontier feels safer ("what if the cheap model gives a bad answer?"), but be honest about what actually needs frontier-level intelligence and what doesn't. Your autocomplete does not need GPT-5.

Two traps to watch for:

- **Embeddings get called more than you think.** Always more.
- **You will default everything to the most expensive model.** Resist that.

In `03-the-margin/cost-curve.md`, fill the **Cost Model** table with cost categories like inference, infrastructure, data/storage, human review, and total AI COGS. Then fill the **Cascading Strategy** section: small model, frontier model, routing rule, and expected split (e.g. 72% small / 28% frontier).

Estimates are fine. **Structure beats false precision.**

### Slide 18 - Design Your Pricing

This is where Product-Market-Pricing Fit lands. Three steps:

1. **Pick a strategy posture** - skim like Apple, penetrate like Amazon, or maximize like Microsoft.
2. **Name the unit of work** you would meter.
3. **Set the structure** - base fee plus per-unit price.

The proof point: GitHub Copilot is **$19 per user**. That's 4.75x a typical SaaS seat, and nobody blinks. Why? Because developers complete tasks **55% faster**. The price isn't justified by features - it's justified by outcome. When someone saves an hour a day, $19 is a rounding error.

The **Pricing Strategy Designer** tool linked on this slide is a sample walkthrough that helps you generate the minimum block for `03-the-margin/cost-curve.md`: strategy posture, pricing model, unit of work, base fee, per-unit price, and implied revenue per user.

A worked example for an AI support copilot:

- Strategy posture = Maximize
- Pricing model = Hybrid
- Unit of work = resolved support conversation
- Base fee = $49/month
- Price per unit = $0.75
- Estimated units per user per month = 80
- **Implied revenue per user = $109/month**

Compare that to a flat $49 subscription. If the product actually resolves 80 conversations a month, the old price was giving away $60 of value per user before margin even enters the conversation.

After the tool, update the **Pricing Model** section of `cost-curve.md`: current pricing, proposed AI pricing, model type, and why that model fits the buyer. If you have time, start the revenue side of **Break-Even Math**: average customer size, base revenue, overage revenue, implied revenue per user.

A reminder: hybrid strategies and archetypes are lenses, not playbooks. The right structure is the one that fits your buyer's mental model and how value shows up in their world.

### Slide 19 - Board Lab

Last lab of the day, and the most "real world" one. You're building a board one-pager - a before-and-after comparison you could actually present to leadership. Everything from today feeds in: the cost model, the cascade assumptions, and the pricing model.

### Slide 20 - Before/After for Your Board

Ten minutes to build a before-and-after comparison: your current model versus the AI-enhanced model.

The reframe to internalize, because it trips up even experienced PMs: **a lower margin percentage can be totally fine if revenue and gross profit are both up.** This sounds counterintuitive. We're trained to panic when margin percentage drops. But AI can expand the numerator even if the percentage dips. If your margin goes from 80% to 65% but revenue triples, you are winning.

This one-pager is what you'd actually present to a board. When someone asks "why is our margin lower?" - this is your answer.

In `03-the-margin/cost-curve.md`, this is the **Board One-Pager** plus the final **Break-Even Math**. The minimum acceptable output: before pricing, after pricing, gross margin shift, why the lower margin is acceptable, and the business outcome that makes the bet worth it.

### Slide 21 - Your Repo After Today

Tying it back to slide 5. Remember the three security blankets - costs come down, seat pricing works, scale fixes everything? Look at what you know now. Margin compression is the default for AI products. But now you have the levers - cascading, routing, pricing model, bundling - and you have the artifact in the repo to do something about it.

Your living strategy repo now has:

```text
01-the-bet/
  diagnostic.md
  prototype.md

02-the-moat/
  data-flywheel.md
  kill-switch.md

03-the-margin/
  cost-curve.md
```

The three things you should be able to point to in `03-the-margin/`: a **cost curve**, a **pricing decision**, and a **board story**. If one is weak, that's homework before Module 4.

### Slide 22 - Bridge to Module 4

Module 3 answers: **Will the economics work?**

Module 4 asks: **Why will users trust the output enough to pay?**

Economics without trust doesn't convert. You can have perfect pricing and beautiful margins, but if customers don't trust the output, none of it matters. Module 4 is about reliability, contracts, and evaluation - the things that make customers actually adopt and keep using what you've priced and built. Everything from today - your cost curve, your pricing strategy, even the kill switch from Module 2 - feeds directly into Module 4's vendor evaluation framework.

### Slide 23 - Key Takeaways

Three takeaways, all illustrated through Intercom Fin:

1. **AI products have fundamentally different economics.** Intercom could have treated Fin like a normal SaaS feature - add the assistant, charge per seat, raise the plan price. That would miss the economics completely. Fin is doing work, not just providing access. Every conversation creates variable AI cost, and the expensive edge cases are exactly where the product has to be smartest. **Margin is designed into the architecture, not added afterward.**

2. **Model cascading is the highest-leverage margin lever.** Not every support question should go to the most expensive path. "Where is my invoice?" runs cheap. Ambiguous policy or angry-customer escalations need more expensive reasoning or a human handoff. **You don't protect margin by making the AI worse. You protect margin by matching the model path to the complexity of the work.**

3. **How you charge matters more than how much.** Intercom charges per resolved conversation - the unit of work the customer already recognizes. If Fin resolves the issue, the customer got value. If it doesn't, Intercom doesn't get to pretend the value happened. **The best pricing unit is the one your customer already thinks in.**

The single thing to hold onto: don't just ask "what does this cost us?" Ask "what work did we do, who got value, and how should that value be captured?"

### Slide 24 - Optional: Go Deeper

Two optional exercises before Module 4:

- **Try three different cascading ratios in the Margin Calculator** and pick the healthiest margin path.
- **Refine your board one-pager with actual numbers from your provider's pricing page.** The more real the numbers, the more useful the artifact becomes.

Next session: **Module 4 - The Contract.** Economics without trust doesn't convert.

### Slide 25 - Survey

Brief survey before signing off. The feedback genuinely shapes the next session.

### Slide 26 - Q&A

Questions before wrap. Slack is always open between sessions.

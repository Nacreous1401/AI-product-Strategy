# Module 3 Glossary

*The terms introduced in Module 3 - The Margin. For earlier modules, see [`Module 1 - Glossary.md`](./Module%201%20-%20Glossary.md) and [`Module 2 - Glossary.md`](./Module%202%20-%20Glossary.md). For the full course-wide reference, see [`Glossary.md`](./Glossary.md).*

Two sections:

1. **AI/ML Foundations** - the technical vocabulary you keep hearing in cost and pricing conversations.
2. **Economics & Pricing** - everything Module 3 introduces about how AI products make and lose money.

---

## 1. AI/ML Foundations

### Agent

An AI system that can take multiple steps on its own to complete a task - calling tools, making decisions, looping until done - rather than producing a single response. Agents are powerful and expensive: one running for a day can burn through more cost than a hundred regular conversations.
*Seen in: M3, Slide 9 (a $200/month plan blew up because users ran agent workflows on it).*

### Caching

Storing AI responses so the next time the same question (or a similar one) is asked, you serve the saved answer instead of paying for a new model call. One of the four levers for protecting AI margin.
*Seen in: M3, Slide 7 (Model Cascading).*

### Context window

The amount of text (measured in tokens) the model can see at once when generating a response. Longer windows let you feed in more documents or history but cost more per call.
*Seen in: M3, Slide 5 (longer context windows are one of the ways usage intensity rises even when token prices fall).*

### Embedding

A numerical representation of a piece of text (or image, audio, etc.) that captures its meaning, so the system can compare it to other content and retrieve what is most relevant. They are how RAG systems "look things up." They are also called more often than people expect, which is why they show up as a cost trap.
*Seen in: M3, Slide 17 ("you will underestimate how often embeddings get called").*

### Frontier model

The most powerful (and most expensive) tier of model from a provider - GPT-5, Claude Opus, Gemini Pro, etc. Use it for genuinely hard work. Default everything to it and your cost curve will hurt.
*Seen in: M3, Slides 6, 7, 17 (cascading is the discipline of not using frontier when you don't need it).*

### Inference

Running a request through a model to get a response - the live, in-production cost of using AI. Distinct from training. When people say "inference cost," they mean what each call costs you in real time.
*Seen in: M3, Slide 5 (the provocation question: what is your inference cost per user per month?).*

### Prompt optimization

Rewriting prompts to get the same (or better) quality with fewer tokens or fewer model calls. One of the four levers for protecting AI margin.
*Seen in: M3, Slide 7.*

### Quantization

Compressing a model so it runs cheaper and faster, usually with a small quality trade-off. Shows up alongside caching and prompt optimization as a margin lever.
*Seen in: M3, Slide 7.*

### Small / cheap model

The lower-tier models - GPT-mini, Claude Haiku, Llama variants, etc. Cheap, fast, often "good enough" for the bulk of requests. The 80% in an 80/20 cascade.
*Seen in: M3, Slide 7.*

### Token

The unit AI providers bill in. Roughly speaking, one token is about three-quarters of an English word. Both your input (prompt) and the model's output cost tokens. Every cost calculation in Module 3 ultimately resolves to tokens.
*Seen in: M3, Slide 6.*

---

## 2. Economics & Pricing

### 70% Rule

The bundling threshold. If more than 70% of users touch a feature, bundle it into the main plan. If fewer, price it separately as an add-on. Otherwise you are subsidizing your heaviest users with everyone else's subscription.
*Seen in: M3, Slide 11.*

### 80/20 split

The starting cascade ratio: 80% of requests routed to a cheap model, 20% to a frontier model. Cursor and GitHub Copilot ship variations of this in production. Tune the ratio to your domain - it might be 95/5 or 60/40.
*Seen in: M3, Slide 7.*

### AI COGS

The portion of your Cost of Goods Sold that comes specifically from AI: tokens, inference calls, embeddings, retrieval, evals, human review. The number Module 3's Margin Calculator helps you put a value on per user.
*Seen in: M3, Slide 6.*

### Base fee + per-unit pricing

A hybrid pricing structure: customers pay a recurring base for access plus a usage fee per unit of work. Example from Module 3: $49/month base + $0.75 per resolved support conversation.
*Seen in: M3, Slide 18.*

### Board one-pager

A before-and-after comparison of your current vs. AI-enhanced model that shows revenue, cost, gross margin, and the business outcome that justifies the bet. The third Module 3 artifact in `03-the-margin/cost-curve.md`.
*Seen in: M3, Slides 19-20.*

### Break-even

The point where revenue covers cost. In Module 3 it shows up as the **Break-Even Math** section of `cost-curve.md`: average customer size, base revenue, overage revenue, and implied revenue per user.
*Seen in: M3, Slides 18, 20.*

### COGS (Cost of Goods Sold)

The direct cost of delivering your product. In classic SaaS this is mostly fixed (servers, hosting). In AI it includes a large variable component (tokens, inference) that scales with usage.
*Seen in: M3, Slide 6.*

### Cost curve

A map of how your AI cost grows as usage grows. Built by tagging every AI feature in your product with a model tier and a per-call estimate. The first Module 3 artifact in `cost-curve.md`.
*Seen in: M3, Slides 16-17.*

### Fixed vs. variable cost

Fixed costs don't change with usage (servers, salaries). Variable costs do (tokens, inference, retrieval). The Module 3 punchline: AI shifts a meaningful share of cost from fixed to variable, which is why scale alone doesn't fix unit economics.
*Seen in: M3, Slides 5-6.*

### Gross margin

Revenue minus COGS, expressed as a percentage. Classic SaaS runs at 80%+. AI products often run at 40-65% before you apply the levers. A lower margin can still be a winning move if revenue and gross profit are both up.
*Seen in: M3, Slides 6, 13, 20.*

### Hybrid pricing

A pricing model that combines a base fee for access with a usage fee for the work done. The middle ground between pure seat pricing and pure outcome pricing.
*Seen in: M3, Slide 9.*

### Leader / Filler / Killer

The bundling lens, told through a Big Mac. The **Leader** is what the customer comes for (your core intelligence). The **Filler** bumps the average order (lightweight features). The **Killer** is too heavy or too different to bundle (image generation, agent workflows) - sell it separately.
*Seen in: M3, Slide 11.*

### Margin compression

When the percentage profit per unit shrinks. Module 3's premise: AI compresses margins before it expands revenue, because variable costs land before pricing can adapt.
*Seen in: M3, Slides 5-6.*

### Maximize strategy

A pricing posture that captures the highest possible value from each customer through hybrid or outcome-based pricing - the GitHub Copilot or Microsoft model.
*Seen in: M3, Slide 18.*

### Model cascading

Routing each request to the cheapest model that can handle it well, and saving the frontier model for the hard cases. The single highest-leverage lever for protecting AI margin.
*Seen in: M3, Slide 7.*

### Outcome-based pricing

Charging for the unit of work the customer actually values - a resolved support conversation, a generated lead, a completed task. Intercom Fin is the standout example.
*Seen in: M3, Slide 9.*

### Penetrate strategy

A pricing posture that uses lower prices to win share quickly - the Amazon model.
*Seen in: M3, Slide 18.*

### Seat-based pricing

Charging per user with access to the product. Standard in classic SaaS. Breaks both ways for AI: heavy users get away with massive value for the same price, while light users churn because they don't see enough value to renew.
*Seen in: M3, Slides 5, 9.*

### Skim strategy

A pricing posture that captures premium value from a smaller, willing-to-pay segment - the Apple model.
*Seen in: M3, Slide 18.*

### Unit economics

The cost and revenue of a single unit (a user, a transaction, a conversation). When unit economics are negative, scaling makes the loss bigger and faster - the inverse of the classic SaaS playbook.
*Seen in: M3, Slide 5.*

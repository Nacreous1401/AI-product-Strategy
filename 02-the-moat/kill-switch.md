# Kill Switch Audit

## Vendor Dependency Assessment

| Dimension | Current State | Risk Level | 48-Hour Action |
|-----------|--------------|------------|---------------|
| **Provider** |OpenAI powers the copilot's recommendations and incident analysis | M |List every OpenAI API call in the codebase. Identify which are portable vs provider-specific. |
| **Abstraction** |Copilot calls OpenAI directly — no model router or abstraction layer exists | H |Add LiteLLM or equivalent router. One-day task. Lets you swap providers without touching product code. |
| **Routing** |	All inference goes through one provider — no fallback if OpenAI has an outage or price change | M |Configure Anthropic Claude or Gemini as a secondary fallback. Test it handles a real incident query. |
| **Eval** | No eval suite — output quality is assessed manually. No way to verify a new model performs as well.| H |Write 10 golden test cases — real SIM incidents with known correct resolutions. Run before any provider switch. |

## Portability Score
<!-- Ready / Partial / Locked -->

## If [primary vendor] doubles pricing tomorrow:
<!-- What's your 48-hour response? -->

## If [primary vendor] ships a competing product:
<!-- What's defensible that they can't replicate? -->

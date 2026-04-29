# Kill Switch Audit

## Vendor Dependency Assessment

| Dimension | Current State | Risk Level | 48-Hour Action |
|-----------|--------------|------------|---------------|
| **Provider** |Main AI features depend on OpenAI for recommendations, summaries, and assistant responses | M |Open backup accounts with Anthropic or Google Gemini and test key workflows immediately.|
| **Abstraction** |AI provider logic is directly connected to parts of the product | H |AMove all AI calls into one shared internal service so providers can be swapped faster.|
| **Routing** |	Requests currently go to one provider only. | M |Add a simple switch to route traffic to a second provider if needed. |
| **Eval** | No formal testing system exists to compare provider quality. | H |Build 10 real connectivity incident test cases and compare outputs across providers. |

## Portability Score
<!-- Ready / Partial / Locked -->

## If [primary vendor] doubles pricing tomorrow:
<!-- What's your 48-hour response? -->

## If [primary vendor] ships a competing product:
<!-- What's defensible that they can't replicate? -->

# Pricing comparison

Verified-price snapshot as of **2026-09-29**. ✅ = read on the vendor's official pricing page that day; ⚠️ = third-party/stale. Full records (with `price_verified` booleans) are in [`data/models.json`](../data/models.json) and [`data/platforms.json`](../data/platforms.json).

## Cheapest verified input prices (per 1M tokens)

| Model | Input | Output | Confidence |
|---|---|---|---|
| GLM-4.7 / 4.5 / 4.6V Flash (Zhipu) | $0.00 | $0.00 | ✅ |
| Qwen3.7 Flash ≤32K (Alibaba) | $0.03 | $0.13 | ✅ |
| Qwen Flash ≤256K (Alibaba) | $0.05 | $0.40 | ✅ |
| Qwen Turbo (Alibaba, legacy) | $0.05 | $0.20 | ✅ |
| Gemini 2.5 Flash-Lite (Google) | $0.10 | $0.40 | ✅ |
| GPT-6 Luna short ctx (OpenAI) | $0.10 | $0.50 | ✅ |
| Qwen3.5 Flash (Alibaba) | $0.10 | $0.40 | ✅ |
| Ministral 3 3B (Mistral) | $0.10 | $0.10 | ✅ |
| MiMo V2.6 Flash (Xiaomi) | $0.14 | $0.28 | ✅ |
| DeepSeek V4.1 Flash off-peak (DeepSeek) | $0.15 | $0.60 | ✅ |
| Qwen3.8 Flash (Alibaba) | $0.15 | $0.47 | ✅ |
| GLM-5.3 Flash (Zhipu) | $0.15 | $0.50 | ✅ |
| Mistral Small 4 / Ministral 3 8B (Mistral) | $0.15 | $0.60 / $0.15 | ✅ |

## Cheapest verified cache-hit prices (per 1M tokens)

| Model | Cache-hit input | Confidence |
|---|---|---|
| MiMo V2.6 Flash (Xiaomi) | $0.0028 | ✅ |
| DeepSeek V4.1 Flash (DeepSeek) | $0.006 | ✅ |
| GPT-6 Luna (OpenAI) | $0.01 | ✅ |
| GLM-4.7 FlashX (Zhipu) | $0.01 | ✅ |
| Ministral 3 3B (Mistral) | $0.01 | ✅ |
| Qwen3.8 Omni Flash (Alibaba) | $0.016 | ✅ |

## Cheapest verified third-party serving (per 1M tokens, open models)

| Provider | Example | Input | Output | Confidence |
|---|---|---|---|---|
| DeepInfra | DeepSeek-V4-Flash | $0.09 | $0.18 | ✅ |
| DeepInfra | Llama-3.1-8B-Turbo | $0.02 | $0.04 | ✅ |
| Novita | DeepSeek V4 Flash | $0.14 | $0.28 | ✅ |
| Nebius | DeepSeek-V4-Flash-0731 | $0.14 | $0.28 | ✅ |
| Together | GPT-OSS 120B | $0.15 | $0.60 | ✅ |
| Fireworks | GPT-OSS 120B | $0.15 | $0.60 | ✅ |
| Fireworks | DeepSeek V4.1 Flash | $0.30 | $1.20 | ✅ |
| Cerebras | GPT-OSS 120B | $0.35 | $0.75 | ✅ |

## The $/task math that matters

1. **Sticker price is the ceiling.** With 80% cache hits on a $0.14/M input / $0.0028/M cache-hit model (MiMo V2.6 Flash), effective input cost is ~$0.03/M — cheaper than any sticker price in the table.
2. **Batch and off-peak stack.** 50%-off batch APIs are offered by DeepSeek, Qwen, Mistral, Anthropic, Fireworks, Together, Novita; DeepSeek off-peak adds another 50%.
3. **Free tiers are real but fragile.** Zhipu's free Flash models, Qwen's 90-day quota, Novita's free Ling models, Groq's no-card tier, and Cloudflare's 10K neurons/day all exist today — all can change; the `price_verified` field and verification date exist for exactly this reason.
4. **Watch scheduled changes.** Nebius announced +18.3% dedicated-endpoint rises effective Oct 1, 2026; Gemini 3.x intro pricing ($0.75/$3.75) ends 2026-12-31.

# Awesome Flash LLMs [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated directory of **Flash-class LLMs** — the fast, cheap, high cost-performance efficiency tiers from every major lab — and the **platforms to deploy and serve them**: serverless inference providers, aggregation gateways, and self-hosting stacks.

"Flash" started as Google's name for its efficiency tier (Gemini Flash), but every lab now ships one: OpenAI's Luna/mini line, Anthropic's Haiku, xAI's fast Groks, Mistral's Small/Ministral, DeepSeek's V4.1 Flash, Qwen's Flash/Turbo SKUs, Zhipu's GLM Flash (some **free**), MiniMax, Xiaomi's MiMo, StepFun — plus the open-weight models that third-party inference chips serve at 500–3,000 tokens/sec. This list tracks the models *and* where to run them, as of **September 2026**.

**Pricing confidence:** every price below is stamped ✅ **verified 2026-09-29** (read on the vendor's official pricing page) or ⚠️ **unverified** (third-party or stale). **Prices are never guessed.** Machine-readable records live in [`data/models.json`](data/models.json) and [`data/platforms.json`](data/platforms.json) with a `price_verified` boolean per entry.

## 2026 Highlights

- **OpenAI DevDay (Sept 29, 2026)** launched **GPT-6.1 Sol**; the new cheap tier **GPT-6 Luna** starts at $0.10/$0.50 per 1M tokens (verified).
- **DeepSeek V4.1 Flash** went GA (Sept 2026): 1M context, off-peak 50% off, cache-hit input at **$0.006/M**.
- **Xiaomi MiMo V2.6 Flash** (Sept 21–22, 2026): omni-modal open-weight model at $0.14/M input, $0.0028/M cache hits — the open efficiency standout.
- **Qwen3.8 Flash** (Aug 26) and **GLM-5.3 Flash** (Aug 18) refreshed the Chinese flash race; **Zhipu keeps three Flash models free** on its API.
- **Cerebras** serves GPT-OSS 120B at a vendor-reported **~3,000 tok/s**; **Groq** and **SambaNova** push LPUs/RDUs for sub-100ms TTFT.
- **xAI retired** the old `grok-4-fast` / `grok-code-fast-1` names (~May 2026) — don't quote their old prices.

## Contents

- [Flash-class models](#flash-class-models)
  - [Google — Gemini Flash](#google--gemini-flash)
  - [OpenAI](#openai)
  - [xAI — Grok](#xai--grok)
  - [Anthropic — Haiku](#anthropic--haiku)
  - [Mistral AI](#mistral-ai)
  - [Cohere](#cohere)
  - [Amazon — Nova](#amazon--nova)
  - [DeepSeek](#deepseek)
  - [Alibaba — Qwen](#alibaba--qwen)
  - [Zhipu AI — GLM](#zhipu-ai--glm)
  - [Moonshot AI — Kimi](#moonshot-ai--kimi)
  - [MiniMax](#minimax)
  - [Xiaomi — MiMo](#xiaomi--mimo)
  - [StepFun](#stepfun)
  - [Baidu — ERNIE](#baidu--ernie)
- [Inference platforms](#inference-platforms) — hosted/serverless providers & gateways
- [Self-hosting stacks](#self-hosting-stacks) — serve efficient models yourself
- [Benchmarks & eval notes](#benchmarks--eval-notes)
- [Guides](#guides)
- [Related repositories](#related-repositories)
- [Contributing](#contributing)
- [License](#license)

---

## Flash-class models

### Google — Gemini Flash

- [Gemini 2.5 Flash](https://ai.google.dev/gemini-api/docs/models) — ✅ $0.30 in / $2.50 out (text). 1M context; Batch/Flex 50% off ($0.15/$1.25); context caching ~10% of input; tunable thinking levels.
- [Gemini 2.5 Flash-Lite](https://ai.google.dev/gemini-api/docs/models) — ✅ $0.10 in / $0.40 out. Batch/Flex $0.05/$0.20 — Google's cheapest 2.5 tier, best $/task for simple workloads.
- [Gemini 3.8 Flash](https://ai.google.dev/gemini-api/docs/models) — ⚠️ unverified. **NEW** (GA Sept 2, 2026): "most intelligent Flash" — long-horizon software engineering and agents; ~1M context per third parties.
- [Gemini 3.7 Flash](https://ai.google.dev/gemini-api/docs/models) — ⚠️ unverified. **NEW** 2026: high-speed efficient coding/tool use.
- [Gemini 3.6 Flash](https://ai.google.dev/gemini-api/docs/models) — ⚠️ unverified. **NEW** 2026: multimodal agentic Flash.
- [Gemini 3.5 Flash](https://ai.google.dev/gemini-api/docs/models) — ⚠️ unverified. **NEW** 2026: baseline 3.x Flash tier.
- [Gemini 3.5 Flash-Lite](https://ai.google.dev/gemini-api/docs/models) — ⚠️ unverified. **NEW** 2026: fastest, most cost-effective 3.5.
- [Gemini 3.1 Flash-Lite](https://ai.google.dev/gemini-api/docs/models) — ⚠️ unverified. **NEW** 2026: frontier-class intelligence at a fraction of cost, per Google.
- Pricing page: [ai.google.dev/gemini-api/docs/pricing](https://ai.google.dev/gemini-api/docs/pricing). Note: the official 3.x price blocks (intro $0.75/$3.75 through 2026-12-31, then $1.50/$7.50–$9.00) couldn't be mapped to individual model names in text fetches — marked unverified pending a model-card pass.

### OpenAI

- [GPT-6 Luna](https://developers.openai.com/api/docs/pricing) — ✅ $0.10 in / $0.50 out (short ctx; cached $0.01). **NEW** (~Sept 22, 2026): the cheapest tier on OpenAI's price sheet.
- [GPT-6.1 Sol](https://developers.openai.com/api/docs/pricing) — ✅ $2.00 in / $10.00 out (short ctx; cached $0.10). **NEW** (DevDay Sept 29, 2026).
- [GPT-5.6 Sol](https://developers.openai.com/api/docs/pricing) — ✅ $4.00 in / $20.00 out (promo; cached $0.40). Runs on Cerebras hardware at 750 tok/s per third parties.
- [GPT-4o mini](https://platform.openai.com/docs/models) — ⚠️ $0.15/$0.60 (third-party). Legacy efficiency tier, off the current price sheet; still widely served via Azure/Bedrock.
- [GPT-5-mini](https://platform.openai.com/docs/models) — ⚠️ $0.25/$2.00 (third-party). Reasoning-capable mini; off the current price sheet.
- [GPT-5-nano](https://platform.openai.com/docs/models) — ⚠️ $0.05/$0.40 (third-party). Cheapest GPT-5 variant; off the current price sheet.

### xAI — Grok

- [Grok Build 0.1](https://docs.x.ai/developers/pricing) — ✅ $1.00 in / $2.00 out (<200K prompt; cached $0.20). **NEW** fast tier on the public xAI API; 256K context.
- [Grok 4.3](https://docs.x.ai/developers/pricing) — ✅ $1.25 in / $2.50 out; cached $0.20. 1M context; batch 20% off.
- [Grok 4.20](https://docs.x.ai/developers/pricing) — ✅ $1.25 in / $2.50 out. Reasoning / non-reasoning / multi-agent variants.
- [Grok 4.7 Fast](https://docs.x.ai/developers/pricing) — ✅ $4.00 in / $12.00 out; cached $1.00. Faster-infra tier — **not on the public API** (Cursor + Grok Build only).
- Note: `grok-4-fast` / `grok-code-fast-1` were retired ~May 2026 — old $0.20/$0.50 figures no longer apply.

### Anthropic — Haiku

- [Claude Haiku 4.5](https://platform.claude.com/docs/en/about-claude/pricing) — ✅ $1.00 in / $5.00 out. **NEW** (Oct 2025): "fastest Claude with near-frontier intelligence." 200K in / 64K out; cache read 0.1× ($0.10); batch 50% off. Also on Bedrock + Google Cloud.

### Mistral AI

- [Mistral Small 4](https://docs.mistral.ai/inference/pricing) — ✅ $0.15 in / $0.60 out; cached $0.015. The price/performance workhorse.
- [Mistral Medium 3.5](https://docs.mistral.ai/inference/pricing) — ✅ $1.50 in / $7.50 out; cached $0.15.
- [Ministral 3 8B](https://docs.mistral.ai/inference/pricing) — ✅ $0.15 in / $0.15 out. Near-symmetric pricing; edge-friendly.
- [Ministral 3 14B](https://docs.mistral.ai/inference/pricing) — ✅ $0.20 in / $0.20 out.
- [Ministral 3 3B](https://docs.mistral.ai/inference/pricing) — ✅ $0.10 in / $0.10 out. Mistral's cheapest hosted tier.
- [Codestral](https://docs.mistral.ai/inference/pricing) — ✅ $0.30 in / $0.90 out. Code-specialized.
- Batch 50% off; cached input up to −90% (verified FAQ).

### Cohere

- [Command A+](https://docs.cohere.com/docs/models) — ⚠️ unverified. **NEW** (May 2026): MoE flagship for agents — 128K ctx, vision, reasoning, Azure-deployable.
- [Command A](https://docs.cohere.com/docs/models) — ⚠️ unverified. 256K ctx; 150% higher throughput than Command R+ 08-2024.
- [Command R7B](https://docs.cohere.com/docs/models) — ⚠️ unverified. Small/fast RAG model; 128K ctx.
- [Command R / R+ (08-2024)](https://docs.cohere.com/docs/models) — ⚠️ unverified. RAG-optimized; old aliases deprecated Sept 2025.
- Note: Cohere no longer publishes per-token rates — only custom enterprise / Model Vault.

### Amazon — Nova

- [Nova Micro](https://aws.amazon.com/bedrock/pricing) — ⚠️ $0.035/$0.14 (third-party). Cheapest Nova tier on Bedrock; batch 50% off confirmed.
- [Nova Lite](https://aws.amazon.com/bedrock/pricing) — ⚠️ $0.06/$0.24 (third-party). Multimodal efficiency tier.

### DeepSeek

- [DeepSeek V4.1 Flash](https://api-docs.deepseek.com/quick_start/pricing) — ✅ $0.30 in / $1.20 out (peak; cache-hit $0.006). **NEW** (GA Sept 2026): 1M ctx, 384K output, vision, thinking/non-thinking; **off-peak 50% off** ($0.15/$0.60).
- [DeepSeek V4 Pro](https://api-docs.deepseek.com/quick_start/pricing) — ✅ $1.32 in / $3.96 out (peak; cache-hit $0.044). **NEW** (GA Aug 13, 2026); permanent 75% cut (May 2026); off-peak 50% off.
- [DeepSeek V3.2](https://api-docs.deepseek.com/) — ⚠️ $0.28/$0.42 (third-party). Previous gen; off the official pricing page.

### Alibaba — Qwen

- [Qwen3.8 Flash](https://www.alibabacloud.com/help/en/model-studio/model-pricing) — ✅ $0.15 in / $0.47 out. **NEW** (Aug 26, 2026): 1M ctx; 90-day 1M-token free quota (Singapore); Apache 2.0 weights.
- [Qwen3.8 Omni Flash](https://www.alibabacloud.com/help/en/model-studio/model-pricing) — ✅ $0.15 in / $0.47 out (cache-hit $0.016). **NEW** (Sept 18, 2026): omni-modal (text/image/audio/video), API-only.
- [Qwen3.5 Flash](https://www.alibabacloud.com/help/en/model-studio/model-pricing) — ✅ $0.10 in / $0.40 out. 1M ctx; 50% batch discounts.
- [Qwen3.7 Flash](https://www.alibabacloud.com/help/en/model-studio/model-pricing) — ✅ $0.03 in / $0.13 out (≤32K tier). Among the cheapest hosted options anywhere.
- [Qwen Flash](https://www.alibabacloud.com/help/en/model-studio/model-pricing) — ✅ $0.05 in / $0.40 out (≤256K). Current default flash tier.
- [Qwen Turbo](https://www.alibabacloud.com/help/en/model-studio/model-pricing) — ✅ $0.05 in / $0.20 out. Legacy — page says "no longer updated; switch to Qwen-Flash".
- [Qwen3 Coder Flash](https://www.alibabacloud.com/help/en/model-studio/model-pricing) — ✅ $0.30 in / $1.50 out (≤32K). Code-specialized.

### Zhipu AI — GLM

- [GLM-5.3 Flash](https://docs.z.ai/guides/overview/pricing) — ✅ $0.15 in / $0.50 out (cached $0.03). **NEW** (~Aug 18, 2026).
- [GLM-5.3 FlashX](https://docs.z.ai/guides/overview/pricing) — ✅ $0.37 in / $1.25 out (cached $0.075). Higher-throughput tier.
- [GLM-4.7 FlashX](https://docs.z.ai/guides/overview/pricing) — ✅ $0.07 in / $0.40 out (cached $0.01). Cheapest paid GLM tier.
- [GLM-4.5 Air](https://docs.z.ai/guides/overview/pricing) — ✅ $0.20 in / $1.10 out (cached $0.03).
- [GLM-4.7 Flash / 4.5 Flash / 4.6V Flash](https://docs.z.ai/guides/overview/pricing) — ✅ **FREE** on all columns — zero-cost flash tier including a vision variant.
- Note: GLM Coding Plan went credits-based July 30, 2026 (Lite $18/mo, Pro $72/mo, Max $160/mo — reported); the three free Flash models remain free on the plain API.

### Moonshot AI — Kimi

- [Kimi K3](https://platform.kimi.ai/docs/pricing/chat-k25) — ⚠️ $3.00/$0.30 cached/$15.00 (third-party). **NEW** 2026: 2.8T-param frontier, 1M ctx.
- [Kimi K2.7 Code](https://platform.kimi.ai/docs/pricing/chat-k25) — ⚠️ $0.95/$0.19/$4.00 (third-party). **NEW** (Jun 12, 2026): 262K ctx.
- [Kimi K2.7 Code Highspeed](https://platform.kimi.ai/docs/pricing/chat-k25) — ⚠️ $1.90/$0.38/$8.00 (third-party). ~180–260 tok/s speed tier.
- [Kimi K2.6](https://platform.kimi.ai/docs/pricing/chat-k25) — ⚠️ $0.95/$0.16/$4.00 (third-party). **NEW** (Apr 2026): multimodal + thinking, 262K ctx.
- K2.5, moonshot-v1, and kimi-k2 were discontinued Aug 31, 2026. Official price table is JS-rendered — figures unverified.

### MiniMax

- [MiniMax M3](https://platform.minimax.io/docs/guides/pricing-paygo) — ✅ $0.30 in / $1.20 out (≤512K input). **NEW** 2026: 1M ctx, **permanent 50% off**; MIT weights.
- [MiniMax M2.7](https://platform.minimax.io/docs/guides/pricing-paygo) — ✅ $0.30 in / $1.20 out; cache-read $0.06. ~205K ctx.
- [MiniMax M2.7 Highspeed](https://platform.minimax.io/docs/guides/pricing-paygo) — ✅ $0.60 in / $2.40 out. 2× speed tier.
- [MiniMax M2.5 / M2.1 / M2](https://platform.minimax.io/docs/guides/pricing-paygo) — ✅ $0.30 in / $1.20 out. Legacy tiers (highspeed 2× variants).

### Xiaomi — MiMo

- [MiMo V2.6 Flash](https://mimo.mi.com/docs/en-US/price/pay-as-you-go) — ✅ $0.14 in / $0.28 out (cache-hit **$0.0028**). **NEW** (Sept 21–22, 2026): omni-modal open-weight standout; 1M ctx; cache write limited-time free; batch 50% off; MIT weights.
- [MiMo V2.6 Pro](https://mimo.mi.com/docs/en-US/price/pay-as-you-go) — ✅ $0.435 in / $0.87 out (cache-hit $0.0036). (v2.5 deprecated Oct 21, 2026.)

### StepFun

- [Step 3.7 Flash](https://github.com/stepfun-ai/Step-3.7-Flash) — ✅ $0.20 in / $1.15 out (cache-hit $0.04). **NEW** (May 28, 2026): 198B sparse MoE (~11B active), up to 400 tok/s, 3 reasoning levels, 256K ctx, Apache 2.0.
- [Step 3.5 Flash](https://github.com/stepfun-ai) — ⚠️ $0.10/$0.02/$0.30 (third-party). **NEW** (Jan 29, 2026).

### Baidu — ERNIE

- [ERNIE 4.5 Turbo](https://cloud.baidu.com/product/qianfan) — ⚠️ ~$0.11/$0.44 (third-party). ~80% off ERNIE 4.5; 128K ctx.
- [ERNIE X1 Turbo](https://cloud.baidu.com/product/qianfan) — ⚠️ ~$0.14/$0.55 (third-party). Efficient reasoning tier.
- [ERNIE 5.1](https://cloud.baidu.com/product/qianfan) — ⚠️ ~$0.59/$2.65 (third-party). **NEW** 2026 flagship.
- Baidu's Qianfan pricing page wasn't machine-readable — all figures unverified (CNY converted ≈ ¥7 = $1).

---

## Inference platforms

Hosted and serverless providers for serving flash-class models — the speed/cost angle is the whole game here.

| Platform | Type | Flash angle | Representative price (per 1M) | Confidence |
|---|---|---|---|---|
| [Groq](https://groq.com) | LPU chips | 394–1,000 tok/s; 50–100ms TTFT; free tier (no card) | Llama 3.3 70B ~$0.59/$0.79 | ⚠️ unverified (JS-walled pricing) |
| [Cerebras](https://inference-docs.cerebras.ai) | Wafer-scale chips | GPT-OSS 120B at ~3,000 tok/s | GPT-OSS 120B $0.35/$0.75 | ✅ verified |
| [Together AI](https://www.together.ai) | GPU cloud | 200+ open models; fine-tuning; 50%-off batch | GPT-OSS 120B $0.15/$0.60 | ✅ verified |
| [Fireworks AI](https://fireworks.ai) | GPU cloud | Fast-mode tiers; DeepSeek V4.1 Flash $0.30/$0.006 cached/$1.20 | GLM 5.3 Flash $0.15/$0.03/$0.50 | ✅ verified |
| [DeepInfra](https://deepinfra.com) | GPU cloud | Price leadership; zero-retention serving | DeepSeek-V4-Flash $0.09/$0.18 | ✅ verified |
| [Nebius Token Factory](https://tokenfactory.nebius.com) | GPU cloud | Per-model tok/s published; EU datacenters | DeepSeek-V4-Flash-0731 $0.14/$0.28 | ✅ verified |
| [Novita AI](https://novita.ai) | Serverless API | Aggressive pricing; free Ling Flash models | DeepSeek V4 Flash $0.14/$0.28 | ✅ verified |
| [SambaNova](https://cloud.sambanova.ai) | RDU chips | Full 16-bit precision at speed | Llama 3.3 70B ~$0.60/$1.20 | ⚠️ unverified |
| [OpenRouter](https://openrouter.ai) | Gateway | 300+ models, 60+ providers; no inference markup; `:free` pool | Provider rate + fee | ⚠️ fee unverified |
| [Hugging Face Inference Providers](https://huggingface.co/docs/api-inference/) | Gateway | 18 partners; `:cheapest` routing; auto-failover | No markup on provider rates | ✅ partner list verified |
| [Baseten](https://www.baseten.co/) | Serverless + dedicated GPUs | Managed TensorRT-LLM; per-minute billing, no idle cost | Unverified | ⚠️ unverified |
| [Chutes](https://chutes.ai/) | Decentralized (Bittensor) | 100% Intel TDX TEEs; onchain USDC settlement | Single-digit cents/1M (some models) | ⚠️ unverified |
| [Modal](https://modal.com/) | Serverless GPUs | Bring-your-own vLLM; per-second billing, scale to zero | GPU-hr rates vary | ⚠️ unverified |
| [Replicate](https://replicate.com/) | Marketplace | Thousands of community models; Cog packaging | Per-second GPU billing | ⚠️ unverified |
| [Cloudflare Workers AI](https://www.cloudflare.com/products/workers-ai/) | Edge GPUs | 200+ cities; 10K neurons/day free; no idle costs | ~$0.088/$0.606 (Llama 3.1 8B) | ⚠️ unverified |
| [Parasail](https://parasail.io/) | vLLM supercloud | Day-zero open models; batch 80–90% off realtime | DeepSeek-V4-Flash ~$0.14/$0.28 | ⚠️ unverified |
| [Hyperbolic](https://hyperbolic.xyz/) | GPU marketplace | Serverless inference + GPU rentals from $0.50/hr (4090) | Pay-per-token | ⚠️ unverified |
| [Lambda](https://lambdalabs.com/) | GPU cloud | Dedicated rentals + Inference API (2026 status unverified) | $0.02–$0.90/1M at launch | ⚠️ unverified |
| [fal.ai](https://fal.ai/) | Media GPUs | ⚠️ Generative media only (image/video/audio) — not an LLM platform | — | n/a |

All inference platforms above offer OpenAI-compatible endpoints unless noted.

---

## Self-hosting stacks

Serve efficient open-weight models yourself — zero per-token cost after hardware.

- [vLLM](https://github.com/vllm-project/vllm) — High-throughput engine (PagedAttention + continuous batching), OpenAI-compatible server. GPTQ/AWQ/FP8/Marlin quantization, speculative decoding, tensor/data/expert parallelism. The de-facto baseline — maximizes tokens/sec/$ on rented GPUs. License Apache-2.0 (verified).
- [SGLang](https://github.com/sgl-project/sglang) — RadixAttention prefix caching; structured outputs; disaggregated prefill (3.8× prefill / 4.8× decode gains); day-0 open-model support (DeepSeek-V4, gpt-oss, Qwen3, MiniMax M2, MiMo-V2-Flash). License Apache-2.0 (verified).
- [Ollama](https://github.com/ollama/ollama) — Dead-simple local runtime: `ollama run` pulls, quantizes, and serves hundreds of pre-quantized models (Llama 4, Qwen 3.5, Gemma 4, GPT-OSS) behind a local OpenAI-compatible API. Zero marginal cost. License MIT (verified). v0.34.0, 176K+ stars.
- [llama.cpp](https://github.com/ggml-org/llama.cpp) — Pure C/C++ inference + the GGUF format standard; K-quants + imatrix 2–8-bit; built-in `llama-server`. Best cost-performance on non-NVIDIA hardware (laptops, Apple Silicon, edge). License MIT (verified).
- [TensorRT-LLM](https://github.com/NVIDIA/TensorRT-LLM) — NVIDIA's max-perf library: FP8/INT4/FP4 on Hopper, in-flight batching, XQA kernels (24K+ tok/s on Llama 3 cited). The engine under Baseten's pre-optimized Model APIs. License Apache-2.0 (verified).
- [LMDeploy](https://github.com/InternLM/lmdeploy) — InternLM team's compress/deploy/serve toolkit; TurboMind backend; W8A8/W4A16 + KV-cache quantization + prefix caching; ~1.8× throughput vs vLLM per its own docs. License Apache-2.0 (verified).
- [TGI](https://github.com/huggingface/text-generation-inference) — ⚠️ **Archived upstream** (maintenance mode). HF's production serving toolkit; still a proven baseline, but prefer vLLM/SGLang for new deployments. License Apache-2.0 (verified).
- [TensorZero](https://github.com/tensorzero/tensorzero) — ⚠️ **Archived upstream 2026-06-12** (use a live fork). Not a serving engine — an LLMOps gateway for cheapest-provider routing, prompt-caching policies, and feedback-driven model downgrades: the cost-control layer that keeps a fleet flash-class. License Apache-2.0 (verified).

---

## Benchmarks & eval notes

### Vendor-reported speed figures (treat as vendor claims, not independent)

- **Cerebras:** GPT-OSS 120B ~3,000 tok/s; Llama 3.1 70B ~1,800 tok/s (Artificial Analysis measured).
- **Groq:** Llama 3.1 8B ~840 tok/s; GPT-OSS 120B ~500 tok/s; 50–100ms TTFT.
- **SambaNova:** Llama 3.1 405B at 132 tok/s (full 16-bit); Llama 3.1 70B at 461 tok/s.
- **Nebius Token Factory:** publishes per-model tok/s in its API catalog (e.g. DeepSeek-V4-Flash-0731 351 tok/s, MiniMax-M3 248 tok/s).
- **StepFun:** Step 3.7 Flash up to 400 tok/s.
- **Kimi:** K2.7 Code Highspeed ~180–260 tok/s.

### Methodology caveats — read before comparing

- **Vendor tok/s ≠ your workload:** throughput depends on batch size, sequence length, quantization, and hardware generation. Single-stream chat latency (TTFT) and bulk throughput are different numbers.
- **Reasoning/thinking tokens are billed:** "thinking" variants emit intermediate tokens charged as output — a cheap $/M rate with heavy thinking can cost more per task than a pricier non-thinking model.
- **Cache-hit rates dominate real cost:** agentic loops with long system prompts see 50–90%+ cache hits; compare *effective* $/task, not sticker $/M.
- **Off-peak and batch discounts are large:** DeepSeek off-peak 50% off, most vendors' batch APIs 50% off — schedule bulk work accordingly.
- **Prices move fast:** MiniMax M3's "permanent 50% off", Qwen's free quotas, Zhipu's "limited-time free" cache storage, and Nebius's announced +18.3% dedicated-endpoint rise (Oct 1, 2026) all show why every price here carries a verification date.

---

## Guides

- [Choosing a flash model](docs/choosing-a-flash-model.md) — which efficiency tier fits agents, RAG, coding, or bulk processing.
- [Deployment guide](docs/deployment-guide.md) — hosted API vs inference platform vs self-host: decision framework.
- [Pricing comparison](docs/pricing-comparison.md) — verified-price table with the $/task math that matters.
- [Glossary](docs/glossary.md) — TTFT, context caching, speculative decoding, LPU, disaggregated prefill, and more.
- [Status changes](docs/status-changes.md) — retirements and material pricing changes, newest first.
- [Machine-readable catalog](data/models.json) / [platform catalog](data/platforms.json) — every entry with price-verification status.

## Related repositories

- [awesome-fast-llms](https://github.com/dakotac1994/awesome-fast-llms) — sibling list: LLM inference **speed** — low latency/TTFT and high throughput (tok/s), with every speed claim sourced, dated, and labeled vendor-reported vs independent. (This list covers cost-performance.)

## Related repositories

- [awesome-flagship-llms](https://github.com/dakotac1994/awesome-flagship-llms) — sibling list: flagship frontier LLMs, pricing, and benchmarks.
- [awesome-fast-llms](https://github.com/dakotac1994/awesome-fast-llms) — sibling list: inference-speed LLMs, providers, engines, and optimization techniques.
- [awesome-free-llms](https://github.com/dakotac1994/awesome-free-llms) — sibling list: free LLM API tiers, free chat apps, and open-weight local models.
- [awesome-decisions-llms](https://github.com/dakotac1994/awesome-decisions-llms) — sibling list: LLMs and systems for decision-making — decision-tuned models, decision benchmarks & evals, frameworks, and key research papers.

## Contributing

Entries and corrections are welcome — see [CONTRIBUTING.md](CONTRIBUTING.md). Every PR is checked by CI: lychee link check over all markdown files, and JSON-schema validation of `data/models.json` and `data/platforms.json` (including the `price_verified` boolean and required `pricing_url` for verified prices).

## License

[MIT](LICENSE) © 2026 dakotac1994

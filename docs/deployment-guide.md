# Deployment guide

Hosted API vs inference platform vs self-host — how to serve flash-class models.

## The three routes

### 1. Vendor hosted API (simplest)
Call the lab directly: Gemini API, OpenAI, DeepSeek, Qwen (Model Studio), Zhipu, MiniMax, MiMo, Mistral, xAI, Anthropic, Bedrock (Nova). Best when you want the vendor's newest flash model on day one, with their caching and batch discounts. Nearly all are OpenAI-compatible.

### 2. Inference platform (best $/perf for open models)
Use when you run open-weight models (Llama, Qwen, DeepSeek, Kimi, GPT-OSS, GLM) and want someone else to handle GPUs:
- **Raw speed:** Cerebras (wafer-scale, ~3,000 tok/s on GPT-OSS 120B), Groq (LPUs, sub-100ms TTFT), SambaNova (RDU, full precision).
- **Lowest $/token:** DeepInfra, Novita, Fireworks, Nebius Token Factory, Parasail — compare the [pricing table](pricing-comparison.md).
- **One key, many providers:** OpenRouter or Hugging Face Inference Providers (`:cheapest` routing + failover).
- **Bring your own code:** Modal or Baseten (deploy vLLM yourself, per-second/per-minute billing).

### 3. Self-host (zero per-token cost)
Use when volume is high and steady, data can't leave your infra, or you need custom quantization:
- **General serving:** vLLM (baseline) or SGLang (prefix caching for agentic workloads, disaggregated prefill at scale).
- **NVIDIA-max:** TensorRT-LLM (highest tok/s per GPU); LMDeploy for quantization-first Qwen/DeepSeek stacks.
- **Local/dev:** Ollama (one command), llama.cpp (any hardware, GGUF quants).
- Rule of thumb: self-hosting beats API pricing once sustained throughput saturates a GPU — below that, serverless per-token wins.

## Decision framework

1. **Prototype on a vendor API or gateway** (OpenRouter / HF Providers) — zero infra, swap models by name.
2. **Optimize the hot path** — move your highest-volume model to the cheapest fast platform (check verified prices in `data/platforms.json`).
3. **Turn on caching + batch** — context caching and 50%-off batch APIs are the two biggest discounts available; both are configuration, not code.
4. **Self-host only the steady-state bulk** — keep bursty/edge traffic on serverless.
5. **Add a cost-control layer** — gateway routing (cheapest-provider failover), cache policies, and model downgrades keep a fleet flash-class as prices move.

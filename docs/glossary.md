# Glossary

Terms that recur across efficient-LLM model cards, pricing pages, and inference platforms.

- **Flash-class** — this list's shorthand for a vendor's efficiency-tier model: the fastest, cheapest model in a family that still clears a quality bar (e.g. Gemini Flash, GPT-5-mini, Claude Haiku, Kimi's speed variants, Qwen Turbo). Not a formal standard — each vendor defines its own tier.
- **$/1M tokens** — the standard unit for API pricing: dollars per one million input tokens in / output tokens out. Input and output are priced separately; output is usually 2–4× input.
- **Context window** — the maximum tokens a model can attend to in one request (input + output). Flash-class models in 2026 typically offer 128K–1M+ token windows; a large window on a cheap model is the headline value proposition.
- **TTFT (time to first token)** — latency until the first output token streams back. The metric that matters for interactive agents and chat; inference-chip providers (Groq, Cerebras) optimize it aggressively.
- **Throughput (tokens/sec)** — sustained generation speed. Batch/offline workloads care about this more than TTFT; it drives effective cost per task.
- **Context caching** — reusing the KV-cache of a repeated prompt prefix across requests (explicit or implicit). Cuts input cost and TTFT for agentic loops with long system prompts; discount rates vary by vendor (typically 50–90% off cached tokens).
- **Batch API** — asynchronous, non-urgent inference at a steep discount (often 50% off) in exchange for relaxed latency (minutes–hours). Ideal for evals, distillation, and bulk processing.
- **Speculative decoding** — a small draft model proposes tokens that the large model verifies in parallel, raising throughput without quality loss. Supported by vLLM, SGLang, TensorRT-LLM, and several hosted providers.
- **Quantization** — shrinking model weights (FP16 → INT8/INT4/FP8) to cut memory and raise throughput, with small quality trade-offs. The main lever self-hosters use to make efficient models cheaper still; llama.cpp, vLLM, and Ollama all ship quantized builds.
- **Disaggregated prefill/decode** — splitting prompt processing (prefill) from token generation (decode) onto different hardware, each tuned for its phase. Used by SGLang and large-scale serving stacks to lift throughput.
- **LPU / wafer-scale** — non-GPU inference silicon: Groq's Language Processing Unit and Cerebras' wafer-scale engine, both purpose-built for transformer inference with very high tokens/sec on supported models.
- **OpenAI-compatible endpoint** — an API that speaks the OpenAI chat-completions (and usually embeddings) wire format, so clients switch providers by changing base URL + key. Nearly every inference platform in this list offers one.
- **Aggregation gateway** — a provider (e.g. OpenRouter) that routes to many underlying model providers behind one key, with fallbacks and price comparison, rather than serving models on its own hardware.
- **Reasoning / thinking tokens** — intermediate chain-of-thought tokens some models emit (often billed as output). Efficiency-tier "thinking" variants trade extra tokens for better reasoning scores — watch the billed-token math.

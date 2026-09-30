# Choosing a flash model

How to pick among 60+ efficiency-tier models. Prices below are as of **2026-09-29** (✅ = verified on official pricing pages that day).

## Start with the workload

- **High-volume agents / tool-calling loops** — you want cheap input + cheap cache hits, since system prompts repeat. Top picks: **DeepSeek V4.1 Flash** (✅ $0.30 in / $0.006 cache-hit, off-peak 50% off), **MiMo V2.6 Flash** (✅ $0.14 / $0.0028 cache-hit), **Qwen3.8 Flash** (✅ $0.15 in), **Gemini 2.5 Flash-Lite** (✅ $0.10 in).
- **RAG / long-context retrieval** — 1M-context cheap models win: **DeepSeek V4.1 Flash**, **Qwen3.8 Flash**, **Kimi K3** (⚠️ $3.00/$15.00 — pricier, frontier quality), **Claude Haiku 4.5** (✅ $1.00/$5.00, 200K ctx).
- **Coding agents** — **Qwen3 Coder Flash** (✅ $0.30/$1.50), **Kimi K2.7 Code Highspeed** (⚠️ ~180–260 tok/s), **Codestral** (✅ $0.30/$0.90), **Gemini 3.8 Flash** (⚠️ — "most intelligent Flash", per Google).
- **Bulk processing / evals / distillation** — use **batch APIs** (typically 50% off): DeepSeek, Qwen, Mistral, Anthropic, Fireworks, Together, and Novita all offer them. Schedule during **DeepSeek off-peak** for another 50% off.
- **Simple classification / extraction at scale** — the floor: **Zhipu GLM Flash models are FREE** (✅ $0.00), **Ministral 3 3B** (✅ $0.10/$0.10), **Qwen3.7 Flash** (✅ $0.03/$0.13 ≤32K), **Novita's free Ling Flash models** (✅, status can change — check the page).

## Decision rules

1. **Compute $/task, not $/token.** A $0.10/M model that needs 3 retries loses to a $0.30/M model that gets it right once. Benchmark on *your* prompts.
2. **Cache-hit rate is the biggest lever.** Agentic loops with stable system prompts routinely see 50–90%+ cache hits — a model with $0.0028/M cache reads (MiMo) can beat a cheaper sticker price elsewhere.
3. **Watch thinking-token billing.** Reasoning variants bill intermediate tokens as output; compare effective cost per completed task.
4. **Prefer verified prices.** Entries marked ⚠️ unverified come from third parties — re-check the vendor page before committing budget.
5. **Mind the deprecations.** Qwen-Turbo → Qwen-Flash; Kimi K2.5/moonshot-v1 discontinued Aug 31, 2026; MiMo v2.5 deprecated Oct 21, 2026; old xAI `grok-4-fast` names retired.

# Contributing

Thanks for helping keep this the most current directory of Flash-class LLMs and the platforms that serve them!

## Adding an entry

1. **Check it fits:** a fast, cheap, high cost-performance ("Flash-class") LLM — a vendor's efficiency-tier model or an open-weights model notable for speed/cost — or a platform/stack for deploying and serving such models (serverless inference, aggregation gateway, GPU cloud, or self-hosting software). A PR must point at a primary source: the vendor's pricing/docs page or the project's repo.
2. **Add to the right section** of `README.md`:
   - Flash-class models → vendor's efficiency-tier models, open-weights efficient models
   - Inference platforms → hosted/serverless inference providers and gateways (the platforms table)
   - Self-hosting stacks → vLLM, SGLang, Ollama, llama.cpp, TensorRT-LLM and friends
   - Benchmarks & eval notes → published measurements with sources, labeled by confidence
   - Archived / deprecated → retired models or shut-down providers with the date and successor
3. **One entry = one bullet** (or one table row for platforms). Format:
   `- [Name](https://official-site-or-docs) — ` one-line description + 2–4 key facts inline.
   Tag price confidence honestly: write `✅ verified 2026-09-29` only when you read the price on the vendor's official pricing page yourself; otherwise mark it `⚠️ unverified`.
4. **Add the matching record** to `data/models.json` or `data/platforms.json` with these exact fields:

| field | type | values |
|---|---|---|
| `name` | string | model or platform name |
| `vendor` | string | vendor / organization |
| `url` | string | official https:// URL (pricing page preferred for models) |
| `description` | string | one sentence |
| `price_input_per_1m` | string | e.g. `"$0.10"` or `"unverified"` |
| `price_output_per_1m` | string | e.g. `"$0.40"` or `"unverified"` |
| `price_verified` | bool | `true` only if you read the price on an official pricing page |
| `pricing_url` | string | official pricing page URL, or `""` |
| `status` | string | `active` / `maintenance` / `archived` / `commercial` |
| `category` | string | `model` / `platform` / `selfhost` |
| `features` | string[] | 3–6 key capabilities |

5. **Status changes:** if a model is retired, a provider shuts down, or pricing changes materially, update its README entry *and* add a row (newest-first) to `docs/status-changes.md`.

## Style rules

- Link the **official site** (vendor pricing/docs page or project repo), never a blog post or reseller.
- Facts that can change (prices, context windows, release versions) get "as of" context in prose or are omitted — link the source instead of hard-coding numbers that rot.
- Vendor claims stay labeled as vendor claims ("vendor claims", "reported by community sources").
- Prices in the README are stamped with their verification date; never guess a price.
- Keep README descriptions to one entry per bullet; put depth in `docs/`.

## CI

Every PR runs:
- **Link check** (lychee) over all markdown files — no dead links.
- **JSON validation** — `data/models.json` and `data/platforms.json` must parse, every record must have the required fields, and `status`/`category` must be from the allowed sets above.

Run locally before pushing:

```bash
python3 -c "import json; [json.load(open(f'data/{n}.json')) for n in ('models','platforms')]; print('ok')"
```

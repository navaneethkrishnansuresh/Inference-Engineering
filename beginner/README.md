# Beginner

The goal of this level is to build the core pieces of a small LLM serving runtime, rather than only learning how to call a high-level generation API.

The path is intentionally incremental:

```text
prompt
  → tokenizer
  → embeddings
  → prefill
  → logits
  → token selection
  → KV cache
  → decode loop
  → sampling
  → request state
  → scheduler
  → continuous batching
  → KV-cache management
  → benchmarking
```

The implementation here is simplified on purpose. Production engines such as vLLM and SGLang work on the same broad categories of problems, but at a much deeper and more optimized level.

## Chapters

| Chapter | Topic | Status |
| --- | --- | --- |
| 01 | [Manual LLM Inference From First Principles](01_manual_llm_inference/01_manual_llm_inference.ipynb) | Available |
| 02 | [Sampling — build the sampler without `generate()`](02_sampling/02_sampling.ipynb) | Available |

Future topics are tracked in the [main roadmap](../README.md#1-beginner). They are plans, not completed chapters.

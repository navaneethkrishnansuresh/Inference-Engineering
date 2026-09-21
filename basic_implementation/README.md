# Basic Implementation

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

## Parts

| Part | Topic | Status |
| --- | --- | --- |
| 01 | [Manual LLM Inference From First Principles](01_manual_llm_inference/01_manual_llm_inference.ipynb) | Available |
| 02 | [Sampling: Temperature, Top-k and Top-p](02_sampling/02_sampling.ipynb) | Available |
| 03 | [Multi-Request State](03_multi_request_state/03_multi_request_state.ipynb) | Available |
| 04 | [Simple Scheduler](04_simple_scheduler/04_simple_scheduler.ipynb) | Available |

Future topics are listed in the [main README](../README.md#1-basic-implementation). They are planned work, not completed parts.

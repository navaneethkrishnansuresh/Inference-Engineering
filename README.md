# Inference Engineering From First Principles

This repository documents how an LLM inference runtime is built from first principles.

The goal is to understand what actually happens when an LLM serves a request: how prompts are processed, how tokens are generated, how KV cache grows, how requests are scheduled, how batching works, where GPU memory goes, and why inference engines need all the systems around the model itself.

We start from the smallest useful pieces and build upward:

tokenization
→ prefill
→ decode
→ KV cache
→ sampling
→ request state
→ scheduling
→ continuous batching
→ memory management
→ serving-engine internals

The focus is not on training models or getting better model quality. It is on the runtime side of LLMs: latency, throughput, memory, scheduling, GPU utilization, and the systems that make serving efficient.

Everything is implementation-first. We inspect tensors, cache state, memory usage and model outputs directly, then gradually turn those pieces into a small inference runtime.

The repository is split into Beginner, Intermediate and Advanced levels. Beginner contains the current work. Intermediate and Advanced will be added as the project moves deeper into real inference-engine and GPU systems work.

The list is intentionally flexible. Topics may be added, split, or reordered as the implementation grows.

New parts will be added every one to two days when possible.



## What This Repository Builds

### 1. Beginner

**Status:** Current work

Beginner builds the core mental model of what happens when an LLM generates tokens.

| Part | Topic | Status |
| --- | --- | --- |
| 01 | [Manual LLM Inference From First Principles](beginner/01_manual_llm_inference/01_manual_llm_inference.ipynb) | Available |
| 02 | [Sampling: Temperature, Top-k and Top-p](beginner/02_sampling/02_sampling.ipynb) | Available |
| 03 | [Multi-Request State](beginner/03_multi_request_state/03_multi_request_state.ipynb) | Available |
| 04 | Simple Scheduler | Planned |
| 05 | Continuous Batching | Planned |
| 06 | KV Cache Management | Planned |
| 07 | Paged / Block KV Cache | Planned |
| 08 | Prefix Caching | Planned |
| 09 | Benchmarking Inference | Planned |

This list will change as the implementation gets deeper.

### 2. Intermediate

**Status:** Not available yet

Intermediate work begins after the Beginner runtime is complete and the project moves deeper into performance and real inference-engine internals.

### 3. Advanced

**Status:** Not available yet

Advanced work comes later with deeper GPU/runtime optimization and production inference systems.

## Begin Here

Open [Part 1](beginner/01_manual_llm_inference/) and work through the notebook in order.

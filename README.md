# Inference Engineering Zero to Hero

This repository is a hands-on path into LLM inference engineering.

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

The repository is split into Beginner, Intermediate and Advanced levels. Beginner is being built now. Intermediate and Advanced will be added as the project moves deeper into real inference-engine and GPU systems work.

The roadmap is intentionally flexible. Topics may be added, split or reordered as new problems show up while building.

I will try to add a new chapter every one to two days as I progress.



## Learning Path

### 1. Beginner

**Status:** In progress

The Beginner track builds the core mental model of what happens when an LLM generates tokens.

| Chapter | Topic | Status |
| --- | --- | --- |
| 01 | [Manual LLM Inference From First Principles](beginner/01_manual_llm_inference/01_manual_llm_inference.ipynb) | Available |
| 02 | [Sampling — build the sampler without `generate()`](beginner/02_sampling/02_sampling.ipynb) | Available |
| 03 | Request State | Planned |
| 04 | Simple Scheduler | Planned |
| 05 | Continuous Batching | Planned |
| 06 | KV Cache Management | Planned |
| 07 | Paged / Block KV Cache | Planned |
| 08 | Prefix Caching | Planned |
| 09 | Benchmarking Inference | Planned |

This roadmap will evolve. Chapters may be added, removed, split, or reordered as the implementation gets deeper.

### 2. Intermediate

**Status:** Not available yet

Intermediate material will be added after the Beginner runtime is complete and the project moves deeper into performance and real inference-engine internals.

### 3. Advanced

**Status:** Not available yet

Advanced material will come later as the project moves into deeper GPU/runtime optimization and production inference systems.

## Start here

Open [Chapter 1](beginner/01_manual_llm_inference/) and work through the notebook in order.

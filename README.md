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

## Disclaimer

This is my personal implementation work around LLM inference. Take inspiration from it, use it to learn a few things, and adapt ideas for your own experiments.

It is not a production serving system or a claim of a new state-of-the-art method.

Please skip this for now if you do not have basic PyTorch, machine learning, and Transformer knowledge. If you are a larper who only wants to skim keywords, this repo is not for you. It is meant for people who want to read the code, run it, and understand what each part does.

The repository is split into Basic Implementation, Intermediate Implementation, and Advanced Implementation. Basic Implementation contains the current work. The other sections will be added as the project moves deeper into real inference-engine and GPU systems work.

Topics may be added, split, or reordered as the implementation grows.

New parts will be added every one to two days when possible.



## What This Repository Builds

### 1. Basic Implementation

**Status:** Current work

Basic Implementation builds the core mental model of what happens when an LLM generates tokens.

| Part | Topic | Status |
| --- | --- | --- |
| 01 | [Manual LLM Inference From First Principles](basic_implementation/01_manual_llm_inference/01_manual_llm_inference.ipynb) | Available |
| 02 | [Sampling: Temperature, Top-k and Top-p](basic_implementation/02_sampling/02_sampling.ipynb) | Available |
| 03 | [Multi-Request State](basic_implementation/03_multi_request_state/03_multi_request_state.ipynb) | Available |
| 04 | [Simple Scheduler](basic_implementation/04_simple_scheduler/04_simple_scheduler.ipynb) | Available |
| 05A | [Continuous Batching Foundations](basic_implementation/05a_continuous_batching_foundations/05a_continuous_batching_foundations.ipynb) | Available |
| 05B | [Dynamic Continuous Batching](basic_implementation/05b_dynamic_continuous_batching/) | Not available yet |
| 06 | KV Cache Management | Planned |
| 07 | Paged / Block KV Cache | Planned |
| 08 | Prefix Caching | Planned |
| 09 | Benchmarking Inference | Planned |

This list will change as the implementation gets deeper.

### 2. Intermediate Implementation

**Status:** Not available yet

Intermediate work begins after the Basic Implementation runtime is complete and the project moves deeper into performance and real inference-engine internals.

### 3. Advanced Implementation

**Status:** Not available yet

Advanced work comes later with deeper GPU/runtime optimization and production inference systems.

## Begin Here

Open [Part 1](basic_implementation/01_manual_llm_inference/) and work through the notebook in order.

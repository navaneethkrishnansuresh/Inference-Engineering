# Inference Engineering From First Principles

Most tutorials show how to call `model.generate()`.

This repository goes in the other direction. We start with a pretrained model and rebuild the pieces beneath generation: tokenization, prefill, the KV cache, decoding, sampling, request state, scheduling, batching, and eventually memory-management ideas used by real inference systems.

The focus is on understanding the runtime, not model quality, so the early chapters use small models. The notebooks are designed to run in Google Colab; a T4 or A100 GPU is useful for the early experiments.

This is a learning project built in public while I progress. The roadmap is not fixed. More chapters and topics may be added as the project progresses and as new concepts become necessary.

## Course Structure

### 1. Beginner

**Status:** In progress

The Beginner track builds the core mental model of what happens when an LLM generates tokens.

| Chapter | Topic | Status |
| --- | --- | --- |
| 01 | [Manual LLM Inference From First Principles](beginner/01_manual_llm_inference/) | Available |
| 02 | Sampling | Planned |
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

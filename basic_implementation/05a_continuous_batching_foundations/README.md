# Part 5A: Continuous Batching Foundations

This part shows why a serving engine must schedule again after every generation step. Requests can finish and new waiting requests can take their place instead of waiting for a fixed batch to end.

Open the notebook: [05a_continuous_batching_foundations.ipynb](05a_continuous_batching_foundations.ipynb)

## Inside this part

1. Why continuous batching exists
2. Request lifecycle: `waiting → running → finished`
3. Iteration-level scheduling
4. Re-running the scheduler after every generation step
5. Real model inference inside scheduled requests
6. Per-request KV cache
7. Prefill → decode transition
8. Attention masks and why they matter now
9. Different sequence lengths
10. Left padding for batched inference
11. Building a real batch from multiple running requests
12. First actual batched model forward pass
13. Mapping batched outputs back to individual requests

## Boundary of this part

The final batched forward pass is a fixed-batch experiment. Its KV cache belongs to that batch, not to independently movable requests. It does not yet perform batched decode or safely handle `[A, B] → [B, C]`.

Part 5B picks up from that boundary.

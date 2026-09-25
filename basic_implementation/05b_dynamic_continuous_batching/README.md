# Part 5B: Dynamic Continuous Batching

Not available yet.

This part will turn the fixed-batch experiment from Part 5A into a dynamic batch that can change while generation is running.

## Planned work

1. Batched decode with KV cache
2. Dynamic active batches such as `[A, B] → [B, C]`
3. Preserving KV state when requests enter and leave
4. New-request prefill while existing requests are decoding
5. Prefill vs decode scheduling
6. Token-budget-aware scheduling with `max_tokens_per_step`
7. Scheduling based on token cost instead of only request count
8. Large prompts and scheduler fairness
9. Chunked prefill
10. Preventing long prefills from blocking decode requests
11. Final dynamic continuous-batching scheduler
12. An end-to-end engine loop with request admission, token budgeting, prefill, decode, batched execution, completion, and continuous refill

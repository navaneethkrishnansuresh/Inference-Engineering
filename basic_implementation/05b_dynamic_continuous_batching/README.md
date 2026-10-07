# Part 5B: Dynamic Continuous Batching

This part turns the fixed batch from Part 5A into an active batch that can change while generation is running.

## Index

1. **Batched Decode With KV Cache**
   - batched prefill and batched decode
   - one next token per active request
2. **Removing Finished Requests From the Batch**
   - detect completed requests
   - compact `running`, `next_tokens`, attention masks, and KV-cache rows
3. **Dynamic Request Admission**
   - transition from `[A, B]` to `[B]` to `[B, C]`
   - preserve B's existing KV state
4. **Prefill + Decode Coexistence**
   - an existing request decodes while a new request performs prefill
   - align and merge their cache state before batched decode continues
5. **Token-Budget-Aware Scheduling**
   - `max_tokens_per_step`
   - decode cost is one token per request
   - prefill cost is the prompt token count
6. **Prefill Deferral**
   - a prefill stays waiting when it does not fit the remaining budget
   - no chunked prefill yet
7. **Final Dynamic Continuous-Batching Engine**
   - scheduling, decode, prefill, token accounting, completion, KV compaction, admission, and continuous refill
8. **End-to-End Execution Trace**
   - requests entering and leaving
   - prefill and decode in the same scheduler iteration
   - budget usage per step
9. **Part 5B Conclusion**
   - next: Part 6, KV Cache Management

The notebook uses dense Transformers cache tensors to make the state changes visible. Production engines avoid repeatedly slicing, padding, and concatenating large cache tensors.

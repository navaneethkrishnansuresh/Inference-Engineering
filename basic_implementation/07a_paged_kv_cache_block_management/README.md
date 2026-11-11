# Part 7A: Paged KV Cache Block Allocation and Management

This part replaces logical KV-token capacity with fixed-size physical blocks. It builds the allocation metadata and scheduler behavior needed to allocate, grow, reuse, and release KV cache capacity across concurrent requests.

Open the notebook: [07a_paged_kv_cache_block_management.ipynb](07a_paged_kv_cache_block_management.ipynb)

## Index

1. **KV Memory Accounting and Fixed-Size Blocks**
   - inspect Qwen2.5-0.5B's KV-cache dimensions
   - calculate KV bytes per token and per block
   - calculate block requirements and internal fragmentation
2. **Physical Block Pool and Free List**
   - allocate and release physical block IDs
   - reject allocation that cannot be fully satisfied
   - reuse returned blocks
3. **Per-Request Block Tables**
   - map logical KV blocks to physical block IDs
   - locate a token by logical block and within-block offset
   - support noncontiguous physical allocations
4. **Dynamic KV Cache Growth**
   - grow a request without relocating existing blocks
   - allocate a new block only when the current capacity is full
   - preserve state when a growth allocation fails
5. **Block-Aware Continuous Batching Scheduler**
   - admit prefill only when compute budget and physical blocks are available
   - prioritize decode while allocating a new block when needed
   - release blocks when requests finish and admit waiting work
   - validate pool, block-table, and request-state accounting every step
6. **Part 7A Conclusion**
   - this part manages block IDs and allocation state, not actual K/V tensors
   - next: Part 7B, physical K/V storage and PagedAttention

The implementation is a metadata-level simulation. Physical tensor storage, paged K/V reads, PagedAttention, and quantitative memory experiments are reserved for Part 7B.

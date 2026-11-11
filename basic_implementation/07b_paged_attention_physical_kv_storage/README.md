# Part 7B: PagedAttention, Physical KV Storage and Memory Analysis

**Status:** Not available yet

Part 7A focused on how KV cache blocks are allocated, tracked, and released.

Part 7B will focus on how actual Key and Value tensors are stored in those blocks, how attention accesses them, and how efficiently that memory is used.

It will build on the `BlockPool`, `RequestBlockManager`, and block-aware scheduler from Part 7A instead of implementing them again.

## Index

1. **Setup: Model Configuration and Actual KV Storage**
   - reuse Qwen2.5-0.5B's architecture
   - set up PyTorch and GPU execution
   - allocate K/V storage tensors with physical block dimensions
   - connect physical block IDs to tensor storage locations
   - outcome: a tensor-backed KV block pool
2. **Writing K/V Tensors Into Physical Blocks**
   - generate real K/V tensors from a small transformer
   - inspect per-layer K/V tensor shapes
   - write K/V into paged storage using block tables
   - handle partially filled blocks and block boundaries
   - outcome: real K/V data in noncontiguous physical blocks
3. **Reading Paged KV Cache and Logical-to-Physical Addressing**
   - locate token K/V with a logical block index and offset
   - read cached K/V from arbitrary physical blocks
   - reconstruct a logical K/V sequence for validation
   - compare it with an ordinary contiguous KV cache
   - outcome: verify that paged storage preserves the correct K/V sequence
4. **Implementing PagedAttention**
   - recap scaled dot-product attention and GQA
   - use block tables to guide attention over paged K/V
   - compare output with a contiguous attention reference
   - explain why production kernels avoid gathering the full KV cache into one contiguous tensor
   - outcome: a reference PagedAttention implementation with numerical checks
5. **Memory Pressure and Fragmentation Experiments**
   - measure physical KV block utilization across scheduling iterations
   - calculate internal fragmentation and unused token slots
   - observe KV blocking when the pool runs out of blocks
   - measure how block reuse changes available capacity
   - compare logical KV usage with physically allocated capacity
   - outcome: quantitative analysis of the block-aware scheduler's memory behavior
6. **End-to-End Paged KV Cache Validation**
   - run a prefill and multi-step decode workflow
   - grow physical KV cache as tokens are processed
   - compare paged attention output with contiguous attention output
   - check block-table correctness and memory release
   - verify numerical correctness with tolerances
   - outcome: an end-to-end paged KV cache and attention demonstration

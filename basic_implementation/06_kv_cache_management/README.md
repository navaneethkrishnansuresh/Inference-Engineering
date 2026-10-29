# Part 6: KV Cache Management

This part treats KV cache as a limited resource that an inference engine must allocate, grow, track, and release for every request.

Open the notebook: [06_kv_cache_management.ipynb](06_kv_cache_management.ipynb)

## Index

1. **KV Cache as a Managed Resource**
   - why dense cache rebuilding does not work for changing request sets
   - request lifecycle: allocate, use, grow, free
2. **KV Memory Cost**
   - estimate KV bytes per token from model architecture
   - observe memory growth with longer contexts and concurrent requests
3. **Basic KV-Cache Manager**
   - total, used, and free logical token capacity
   - per-request allocation, decode growth, and release
4. **Capacity-Aware Scheduling**
   - separate compute capacity from KV capacity
   - show that KV exhaustion can block new and already-running requests
5. **Real KV Accounting**
   - connect the manager to request-owned `DynamicCache` objects
   - verify logical allocations against actual cache sequence lengths
   - reclaim KV capacity as requests finish and admit new work
6. **Part 6 Conclusion**
   - next: Part 7, paged KV cache allocation and PagedAttention

The manager tracks logical cached-token capacity. It does not yet allocate physical GPU blocks or solve fragmentation. Those are the next problems.

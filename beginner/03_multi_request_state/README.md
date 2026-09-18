# Part 3: Multi-Request State

The first two parts work with one request at a time. This part gives every active request its own state, so several requests can exist independently before scheduling or batching is added.

Open the notebook: [03_multi_request_state.ipynb](03_multi_request_state.ipynb)

## Inside this part

- the data one active request needs: an ID, prompt tokens, generated tokens, KV cache, and finished state
- a `RequestState` object that keeps that data together
- prefill for one request and saving its first generated token
- decoding one or more tokens while extending that request's KV cache
- multiple requests with separate caches and generated tokens
- alternating decode steps between requests without mixing their state

The requests still run one at a time here. Batching and scheduling are separate problems that come next.

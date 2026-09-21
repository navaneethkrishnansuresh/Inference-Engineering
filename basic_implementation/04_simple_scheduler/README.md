# Part 4: Simple Scheduler

This part turns independent request state into a scheduler loop. It decides which request can run, gives it one unit of inference work, updates its state, and makes room for the next waiting request.

Open the notebook: [04_simple_scheduler.ipynb](04_simple_scheduler.ipynb)

## Inside this part

- waiting, running, and finished request sets
- FIFO admission and a maximum number of active requests
- prefill for a new request and one-token decode for an active request
- removing finished requests and admitting the next waiting request
- a scheduler loop that gives each selected request one inference step
- why an active request is not always selected in a given scheduler iteration
- estimating prefill and decode work as token cost
- a FIFO-biased, resource-aware, work-conserving scheduler with a token-work budget
- why batching, chunked prefill, and requests arriving during execution are still separate problems

The scheduler can keep multiple requests active, but it still runs model calls one request at a time. Part 5 will move toward batched execution.

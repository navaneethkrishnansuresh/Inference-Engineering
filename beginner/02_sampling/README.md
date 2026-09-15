# Chapter 2: Sampling

Chapter 1 built manual autoregressive inference with greedy `argmax` selection. Here, we replace that choice with a sampling pipeline built directly from logits. Nothing is hidden behind `generate()`.

Open the notebook: [02_sampling.ipynb](02_sampling.ipynb)

## What you'll learn

- next-token logits and their tensor shapes
- softmax, greedy `argmax`, and multinomial sampling
- temperature scaling, top-k filtering, and top-p / nucleus sampling
- boolean masks, sorting, cumulative probability, and renormalization
- how `sample_next_token()` combines the controls
- how sorted positions map back to vocabulary token IDs
- how to use the sampler in a naive autoregressive decode loop
- what each control contributes to a real inference system

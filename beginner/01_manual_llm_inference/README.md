# Chapter 1 — Manual LLM Inference From First Principles

This chapter starts with a small pretrained model and manually walks through the basic inference loop instead of hiding it behind `model.generate()`.

You will use a tokenizer and model from Hugging Face, then inspect prefill, decoding, logits, and the KV cache. A Google Colab runtime with a GPU is recommended; the notebook was written around an NVIDIA T4 and Qwen2.5-0.5B-Instruct.

Open the notebook: [01_manual_llm_inference.ipynb](01_manual_llm_inference.ipynb)

The aim is not to build a production server in one chapter. It is to make each piece of the inference path understandable before adding the systems concepts that build on it.

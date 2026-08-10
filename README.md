# Specialised Multi-Domain LLM Inference Pipeline

## Overview

This repository contains the implementation of a high-throughput Large Language Model (LLM) inference pipeline. Designed to handle specialized queries across multiple distinct domains—algebra, geography, history, and Chinese culture—the system is optimized for speed, precision, and efficient resource utilization.

## Key Achievements

* **High Throughput & Low Latency:** Successfully achieved a Time To First Token (TTFT) of under 150ms, averaging an exceptional 145.72 ms in rigorous 500-question benchmark testing.

* **Efficient Resource Usage:** Leveraged 4-bit quantization to drastically reduce memory footprint without sacrificing generative accuracy.

* **Advanced Contextual Retrieval:** Utilized a combination of Hybrid Retrieval mechanisms to fetch highly relevant background context prior to generation.

## Architecture & Pipeline Strategy

* **Core Model:** Powered by the `Qwen/Qwen3-1.7B` model, optimized via `BitsAndBytesConfig` utilizing 4-bit (nf4) double quantization.

* **Knowledge Base:** Integrated a robust local knowledge base of 400+ domain-specific entries bridging mathematics, world history, global geography, and Chinese language translations.

* **Hybrid Retrieval Engine:** Blends the `BM25Okapi` algorithm for sparse exact-keyword matching with the `all-MiniLM-L6-v2` dense encoder for semantic similarity mapping.

* **Dynamic Prompt Engineering:** Dynamically constructs instructions by injecting subject-specific few-shot examples alongside the retrieved context. This guarantees precise, strict-format outputs (e.g., extracting pure numeric answers for algebra questions).

* **Batched Generation:** Processes prompts in customizable batches (optimally configured for 5 to 16 questions at once) to maximize GPU parallelization and accelerate overall throughput.

## Performance Benchmarks

Tested against a comprehensive 500-question dataset across all four primary domains:

* **Total Processing Time:** 727.87 seconds
* **Average Latency Per Question:** 1455.73 ms
* **Average TTFT (Time To First Token):** 145.72 ms
* **Pipeline Status:** Evaluated natively as a "Good Model" due to optimal time-to-first-token responsiveness.

## Tech Stack

* **Model Architecture:** Qwen3-1.7B
* **Inference & Quantization:** ULLM, 4-bit Quantisation, `bitsandbytes`
* **Retrieval & Embeddings:** RAG, `sentence-transformers`, `rank_bm25`
* **Core Frameworks:** PyTorch, Hugging Face `transformers`, `accelerate`

## Author

* **Abhinav Karforma**
* **Email:** abhinavkarforma2@gmail.com
* **LinkedIn:** [linkedin.com/in/abhinavkarforma](https://www.linkedin.com/in/abhinavkarforma/)
* **GitHub:** [github.com/Abhinav0909](https://github.com/Abhinav0909)

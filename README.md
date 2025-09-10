# LLM Evaluation Project

This repository contains various projects for evaluating Large Language Models (LLMs) using different frameworks and methodologies. The main focus is on performance benchmarking and evaluation of different LLM inference engines.

## Project Structure

```
.
├── README.md                           # This file
├── compare_vllm_and_sglang/           # Performance comparison between vLLM and sglang
├── mlflow/                            # MLflow-based LLM evaluation examples
```

## Subprojects

### [compare_vllm_and_sglang](./compare_vllm_and_sglang)

This project compares the performance of different LLM inference engines using the Qwen3 model. Specifically, it benchmarks the model served directly versus served through vLLM.

For detailed information, please refer to the [compare_vllm_and_sglang README](./compare_vllm_and_sglang/README.md).

### [mlflow](./mlflow)

This project contains examples and experiments for evaluating Large Language Models (LLMs) using MLflow's generative AI evaluation capabilities. It demonstrates how to use MLflow to evaluate LLMs with different prompts and configurations.

For detailed information, please refer to the [mlflow README](./mlflow/README.md).

## Getting Started

1. Clone the repository
2. Navigate to the specific subproject you're interested in
3. Follow the setup instructions in each subproject's README
4. Run the provided notebooks to perform evaluations

## Requirements

- Python 3.11+
- Jupyter Notebook or JupyterLab
- Required Python packages (varies by subproject):
  - `llama-index`
  - `pandas`
  - `asyncio`
  - `mlflow`

## Usage

Each subproject contains Jupyter notebooks that demonstrate different evaluation techniques. Refer to the individual subproject READMEs for specific usage instructions.
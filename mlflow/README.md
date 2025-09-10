# MLflow LLM Evaluation Project

This repository contains examples and experiments for evaluating Large Language Models (LLMs) using MLflow's generative AI evaluation capabilities.

## Project Structure

```
.
├── README.md                           # This file
├── mlflow_example.ipynb               # Basic MLflow LLM evaluation example
└── test_prompts_comparison.ipynb      # Prompt comparison evaluation example
```

## Overview

This project demonstrates how to use MLflow to evaluate LLMs with different prompts and configurations. It includes examples of:

1. Setting up LLM models with LlamaIndex
2. Configuring MLflow tracking
3. Creating evaluation datasets
4. Defining custom scoring functions
5. Running evaluations and comparing results

## Key Components

### mlflow_example.ipynb

A basic example showing how to:
- Configure an LLM (Qwen3) using LlamaIndex
- Set up MLflow tracking URI and experiment
- Define a simple LLM inference function
- Create an evaluation dataset with medical-related questions
- Implement exact match scoring
- Run evaluation and view results

### test_prompts_comparison.ipynb

An advanced example demonstrating prompt engineering evaluation:
- Loading prompts from MLflow Prompt Registry
- Comparing different prompt versions
- Using the same evaluation framework for prompt comparison

## Setup

1. Install required dependencies:
```bash
pip install mlflow llama-index openai-like-llm
```

2. Ensure you have access to:
   - An LLM API endpoint (configured in the notebooks)
   - MLflow tracking server (configured in the notebooks)

## Usage

1. Update the LLM API endpoint and MLflow tracking URI in the notebooks according to your environment
2. Run the notebooks sequentially to understand the evaluation workflow
3. Check MLflow UI for detailed evaluation results and metrics

## Evaluation Dataset

The examples use a medical domain dataset with questions like:
- Diabetes risk assessment based on blood glucose levels
- Hypertension risk based on blood pressure readings
- Basic health-related questions with yes/no answers

## Features Demonstrated

- MLflow generative AI evaluation framework
- Custom scorer implementation
- LLM configuration with LlamaIndex
- Experiment tracking and result visualization
- Prompt registry usage for prompt engineering

## Results

Evaluation results include:
- Exact match accuracy metrics
- Per-sample evaluation details
- MLflow run comparison capabilities
- Detailed logs and model responses

## Requirements

- Python 3.11+
- MLflow 3.x
- LlamaIndex
- Access to LLM API endpoint

## Notes

- The notebooks are configured to work with Qwen3 model
- API endpoints and tracking URIs need to be updated based on your environment
- The evaluation uses a simple exact match scoring, which can be extended with more sophisticated metrics
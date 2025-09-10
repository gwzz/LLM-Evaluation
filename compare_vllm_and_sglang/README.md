# LLM Inference Engine Comparison

This project compares the performance of different Large Language Model (LLM) inference engines using the Qwen3 model. Specifically, it benchmarks the model served directly versus served through vLLM.

## Project Overview

This repository contains a benchmarking framework designed to compare the performance characteristics of different LLM inference serving solutions. The current implementation compares:
- Qwen3 served directly
- Qwen3 served through vLLM

The benchmark measures key performance metrics such as response time, token generation throughput, and success rate across various types of prompts.

## Environment Setup

1. **Python Version**: Python 3.11 is recommended
2. **Required Packages**:
   ```bash
   pip install llama-index
   pip install pandas
   pip install asyncio
   ```

3. **Dependencies**:
   - `llama-index`: For LLM interaction via OpenAI-compatible API
   - `pandas`: For data handling and result processing
   - `asyncio`: For asynchronous operations

## Project Structure

```
.
├── README.md                          # This documentation file
├── compare_vllm_and_sglang.ipynb      # Main benchmark notebook
└── model_benchmark_results.csv        # Benchmark results output
```

## Code Documentation

### ModelBenchmark Class

The main class that handles all benchmarking operations.

#### Constructor
```python
ModelBenchmark(model_configs: Dict[str, Dict[str, Any]])
```

Initializes the benchmark class with model configurations.

**Parameters:**
- `model_configs`: Dictionary containing model API configurations

#### Methods

##### `create_test_messages`
```python
create_test_messages(prompt: str) -> List[ChatMessage]
```
Creates a list of chat messages with system and user prompts.

##### `test_single_model`
```python
async test_single_model(model_name: str, prompt: str, num_runs: int = 5) -> Dict[str, Any]
```
Tests a single model's performance with a specific prompt for multiple runs.

**Parameters:**
- `model_name`: Name of the model to test
- `prompt`: Input prompt for testing
- `num_runs`: Number of test iterations (default: 5)

##### `compare_models`
```python
async compare_models(prompts: List[str], num_runs: int = 5) -> pd.DataFrame
```
Compares performance across multiple models using various prompts.

##### `generate_report`
```python
generate_report(results_df: pd.DataFrame) -> str
```
Generates a formatted performance comparison report.

### Model Configuration

The benchmark compares two model configurations:

1. **qwen3** (Direct serving):
   - API endpoint: `http://192.168.100.30:16001/v1`
   - API key: `empty`

2. **qwen3-vllm** (Served through vLLM):
   - API endpoint: `http://192.168.100.30:16002/v1`
   - API key: `empty`

### Test Prompts

Five different prompts are used to evaluate model performance:
1. Explanation of machine learning basics
2. Short story about AI
3. Programming skill improvement suggestions
4. Python quicksort algorithm implementation
5. Climate change impact on global economy

## Workflow

1. **Initialization**: Create `ModelBenchmark` instance with model configurations
2. **Testing**: For each prompt:
   - Run tests on all configured models concurrently
   - Execute each test 3 times (configurable)
   - Measure response time and token throughput for each run
3. **Analysis**: Collect and process results
4. **Reporting**: Generate performance comparison report
5. **Export**: Save detailed results to CSV file

## Outputs

### Console Output
Real-time progress updates during testing and a detailed performance report showing:
- Response time for each model and prompt
- Throughput (tokens/second) for each model and prompt
- Success rates
- Overall performance comparison

### File Output
[model_benchmark_results.csv](): Detailed CSV file containing:
- Performance metrics for each prompt and model combination
- Average response times
- Throughput values
- Success rates

## Performance Metrics Explained

1. **Response Time**: Time taken to generate a complete response (seconds)
2. **Throughput**: Tokens generated per second (tokens/s)
3. **Success Rate**: Percentage of successful requests (no errors)
4. **Token Count**: Approximate number of tokens in the response (calculated by word splitting)

## Results Interpretation

Based on the benchmark results, you can compare:
- Which serving solution provides faster response times
- Which solution offers better token generation throughput
- Consistency of performance across different types of prompts
- Resource efficiency of different serving solutions

## Usage

To run the benchmark:

1. Ensure the model APIs are running at the specified endpoints
2. Execute the Jupyter notebook:
   ```bash
   jupyter notebook compare_vllm_and_sglang.ipynb
   ```
3. View the results in the console and the generated CSV file

## Customization

You can customize the benchmark by modifying:
- Model configurations in `model_configs`
- Test prompts in `test_prompts`
- Number of test runs via the `num_runs` parameter
- Adding more models for comparison
- Adding different types of prompts

## Notes and Limitations

- Token counting is approximate (based on word splitting)
- Results may vary based on hardware and network conditions
- Tests run sequentially with a small delay between runs to avoid resource contention
- Timeout is set to 100 seconds per request
- "Thinking" mode is disabled in chat templates for consistent testing

This benchmark framework provides a standardized way to compare LLM performance across different serving engines, helping users make informed decisions about deployment options.
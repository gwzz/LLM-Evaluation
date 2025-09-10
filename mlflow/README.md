# MLflow LLM 评测示例

本项目演示如何结合 [MLflow](https://mlflow.org/) 与 LlamaIndex，对大语言模型（LLM）进行自动化评测。通过自定义 scorer、构造问答数据集，并调用 MLflow 的评测接口，实现模型输出的自动化验证和实验追踪。

## 主要内容

- **模型参数配置**：设置 LlamaIndex 支持的 LLM 参数，包括模型名称、API 地址、最大 token 数等。测试环境部署于**192.168.100.30:5000**
- **MLflow 配置**：导入 MLflow 并设置 tracking server 地址，便于实验追踪和结果管理。
- **推理函数定义**：实现 `llm_function`，用于将输入问题传递给大模型并返回回答。
- **评测 scorer 定义**：自定义 `exact_match` scorer，判断模型输出是否与期望答案完全一致。
- **评测数据集构造**：构造多条问答对，包含输入问题和标准答案。
- **自动化评测**：调用 `mlflow.genai.evaluate`，对模型进行批量评测并输出结果。

## 运行环境

- Python 3.10+
- [MLflow](https://mlflow.org/) >= 3.3
- 其他依赖见 notebook 头部

## 快速开始

1. **配置 LLM 参数**  
   在 notebook 中设置模型名称、API 地址、token 数等参数，并初始化 LLM。

2. **设置 MLflow Tracking URI**  
   指定 MLflow tracking server 地址，便于实验追踪。

3. **定义推理与评测函数**  
   - `llm_function`：将问题传递给大模型，返回回答。
   - `exact_match`：判断模型输出是否与标准答案一致。

4. **构造评测数据集**  
   按如下格式准备数据：
   ```python
   dataset = [
       {
           "inputs": {"question": "你的问题？"},
           "expectations": {"expected_response": "标准答案"}
       },
       ...
   ]
   ```

5. **执行评测**  
   调用如下代码进行评测并输出结果：
   ```python
   results = mlflow.genai.evaluate(
       data=dataset,
       predict_fn=llm_function,
       scorers=[exact_match],
   )
   print(results)
   ```

## 参考

- [MLflow 官方文档](https://mlflow.org/docs/latest/index.html)
- [LlamaIndex 官方文档](https://docs.llamaindex.ai/)

---

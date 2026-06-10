---
name: ai-model-evaluation
description: "Systematically evaluate the performance, safety, and reliability of AI models and LLM applications. Master metric selection, LLM-as-a-judge, RAG evaluation, and human-in-the-loop processes."
---

# AI Model Evaluation Skill

Develop rigorous evaluation frameworks to ensure AI models and LLM-based applications are accurate, safe, reliable, and efficient.

## When to Use

Use this skill when the user wants to:
- Compare different LLMs (e.g., GPT-4 vs. Claude 3.5) for a specific task.
- Measure the impact of prompt engineering changes on output quality.
- Evaluate the performance of a RAG system (faithfulness, relevance).
- Implement automated evaluation in a CI/CD pipeline for AI.
- Benchmark the latency and cost-effectiveness of various model configurations.
- Build a dataset for fine-tuning or few-shot prompting.

## Core Pillars

### 1. Metric Selection
- **Traditional NLP Metrics**: BLEU, ROUGE, METEOR (for translation/summarization, though limited for semantic nuance).
- **Semantic Similarity Metrics**: BERTScore, Cosine Similarity of embeddings (to capture meaning rather than exact words).
- **LLM-based Metrics (LLM-as-a-Judge)**: Using a high-reasoning model (e.g., GPT-4o) to grade outputs based on specific criteria like tone, helpfulness, or logic.
- **RAG-Specific Metrics**: Using frameworks like RAGAS to measure faithfulness, answer relevance, context precision, and context recall.
- **Operational Metrics**: Latency (TTFT - Time to First Token), throughput, and cost-per-request.

### 2. Dataset Curation & Management
- **Gold Standard Datasets**: Creating high-quality, human-verified "ground truth" answers for testing.
- **Edge Case Generation**: Developing test cases that specifically target known model weaknesses (e.g., math, logic, sensitive topics).
- **Synthetic Data Generation**: Using LLMs to create large-scale, diverse test datasets.
- **Data Splits**: Implementing proper training, validation, and testing splits to avoid overfitting.

### 3. Benchmarking & Regression Testing
- **Model Benchmarking**: Comparing models against standardized benchmarks (MMLU, GSM8K, etc.) and custom-built task-specific benchmarks.
- **Prompt Regression Testing**: Ensuring that updating a prompt to fix one issue doesn't break other behaviors.
- **A/B Testing**: Comparing two different model/prompt versions in production using real user interactions.

### 4. Human-in-the-Loop (HITL)
- **Expert Labeling**: Designing workflows for subject matter experts to grade model outputs.
- **Feedback Loops**: Collecting implicit (user likes/dislikes) and explicit (thumbs up/down) user feedback to improve models.
- **Error Categorization**: Manually reviewing failures to identify systematic patterns (e.g., "always fails on math" or "hallucinates names").

## Best Practices

- **Don't rely on a single metric**: A model might have high ROUGE scores but be factually incorrect. Use a combination of semantic and LLM-based metrics.
- **Use LLM-as-a-judge with caution**: Ensure the "judge" model is significantly more capable than the "student" model, and be aware of "LLM bias" (preference for longer answers, etc.).
- **Automate everything**: Integration of evaluation into your development loop (CI/CD) is crucial for maintaining quality.
- **Focus on "Vibe Check" vs. Rigor**: For early prototyping, a "vibe check" is fine, but for production, you need statistical significance.
- **Test for safety and bias**: Always include evaluation steps for toxic content, bias, and adherence to safety guidelines.
- **Consider the cost of evaluation**: Evaluating every request with GPT-4 is expensive. Use smaller models or sampling for continuous monitoring.

## Deliverables

- Comprehensive evaluation frameworks and protocols.
- Test datasets (Gold standard, edge cases, synthetic).
- Benchmark reports and comparative analyses.
- Automated evaluation pipelines (CI/CD).
- Feedback collection and analysis systems.

## Quality Checklist

- [ ] Multiple metrics are used to capture different aspects of performance.
- [ ] Ground truth/gold standard data is available and verified.
- [ ] Edge cases and failure modes are explicitly tested.
- [ ] LLM-as-a-judge is used with clearly defined rubric/criteria.
- [ ] Regression testing is implemented for prompt/model updates.
- [ ] Performance metrics (latency/cost) are tracked alongside accuracy.
- [ ] A mechanism for human feedback is integrated.

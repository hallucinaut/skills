---
name: ai-prompt-engineering
description: "Design and optimize high-performance prompts for LLMs. Master techniques like Chain-of-Thought, Few-Shot, and ReAct to elicit accurate, structured, and reliable responses."
---

# AI Prompt Engineering Skill

Master the art and science of interacting with Large Language Models (LLMs) to achieve precise, reliable, and production-ready outputs.

## When to Use

Use this skill when the user wants to:
- Design complex instructions for LLMs (GPT-4, Claude, Llama, etc.)
- Improve the accuracy and reliability of LLM responses
- Implement advanced prompting techniques like Chain-of-Thought or ReAct
- Structure LLM outputs (JSON, XML, Markdown) for programmatic use
- Optimize prompts for cost and latency
- Build robust prompt templates for application integration

## Core Pillars

### 1. Prompting Techniques
- **Zero-Shot Prompting**: Providing instructions without any examples.
- **Few-Shot Prompting**: Providing one or more examples to guide the model's behavior and output format.
- **Chain-of-Thought (CoT)**: Encouraging the model to show its reasoning step-by-step to improve complex reasoning tasks.
- **Tree-of-Thoughts (ToT)**: Guiding the model through multiple reasoning paths to find the best solution.
- **ReAct (Reason + Act)**: Combining reasoning with action (tool usage) to enable agents to interact with the world.
- **Self-Consistency**: Generating multiple reasoning paths and selecting the most frequent answer.

### 2. Structural Design
- **Role Prompting**: Assigning a specific persona or role to the LLM (e.g., "You are a senior DevOps engineer").
- **Delimiters**: Using clear separators (e.g., `###`, `"""`, `---`) to distinguish instructions from data.
- **Few-Shot Examples**: Designing high-quality, diverse examples that cover edge cases.
- **Input/Output Schemas**: Explicitly defining the expected format (e.g., "Respond only in valid JSON").

### 3. Context & Constraint Management
- **Context Window Optimization**: Managing the amount of information provided to stay within token limits.
- **Negative Constraints**: Clearly stating what the model *should not* do.
- **Few-Shot Diversity**: Ensuring examples cover the range of possible inputs.
- **Contextual Injection**: Dynamically inserting relevant data into templates.

### 4. Iterative Refinement & Evaluation
- **Prompt Versioning**: Tracking changes to prompts as they evolve.
- **A/B Testing**: Comparing different prompt versions against specific metrics.
- **Error Analysis**: Identifying where prompts fail (hallucinations, format errors, logic errors) and adjusting.
- **Systematic Testing**: Using test sets to ensure prompt changes don't cause regressions.

## Best Practices

- **Be explicit and direct**: Avoid ambiguity. Instead of "Write a short story," use "Write a 300-word story in the style of Ernest Hemingway."
- **Use structured formats**: When integrating with code, always demand structured output (JSON, YAML) and provide a schema.
- **Provide clear context**: The more the model knows about the goal, the better the result.
- **Iterate based on failure**: If a prompt fails, analyze *why* (was it lack of context? ambiguity? too much data?) and adjust.
- **Test for robustness**: Test your prompts with diverse and "adversarial" inputs to ensure they don't break easily.
- **Balance complexity and cost**: Long, complex prompts are more expensive and can increase latency. Find the "sweet spot."

## Deliverables

- High-performance prompt templates.
- Few-shot example sets.
- Prompt evaluation datasets.
- Documentation of prompt versions and testing results.
- System prompts for autonomous agents.

## Quality Checklist

- [ ] Prompt clearly defines the role and task.
- [ ] Output format is explicitly specified (e.g., JSON schema).
- [ ] Delimiters are used to separate instructions from data.
- [ ] Examples (if used) are accurate and representative.
- [ ] Negative constraints are clearly stated.
- [ ] Prompt is optimized for the target model (GPT, Claude, etc.).
- [ ] Prompt performance is verified against a test set.

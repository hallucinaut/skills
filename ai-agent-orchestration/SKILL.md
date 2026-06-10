---
name: ai-agent-orchestration
description: "Design and implement autonomous and semi-autonomous AI agents. Master reasoning loops (ReAct, Plan-and-Execute), tool/action integration, memory management, and multi-agent collaboration."
---

# AI Agent Orchestration Skill

Design and build intelligent agents capable of reasoning, using tools, and collaborating to solve complex, multi-step tasks.

## When to Use

Use this skill when the user wants to:
- Build autonomous agents (e.g., AutoGPT, BabyAGI style).
- Implement "Agentic Workflows" (Iterative reasoning, planning, and tool use).
- Create agents that can interact with external software/APIs (Function Calling).
- Implement memory systems for persistent AI personality and knowledge.
- Coordinate multiple specialized agents to solve a complex problem.

## Core Pillars

### 1. Agentic Reasoning Loops
- **ReAct (Reason + Act)**: The agent generates a thought, performs an action, observes the result, and repeats until the task is done.
- **Plan-and-Execute**: The agent first creates a detailed multi-step plan and then executes each step sequentially or in parallel.
- **Reflection / Self-Correction**: The agent reviews its own previous outputs and corrects errors before finalizing the response.
- **Tree-of-Thoughts (ToT)**: Exploring multiple branches of reasoning to find the optimal path to a solution.

### 2. Tool & Action Integration
- **Function Calling**: Designing well-defined JSON schemas so LLMs can request specific tool executions.
- **Sandboxed Execution**: Providing secure environments (e.g., Docker, WASM) for agents to run code safely.
- **API Interaction**: Enabling agents to read/write data across various SaaS platforms and local services.
- **Error Recovery**: Designing mechanisms for the agent to handle tool failures or incorrect outputs gracefully.

### 3. Memory Management
- **Short-Term Memory**: Managing conversation history (buffer memory, sliding window) to maintain immediate context.
- **Long-Term Memory**: Using vector databases (RAG) to allow agents to "remember" information across sessions.
- **Summarization Memory**: Using an LLM to summarize past interactions to manage token usage while preserving context.
- **Entity Memory**: Storing and retrieving facts about specific people, places, or objects mentioned in conversations.

### 4. Multi-Agent Orchestration
- **Hierarchical Orchestration**: A "Manager" agent assigns tasks to specialized "Worker" agents.
- **Sequential/Pipeline Patterns**: Agents working in a series, where the output of one becomes the input to the next.
- **Collaborative Patterns**: Agents communicating in a shared space to solve a common problem (e.g., debate, peer review).
- **Conflict Resolution**: Managing disagreements between multiple agents' proposed solutions.

## Best Practices

- **Start with Simple Loops**: Don't jump to multi-agent systems before mastering single-agent ReAct loops.
- **Define Strict Tool Schemas**: Provide clear, unambiguous descriptions for every tool function to prevent "hallucinated" tool calls.
- **Implement Robust Error Handling**: Assume tools will fail. Build agents that can observe an error and try a different approach.
- **Manage Token Budgeting**: Agents can enter infinite loops or consume massive amounts of tokens. Implement limits and "circuit breakers."
- **Prioritize Observability**: Use tracing (e.g., LangSmith, Phoenix) to visualize the agent's thought process and tool calls for debugging.
- **Enforce Safety and Sandboxing**: Never give an agent unbridled access to sensitive systems or your local terminal without strict isolation.

## Deliverables

- Autonomous or semi-autonomous agent architectures.
- Tool/Function definitions and integration layers.
- Memory management and persistence systems.
- Multi-agent communication protocols.
- Agent reasoning traces and evaluation logs.

## Quality Checklist

- [ ] Agent has a clearly defined role and goal.
- [ ] Tool schemas are precise and easy for the LLM to understand.
- [ ] The agent can handle tool failures or incorrect data.
- [ ] Memory is implemented (short-term/long-term) to support task complexity.
- [ ] Token usage and execution time are monitored and bounded.
- [ ] Agent reasoning is observable and traceable.
- [ ] Safety measures (sandboxing, limits) are in place.

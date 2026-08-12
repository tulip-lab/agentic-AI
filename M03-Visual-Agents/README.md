[![Course home](https://img.shields.io/badge/FLIP-Agentic_AI-informational)](../README.md)

# M03: Visual Agent Workflows

Visual orchestration makes prompts, models, memory, retrieval, and tools inspectable as a connected workflow. This module uses Flowise to develop system-level reasoning before the same ideas are implemented in code.

## Why This Module Matters

A visible graph helps teams discuss data flow, trust boundaries, and failure handling. It also exposes when an apparently simple chatbot depends on hidden state or excessive tool authority.

## Learning Outcomes

You should be able to:

- **Configure** a Flowise environment and store credentials appropriately.
- **Assemble** chat, memory, retrieval, and tool nodes into a coherent workflow.
- **Diagnose** a workflow by tracing inputs, state, model calls, and outputs.
- **Assess** API, embedding, and deployment readiness before sharing a flow.

## Core Concepts

Nodes and edges; chatflows; prompts and memory; document ingestion; retrieval; AgentFlow; tool schemas; testing panels; API and embed surfaces.

## Sessions and Practicals

| Session | Focus | Lab |
| --- | --- | --- |
| M03X | Flowise environment setup | [Tutorial](https://github.com/tulip-lab/agentic-AI-lab/tree/develop/M03-Visual-Agents/Flowise/M03X-Flowise-Environment-Setup.md) |
| M03A | Flowise interface and first chatflow | [Tutorial](https://github.com/tulip-lab/agentic-AI-lab/tree/develop/M03-Visual-Agents/Flowise/M03A-Flowise-Interface-First-Chatflow.md) |
| M03B | Chatbot prompting and memory | [Tutorial](https://github.com/tulip-lab/agentic-AI-lab/tree/develop/M03-Visual-Agents/Flowise/M03B-Flowise-Chatbot-Prompt-Memory.md) |
| M03C | Retrieval-augmented generation over public unit documents | [Tutorial](https://github.com/tulip-lab/agentic-AI-lab/tree/develop/M03-Visual-Agents/Flowise/M03C-Flowise-RAG-Public-Unit-Docs.md) |
| M03D | AgentFlow with safe tools | [Tutorial](https://github.com/tulip-lab/agentic-AI-lab/tree/develop/M03-Visual-Agents/Flowise/M03D-Flowise-AgentFlow-Safe-Tools.md) |
| M03E | Embedding, APIs, deployment, and readiness | [Tutorial](https://github.com/tulip-lab/agentic-AI-lab/tree/develop/M03-Visual-Agents/Flowise/M03E-Flowise-Embed-API-Deployment-Readiness.md) |

## Authoritative Resources

- [Flowise documentation](https://docs.flowiseai.com/) - use the current product concepts and configuration guidance.
- [Flowise Agentflows](https://docs.flowiseai.com/using-flowise/agentflows) - compare explicit agent orchestration patterns.
- [Flowise API reference](https://docs.flowiseai.com/api-reference) - inspect the boundary between a visual workflow and an application.

## Responsible Practice

Treat exported flows as potentially sensitive because they may reveal endpoints, prompts, or configuration. Remove secrets, constrain tools, and test missing-information and malicious-input cases before enabling an API or embed surface.

## Offering and Assignment Note

Practical evidence requirements are defined by the relevant offering, not by this overview.

[Previous: M02](../M02-AI-Modeling/README.md) | [Course home](../README.md) | [Next: M04](../M04-Agent-Programming/README.md)

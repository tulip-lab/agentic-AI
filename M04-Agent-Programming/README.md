[![Course home](https://img.shields.io/badge/FLIP-Agentic_AI-informational)](../README.md)

# M04: Agent Programming and Tool Use

Programmatic orchestration turns model suggestions into testable software behaviour. This module develops agents with explicit tools, schemas, storage, and action boundaries.

## Why This Module Matters

Once an agent can read or change external state, ordinary software engineering concerns become safety concerns. Clear interfaces and deterministic validation are essential.

## Learning Outcomes

You should be able to:

- **Implement** an agent loop with explicit model and tool boundaries.
- **Define** tool schemas that validate inputs and communicate failure.
- **Constrain** storage and action tools to an intended scope.
- **Test** a research-and-writing workflow for traceability and unsupported claims.

## Core Concepts

Messages and prompts; structured tool calls; schemas; dispatch; state; storage; action confirmation; traces; deterministic versus model-controlled logic.

## Sessions and Practicals

| Session | Focus | Lab |
| --- | --- | --- |
| M04A | LangChain fundamentals | [Notebook](https://github.com/tulip-lab/agentic-AI-lab/tree/develop/M04-Agent-Programming/Jupyter/M04A-LangChain-Fundamentals.ipynb) |
| M04B | Tool-using agents | [Notebook](https://github.com/tulip-lab/agentic-AI-lab/tree/develop/M04-Agent-Programming/Jupyter/M04B-LangChain-ToolAgents.ipynb) |
| M04C | Custom tools, local storage, and safe actions | [Notebook](https://github.com/tulip-lab/agentic-AI-lab/tree/develop/M04-Agent-Programming/Jupyter/M04C-CustomTools-Storage-Actions.ipynb) |
| M04D | Lead research and personalised writing agents | [Notebook](https://github.com/tulip-lab/agentic-AI-lab/tree/develop/M04-Agent-Programming/Jupyter/M04D-LeadResearch-WritingAgent.ipynb) |

## Authoritative Resources

- [LangChain agents](https://python.langchain.com/docs/concepts/agents/) - review the agent and tool abstraction used in the practicals.
- [LangGraph overview](https://langchain-ai.github.io/langgraph/) - compare graph-based control with an unconstrained loop.
- [OpenAI function calling](https://platform.openai.com/docs/guides/function-calling) - study structured model-to-application requests.

## Responsible Practice

Never equate a valid tool-call schema with permission to execute. Validate values, restrict file and network scope, make consequential actions reviewable, and represent tool errors explicitly so the model cannot reinterpret failure as success.

## Offering and Assignment Note

See the [offering index](../offerings/README.md) for adopted learning evidence.

[Previous: M03](../M03-Visual-Agents/README.md) | [Course home](../README.md) | [Next: M05](../M05-Knowledge-Agents/README.md)

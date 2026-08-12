[![Course home](https://img.shields.io/badge/FLIP-Agentic_AI-informational)](../README.md)

# M08: Agent Engineering and Productisation

The final module treats an agent as an engineered product rather than a demonstration. It brings together evaluation, codebase-aware development, interface protocols, workflow guards, and product decisions.

## Why This Module Matters

Production readiness depends on repeatable evaluation, observable boundaries, maintainable integration, and a credible user need. A polished demo without these properties is fragile.

## Learning Outcomes

You should be able to:

- **Design** an evaluation set and interpret model or agent results.
- **Use** a coding agent through audit, plan, patch, test, and human review stages.
- **Explain** how Model Context Protocol separates hosts, clients, servers, tools, and resources.
- **Implement** hooks or guards at consequential workflow boundaries.
- **Assess** product readiness using user value, technical risk, operation, and governance evidence.

## Core Concepts

Evaluation datasets and metrics; codebase context; reviewable patches; MCP architecture; tools and resources; hooks; policy gates; observability; product discovery; deployment readiness.

## Sessions and Practicals

| Session | Focus | Lab |
| --- | --- | --- |
| M08A | Hugging Face evaluation | [Notebook](https://github.com/tulip-lab/agentic-AI-lab/tree/develop/M08-Agent-Engineering/Jupyter/M08A-HuggingFace-Evaluation.ipynb) |
| M08B | Codex codebase understanding and development | [Handout](https://github.com/tulip-lab/agentic-AI-lab/tree/develop/M08-Agent-Engineering/Codex/M08B-Codex-Codebase-Understanding-and-Development.md) |
| M08C | Productised AI agents and go-to-market planning | [Handout](https://github.com/tulip-lab/agentic-AI-lab/tree/develop/M08-Agent-Engineering/Codex/M08C-Productised-AIAgents-GoToMarket.md) |
| M08D | Model Context Protocol fundamentals and tool/context servers | [Notebook](https://github.com/tulip-lab/agentic-AI-lab/tree/develop/M08-Agent-Engineering/Jupyter/M08D-MCP-Fundamentals-ToolContextServers.ipynb) |
| M08E | Agent hooks and workflow guards | [Notebook](https://github.com/tulip-lab/agentic-AI-lab/tree/develop/M08-Agent-Engineering/Jupyter/M08E-Agent-Hooks-WorkflowGuards.ipynb) |

## Authoritative Resources

- [Hugging Face Evaluate](https://huggingface.co/docs/evaluate/) - structure repeatable metric and comparison workflows.
- [Model Context Protocol specification](https://modelcontextprotocol.io/specification/) - use the protocol's authoritative concepts and lifecycle.
- [OpenAI Codex documentation](https://developers.openai.com/codex/) - review current code-agent workflows and controls.

## Responsible Practice

Define success and unacceptable failure before deployment. Keep generated changes reviewable, authenticate protocol connections, validate tool inputs and outputs, monitor drift, and ensure a human can stop or override consequential automation.

## Offering and Assignment Note

Capstone or product evidence is adopted only through an offering's approved assignment index.

[Previous: M07](../M07-Model-Adaptation/README.md) | [Course home](../README.md)

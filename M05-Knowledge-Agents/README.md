[![Course home](https://img.shields.io/badge/FLIP-Agentic_AI-informational)](../README.md)

# M05: Knowledge and Stateful Agents

Useful agents must often work with evidence beyond a model's parameters and preserve state across multiple steps. This module develops retrieval-augmented and stateful workflows.

## Why This Module Matters

Retrieval and memory can improve grounding, but they also introduce provenance, freshness, access-control, and state-consistency risks that prompt engineering alone cannot solve.

## Learning Outcomes

You should be able to:

- **Build** a basic retrieval pipeline from ingestion to cited response.
- **Evaluate** retrieval separately from answer generation.
- **Represent** workflow state and transitions explicitly.
- **Design** a copilot-style workflow that combines vision, context, and bounded action.

## Core Concepts

Chunking; embeddings and indexes; retrieval quality; provenance; citations; short- and long-lived state; graph transitions; checkpoints; multimodal context.

## Sessions and Practicals

| Session | Focus | Lab |
| --- | --- | --- |
| M05A | Basic retrieval-augmented generation | [Notebook](https://github.com/tulip-lab/agentic-AI-lab/tree/develop/M05-Knowledge-Agents/Jupyter/M05A-Basic-RAG-System.ipynb) |
| M05B | Domain assistants over course materials | [Notebook](https://github.com/tulip-lab/agentic-AI-lab/tree/develop/M05-Knowledge-Agents/Jupyter/M05B-RAG-CourseMaterials-Assistant.ipynb) |
| M05C | Stateful workflows with LangGraph | [Notebook](https://github.com/tulip-lab/agentic-AI-lab/tree/develop/M05-Knowledge-Agents/Jupyter/M05C-LangGraph-StatefulWorkflows.ipynb) |
| M05D | Copilot-style vision and task execution | [Notebook](https://github.com/tulip-lab/agentic-AI-lab/tree/develop/M05-Knowledge-Agents/Jupyter/M05D-Copilot-Vision-TaskExecution.ipynb) |

## Authoritative Resources

- [LangChain retrieval](https://python.langchain.com/docs/concepts/retrieval/) - map loaders, splitters, embeddings, stores, and retrievers.
- [LangGraph persistence](https://langchain-ai.github.io/langgraph/concepts/persistence/) - understand checkpoints and state over workflow steps.
- [NIST AI RMF Playbook](https://airc.nist.gov/AI_RMF_Knowledge_Base/Playbook) - connect system evidence and monitoring to risk management.

## Responsible Practice

Index only material you are permitted to process. Preserve source identity, separate retrieved evidence from generated interpretation, expire stale state, and ensure that one user's context cannot cross into another user's session.

## Offering and Assignment Note

Offering-specific datasets and submission evidence require separate approval and are not defined here.

[Previous: M04](../M04-Agent-Programming/README.md) | [Course home](../README.md) | [Next: M06](../M06-Multi-Agent-Safety/README.md)

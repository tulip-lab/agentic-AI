[![Course home](https://img.shields.io/badge/FLIP-Agentic_AI-informational)](../README.md)

# M01: Agentic AI Foundations

Agentic systems combine probabilistic models with software interfaces, tools, and control logic. This module establishes the vocabulary and safe working habits needed to distinguish a useful agent workflow from an unconstrained chatbot.

## Why This Module Matters

Every later module assumes that you can manage credentials, reason about model limitations, and explain how an API request becomes a bounded system action.

## Learning Outcomes

You should be able to:

- **Configure** a notebook environment without exposing credentials.
- **Explain** the relationship among generative models, agents, tools, and orchestration.
- **Trace** a function-calling request from model output to validated application code.
- **Test** API interactions for expected, missing-input, and failure cases.

## Core Concepts

Python and Colab workflows; environment variables; generative versus agentic behaviour; tokens and context; APIs; structured outputs; function calling; human approval.

## Sessions and Practicals

| Session | Focus | Lab |
| --- | --- | --- |
| M01A | Python, Colab, and API safety | [Notebook](https://github.com/tulip-lab/agentic-AI-lab/tree/develop/M01-Foundations/Jupyter/M01A-Python-Colab-API-Safety.ipynb) |
| M01B | Generative AI and agentic AI fundamentals | [Notebook](https://github.com/tulip-lab/agentic-AI-lab/tree/develop/M01-Foundations/Jupyter/M01B-GenAI-Fundamentals.ipynb) |
| M01C | LLMs, function calling, APIs, and agent ecosystems | [Notebook](https://github.com/tulip-lab/agentic-AI-lab/tree/develop/M01-Foundations/Jupyter/M01C-LLMs-FunctionCalling-APIs.ipynb) |

## Authoritative Resources

- [Python tutorial](https://docs.python.org/3/tutorial/) - review the language constructs used in notebooks and tool wrappers.
- [Google Colab overview](https://colab.research.google.com/notebooks/intro.ipynb) - understand the hosted runtime and notebook workflow.
- [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) - frame reliability, transparency, and risk as system responsibilities.

## Responsible Practice

An API key is a capability, not course content. Keep it outside notebooks and logs, give tools the least privilege needed, and require application code to validate model-proposed arguments before execution.

## Offering and Assignment Note

Offerings select from this common core. Any adopted assignment is linked from its [offering page](../offerings/README.md) and remains canonical in Lab.

[Course home](../README.md) | [Next: M02](../M02-AI-Modeling/README.md)

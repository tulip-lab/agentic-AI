[![Course home](https://img.shields.io/badge/FLIP-Agentic_AI-informational)](../README.md)

# M01: Introduction to Agentic AI

## Overview

**Course introduction.** *FLIP: Agentic AI in Practice* develops the conceptual judgement and practical skills needed to understand, build, evaluate, and govern useful agentic AI systems. M01 establishes the shared language for the course before later modules examine AI models, visual workflows, agent programming, knowledge and state, multi-agent safety, model adaptation, and production-oriented agent engineering.

**Prerequisites.** The course is designed for senior undergraduate and postgraduate learners from computing and related disciplines, but it does not require a specific academic major. Learners should be able to read basic Python, work with files and web applications, and interpret introductory data-analysis or machine-learning concepts. Prior experience with generative AI or large language models is useful but not required, and advanced deep-learning mathematics is not assumed.

**Professor Gang Li and TULIP Lab.** The course is led by Professor Gang Li from Deakin University's School of Information Technology. It is developed through [TULIP Lab](https://www.tulip.academy), the Team for Universal Learning and Intelligent Processing, whose work spans artificial intelligence, privacy and security, business intelligence, and applied AI. The course connects these research and teaching perspectives with reproducible public learning resources.

**The AI era.** Predictive AI systems learn patterns for tasks such as classification, regression, recommendation, or forecasting. Generative AI extends this landscape by producing new text, images, audio, code, and other content. Large language models make natural-language interaction and flexible content generation widely accessible, but fluent output is still probabilistic: it can vary, omit evidence, or confidently present unsupported claims.

The progression from **generative AI** to **LLM applications** and then to **agentic AI** is primarily a change in system design. A model may generate or propose an action; an application can add context, memory, tools, state, control flow, validation, and human approval. These surrounding components determine what the system can observe, decide, and change.

**Agentic AI.** An agentic system works towards a goal through a loop of observations, decisions, actions, and feedback. A useful architecture separates the model from the state it reads, the tools it may request, the orchestration that controls execution, and the people or policies that retain authority. Not every task needs an agent: deterministic code or a fixed workflow remains preferable when it solves the problem more clearly and reliably.

**Recommended tools and platforms.** The course uses [GitHub](https://github.com/) for versioned learning resources, [Google Colab](https://developers.google.com/colab) and Jupyter notebooks for executable experiments, and model-provider interfaces for studying prompts, structured outputs, and tool calling. Later modules introduce [Flowise](https://flowiseai.com/) for visual workflows, Python agent frameworks for programmatic systems, Codex for repository-aware development, and local or open-model tooling where privacy, portability, or deployment trade-offs matter. A platform is selected for its learning purpose; it does not replace validation, safe credential handling, or critical evaluation.

**Assignments and assessment.** Assessment requirements are offering-specific. Approved task descriptions, weights, dates, submission rules, and grading requirements must come from the relevant entry in the [course offering index](../offerings/README.md). This common-core page does not create or override assessment policy.

**Summary and transition.** M01 frames agentic AI as a controlled system built around probabilistic models rather than as a model acting alone. The next module moves beneath this system-level view to examine the AI models and representations that provide prediction, learned features, embeddings, and similarity.

#### Learning Outcomes

After completing M01, learners should be able to:

- **explain** how generative AI, large language models, and agentic AI relate;
- **identify** the model, state, tools, orchestration, and oversight elements of an agentic system;
- **select** an appropriate tool or platform for a bounded learning task;
- **describe** the expected background and responsible-practice boundaries for the unit; and
- **locate** authoritative practical and offering-specific assessment information.

## Practicals

| Session | Practical focus | Public Lab notebook |
| --- | --- | --- |
| M01A | Safe configuration, structured state, tools, and tests | [Python, Colab, and API Safety](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M01-Foundations/Jupyter/M01A-Python-Colab-API-Safety.ipynb) |
| M01B | Generative-AI concepts and the transition to agentic workflows | [Generative AI Fundamentals](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M01-Foundations/Jupyter/M01B-GenAI-Fundamentals.ipynb) |
| M01C | Mock function calling, validation, routing, and failure behaviour | [LLMs, Function Calling, and APIs](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M01-Foundations/Jupyter/M01C-LLMs-FunctionCalling-APIs.ipynb) |

## Further Reading

- [The Python Tutorial](https://docs.python.org/3/tutorial/) - review the functions, dictionaries, and exceptions used in explicit workflow state and tool interfaces.
- [Google Colab](https://developers.google.com/colab) - understand the hosted notebook runtime used by the practicals.
- [Anthropic: Building Effective Agents](https://www.anthropic.com/research/building-effective-agents) - compare workflows and agents and examine common system patterns.
- [OpenAI function-calling guide](https://developers.openai.com/api/docs/guides/function-calling) - examine one provider's current tool-description and tool-call pattern.
- [Gemini function-calling guide](https://ai.google.dev/gemini-api/docs/function-calling) - compare the same conceptual boundary in another provider API.
- [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) - connect system controls and human oversight to a broader risk-management vocabulary.

## Responsible Practice

Never place real credentials, personal data, private course material, or unreviewed model output in public notebooks, prompts, screenshots, or repositories. Treat model output as untrusted input at every software boundary, give tools the least capability needed, validate before execution, and retain human review where an incorrect action could affect people, systems, or data.

[Course home](../README.md) | [Next: M02 - AI Models and Representations](../M02-AI-Modeling/README.md)

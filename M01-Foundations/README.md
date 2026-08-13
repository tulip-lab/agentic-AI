[![Course home](https://img.shields.io/badge/FLIP-Agentic_AI-informational)](../README.md)

# M01: Agentic AI Foundations

## Module Overview

Agentic AI systems combine probabilistic models with software interfaces, tools, state, and control logic.
This module develops the vocabulary and safe engineering habits needed to understand that combination before working with larger frameworks.

The organising question is: **how does model output become controlled system behaviour?**
M01 answers it in three stages: establish a safe runtime, understand what generative models can and cannot do, then trace a model-proposed tool call through validation and execution.

## Learning Outcomes

After completing this module, you should be able to:

- **Configure** a notebook environment without exposing credentials.
- **Distinguish** a generative model, chatbot, workflow, and tool-using agent.
- **Explain** how tokens, context, prompts, state, tools, and orchestration contribute to system behaviour.
- **Trace** an API request from user input to a validated tool result and final response.
- **Design** normal, edge, and failure tests for a bounded tool interaction.
- **Identify** where application controls or human approval are needed before consequential actions.

## M01A: Python, Colab, and API Safety

M01A establishes the runtime foundation for later agent work.
A notebook is an interactive program running inside a temporary process: variables and credentials live in that runtime, cells can be executed out of order, and a restart can remove state that has not been saved deliberately.
The essential Python ideas are correspondingly small but important—functions define explicit behaviour, dictionaries make workflow state inspectable, and exceptions or structured error values make failure visible.

API keys are capabilities rather than ordinary course content.
They belong in an environment variable or an approved secret store, never in a committed cell, screenshot, output, or execution trace.
The same boundary applies to tools: accept narrow structured inputs, validate types and domain constraints, avoid unrestricted execution such as `eval`, and return a result that later workflow steps can inspect.

A tool is not reliable because one example succeeds.
M01A therefore introduces normal cases, boundary values, and expected failures as three distinct forms of evidence.
These habits prepare the workflow for model-generated input in M01C.

## M01B: Generative AI and Agentic AI Fundamentals

A large language model generates output from tokens in a supplied context.
Instructions, conversation history, retrieved evidence, and tool results can all shape that context, but they do not turn probabilistic generation into guaranteed truth.
Outputs can vary, omit relevant details, reproduce an unsupported claim, or rely on knowledge that is no longer current.

The distinction between a chatbot and an agentic workflow is therefore architectural rather than rhetorical.
A chatbot primarily exchanges messages; a bounded agentic workflow adds explicit state, approved tools, control flow, validation, and oversight.
Increasing autonomy also increases the need to define what the system may observe, decide, and change.

M01B provides a reusable mental model for the rest of the course: the model proposes or generates, while application code controls permissions, state transitions, evidence, and execution.
Not every task needs an agent; a deterministic function or fixed workflow is preferable when it solves the problem more clearly and reliably.

## M01C: LLMs, Function Calling, and APIs

An LLM API exchange usually combines a model identifier, role-based messages, generation settings, optional tool descriptions, and a response.
That response may be natural language, structured data, or a proposed function call.
Structured output can make a response easier to parse, but syntax alone does not establish that its content is valid, authorised, or safe to execute.

A model-proposed tool call is therefore a request to the application, not an execution command.
The runtime should check that the tool is allowlisted, validate the argument schema, enforce domain constraints and permissions, and reject unsupported requests before any function runs.
Read-only lookup, reversible changes, and consequential actions should not share the same approval policy.

Human approval belongs immediately before a consequential action, with enough information to understand the proposed target and effect.
After execution, the system should retain a structured result or error so that the final response is based on what actually happened rather than on what the model expected to happen.

## Bringing the Module Together

A bounded agentic interaction can be traced as one controlled sequence:

```text
user request
  → model receives instructions and context
  → model proposes a response or tool call
  → application checks tool, arguments, permissions, and approval
  → approved tool executes
  → application records and inspects the result
  → model produces a final response grounded in that result
```

The model participates in this sequence, but it does not own the trust boundary.
Reliable agentic systems place controls around probabilistic output and preserve enough state to explain both success and failure.

## Practicals

| Session | Practical focus | Public Lab notebook |
| --- | --- | --- |
| M01A | Safe configuration, structured state, tools, and tests | [Python, Colab, and API Safety](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M01-Foundations/Jupyter/M01A-Python-Colab-API-Safety.ipynb) |
| M01B | Generative-AI concepts and the transition to agentic workflows | [Generative AI Fundamentals](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M01-Foundations/Jupyter/M01B-GenAI-Fundamentals.ipynb) |
| M01C | Mock function calling, validation, routing, and failure behaviour | [LLMs, Function Calling, and APIs](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M01-Foundations/Jupyter/M01C-LLMs-FunctionCalling-APIs.ipynb) |

## Further Reading

- [The Python Tutorial](https://docs.python.org/3/tutorial/) — review functions, dictionaries, and exceptions used in explicit workflow state and tool interfaces.
- [Google Colab](https://developers.google.com/colab) — understand the hosted notebook runtime used by the practicals.
- [OWASP Secrets Management Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Secrets_Management_Cheat_Sheet.html) — place credential handling within a broader secret lifecycle.
- [OpenAI function-calling guide](https://developers.openai.com/api/docs/guides/function-calling) — examine one provider's current tool-description and tool-call pattern.
- [Gemini function-calling guide](https://ai.google.dev/gemini-api/docs/function-calling) — compare the same conceptual boundary in another provider API.
- [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) — connect system controls and oversight to a broader risk-management vocabulary.

## Responsible Practice

Never place real credentials, personal data, private course material, or unreviewed consequential actions inside a public notebook.
Treat model output as untrusted input at every software boundary, give tools the least capability needed, and retain human review where an incorrect action could affect people, systems, or data.

[Course home](../README.md) | [Next: M02](../M02-AI-Modeling/README.md)

[![Course home](https://img.shields.io/badge/FLIP-Agentic_AI-informational)](../README.md)

# M04: Agent Programming and Tool Use

## Module Overview

Visual workflows make responsibilities visible; programmatic workflows make those responsibilities explicit, testable interfaces. This module develops the execution path **prompt -> model -> parser -> dispatcher -> tool -> trace**. The model may propose text or a structured action, but application code decides whether that proposal is valid, permitted, and safe to execute.

The sessions move from basic LangChain composition to tool-using loops, custom storage and action tools, and an evidence-aware research and writing workflow. The central engineering distinction is between probabilistic choice and deterministic control. A model can help select an action, while schemas, allowlists, state boundaries, approval rules, and tests remain ordinary software responsibilities.

## Connection to the Course

M03 exposed nodes, state, retrieval, tools, and external interfaces on a canvas. M04 implements the same roles as code and data contracts. This makes hidden defaults easier to replace with named inputs, explicit failure values, bounded side effects, and traces that can be inspected independently of generated prose.

The module also creates the bridge to M05. A research tool can fetch evidence and a storage tool can preserve local state, but reliable knowledge work needs a designed ingestion and retrieval pipeline plus durable workflow state. Those capabilities become the next module's main subject.

## Learning Outcomes

By the end of this module, you should be able to:

- **Compose** prompts, messages, models, parsers, and deterministic steps into a testable program.
- **Define** a tool contract with explicit schema, errors, permissions, and termination behaviour.
- **Implement** bounded storage and action tools using preview, confirmation, recovery, and audit evidence.
- **Trace** an agent loop from model request through dispatch and tool result.
- **Evaluate** a research-and-writing workflow for provenance, claim support, privacy, and unsupported generation.

## Module Map

| Session | Conceptual role | Added responsibility |
| --- | --- | --- |
| M04A | LangChain fundamentals | Explicit composition and model boundaries |
| M04B | Tool-using agents | Schema, selection, dispatch, errors, and stopping |
| M04C | Custom tools and actions | Scoped state mutation, confirmation, and recovery |
| M04D | Research and personalised writing | Evidence separation, user data, and claim traceability |

## M04A: LangChain Fundamentals

### Chapter Overview

A programmatic language-model workflow has distinct layers. Messages express role and content; a prompt template constructs those messages from controlled inputs; a model interface sends the request; and a parser converts the response into an application value. Naming these layers allows each one to be replaced or tested without treating the model call as the entire system.

### Key Ideas

Deterministic composition follows a route chosen by the developer: format input, call a model, validate output, then continue. Agent choice introduces a model-influenced branch, such as selecting among tools. The two patterns should not be confused. Fixed logic is preferable when rules are known, while model choice may help when inputs are variable and the cost of a wrong route is bounded.

A mock or fixed-response model supports repeatable tests of composition, parsing, and failure handling without network variability. A hosted model adds authentication, rate limits, latency, cost, version change, and nondeterministic output. Clear interfaces let the same surrounding workflow be tested under both conditions.

### From Concepts to Practice

The practical constructs a minimal LangChain path and observes the value at each boundary. Compare raw output with parsed output, deliberately provide invalid input, and identify which errors belong to prompt construction, provider communication, parsing, or application logic. This establishes a baseline before tools introduce effects.

### Suggested Readings

- Karpas, E., et al. (2022). [MRKL systems: A modular, neuro-symbolic architecture that combines large language models, external knowledge sources and discrete reasoning](https://arxiv.org/abs/2205.00445). Used to frame modular routing around a language model.
- LangChain. [Agents](https://docs.langchain.com/oss/python/langchain/agents). Official documentation used to map models, messages, state, middleware, and tools.

## M04B: LangChain Tool-Using Agents

### Chapter Overview

A tool is an application capability described to the model through a name, purpose, and input schema. The model can request a call, but it does not execute the underlying function. Application code parses the request, validates it, dispatches to a registered tool, captures the result, and decides whether another model turn is allowed.

### Key Ideas

Good schemas narrow ambiguity with meaningful field names, types, required values, and constrained options. Runtime checks must also validate values, caller authority, resource scope, and current state. Unknown tools, malformed arguments, timeouts, and downstream failures should become explicit error results rather than disappearing into a generic message that a model may reinterpret as success.

An agent loop needs termination conditions. A final response, iteration cap, cost budget, elapsed-time limit, repeated-call detector, or human escalation can stop unproductive behaviour. The trace should link the model request, proposed arguments, validation decision, tool result, and final output. This evidence supports debugging without assuming that a generated explanation accurately describes execution.

### From Concepts to Practice

The tool-agent practical exercises correct calls, requests that require no tool, malformed arguments, unavailable tools, and repeated actions. Compare model-selected routing with a deterministic dispatcher where appropriate. The objective is controlled delegation: useful flexibility inside an application-defined envelope.

### Suggested Readings

- Yao, S., et al. (2023). [ReAct: Synergizing reasoning and acting in language models](https://arxiv.org/abs/2210.03629). *ICLR 2023*. Used to examine observable reasoning-action loops.
- Schick, T., et al. (2023). [Toolformer: Language models can teach themselves to use tools](https://arxiv.org/abs/2302.04761). *NeurIPS 2023*. Used to separate tool-selection capability from execution authority.
- OpenAI. [Function calling](https://platform.openai.com/docs/guides/function-calling). Official guidance used to distinguish structured requests from application-side execution.

## M04C: Custom Tools, Local Storage, and Action Execution

### Chapter Overview

Custom tools connect an agent to domain operations. Reading a bounded local record is different from modifying it; drafting an action is different from performing it. Tool design should therefore encode effect level, accessible resources, and the conditions under which a state change may occur.

### Key Ideas

Storage must be scoped to an intended directory, namespace, user, or session. Paths and identifiers require canonical validation so model-generated values cannot escape that scope. State mutation should be idempotent where possible: retrying the same operation should not create duplicate or conflicting effects. A preview shows the proposed change; confirmation authorises a defined version of that change; recovery handles partial failure or supports reversal.

Audit evidence records what was requested, validated, approved, attempted, and observed. It should omit secrets and unnecessary personal data while retaining enough context to explain a material state transition. A success value should reflect verified postconditions, not merely the absence of an exception.

### From Concepts to Practice

The practical introduces bounded local storage and controlled action execution. Test invalid paths, duplicate calls, stale previews, denied confirmation, and interrupted operations. These cases expose whether the tool contract remains reliable when execution does not follow the ideal path.

### Suggested Readings

- LangChain. [Tools](https://docs.langchain.com/oss/python/langchain/tools). Official reference for tool schemas, runtime context, and returned values.
- LangGraph. [Overview](https://docs.langchain.com/oss/python/langgraph/overview). Official reference used to compare explicit graph control with a free-running loop.

## M04D: Lead Research and Personalised Writing Agent

### Chapter Overview

A research-and-writing workflow combines public evidence with user-provided context to produce tailored prose. Four information classes must remain distinguishable: source material, claims supported by that material, private or user-specific data, and generated wording. Blending them too early makes provenance and privacy difficult to inspect.

### Key Ideas

Research quality depends on source scope, freshness, authority, and faithful extraction. A citation supports only the claim warranted by its content. Personalisation should use the minimum necessary user data and should not convert inference into fact. Draft generation needs an abstention or qualification path when evidence is weak, conflicting, or absent.

The workflow trace should associate material claims with inspected evidence and record transformations without exposing sensitive inputs. Review should ask both whether the prose is useful and whether each factual claim is supported. Fluency, personal relevance, and evidential reliability are separate qualities.

### From Concepts to Practice

The practical composes research and drafting tools under a bounded workflow. Inspect retrieved material before generation, identify unsupported additions, and test how the agent behaves when sources do not answer the request. This reveals why persistent corpora, retrieval evaluation, and explicit state become necessary in M05.

### Suggested Readings

- Lewis, P., et al. (2020). [Retrieval-augmented generation for knowledge-intensive NLP tasks](https://arxiv.org/abs/2005.11401). *Advances in Neural Information Processing Systems 33*. Used to distinguish retrieved evidence from generated output.

## Bringing the Module Together

The execution chain begins with constructed messages and ends with observable evidence. The model proposes; the parser creates a typed value; the dispatcher applies deterministic policy; the tool operates within a scope; and the trace records outcomes. Storage and writing examples show that the same boundary matters for both state changes and information claims. Reliability comes from the whole chain, not from a persuasive final response.

## Practicals

The public Lab notebooks are the canonical executable companions to these conceptual chapters.

| Session | Public practical | Evidence focus |
| --- | --- | --- |
| M04A | [LangChain fundamentals notebook](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M04-Agent-Programming/Jupyter/M04A-LangChain-Fundamentals.ipynb) | Component boundaries, parsing, and controlled failures |
| M04B | [Tool-using agents notebook](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M04-Agent-Programming/Jupyter/M04B-LangChain-ToolAgents.ipynb) | Selection, dispatch, errors, trace, and termination |
| M04C | [Custom tools, storage, and actions notebook](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M04-Agent-Programming/Jupyter/M04C-CustomTools-Storage-Actions.ipynb) | Scope, idempotence, confirmation, and recovery |
| M04D | [Lead research and writing agent notebook](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M04-Agent-Programming/Jupyter/M04D-LeadResearch-WritingAgent.ipynb) | Evidence, user context, claim support, and abstention |

## Further Reference Resources

- LangChain. [Python documentation](https://docs.langchain.com/oss/python/langchain/overview). Official entry point for current component and agent guidance.
- The LangGraph and provider references within the sessions should be checked against installed versions because interfaces and defaults evolve.

## Responsible Practice

Treat all model-produced tool names, arguments, paths, and explanations as untrusted proposals. Validate with deterministic code, apply least privilege, set budgets and stopping conditions, and require review before consequential or irreversible effects. Logs should support accountability without becoming a second store of credentials or sensitive content.

For research and personalisation, respect source terms, data purpose, retention, and user expectations. Preserve provenance, label uncertainty, and avoid presenting generated inference as a verified fact. A valid schema, successful call, or attached citation is not sufficient evidence on its own.

## Preparing for the Next Module

M05 expands the evidence and state responsibilities introduced here. Instead of one research call or local record, the workflow will ingest a governed corpus, evaluate retrieval separately from generation, persist graph state across steps, and combine uncertain visual context with controlled action.

[Previous: M03](../M03-Context-Orchestration/README.md) | [Course home](../README.md) | [Next: M05](../M05-Knowledge-Agents/README.md)

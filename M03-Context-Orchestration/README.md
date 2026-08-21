[![Course home](https://img.shields.io/badge/FLIP-Agentic_AI-informational)](../README.md)

# M03: Context Engineering and Agent Orchestration

## Module Overview

Context Engineering determines what information each model call can see. Agent orchestration determines which component runs next and how its result changes future context. This module uses Flowise to make both mechanisms inspectable as **nodes -> data flow -> state -> tools -> external interface**. The canvas reveals where prompts, models, memory, retrieval, and actions meet, but the visible graph is still executable software: its credentials, inputs, tools, and deployment surface require deliberate controls.

The module moves from environment setup and a first chatflow to stateful conversation, retrieval-augmented generation (RAG), safe tool use, and external integration. Each session adds one responsibility while preserving the ability to trace what entered the flow, what changed, what external capability was invoked, and what evidence supports the result.

## Connection to the Course

M02 examined models and representations separately. M03 composes them: an embedding model transforms documents and queries, a vector store supports retrieval, a chat model generates a response, and workflow state carries selected information between nodes. Failures can now occur at connections as well as within a model.

This inspectable stage also prepares for M04. Flowise exposes responsibilities that will later become software interfaces: message construction, parsing, dispatch, storage, validation, and tracing. Understanding them on a canvas makes the move to code a change of implementation medium rather than a new conceptual system.

## Learning Outcomes

By the end of this module, you should be able to:

- **Engineer** the context assembled for a model call from instructions, conversation state, retrieved evidence, and tool observations.
- **Compare** fixed, conditional, and model-influenced orchestration, tracing how each step changes state and subsequent context.
- **Configure** and inspect these mechanisms in Flowise using explicit nodes, edges, inputs, outputs, and runtime traces.
- **Constrain** an Agentflow with bounded tools, validated arguments, and explicit rejection behaviour.
- **Assess** an embed or API surface for authentication, exposure, observability, and deployment readiness.

## Module Map

| Session | Conceptual role | Added system responsibility |
| --- | --- | --- |
| M03X | Environment and deployment choices | Runtime, secrets, persistence, and exposure |
| M03A | Visible model call | Nodes, edges, execution, and runtime trace |
| M03B | Context Engineering | Selection, structure, lifecycle, quality, and memory scope |
| M03C | Context acquisition | Retrieval mode, grounding, provenance, and abstention |
| M03D | Dynamic orchestration | Routing, tool authority, state transition, stop, and recovery |
| M03E | Boundaries and evidence | Isolation, evaluation, interfaces, and readiness |

## M03X: Flowise Environment Setup

### Chapter Overview

A workflow begins before any node is placed. Local installation, containers, or hosted deployment create different boundaries for storage, network access, upgrades, and operational ownership. Environment setup therefore belongs to system design rather than being treated as an incidental prerequisite.

### Key Ideas

Configuration should distinguish the runtime from the flow definition and from secrets. Credentials must not be embedded in exported flows, screenshots, or source history. Persistence determines whether flows and state survive restarts; network binding determines who can reach the service. Version recording and a basic health check make later results reproducible.

### From Concepts to Practice

The setup tutorial establishes a known runtime and identifies its components before agent behaviour is tested. Document the chosen deployment boundary, where configuration is stored, and which interfaces are reachable. This creates the operational map used by every later session.

### Suggested Readings

- FlowiseAI. [Deployment](https://docs.flowiseai.com/configuration/deployment). Official guidance used to compare supported runtime and hosting options.

## M03A: Interface and First Chatflow

### Chapter Overview

A chatflow is a directed composition of configured components. Nodes perform roles such as constructing a prompt, calling a model, or formatting output; edges carry compatible data between them. The canvas is valuable because the path from user input to model response can be inspected rather than hidden inside one call.

### Key Ideas

Visual proximity does not define execution: typed connections, node settings, and runtime inputs do. A model node may still depend on implicit defaults, credentials, and provider behaviour. The first debugging question should be structural: what value entered each node, what configuration affected it, and what value left it?

### From Concepts to Practice

The first-chatflow tutorial builds the smallest useful path and tests it with controlled inputs. Change one configuration at a time, preserve a known baseline, and compare outputs. This provides a traceable foundation before memory or tools introduce additional state and branches.

## M03B: Chatbot Prompting and Memory

### Chapter Overview

System instructions define intended behaviour, while conversation messages provide immediate context. Memory components decide which prior information is made available again. These mechanisms influence the next model call, but they should not be conflated: context is what the model currently receives; memory is a system process for retaining and selecting information across turns.

### Key Ideas

Memory scope matters. A session identifier can separate conversations, a window can limit retained messages, and a summary can compress older context while losing detail. Durable user memory introduces stronger requirements for consent, deletion, freshness, and isolation. State-dependent tests should compare a fresh session, a continued session, and an incorrect or missing identifier.

### From Concepts to Practice

The practical adds prompting and memory to the baseline chatflow, then observes how prior messages affect responses. Inspect what is actually supplied to the model and test whether information crosses a boundary it should not cross. Useful continuity must not become uncontrolled retention.

## M03C: RAG over Public Unit Documents

### Chapter Overview

RAG introduces an external evidence path. Documents are loaded, divided into chunks, embedded, stored, and retrieved for a query; selected passages then condition generation. Retrieval and generation are separate operations, so a polished answer does not prove that the correct evidence was found.

### Key Ideas

Corpus boundaries, chunk size, overlap, metadata, encoder choice, retrieval depth, and ranking all shape the evidence reaching the model. Grounding means the response is supported by retrieved material, not merely that passages were present in the prompt. Provenance should remain visible so a user can inspect sources, and the system should abstain or qualify an answer when evidence is missing or conflicting.

### From Concepts to Practice

The visual RAG tutorial uses public course documents to trace ingestion through response. Test questions with direct support, ambiguous support, and no support. Examine retrieved chunks before judging generated prose; this isolates whether an error belongs to ingestion, representation, retrieval, prompt construction, or generation.

### Suggested Readings

- Lewis, P., et al. (2020). [Retrieval-augmented generation for knowledge-intensive NLP tasks](https://arxiv.org/abs/2005.11401). *Advances in Neural Information Processing Systems 33*. Used to establish the distinction between parametric generation and retrieved external evidence.

## M03D: Agentflow with Safe Tools

### Chapter Overview

An Agentflow allows a model-influenced step to select an action or route rather than following only a fixed chain. A tool converts that selection into an external capability. This is the point where plausible text may become a database query, calculation, network request, or state change, so the application must retain authority over execution.

### Key Ideas

A tool schema communicates available arguments, but schema validity is not permission. Safe execution also requires an allowlist, value validation, bounded scope, time and iteration limits, explicit error representation, and rejection for unsupported requests. Read-only tools and reversible actions are appropriate starting points. Consequential actions may require preview and human approval.

### From Concepts to Practice

The Agentflow tutorial connects a small set of safe tools and observes selection, arguments, results, and stopping behaviour. Test expected requests, malformed values, attempts to exceed tool scope, and tool failure. The trace should show why an action was allowed or rejected without relying on the model to police itself.

### Suggested Readings

- Yao, S., et al. (2023). [ReAct: Synergizing reasoning and acting in language models](https://arxiv.org/abs/2210.03629). *ICLR 2023*. Used to study interleaved reasoning and action as an observable loop.
- Schick, T., et al. (2023). [Toolformer: Language models can teach themselves to use tools](https://arxiv.org/abs/2302.04761). *NeurIPS 2023*. Used to distinguish tool-use capability from runtime authorisation.
- FlowiseAI. [Agentflow V2](https://docs.flowiseai.com/using-flowise/agentflowv2). Official reference for the current visual agent-workflow builder.

## M03E: Embedding, API, and Deployment Readiness

### Chapter Overview

An embed presents a workflow through a user interface; a prediction API lets another application invoke it. Both turn an internal canvas into an external service boundary. Deployment readiness therefore concerns more than whether the flow produces a response in the test panel.

### Key Ideas

Authentication identifies or verifies a caller; authorisation limits what that caller may do. Input validation, rate and cost limits, error handling, output filtering, logs, and request correlation support reliable operation. Browser embeds add origin and user-interface considerations, while server-to-server APIs require protected credentials and explicit timeouts. Public exposure should be assumed adversarial.

### From Concepts to Practice

The final tutorial exercises embed and prediction surfaces, then reviews what is observable when requests succeed or fail. Boundary tests should include missing credentials, invalid payloads, oversized input, unavailable dependencies, and attempts to invoke disallowed capabilities. A flow is ready to share only when failure is bounded and diagnosable.

### Suggested Readings

- FlowiseAI. [Prediction API](https://docs.flowiseai.com/api-reference/prediction). Official request and response reference for invoking a flow from an application.
- FlowiseAI. [Embed](https://docs.flowiseai.com/using-flowise/embed). Official guidance for exposing a chatflow through a web interface.

## Bringing the Module Together

The canvas now represents a complete system path. The runtime hosts configured nodes; edges carry data; state preserves selected context; retrieval introduces external evidence; tools create effects; and embed or API surfaces admit external callers. Inspection must follow that same path. Visual configuration improves shared understanding, but security and reliability come from runtime controls and tests at each boundary.

## Practicals

The canonical Lab tutorials preserve the implementation sequence and the exact public workflow boundaries.

| Session | Public practical | Evidence focus |
| --- | --- | --- |
| M03X | [Flowise environment setup](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M03-Context-Orchestration/Flowise/M03X-Flowise-Environment-Setup.md) | Runtime, configuration, persistence, and exposure |
| M03A | [Interface and first chatflow](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M03-Context-Orchestration/Flowise/M03A-Flowise-Interface-First-Chatflow.md) | Node configuration and end-to-end message tracing |
| M03B | [Chatbot prompt and memory](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M03-Context-Orchestration/Flowise/M03B-Flowise-Chatbot-Prompt-Memory.md) | Instructions, session state, and isolation |
| M03C | [RAG over public unit documents](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M03-Context-Orchestration/Flowise/M03C-Flowise-RAG-Public-Unit-Docs.md) | Retrieval, grounding, provenance, and abstention |
| M03D | [Agentflow with safe tools](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M03-Context-Orchestration/Flowise/M03D-Flowise-AgentFlow-Safe-Tools.md) | Tool selection, validation, rejection, and termination |
| M03E | [Embed, API, and deployment readiness](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M03-Context-Orchestration/Flowise/M03E-Flowise-Embed-API-Deployment-Readiness.md) | External boundaries, failure tests, and observability |

## Further Reference Resources

- FlowiseAI. [Documentation](https://docs.flowiseai.com/). Authoritative entry point for current builders, integrations, configuration, and operations.

## Responsible Practice

Use only documents and data that may be processed for the intended purpose. Keep credentials outside exported flows, minimise retained conversation data, preserve source identity, and prevent one user or session from accessing another's state. Tool authority should be the minimum required for the demonstrated task.

Before sharing a flow, test malicious instructions, missing evidence, invalid tool arguments, dependency failure, and unauthorised requests. Record versions and material configuration, log actions without exposing secrets or unnecessary personal data, and provide a way to disable the workflow when behaviour or cost exceeds expectations.

## Preparing for the Next Module

M04 reconstructs these responsibilities in code. Nodes become functions or runnable components, edges become explicit data contracts, Agentflow selection becomes dispatch logic, and the visual trace becomes structured application evidence. The objective remains the same: keep model choice separate from application authority.

[Previous: M02](../M02-AI-Modeling/README.md) | [Course home](../README.md) | [Next: M04](../M04-Agent-Programming/README.md)

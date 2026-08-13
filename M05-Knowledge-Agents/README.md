[![Course home](https://img.shields.io/badge/FLIP-Agentic_AI-informational)](../README.md)

# M05: Knowledge and Stateful Agents

## Module Overview

Useful agents often need knowledge outside model parameters and state that survives one call. This module develops the path **ingest -> retrieve -> generate -> persist -> act**. It begins with a basic RAG system, narrows that design to a governed domain assistant, represents longer workflows as explicit graphs, and then incorporates vision-derived context into a bounded copilot pattern.

Retrieval and memory do not automatically make an agent truthful or consistent. They introduce new questions about corpus authority, chunking, relevance, provenance, access, freshness, checkpoints, and state ownership. The module treats each of these as an observable subsystem with its own evaluation evidence.

## Connection to the Course

M04 established explicit prompts, parsers, dispatchers, tools, and traces. M05 supplies those tools with managed knowledge and gives multi-step workflows durable state. It also clarifies terminology: retrieved evidence is not model memory, conversation context is not a durable record, and a checkpoint is not a guarantee that stored values remain correct.

The resulting stateful agents create a larger trust surface. M06 will add multiple roles and adversarial inputs, asking how messages, retrieved content, shared state, and tools can influence one another and who remains accountable for the combined behaviour.

## Learning Outcomes

By the end of this module, you should be able to:

- **Design** a RAG pipeline with explicit corpus, chunking, embedding, retrieval, and generation stages.
- **Evaluate** retrieval relevance separately from answer support and response quality.
- **Define** a bounded domain assistant with provenance, abstention, and access controls.
- **Represent** workflow state, transitions, checkpoints, loops, and intervention points in a graph.
- **Assess** a vision-enabled copilot for perception uncertainty, user intent, confirmation, and action safety.

## Module Map

| Session | Conceptual role | Added responsibility |
| --- | --- | --- |
| M05A | Basic RAG | Ingestion, ranked retrieval, grounding, and two-stage evaluation |
| M05B | Domain assistant | Scope, provenance, access, citations, and abstention |
| M05C | Stateful LangGraph workflow | State schema, transitions, checkpoints, and intervention |
| M05D | Vision and task copilot | Perception uncertainty, intent, confirmation, and bounded action |

## M05A: Basic Retrieval-Augmented Generation

### Chapter Overview

RAG connects a corpus to a generator at inference time. Documents are loaded, normalised, divided into retrievable units, transformed into embeddings, and stored with metadata. A query is represented and matched against the index; selected passages are then placed into the generation context. Each stage can succeed technically while still weakening the final answer.

### Key Ideas

Chunking controls the evidence unit. Pieces that are too small may lose context; pieces that are too large may mix topics and consume the context budget. Metadata preserves source identity and can support filters. Retrieval depth trades recall against noise. Dense similarity can find semantic matches, but lexical identifiers, dates, or rare terms may require other strategies or combined retrieval.

Retrieval evaluation asks whether relevant passages are found and ranked usefully, using labelled questions, expected sources, recall-oriented measures, or inspection at a chosen depth. Generation evaluation asks whether the answer is supported, complete, appropriately qualified, and faithful to those passages. Evaluating only prose can hide retrieval failure; evaluating only retrieval does not show whether the generator used evidence correctly.

### From Concepts to Practice

The basic RAG practical exposes the full pipeline. Inspect chunks and metadata, view retrieved passages before the response, and test supported, ambiguous, and unsupported questions. Record failure by stage so that changing a prompt is not used to mask a corpus or retrieval problem.

### Suggested Readings

- Lewis, P., et al. (2020). [Retrieval-augmented generation for knowledge-intensive NLP tasks](https://arxiv.org/abs/2005.11401). *Advances in Neural Information Processing Systems 33*. Used to establish the retrieve-then-generate architecture.
- Karpukhin, V., et al. (2020). [Dense passage retrieval for open-domain question answering](https://arxiv.org/abs/2004.04906). *Proceedings of EMNLP 2020*. Used to explain learned query and passage representations.
- Reimers, N., & Gurevych, I. (2019). [Sentence-BERT](https://doi.org/10.18653/v1/D19-1410). *Proceedings of EMNLP-IJCNLP 2019*. Used to connect efficient sentence embeddings with similarity search.
- LangChain. [Retrieval](https://docs.langchain.com/oss/python/langchain/retrieval). Official reference for loaders, splitters, embeddings, vector stores, and retrievers.

## M05B: RAG Domain Assistant Using Course Materials

### Chapter Overview

A domain assistant narrows the RAG problem to an authorised body of knowledge and a declared user purpose. The corpus boundary states what the assistant may know from retrieval; it does not prevent the underlying model from generating outside that evidence. The response policy must therefore specify when to answer, qualify, cite, ask a clarifying question, or abstain.

### Key Ideas

Query interpretation identifies the user's information need without silently broadening it. Evidence selection should preserve source, section, date, and version where relevant. Citations must point to material that actually supports the adjacent claim. Conflicting or stale sources need an explicit handling rule rather than being blended into a confident average.

Access control belongs before retrieval as well as before display. Index membership, metadata filters, tenant or user scope, and cache design can all expose restricted material. Provenance records should make a response inspectable without leaking inaccessible passages. Domain boundaries also support evaluation because expected sources and acceptable abstentions can be defined.

### From Concepts to Practice

The course-material assistant practical narrows the corpus and tests questions inside, outside, and at the edge of scope. Compare retrieved evidence with citations, verify that an unsupported request does not produce invented course facts, and inspect whether document updates can be distinguished from older indexed content.

### Suggested Readings

- The Lewis and Karpukhin readings in M05A provide the research basis for separating evidence selection from generation; this session applies that separation to provenance, scope, and access.

## M05C: LangGraph Stateful Workflows

### Chapter Overview

A graph-based workflow makes control and state transitions explicit. A state schema names values carried between steps. Nodes compute or invoke operations; edges define permitted transitions; conditional edges select a route from observed state. This structure is useful when a workflow must branch, retry, pause, or resume without reconstructing intent from a transcript.

### Key Ideas

Checkpointing records state at defined points and associates it with a thread or run identity. It supports inspection and recovery, but stored state needs versioning, retention, isolation, and migration rules. Resumability requires deterministic awareness of which effects already occurred. Code before an interruption may run again, so side-effecting operations need idempotence or an external transaction boundary.

Loops need a progress measure and termination condition. Human intervention should present the relevant state and proposed action, accept a structured decision, and resume along an explicit edge. Editing or replaying state is powerful but can create a history different from what originally occurred; audit evidence should distinguish original execution from later intervention.

### From Concepts to Practice

The LangGraph practical defines state, routes it through nodes, persists checkpoints, and exercises a pause or recovery path. Inspect state changes rather than relying on conversational summaries. Test a retry after partial progress and confirm that already-completed effects are not duplicated.

### Suggested Readings

- Harel, D. (1987). [Statecharts: A visual formalism for complex systems](https://doi.org/10.1016/0167-6423%2887%2990035-9). *Science of Computer Programming, 8*(3), 231-274. Used to ground explicit state and transition modelling.
- LangGraph. [Persistence](https://docs.langchain.com/oss/python/langgraph/persistence). Official reference for checkpoints, threads, and stored workflow state.
- LangGraph. [Interrupts](https://docs.langchain.com/oss/python/langgraph/interrupts). Official reference for pausing and resuming with human input.

## M05D: Copilot-Style Assistant with Vision and Task Execution

### Chapter Overview

A copilot combines user intent with perceived context and proposes or performs a task. When context comes from an image, screenshot, or camera, it is a model-derived interpretation rather than a direct fact. Text may be misread, objects omitted, spatial relationships confused, and important context outside the frame.

### Key Ideas

The workflow should separate raw input, perception output, task interpretation, planned action, confirmation, and execution result. Confidence language from a model is not calibrated evidence by default. Consequential action should depend on observable conditions and user confirmation, especially when the target, quantity, recipient, or irreversible effect is uncertain.

Privacy and accessibility also change with vision. Images may contain bystanders, identifiers, messages, or location information. Alternatives should exist when a user cannot provide or inspect an image. The system should reveal what it believes it observed and allow correction before that interpretation drives a tool.

### From Concepts to Practice

The copilot practical connects visual context to a bounded task path. Test clear, ambiguous, incomplete, and contradictory inputs; require confirmation of material details; and verify the execution result rather than trusting the proposed plan. The goal is not autonomous action at any cost, but appropriate assistance under uncertainty.

### Suggested Readings

- Radford, A., et al. (2021). [Learning transferable visual models from natural language supervision](https://proceedings.mlr.press/v139/radford21a.html). *Proceedings of ICML 2021*. Used to frame transferable image-text representations and their data limitations.
- OpenAI. [Images and vision](https://platform.openai.com/docs/guides/images-vision). Official provider guidance used to inspect current image-input boundaries and constraints.

## Bringing the Module Together

The module's pipeline now joins knowledge, state, and action. Ingestion creates a governed evidence base; retrieval selects candidate support; generation interprets that evidence; persistence carries explicit state; and tools act on a confirmed interpretation. Provenance and checkpoints make these stages inspectable, while abstention and intervention prevent uncertainty from being hidden by fluent output.

## Practicals

The public Lab notebooks provide the canonical implementation contexts for the four chapters.

| Session | Public practical | Evidence focus |
| --- | --- | --- |
| M05A | [Basic RAG system notebook](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M05-Knowledge-Agents/Jupyter/M05A-Basic-RAG-System.ipynb) | Chunks, retrieval, grounding, and separate evaluation |
| M05B | [Course-material domain assistant notebook](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M05-Knowledge-Agents/Jupyter/M05B-RAG-CourseMaterials-Assistant.ipynb) | Scope, provenance, citations, access, and abstention |
| M05C | [LangGraph stateful workflows notebook](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M05-Knowledge-Agents/Jupyter/M05C-LangGraph-StatefulWorkflows.ipynb) | State, transitions, checkpoints, retry, and intervention |
| M05D | [Vision and task-execution copilot notebook](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M05-Knowledge-Agents/Jupyter/M05D-Copilot-Vision-TaskExecution.ipynb) | Perception uncertainty, confirmation, and verified action |

## Further Reference Resources

- LangChain and LangGraph. [Documentation](https://docs.langchain.com/). Official entry point for current retrieval and orchestration interfaces.
- Revisit the M02 embedding material when diagnosing retrieval quality; representation, index, corpus, and query failures require different changes.

## Responsible Practice

Index only material that may be processed for the declared purpose. Preserve provenance, enforce access before retrieval, isolate users and threads, define retention, and provide correction or deletion paths where appropriate. Treat retrieved text as untrusted content rather than as instructions to the system.

Persist the minimum state needed for continuity and make consequential effects reviewable. For vision, disclose uncertainty and provide accessible alternatives. Across every stage, record enough evidence to locate a failure without retaining unnecessary personal or sensitive data.

## Preparing for the Next Module

M06 introduces multiple agent roles and adversarial pressure. Retrieved passages, visual interpretations, tool results, and inter-agent messages will all be treated as potentially untrusted inputs. Coordination must then be justified against a simpler baseline and paired with explicit security controls and accountable ownership.

[Previous: M04](../M04-Agent-Programming/README.md) | [Course home](../README.md) | [Next: M06](../M06-Multi-Agent-Safety/README.md)

[![Course home](https://img.shields.io/badge/FLIP-Agentic_AI-informational)](../README.md)

# M02: Prompt Engineering and Retrieval-Augmented Generation

## Module Overview

An agent's next action begins with a single model call, and the prompt and evidence supplied to that call are the first things a developer can actually control. This module follows a four-hour path across three control questions: what should the model do, did an intervention work, and which evidence should enter the call. It treats prompting not as a search for a magic phrase but as a repeatable control loop, and it treats missing facts not as a prompting failure but as a signal to retrieve evidence before generation.

The emphasis is not on collecting prompt tricks. It is on making a target observable, testing an intervention under a controlled comparison, and diagnosing precisely which failure occurred, a specification problem, an evidence-use problem, or an evidence-access problem, before choosing a remedy. These same judgments later determine whether a node in an orchestrated agentic workflow can be trusted to specify, retrieve, and ground correctly.

## Connection to the Course

M01 established four foundations: the Python and ML modelling workflow, generative AI concepts, LLM mechanics such as tokens, context windows, next-token prediction, and instruction following, and information retrieval, including indexes, sparse and dense scoring, and relevance. M02 applies these foundations directly, moving from instruction-following behaviour to a controlled prompt-engineering loop, then extending the model call with retrieved evidence whenever the required facts are not already present in context.

M03 places these same mechanisms inside a visible, orchestrated workflow. A learner who can already specify a testable prompt, diagnose whether a failure is a specification, evidence-use, or evidence-access problem, and trace a retrieval pipeline end to end is better prepared to decide what a workflow node should do and what must be verified at each connection between nodes.

## Learning Outcomes

By the end of this module, you should be able to:

- **Relate** generative AI, foundation models, LLMs, and instruction-following behaviour to locate where runtime control actually operates.
- **Distinguish** model-level control, pretraining, instruction tuning, and alignment, from runtime control, prompt, supplied context, and retrieval.
- **Design** prompts as specifications, using task, context, constraints, examples, and output contracts to produce observable, checkable behaviour.
- **Evaluate** prompt interventions through controlled comparisons across normal, edge, and ambiguous cases.
- **Construct** a retrieval-augmented generation pipeline from source governance and chunking through retrieval, context construction, and grounded generation.
- **Diagnose** a model-call failure as a specification, evidence-use, or evidence-access problem and select the remedy that matches it.

## Module Map

| Session | Conceptual role | Progression |
| --- | --- | --- |
| M02A | Prompt foundations | Instruction following, model-level vs. runtime control, and in-context learning |
| M02B | Prompt engineering as a control loop | Target, intervention, observation, evaluation, and diagnosis |
| M02C | Retrieval-augmented generation | Source governance, offline indexing, online retrieval, grounding, and evaluation |

## M02A: Prompt Foundations

### Chapter Overview

Generative AI, foundation models, and large language models describe nested lenses on one model landscape: generative systems broadly, models broadly pretrained and adaptable across tasks, and models that are language-centred and trained to predict the next token. Locating a system inside that nesting matters because it separates what comes from pretraining from what is supplied at call time. Instruction tuning, illustrated by the shift from a base model to an instruction-tuned counterpart, updates model parameters before deployment so that a task is more likely to be completed rather than merely continued; it does not specify what any particular future user actually wants.

### Key Ideas

Two layers of control shape any deployed system. Model-level control, pretraining, instruction tuning, and alignment, is persistent across calls and usually outside the application developer's reach. Runtime control, the prompt, supplied context, and retrieval, conditions one specific call and is the layer this module teaches developers to design deliberately. A prompt specifies a call through task, supplied context, constraints, examples, and an output contract; role is optional and should be included only when a real audience or perspective changes the expected response. The context window is a finite, ordered workspace: enlarging it increases capacity but does not by itself select relevant or trustworthy content, a distinction sharpened by cases where the same input produces a different answer once local context changes without any change to model parameters. In-context learning lets a frozen model infer a task mapping from a description or demonstrations supplied at inference time; zero-, one-, and few-shot regimes differ only in how many demonstrations are supplied, and their usefulness depends on the demonstrations being relevant, sufficient, and consistent with each other, since conflicting examples can induce the wrong rule.

### From Concepts to Practice

The practical exercises trace one fixed system map across specification, control layer, and demonstration design. Learners predict model behaviour before observing it, identify exactly which examples a model was shown, and test what happens when demonstrations conflict. The habit to build here is treating every prompt as a specification whose fields can be listed and checked, not as a single inspired sentence.

### Suggested Readings

- Brown, T. B., et al. (2020). [Language models are few-shot learners](https://papers.nips.cc/paper/2020/hash/1457c0d6bfcb4967418bfb8ac142f64a-Abstract.html). *Advances in Neural Information Processing Systems 33*. Used to define in-context learning and the zero-, one-, and few-shot regimes.
- Google Research. [Better language models without massive compute](https://research.google/blog/better-language-models-without-massive-compute/) (2022). Used to contrast base and instruction-tuned model behaviour on the same task.

## M02B: Prompt Engineering as a Control Loop

### Chapter Overview

Prompt engineering treats prompting as a repeatable control loop rather than a one-off request: define an observable target, design an intervention, observe the output, evaluate it under a controlled comparison, and diagnose the earliest failure before revising anything. A named pattern, such as a structured output contract or task decomposition, is a reusable response to a recurring requirement; a specific phrase claimed to change behaviour is a testable hypothesis, not a rule to imitate.

### Key Ideas

A target is useful only when it is observable: naming an audience, the required content, and a checkable limit turns a vague request into a specification that can actually be judged. Interventions include explicit output contracts that let downstream code parse, validate, and accept, repair, or reject a response; decomposition into inspectable steps so a complex judgement is not left implicit; and grounding constraints that bind claims to supplied evidence through scope, traceability, and an explicit abstention rule for missing support. Observation records what a specific prompt version, model, and setting actually produced, including confident but fabricated or self-contradicted claims, and is distinct from evaluation, which compares that evidence across cases and conditions. A fair evaluation changes one variable at a time, tests normal, edge, and ambiguous cases, measures both the intended gain and any regression, and states only the conclusion the fixed comparison supports; scores are comparable only when the same cases, runs, and measures apply to every condition. Diagnosis then separates a specification failure, where the task or required output was unclear, from an evidence-use failure, where relevant evidence was ignored or misstated, from an evidence-access failure, where the required evidence was missing, stale, restricted, or distributed, and each diagnosis implies a different next action: revise the prompt, strengthen grounding, or retrieve.

### From Concepts to Practice

The practical runs the same classification and evidence-bound tasks under baseline and intervention prompts, scores both under identical cases and decision rules, and states only the conclusion the scores support. Learners then classify a set of failure traces by cause and select the matching remedy, which sets up the transition to retrieval when the diagnosed cause is evidence access rather than prompt wording.

## M02C: Retrieval-Augmented Generation

### Chapter Overview

Retrieval-augmented generation adds the capability that prompt revision alone cannot supply: evidence that is missing, stale, restricted, or distributed across sources. RAG is a two-path system: an offline path builds and maintains a searchable index from governed sources, and an online path turns one query into retrieved evidence, a constructed context, and a grounded, traceable answer; a separate evaluation loop locates the earliest failed stage rather than only scoring the final response.

### Key Ideas

Offline indexing begins with source governance: a source is admitted as evidence only when its currency, access permission, and traceability are recorded, so stale or unauthorised material is excluded before it can ever be retrieved. Admitted text is split into chunks sized to keep one governed condition or exception together; chunk size and overlap are retrieval parameters that trade completeness against irrelevant text and index size, not formatting preferences. Chunks and queries are then mapped into a shared vector space by a retrieval encoder, building on the word-embedding idea introduced in M01, and organised into a reproducible index. Online, a query is translated into that same representation and matched using sparse, dense, or fused scoring to maximise recall and ranking quality before any context is assembled. Context construction is a constrained optimisation: select trustworthy evidence under a token budget, order and diversify it, and package a complete, delimited input, since retrieving something relevant does not guarantee it will be selected or used. Generation is grounded only when material claims trace to supplied evidence, with explicit qualification or abstention when the evidence is insufficient. Evaluation uses stage-level traces, source inventory, retrieval quality, context composition, and groundedness, to locate the earliest failure and revise exactly one variable before rerunning.

### From Concepts to Practice

The practical builds a small end-to-end pipeline over a governed source inventory: apply admission and chunking rules, build an index, run retrieval, construct a context under a budget, generate a grounded answer, and trace a deliberately introduced failure back to its stage. This mirrors a running case of a policy question whose answer is missing, stale, or distributed, and it produces the evidence-access capability that the M02B control loop can call on before generation.

### Suggested Readings

- Lewis, P., et al. (2020). [Retrieval-augmented generation for knowledge-intensive NLP tasks](https://arxiv.org/abs/2005.11401). *Advances in Neural Information Processing Systems 33*. Used to establish the distinction between parametric generation and retrieved external evidence.
- Reimers, N., & Gurevych, I. (2019). [Sentence-BERT: Sentence embeddings using Siamese BERT-networks](https://doi.org/10.18653/v1/D19-1410). *Proceedings of EMNLP-IJCNLP 2019*. Used to connect retrieval encoders to the shared vector space that indexing and matching depend on.

## Bringing the Module Together

The three sessions form one control chain over a single model call. M02A asks what a prompt actually specifies and what a frozen model can infer from context alone. M02B turns prompting into a loop that sets an observable target, tests an intervention under controlled comparison, and diagnoses whether the remaining failure is a specification problem or an evidence problem. M02C answers the evidence-access diagnosis by retrieving, constructing, and grounding context before generation resumes. Prompt and RAG both operate inside a single decision step of an agent's interaction with its environment; M03 is where that step is composed with memory, routing, and tools into a complete orchestrated workflow.

## Practicals

The Lab repository has been realigned to this module's confirmed Prompt Engineering and RAG design: the notebook directory and file names now match the M02A-M02C session structure below. The notebooks currently contain a structured outline with placeholder exercises; full worked practicals are still being authored and will be filled in without changing these stable names.

| Session | Lab notebook | Notebook status |
| --- | --- | --- |
| M02A | [Prompt foundations notebook](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M02-Prompt-RAG/Jupyter/M02A-Prompt-Foundations.ipynb) | Outline and placeholder exercises |
| M02B | [Prompt engineering control loop notebook](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M02-Prompt-RAG/Jupyter/M02B-Prompt-Engineering-Control-Loop.ipynb) | Outline and placeholder exercises |
| M02C | [Retrieval-augmented generation notebook](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M02-Prompt-RAG/Jupyter/M02C-Retrieval-Augmented-Generation.ipynb) | Outline and placeholder exercises |

## Further Reference Resources

- Sentence Transformers. [Semantic search](https://www.sbert.net/examples/sentence_transformer/applications/semantic-search/README.html). Official documentation used to relate retrieval encoders to the dense-retrieval step of the RAG pipeline.

## Responsible Practice

Bind every material claim to supplied evidence and state what happens when support is missing, rather than letting a fluent answer stand in for a verified one. Admit a source into an index only when its currency, access permission, and provenance are recorded, and exclude stale or restricted material before it can be retrieved. Preserve traceability from an answer back to its source so a user or reviewer can inspect what was actually used, and prefer qualification or abstention over a confident but unsupported claim.

## Preparing for the Next Module

M03 places the prompt and RAG capabilities built here inside a visible, orchestrated workflow. The control loop from M02B becomes a testable node behaviour, the retrieval pipeline from M02C becomes a Flowise ingestion and retrieval chain, and diagnosis extends from one model call to failures that can occur at the connections between nodes.

[Previous: M01](../M01-Foundations/README.md) | [Course home](../README.md) | [Next: M03](../M03-Context-Orchestration/README.md)

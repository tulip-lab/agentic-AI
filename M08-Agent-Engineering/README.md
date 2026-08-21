[![Course home](https://img.shields.io/badge/FLIP-Agentic_AI-informational)](../README.md)

# M08: Agent Engineering and Productisation

## Module Overview

The final common-core module treats an agent as an engineered product rather than a demonstration. It develops the sequence **requirements -> evaluation -> integration -> guardrails -> operation -> product evidence**. Readiness depends on complete workflows, explicit interfaces, bounded authority, observable operation, and a user need that justifies cost and risk.

The sessions connect evaluation design, repository-aware coding agents, product experiments, Model Context Protocol (MCP), and lifecycle hooks or guards. Together they establish a reviewable path from intended outcome to operational evidence. The aim is not maximum autonomy; it is appropriate automation with known boundaries, measurable performance, and accountable control.

## Connection to the Course

M01-M07 supplied the components: controlled model access, representations, visual and programmatic orchestration, retrieval, durable state, multi-agent coordination, safety analysis, adaptation, and serving. M08 asks whether the assembled system works for its intended users under expected, edge, adversarial, and failure conditions.

This integration changes the unit of evaluation. A model may answer accurately while an agent chooses the wrong tool, loses state, exceeds a budget, or creates an unreviewable change. A modest model can still support a valuable product when the surrounding workflow is well designed.

## Learning Outcomes

By the end of this module, you should be able to:

- **Define** success, unacceptable failure, datasets, slices, baselines, and metrics before evaluation.
- **Operate** a coding agent through repository audit, planning, bounded changes, tests, review, and rollback.
- **Test** product assumptions about user need, workflow fit, adoption, economics, and risk.
- **Explain** MCP hosts, clients, servers, primitives, transports, capability discovery, and trust boundaries.
- **Place** validation, approval, policy, audit, and interruption controls at observable workflow events.

## Module Map

| Session | Conceptual role | Engineering evidence |
| --- | --- | --- |
| M08A | Model and agent evaluation | Requirements, datasets, slices, metrics, uncertainty, and errors |
| M08B | Coding-agent development | Context, plan, patch, test, review, and rollback |
| M08C | Productised AI agents | User problem, adoption, economics, risk, and experiments |
| M08D | MCP fundamentals | Interoperable context and capability boundaries |
| M08E | Hooks and workflow guards | Event-based validation, approval, enforcement, audit, and interruption |

## M08A: Hugging Face Evaluation

### Chapter Overview

Evaluation begins by defining the intended outcome and unacceptable failure. Only then can a dataset and metric represent the requirement. Model evaluation measures outputs for selected inputs; agent evaluation also observes action sequences, tool effects, state transitions, cost, latency, recovery, and completion under interaction.

### Key Ideas

An evaluation set should reflect expected use without duplicating training or tuning data. Slices expose performance across task types, difficulty, languages, user groups, tools, or failure conditions. A baseline reveals whether added agent complexity improves on a fixed workflow, earlier version, or simple rule. Metrics should cover relevant trade-offs rather than compressing all evidence into one score.

Sampling variation, model updates, judge disagreement, and small datasets create uncertainty. Report counts and distributions, repeat variable runs where needed, and inspect confidence intervals or paired differences when appropriate. Error analysis groups failures by cause and severity, then links them to a system change.

### From Concepts to Practice

The practical uses Hugging Face evaluation tooling to compute repeatable measures while preserving examples for inspection. Define success and slices first, compare a baseline, and produce a short error taxonomy. A metric implementation can calculate a value; it cannot decide whether the value represents product success.

### Suggested Readings

- Liang, P., et al. (2022). [Holistic evaluation of language models](https://arxiv.org/abs/2211.09110). Used to connect scenarios, multiple metrics, coverage, and transparent reporting.
- Liu, X., et al. (2023). [AgentBench: Evaluating LLMs as agents](https://arxiv.org/abs/2308.03688). Used to distinguish interactive agent behaviour from isolated model responses.
- Hugging Face. [Evaluate](https://huggingface.co/docs/evaluate/index). Official reference for maintained metric and evaluation workflows.

## M08B: Codex Codebase Understanding and Development

### Chapter Overview

A coding agent operates inside a software system with existing architecture, tests, conventions, dependencies, and user changes. Repository understanding is therefore part of the task. A disciplined workflow audits relevant context, states a plan, makes a bounded patch, runs evidence-producing checks, and presents the result for human review.

### Key Ideas

The audit identifies authoritative files, local instructions, branch state, affected interfaces, and tests. Planning defines scope and acceptance evidence. The patch should preserve unrelated work and remain reviewable. Tests, diffs, and runtime observations establish what changed; generated explanations are not substitutes for those artefacts.

Sandboxing limits technical reach, while approval controls when a person must authorise an action. Neither guarantees that a requested change is correct. Review should examine intent, design, security, data handling, maintainability, and evidence. Rollback requires known commits, reversible migrations, feature controls, or another recovery path appropriate to the change.

### From Concepts to Practice

The Codex handout applies this sequence to codebase understanding and development. Separate read-only investigation from state-changing work, keep commands within authorised scope, and compare the final diff with the original requirement. A coding agent is most useful when its work remains inspectable and recoverable.

### Suggested Readings

- Jimenez, C. E., et al. (2023). [SWE-bench: Can language models resolve real-world GitHub issues?](https://arxiv.org/abs/2310.06770). Used to connect repository context and executable tests with coding-agent evaluation.
- OpenAI. [Codex documentation](https://developers.openai.com/codex/). Official reference for current coding-agent workflows, sandboxing, approvals, and review controls.

## M08C: Productised AI Agents and Go-to-Market Planning

### Chapter Overview

Productisation starts with a bounded user problem, not an agent feature. The workflow must identify who experiences the problem, what they do today, where delay or error occurs, and why an AI-assisted step improves the outcome. The proposed automation should fit the surrounding people, systems, incentives, and exceptions.

### Key Ideas

A value proposition is a testable claim about outcome, user, and context. Adoption evidence includes repeated use, task completion, retained users, willingness to switch, and appropriate trust, not only stated enthusiasm. Human-AI interaction should communicate capability, set expectations, support correction, expose relevant uncertainty, and allow efficient override.

Unit economics include inference, retrieval, storage, integration, monitoring, human review, support, and incident costs. Risk can change the viable market or operating model even when technical performance is strong. Small experiments should isolate assumptions: a concierge workflow can test value before automation, a prototype can test usability, and a controlled pilot can test operational performance and retention.

### From Concepts to Practice

The go-to-market handout converts one use case into explicit hypotheses, measures, and stop or continue criteria. Map the existing workflow, identify the smallest valuable intervention, estimate recurring costs, and choose an experiment that could disconfirm the main assumption. Product evidence should remain separate from benchmark evidence.

## M08D: MCP Fundamentals and Tool/Context Servers

### Chapter Overview

MCP standardises how an AI application exchanges context and capabilities with external servers. The host is the application that coordinates users, models, policy, and context. It creates client instances; each client communicates with one server. Servers expose focused capabilities and may run as local processes or remote services.

### Key Ideas

The core server primitives have different purposes. **Resources** expose addressable contextual data. **Prompts** expose reusable interaction templates. **Tools** expose callable operations with schemas. Discovery and capability declarations tell each side what is supported; they do not grant permission or establish trust. The current protocol uses self-contained requests carrying version and capability information rather than relying on hidden conversational state.

A transport carries protocol messages and shapes process, network, authentication, and availability concerns. Connection, server-process, request, and subscription lifecycles need explicit cleanup, timeout, retry, and failure behaviour. The host should limit context shared with each server and keep servers isolated from one another. Tool results and resource content remain untrusted inputs.

### From Concepts to Practice

The MCP practical identifies host, client, server, transport, and primitives before connecting a bounded server. Inspect advertised capabilities, request and response schemas, errors, and data exposure. Test unavailable servers, invalid arguments, unauthorised access, and a capability that changes between versions.

### Suggested Readings

- Model Context Protocol. [Specification](https://modelcontextprotocol.io/specification/). Authoritative source for the current architecture, primitives, transport patterns, discovery, and security requirements.

## M08E: Agent Hooks and Workflow Guards

### Chapter Overview

Hooks observe defined lifecycle events such as session start, prompt submission, tool use, permission request, or stop. A guard attaches a deterministic check or control to an event where relevant data and authority are available. Event placement matters: checking an action after execution cannot prevent its effect.

### Key Ideas

Validation checks form, type, state, or postconditions and returns structured evidence. Approval asks an authorised person or service to accept a specific proposed action. Policy enforcement allows, denies, or transforms behaviour according to a rule. Audit records what occurred. Interruption pauses or stops a workflow when safe continuation is uncertain. One hook may support several purposes, but the purposes and failure policy should remain explicit.

Hooks are executable dependencies. Their source, precedence, permissions, timeouts, concurrency, output handling, and failure mode require review and tests. A fail-open guard may preserve availability while allowing unsafe action; a fail-closed guard may prevent harm while blocking legitimate work. The choice should follow the protected asset and operational requirement.

### From Concepts to Practice

The final practical places guards at selected workflow events and tests allowed, denied, failed, and unavailable-check cases. Verify that logs correspond to actual events, approvals bind to the reviewed action, and interruption leaves recoverable state. Guard effectiveness must be demonstrated with traces, not inferred from configuration alone.

### Suggested Readings

- OpenAI. [Codex hooks](https://developers.openai.com/codex/hooks). Official reference for current lifecycle events, matching, handler execution, and hook trust behaviour.

## Bringing the Module Together

Engineering evidence now follows the whole product. Requirements define evaluation; evaluation identifies errors; coding practice makes changes reviewable; product experiments test value and adoption; MCP creates explicit integration boundaries; and guards control observable events. Operation feeds new failures, cost, and user evidence back into requirements. This is a lifecycle rather than a one-time release gate.

## Practicals

The public Lab materials provide the canonical implementation and analysis contexts for the final module.

| Session | Public practical | Evidence focus |
| --- | --- | --- |
| M08A | [Hugging Face evaluation notebook](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M08-Agent-Engineering/Jupyter/M08A-HuggingFace-Evaluation.ipynb) | Success criteria, baselines, slices, metrics, and errors |
| M08B | [Codex codebase development handout](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M08-Agent-Engineering/Codex/M08B-Codex-Codebase-Understanding-and-Development.md) | Audit, plan, bounded change, tests, review, and rollback |
| M08C | [Productised AI agents handout](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M08-Agent-Engineering/Codex/M08C-Productised-AIAgents-GoToMarket.md) | User workflow, hypotheses, adoption, economics, and experiments |
| M08D | [MCP fundamentals notebook](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M08-Agent-Engineering/Jupyter/M08D-MCP-Fundamentals-ToolContextServers.ipynb) | Architecture, discovery, primitives, transport, and trust |
| M08E | [Agent hooks and workflow guards notebook](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M08-Agent-Engineering/Jupyter/M08E-Agent-Hooks-WorkflowGuards.ipynb) | Event placement, validation, approval, audit, and interruption |

## Further Reference Resources

- NIST. [AI RMF Playbook](https://airc.nist.gov/AI_RMF_Knowledge_Base/Playbook). Authoritative action-oriented resource for connecting governance, mapping, measurement, management, monitoring, and accountable review.
- Revisit the M06 security sources when an interface, hook, coding agent, or product experiment changes authority, data exposure, affected people, or legal context.

## Responsible Practice

Define prohibited outcomes and human authority before deployment. Protect evaluation data, repositories, credentials, protocol connections, hook code, logs, and user records. Use least privilege, authenticated interfaces, explicit approval for consequential effects, monitored budgets, recoverable state, incident procedures, and a tested stop path.

Report results with versions, conditions, uncertainty, negative findings, and affected slices. Do not convert benchmark performance into claims about safety, user value, or legal compliance. Continue monitoring for drift, new attack paths, changing costs, and user harm, and assign each response decision to an accountable owner.

## Completing the Common Core

The eight modules form one engineering progression. M01 establishes controlled interaction; M02 supplies models and representations; M03 engineers runtime context and orchestration; M04 makes the resulting tools and traces explicit in code; M05 adds knowledge and durable state; M06 expands coordination and safety; M07 evaluates adaptation and serving; and M08 integrates requirements, evidence, interfaces, controls, operation, and user value.

Completion means being able to explain and test this whole path, including its limits. A responsible agentic system is not defined by how many autonomous steps it can take, but by whether its behaviour is useful, bounded, observable, recoverable, and governed with evidence.

[Previous: M07](../M07-Model-Adaptation/README.md) | [Course home](../README.md)

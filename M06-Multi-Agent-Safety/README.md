[![Course home](https://img.shields.io/badge/FLIP-Agentic_AI-informational)](../README.md)

# M06: Multi-Agent Systems and Safety

## Module Overview

Multiple agents can divide work, use different capabilities, critique intermediate outputs, and involve people at selected points. They also create more messages, state, credentials, tools, and failure paths. This module develops the sequence **roles -> messages -> coordination -> threats -> controls -> accountability** and asks whether each added role creates measurable value over a simpler design.

The sessions move from collaboration patterns to prompt-injection defence, local model operation, and integrated security, data, legal, and governance analysis. Safety is treated as a property supported by evidence across the system, not as a personality assigned to one agent or a sentence added to a prompt.

## Connection to the Course

M05 combined external knowledge, persistent state, visual interpretation, and bounded action. In M06, those same values can cross agent boundaries. A retrieved passage may influence a planner, one agent's message may redirect another, and shared state may carry an error through an entire workflow. Coordination therefore expands both capability and attack surface.

M07 will ask whether changing or serving a different model is justified after system-level controls are understood. This ordering matters: fine-tuning cannot repair missing authorisation, insecure tools, weak data provenance, or unclear ownership.

## Learning Outcomes

By the end of this module, you should be able to:

- **Justify** a multi-agent design against a single-agent or deterministic baseline.
- **Specify** roles, message contracts, shared state, termination, and escalation paths.
- **Model** direct and indirect prompt-injection threats across retrieval, agents, and tools.
- **Assess** local model operation across privacy, quality, hardware, network, and maintenance constraints.
- **Link** threats, vulnerabilities, harms, controls, evidence, and accountable owners in a system risk review.

## Module Map

| Session | Conceptual role | Main question |
| --- | --- | --- |
| M06A | Multi-agent collaboration | Does role separation improve observable task performance? |
| M06B | Malicious-instruction defence | Can untrusted data alter instructions or tool behaviour? |
| M06C | Private agents with Ollama | Which risks move, remain, or increase under local operation? |
| M06D | Security, poisoning, and law | What controls, evidence, and ownership make risk governable? |

## M06A: Multi-Agent Collaboration

### Chapter Overview

A multi-agent workflow assigns distinct responsibilities to communicating components. Roles may plan, retrieve, execute, verify, or approve. Separation can improve context focus and independent checking, but every handoff can lose information, duplicate work, increase latency, or diffuse responsibility.

### Key Ideas

Task decomposition should follow genuine differences in information, tools, expertise, or control. A role needs defined inputs, outputs, authority, and failure behaviour. Message contracts should distinguish instructions, observations, proposals, and decisions. Shared state needs an owner and update policy; otherwise later agents may treat an unverified assertion as established fact.

Coordination patterns include sequential delegation, parallel work with aggregation, critique and revision, and voting or consensus. Agreement is not correctness because agents may share the same model and failure mode. Loops require budgets, progress criteria, and termination. Escalation should identify the condition and the person or system authorised to resolve it.

### From Concepts to Practice

The collaboration practical compares a role-based workflow with a single-agent baseline on the same bounded task. Measure quality, consistency, calls, time, cost, and recoverability. Inspect message traces to determine whether an improvement comes from useful decomposition or merely from spending more inference.

### Suggested Readings

- Li, G., et al. (2023). [CAMEL: Communicative agents for "mind" exploration of large language model society](https://arxiv.org/abs/2303.17760). Used to examine role-playing communication and its assumptions.
- Wu, Q., et al. (2023). [AutoGen: Enabling next-gen LLM applications via multi-agent conversation](https://arxiv.org/abs/2308.08155). Used to study configurable roles, messages, human participation, and termination.

## M06B: Malicious Instructions and Prompt-Injection Defence

### Chapter Overview

Prompt injection occurs when attacker-controlled content influences a model to disregard the intended task or expose capabilities. Direct injection arrives through a user message. Indirect injection is embedded in a document, website, tool result, image, or agent message that the system retrieves and places into context.

### Key Ideas

Instruction hierarchy helps describe intended precedence, but a model does not provide a hard security boundary between instructions and data. Retrieved content and inter-agent messages should be labelled, delimited, minimised, and treated as untrusted. Sensitive operations should occur behind deterministic policy, allowlisted tools, narrow credentials, argument validation, and approval when consequences warrant it.

Isolation limits what a compromised component can observe or affect. Separate contexts, read-only retrieval, network restrictions, output encoding, and least-privilege tool scopes reduce impact. Detection may identify known patterns but cannot be the sole control. Adversarial tests should vary placement, encoding, language, multi-turn setup, and attempts to make one agent relay hostile content to another.

### From Concepts to Practice

The defence practical builds an attack set before judging controls. Record the protected asset, attack path, expected refusal or safe behaviour, and actual trace. Test both whether the agent follows the malicious instruction and whether it leaks, calls a tool, modifies state, or contaminates another role.

### Suggested Readings

- Greshake, K., et al. (2023). [Not what you've signed up for: Compromising real-world LLM-integrated applications with indirect prompt injection](https://arxiv.org/abs/2302.12173). Used to establish external content as an instruction-delivery path.
- OWASP. [Top 10 for LLM and generative AI applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/). Authoritative security taxonomy used to connect injection with excessive agency, data, and supply-chain risks.

## M06C: Private Agents with Open-Source Models and Ollama

### Chapter Overview

Running a model locally can keep prompts and outputs within an organisation-controlled environment and reduce reliance on a hosted inference provider. It does not automatically make an agent private. Models, packages, telemetry, update channels, network tools, logs, and the host operating system remain part of the data path.

### Key Ideas

Local model choice involves capability, model and data provenance, licence terms, context length, quantisation, memory, accelerator support, and energy use. Smaller or compressed models may reduce hardware requirements while changing task quality. A private deployment still needs benchmark evidence on the actual workload rather than assumptions based on model size or popularity.

The serving boundary needs authentication if reachable beyond one trusted process. Network binding, firewall rules, file permissions, patching, backups, resource limits, monitoring, and incident recovery become local responsibilities. Offline operation can reduce some exposure but may complicate updates and vulnerability response. Hosted and local designs move risks; neither removes governance.

### From Concepts to Practice

The Ollama practical runs a bounded agent workflow against a local model and records quality, latency, resource use, and connectivity. Inspect which data remains local, which dependencies were downloaded, which ports are reachable, and how the system behaves when resources are exhausted or the model is unavailable.

### Suggested Readings

- Ollama. [Documentation](https://docs.ollama.com/). Official reference for current model management, runtime configuration, and service interfaces.

## M06D: Agent Security, Data Poisoning, and Legal Risks

### Chapter Overview

An integrated review begins with assets and intended use, then identifies threats and vulnerabilities. A threat is a potential cause of an unwanted event; a vulnerability is a weakness it can exploit; harm is the consequence to people, organisations, or systems. A control changes likelihood or impact, evidence shows whether it operates, and an accountable owner decides and responds.

### Key Ideas

Agent systems combine conventional software threats with model-specific uncertainty. Relevant paths include poisoned training or retrieval data, compromised dependencies, malicious tools, insecure outputs, excessive permissions, privacy leakage, denial of service, and manipulated shared state. Data provenance, dependency review, access control, sandboxing, monitoring, rollback, and incident procedures form a layered control set.

Legal and governance duties depend on jurisdiction, role, data, sector, system use, and time. Primary legal text and authoritative guidance should be consulted rather than treating a generic checklist as legal advice. Privacy, intellectual property, consumer protection, discrimination, record keeping, and safety obligations may intersect. Every material risk needs a named owner and an escalation path, even when a vendor supplies the model.

### From Concepts to Practice

The final practical creates a traceable risk analysis: asset, threat, vulnerability, plausible harm, existing control, evidence gap, further treatment, owner, and review trigger. Prioritise concrete attack paths and affected parties. Avoid claiming that a framework label or policy statement proves the system is safe.

### Suggested Readings

- Carlini, N., et al. (2023). [Poisoning web-scale training datasets is practical](https://arxiv.org/abs/2302.10149). Used to connect data collection and provenance with supply-chain attack feasibility.
- NIST. [AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework). Authoritative voluntary framework used to connect governance, mapping, measurement, and management.
- Australian Government. [Voluntary AI Safety Standard](https://www.industry.gov.au/publications/voluntary-ai-safety-standard). Authoritative example of lifecycle guardrails in an Australian context.
- European Union. [Regulation (EU) 2024/1689](https://eur-lex.europa.eu/eli/reg/2024/1689/oj). Primary legal text used to demonstrate role-, risk-, and context-dependent regulatory analysis.

## Bringing the Module Together

Role specialisation can create useful checks, but it also creates new trust boundaries. Messages and retrieved content are data, not trusted instructions; local operation changes ownership rather than eliminating risk; and controls matter only when their operation is evidenced. The complete chain ends with accountability: someone must own the decision to accept, reduce, transfer, avoid, monitor, or revisit a risk.

## Practicals

The canonical Lab notebooks develop the module from coordination evidence to integrated risk analysis.

| Session | Public practical | Evidence focus |
| --- | --- | --- |
| M06A | [Multi-agent collaboration notebook](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M06-Multi-Agent-Safety/Jupyter/M06A-MultiAgent-Collaboration.ipynb) | Baseline comparison, messages, cost, and termination |
| M06B | [Malicious-instruction defence notebook](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M06-Multi-Agent-Safety/Jupyter/M06B-LLM-Malicious-Instruction-Defense.ipynb) | Attack paths, isolation, tool effects, and adversarial tests |
| M06C | [Private agents with Ollama notebook](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M06-Multi-Agent-Safety/Jupyter/M06C-PrivateAgents-Ollama.ipynb) | Data path, quality, latency, resources, and exposure |
| M06D | [Agent security and legal risks notebook](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M06-Multi-Agent-Safety/Jupyter/M06D-AgentSecurity-LegalRisks.ipynb) | Threats, harms, controls, evidence, ownership, and review |

## Further Reference Resources

- Use the OWASP taxonomy to identify technical attack patterns, then use the NIST AI RMF to place evidence, ownership, and review across the system lifecycle.
- Regulatory texts and voluntary standards change independently; verify the current version and applicability for the actual deployment context.

## Responsible Practice

Begin with the least complex architecture that meets the need. Limit roles, messages, shared state, credentials, and tool authority; protect logs and prompts; test compromised-role scenarios; and preserve a human path to stop consequential automation. Do not present agreement among agents as independent validation when they share models, prompts, data, or tools.

Risk analysis should name affected people and plausible harms, not only system assets. Record assumptions, residual risk, evidence gaps, accountable owners, and review triggers. Seek qualified privacy, security, or legal advice when the context requires it.

## Preparing for the Next Module

M07 evaluates model adaptation and serving choices. The decision starts from a measured baseline and asks whether prompting, retrieval, workflow controls, a different model, or fine-tuning addresses the observed gap. Any adaptation must preserve the security, provenance, and accountability established here.

[Previous: M05](../M05-Knowledge-Agents/README.md) | [Course home](../README.md) | [Next: M07](../M07-Model-Adaptation/README.md)

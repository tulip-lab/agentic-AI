[![Course home](https://img.shields.io/badge/FLIP-Agentic_AI-informational)](../README.md)

# M06: Multi-Agent Systems and Safety

Multiple specialised agents can divide work, critique outputs, and coordinate decisions. They can also amplify errors, obscure accountability, and expand the attack surface.

## Why This Module Matters

Collaboration patterns must be justified by task structure and tested against adversarial inputs. More agents do not automatically produce more reliable results.

## Learning Outcomes

You should be able to:

- **Design** roles, messages, termination conditions, and escalation paths for a multi-agent workflow.
- **Compare** collaborative and single-agent approaches using observable evidence.
- **Defend** a workflow against prompt injection and malicious instructions.
- **Analyse** privacy, security, data-poisoning, and legal risks.

## Core Concepts

Role decomposition; delegation; shared state; consensus and critique; termination; prompt injection; least privilege; local models; threat modelling; auditability.

## Sessions and Practicals

| Session | Focus | Lab |
| --- | --- | --- |
| M06A | Multi-agent collaboration | [Notebook](https://github.com/tulip-lab/agentic-AI-lab/tree/develop/M06-Multi-Agent-Safety/Jupyter/M06A-MultiAgent-Collaboration.ipynb) |
| M06B | Malicious-instruction and prompt-injection defence | [Notebook](https://github.com/tulip-lab/agentic-AI-lab/tree/develop/M06-Multi-Agent-Safety/Jupyter/M06B-LLM-Malicious-Instruction-Defense.ipynb) |
| M06C | Private agents with open-source models and Ollama | [Notebook](https://github.com/tulip-lab/agentic-AI-lab/tree/develop/M06-Multi-Agent-Safety/Jupyter/M06C-PrivateAgents-Ollama.ipynb) |
| M06D | Agent security, data poisoning, and legal risks | [Notebook](https://github.com/tulip-lab/agentic-AI-lab/tree/develop/M06-Multi-Agent-Safety/Jupyter/M06D-AgentSecurity-LegalRisks.ipynb) |

## Authoritative Resources

- [OWASP Top 10 for LLM Applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/) - use a current threat taxonomy for design review.
- [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) - connect technical controls with governance and monitoring.
- [Ollama documentation](https://docs.ollama.com/) - examine local model operation and its configuration boundaries.

## Responsible Practice

Assign every capability and final decision to an accountable owner. Separate untrusted content from instructions, constrain inter-agent messages, cap loops and cost, log material decisions, and test whether one compromised role can influence another.

## Offering and Assignment Note

Local legal or institutional policy belongs in an approved offering layer.

[Previous: M05](../M05-Knowledge-Agents/README.md) | [Course home](../README.md) | [Next: M07](../M07-Model-Adaptation/README.md)

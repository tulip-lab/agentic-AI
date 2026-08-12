[![Course home](https://img.shields.io/badge/FLIP-Agentic_AI-informational)](../README.md)

# M07: Model Adaptation and Multimodal AI

Agent behaviour can be changed through prompts, retrieval, fine-tuning, model choice, and multimodal components. This module develops evidence-based choices among those approaches.

## Why This Module Matters

Adaptation can improve task fit while introducing cost, forgetting, licensing, privacy, and evaluation risks. A technically possible method is not necessarily the appropriate one.

## Learning Outcomes

You should be able to:

- **Plan** a bounded fine-tuning experiment with a defensible baseline.
- **Measure** task improvement and unintended forgetting.
- **Compare** text, image, and speech generation workflows.
- **Select** an inference provider or local model using quality, latency, cost, and governance criteria.

## Core Concepts

Parameter-efficient fine-tuning; datasets and splits; catastrophic forgetting; diffusion; speech generation; multimodal evaluation; latency and throughput; provider comparison.

## Sessions and Practicals

| Session | Focus | Lab |
| --- | --- | --- |
| M07A | Fine-tuning large language models | [Notebook](https://github.com/tulip-lab/agentic-AI-lab/tree/develop/M07-Model-Adaptation/Jupyter/M07A-Finetuning-LLM.ipynb) |
| M07B | Fine-tuning and forgetting | [Notebook](https://github.com/tulip-lab/agentic-AI-lab/tree/develop/M07-Model-Adaptation/Jupyter/M07B-Finetuning-Forgetting.ipynb) |
| M07C | Diffusion customisation | [Notebook](https://github.com/tulip-lab/agentic-AI-lab/tree/develop/M07-Model-Adaptation/Jupyter/M07C-Diffusion-Customization.ipynb) |
| M07D | Speech generation | [Notebook](https://github.com/tulip-lab/agentic-AI-lab/tree/develop/M07-Model-Adaptation/Jupyter/M07D-Speech-Generation.ipynb) |
| M07E | Fast inference and model-provider comparison | [Notebook](https://github.com/tulip-lab/agentic-AI-lab/tree/develop/M07-Model-Adaptation/Jupyter/M07E-FastInference-ProviderComparison.ipynb) |

## Authoritative Resources

- [Hugging Face PEFT](https://huggingface.co/docs/peft/) - study parameter-efficient adaptation methods.
- [Hugging Face Diffusers](https://huggingface.co/docs/diffusers/) - inspect diffusion pipelines and customisation.
- [Hugging Face Transformers](https://huggingface.co/docs/transformers/) - connect model, tokenizer, training, and inference APIs.

## Responsible Practice

Verify dataset rights, consent, representation, and retention before adaptation. Evaluate both intended capability and regressions, disclose synthetic media appropriately, and record model and provider versions so evidence can be reproduced.

## Offering and Assignment Note

Compute budgets, approved providers, and evidence requirements are offering-specific.

[Previous: M06](../M06-Multi-Agent-Safety/README.md) | [Course home](../README.md) | [Next: M08](../M08-Agent-Engineering/README.md)

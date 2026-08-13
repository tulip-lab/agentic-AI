[![Course home](https://img.shields.io/badge/FLIP-Agentic_AI-informational)](../README.md)

# M07: Model Adaptation and Multimodal AI

## Module Overview

Agent behaviour can change through instructions, retrieval, tools, model choice, fine-tuning, or modality-specific components. This module uses the sequence **baseline -> adaptation choice -> training -> regression testing -> serving** to decide when changing model parameters is justified and how that change should be evaluated and operated.

Text, image, and speech systems share requirements for data rights, reproducibility, evaluation, and disclosure, but their outputs and harms are not interchangeable. The sessions therefore examine language-model adaptation and forgetting before treating diffusion images, generated speech, and inference infrastructure on their own terms.

## Connection to the Course

M06 showed that many failures originate in architecture, permissions, data, or governance rather than model capability. M07 begins from that diagnosis. Retrieval is preferable when knowledge must remain current and attributable; prompting or tools are preferable when behaviour can be expressed outside parameters; a different base model may outperform an adaptation effort.

When adaptation is warranted, it becomes one component of the agent system. M08 will integrate the resulting model with evaluation datasets, coding workflows, protocols, guards, monitoring, and product evidence. A successful training run is therefore an intermediate result, not production readiness.

## Learning Outcomes

By the end of this module, you should be able to:

- **Select** among prompting, retrieval, model replacement, and fine-tuning using measured gaps and constraints.
- **Plan** a bounded parameter-efficient adaptation experiment with held-out and regression evidence.
- **Evaluate** retention and plasticity and define rollback criteria.
- **Compare** image and speech generation using modality-appropriate quality, safety, provenance, and consent criteria.
- **Assess** hosted and local inference across quality, latency, throughput, cost, privacy, reliability, lock-in, and reproducibility.

## Module Map

| Session | Conceptual role | Decision focus |
| --- | --- | --- |
| M07A | Fine-tuning LLMs | Is parameter adaptation justified and testable? |
| M07B | Fine-tuning and forgetting | Did new capability damage retained behaviour? |
| M07C | Diffusion customisation | Which conditioning or parameter change fits the image goal? |
| M07D | Speech generation | Are intelligibility, naturalness, identity, and consent acceptable? |
| M07E | Fast inference and providers | Can the selected model be served reliably within constraints? |

## M07A: Fine-Tuning Large Language Models

### Chapter Overview

Fine-tuning updates model parameters using examples of desired behaviour. It may improve a stable task format, domain style, classification boundary, or response pattern. It is a weak mechanism for frequently changing facts, hard access rules, or deterministic computation, which are better handled through retrieval, policy, or tools.

### Key Ideas

An adaptation decision starts with a reproducible base-model baseline and a defined gap. Dataset examples must represent the intended task, edge cases, refusals, and output format without leaking evaluation cases. Training, validation, and test separation still apply. Data origin, consent, licence, personal information, and representational balance constrain what may be used.

Full fine-tuning changes all parameters and can require substantial compute and storage. Parameter-efficient methods such as low-rank adaptation train a smaller set of added or transformed parameters, making experiments easier to store and compare. Efficiency does not guarantee quality. Learning rate, number of updates, adapter rank, sampling, and prompt format can change both target behaviour and unintended regressions.

### From Concepts to Practice

The fine-tuning practical defines a baseline, a small adaptation objective, and held-out evaluation before training. Compare the adapted model with the unchanged base under identical prompts, record configuration and seeds where possible, and retain enough provenance to reproduce or reject the result.

### Suggested Readings

- Hu, E. J., et al. (2022). [LoRA: Low-rank adaptation of large language models](https://arxiv.org/abs/2106.09685). *ICLR 2022*. Used to introduce parameter-efficient adaptation and its resource trade-offs.
- Hugging Face. [PEFT](https://huggingface.co/docs/peft/index). Official reference for maintained parameter-efficient methods and adapters.
- Hugging Face. [Transformers training](https://huggingface.co/docs/transformers/training). Official guidance used to map dataset, trainer, and evaluation stages.

## M07B: Fine-Tuning and Forgetting

### Chapter Overview

Adaptation creates a retention-plasticity trade-off. Plasticity is the ability to learn the target behaviour; retention is the ability to preserve capabilities that should remain. Catastrophic forgetting describes substantial degradation on earlier knowledge or tasks after learning new data.

### Key Ideas

A target-task score alone cannot reveal forgetting. A regression set should sample preserved capabilities, safety behaviour, formatting, multilingual or subgroup cases, and ordinary requests affected by the change. Evaluate the base and adapted checkpoints on the same target and regression slices. Differences need uncertainty estimates or repeated evidence when generation is variable.

Mitigation may include lower update intensity, replay or mixed data, regularisation, adapter isolation, earlier stopping, or choosing retrieval instead. Checkpoints and data versions support comparison. Rollback criteria should be defined before deployment: a gain is not acceptable when a critical retained behaviour falls below its threshold.

### From Concepts to Practice

The forgetting practical compares pre- and post-adaptation behaviour across both new and retained tasks. Inspect individual regressions rather than averaging them away, identify which data or configuration might explain the trade-off, and make an explicit keep, revise, or rollback decision.

### Suggested Readings

- McCloskey, M., & Cohen, N. J. (1989). [Catastrophic interference in connectionist networks: The sequential learning problem](https://doi.org/10.1016/S0079-7421%2808%2960536-8). *Psychology of Learning and Motivation, 24*, 109-165. Used as the foundational retention and interference account.
- Hugging Face Hub. [Model cards](https://huggingface.co/docs/hub/model-cards). Official guidance used to document versions, evaluations, intended use, and limits.

## M07C: Diffusion Customisation

### Chapter Overview

Diffusion models learn to reverse a gradual noising process, commonly operating in a compressed latent representation for efficient image generation. Conditioning guides the reverse process using text, images, masks, structure, or other signals. Customisation may change only the prompt and conditioning inputs, attach a lightweight adapter, or update model parameters.

### Key Ideas

The least invasive method that meets the goal is usually easiest to evaluate and reverse. Prompt and reference conditioning preserve the base model but may offer limited consistency. Adapter or subject customisation can improve task fit while introducing memorisation, identity, style, and dataset-rights concerns. Training images need provenance, consent where relevant, and a clear relationship to the intended output.

Image evaluation combines task alignment, visual quality, diversity, consistency, artefacts, and human judgement. It should also inspect stereotypes, unsafe content, near-copying, misleading realism, and provenance signals. Text-model metrics do not transfer automatically to images, and one attractive sample is not distributional evidence.

### From Concepts to Practice

The diffusion practical compares a bounded customisation with an unchanged baseline across fixed prompts and seeds where supported. Review a set of outputs, disclose synthetic origin, record model and adapter versions, and separate subjective preference from task-specific acceptance criteria.

### Suggested Readings

- Ho, J., Jain, A., & Abbeel, P. (2020). [Denoising diffusion probabilistic models](https://arxiv.org/abs/2006.11239). *Advances in Neural Information Processing Systems 33*. Used to explain forward noising, reverse denoising, and conditional generation.
- Hugging Face. [Diffusers training overview](https://huggingface.co/docs/diffusers/training/overview). Official reference for current diffusion adaptation paths and resource considerations.

## M07D: Speech Generation

### Chapter Overview

Speech generation transforms text and control inputs into an acoustic representation and then a waveform. Text normalisation expands numbers, abbreviations, and symbols; an acoustic model predicts features such as mel spectrograms; a vocoder renders audio. Contemporary systems may combine stages, but the conceptual separation helps locate pronunciation, rhythm, speaker, and waveform errors.

### Key Ideas

Evaluation should distinguish intelligibility, naturalness, pronunciation, prosody, speaker similarity, latency, and robustness to unusual text. Listener studies require clear protocols and appropriate samples. Automatic measures can support comparison but do not fully capture human perception or whether a generated voice is suitable for its context.

Speaker conditioning creates identity risks. Voice data may be biometric or personally sensitive, and imitation can enable deception. Collection and use require permission and purpose limits; outputs may require disclosure or watermarking; access should be restricted; and interfaces should avoid implying a real person said generated words. Accessibility benefits should be designed with users rather than assumed.

### From Concepts to Practice

The speech practical inspects a small generation pipeline across ordinary and difficult text. Compare intelligibility and naturalness separately, record voice and model provenance, and evaluate consent and disclosure alongside audio quality. Do not treat a single pleasant clip as sufficient evidence.

### Suggested Readings

- Shen, J., et al. (2018). [Natural TTS synthesis by conditioning WaveNet on mel spectrogram predictions](https://doi.org/10.1109/ICASSP.2018.8461368). *Proceedings of ICASSP 2018*, 4779-4783. Used to separate text-to-acoustic prediction from waveform synthesis.

## M07E: Fast Inference and Model-Provider Comparison

### Chapter Overview

Serving turns a selected model into an operational dependency. Quality remains necessary, but deployment also depends on time to first output, end-to-end latency, throughput under concurrency, memory use, availability, cost, privacy, version stability, and support for required modalities and tool interfaces.

### Key Ideas

Local inference offers control and can reduce external data transfer, while placing hardware, scaling, patching, and incident response on the operator. Hosted providers may offer elastic capacity and managed infrastructure while introducing network dependency, data-processing terms, quotas, version change, and lock-in. Hybrid designs need clear routing and consistent evaluation.

Benchmarks should reflect prompt lengths, output lengths, concurrency, hardware, geography, and failure conditions of the intended workload. Throughput improvements can worsen tail latency; caching can improve cost while creating freshness or privacy concerns. Reproducibility requires model identifiers, revisions, serving version, quantisation, configuration, and test inputs.

### From Concepts to Practice

The provider-comparison practical measures the same bounded task across selected serving paths. Compare quality and operational evidence together, include failures and rate limits, and state which trade-off drives the recommendation. The fastest response is not the best choice when it cannot meet reliability, privacy, or quality requirements.

### Suggested Readings

- Kwon, W., et al. (2023). [Efficient memory management for large language model serving with PagedAttention](https://arxiv.org/abs/2309.06180). *Proceedings of SOSP 2023*, 611-626. Used to connect memory management with serving throughput.
- vLLM. [Documentation](https://docs.vllm.ai/en/latest/). Official reference for current serving configuration and performance concepts.

## Bringing the Module Together

Adaptation is an evidence-based choice, not a default stage. The unchanged baseline anchors comparison; the smallest suitable intervention limits cost and risk; training records establish reproducibility; regression sets protect retained behaviour; and serving tests determine whether gains survive operation. Image and speech sessions reinforce that evaluation must follow the actual modality and affected people.

## Practicals

The public Lab notebooks connect each decision to reproducible evidence.

| Session | Public practical | Evidence focus |
| --- | --- | --- |
| M07A | [Fine-tuning LLM notebook](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M07-Model-Adaptation/Jupyter/M07A-Finetuning-LLM.ipynb) | Baseline, dataset, adaptation configuration, and held-out results |
| M07B | [Fine-tuning and forgetting notebook](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M07-Model-Adaptation/Jupyter/M07B-Finetuning-Forgetting.ipynb) | Target gains, retained behaviour, regressions, and rollback |
| M07C | [Diffusion customisation notebook](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M07-Model-Adaptation/Jupyter/M07C-Diffusion-Customization.ipynb) | Conditioning, output sets, provenance, and image risks |
| M07D | [Speech generation notebook](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M07-Model-Adaptation/Jupyter/M07D-Speech-Generation.ipynb) | Intelligibility, naturalness, identity, consent, and disclosure |
| M07E | [Inference and provider comparison notebook](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M07-Model-Adaptation/Jupyter/M07E-FastInference-ProviderComparison.ipynb) | Quality, latency, throughput, cost, privacy, and reliability |

## Further Reference Resources

- Use the Hugging Face model-card guidance across all modalities to preserve intended use, version, evaluation, training-data information, and known limits.
- Use provider and serving documentation as versioned operational evidence; repeat benchmarks when models, hardware, configuration, or traffic patterns change.

## Responsible Practice

Verify dataset rights, consent, purpose, representativeness, retention, and security before training. Keep evaluation data independent, report negative and subgroup results, retain rollback artefacts, and avoid claiming that adaptation adds factual knowledge reliably when retrieval is the appropriate mechanism.

Generated images and speech need modality-specific safeguards, provenance, and disclosure. Serving choices should protect data in transit, at rest, and in logs; document external processors and versions; and monitor quality and cost drift after release.

## Preparing for the Next Module

M08 shifts from model capability to system and product readiness. It will define success before metrics, evaluate complete agent behaviour, integrate coding agents and MCP interfaces, place guards at observable events, and test whether a bounded user problem supports responsible operation.

[Previous: M06](../M06-Multi-Agent-Safety/README.md) | [Course home](../README.md) | [Next: M08](../M08-Agent-Engineering/README.md)

[![Course home](https://img.shields.io/badge/FLIP-Agentic_AI-informational)](../README.md)

# M02: AI Models and Representations

Agents inherit the strengths and failure modes of the models and representations beneath them. This module connects conventional prediction, deep learning, and vector representations to later retrieval and decision workflows.

## Why This Module Matters

Choosing an unsuitable representation or evaluation measure can make an agent appear fluent while its retrieval, classification, or ranking behaviour remains unreliable.

## Learning Outcomes

You should be able to:

- **Train** and interpret a baseline predictive model.
- **Compare** conventional and deep-learning workflows using appropriate evidence.
- **Construct** embeddings and compute similarity for a bounded retrieval task.
- **Evaluate** representation quality and identify misleading results.

## Core Concepts

Features and labels; train/test separation; loss and metrics; neural representations; embeddings; vector distance; dimensionality; retrieval trade-offs.

## Sessions and Practicals

| Session | Focus | Lab |
| --- | --- | --- |
| M02A | Regression and machine-learning foundations | [Notebook](https://github.com/tulip-lab/agentic-AI-lab/tree/develop/M02-AI-Modeling/Jupyter/M02A-Regression-ML-Basics.ipynb) |
| M02B | Deep-learning image classification | [Notebook](https://github.com/tulip-lab/agentic-AI-lab/tree/develop/M02-AI-Modeling/Jupyter/M02B-DeepLearning-ImageClassification.ipynb) |
| M02C | Embeddings, vector data, and similarity search | [Notebook](https://github.com/tulip-lab/agentic-AI-lab/tree/develop/M02-AI-Modeling/Jupyter/M02C-Embeddings-VectorData-Similarity.ipynb) |

## Authoritative Resources

- [scikit-learn user guide](https://scikit-learn.org/stable/user_guide.html) - connect estimators, preprocessing, validation, and metrics.
- [PyTorch tutorials](https://pytorch.org/tutorials/) - inspect end-to-end deep-learning workflows.
- [Sentence Transformers semantic search](https://www.sbert.net/examples/sentence_transformer/applications/semantic-search/README.html) - study embedding-based retrieval and similarity.

## Responsible Practice

Document training data, splits, metrics, and uncertainty. Similarity is not truth: test for representation bias, near-duplicate leakage, and plausible but irrelevant neighbours before an embedding index informs an action.

## Offering and Assignment Note

Offering-specific expectations are declared outside the common core. See the [offering index](../offerings/README.md).

[Previous: M01](../M01-Foundations/README.md) | [Course home](../README.md) | [Next: M03](../M03-Visual-Agents/README.md)

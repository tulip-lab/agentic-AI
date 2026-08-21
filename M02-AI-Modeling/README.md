[![Course home](https://img.shields.io/badge/FLIP-Agentic_AI-informational)](../README.md)

# M02: AI Models and Representations

## Module Overview

An agent does not reason directly over the world. It receives data through a representation, applies a model, and turns model outputs into decisions. This module develops that underlying chain as **data -> representation -> model -> metric -> decision**. It begins with supervised prediction, moves to learned image representations, and ends with embeddings for semantic similarity and retrieval.

The emphasis is not on collecting more algorithms. It is on making defensible choices: what a row or image represents, what target is being predicted, which evidence is held out, what a metric rewards, and whether a numerical result supports the intended use. These choices later determine the quality of retrieval, routing, memory, and tool selection in an agentic workflow.

## Connection to the Course

M01 introduced controlled model interaction, API boundaries, and the distinction between a generative model and an agent. M02 now examines the predictive and representational components beneath those systems. It supplies the vocabulary needed to diagnose whether a later agent failure originates in its data, model, representation, similarity measure, or decision rule.

M03 will place these components inside visible workflows. A learner who can trace model inputs, evaluation evidence, and representation limits is better prepared to decide what each workflow node should do and what must be tested at the connections between nodes.

## Learning Outcomes

By the end of this module, you should be able to:

- **Frame** a bounded supervised-learning problem using features, labels, baselines, and separated data splits.
- **Evaluate** regression and classification models with metrics appropriate to the decision context.
- **Explain** how neural networks learn representations and how transfer learning changes a modelling workflow.
- **Construct** and compare embeddings using explicit similarity measures.
- **Diagnose** misleading predictions or neighbours through error analysis, leakage checks, and subgroup inspection.

## Module Map

| Session | Conceptual role | Progression |
| --- | --- | --- |
| M02A | Regression and machine-learning foundations | Data, targets, baselines, splits, loss, and generalisation |
| M02B | Deep-learning image classification | Learned representations, optimisation, transfer, and error analysis |
| M02C | Embeddings and similarity search | Vector geometry, semantic retrieval, indexing, and relevance limits |

## M02A: Regression and Machine-Learning Foundations

### Chapter Overview

Supervised learning starts with a precise relationship between observations and targets. Features encode what the model may use; labels encode what it should learn to predict. Regression predicts a continuous value, while classification estimates a category or class-related score. In both cases, the task definition must precede model selection: a technically accurate prediction can still be useless if the target does not represent the real decision.

### Key Ideas

A baseline establishes the performance that added complexity must beat. A mean predictor, simple linear model, or transparent rule is often more informative than starting with an elaborate method. Training data is used to fit parameters; validation evidence supports choices; test data estimates performance after those choices are fixed. Leakage occurs when information from evaluation data, the future, or the target enters training and produces evidence that will not survive deployment.

Loss guides model fitting, whereas an evaluation metric expresses how results will be judged. Mean absolute error preserves the units of a regression target and treats deviations linearly; mean squared error penalises large deviations more strongly. Classification metrics reveal different consequences of false positives and false negatives. No metric is automatically correct: selection should follow the costs, class balance, and decision threshold of the use case. Generalisation is demonstrated by consistent performance on relevant unseen cases, not by low training loss.

### From Concepts to Practice

The practical develops a small regression workflow from inspection and preprocessing through baseline comparison and held-out evaluation. Treat every output as evidence for a modelling claim: describe the split, state the metric, compare against the baseline, and inspect individual errors rather than reporting one score. This habit becomes essential when later agent components appear plausible but fail on specific inputs.

### Suggested Readings

- scikit-learn developers. [Metrics and scoring: quantifying the quality of predictions](https://scikit-learn.org/stable/modules/model_evaluation.html). Official documentation used to connect metric definitions with prediction tasks and scoring conventions.

## M02B: Deep-Learning Image Classification

### Chapter Overview

Traditional feature engineering specifies useful input patterns in advance. Deep learning instead learns layers of representation while fitting the task. In image classification, early layers can respond to local visual structures, later layers combine them, and the final representation supports a decision. This makes the representation powerful, but it does not make the learned features transparent or universally reliable.

### Key Ideas

Convolutional networks exploit spatial structure through local filters and shared parameters. Optimisation adjusts parameters using gradients calculated from a training loss. Learning rate, batch construction, regularisation, and architecture affect whether training converges and whether the model generalises. Overfitting appears when training performance improves while validation performance stalls or deteriorates; it is evidence of a mismatch between learned detail and transferable structure.

Transfer learning begins from a model trained on a broader source task. Reusing or fine-tuning its representation can reduce data and compute requirements, but transfer is not guaranteed: source images, labels, and visual conditions may differ from the target setting. Error analysis should therefore examine confusion patterns, difficult examples, subgroup performance, and sensitivity to background or image quality. Aggregate accuracy can hide systematic failure.

### From Concepts to Practice

The image-classification practical makes the modelling lifecycle visible: transforms define the input representation, the network produces scores, the loss drives optimisation, and evaluation compares predictions with held-out labels. Record the baseline and training conditions, then inspect errors as images rather than only numbers. The goal is to explain what evidence would justify reuse of a learned representation in a later workflow.

### Suggested Readings

- LeCun, Y., Bengio, Y., & Hinton, G. (2015). [Deep learning](https://doi.org/10.1038/nature14539). *Nature, 521*, 436-444. Used to frame deep learning as representation learning across several model families.
- He, K., Zhang, X., Ren, S., & Sun, J. (2016). [Deep residual learning for image recognition](https://doi.org/10.1109/CVPR.2016.90). *Proceedings of CVPR 2016*. Used to connect architecture design with trainability and transferable visual representations.
- PyTorch. [Transfer learning for computer vision tutorial](https://docs.pytorch.org/tutorials/beginner/transfer_learning_tutorial.html). Official guidance used to compare fixed-feature and fine-tuning strategies.

## M02C: Embeddings, Vector Data, and Similarity Search

### Chapter Overview

An embedding maps an item such as a word, sentence, image, or user query to a vector. The coordinates are learned so that selected relationships become measurable in a shared space. Embeddings allow a system to compare meaning or usage without requiring exact keyword matches, which makes them a central representation for retrieval and agent memory.

### Key Ideas

Similarity is a design choice, not an intrinsic truth. Cosine similarity compares vector direction; dot product also reflects magnitude; Euclidean distance measures geometric separation. Results depend on the encoder, normalisation, training objective, domain, and query-document relationship. High dimensionality can capture many factors, but it complicates interpretation and makes exhaustive comparison expensive at scale. Approximate nearest-neighbour indexes trade exactness for speed and memory efficiency.

Semantic search embeds a query and candidate collection, retrieves nearby vectors, and ranks candidates for downstream use. Its evaluation should ask whether relevant items appear near the top, not merely whether neighbours look linguistically similar. Bias in training data can shape the geometry. Near duplicates can inflate apparent quality. A fluent but irrelevant neighbour can be especially harmful when passed to a generator, because downstream text may conceal the retrieval error.

### From Concepts to Practice

The practical compares vectors and similarity measures before using them for a bounded search task. Inspect both useful and irrelevant neighbours, vary the query wording, and distinguish representation failure from ranking or corpus failure. These observations prepare for M03, where an embedding node and vector store become only two parts of a larger retrieval-augmented workflow.

### Suggested Readings

- Mikolov, T., Chen, K., Corrado, G., & Dean, J. (2013). [Efficient estimation of word representations in vector space](https://arxiv.org/abs/1301.3781). Used to introduce distributed representations and geometric relationships.
- Reimers, N., & Gurevych, I. (2019). [Sentence-BERT: Sentence embeddings using Siamese BERT-networks](https://doi.org/10.18653/v1/D19-1410). *Proceedings of EMNLP-IJCNLP 2019*. Used to explain efficient sentence-level similarity search.
- Sentence Transformers. [Semantic search](https://www.sbert.net/examples/sentence_transformer/applications/semantic-search/README.html). Official documentation used to distinguish symmetric and asymmetric retrieval tasks.

## Bringing the Module Together

The three sessions describe one evidence chain. M02A asks whether data and targets support a predictive claim. M02B asks what representation a neural model learns and whether it transfers. M02C asks what relationships an embedding space preserves and whether neighbours are relevant. At every stage, evaluation connects a numerical output to an intended decision. A strong result at one stage cannot compensate automatically for an invalid assumption at another.

## Practicals

The Lab repository contains the canonical executable work. Each notebook turns one part of the module storyline into observable evidence.

| Session | Public practical | Evidence focus |
| --- | --- | --- |
| M02A | [Regression and ML basics notebook](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M02-AI-Modeling/Jupyter/M02A-Regression-ML-Basics.ipynb) | Baselines, splits, metrics, and error interpretation |
| M02B | [Deep-learning image classification notebook](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M02-AI-Modeling/Jupyter/M02B-DeepLearning-ImageClassification.ipynb) | Training behaviour, transfer, and image-level errors |
| M02C | [Embeddings and similarity notebook](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M02-AI-Modeling/Jupyter/M02C-Embeddings-VectorData-Similarity.ipynb) | Geometry, ranking, and misleading neighbours |

## Further Reference Resources

- scikit-learn. [User Guide](https://scikit-learn.org/stable/user_guide.html). Official reference for preprocessing, estimators, validation, inspection, and common modelling pitfalls.
- PyTorch. [Tutorials](https://docs.pytorch.org/tutorials/). Official examples that connect tensors, data loading, optimisation, evaluation, and model reuse.

## Responsible Practice

Record data origin, permitted use, preprocessing, split logic, model and library versions, metric definitions, and known exclusions. Test for leakage, duplicated records, imbalance, and performance differences across relevant groups. Do not infer sensitive attributes or deploy a proxy target without a justified purpose and appropriate governance.

Treat model outputs and similarity scores as uncertain evidence. Define what happens when confidence is low, examples are out of distribution, or retrieved neighbours conflict. Human review, abstention, or a safer default may be more appropriate than forcing every output into a decision.

## Preparing for the Next Module

M03 turns the components from this module into an inspectable context and orchestration system. Models become nodes, embeddings connect ingestion to retrieval, state carries information between steps, and evaluation shifts from one model to the behaviour of an entire workflow.

[Previous: M01](../M01-Foundations/README.md) | [Course home](../README.md) | [Next: M03](../M03-Context-Orchestration/README.md)

# Bio-Inspired Similarity Search & Clustering

Experiments with biologically inspired representation learning, similarity search, and clustering based on competitive hidden-unit learning.

This repository builds on Dmitry Krotov and John Hopfield's work on **unsupervised learning by competing hidden units** and explores two derived ideas:

1. using the learned synaptic representation for **BioHash-style similarity search**, and
2. adapting the learning dynamics into a **mean-shifted bio-inspired clustering algorithm**.

The clustering method is also explored as part of a fake-news classification pipeline.

## Motivation

Conventional similarity search and clustering methods usually begin with geometric objectives defined directly in feature space. This project asks whether a representation learned through a more biologically motivated competitive-learning rule can itself provide useful structure for retrieval and clustering.

The work began from the learning algorithm described in:

> D. Krotov and J. Hopfield, *Unsupervised Learning by Competing Hidden Units*, PNAS, 2019.

The original weight-learning implementation is not my work; attribution is documented below. My experiments extend the learned representation into retrieval and clustering workflows.

## What this repository explores

### 1. Bio-inspired representation learning

A set of higher-dimensional synaptic units is learned using a Hebbian-like competitive update rule.

### 2. Similarity search / BioHashing

The learned weights are used as a locality-sensitive representation for retrieving similar MNIST examples.

### 3. Mean-Shifted Bio-Clustering (MSBC)

I derived a clustering variant from the same learning dynamics. The number of synaptic units is interpreted as the number of clusters, while the origin is shifted toward the mean of the dataset. The resulting partitioning behaviour is based on angular structure relative to that shifted origin.

The repository includes comparisons against K-means to visualize how the induced partitions differ.

### 4. Fake-news classification experiment

The clustering approach is also applied to a fake-news dataset as an unsupervised representation/clustering step. In the experiment included here, the resulting pipeline reaches **~87% classification accuracy**.

Kaggle notebook:

https://www.kaggle.com/vanirudhsharma/unsupervised-bio-clustering-fake-news

Dataset:

https://www.kaggle.com/clmentbisaillon/fake-and-real-news-dataset

## Conceptual view

```text
Input vectors
    │
    ▼
Competitive / Hebbian-style weight learning
    │
    ├──────────────► Learned high-dimensional representation
    │                         │
    │                         ├──► Similarity search / BioHashing
    │                         │
    │                         └──► Mean-shifted clustering
    │                                      │
    │                                      └──► downstream classification experiment
    ▼
Analysis against conventional baselines
```

## Running the fake-news experiment

Download the fake/real news dataset and extract it to the input location expected by the notebook, then run the fake-news clustering/classification notebook.

The Kaggle version is the easiest way to reproduce the experiment because the dataset can be attached directly there.

## Attribution

### Original learning algorithm

The base competitive hidden-unit learning implementation originates from work by **Dmitry Krotov** and is distributed under the Apache 2.0 License.

Reference:

- Dmitry Krotov & John Hopfield, *Unsupervised Learning by Competing Hidden Units*, PNAS (2019)
- MIT 6.S191 lecture material discussing the approach

### Extensions in this repository

**V. S. S. Anirudh Sharma, 2021**

- similarity-search experiments using learned biological-style representations
- BioHashing-oriented retrieval experiments
- mean-shifted bio-inspired clustering formulation
- clustering visualization against K-means
- fake-news application experiment

## Research status

This is an exploratory research repository rather than a production library. The clustering method and evaluation were developed as experiments, and the results should be interpreted in that context rather than as a general benchmark claim.

## Author

**V. S. S. Anirudh Sharma**  
AI/ML Engineer · Researcher · Builder

[GitHub](https://github.com/showman-sharma) · [LinkedIn](https://www.linkedin.com/in/v-s-s-anirudh-sharma-ab405617b/)

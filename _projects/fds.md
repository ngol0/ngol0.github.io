---
layout: page
title: Federated Dataset Simulation (FDS)
description: A framework for creating and evaluating heterogeneous data partitions for federated learning research.
img: assets/img/vlm_pipeline.svg
importance: 1
category: machine learning and AI
related_publications: false
---

Federated learning (FL) assumes that data is distributed across multiple clients — but in practice, each client's data reflects its own local context, making it non-IID (non-independent and identically distributed). Designing FL algorithms that handle this heterogeneity requires realistic, controlled data partitions to experiment with.

**FDS** is a framework for creating such partitions and measuring their heterogeneity. It supports multiple partitioning strategies:
- **VLM-based**: criterion-driven partitioning using vision-language models
- **Embedding-based**: semantic clustering using foundation model embeddings (DINOv2, CLIP, SigLIP)


## Motivation

Federated learning is well-established, and many tools provide federated splits, most notably Dirichlet-based label splitting. 

However, these approaches primarily simulate heterogeneity through **label distribution skew**: clients differ in how many samples of each class they hold. This is useful but arguably artificial because real-world clients don't just have class imbalances, they hold data that is *visually and semantically* distinct. 

FDS addresses this by partitioning data based on **semantic content** — using foundation model embeddings or VLM-guided annotation, and providing an evaluation framework to measure whether the resulting heterogeneity is meaningfully different from the Dirichlet baseline across both label and feature distributions.

## Partitioning Strategies

### VLM-Based Partitioning
A multi-step LLM + VLM pipeline that annotates images along a chosen visual criterion (e.g. main object, dominant color, location, time of day), then groups images by the resulting categories to form client partitions. Supported datasets include Tiny ImageNet, Food-101, ADE20K, and PascalVOC.

*Pipeline based on [ICTC](https://github.com/sehyunkwon/ICTC) by Kwon et al.*

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/vlm_pipeline.svg" title="VLM partitioning pipeline" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    The four-step VLM pipeline: images are annotated by a VLM, categories are proposed and assigned by an LLM, then grouped into non-IID client partitions.
</div>


### Embedding-Based Partitioning
Uses foundation model embeddings (DINOv2, CLIP, SigLIP) to group semantically similar images together, assigning each cluster to a client. This creates a more realistic form of heterogeneity than label skew alone — clients hold data that is visually and conceptually coherent, not just class-imbalanced.

The pipeline:
1. Extract image embeddings from a pretrained foundation model
2. Pool tokens (CLS, mean, max, GeM, last-K layer, spectral sharpening)
3. Optionally reduce dimensionality with UMAP
4. Cluster with HDBSCAN, k-means, k-NN graph, or spectral clustering
5. Assign clusters to clients

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/embedding_pipeline.svg" title="Embedding-based partitioning pipeline" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    The embedding pipeline: foundation model embeddings are pooled, optionally reduced with UMAP, clustered into semantic groups, and assigned to FL clients. The heterogeneity parameter β controls cluster granularity.
</div>


## Evaluation

The evaluation module provides 17 heterogeneity metrics organised into three tiers:

**Label distribution** — Jensen-Shannon Divergence, Total Variation, and per-client JSD against the global distribution. These operate on class label counts alone and serve as the standard FL benchmark metrics.

**Feature distribution** — FID, MMD, Sliced Wasserstein, Energy Distance, Kolmogorov-Smirnov test, Vendi score, k-NN separability, centroid distance, feature variance, and intrinsic dimensionality. These extract visual embeddings via the same foundation model backends used in partitioning and measure distributional distance in feature space. GPU-accelerated via FAISS.

**Gradient diversity** — Cosine similarity, gradient variance, conflict score, and spectral diversity computed from client gradient tensors during FL training rounds. These capture whether data heterogeneity actually affects gradient alignment during training.

Embeddings are shared with the partitioning pipeline via a persistent disk cache, so features computed during split generation are reused at evaluation time at no extra cost.

Early results show that VLM-guided partitioning creates non-IID splits with 2× higher heterogeneity than Dirichlet sampling while preserving semantic coherence.

## Implementation Status

The core data infrastructure is complete: partitioning strategies, embedding extraction, and the heterogeneity metric library are all implemented and tested (540+ tests across 17 test files). Substantial work is still ongoing — FL training experiments, systematic metric gathering across partition configurations, ablation studies, theoretical grounding, and manuscript writing are all in progress.


## Contributors

- **Vasilis Siomos**, PhD — City St George's University of London: project lead, contributing to embedding-based pipeline implementations, evaluation and federated learning training steps
- **Lam Ngo**, MSc — City St George's University of London: research engineer, contributing to VLM-guided pipeline implementations and research
- **Dr. Giacomo Tarroni** — City St George's University of London: supervisor

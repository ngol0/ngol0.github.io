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

**FDS** is a framework for creating such partitions and measuring their heterogeneity. It supports multiple partitioning strategies.


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
2. Pool tokens (CLS, mean, GeM, spectral sharpening)
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

## Status

The partitioning pipelines are complete. Evaluation of the resulting partitions — comparing heterogeneity across methods using label and feature distribution metrics — is currently ongoing.

## Links

- [GitHub (public)](https://github.com/ngol0/FDS-public)

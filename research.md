---
layout: default
title: "Research"
nav_order: 2
permalink: /research/
---

# Research
The recent breakthroughs in artificial intelligence (AI) have been achieved through training large neural network (NN) models on enormous amount of data, which eventually requires a significant amount of training compute. Moreover, serving these large models also requires an enormous amount of memory and compute during inference. Therefore, for the sustainable growth of the capabilities of the current and future AI models, efficient training and inference methods need to be explored. From this perspective, my current research focuses on developing efficient training and inference methods for state-of-the-art AI models in a theoretically principled way. In other words, we want to develop **efficient training and inference methods for large AI models with theoretical performance guarantees**.

One of the key techniques for efficient training of large AI models is the sparse **Mixture-of-Experts** (MoE). Despite the empirical success of MoE, the theoretical understanding of the architecture is limited. Moreover, due to their excellent scalability, the MoE models are enormous in size and hence require huge memory and compute during inference. My recently completed research projects focus on understanding the training dynamics of the architecture under different learning scenarios, and using the analytical insights to design efficient inference methods for such models.

**Provable Training Efficiency of the Sparse MoE Models**

Scaling model size is computationally expensive. Naively increasing the model size proportionally increases the training compute requirements for dense models. MoE models are introduced to efficiently scale the model size with only a sublinear increase in training compute. Instead of processing every input by every parameter of the model, the architecture routes (via a *router*) different inputs to different groups of parameters (each parameter group is referred to as an *expert*) for processing. Modern MoE models employ *patch/token-level routing*, where instead of routing the whole input sequence (e.g., an image for vision tasks, or a sequence of tokens in NLP tasks) to an expert, different patches/tokens of the sequence are routed to different experts. The patch/token-level routing demonstrates significant empirical success (e.g., 20% reduction of training FLOPs compared to dense models). Despite the empirical success, theoretically, the architecture remains mysterious due to its superior performance despite incorporating sparse computation. In this project, we address the following questions theoretically:

<p align="center">
<b><i>Why does the MoE model save training compute? How much computational resource does MoE save?</i></b>
</p>

Our contributions:

1. This project provides the first theoretical generalization analysis of patch-level MoE (pMoE). Our analysis on pMoE with two-layer CNNs as experts reveals that the architecture can achieve the same generalization performance as conventional CNN while reducing the sample complexity (the required number of training samples to learn a proper model) and model complexity. Specifically, we prove that as long as $l$ is larger than a certain threshold, pMoE reduces the sample complexity and model complexity by a factor polynomial in $n/l$, indicating an improved generalization with a smaller $l$.

---
layout: default
title: "Research"
nav_order: 2
permalink: /research/
---

<script id="MathJax-script" async
  src="https://cdn.jsdelivr.net/npm/mathjax@4/es5/tex-mml-chtml.js">
</script>
<script>
  window.MathJax = {
    tex: { inlineMath: [['$', '$'], ['\\(', '\\)']] }
  };
</script>

# Research
The recent breakthroughs in artificial intelligence (AI) have been achieved through training large neural network (NN) models on enormous amount of data, which eventually requires a significant amount of training compute. Moreover, serving these large models also requires an enormous amount of memory and compute during inference. Therefore, for the sustainable growth of the capabilities of the current and future AI models, efficient training and inference methods need to be explored. From this perspective, my current research focuses on developing efficient training and inference methods for state-of-the-art AI models in a theoretically principled way. In other words, we want to develop **efficient training and inference methods for large AI models with theoretical performance guarantees**.

One of the key techniques for efficient training of large AI models is the sparse **Mixture-of-Experts** (MoE). Despite the empirical success of MoE, the theoretical understanding of the architecture is limited. Moreover, due to their excellent scalability, the MoE models are enormous in size and hence require huge memory and compute during inference. My recently completed research projects focus on understanding the training dynamics of the architecture under different learning scenarios, and using the analytical insights to design efficient inference methods for such models.

**Provable Training Efficiency of the Sparse MoE Models**

Scaling model size is computationally expensive. Naively increasing the model size proportionally increases the training compute requirements for dense models. MoE models are introduced to efficiently scale the model size with only a sublinear increase in training compute. Instead of processing every input by every parameter of the model, the architecture routes (via a *router*) different inputs to different groups of parameters (each parameter group is referred to as an *expert*) for processing. Modern MoE models employ *patch/token-level routing*, where instead of routing the whole input sequence (e.g., an image for vision tasks, or a sequence of tokens in NLP tasks) to an expert, different patches/tokens of the sequence are routed to different experts. The patch/token-level routing demonstrates significant empirical success (e.g., 20% reduction of training FLOPs compared to dense models). Despite the empirical success, theoretically, the architecture remains mysterious due to its superior performance despite incorporating sparse computation. In this project, we address the following questions theoretically:

<p align="center">
<b><i>Why does the MoE model save training compute? How much computational resource does MoE save?</i></b>
</p>

Our contributions:

1. We provide the first theoretical generalization analysis of MoE with patch/token-level routing. Our analysis shows that the architecture can achieve the same generalization performance as its dense counterpart while reducing the computational complexity by a polynomial order of $n/l$. Here, $n$ is the sequence length and $l$ is the number of patches/tokens processed by each expert.
2. We theoretically prove that the router of an MoE layer learns to dispatch similar patches/tokens to the same expert. This allows the experts to learn with lower complexity compared to dense models, as the interference from dissimilar patches/tokens is greatly reduced. We also prove that the complexity of learning the router to achieve this discriminative property is insignificant compared to learning the experts or dense models.
3. We empirically demonstrate the sample-efficient mode of operation of patch/token-level MoE for the first time in the literature with CNN type architecture.  

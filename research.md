---
layout: default
title: "Research"
nav_order: 2
permalink: /research/
---
<script type="text/javascript" id="MathJax-script" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
  </script>

<script>
  MathJax = {
    tex: {
      inlineMath: [['$', '$'], ['$`', '`$'], ['\\(', '\\)']],
      displayMath: [['```math', '```'], ['$$', '$$'], ['\\[', '\\]']]
    }
  };
</script>
# Research
The recent breakthroughs in artificial intelligence (AI) have been achieved through training large neural network (NN) models on enormous amount of data, which eventually requires a significant amount of training compute. Moreover, serving these large models also requires an enormous amount of memory and compute during inference. Therefore, for the sustainable growth of the capabilities of the current and future AI models, efficient training and inference methods need to be explored. From this perspective, my current research focuses on developing efficient training and inference methods for state-of-the-art AI models in a theoretically principled way. In other words, we want to develop **efficient training and inference methods for large AI models with theoretical performance guarantees**.

One of the key techniques for efficient training of large AI models is the sparse **Mixture-of-Experts** (MoE). Despite the empirical success of MoE, the theoretical understanding of the architecture is limited. Moreover, due to their excellent scalability, the MoE models are enormous in size and hence require huge memory and compute during inference. My recently completed research projects focus on understanding the training dynamics of the architecture under different learning scenarios, and using the analytical insights to design efficient inference methods for such models.

**Provable Training Efficiency of the Sparse MoE Models**

Scaling model size is computationally expensive. Naively increasing the model size proportionally increases the training compute requirements for dense models. MoE models are introduced to efficiently scale the model size with only a sublinear increase in training compute. Instead of processing every input by every parameter of the model, the architecture routes (via *routers*) different inputs to different groups of parameters (each parameter group is referred to as an *expert*) for processing. Modern MoE models employ *patch/token-level routing*, where instead of routing the whole input sequence (e.g., an image for vision tasks, or a sequence of tokens in NLP tasks) to an expert, different patches/tokens of the sequence are routed to different experts. The patch/token-level routing demonstrates significant empirical success (e.g., 20% reduction of training FLOPs compared to dense models). Despite the empirical success, theoretically, the architecture remains mysterious due to its superior performance despite incorporating sparse computation. In this project, we address the following questions theoretically:

<p align="center">
<b><i>Why does the MoE model save training compute? How much computational resource does MoE save?</i></b>
</p>

<div style="display:flex; gap:20px; justify-content:center; margin:2em 0;">
  <figure style="width:30%; text-align:center;">
    <img src="/assets/pMoE_c_1.png" style="max-width:100%;">
  </figure>

  <figure style="width:30%; text-align:center;">
    <img src="/assets/o_1.png" style="max-width:100%;">
  </figure>

  <figure style="width:30%; text-align:center;">
    <img src="/assets/o_2.png" style="max-width:100%;">
  </figure>
</div>

<figure style="text-align:center; margin: 2em 0;">
  <img src="/assets/complexity_pmoe.png"
       alt="Training efficiency of sparse MoE"
       style="max-width:80%; height:auto;">
</figure>

<div style="display:flex; gap:20px; justify-content:center; margin:2em 0;">
  <figure style="width:30%; text-align:center;">
    <img src="/assets/celeba_multiclass_plot_2.png" style="max-width:100%;">
  </figure>

  <figure style="width:30%; text-align:center;">
    <img src="/assets/celeba_multiclass_training_flops_plot_2.png" style="max-width:100%;">
  </figure>
</div>

Our contributions:

1. We provide the first theoretical generalization analysis of MoE with patch/token-level routing. Our analysis shows that the architecture can achieve the same generalization performance as its dense counterpart while reducing the computational complexity by a polynomial order of $$n/l$$. Here, $$n$$ is the sequence length and $$l$$ is the number of patches/tokens processed by each expert.
2. We theoretically prove that the routers of an MoE layer learn to dispatch similar patches/tokens to the same expert. This allows the experts to learn with lower complexity compared to dense models, as the interference from dissimilar patches/tokens is greatly reduced. We also prove that the complexity of learning the router to achieve this discriminative property is insignificant compared to learning the experts or dense models.
3. We empirically demonstrate the sample-efficient mode of operation of patch/token-level MoE for the first time in the literature with CNN type architecture.

**Provably Effective Expert-Pruning for Efficient Inference of MoE Models**

As MoE models are efficient to train, they possess incomparably large model sizes. Serving these models requires a huge amount of GPU memory. However, during pretraining, experts learn diverse features. Not all of the experts are useful for a downstream task. In this project, we theoretically investigate the model's learning dynamics during finetuning on a particular downstream task to identify the post-finetuning model property that can appropriately determine the relevant experts for the task.

Our investigation reveals that the experts learning relevant features for the downstream task undergo a larger change in their router norm compared to irrelevant experts during finetuning. Therefore, pruning the experts with a lower change in router norm during finetuning can provably maintain model performance while reducing the model size significantly.

Our contributions:

1. We provide the first provably effective pruning metric for expert-pruning in finetuned MoE models. Our work not only provides the theoretical generalization guarantee for the pruned model, but also describes why and how the different experts become relevant/irrelevant to the task.
2. We empirically demonstrate the effectiveness of the proposed pruning method on state-of-the-art large MoE models for various benchmark tasks.

{% comment %}
**Efficient Quantization of MoE Models with Theoretical Generalization Guarantees**

Post-training weight quantization has been explored to address the memory requirement of large MoE models. However, a uniform bit-width for all experts significantly degrades performance for ultra-low-bit (e.g., under 3-bit). On the other hand, the diversity of the experts suggests greater potential for expert-wise mixed-precision (i.e., varying bit-width across experts) in the ultra-low-bit scenario. Recent works explored in this direction. However, their approaches are calibration data-dependent heuristics, require substantial computation for bit-width allocation, and overlook the varying sensitivity of model performance (e.g., model accuracy) to the quantization of different experts.

In this project, through the lens of feature learning dynamics of MoE, we theoretically investigate why and how we can vary bit-width across experts. Our theoretical analysis reveals that, among the experts with maximum intra-neuron weight variance within an acceptable range, the experts with lower router norm change during training exhibit weaker activation (as they learn less frequent but critical features), and hence, model performance is more sensitive to the quantization of these experts. Furthermore, the experts which maximum intra-neuron weight variance that is unusually large, inject significant quantization noise into the model. Based on these theoretical insights, we design a two-step expert ranking strategy for allocating experts in higher ranks to higher bit-width. Specifically, we primarily place the experts with lower router norm changes to higher ranks, and then re-order some lower-rank experts to higher ranks if their maximum intra-neuron weight variance is significantly larger.

Our contributions:

1. Our proposed expert-wise mixed precision strategy is theoretically-grounded, providing insights about why and how we can vary bit-width across experts.
2. Our empirical results demonstrate superior performance over other expert-wise and non-expert-wise mixed-precision baselines.
3. Our method reduces the inference computation compared to prior methods, and incurs negligible computational overhead to determine expert bit-widths, while the alternative methods require significant GPU computation.
{% endcomment %}

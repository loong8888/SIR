<h1 align="center">SIR: Self-supervised Image Rectification via Seeing the Same Scene from Multiple Different Lenses
</h1>

<p align="center">
<a href="https://arxiv.org/abs/2011.14611"><img  src="https://img.shields.io/badge/arXiv-Paper-<COLOR>.svg" ></a>
</p>


<h4 align="center">This is the official repository of the paper <a href="https://arxiv.org/abs/2011.14611">SIR</a>.</h4>
<h5 align="center"><em>Jinlong Fan, Jing Zhang, Dacheng Tao</em></h5>

<p align="center">
  <a href="##Introduction">Introduction</a> |
  <a href="#Method">Method</a> |
  <a href="#Results">Results</a> |
  <a href="#Statement">Statement</a>
</p>

## Introduction

<p align="justify">
Deep learning has demonstrated its power in image rectification by leveraging the representation capacity of deep neural networks via supervised training based on a large-scale synthetic dataset. However, the model may overfit the synthetic images and generalize not well on real-world fisheye images due to the limited universality of a specific distortion model and the lack of explicitly modeling the distortion and rectification process. In this paper, we propose a novel <strong>self-supervised image rectification (SIR)</strong> method based on an important insight that the rectified results of distorted images of a same scene from different lens should be the same. Specifically, we devise a new network architecture with a shared encoder and several prediction heads, each of which predicts the distortion parameter of a specific distortion model. We further leverage a differentiable warping module to generate the rectified images and re-distorted images from the distortion parameters and exploit the intra- and inter-model consistency between them during training, thereby leading to a self-supervised learning scheme without the need for ground-truth distortion parameters or normal images. Experiments on synthetic dataset and real-world fisheye images demonstrate that our method achieves comparable or even better performance than the supervised baseline method and representative state-of-the-art methods. Self-supervised learning also improves the universality of distortion models while keeping their self-consistency.
</p>


## Method
![](files/NN.png)
<p align="justify"> 
Unlike existing supervised methods, the proposed self-supervised method does not need any ground truth distortion parameters, distortion field, or the normal image to train the network. The 
framework is illustrated in the above figure. During training, $s$ distorted images are synthesized from one normal image realB using d distortion models, so totally there will be d ∗ s images in 
each batch. For clarity, we only show two samples for each model here, as in our experiment setting. Each head shares the same distortion
model (in the same color). The input images are fed into a shared encoder, i.e. ResNet-50. Next, the prediction head for each model (i.e. hi) predicts the distortion parameters (i.e. Ki) under 
that distortion model (i.e. Di) accordingly. Finally, the forward warping module (i.e. fi) generates the rectified images (e.g. Bi). A1 i means the sample is under distortion model Di with 
parameter k1. Similarly, ki1 is the distortion parameter k1 defined under model Di. Bi1 is the rectified result of $A^1_i$.
</p>



We also generate the wordcloud of the prompts, attributes and relationships in RefMatte as belows. As can be seen, the dataset has a large portion of human and animals since they are very common in the image matting task. The most frequent attributes in RefMatte are *male, gray, transparent,* and *salient*, while the relationship words are more balanced.

## Results

We show some examples of our test results on RefMatte test set and RefMatte-RW100 by our CLIPIMat given text inputs and the images under both prompt- and expression- based setting.

<img src="files/metrics.png">
<img src="files/metrics_2.png">
<img src="files/syn_data.png">
<img src="files/real_fisheye.png">


## Statement

If you are interested in our work, please consider citing the following:
```
@article{jfan2021sir,
  title={SIR: Self-supervised Image Rectification via Seeing the Same Scene from Multiple Different Lenses},
  author={Jinlong Fan and Jing Zhang and Dacheng Tao},
  journal={ArXiv},
  year={2021},
  volume={abs/2011.14611}
}

```

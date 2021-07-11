---
layout: post
title: Learning To style Paint with RL
cover-img: /assets/img/rlwall.jpg
subtitle:  Style transfer painting using Reinforcement Learning
tags: [RL, Deep Learning, GAN, generative art]
image_cover : /assets/img/four-rl.gif
comments: true
---

# Learning To Paint with RL

This problem aims at training an agent to generate paintings using stroke based sequential actions. We plan to break down the given target image into a set number of strokes, using a RL agent, which can generate a painted image. Compare On Policy (PPO) and Off Policy (DDPG) methods for solving the problem. We also aim at incorporating style transfer while painting.


## Applications
- Learning to Paint is a complex process and often requires considerable time and effort to master the art
- Making an AI agent learn how to reproduce an existing painting by decomposing it into a sequence of brush strokes across the canvas.
- The training process of such an agent does not require any considerable vast experience.
- The problem statement has multiple applications in real life such as handwriting reproduction, painting restoration etc.
- Additionally using concepts from neural style transfer, the reward for the agent can be adjusted in order to incorporate style elements from a reference image.

For results, and presentation see  [this](https://docs.google.com/presentation/d/12qKSNMhIWJkjU_1e4IlkE3kd8cIfE_pRqcq-_oIeAsw/edit?usp=sharing)


### Quickstart 

For training and testing on MNIST

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1wHKp5FlVWwmLKnhxoAHv1JGKkZm6yiGN?usp=sharing)

For training and testing on celeb

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1fVujftlc5I6oAxavgz0TFMdjy77PNCbl?usp=sharing)

For training Style transfer RL on MNIST

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1IBQIrQ3Hg3exDMVc7IxHnfQhaAeTI6mK?usp=sharing)

## Style transfer
![Alt text](https://github.com/asmitks/StylePaintingwithRL/blob/main/images/Blank%20diagram.jpeg?raw=true)
## Demo
### Style Transfer on MNIST
![Alt text](https://github.com/asmitks/StylePaintingwithRL/blob/main/images/ezgif-6-f82684ab87d4.gif?raw=true)
### Using DDPG on CelebA
![Alt text](https://github.com/asmitks/StylePaintingwithRL/blob/main/images/ezgif.com-gif-maker.gif?raw=true)

### Using PPO on MNIST
![Alt text](https://github.com/asmitks/StylePaintingwithRL/blob/main/images/ppo_3.gif?raw=true)

## Version Info

Version : 1.0.0

## Authors

* **Asmit Kumar Singh** - *IIIT-Delhi* - [Other Work](https://github.com/asmitks)
* **Suchet Aggarwal** - *IIIT-Delhi* - [Other Work](https://github.com/Suchet-Agg)
* **Pragya Sethi** - *IIIT-Delhi* - [Other Work](https://github.com/Pragya2804)

## Acknowledgments

* [Code for DDPG and environment](https://github.com/megvii-research/ICCV2019-LearningToPaint)

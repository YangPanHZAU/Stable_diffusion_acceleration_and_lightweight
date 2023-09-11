# Stable_diffusion_acceleration_and_lightweight
Fewer parameters and inference time steps,more aesthetically results

## Introduction

### Text to Image(T2I):
Text-to-image uses AI to understand your words and convert them to a unique image each time.
![introduction](asset/fig1.jpg)

### The development of T2I model:
<a href='https://github.com/CompVis/stable-diffusion'>Stable diffusion</a>: a milestone work on latent space. A framework that trains the diffusion models on latent space, which is a scaled-up version
of Latent Diffusion Model (LDM).
![T2I model](asset/fig2.jpg)

### Relate work: On distillation of guided T2I diffusion models:

#### <a href='https://arxiv.org/abs/2210.03142'>W-condition(CVPR 2023 2023 CVPR Award Candidate)</a>

Two-stage distillation model:

stage1: Guidance weight stage, Guidance weight w as extra parameter to the UNet to prevent positive prompts and negative prompts of the Classifier-Free Guidance (CFG).

stage2: Progressive distillation, the progress distillation pipeline similarity the work is employ to decrease the inference steps.
![T2I model](asset/w-condition.jpg)

#### <a href='https://arxiv.org/abs/2306.00980'>Snapfusion</a>

stage1:In direct distillation, the teacher only distills 
once (16 → 8).Balancing the CFG-Aware loss and Vanilla step distillation loss for step reduction
![T2I model](asset/snapfusion.jpg)

## Our Framework

### Step distillation for guided T2I diffusion models:

### Algorithm Description:

## Result

### Zero-shot quantitative results on MSCOCO 2017 caption dataset and HPSv2 dataset

### Visualization results

## Reference
https://snap-research.github.io/SnapFusion/

https://github.com/Nota-NetsPresso/BK-SDM

## TODO List

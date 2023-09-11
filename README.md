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

#### Challenge

1. An extra multi-stage distillation pipeline will lead to accumulated error.512→256→128→64→32→16→8
   
2. Poor scalability:simple UNet output with v-prediction, the w-condition and snapfusion are based on diffusion model outputs in the form of v-prediction predictions(stabel diffusion v2.0).But stable diffusion v1.x are not suitable.

The prediction type of stable diffusion consist of 'epsilon','sample', and 'v_prediction'. More information can be found in <a href='https://arxiv.org/pdf/2010.02502.pdf'>Progressive distillation</a>.

## Our Framework

### Step distillation for guided T2I diffusion models:

### Algorithm Description:

## Result
### Generation Details
Images of size 512 × 512 are generated from the publicly released model with the DPM Solver++ sampler, 8, 16 and 20 sampling steps, and
a guidance scale of 7.5.
For MSCOCO 2017 caption dataset, the first prompt of each image are selected for zero-shot inference. 

For <a href='https://github.com/tgxs002/HPSv2'>HPSv2</a> dataset, we infer the test dataset benchmark include the four types prompts,"Animation", "Concept-art", "Painting", and "Photo".

### Zero-shot quantitative results on MSCOCO 2017 caption dataset and HPSv2 dataset
![T2I model](asset/fid_is_hpsv2.jpg)
### Visualization results
![T2I model](asset/result.jpg)
## Reference
https://snap-research.github.io/SnapFusion/

https://github.com/Nota-NetsPresso/BK-SDM

https://github.com/tgxs002/HPSv2

## TODO List

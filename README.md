
# Enhanced AI-trained Reward Model

Branding new improvements are being made, current stage not yet ready for utilization.

## Detailed Description

This project revolves around implementing a prime reward model that leverages RWKV models. The primary objectives of our project include:

- Demonstrating the ability of RWKV models to effectively learn reward functions
- Utilizing the trained reward model for training an advance policy using RL algorithms which encourages quality answers and diverse trajectories from the base RWKV model.

## Steps for Experimentation

### 1. Environment Setup

Initial setup includes the installation of `rwkv` official pypi, `datasets` and `pytorch` via pip install.

```
pip install rwkv
pip install datasets
pip install torch
```

### 2. Weight Downloading

For our experiment, we are opting for a smaller RWKV model with 430M parameters for quick training and testing via a single GPU. The relevant weight can be downloaded at [this page](https://huggingface.co/BlinkDL/rwkv-4-pile-430m/resolve/main/RWKV-4-Pile-430M-20220808-8066.pth)

### 3. Execution of Experiment

```
python train.py
```

The reward dataset being utilized in this experiment is derived from [here](https://huggingface.co/datasets/yitingxie/rlhf-reward-datasets). It includes 100 data points from the train and 20 from the validation to demonstrate that the reward model is capable of predicting reward values.

## Reward Model Details

Simply put, the process involves the reward model reading the prompt and output from another model, then rating the output from 1 to -1 for 'accept' or 'reject' respectively. Based on the dataset utilized, each prompt consists of two answers, of which one is rated as 'accept' and the other is rated as 'reject' by human raters. The goal is to develop a reward model that predicts these human ratings.

## Upcoming Work

1. The current reward model is not perfectly trained; only the last few layers have been trained.
2. qLora will be implemented on this reward model for complete trainability.
3. The dataset used for illustration currently lacks adequate diversity and size. More data will be collected for enhanced training of the reward model.
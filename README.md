# Fine-Tuning LLaMA-7B for Code Generation Using LoRA Layers

This repository contains the code and steps for fine-tuning the LLaMA-7B (LLaMA: Large Language Model Meta AI) model for code generation tasks using LoRA (Low-Rank Adaptation of Large Language Models) layers. In this project, only the LoRA layers were trained, while all other layers in the model were frozen.

## Overview

- **Model Used**: [LLaMA-7B](https://huggingface.co/Enoch/llama-7b-hf)
- **Task**: Code Generation
- **Dataset**: [codeparrot/codeparrot-clean](https://huggingface.co/datasets/codeparrot/codeparrot-clean)
- **Fine-tuning Method**: LoRA Layers (All other layers frozen)

LoRA allows for efficient adaptation of large models by introducing additional trainable parameters (low-rank matrices) into the model, reducing computational and memory overhead compared to full fine-tuning.

## Table of Contents

- [Introduction](#introduction)
- [Dataset](#dataset)
- [Fine-Tuning Process](#fine-tuning-process)
- [Results](#results)

## Introduction

LLaMA-7B is a powerful large language model developed by Meta AI, pre-trained on a vast amount of text data. However, in this project, I specialize the model for code generation tasks. To do this efficiently, I applied LoRA to fine-tune the model by introducing trainable low-rank matrices, while freezing the original parameters of the model.

## Dataset

For this fine-tuning process, I used the [codeparrot/codeparrot-clean](https://huggingface.co/datasets/codeparrot/codeparrot-clean) dataset from Hugging Face.

- **Dataset Size**: ~60GB
- **Languages**: Mainly Python, but includes some other languages
- **Preprocessing**: The dataset is cleaned and deduplicated to ensure high-quality code without redundant or low-quality snippets.
- **Source**: The dataset was scraped from publicly available code repositories on GitHub and processed by the CodeParrot team.

## Fine-Tuning Process

### 1. LoRA Architecture

![image](https://github.com/user-attachments/assets/cb3fac1a-d96a-47a5-acee-77dcb4532329)

- **Key idea**: Instead of updating all the parameters of the LLaMA model during fine-tuning, I only update the LoRA layers, significantly reducing training time and memory usage.

### 2. Steps for Fine-Tuning

- Load the pre-trained LLaMA-7B model with all layers frozen.
- Inject LoRA layers into the model's architecture.
- Train the model for code generation tasks using a curated dataset.
- See the model's code generation performance.

### 3. Freezing All Layers Except LoRA

During fine-tuning, all original layers of LLaMA-7B remain frozen. Only the LoRA layers (low-rank matrices) are trained. This allows for fine-tuning on a specific task (code generation) while maintaining the general knowledge contained in the pre-trained model.

## Results

The fine-tuned model demonstrated improved performance in generating python code snippets. Some of them are shown in the notebook.

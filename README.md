# Indonesian Abstractive Text Summarization using PEGASUS with Bayesian Tuning

This repository contains the implementation of fine-tuning the PEGASUS model for Indonesian abstractive text summarization, enhanced with Bayesian optimization for *hyperparameter* tuning.

## 📌 Background

Abstractive summarization aims to generate summaries that are not merely extracted from the original text, but are newly constructed to capture the core information.

Pre-trained models like PEGASUS have shown strong performance in this task. However, their effectiveness heavily depends on properly tuned *hyperparameters*. Therefore, this project applies Bayesian tuning to find optimal configurations.

Additionally, the labeling strategy is enriched by combining:

* `summary`
* `title`
* `keyphrases`

to provide richer learning signals for the model.

## 🧠 Methodology

### Model

* PEGASUS (fine-tuned)
* Tokenizer: Modified PEGASUS tokenizer for Indonesian

### Hyperparameter Tuning

* Framework: Optuna
* Method: Bayesian Optimization
* Tuned parameters include:

  * *learning rate*
  * *batch size*
  * *weight decay*
  * *dropout*
  * etc.

### Infrastructure

* TPU (Google Cloud / TPU Research Cloud)
* Distributed training using TPU VM

### Dataset

The dataset consists of the following fields:

* `title`
* `body`
* `keyphrases`
* `summary`

The final target label is constructed by combining multiple fields above.


## 🚀 Getting Started

Learn the structure of the experiment_notebook.ipynb

## ⚙️ Key Configurations

Important parameters include:

* *learning rate*: determined via Optuna tuning
* *max input length*: adjusted based on article length
* *max target length*: summary length
* Indonesian-specific tokenizer adjustments

## 📊 Evaluation

Evaluation is conducted using:

* ROUGE-1
* ROUGE-2
* ROUGE-L
* ROUGE-Lsum
* BERTscore


## 📝 Notes

* Training is performed on TPU to accelerate fine-tuning
* Indonesian datasets have unique characteristics (e.g., long-form news structure)
* Tokenizer is adapted to better handle Indonesian text distribution

## 📚 References

* PEGASUS: Pre-training with Extracted Gap-sentences for Abstractive Summarization
* Optuna: A Next-generation Hyperparameter Optimization Framework
* LipKey: A Large-Scale News Dataset for Absent Keyphrases Generation


---

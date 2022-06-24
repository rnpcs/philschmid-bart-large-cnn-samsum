
---
language: en
tags:
- sagemaker
- bart
- summarization
datasets:
- samsum
widget:
- text: "Jeff: Can I train a \U0001F917 Transformers model on Amazon SageMaker? \n\
    Philipp: Sure you can use the new Hugging Face Deep Learning Container. \nJeff:\
    \ ok.\nJeff: and how can I get started? \nJeff: where can I find documentation?\
    \ \nPhilipp: ok, ok you can find everything here. https://huggingface.co/blog/the-partnership-amazon-sagemaker-and-hugging-face\n"
model-index:
- name: bart-large-cnn-samsum
  results:
  - task:
      name: Abstractive Text Summarization
      type: abstractive-text-summarization
    dataset:
      name: 'SAMSum Corpus: A Human-annotated Dialogue Dataset for Abstractive Summarization'
      type: samsum
    metrics:
    - name: Validation ROGUE-1
      type: rogue-1
      value: 42.621
    - name: Validation ROGUE-2
      type: rogue-2
      value: 21.9825
    - name: Validation ROGUE-L
      type: rogue-l
      value: 33.034
    - name: Test ROGUE-1
      type: rogue-1
      value: 41.3174
    - name: Test ROGUE-2
      type: rogue-2
      value: 20.8716
    - name: Test ROGUE-L
      type: rogue-l
      value: 32.1337
  - task:
      type: summarization
      name: Summarization
    dataset:
      name: samsum
      type: samsum
      config: samsum
      split: test
    metrics:
    - name: ROUGE-1
      type: rouge
      value: 41.3282
      verified: true
    - name: ROUGE-2
      type: rouge
      value: 20.8755
      verified: true
    - name: ROUGE-L
      type: rouge
      value: 32.1353
      verified: true
    - name: ROUGE-LSUM
      type: rouge
      value: 38.401
      verified: true
    - name: loss
      type: loss
      value: 1.4297215938568115
      verified: true
    - name: gen_len
      type: gen_len
      value: 60.0757
      verified: true
---

## `bart-large-cnn-samsum`

This model was trained using Amazon SageMaker and the new Hugging Face Deep Learning container.

For more information look at:
- [🤗 Transformers Documentation: Amazon SageMaker](https://huggingface.co/transformers/sagemaker.html)
- [Example Notebooks](https://github.com/huggingface/notebooks/tree/master/sagemaker)
- [Amazon SageMaker documentation for Hugging Face](https://docs.aws.amazon.com/sagemaker/latest/dg/hugging-face.html)
- [Python SDK SageMaker documentation for Hugging Face](https://sagemaker.readthedocs.io/en/stable/frameworks/huggingface/index.html)
- [Deep Learning Container](https://github.com/aws/deep-learning-containers/blob/master/available_images.md#huggingface-training-containers)

## Hyperparameters
```json
{
    "dataset_name": "samsum",
    "do_eval": true,
    "do_predict": true,
    "do_train": true,
    "fp16": true,
    "learning_rate": 5e-05,
    "model_name_or_path": "facebook/bart-large-cnn",
    "num_train_epochs": 3,
    "output_dir": "/opt/ml/model",
    "per_device_eval_batch_size": 4,
    "per_device_train_batch_size": 4,
    "predict_with_generate": true,
    "seed": 7
}
```

## Usage
```python
from transformers import pipeline
summarizer = pipeline("summarization", model="philschmid/bart-large-cnn-samsum")

conversation = '''Jeff: Can I train a 🤗 Transformers model on Amazon SageMaker? 
Philipp: Sure you can use the new Hugging Face Deep Learning Container. 
Jeff: ok.
Jeff: and how can I get started? 
Jeff: where can I find documentation? 
Philipp: ok, ok you can find everything here. https://huggingface.co/blog/the-partnership-amazon-sagemaker-and-hugging-face                                           
'''
nlp(conversation)
```

## Results

| key | value |
| --- | ----- |
| eval_rouge1 | 42.621 |
| eval_rouge2 | 21.9825 |
| eval_rougeL | 33.034 |
| eval_rougeLsum | 39.6783 |
| test_rouge1 | 41.3174 |
| test_rouge2 | 20.8716 |
| test_rougeL | 32.1337 |
| test_rougeLsum | 38.4149 |


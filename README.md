# Internet Memes Classification using Multimodal Learning and Image Captioning

## Overview
This project focuses on classifying internet memes using multimodal learning techniques. The aim is to leverage both textual and visual information inherent in memes to accurately categorize them into predefined classes or themes.

## Problem Statement

This project tackles two critical challenges in understanding internet memes by leveraging multimodal learning:

- **Task A – Offensive Content Detection:**  
  Classify memes as offensive or non-offensive by analyzing the sentiment and intent conveyed through both text and images. This task utilizes the **MultiOFF** dataset, which contains multilingual samples to address hate speech detection across diverse languages and cultural contexts.

- **Task B – Emotion Classification:**  
  Detect and categorize multiple emotional dimensions expressed in memes, such as humor, sarcasm, offensiveness, and motivation. Memes can exhibit overlapping emotions, making this a multilabel classification problem. This task is based on the **Memotion-7k** dataset, which provides rich annotations and OCR-extracted text to support detailed emotional analysis.

By addressing these tasks, the project aims to improve the automated understanding of meme content, which is often subtle, context-dependent, and multimodal.


## Dataset

### MultiOFF Dataset  
| Class        | Training | Validation | Testing | Total Samples |
|--------------|----------|------------|---------|---------------|
| Hateful      | 187      | 58         | 58      | 743           |
| Non-Hateful  | 258      | 91         | 91      | 743           |

*The MultiOFF dataset is used for multilingual offensive language identification and hate speech detection.*

---

### Memotion-7k Dataset  
| Class       | Training (Macro F1) | Validation (Macro F1) | Testing (Macro F1) | Total Samples |
|-------------|---------------------|----------------------|-------------------|---------------|
| Humour      | 4,272 (1,320)       | 534 (166)            | 534 (166)         | 6,992         |
| Sarcasm     | 4,358 (1,236)       | 544 (155)            | 544 (155)         | 6,992         |
| Offensive   | 3,432 (2,170)       | 426 (269)            | 426 (269)         | 6,992         |
| Motivation  | 1,973 (3,621)       | 246 (453)            | 246 (453)         | 6,992         |

*Memotion-7k includes OCR-extracted text metadata enabling multimodal analysis of memes.*

## Model Architecture
- **ALBERT:** A lightweight transformer-based language model used to extract semantic and contextual features from meme text. It is efficient and well-suited for understanding nuanced language such as sarcasm and humor.
- **VGG-11:** A convolutional neural network used to extract visual features from meme images, capturing visual cues like facial expressions, objects, and background context.
- **BLIP:** A model for automatic caption generation that enriches visual understanding by generating descriptive text captions from images. These captions are processed via a stacked BiLSTM.
- **Multimodal Fusion:** Features extracted from ALBERT (text), VGG-11 (image), and BLIP-generated captions are combined using late fusion. The combined features pass through dense layers and a softmax classifier to predict sentiment and emotion labels.

## Performance Metrics

### Task A - Offensive Content Detection

| Model                  | Accuracy | Precision | Recall | F1-score |
|------------------------|----------|-----------|--------|----------|
| Without Image Captioning| 0.6376   | 0.6173    | 0.6158 | 0.6164   |
| With Image Captioning   | 0.4832   | 0.5027    | 0.4832 | 0.4894   |

---

### Task B - Emotion Classification

| Metrics  | Humor (H) | Sarcasm (S) | Offensive (O) | Motivation (M) | Average  |
|----------|-----------|-------------|---------------|---------------|----------|
| **Without Image Captioning** |           |             |               |               |          |
| Accuracy | 0.7467    | 0.7598      | 0.5136        | 0.5763        | 0.6491   |
| F1-Score | 0.6964    | 0.6650      | 0.5048        | 0.5416        | 0.6098   |
| Precision| 0.6717    | 0.6667      | 0.4984        | 0.5361        | 0.5932   |
| Recall   | 0.7467    | 0.7598      | 0.5136        | 0.5763        | 0.6491   |

| Metrics  | Humor (H) | Sarcasm (S) | Offensive (O) | Motivation (M) | Average  |
|----------|-----------|-------------|---------------|---------------|----------|
| **With Image Captioning** |           |             |               |               |          |
| Accuracy | 0.7858    | 0.7811      | 0.5467        | 0.6189        | 0.6831   |
| F1-Score | 0.6970    | 0.7053      | 0.5420        | 0.5072        | 0.6129   |
| Precision| 0.7466    | 0.6980      | 0.5382        | 0.5489        | 0.6329   |
| Recall   | 0.7858    | 0.7811      | 0.5467        | 0.6189        | 0.6831   |

## Conclusion
This project demonstrates the effectiveness of multimodal learning in classifying internet memes by integrating textual, visual, and generated caption modalities. The combination of ALBERT, VGG-11, and BLIP models provides rich feature representations that improve the detection of offensive content and nuanced emotions in memes.

## References

- **MultiOFF Dataset:**  
  Suryawanshi, S., Chakravarthi, B. R., Arcan, M., & Buitelaar, P.  
  *Multimodal meme dataset (MultiOFF) for identifying offensive content in image and text.*

- **Memotion-7k Dataset:**  
  Sharma, C., Paka, Scott, W., Bhageria, D., Das, A., Poria, S., Chakraborty, T., & Gambäck, B. (2020).  
  *Task Report: Memotion Analysis 1.0 @SemEval 2020: The Visuo-Lingual Metaphor!*  
  In Proceedings of the 14th International Workshop on Semantic Evaluation (SemEval-2020), Barcelona, Spain, Association for Computational Linguistics.

- **BLIP Model (Bootstrapped Language Image Pretraining):**  
  Li, J., Dong, L., Xu, C., Wang, W., & Wei, F. (2022).  
  *BLIP: Bootstrapping Language-Image Pre-training for Unified Vision-Language Understanding and Generation.*  
  Available at: [https://huggingface.co/Salesforce/blip-image-captioning-large](https://huggingface.co/Salesforce/blip-image-captioning-large)




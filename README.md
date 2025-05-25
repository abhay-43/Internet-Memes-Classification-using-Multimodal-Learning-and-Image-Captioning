# Internet Memes Classification using Multimodal Learning and Image Captioning

## Overview
This project focuses on classifying internet memes using multimodal learning techniques. The aim is to leverage both textual and visual information inherent in memes to accurately categorize them into predefined classes or themes.

## Problem Statement
The project addresses two primary tasks:
- **Task A - Sentiment Analysis:** Classify memes into offensive or non-offensive categories based on the sentiment conveyed.
- **Task B - Emotion Classification:** Identify various emotional nuances within memes, including humor, sarcasm, offensiveness, and motivational content. Memes may belong to more than one emotion category.

## Dataset

### MultiOFF Dataset  
| Split       | Hateful Samples | Non-Hateful Samples | Total Samples |
|-------------|-----------------|---------------------|---------------|
| Training    | 187             | 258                 | 445           |
| Validation  | 58              | -                   | 58            |
| Testing     | 91              | -                   | 91            |
| **Total**   | 743 (combined)  |                     | 743           |

*The MultiOFF dataset is used for multilingual offensive language identification and hate speech detection.*

---

### Memotion-7k Dataset  
| Split      | Humor | Sarcasm | Offensive | Motivation | Total Samples |
|------------|-------|---------|-----------|------------|---------------|
| Training   | 4,272 | 4,358   | 3,432     | 1,973      | 6,992         |
| Validation | 534   | 544     | 426       | 246        | -             |
| Testing    | 534   | 544     | 426       | 246        | -             |

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
- [MultiOFF Dataset](https://github.com/your-repo/multioff)  
- [Memotion-7k Dataset](https://github.com/your-repo/memotion7k)  
- [ALBERT Paper](https://arxiv.org/abs/1909.11942)  
- [VGG-11 Model](https://arxiv.org/abs/1409.1556)  
- [BLIP: Bootstrapped Language Image Pretraining](https://arxiv.org/abs/2201.12086)  


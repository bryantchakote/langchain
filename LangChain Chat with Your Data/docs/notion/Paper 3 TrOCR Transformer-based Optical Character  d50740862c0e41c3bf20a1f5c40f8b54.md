# Paper 3: TrOCR: Transformer-based Optical Character Recognition with Pre-trained Models

---

Minghao Li and Tengchao Lv and Jingye Chen and Lei Cui and Yijuan Lu and Dinei Florencio and Cha Zhang and Zhoujun Li and Furu Wei. 2022. TrOCR: Transformer-based Optical Character Recognition with Pre-trained Models.

---

# Abstract

- Text recognition is a long-standing research problem for document digitalization. Existing approaches are usually built based on CNN for image understanding and RNN for char-level text generation.
- In this paper, we propose an end-to-end text recognition approach with pre-trained image Transformer and text Transformer models, namely TrOCR, which leverages the Transformer architecture for both image understanding and wordpiece-level text generation.

# Introduction

- Optical Character Recognition (OCR) is the electronic or mechanical conversion of images of typed, handwritten or printed text into machine-encoded text, whether from a scanned document, a photo of a document, a scene photo or from subtitle text superimposed on an image.
- Typically, an OCR system includes two main modules: a text detection module and a text recognition module. Text detection aims to localize all text blocks within the text image, either at word-level or textline-level. […] Meanwhile, text recognition aims to understand the text image content and transcribe the visual signals into natural language tokens. […] In this paper, we focus on the text recognition task for document images and leave text detection as the future work.
- Recent progress in text recognition (Diaz et al. 2021) has witnessed the significant improvements by taking advantage of the Transformer (Vaswani et al. 2017) architectures. However, existing methods are still based on CNNs as the backbone, where the self-attention is built on top of CNN backbones as encoders to understand the text image. For decoders, Connectionist Temporal Classification (CTC) (Graves et al. 2006) is usually used compounded with an external language model on the character-level to improve the overall accuracy.
- We propose TrOCR, an end-to-end Transformer-based OCR model for text recognition with pre-trained CV and NLP models. […] Distinct from the existing text recognition models, TrOCR is a simple but effective model which does not use the CNN as the backbone. Instead, following (Dosovitskiy et al. 2021), it first resizes the input text image into 384 x 384 and then the image is split into a sequence of 16 x 16 patches which are used as the input to image Transformers. Standard Transformer architecture with the self-attention mechanism is leveraged on both encoder and decoder parts, where word-piece units are generated as the recognized text from the input image.

# Model architecture

- TrOCR is built up with the Transformer architecture, including an image Transformer for extracting the visual features and a text Transformer for language modeling. We adopt the vanilla Transformer encoder-decoder structure in TrOCR. The encoder is designed to obtain the representation of the image patches and the decoder is to generate the word piece sequence with the guidance of the visual features and previous predictions.

# Evaluation metrics

- The SROIE dataset is evaluated using the word-level precision, recall and f1 score […] (which) are described as:

$$
Precision = \frac{Correct\;matches}{Number\;of\;detected\;words}\\
Recall = \frac{Correct\;matches}{Number\;of\;ground\;truth\;words}\\
F1 = \frac{2 * Precision * Recall}{Precision + Recall}
$$

- The IAM dataset is evaluated by the case-sensitive Character Error Rate (CER).
- The scene text datasets are evaluated by the Word Accuracy.

# Related work

## Scene Text Recognition

- The texts in natural images may appear in irregular shapes caused by perspective distortion. (Shi et al. 2016; Baek et al. 2019; Litman et al. 2020; Shi et al. 2018; Zhan and Lu 2019) addressed this problem by processing the input images with an initial rectification step.

# Conclusion

- In this paper, we present TrOCR, an end-to-end Transformer-based OCR model for text recognition with pre-trained models. Distinct from existing approaches, TrOCR does not rely on the conventional CNN models for image understanding. Instead, it leverages an image Transformer model as the visual encoder and a text Transformer model as the textual decoder. Moreover, we use the wordpiece as the basic unit for the recognized output instead of the character-based methods, which saves the computational cost introduced by the additional language modeling. Experiment results show that TrOCR achieves state-of-the-art results on printed, handwritten and scene text recognition with just a simple encoder-decoder model, without any post-processing steps.
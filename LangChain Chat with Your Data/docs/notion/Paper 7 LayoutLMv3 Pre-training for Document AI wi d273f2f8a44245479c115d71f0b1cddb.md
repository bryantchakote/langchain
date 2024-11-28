# Paper 7: LayoutLMv3: Pre-training for Document AI with Unified Text and Image Masking

---

Yupan Huang, Tengchao Lv, Lei Cui, Yutong Lu, and Furu Wei. 2022. LayoutLMv3: Pre-training for Document AI with Unified Text and Image Masking. In Proceedings of the 30th ACM International Conference on Multimedia(MM’22), October 10–14, 2022, Lisboa, Portugal. ACM, New York, NY, USA, 10 pages. [https://doi.org/10.1145/3503161.3548112](https://doi.org/10.1145/3503161.3548112)

---

# Abstract

- Most multimodal pre-trained models use a masked language modeling objective to learn bidirectional representations on the text modality, but they differ in pre-training objectives for the image modality. This discrepancy adds difficulty to multimodal representation learning. In this paper, we propose LayoutLMv3 to pre-train multimodal Transformers for Document AI with unified text and image masking.
- Experimental results show that LayoutLMv3 achieves state of-the-art performance not only in text-centric tasks, including form understanding, receipt understanding, and document visual
question answering, but also in image-centric tasks such as document image classification and document layout analysis.

# Introduction

- A pre-trained Document AI model can parse layout and extract key information for various documents such as scanned forms and academic papers.
- Comparisons with existing works (e.g., DocFormer [2] and SelfDoc [31])
    - On image embedding: our LayoutLMv3 uses linear patches to reduce the computational bottleneck of CNNs and eliminate the need for region supervision in training object detectors.
    - On pre-training objectives on image modality: our LayoutLMv3 learns to reconstruct discrete image tokens of masked patches instead of raw pixels or region features to capture high-level layout structures rather than noisy details.
- To overcome the discrepancy in pre-training objectives of text and image modalities and facilitate multimodal representation learning, we propose LayoutLMv3 to pre-train multimodal Transformers for Document AI with unified text and image masking objectives MLM (Masked Language Modeling) and MIM (Masked Image Modeling).
- Inspired by DALL-E [43] and BEiT [3], we obtain the target image tokens from latent codes of a discrete VAE. For documents, each text word corresponds to an image patch. To learn this cross-modal alignment, we propose a Word-Patch Alignment (WPA) objective to predict whether the corresponding image patch of a text word is masked.
- Inspired by ViT [11] and ViLT [22], LayoutLMv3 directly leverages raw image patches from document images without complex pre-processing steps such as page object detection.
- LayoutLMv3 jointly learns image, text and multimodal representations in a Transformer model with unified MLM, MIM and WPA objectives. This makes LayoutLMv3 the first multimodal pre-trained Document AI model without CNNs for image embeddings, which significantly saves parameters and gets rid of region annotations.
- The simple unified architecture and objectives make LayoutLMv3 a general purpose pre-trained model for both text-centric tasks and image centric Document AI tasks.

# LayoutLMv3

## Model Architecture

- LayoutLMv3 applies a unified text-image multimodal Transformer to learn cross-modal representations. The Transformer has a multi-layer architecture and each layer mainly consists of multi-head self-attention and position-wise fully connected feed-forward networks [49]. The input of Transformer is a concatenation of text embedding Y = y1:𝐿 and image embedding X = x1:𝑀 sequences, where 𝐿 and 𝑀 are sequence lengths for text and image respectively. Through the Transformer, the last layer outputs text-and-image contextual representations.
- Text embedding is a combination of word embeddings and position embeddings. We pre-processed document images with an off-the-shelf OCR toolkit to obtain textual content and corresponding 2D position information. We initialize the word embeddings with a word embedding matrix from a pre-trained model RoBERTa. The position embeddings include 1D position and 2D layout position embeddings, where the 1D position refers to the index of tokens within the text sequence, and the 2D layout position refers to the bounding box coordinates of the text sequence.
- Image Embedding: Inspired by ViT [11] and ViLT [22], we represent document images with linear projection features of image patches before feeding them in to the multimodal Transformer. […] We insert semantic 1D relative position and spatial 2D relative position as bias terms in self-attention networks for text and image modalities following LayoutLMv2[56].

## Pre-training Objectives

Objective 1: Masked Language Modeling (MLM). We mask 30% of text tokens with a span masking strategy with span lengths drawn from a Poisson distribution (𝜆 = 3) [21, 27].

Objective 2: Masked Image Modeling (MIM). The MIM objective is a symmetry to the MLM objective, that we randomly mask a percentage of about 40% image tokens with the blockwise masking strategy [3].

Objective 3: Word-Patch Alignment (WPA). For documents, each text word corresponds to an image patch. As we randomly mask text and image tokens with MLM and MIM respectively, there is no explicit alignment learning between text and image modalities. We thus propose a WPA objective to learn a fine-grained alignment between text words and image patches. The WPA objective is to predict whether the corresponding image patches of a text word are masked.

# Experiments

## Fine-tuning on Multimodal Tasks

- Task 1: Form and Receipt Understanding. Form and receipt understanding tasks require extracting and structuring forms and receipts’ textual content. The tasks are a sequence labeling problem aiming to tag each word with a label. We predict the label of the last hidden state of each text token with a linear layer and an MLP classifier for form and receipt understanding tasks, respectively.
- Task 2: Document Image Classification. The document image classification task aims to predict the category of document images. We feed the output hidden state of the special classification token ([CLS]) into an MLP classifier to predict the class labels.
# Paper 8: Document Analysis and Recognition: A survey

---

Nigam, Shivangi & Verma, Shekhar & Nagabhushan, P.. (2023). Document Analysis and Recognition: A survey. 10.36227/techrxiv.22336435.

---

# Abstract

- The journey of research for Document Analysis and Recognition (DAR) started with the problem of automatic character recognition. Today, it has covered a vast span of recognition tasks such as text recognition, script identification, WI, word spotting, signature verification etc., in scripts like Roman, Arabic, Chinese, Japanese, Brahmi etc. Extensive advancements in deep learning techniques have achieved state-of-the-art results for various DAR tasks.

# Introduction

- Document analysis and recognition (DAR) is the ability to localize and transform the textual content of document images into a machine-readable format.
- Text localization, feature extraction and classification of document images can produce transcripted text for machine interpretation.
- The very onset of DAR used handcrafted methodologies for various tasks. These methods required application-specific pre-processing and post-processing operations. Also, the handcrafted features were limited by the pre-determined patterns and structures in the data they could process. Thus, they were incompetent in the convoluted innominate environment.
- The key contributions of this research are enlisted as follows.
    - Elaborate analysis of the problem of DAR from various perspectives.
    - Comprehensive review of techniques for basic tasks of DAR, viz, Pre-processing, Segmentation and Recognition.
    - Comparative analysis of state-of-the-art techniques through tables and figures.
    - Detailed categorization of Datasets with categorization into Historic, Printed, Handwritten(offline and online)
    - Exposition of different variety of evaluation metrics proposed for various tasks
    - A critique of script-related challenges for DAR.
    - Insights for potential future research directions for a generic DAR model

# Document Analysis and Recognition (DAR)

- Automatic collection of data, identifying objects and recognizing optically processed characters without human intervention was termed OCR [4], [5].
- OCRs can convert PDF files, scanned papers or camera-captured document images into machine-readable textual formats.

# Challenges

![Untitled](Untitled%201.png)

- Multi-lingual environments, font variations, handwritten text, dependency on Intermediate steps, idiosyncrasies of various scripts (for instance, characters like d and l can confuse the recognizer as they have similar stroke patterns), noise, camera and environment challenges.

# Tasks of DAR

- All methods can be categorized into three classes of tasks: pre-processing step eliminates the unwanted elements and improve the quality of images, segmentation steps deals with pre-processed documents and extracts various text/non-text elements and lastly text recognition performs feature extraction and classification. The output of recognition requires post-processing for producing machine-readable unicode text.
- Pre-processing: The basic purpose of a pre-processor is to produce an image ready for feature extraction such that it improves the recognition capability of the text recognition system.
    - Image correction: noise reduction, normalization, lighting correction, geometric corrections
    - Image enhancement: enhancing illumination, blur and focus, background estimation, grayscale conversion
    - Image compression
    - Binarization: Document binarization involves dividing a document image into two groups: foreground pixels and background pixels. The foreground pixels are turned black, and the rest are white.
- Page segmentation: There are two levels of segmentation. […] First, a document is segmented into text and non-text regions (graphics, tables, etc.). Further, the text region is segmented into paragraphs, lines, words, and characters.
- Text recognition: The recognition of text from document images corresponds to observing characteristic patterns of text elements and utilizing the features of these elements for recognition purposes. A recognition system’s performance depends on extracted features’ quality, which is further based on the pre-processing and segmentation steps.

# Evaluation metrics

- Pre-processing: precision, recall and F-1 score on extracted objects, MPM (distance between contour points of ground truth and binary images)
- Segmentation: IoU, mAP of different classes to be recognized
- Recognition: $CER = \frac{wrong\;recognized\;characters}{total\;characters}$, $WER = \frac{wrong\;recognized\;words}{total\;words}$

# Future research directions

- Integration of Language model
- End-to-end recognition systems: The step-wise segmentation methods have a drawback in that the consequent steps depend on the performance of the previous steps.
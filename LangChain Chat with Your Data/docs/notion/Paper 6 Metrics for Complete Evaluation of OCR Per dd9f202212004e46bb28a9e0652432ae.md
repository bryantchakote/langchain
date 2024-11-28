# Paper 6: Metrics for Complete Evaluation of OCR Performance

---

Romain Karpinski, Devashish Lohani, Abdel Belaid. Metrics for Complete Evaluation of OCR Performance. IPCV’18- The 22nd Int’l Conf on Image Processing, Computer Vision, & Pattern Recognition, Jul 2018, Las Vegas, United States. hal-01981731

---

# Abstract

- In this paper, we study metrics for evaluating OCR performance both in terms of physical segmentation and in terms of textual content recognition. These metrics rely on the OCR output (hypothesis) and the reference (also called ground truth) input format. Two evaluation criteria are considered: the quality of segmentation and the character recognition rate.

# Introduction

- Retro-conversion is the task of extracting and recognizing the content of a document image. To perform this task, most OCRs usually work in two steps: region-based text segmentation, and characters recognition using the extracted regions. Depending on the segmentation algorithm used, the location of the lines, words and characters can be obtained.
- For documents with a simple layout, such as pages in a book, the performance of current OCRs
makes it possible to retro-translate them reliably. However, for documents with a much more complex layout, such as newspapers or administrative documents, more segmentation
errors may occur.
- Segmentation errors can either be a split (under-segmentation) or a merge (over-segmentation) and in two directions: vertical or horizontal.
- Regarding the evaluation of character recognition rate, the textual content of reference must be available to align it with the text given by the OCR.
- The evaluation of segmentation quality is often determined by zone alignments.
- It is difficult, with only two Texts, to fully evaluate the segmentation.
- Two input formats are distinguished for the alignment method: text and xml. The text format is a sequence of strings. representing the sentences of the document image. The xml format is a text with spatial information such as line, word or character bounding boxes.

# Related work

## Text-to-Text evaluation

- Text-to-Text evaluation consists of aligning and comparing two texts.
- The lines may have undergone all the segmentation errors defined above. It can thus be seen that the difficulty of aligning the lines stems directly from the quality of the segmentation.

## XML-to-XML evaluation

- For xml-to-xml evaluation, zones from both xmls must be aligned together. This alignment will make it possible to compare the zones (error amount and type of errors), and thus the evaluation of the segmentation. Then, this spatial alignment of zones can help with the content alignment (lines, words, etc.).

# Our contribution

## ZoneMapAltCnt

- ZoneMapAltCnt is a new method that we propose here for complete ocr evaluation. It is an extension of ZoneMapAlt where the content of zones in different configurations is taken into account.
- Character metric is based on the Levenshtein distance which represent the minimum number of edit operations (character insertions, deletions, and substitutions) needed to correct the hypothesis Text (OCR generated Text) to match it with the reference Text.
- Word metric is based on the Levenshtein distance, like in characters, but at a word level. This means that we will look for the minimum number of word insertions, deletions, and
substitutions needed to correct the hypothesis Text to match it with the reference Text. If word in RZ is a substring of the word in corresponding HZ, then it is considered correct.
- The strict word metric is identical to word metric except for the computation of a correct word.
- Group configuration
    - False Alarm: The group contains only one HZ with content and no corresponding RZ. It means that the system has over-detected this zone and its content.
    - Miss: The group contains only one RZ with content and no corresponding HZ. It means that the system has under-detected this zone and its content.
    - Match: The group contains only one HZ and one RZ.
    - Split: The group contains only one RZ and more than one HZs. It means that the RZ has been segmented into several parts.
    - Merge: The group contains more than one RZs and one HZ, meaning RZs have been merged by an HZ.
    - Multiple: The group contains more than one RZs and HZs.

## Text-to-xml Approach

### Marking of common unique strings

- This first treatment provides us with an alignment draft that must be checked and which will serve as a basis for realizing the entire alignment.

### Detection and correction of merges and splits

- This draft may have segmentation errors such as merges and splits. If an hypothesis line is aligned with at least 2 reference lines then this is a merge. Conversely, if one reference line is aligned with at least 2 hypothesis lines then it is a split.

### Correction of last alignments

- A cardinality relation of one-to-one does not mean that there are no segmentation errors. It is important to check each alignment that we have made.

### Alignment of new elements

- We iterate on the reference lines by making intervals between two lines. These intervals form lists of non-aligned reference lines. Also, it gives us, thanks to the matches of the two lines forming the interval, a search zone.

# Results and experiments

- Text-to-Text methods will fail to evaluate 2D documents properly because they may contain segmentation errors that were not present in 1D documents.
- It can be observed that for every corpus, false alarm error is responsible for at least 96% of the error score. Even after this extremely dominating segmentation error, character metric results are surprisingly excellent with at least 93.53% precision across all corpora. This led us to formulate the following hypothesis: most of the false alarm errors does not contain any character otherwise the character precision would have been greatly affected. To verify this hypothesis, a visual inspection has been conducted which reveals that elements constituting graphic zones such as table lines are identified as zones without content.
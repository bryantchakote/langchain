# Paper 4: Document image analysis and recognition: a survey

---

Arlazarov VV, Andreeva EI, Bulatov KB, Nikolaev DP, Petrova OO, Savelev BI, Slavin OA. Document image analysis and recognition: a survey. Computer Optics 2022; 46(4): 567-589. DOI: 10.18287/2412-6179-CO-1020.

---

# Abstract

- This paper analyzes the problems of document image recognition and the existing solutions.
- Here, we consider methods of document recognition and analysis applied to a wide range of tasks: identification and verification of identity, due diligence, machine learning algorithms, questionnaires, and audits.

# Introduction

- Despite consistent predictions that electronic document flow will soon replace paper one, after 40 years people around the world still use the mixed electronic and paper document flow. In such a situation it is important to have technologies that help easily and accurately translate a document from one form to another.
- We define a document as a set of unchangeable elements and information attributes. The attribute values are interpreted by an information system to perform operations on a document. Examples of such operations are registration, control, and cancellation of a document, synchronization of document attributes and data in the electronic archive.
- The graphical representation of any document contains static graphic elements and content elements.
- One of the most important elements of certain templates is the complex background. For ID or registration documents, text on stamped paper with a so-called "guilloché" background is typical. Such background is a classical static element. The background of bank plastic cards can be a random image that changes from series to series. It is not a static element in the strict sense, but as a rule, it is not an information attribute either.
- By document recognition, we denote the extraction of attribute values from the document image.
- Among the variety of documents, the following classes can be considered based on the document structure:
    - rigid forms created in a uniform polygraphic way, such as ID documents (passport, ID card), driver's license;
    - flexible forms created based on the known templates, e.g. standard questionnaires, notifications, declarations, bank plastic cards;
    - documents without a strict template, e.g. contracts, letters of attorney;
    - documents that do not have a common template, such as business letters.
- The transition from the analysis of scanned images to the analysis of document photographs required the development of new approaches, resistant at least to projective distortions and uneven illumination. This brought the field of Document Image Analysis (DIA) closer to computer vision.

# A review of DIA methods

## Document image normalization (1.1)

- Due to human and technical factors, digital images may contain distortions. Elimination of distortions, or normalization, is a classical task of digital document imaging. A particular case of such distortions is the skew (rotation) of the acquired document image.

## Document image binarization (1.4)

- Document image binarization separates pixels of document contents from pixels of background. This classification of pixels allows for a significant reduction in the memory required to store the image, and it simplifies all the subsequent OCR steps.

## Document classification and localization based on keypoints (2)

- Localization via keypoints detection assumes that a document’s template has unique features, and they should be known in advance. Often, this is not the case. […] In this case, at the geometric normalization step, a rectangle is chosen as a model for a document.

## Visual appearance based document image classification and localization (2)

- There is another approach to document localization and classification. It is used when the document template does not have unique and stable local features, but the document can still be easily recognized by its visual appearance.

## Document boundary detection (1.1)

- Works on document boundary detection consider both scanned images and photographs. The second case is more general, because such images may have a non-uniform background, which increases the probability of false positives. In addition, the borders of the document may be partially obscured.
- The image of a document in scanned images is a rectangle that differs from the preimage by shift, rotation, and isotropic compression.
- There are three main approaches to document boundary detection: contour analysis, image segmentation, and document corner detection.
- It is worth noting that the basic assumption of the contour analysis approach is that all sides of the document are visible in the image and have a strong contrast to the background.

## Document structure analysis algorithms (2)

- The tasks included in the document structure analysis block can be divided into the following groups:
    - detection and localization of text elements (lines, words) of the document;
    - analysis of the text blocks structure and the segmentation of the document into separate text blocks, columns, paragraphs, or text fields;
    - finding the text reading sequence of text blocks (columns, paragraphs, fields) in a document;
    - detection and localization of graphic elements within the document, i.e. shapes, figures, formulas, seals, stamps, etc.
- In terms of document features, document structure analysis methods are divided into rigid templates structure analysis methods (i.e., documents with variable elements located at the same places throughout samples), single-column and multi-column Manhattan structure analysis (i.e. documents that can be decomposed into non-overlapping orthotropic rectangular regions, each containing either a text block or a figure, a table, etc.), and analysis of documents with arbitrary structure (i.e. documents where graphical elements and text blocks can be of arbitrary shape and with arbitrary text direction).
- Methods of document structure parsing are also divided into methods involving a priori knowledge of the template ("grammar") of the document components structure, and methods applicable to documents with a priori unknown structure.

## Table recognition methods (3)

- Tables are an important element of many types of documents. Despite the long history of research, the problem of their recognition remains relevant, and the bulk of the results are given for closed datasets, which complicates the analysis and verification of the results.
- When processing tables, algorithms can rely on more heuristics, and additionally use such characteristic structural elements as layout lines, corners and junctions, alignments, etc. Nevertheless, in recent years, there has been a shift in researchers' interest from engineering problem-solving methods to learning ones.
- The main subtasks of optical table recognition can be formulated as follows:
    - table detection (localization), i.e. detection of the borders of tabular structured information areas, usually in the form of orthotropic rectangles, in the image;
    - table segmentation (structure recognition), i.e. recognition of the table structure as a graph of adjacent cells, specifying the relative position of each table cell;
    - table recognition, i.e. recognition of the table structure and the contents of each cell.
- To assess the performance of the table detection algorithms, the detection results are compared to the reference rectangles using the Intersection over Union (IoU) coefficient.
- To assess the segmentation quality of the table area [85], a comparison with the benchmark structure of vertical and horizontal links between adjacent filled cells in the matrix structure is often used. In [89], this approach is criticized for its lack of sensitivity to errors caused by empty cells and mismatched cells outside of immediate neighbors, and for the fact that it does not accurately assess the quality of cell content (text) recognition. The proposed new function of the TEDS (Tree-Edit-Distancebased Similarity) quality of table recognition evaluation is based on the representation of the table in the form of a hierarchical tree structure (HTML table tree). The quality score is calculated based on the cost of editing (edit distance) of such a tree-like recognition result to bring it to the reference, which allows taking in to account both errors related to the structure and to the values of the terminal cells.
- The use of neural network methods for detection has allowed reaching the industrial quality (with a probability of correct table recognition above 90 %), and the main focus of researchers has now shifted to the task of segmentation of tables in images of articles, books, reports, etc.

## Character and word recognition using artificial neural networks (3)

- Most of the methods and approaches to optical character recognition are based on artificial neural networks (ANNs).
- All methods used for line recognition can be divided into two large groups: methods with and without explicit segmentation of a text line into characters.
- When segmenting a text line, a bounding rectangle is constructed for each character, and the contents of the former are passed to the classifier. In this group of methods, segmentation is considered a more complicated task than classification.
- ANN can be built into segmentation algorithms.
- After text line segmentation, the classification of character images is performed. Convolutional neural networks (CNN) are mostly used for the latter. There are also approaches based on cascade ANNs, when the final response is based on the estimates of all the networks in the cascade.
- With the emergence of claims about the instability of segmentation algorithms on distorted images, approaches without explicit character-by-character segmentation began to appear. Nowadays, most of such approaches are based on sliding window classifiers [103] and recurrent neural networks (RNNs) [104], particularly, LSTM (networks with long short-term memory blocks).
- The text line recognition methods are often tailored to the peculiarities of writing. In this case, most studies have been and are being conducted for printed text with the English alphabet.

## Recognition results post-processing (3)

- The result of text document recognition can contain various errors: incorrect recognition of one or more word characters, segmentation errors of word boundaries, punctuation errors. Recognition accuracy can be improved by recognition results post-processing. The post-processing algorithms usually include two stages: error detection and further error correction.
- The rules embedded in the post-processing algorithms usually employ the information on the syntactic and semantic structure of the data being recognized. Syntactic rules describe constructions that are acceptable in terms of the recognition language. Semantic rules are based on the semantic interpretation of the data. Thus, from the language point of view, errors can be divided into those that result in non-existing words, and those where the wrong recognition result is acceptable for the language but contradicts the grammatical rules or context.

# Applications of document image analysis and recognition methods

## Extraction of attributes

- The most popular scenario for processing the document recognition results is the extraction of attributes (fields). The extracted data is transferred to the document management system. For example, the extracted attributes together with the image can be stored in a digital archive.
- The data to be extracted from texts usually includes the following objects:
    - meaningful object: the name of a person, a company name, etc. for news reports; a subject area term for a special text; a reference to literature for scientific and technical documents, etc;
    - attributes of the object, further characterizing it, for example, for a company this is the legal address, phone, name of the CEO, etc.
    - the relationship between objects: for example, the relationship "to be the owner" connects the company and the owner, "to be part of" connects the faculty and the university;
    - an event/fact that links several objects, e.g., the event "a meeting took place" includes meeting participants, as well as the place and time of the meeting.

## Document sorting

- In document management systems of large enterprises, one of the important tasks is sorting the flow of in coming documents in order to route them further. The task is usually complicated by the fact that the flow contains both single-page and multi-page documents.
- Inter-class similarity and intra-class document variability are pointed out as one of the main classification problems.
- Several groups of document classification methods are considered in [3]:
    - textual methods;
    - visual methods;
    - structural methods.
- Textual information analysis is based on global text descriptors such as Bag-of-Words (BOW), which is then analyzed by classical classifiers. The Bag-of-Words representation of a document can be replaced by more relevant models that take into account word order, such as statistically stable N-grams and vector word representations.
- Effective methods of textual information analysis are the application of probabilistic topic models designed to determine the topics of a collection of documents by representing each topic by a discrete distribution of word probabilities and each document by a discrete probability distribution of topics [126].
- Before constructing topic models of documents in natural language, normalization [127] is usually performed via several transformations: lemmatization, stemming, and others.
- Text-based methods employ optical character recognition (OCR) results. Due to text recognition errors, the use of text descriptors may result in decreased classification accuracy.
- Structural methods explicitly use the structure of a document defined in its design. The image is segmented into several physical or logical components, then mapped to a set of templates or to a set of graph descriptions.
- Template-matching methods use one or more templates that characterize each class. A similarity function between the image and the template is specified in advance.
- Unlike structural methods, visual methods implicitly describe the structure of a document image. Visual methods do not require preliminary image segmentation. Visual methods of image classification are divided into two categories: methods based on predefined features, and methods based on deep learning [3].
- Predefined features are usually local features or key points, discussed in detail in Section 1.3. Depending on the expected composition of the document flow, these features are analyzed in the Bag-Of-Features model (also called BOVW - Bag-Of-Visual-Words in this task, by analogy with the BOW model for text descriptors).
- The BOVW model allows for aggregation of local descriptors into a single vector but ignores the spatial location of "visual words", which leads to lower classification accuracy.
- But the most popular direction of document image classification is algorithms using convolutional neural networks. The typical architecture of CNNs used for this task includes two components. The first component consists of convolutional and subsampling layers and forms the input vector of deep features. The second component of CNNs is a multilayer perceptron, which classifies the feature vector.
- Hybrid methods combine textual methods with analysis of visual and /or structural features to classify document images.

## Document comparison

- Document images comparison is relevant when checking the correctness of signed paper documents, for example, when two parties sign contracts and agreements [137]. In this case, a detailed analysis of the document contents is required, as a change of even a single character may become critical for disputing the deal.
- Possible changes to the document may relate to both the content of the document and the layout of the document (font style, color, and text size), spatial arrangement of elements (line spacing). It is possible to add and delete content elements, including text, figures, graphs, tables, handwritten content (notes, signatures), stamps.
- The simplest comparison method is text recognition using OCR followed by the diff utility
based on the longest common subsequence (LCS) search to compare the recognition results for two documents [138]. The disadvantages of this method are a large number of false positives due to recognition errors and loss of information about the font, color, and text size. Also, text recognition cannot be used to compare seals, figures, and other non-text elements present in the document images.
- Another approach, which does not rely on character recognition, uses descriptors with pre-segmentation of text into text lines. In [137], dense SIFT descriptors were used. Segmentation of the document image not only into text lines but also into characters, as proposed in [139], can also be used.
- Another method for document images comparison relies on the visual similarity of documents. In [140], a visual similarity measure is proposed for document comparison, which uses document layout and text characteristics derived from text primitives: text block complexity, based on entropy, and clarity, dealing with font boldness. This measure of document image similarity can be used to classify documents and sort out similar documents.
- Document comparison is also employed for duplicates or near-duplicates search, for example, when constructing large datasets, documents corpora.
- In some cases, duplicates may refer to versions of a document obtained under different conditions [141]. Near-duplicates are, for example, images with the same textual content but different handwritten notes [142].
- Document images comparison can be employed to determine whether an image is a forgery, according to a predetermined set of data [145, 146]. […] A common problem in counterfeit detection is the lack of public datasets for algorithms evaluation. First, it is natural that forgers do not want to disclose their methods and the types of forgeries they have made. Second, most of the documents that are being modified contain personal information and are confidential.
# ViTs and More: Exploring Signature Forgery Verification

The detection and verification of signature forgeries are crucial in mitigating fraud and ensuring document authenticity. As digital documentation becomes prevalent, the risks associated with signature forgery escalate, highlighting the need for advanced verification techniques. Our research builds on the ChiSig benchmark, integrating Vision Transformers (ViTs) to push the boundaries of signature verification accuracy and efficiency.

## Dataset: ChiSig

To access the ChiSig dataset, please visit the [ChiSig submodule](https://github.com/dskezju/ChiSig.git).

Utilizing the ChiSig dataset, our study analyzes over 10,242 signature images from 500 unique names. The dataset categorizes forgeries and originals systematically, aiding in precise and structured analysis.

### Data Manipulation

We divided the dataset into training (70%), testing (15%), and validation (15%) subsets, ensuring a balanced approach to model training and evaluation. Image normalization and resizing to 224x224 pixels were critical steps in preparing the data for processing by deep learning models.

## Experimentation

Our methodology involves comparing embeddings from five models: ResNet50, InceptionResnet, ResNeXt50, VGG16, and ViT. We calculate cosine similarity between signature pairs to verify authenticity, focusing on metrics such as Accuracy, Equal Error Rate (EER), and True Acceptance Rate (TAR).

### Architectures

- ResNet50: A deep network with residual blocks to combat the vanishing gradient problem.
- InceptionResnet: Combines Inception's depth and width with ResNet's residual connections.
- ResNeXt50: Introduces "cardinality" as a new dimension to enhance feature learning.
- VGG16: Known for its depth, capturing detailed image patterns.
- ViT: Applies the transformer framework to image processing, focusing on global context and long-range dependencies.

### ViT
For signature verification, ViT dissects each signature image into a grid of fixed-size patches. Each patch is then flattened and projected into an embedding space, creating a sequence of embeddings that represents the signature. This sequence is processed through multiple layers of transformer architecture, utilizing self-attention mechanisms to capture intricate relationships between different parts of the signature.

This method allows ViT to analyze the global context of the signature, recognizing patterns and structures that span across the entire image. Such an approach is fundamentally different from conventional convolutional neural networks (CNNs), which primarily focus on local features. By understanding the holistic view of the signature, ViT can detect subtle nuances and variations that are indicative of forgeries.

Figure 2 below illustrates how ViT performs on signature data, showcasing the process of dividing the signature image into patches, analyzing these patches through the transformer layers, and deriving insights that facilitate the verification of signature authenticity.

<p align="center">
  <img src="images\Vit_patches.PNG" alt="Alt text" title="Optional title" />
</p>

### Evaluation & Results 
- Accuracy (Acc): Measures the system's precision in identifying genuine and forged signatures.
- Equal Error Rate (EER): Indicates the system's balance between false acceptances and rejections.
- True Acceptance Rate (TAR) at FAR of 0.1%: Assesses the system's ability to authenticate genuine signatures at a stringent false acceptance threshold.

Our evaluation of different embedding models for signature verification yielded the following key metrics, summarized in Table 1.

<p align="center">
  <img src="images\Results.PNG" alt="Alt text" title="Optional title" />
</p>

Our exploration into Vision Transformer (ViT) for signature verification reveals its innovative capacity to process images as sequences of patches, offering a fresh perspective compared to traditional CNN approaches. Despite ViT's slightly lower accuracy of 81.26% compared to InceptionResnet's 85.29%, its application signifies a significant leap in detecting sophisticated forgeries, evidenced by its unique analysis of global context and long-range dependencies. This project underscores the potential of Vision Transformers in enhancing signature forgery detection, supported by comprehensive experiments and evaluations.

## How to Use This Repository
### Installation

Use the package manager [conda](https://docs.anaconda.com/free/miniconda/) to install foobar.

```bash
conda env create -f signature_verification_env.yml
```

The details for proper data manipulation and evluation are given in detail in the [corresponding paper](/ViTs%20and%20More%20-%20Exploring%20Signature%20Forgery%20Verification-1.pdf). 

*This project was created as the final project for CS427 - Introuction to Artificial Intelligence at KAIST.
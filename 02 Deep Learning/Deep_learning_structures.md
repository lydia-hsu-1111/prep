# Neural Network Architectures Overview

## 1. Feedforward Neural Network (FNN / MLP)
- **Use Case**: Classification/regression on tabular data.
- **Structure**: Fully connected layers (dense layers), no memory or recurrence.
- **Example**: Predict housing prices, MNIST digit classification.

---

## 2. Convolutional Neural Network (CNN)
- **Use Case**: Image, video, spatial data.
- **Structure**: Uses convolutional layers to extract local patterns (edges, textures).
- **Variants**:
  - LeNet (early CNN)
  - AlexNet (ImageNet breakthrough)
  - VGG (deep but simple)
  - ResNet (residual connections for very deep networks)
  - Inception/GoogLeNet (multi-scale filters)
- **Example**: Image classification, object detection.

---

## 3. Recurrent Neural Network (RNN)
- **Use Case**: Sequential data (text, time series).
- **Structure**: Processes input sequentially with memory of previous steps.
- **Variants**:
  - Vanilla RNN (simple, suffers from vanishing gradients)
  - LSTM (Long Short-Term Memory)
  - GRU (Gated Recurrent Unit)
- **Example**: Text generation, time-series forecasting.

---

## 4. Transformer
- **Use Case**: NLP, vision, audio, time-series.
- **Structure**: Based entirely on self-attention; no recurrence or convolution.
- **Variants**:
  - BERT (encoder-only for understanding)
  - GPT (decoder-only for generation)
  - T5, BART (encoder-decoder for seq2seq)
  - ViT (Vision Transformer)
- **Example**: Chatbots, summarization, translation, image classification.

---

## 5. Autoencoder
- **Use Case**: Dimensionality reduction, denoising, anomaly detection.
- **Structure**: Encoder → bottleneck → decoder.
- **Variants**:
  - Denoising Autoencoder
  - Variational Autoencoder (VAE) — probabilistic version.
- **Example**: Reconstruct input, latent space learning.

---

## 6. Generative Adversarial Network (GAN)
- **Use Case**: Generating new samples (images, text).
- **Structure**: Generator vs. Discriminator (two networks in adversarial training).
- **Variants**:
  - DCGAN (convolutional GAN)
  - CycleGAN (image-to-image translation)
  - StyleGAN (photo-realistic face generation)
- **Example**: Generate fake images, art synthesis.

---

## 7. Graph Neural Networks (GNN)
- **Use Case**: Graph-structured data (social networks, molecules).
- **Structure**: Learns over nodes, edges, and their relations.
- **Variants**:
  - GCN (Graph Convolutional Network)
  - GAT (Graph Attention Network)
- **Example**: Node classification, link prediction.

---

## 8. Attention Mechanisms
- **Used in**:
  - Transformers (self-attention)
  - RNNs (sequence-to-sequence models with attention)
  - Image models (visual attention)
- **Purpose**: Allow model to focus on relevant parts of input.

---

## Optional: Hybrid Architectures
- CNN + RNN (e.g., for video)
- Transformer + CNN (e.g., DETR for object detection)
- RNN + Attention (e.g., translation)

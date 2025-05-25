# 🧠 Introduction to Deep Learning Structures

Deep learning models are built using layers of neurons that automatically learn representations from data. This guide introduces core structures commonly used in deep learning architectures.

---

## 📚 1. Perceptron

- Simplest neural unit.
- Takes weighted input, applies an activation function.

**Formula:**

```
output = activation(w₁x₁ + w₂x₂ + ... + b)
```

---

## 🧱 2. Feedforward Neural Network (FNN)

- Also called Multi-Layer Perceptron (MLP).
- Data flows in one direction: input → hidden layers → output.
- Common for structured data (e.g., tabular).

**Diagram:**

```
Input → [Hidden Layer(s)] → Output
```

---

## 🔁 3. Convolutional Neural Network (CNN)

- Specializes in grid data like images.
- Uses convolutional layers to extract local features.

**Typical Layers:**

- Convolution
- ReLU
- Pooling (e.g., MaxPool)
- Fully connected (FC)

**Use Cases:**

- Image classification
- Object detection

---

## 🔄 4. Recurrent Neural Network (RNN)

- Processes sequences of data.
- Output depends on current input and previous hidden state.

**Equation:**

```
hₜ = f(Wxₜ + Uhₜ₋₁ + b)
```

**Limitation:**

- Struggles with long-term dependencies.

---

## 🧠 5. Long Short-Term Memory (LSTM)

- A type of RNN with gates:
  - **Input gate**
  - **Forget gate**
  - **Output gate**
- Handles long-term dependencies better.

---

## ⚡ 6. Transformer

- Eliminates recurrence using **self-attention**.
- Processes entire sequence in parallel.
- Backbone of models like BERT, GPT.

**Components:**

- Multi-head attention
- Positional encoding
- Feedforward layers

**Advantages:**

- Faster training
- Captures global dependencies

---

## 🧮 7. Autoencoder

- Unsupervised learning structure for compression.
- Learns to encode and reconstruct input.

**Architecture:**

```
Input → Encoder → Bottleneck → Decoder → Output
```

**Use Cases:**

- Denoising
- Anomaly detection

---

## 🔄 8. Generative Adversarial Network (GAN)

- Two networks:
  - **Generator** creates fake data.
  - **Discriminator** distinguishes real from fake.
- Compete in a zero-sum game.

**Training Goal:**

```
Generator tries to fool the Discriminator.
```

---

## 📈 9. Graph Neural Network (GNN)

- Operates on graph-structured data.
- Nodes pass messages to neighbors to learn representations.

**Applications:**

- Social networks
- Molecule classification
- Recommendation systems

---

## 🔚 Summary Table

| Structure     | Use Case         | Key Feature             |
|---------------|------------------|--------------------------|
| MLP           | Tabular data     | Fully connected          |
| CNN           | Image data       | Convolutions             |
| RNN           | Sequences        | Recurrent states         |
| LSTM          | Long sequences   | Memory cells             |
| Transformer   | Language, vision | Self-attention           |
| Autoencoder   | Compression      | Bottleneck layer         |
| GAN           | Generation       | Adversarial training     |
| GNN           | Graph data       | Message passing          |

---

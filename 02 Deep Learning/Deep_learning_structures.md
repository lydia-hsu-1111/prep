# Neural Network Architectures Overview (with Code Snippets)

## 1. Feedforward Neural Network (FNN / MLP)
- **Use Case**: Classification/regression on tabular data.
- **Structure**: Fully connected layers (dense layers), no memory or recurrence.

```python
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense

model = Sequential([
    Dense(64, activation='relu', input_shape=(input_dim,)),
    Dense(64, activation='relu'),
    Dense(1)  # or Dense(num_classes, activation='softmax') for classification
])
model.compile(optimizer='adam', loss='mse')  # or categorical_crossentropy
```

---

## 2. Convolutional Neural Network (CNN)
- **Use Case**: Image, video, spatial data.

```python
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Conv2D, MaxPooling2D, Flatten, Dense

model = Sequential([
    Conv2D(32, kernel_size=(3, 3), activation='relu', input_shape=(28, 28, 1)),
    MaxPooling2D(pool_size=(2, 2)),
    Flatten(),
    Dense(64, activation='relu'),
    Dense(10, activation='softmax')
])
```

---

## 3. Recurrent Neural Network (RNN)
- **Use Case**: Sequential data (text, time series).

```python
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import SimpleRNN, Dense

model = Sequential([
    SimpleRNN(50, input_shape=(timesteps, features)),
    Dense(1)
])
```

**LSTM Variant**:
```python
from tensorflow.keras.layers import LSTM

model = Sequential([
    LSTM(50, input_shape=(timesteps, features)),
    Dense(1)
])
```

---

## 4. Transformer (via Hugging Face for simplicity)
- **Use Case**: NLP, vision, audio, time-series.

```python
from transformers import AutoModelForSequenceClassification, AutoTokenizer

tokenizer = AutoTokenizer.from_pretrained("bert-base-uncased")
model = AutoModelForSequenceClassification.from_pretrained("bert-base-uncased")
```

---

## 5. Autoencoder

```python
from tensorflow.keras.models import Model
from tensorflow.keras.layers import Input, Dense

input_layer = Input(shape=(784,))
encoded = Dense(128, activation='relu')(input_layer)
bottleneck = Dense(64, activation='relu')(encoded)
decoded = Dense(128, activation='relu')(bottleneck)
output_layer = Dense(784, activation='sigmoid')(decoded)

autoencoder = Model(inputs=input_layer, outputs=output_layer)
```

---

## 6. Generative Adversarial Network (GAN)

```python
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense

# Generator
generator = Sequential([
    Dense(128, activation='relu', input_dim=100),
    Dense(784, activation='sigmoid')
])

# Discriminator
discriminator = Sequential([
    Dense(128, activation='relu', input_dim=784),
    Dense(1, activation='sigmoid')
])
```

---

## 7. Graph Neural Networks (GNN) using PyTorch Geometric

```python
import torch
from torch_geometric.nn import GCNConv

class GCN(torch.nn.Module):
    def __init__(self, in_channels, hidden_channels, out_channels):
        super().__init__()
        self.conv1 = GCNConv(in_channels, hidden_channels)
        self.conv2 = GCNConv(hidden_channels, out_channels)

    def forward(self, x, edge_index):
        x = self.conv1(x, edge_index).relu()
        x = self.conv2(x, edge_index)
        return x
```

---

## 8. Attention Mechanism (Basic)

```python
import torch.nn.functional as F

def attention(query, key, value):
    scores = query @ key.transpose(-2, -1) / key.size(-1) ** 0.5
    weights = F.softmax(scores, dim=-1)
    return weights @ value
```

---

## Optional: Hybrid Architectures

**CNN + RNN**:
```python
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import TimeDistributed, Conv2D, MaxPooling2D, LSTM, Flatten

model = Sequential([
    TimeDistributed(Conv2D(32, (3, 3), activation='relu'), input_shape=(timesteps, 64, 64, 3)),
    TimeDistributed(MaxPooling2D((2, 2))),
    TimeDistributed(Flatten()),
    LSTM(50),
    Dense(1)
])
```

**Transformer + CNN (DETR-like)**: Use PyTorch and prebuilt models from `torchvision` or HuggingFace.

---

## Simple Autoencoder in TensorFlow

```python
import tensorflow as tf
from tensorflow.keras import layers, models

# Define the Autoencoder
def build_autoencoder(input_dim, hidden_dim):
    input_layer = layers.Input(shape=(input_dim,))
    # Encoder
    encoded = layers.Dense(hidden_dim, activation='relu')(input_layer)
    # Decoder
    decoded = layers.Dense(input_dim, activation='sigmoid')(encoded)  # Use sigmoid if input is normalized
    autoencoder = models.Model(inputs=input_layer, outputs=decoded)
    autoencoder.compile(optimizer='adam', loss='mse')
    return autoencoder

# Example usage
import numpy as np

# Sample data: 1000 samples, 64 features
X = np.random.rand(1000, 64).astype(np.float32)

# Build and train
autoencoder = build_autoencoder(input_dim=64, hidden_dim=32)
autoencoder.fit(X, X, epochs=20, batch_size=32, shuffle=True)
```

## Pytorch

```python
import torch
import torch.nn as nn
import torch.optim as optim
from torch.utils.data import DataLoader, TensorDataset

# Define the Autoencoder
class Autoencoder(nn.Module):
    def __init__(self, input_dim, hidden_dim):
        super(Autoencoder, self).__init__()
        self.encoder = nn.Sequential(
            nn.Linear(input_dim, hidden_dim),
            nn.ReLU()
        )
        self.decoder = nn.Sequential(
            nn.Linear(hidden_dim, input_dim),
            nn.Sigmoid()  # or nn.ReLU() for non-bounded output
        )

    def forward(self, x):
        encoded = self.encoder(x)
        decoded = self.decoder(encoded)
        return decoded

# Example usage
if __name__ == "__main__":
    # Sample data (1000 samples, 64 features)
    X = torch.randn(1000, 64)
    dataset = TensorDataset(X)
    dataloader = DataLoader(dataset, batch_size=32, shuffle=True)

    model = Autoencoder(input_dim=64, hidden_dim=32)
    criterion = nn.MSELoss()
    optimizer = optim.Adam(model.parameters(), lr=1e-3)

    # Training loop
    for epoch in range(20):
        for batch in dataloader:
            data = batch[0]
            output = model(data)
            loss = criterion(output, data)
            optimizer.zero_grad()
            loss.backward()
            optimizer.step()
        print(f"Epoch {epoch+1}, Loss: {loss.item():.4f}")
```

## VAE in TensorFlow
```python
import tensorflow as tf
from tensorflow.keras import layers, Model
import numpy as np

# Sampling layer (reparameterization trick)
class Sampling(layers.Layer):
    def call(self, inputs):
        z_mean, z_log_var = inputs
        eps = tf.random.normal(shape=tf.shape(z_mean))
        return z_mean + tf.exp(0.5 * z_log_var) * eps

# VAE model
class VAE(Model):
    def __init__(self, input_dim, latent_dim):
        super(VAE, self).__init__()
        self.encoder = self.build_encoder(input_dim, latent_dim)
        self.decoder = self.build_decoder(input_dim, latent_dim)

    def build_encoder(self, input_dim, latent_dim):
        inputs = layers.Input(shape=(input_dim,))
        x = layers.Dense(64, activation='relu')(inputs)
        z_mean = layers.Dense(latent_dim)(x)
        z_log_var = layers.Dense(latent_dim)(x)
        z = Sampling()([z_mean, z_log_var])
        return Model(inputs, [z_mean, z_log_var, z], name="encoder")

    def build_decoder(self, input_dim, latent_dim):
        latent_inputs = layers.Input(shape=(latent_dim,))
        x = layers.Dense(64, activation='relu')(latent_inputs)
        outputs = layers.Dense(input_dim, activation='sigmoid')(x)
        return Model(latent_inputs, outputs, name="decoder")

    def compile(self, optimizer):
        super(VAE, self).compile()
        self.optimizer = optimizer
        self.total_loss_tracker = tf.keras.metrics.Mean(name="loss")

    def train_step(self, data):
        if isinstance(data, tuple):
            data = data[0]
        with tf.GradientTape() as tape:
            z_mean, z_log_var, z = self.encoder(data)
            reconstruction = self.decoder(z)
            reconstruction_loss = tf.reduce_mean(tf.reduce_sum(tf.square(data - reconstruction), axis=1))
            kl_loss = -0.5 * tf.reduce_mean(tf.reduce_sum(
                1 + z_log_var - tf.square(z_mean) - tf.exp(z_log_var), axis=1))
            total_loss = reconstruction_loss + kl_loss
        grads = tape.gradient(total_loss, self.trainable_weights)
        self.optimizer.apply_gradients(zip(grads, self.trainable_weights))
        self.total_loss_tracker.update_state(total_loss)
        return {"loss": self.total_loss_tracker.result()}
```

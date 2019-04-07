---
layout: default
title: "Autoencoders"
---

Analysis Scale: 3

# Autoencoder / Auto-associative


An MLP which has as targets the inputs. Create a bottleneck hidden layer to represent all of the information of the input. This way the hidden layer of the MLP are finding a differ representation of the input data to extract important components and ignoring the noise. This can be useful for data compression and reconstruction of noisy images.

If all the nodes have linear activations then the representation that the network learns to compute is the Principal Components of the data. PCA is a very useful dimensionality reduction technique.


"When the decoder is linear and L is the mean squared error an undercomplete autoencoder learns to span the same subspace as PC.

In this case, an autoencoder trained to perform the copying task has learned the principal subspace of the training data as a side effect.

Autoencoders with nonlinear encoder functions f and nonlinear decoder functions g can thus learn a more powerful nonlinear generalization of PCA

---
layout: default
title: "Autoencoders"
---

<div style="text-align: right"> <i> Analysis Scale: 2 </i> </div>

##  An introduction to Auto-encoders

If we were to describe what an autoencoder is in just a small sentence then we could say "Its an MLP which has as output targets, its inputs". An auto-encoder then creates a bottleneck hidden layer to represent all of the information of the input. This way the hidden layer finds a different representation of the input data to extract important components and to ignore the noise. This can be useful for data compression and reconstruction of noisy images. *Fun fact!*: If all the nodes have linear activations then the representation that the network learns to compute is the Principal Components of the data. PCA is a very useful dimensionality reduction technique. Autoencoders with nonlinear encoder functions f and nonlinear decoder functions g can thus learn a more powerful nonlinear generalization of PCA

Their main usage is:
- Dimensionality reduction
- Feature Learning
- Generative modelling (through latent variable representation)

Also, in the era before ReLUs, transfer learning (around 2007?) and other nice tricks to combat the vanishing gradients problem, it was very popular to pre-train greedily layer by layer a Deep Neural Network by using a stack of shallow auto-encoders.  

### Types of Auto-encoders


#### Under-complete

An auto-encoder whose code dimension is less than the input dimension is called under-complete. Learning an under-complete representation forces the auto-encoder to capture the most salient features of the training data. When the decoder is linear and L is the mean squared error, an under-complete auto-encoder learns to span the same subspace as PCA. In this case, an auto-encoder trained to perform the copying task has learned the principal subspace of the training data as a side-effect.

#### Over-complete

On the other hand, an over-complete auto-encoder is defined when the hidden code has dimension greater than the input. In these cases, even a linear encoder and linear decoder can learn to copy the input to the output without learning anything useful about the data distribution.

To tackle this we use **Regularized auto-encoders** which provide the ability to do so. Rather than limiting the model capacity by keeping the encoder and decoder shallow and the code size small, regularized autoencoders use a loss function that encourages the model to have other properties besides the ability to copy its input to its output. These other properties include sparsity of the representation, smallness of the derivative of the representation, and robustness to noise or to missing inputs. A regularized autoencoder can be nonlinear and
overcomplete but still learn something useful about the data distribution even if the model capacity is great enough to learn a trivial identity function.


#### Sparse Auto-encoders

Sparse autoencoders are typically used to learn features for another task such as classification. An autoencoder that has been regularized to be sparse must respond to unique statistical features of the dataset it has been trained on, rather than simply acting as an identity function. In this way, training to perform the copying task with a sparsity penalty can yield a model that has learned useful features as a byproduct. *Penalizing non‐sparse solutions can be seen as adding latent variables with a prior and maximising likelihood*

#### Denoising Auto-encoders

In simple terms, they try to minimize a function but using a corrupted input. Denoising autoencoders must therefore undo this corruption rather than simply copying their input


#### Deep Auto-encoders

One major advantage of non-trivial depth is that the universal approximator theorem guarantees that a feedforward neural network with at least one hidden layer can represent an approximation of any function (within a broad class) to an arbitrary degree of accuracy, provided that it has enough hidden units. This means that an autoencoder with a single hidden layer is able to represent the identity function along the domain of the data arbitrarily well. However, the mapping from input to code is shallow. This means that we are not able to enforce arbitrary constraints, such as that the code should be sparse. A deep autoencoder, with at least one additional hidden layer inside the encoder itself, can approximate any
mapping from input to code arbitrarily well, given enough hidden units. 

### Other Notes

When training autoencoders there needs to be a compromise between 1 and 2
1. Need to approximately recover x – reconstruction force
2. Need to satisfy the regularization term – regularisation force.

- Depth can exponentially reduce the computational cost of representing some functions. 

- Depth can also exponentially decrease the amount of training data needed to learn some functions.


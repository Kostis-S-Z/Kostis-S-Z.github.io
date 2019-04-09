---
layout: default
title: "Some FUNdamentals _(AS:3)_"
---

<div style="text-align: right"> <i> Analysis Scale: 3 </i> </div>

## _Motivation for Machine Learning_

* Data with many dimensions are difficult to process for humans
* Reducing the dimensionality in a human-acceptable level can cause information loss and confusion
* Just too many data to process

_Final **Goal** is for machines to **Learn** which is a sign of **Intelligence**_

* Learning comes from data, specifically by extracting useful information out of them and then being able to **generalise** to more unseen data, scenarios, situations etc.

* Intelligence is also _reasoning_ and _logical deduction_ but even though this might be considered AI it is not ML.

A Machine Learning algorithm basically consists of: 
- A dataset
- A cost / error function
- An optimization procedure
- A model


## _Types of ML_

### Supervised Learning

A training set of examples that comes with the correct answers (targets) is provided and based on that the algorithm learns to generalise to respond correctly to all possible inputs. Ability to generalise and withstand noise

#### Regression _(aka: function approximation, interpolation)_

Trying to predict a value between values we know / fitting a mathematical function (a curve) that passes through all of our datapoints

#### Classification _(its discrete)_

Given an input vector decide in which of the N classes it belongs to based on the training examples

### Unsupervised Learning

The goal here is for the algorithm to identify similarities between the inputs. Correct responses (targets) thus are not provided and the algorithm tries to find what things the inputs might have in common in order to categorise them together.

### Reinforcement Learning

The algorithm gets told when the answer it provides is wrong but not how to correct it. Then the algorithm explores and tries different possibilities until the answer is correct.

## _A distinction between two types of models_

### Generative models

This type of classifiers focus on how the data were generated in order to classify them correctly. It finds the category the data mostly like belong to based on how they were generated. Given an observable variable X and a target variable Y, a generative model is a statistical model of the joint probability distribution on X × Y


### Discriminative models

On the other hand, discriminative models do not care about how the data were generated, they simply predict given a signal. A discriminative model is a model of the conditional probability of the target Y, given an observation X


## _Definitions of words that you will hear often_

* **Activation function** : In a neural network, g(x) is a mathematical function that describes the firing of the neuron (when the neuron is fired) as a response to the weighted inputs. Examples: threshold function, sigmoid etc

* **Error** : a function that computes the inaccuracies of the network as a function of the outputs y and the targets t.

* **Input vector** : One sample that contains _ number of features / elements / attributes . 

* **Test set** : In order to examine if the algorithm is able to generalise to examples outside of the training set, a different dataset is needed. When we use the test set, the network gives an output without changing its weights / parameters. The test set is the correct way to measure how well an algorithm has learnt

* **Overfitting** : The goal of the algorithm is to be trained enough in order to generalise well. If we train for too long, then noise and inaccuracies in the data are also learnt together with the actual function, leading to a very complicated model with poor generalisation abilities. The model will have memorised the learning examples and the noise that comes with them.

* **Underfitting** : On the other hand, if the model is too simple or not trained for a sufficient amount of time (which is common enough), then it will under perform and lead to bad results, even random.

***Overfitting and Underfitting are both equally dangerous and harmful when training a model***

* **The confusion matrix (classification)** : Is a matrix that tells us how many samples from each class were classified in each class. By dividing the sum of the elements of the leading diagonal by the sum of all the elements of the matrix you get accuracy.

* **_Metrics_** :
 
  - Accuracy: The sum of correctly classified samples (from both classes) divided by the total number of samples.

  - Recall or Sensitivity (true positive rate): Ratio of how many from the positive class where predicted correctly 

  -  ROC Curve for classifier comparison
          Perfect classifier -> (0, 1)
          All wrong classifier -> (1, 0)
          Random -> a diagonal line

  -  Matthew’s Correlation Coefficient (MCC) for binary classification: When you have an imbalanced dataset (more examples one class than another) you need to calculate a balanced accuracy

* **Curse of dimensionality** : As the number of dimensions tends to infinity, the volume of the hypersphere tends to zero

* **Trueness** : The average distance between the correct output and the prediction

* **Bias - Variance Tradeoff** : The more degrees of freedom the algorithm has, the more complicated the model that can be fitted. A model can be bad in one of two ways:
  -  High bias: It is not accurate and cannot match the data well enough. The model will be very simple and will show signs of underfitting. (A straight line to separate classes)

  -  High variance: It is not very precise and there is a lot of variation in the results. The model will be very complex and will have overfitted the training data. (One weight to each point)

  -  Complex classifiers will improve bias but will have high variance. -> Using a high degree polynomial curve
Making the model more specific will reduce the variance but increase the bias. -> Using a straight line.

## _A glimpse into Neural Networks_

_Based on neurons that make synapses and are able to change / adapt._

* **Hebb’s rule** : If two neurons fire simultaneously all the time then the connection between them gets stronger (Pavlov’s dog), if they never fire simultaneously then the connection dies. 

* **McCulloch and Pitts Neuron** consists of:
  -  A set of weighted inputs
  -  An adder
  -  An activation function

    The inputs x_i are multiplied by the weights w_i and the neuron sums their values.
    This sums is then passed through the activation function (threshold function with θ) that dictates if the neuron will fire or not. Imagine input data flowing through synapses that have strengths (weights) which indicate how important each synapse is to the neuron.

  -  **Note**: _The McCulloch and Pitts neuron isn’t very realistic. They may not add up the inputs linearly. Most importantly they do not output one value, but a spike train!_


* **Perceptron**: A one layer fully connected Neural Network.

The input nodes show the number of features fed to the neurons.
The lines are the synapses where each line represents a weight from the specific input value to the specific neuron. If you have M number of features and N neurons then you have MxN number of weights.
All neurons are independent of each other. Even weights of a neuron are independent of each other.

-  If a neuron is correct, great :)
-  If not we need to change the weights somehow, so the next time it will be correct.

This is determined by the learning method which ultimately is how you calculate the error.

### Learning Method:

The update of the weights: $$ w_{ij} = w_{ij} - \Delta w_{ij} $$

#### Perceptron: Find the weights that fit exactly the correct solution (y=t)

$$ \Delta w = - \eta * (y_j - t_j) * x_i $$ where y: the predictions of the model and t: the targets (ground truth) 

#### Delta Rule: Try to minimise the error based on its gradient (this is a hint about the famous gradient descent used in multilayer networks!)

_Use the output of the neuron **before** the activation function_

e = t - wx

_Set the error function as following_

$$ \epsilon = \frac{e^2}{2} $$

_Take the derivative of the error function_

$$ \frac{\delta \epsilon}{\delta w} = e \frac{\delta e}{\delta w} = e \frac{\delta (t-wx)}{\delta w} = -e * x $$

$$ \Delta w = - \eta * e * x $$

_Some notes regarding the gradient:_

- For a thresholded input, the gradient would be 0, that is why we take the unthresholded input

- For a linear input, the gradient is always 1

- There are more activation functions (non linear) that can provide us with the direction of the error (since the gradient i not just 1).

* **Learning rate (η)** : Parameters that controls how much the weights are going to be updated at each epoch. Setting this parameter to 1 (meaning ignore it) leads to an unstable model. Small values means that the NN needs to the see the input multiple times meaning longer convergence time but also is more robust to noise and inaccuracies to the data.

* **Bias** : When we want to update when a neuron will fire, in addition to changing the weights we might want to change the threshold of the activation function. Imagine a case where we want one neuron to fire and another to not fire. If the inputs to the neurons are zero then they will both output zero since the values of their weights won't matter when multiplied with zero.
In order to make the threshold adjustable, we define another input weight called bias, with a value of -1. 

* **Complexity**: At each iteration the algorithm loops over neurons and each neuron over the inputs. Each iteration then is O(mn). For T iterations it is O(T*mn)

* **Limitations of Perceptron** 

- Linear Separability: Separate the cases when the neuron should fire and when it should not. Meaning finding a decision boundary (line in 2D, plane in 3D etc) where in one side it fires and in the other it doesn’t. For each neuron there is a boundary where xw (their inner product) >= 0 makes that neuron fire. 
So for linearly separable data, Perceptron will converge to a correct solution in a finite number of iterations.
But for a simple case, even as XOR, Perceptron is unable to find a solution in 2D. However, XOR is linearly separable in 3D, so by adding a third input feature making the data 3D we are able to solve this problem.

- Quality of Output: The perceptron also stops whenever the training data are classified correctly without taking into account how well they are split, meaning if the decision boundary margin is the largest possible. Because delta rule tries to minimize the error, it will actually try to find the largest possible margin.


***It is always possible to separate two classes with a linear function provided you project the data in the correct number of dimensions. (for this checkout SVM)***

* **Scaling the input data / Normalization / Standarization**:

  -  Treat each dimension independently.
  -  Two very simple (and common) methods are:
      1. make each dimension to have a zero mean and a unit variance 
      2. scale them that max value is 1 and min value is -1

  -  Normalization should be done in the training data and in the test data in the same way (same mean and variance)!

It is common to turn classification problems into regression problems. Two ways to do it:
Introduce an indicator variable which says in which class each datapoint belongs and then try to predict this variable
Repeated regression, once for each class, with the indicator being one for all examples in this class and 0 for all the others.



## _Nice Quotes_

> _The question of which features to choose is not always an easy one._

> _Computers don't care about number of dimensions._

> _Under-training and over-training are equally dangerous._
 
 
### Sources:

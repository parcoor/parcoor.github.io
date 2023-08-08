---
layout: post
title: Presenting NNC - Neural Network Library in C by Parcoor 
subtitle: An opensource library for lightweight neural network in C, for every device and platform
tags: [opensource deep-learning]
---

Parcoor is glad to release the first version of NNC - our deep learning
framework. NNC is open-sourced under
[GPL-v3](https://www.gnu.org/licenses/gpl-3.0.en.html) licence. The source code 
is available on its [Github repo](https://github.com/parcoor/nnc/). 
Any contribution is warmly welcome. 

NCC is coded entirely in C with no dependence to external library (other than
standard), thus making it highly portable to nearly any device.

## Short presentation
NNC allows to build, train, persist, deploy
neural networks everywhere, quite easily and intuitively. NNC is being built 
with resource efficiency in mind. It also allows fine granularity in the 
observation of the inner work of the neural network in real-time.

NNC ambitions to become to deep learning what
[sqlite](https://www.sqlite.org/index.html) is to databases: a minimalistic -
yet full-fledged solution, embeddable everywhere.

So far, this first release implements:
- only fully connected dense layers
- most common weight initialization strategies: Glorot uniform / gaussian etc.
- only SGD optimizer
- most common layer activation functions (ReLu, tanh, sigmoid...)
- most common loss functions: MSE, binary cross-entropy etc.

## Motivation
The most common deep learning frameworks like
[Tensorflow](https://www.tensorflow.org/) or [PyTorch](https://pytorch.org/)
are extremely powerful - but somehow also very complex, and kind of an overkill
in many cases. Shipping their models to embedded devices is also a tedious and
quite error-prone task. Those frameworks were developed with deployment on the
cloud (or on powerful servers) in mind. They are to deep learning what postgres or
mysql are to databases. 

A minimalistic, lightweight, intuitive framework easily
allowing fine-granular control was still missing. 
That is why we started developing NNC.

## Usage
### Basics
Creating a simple neural network takes just a few lines of code:

```c
network nk;
uint16_t max_n_layers = 3;

init_network(&nk, max_n_layers);
addinit_layer(&nk, 2, 3, GLOROT_UNIFORM_INIT, SIGMOID_ACT);
addinit_layer(&nk, 0, 3, GLOROT_UNIFORM_INIT, RELU_ACT);
addinit_layer(&nk, 0, 1, GLOROT_UNIFORM_INIT, SIGMOID_ACT);
```
The function `init_network()` initializes the (neural) network previously
declared with the maximum number of layer it can contain. 

The function `addinit_layer()` initializes a new fully connected dense layer,
taking as parameters:
1. the input size. Relevant only for the first layer. For the following
   layers, it is set automatically to match the output size of the previous
   layer
2. the output size - or equivalently - the number of neurons the layer contains
3. the weight initialization strategy
4. the activation function of the layer

For forwarding an input batch through the network:
```c
batch_forward(&nk, batch_s, input_s, X, output_s, y_pred);
```
where `batch_s` is the batch size, `input_s` the input size (must match the
input size of the first layer of the network), `X` is an array of size
`(batch_s, input_s)` containing the batch values, `output_s` is the output size
(must match the output size of the last layer of the network) and `y_pred` is an
array of size `(batch_s, output_s)` that will store the output of this forward
pass.

For operating a back-propagation pass, we first have to compute the error of
the output:
```c
loss_batch(BINARY_CROSS_ENTROPY_LOSS, batch_s, output_s, y_pred, y_true, true, error);
```
where the first argument is the loss function used, `y_true` is an array of the
same size than `y_pred` containing the true output values, `true` is a boolean
telling to use the derivative of the loss function (mandatory for use in
backpropagation) and `error` is an array the same size than `y_pred` that will contain
its error (as computed by the loss function).

Then you can proceed with the backpropagation itself:
```c
backpropagation_batch(&nk, batch_s, output_s, error, input_s, X, lr);
```
(`lr` being the learning rate) that will update accordingly the network's
weights and biases.

This syntax is (hopefully) not so complicated, and allows quite simply many
variations like training with cyclical learning rates, storing the training
history etc. as shown in [those full-code
examples](https://github.com/parcoor/nnc/tree/main/examples).

### Persisting
Saving a network on the disk for future reload is also quite easy:
```c
persist_network(&nk, network_fp);
```
where `network_fp` is the path where the network will be stored.

The network is then stored in a text file, almost in plain English:
```
=== Network
Max Number of Layers: 3
Current Number of Layers: 3
== Layer 1
Input Size: 5
Number of Neurons: 7
Activation: ReLu
= Neuron 1
Input size: 5
weights: [0.222638, 0.298208, -0.101303, 0.288833, -0.052172]
biases: [0.354045, -0.226585, -0.009729, 0.344690, -0.163823]
= Neuron 2
Input size: 5
weights: [-0.155720, 0.327395, -0.010867, 0.156187, 0.139521]
biases: [-0.102826, -0.352790, 0.304954, -0.272849, 0.157624]
...
```

If you want to experiment, you can modify the weights, the activation function
or whatever in this file.

To load a network from such a file:
```c
load_network(&loaded_nk, network_fp);
```
and `loaded_nk` is ready to go.


### Introspection
It is also pretty easy to access the parameters within a network. For example,
the 3rd weight of the 5th neuron in the 2nd layer is accessible through
```c
nk->layers[1]->neurons[4]->weights[2];
```
(N.B.: indexing starts at 0. Replace `->` by `.` if `nk` is the network itself,
and not a pointer to it).

After a backpropagation pass, you can check the *delta* value associated to
this neuron through:
```c
nk->layers[1]->delta[4];
```

## Conclusion
NNC allows to build, train, store, use neural networks in a pretty easy and
intuitive way. We hope - and think - it can be useful for engineers dealing
with limiting resources and wanting to solve relative simple tasks with neural
networks. 

We also think this framework can be useful to teachers and students, through making
the inner-work of a neural network easily observable, enabling fine-granular
control for experimenting etc.

Though quite limited in its current state, it still can tackle a wide range of
real-life tasks. With minimal extension, it can also deal with for example
[PINN](https://en.wikipedia.org/wiki/Physics-informed_neural_networks) and
other interesting challenges.

## Future works
The roadmap for NNC focuses on integrating:
- Convolutional layers
- regularizers
- more optimizers for the backpropagation (Adam...)

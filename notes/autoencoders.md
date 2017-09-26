# Last Week Review

Capacity: ability to fit something
Underfitting: we don't have enough capacity to possible represent the representation
Overfitting: we match the error because we have too much capacity
Regularization: without reducing training error, make your deep learning generalize better

**Deep Learning Meetup!** Domi Station, 6-8pm 28 Sept 2017, meet all the deep learning people!

# What is Deep Learning

Named for networks with more layers to establish heirarchies of abstractions, in other words, deep networks which can _learn their own representations_.

**Def.** _Deep network_: A Deep Network is a network with two or more hidden layers.

## Common Deep Learning Architectures:

1. Deep Feed Forward network (DFF)
    - We have a regular nerual network, but with a bunch of layers.
    - When our gradients back-propagate, however, they can become larger and larger and smaller and smaller; to avoid problems realted to this we perform regularization.
2. Deep Covolutional Network (DCN)
    - We perform convolutional filtering unsing a bunch of filters to process and change the data before we send it to our nerual network.
3. Recurrent nerual Network (RNN)
    - Until very recently, state of the art for time-series or other types of sequential data; many different type of recurrent nerual networks, but they are pretty expensive and difficult to create or run.
    - However, convolutional neural networks have been shown to perform better for some applications of RNNs given a very special type of filtering.
4. Generative Adversarial Networks (GAN) & Variational Auto Encoders (VAE)
    - Claim that they can have nerual networks that can actually approach human level performance in creating new data
    - Adversarial networks try to create fakes and detect fakes, and they make each-other better until the generative network can create things indistinguishable from the non-fakes
    - Both are inherently probabilistic

## Variational Auto-Encoders

**First**, let's examine probabilistic graphical models, which are graphs that represent how probabilities affect each-other.

_Note_: undirected ones are markov chains

Directed graphs which indicate how probabilities affect each-other, showing convineint representations of these probabilities.  Seems much like a mental map...

_In other words,_

> The connections of the networks represent a probability distribution's factorization.
>
> Variational Auto Encoders try to determine these probability distributions.

If we have some probability distribution `p(z,x)`, how can we learn the characteristics of `p(x)`?  How about `p(x|z)` and `p(z|x)`?  We have classical analytical methods to understand these things like information theory and bayes formula.

Variational Autoencoder Architecture:

We have some sort of encoder and decoder size; they are learning two functions: `q_z(z|x)` and `p_theta(x|z)`; we map these to a latent variable space z to figure out how 

```
p(z|x) = (p(x|z)p(z))/p(x)
```

where:
- `p(x|z)` is our
- `p(z)` is our prior
- `p(x)` is our
- `p(z|x)` is our posterior, the thing we want to know exactly

```
p(x|z) = p(x,z)//integral(p(x,z))
```

This integral is very high-dimensional, and is generally intractible.

**Def.** _NP-complete_:
**Def.** _NP-Hard_: means that we cannot compute a function in polynomial time, which means that it's
**Def.** _Intractible_:

We thus have to approximate the integral by simplifying.  Approximate Bayesian Inference is really important, and it's essentially what auto-encoders do.

**Def.** _Parametric Statistics_: We have some parameters independent of our data which describe the data-set
**Def.** _Non-Parametric Statistics_: The data itself describes it's distribution (think a histogram)

Introducing the KL function:

```
KL(q_theta(z|x) || p_theta(z|x)) = \integral_{z~q} log( (q_theta(z|x))/(p_theta(z|x))  )
```

But there's a problem, our posterior is inside the KL function, and since it's integral was intractible in the first place, we can't really do anything!  But, thanks to some very insightful people, we actually have some key insights to make here.

```
-\integral_{z~q} q_theta(z|x)log(p_theta(z,x)/p_theta(x)q_theta(z|x))
```

# Machine Learning

> _Machine learning can learn through data_; more specifically, by learning we mean by some measure of performance, our algorithm can improve it's performance at some task by experience. (Mitchell, 1997)

tasks             | performance measure | experience
------------------|---------------------|------------
classification    | accuracy            | Dataset
transcription     | error rate          | Feedback
anomaly detection |                     | reinforcement
synthesis         |                     |

## Types of learning

- Supervised learning: "I know the labels for my data, sort it for me"
- Unsupervised learning: "I don't have the labels, find some structure for me"
- Reinforcement learning: "Show me results, I'll tell you if it's right or wrong"

### Supervised learning (classification)

If we have some sort of space that represents our data, we want to find regions of space; learn the partitions that seperate classes of information.  I have a sample dataset that represents all possibility, and I want to teach it to my algorithm so it can identify where along these regions in space new data stands.  The supervision algorithms learn the boundaries between classes so it can identify new items.

As it turns out, most machine learning falls under approximation theory and 

### Unsupervised Learning (clustering)

By some clustering algorithm, can we find out what elements are smilar?

Manifold learning: can we learn an underlying structure to our data that represents it's structure?  More abstract and general than regression.  They allow us to represent more complicated information with lower dimensions.

If we have a 2D representation of house addresses, we can try to learn a manifold to represent addresses on one dimension.

## Fundamental Concepts

IID: independent and identically distributed

### Capacity

Capacity describes the ability to model a function.  For example, in interpolation we need n+1 degrees of freedom to model an nth degree polynomial.

However, our degrees of freedom isn't the only thing that represents our capacity to represent high-dimensional data.  Capacity is, in essence, our ability to represent variability.  In higher deimensions, we need exponentially more data to represent _variability_ in our data.

Thus, the problem with capacity is that it allows us to underfit or overfit our data.

Imagine five points sampled from a cubic polynomial: we can try to represent them with a quadratic polynomial, but we will underfit our data and fail to accurately represent it's shape if we have new data.

If we use a 6th degree polynomial to model the same points we may overfit our data.

See also runge's phenomenon.

_Note_: free variables are just our coefficients which we can change and set as we please in a linear system.

### Underfitting & Overfitting

Inappropriate levels of capacity can create underfitting and overfitting.  A method oft used to prevent issues with capacity is early stopping: simply stop when capacity is optimal in your machine learning algorithm.

**Bias** is analagous to underfitting.

**Variance** is analagous to overfitting.

To reiterate: If we have low variance and low bias, we have hit the mark exactly. If we have high variance and low bias we hav overfitting. If we have low variance and high bias we have underfitting.

_Note:_ the hypothesis space is the number of possible models; in other words, if we have 10 free parameters, we have all possible 1-10 dimensional polynomials as possible models or solutions.  The number of possible solutions contributes to our variance; 

## Biological motivations of machine learning

Neurons have some interesting properties: each neuron has it's body, the soma, from which an axon extends and connects to another cell through a synapse.  Different neurons have different synaptic eficacy; in other words, the strength of their connections is different.

Thus we tried to model this with computers and mathematics:

`y = f(w_1*x_1 + w_2*x_2)`

This represents a simple network of two nodes with two weigths that connect throguh an activation function to the output.

In the brain, the activation function is a heavyset function.  They have an action potential which is essentially an all-or-nothing respons to a stimulous.

_Note:_ Hodgkin-Huxley (HH equations) are a set of differential equations which model how action-potentials propagate.  The lab is currently using machine learning to understand astrocyte potential functions.

If the weights never change, the nerual network is totally static.  This model, since it doesn't change its weights, it cannot learn.

Thus, we must create some way to modify the weights of the nerual network.

## Learning

To adapt the weights of our nerual network we must have some way to measure its performance.  A neural network exists independently of a cost function, but we use the cost function to optimize the weights of a nerual network to minimize the error of it's performance measure; to make it perform better.

Learning is optimization of our performance measure.  We have a variety of ways to do this.

Gradient search optimization methods use back propagation to get the partial derviatives of all the weights; we then choose the next set of weights using an optimization method, such as BFGS, newton's method, or the prefered "adam" method.

The specific method of determining the partial derviatives and performing optimization are implementation details.

Consider a case where we have two nonlinear functions to classify: if we have a linear classifier, we can try to seperate them with a straight line but we will probably underfit the data.  If we add a layer we can transform the space until it's possible to draw a straight line through it.  Overfitting the data might be a transformation on our space that creates little to no boundary between the two functions we want to classify, and enough noise that they overlap between each-other.

A black-box, feed-forward neural network is just a function, and approximation theory tells us that with a finite number of nodes we can approximate any function.  Thus, we can theoretically learn anything.

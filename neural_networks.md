# Neural Networks Notes

## Using Sckikit-Learn

### MLPClassifier

`from sklearn.neural_network import MLPCLassifier`

**MLPClassifier** (Multi-Layer Perceptron Classifier) is the easiest way to implement a Neural Network using Scikit-Learn library.

Unlike other Classifiers found in Scikit-Learn such as Logistic Regression, SVM, and others, MLPClassifier is built in the definition of a **Perceptron**. 

![perceptron](imgs/neural_networks_images/perceptron.png)

In other words this Classifier is mainly built on the *input, hidden, and output layers*.

One similarity that MLPClassifier has with other Classifiers in the Scikit-Learn library is that is easy to implement in code.

#### Important parameters:
- `hidden_layer_sizes` : This allows us to set the number of layers and the number of nodes we wish to have in the Neural Network Classifier. Each element in the tuple represents the number of nodes at the $ith$ position where $i$ is the index of the tuple. Thus the length of tuple denotes the total number of hidden layers in the network.
- `max_iter`: It denotes the number of epochs.
- `activation`: The activation function for the hidden layers such as softmax or sigmoud.
- `solver`: This parameter specifies the algorithm for weight optimization across the nodes.
- `random_state`: The parameter allows to set a seed for reproducing the same results


#### Can a NN be a Logistic Model?

Yes, activation function must be positive. Using a Sigmoid function given by $\frac{1}{1 + e^{-x}}$


#### What is the Bias $\Theta$?

Think of it as a constant input.

It is used to shift the data. For example, if we want to learn about the Precision of a certain model, we can use the Bias to shift the model performance to Accuracy instead. 

Think of the Bias Variance Tradeoff.

### Error
#### Problems with squared error

- If the target output is 1 and the actual output is $0.00000001$, then there is **almost no gradient for a logistic unit to fix up the error or change**.
    - In other words, it is way out on the plateau where the slope is almost exactly horizontal and so it will take a very long time to change its wieghts even though it is making as big an error as it's possible to make
- If we are tring to assing probabilities to mutally exclusive class labels, we know that the outpyut shopuld sum to 1, but we are depriving the network of this knowledge.
    - For example if the probability output of two random variables let's say $P(A) = \frac{3}{4}$ and also $P(B) = \frac{3}{4}$ then this is just a crazy answer. We ought to tell the network that information. we shouldn't deprive it with the knwoledge that these are mutually exclusive answer

#### Is there a different cost function that works better?

We need to find a way of telling that $A$ and $B$ are muttually exclusive and then an appropiate cost function.

**We need to force the output of the Neural Network to represent a probability distribution across discrete alternatives**.

##### Softmax

**What?** A soft continuous version of the maximum function.

**How?** each 


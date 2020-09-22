# Neural Networks Notes

## Using Sckikit-Learn

### MLPClassifier

```python
from sklearn.neural_network import MLPCLassifier
```

**MLPClassifier** (Multi-Layer Perceptron Classifier) is the easiest way to implement a Neural Network using Scikit-Learn library.

Unlike other Classifiers found in Scikit-Learn such as Logistic Regression, SVM, and others, MLPClassifier is built in the definition of a **Perceptron**. 

![perceptron](imgs/neural_networks_images/perceptron.png)

In other words this Classifier is mainly built on the *input, hidden, and output layers*.

One similarity that MLPClassifier has with other Classifiers in the Scikit-Learn library is that is easy to implement in code.

#### Important parameters:
- `hidden_layer_sizes` : This allows us to set the number of layers and the number of nodes we wish to have in the Neural Network Classifier. Each element in the tuple represents the number of nodes at the $ith$ position where $i$ is the index of the tuple. Thus the length of tuple denotes the total number of hidden layers in the network.
- `max_iter`: It denotes the number of epochs or iterations.
- `activation`: The activation function for the hidden layers such as softmax or sigmoud.
- `solver`: This parameter specifies the algorithm for weight optimization across the nodes.
- `random_state`: The parameter allows to set a seed for reproducing the same results

## Using Keras

```python
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense, Activation
```


Prefer using Keras over Scikit-Learn when dealing with very huge datasets. Since Keras has GPU support, it's more preferable to use Keras.

Also, Keras is a wrapper class over TensorFlow. In other words, by Keras being built on top of TensorFlow, it makes easier to write verbose code of TensorFlow because of Keras.

However, we can still combined them. For example, we can use the preprocessing classes that Sckit-Learn has and the use Keras for the NN analysis.

**Keras Models and Classes**:

There are two ways to build Keras models: Sequential and Functional

- `Sequential` : Model that create a sequence of layers. It does not allow you yo create models that share layers or have multiple inputs or outputs.

Funtional are more flexible as you cane asily deine mmodels where layers connect to more than just the previopus and nex layers.

- `Dense`: connects the nodes of each layer to the next layers. We can specify the number of number of neurons or nodes in the layer as 1st argument. Also, speciufy the *activation function*. To be more explictit, when you `add(Dense)` you are adding a **Hidden Layer**
    - `units` or 1st par.: it is the dimensionality of output space or number of nodes added to the hidden layer.
    - `input_dim`: number of features as input
    - `activation`: name of the activation function desired for the hidden layer.
**Note**: last hidden layer works as the output so if you want an output of 1s and 0s for the last `Dense` hidden layer you might want to set `activation=sigmoid` because of possible values of this well-known function

- `.compile()`: it configure the model's loss function and metrics
    -`loss`: specify Loss Function such as `binary_crossentropy`
    -`optimizer`: type of solver. Some well-known are `adam` that makes the learning fast and efficient.  
    -`metrics`:

- `.fit()`: train model

- `.predict()`: use model to do the prediction

-  `.summary()`: returns a string summary of the Network

- `.get_layer()`: you can specify the layer based on `name` or `index`

Pseudo code for a basic Keras Neural Network:

```python
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense, Activation
from sklearn.preprocessing import StandardScaler()

sc = StandardScaler()
x_train_scaled  = sc.fit_transform(x_train)
x_test_scaled  = sc.fit_transform(x_test)


model = Sequential()
model.add(Dense(30, input_dim=30, activation='softmax'))

model.compile(loss='binary_crossentropy', optimizer='adam', metrics=['accuracy'])


model.summary()

model.fit(x_train_scaled, x_test_scaled, epochs=100)

## accuracy on training
target_pred_train = model.predict_classes(x_train_scaled)
print(accuracy_score(target_train, target_pred_train))


## accuracy on test
target_pred_test = model.predict_classes(x_test_scaled)
print(accuracy_score(target_test,target_pred_test))
```


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

**How?** Each hidden unit receives some total input wighted from the input or previoues hidden layers' units, $z_i$. The output, $y_i$, depend on the accumulated $z_i$ of the adjacent layers. 

**Goal** Like it was said before, Softmax forces the outputs to represent a probability distribution of mutually exclusive alternatives.




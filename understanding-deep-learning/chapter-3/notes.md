# chapter 3 - shallow neural network
**shallow neural network have one hidden layer composed of a certain capacity of hidden units**

## same methodology to define a neural network, train and test
an equation represents a **family** of input/output relations. 

depending on the choice of the parameters we chose a member of this family. 

we **fit** the data to our model with a training data set by defining a cost function and looking for parameters **minimizing** it.

we look at how well the model perform on test data (**generalization**)

## hidden units (also called neurons)
refers to a term in calculating the output (one preliminary step in the neural network process = the calculation input/output relationship) that is transformed by an activation function.

in the example these are equal to the composition of an activation ReLu function and a linear function

$$ h_1 = a(\theta_{10} +\theta_{11} \times x) $$
### active patterns :
#### active
when a hidden unit is non zero on a certain space of inputs we call it active
#### inactive
when a hidden unit equals zero on a certain space of inputs we call it inactive

## depicting a neural network with 1D input and 1D output
$$ y = f(x, **\phi**) =  \phi_0 + \phi_1\times a(\theta_{10} +\theta_{11} \times x) +\phi_2\times a(\theta_{20} +\theta_{21} \times x) + \phi_3\times a(\theta_{30} +\theta_{31} \times x)$$

<img width="485" height="519" alt="neural network complete" src="https://github.com/user-attachments/assets/3d24e469-7855-43ed-969a-5b4f8437de09" />
<img width="485" height="519" alt="neural network" src="https://github.com/user-attachments/assets/ab7e8153-4c17-4501-b244-488f002a036e" />

* both a complete drawing of the neural network and a simpler version of the same network
* the elements on the arrows represent the weights. the number on one node is multiplied by the weights in the outcoming arrow; the result is added to the next node.
* how many parameters ? $10$

## feed-forward network
refers to the arrows from a node on the left to a node on the right = forward directed arrows (that explains the name).

## why an activation function ?
###  history of neural networks :
* the perceptron was discovered by Rosenblatt in 1958. It linearly combined inputs and thresholded them to make a yes/no decision.
* Minsky & Papert published in 1969 a book to show that linear functions were unsufficient for more general input/output relations and added non linear (activation) function in hidden layers (the name **multi-layer perceptron** comes from there). Moreover they concluded that the learning algorithm developped by Rosenblatt couldn't learn the parameters.
* It was not until the 1980s that a practical algorithm (backpropagation) was developped and significant work on neural networks resumed. 
### activation functions : 
* in the early days of neural nets more common activation functions included : logistic sigmoid & tanh
* ReLU was re-popularized by such notable papers :
* * paper by Jarett et al. in 2009 named "What is the Best Multi-Stage Architecture for Object Recognition?"
  * paper by Nair & Hinton in 2010 named "Rectified Linear Units Improve Restricted Boltzmann Machines"
  * paper by Glorot et al. in 2011 named "Deep Sparse Rectifier Neural Networks"
### Why ReLU and why not ?
* has the nice property that the derivative for positive value is the constant $1$ : which increases **stability and efficiency of learning** (see chapter 7) and contrasts with the derivatives of the sigmoid and tanh functions that become closer to zero for big numbers (in absolute value).
* however it's derivative is zero for negative numbers. So over that input space the gradient with respect to the weights is locally flat : leading to **the dying ReLU problem**
* other functions have been worked by tons of research papers (see page 38 of the book to get deeper)



## solution to problems 
### solution to problem 3.1
if the activation function would be linear it would cause the model to be linear
#### 1st case :
$a(z)= \psi_0 + \psi_1 \times z \implies y = \phi_0 + \phi_1 (\psi_0 + \psi_1 (\theta_{10} + \theta_{11}\times x) ) + \phi_2 (\psi_0 + \psi_1 (\theta_{20} + \theta_{21}\times x) ) + \phi_3 (\psi_0 + \psi_1 (\theta_{30} + \theta_{31} \times x))$ 

$\implies y = C + (\phi_1\psi_1\theta_{11} + \phi_2\psi_1\theta_{21} + \phi_3\psi_1\theta_{31})\times x $
#### 2nd case :
$a(z)=z \implies \phi_0 + \phi_1 (\theta_{10} +\theta_{11} \times x) +\phi_2 (\theta_{20} +\theta_{21} \times x) + \phi_3 (\theta_{30} +\theta_{31} \times x)$

$\implies y = C' + (\phi_1\theta_{11} + \phi_2\theta_{21} + \phi_3\theta_{31})\times x$

### solution to problem 3.2
$h_1$ : inactive; active; active

$h_2$ : inactive; inactive; active

$h_3$ : active;  active; inactive

### solution to problem 3.3
$-\frac{\theta_{10}}{\theta_{11}}$

$-\frac{\theta_{20}}{\theta_{21}}$

$-\frac{\theta_{30}}{\theta_{31}}$

### solution to problem 3.4
<img width="485" height="519" alt="modified-last-hidden-unit" src="https://github.com/user-attachments/assets/c5614cf3-ba10-4def-a800-95b6f795ba79" />

### solution to problem 3.5
$$
\begin{aligned}
\text{ReLU}(\alpha z) &= \begin{cases} 
\alpha z & \text{if } \alpha z \geq 0 \\
0 & \text{else}
\end{cases} \\
&= \begin{cases} 
\alpha z & \text{if } z \geq 0 \\
0 & \text{else}
\end{cases}  \\
&= \alpha \text{ReLU} (z)
\end{aligned}
$$

### solution to problem 3.6
#### when $\alpha \geq 0 :$
from the homogeneity proved in *problem 3.5* multiplying the coefficients for the slope and y-intercept by $\alpha$ lead to a factor of $\alpha$ outside the ReLU activation function. When dividing $\phi$ by $\alpha$ it cancels $\alpha$.

Overall the operation does nothing !

#### when $\alpha < 0 :$
the linear function is multiplied by a negative number so geometrically it's a symmetry on the $x$-axis of this line.

Then we apply ReLU which cancels the negative part (previously positive) and activates the positive part (previously positive)

Overall this operation exchanged the positive and negative parts.


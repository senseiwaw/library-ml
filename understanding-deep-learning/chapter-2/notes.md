# chapter 2 - supervised learning
cost function refers to the whole sum that we minimize (there is a more general concept of objective function which means any funciton we minimize or maximize)

loss function refers to specific indexed terms we want to minimze in the sum of the cost function.
## solution to problem 2.1
 $\displaystyle \frac{\partial L}{\partial \phi_0} = \sum_{i=1}^{I}2\times 1(\phi_0 + \phi_1\times x[i] -y[i])$
 
 $\displaystyle \frac{\partial L}{\partial \phi_1} = \sum_{i=1}^{I}2\times x[i](\phi_0 + \phi_1 \times x[i] -y[i])$

## solution to problem 2.2
$L$ as a function of $\phi_0$ is a polynomial of degree $2$ with a positive dominant coefficient so it's minimum is the unique solution of $\displaystyle \frac{\partial L}{\partial \phi_0}=0$
from problem 2.1 finding $\phi_0$ minimizing the cost function is equivalent to solve  : $$\sum_{i=1}^{I}2\times 1(\phi_0 + \phi_1\times x[i] -y[i]) =0 $$

same for $\phi_1$

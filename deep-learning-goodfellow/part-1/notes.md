# Part I : Applied Math and Machine Learning Basics

## 0. Key Questions
> **Goal:** Identify the mathematical foundations required for Deep Learning.

* What are the basic mathematical concepts needed to understand machine learning?
* Why did we chose such paradigms and not other/ what's the philosophy of modeling machine learning ?
* What are the goals of machine learning?

---

## 1. Linear Algebra Prerequisites
*Focus: Concepts I don't know yet (learn) or distinct perspectives from my knowledge (review).*

### 1.1 Eigendecomposition of a symmetric matrix
Symmetric matrices will play a crucial role. Why ? They have a decomposition in **real eigenvalues** in a basis of **real eigenvectors**.

$$
A = Q \Lambda Q^\top
$$

Where:
* $Q$ is an **orthogonal matrix** of eigenvectors of $A$.
* $\Lambda$ is a **diagonal matrix** of eigenvalues.
* The eigenvalue $\Lambda_{i,i}$ is associated with the eigenvector in column $i$ of $Q$.

### 1.2 Singular Value Decomposition (SVD)
Unlike eigendecomposition, SVD is applicable to **any** matrix (even rectangular ones). [One of the most useful feature of SVD is that we can use it to partially generalize matrix inversion to non-square matrices](#13-the-moore-penrose-pseudoinverse)

$$
A = U D V^\top
$$

Where : 
* $A$ is an $m\times n$ matrix
* $U$ is an $m \times m$ **orthogonal matrix** and its columns contain the **left-singular vectors**
* $V$ is an $n \times n$ **orthogonal matrix** and its columns contain the **right-singular vectors** 
* $D$ is an $m \times n$ **diagonal matrix** (not necessarly a **square matrix**!) and its columns contain the **singular values** of $A$

### 1.3 The Moore-Penrose Pseudoinverse
Matrix inversion is not defined for matrices  that are not square. But we may want to solve a linear equation : 

$$
Ax=y 
$$

by multiplying by a matrix *a left inverse* $B$

$$
x=By 
$$

But it's not *always* possible ! The definition of the Moore-Penrose Pseudoinverse of a matrix $A$ is defined as follow : 

$$
A^+ = \lim_{\alpha \searrow 0} (A^\top A + \alpha I)^{-1} A^\top
$$

practical algorithms are not based on this formula but rather this on : 

$$
A^+ = VD^+U^\top
$$

Where : 
* *U,V,D* are the singular value decomposition of $A$
* $D^+$ is obtained by taking the inverse of the non zero elements of $D$ then taking the transpose ($D$ is not necessarly a square !)
* when $A$ has *more columns than rows*, then solving the linear equation with the pseudoinverse provides $x=A^+y$ with minimal Euclidian norm $| x |_2$ among all possible solutions.
* when $A$ has *more rows than columns*, then there might be no solution. Using the pseudoinvers gives a $x$ for which $| Ax -y |_2$ is minimal

## 2. Probability and Information Theory
*Focus: What is information theory ? How probability theory is used in machine learning ? Learn probability theory concepts that that I don't know or review some in different context*

### 2.1 Why Probability ?
- *Frequentist probability refers to events that we can repeat a lot of times and then attribute a probability*
- *Bayesian probability refers to an event we can attribute a degree of belief with 1 indicating certainty and 0 indicating certainty for the opposite*
- Probability can be seen as an extension of logic to events with uncertainty.

### 2.2 Random variables
a **Random variable** is a function that can take different values/states randomly. 

It is associated with a probability distribution in order to specify which state is more likely to happen.

### 2.3 Probability Distribution

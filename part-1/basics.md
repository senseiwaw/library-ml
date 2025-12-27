# Chapter 1: Applied Math and Machine Learning Basics

## 0. Key Questions
> **Goal:** Identify the mathematical foundations required for Deep Learning.

* What are the basic mathematical concepts needed to understand machine learning?
* What are the goals of machine learning?

---

## 1. Linear Algebra Prerequisites
*Focus: Concepts I don't know yet or distinct perspectives from the Orsay curriculum.*

### 1.1 Eigendecomposition
Symmetric matrices play a crucial role in optimization (Hessian matrix). They have a decomposition in **real eigenvalues** in a basis of **real eigenvectors**.

**Theorem:**
$$A = Q \Lambda Q^\top$$

Where:
* $Q$ is an **orthogonal matrix** of eigenvectors of $A$.
* $\Lambda$ is a **diagonal matrix** of eigenvalues.

### 1.2 Singular Value Decomposition (SVD)
Unlike eigendecomposition, SVD is applicable to **any** matrix (even rectangular ones).

$$
A = U D V^\top
$$

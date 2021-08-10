# Logistic Regression

### Sigmoid Function:
$$
g(z)=\frac{1}{1+e^{-z}}
$$

### Hypothesis:
$$
h_{\theta}(X)=g(X\theta)
$$

### Cost Function:
* Normal Form:
* Vectorization Form :
$$
J(\theta)=\frac{1}{m}\cdot (-y^T\log(h)-(1-y)^T\log(1-h))
$$

### Gradient Descent:
* Derivation:
* Gradient:
$$
\begin{align}
\nabla{J(\theta)} &= \frac{1}{m}X^T(h_{\theta}(X)-y) \\
&= \frac{1}{m}X^T(g(X\theta)-y)
\end{align}
$$
* Update:
$$
\begin{align}
\theta &= \theta-\alpha\nabla{J(\theta)} \\
&= \theta-\alpha\frac{1}{m}X^T(g(X\theta)-y)
\end{align}
$$
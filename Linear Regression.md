# Linear Regression

### Hypothesis:
$$
h_{\theta}(x^{(i)}) 
= \theta_0x_0^{(i)}+\theta_1x_1^{(i)}+\dots+\theta_nx_n^{(i)}=\theta^Tx^{(i)}
$$
$$
h_{\theta}(X)=X\theta
$$

### Cost Function:
* Normal Form:
$$
J(\theta)=\frac{1}{2m}\sum_{i=1}^{m}(h_{\theta}(x^{(i)})-y^{(i)})^2
$$
* Vectorization Form:
$$
J(\theta)=\frac{1}{2m}(X\theta-y)^T(X\theta-y)
$$

[[### Gradient Descent]]:
* Derivation:
$$
\begin{align}
\frac{\partial}{\partial\theta_j}J(\theta)
&=
\frac{1}{2m}\cdot 2\sum_{i=1}^{m}(h_{\theta}(x^{(i)})-y^{(i)})
\frac{\partial}{\partial\theta_j}(h_{\theta}(x^{(i)})) \\
&=\frac{1}{m}\sum_{i=1}^{m}(h_{\theta}(x^{(i)})-y^{(i)})\cdot x_j^{(i)}
\end{align}
$$
* Gradient:
$$
\nabla{J(\theta)} = \frac{1}{m}X^T(X\theta-y)
$$

* Update:
$$
\theta_j=\theta_j-\alpha\frac{1}{m}\sum_{i=1}^{m}(h_{\theta}(x^{(i)})-y^{(i)})\cdot x_j^{(i)}
\text{\quad for\quad} j=0\dots.n
$$

$$
\begin{align}
\theta&=\theta-\alpha\nabla{J(\theta)} \\
&=\theta-\alpha\frac{1}{m}X^T(X\theta-y) \\
&=\theta-\alpha\frac{1}{m}X^T(h_{\theta}(X)-y)
\end{align}
$$


### Regularization:
* Cost Function:
$$
J(\theta)=\frac{1}{2m}
\left[\sum_{i=1}^{m}(h_{\theta}(x^{(i)})-y^{(i)})^2+
\lambda\sum_{j=1}^{n}\theta_j^2\right]
$$
* Gradient:
$$
\nabla{J(\theta)}=\frac{1}{m}X^T(X\theta-y)+
\frac{\lambda}{m}\theta[1,n]
\text{\quad for\quad} j=1...n
$$
* Update:
$$
\begin{align}
\theta_0&=\theta_0-\alpha\frac{1}{m}\sum_{i=1}^{m}(h_{\theta}(x^{(i)})-y^{(i)})\cdot x_0^{(i)}
\\
\theta_j&=\theta_j-\alpha
\left[\frac{1}{m}\sum_{i=1}^{m}(h_{\theta}(x^{(i)})-y^{(i)})\cdot x_j^{(i)}+\frac{\lambda}{m}\theta_j
\right]
\text{\quad for\quad} j=1\dots.n
\end{align}
$$

### Normal Equation:
$$
\begin{align}
\theta = (X^TX+\lambda\cdot L)^{-1}X^Ty \\
\text{where\quad}L=
\begin{bmatrix}
0\\
&1\\
&&1\\
&&&\ddots\\
&&&&1
\end{bmatrix}
\end{align}
$$
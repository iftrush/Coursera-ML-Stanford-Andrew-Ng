# Hypothesis
### (*n*+1) Parameter:
$$
\theta=\begin{bmatrix}  
\theta_0\\  
\theta_1\\
\vdots\\
\theta_n
\end{bmatrix}
$$

### *m* experiments:

$$
x_j=\begin{bmatrix}  
x_j^{(1)}\\  
x_j^{(2)}\\
\vdots\\
x_j^{(m)}
\end{bmatrix}
$$

### (*n*+1) Features:

$$
x^{(i)}=\begin{bmatrix}
x_0^{(i)}\\x_1^{(i)}\\\vdots\\x_n^{(i)}
\end{bmatrix}
$$

$$
X=\begin{bmatrix}
x_0^{(1)} & x_1^{(1)} & \dots & x_n^{(1)}\\
x_0^{(2)} & x_1^{(2)} & \dots & x_n^{(2)}\\
\vdots & \vdots & \ddots & \vdots\\
x_0^{(m)} & x_1^{(m)} & \dots & x_n^{(m)}\\
\end{bmatrix}
$$

$$
h_{\theta}(x^{(i)}) 
= \theta_0x_0^{(i)}+\theta_1x_1^{(i)}+\dots+\theta_nx_n^{(i)}=\theta^Tx^{(i)}
$$

### Hypothesis Function:

* Perspective 1:
$$
h_{\theta}(x)=\begin{bmatrix}
\theta_0x_0^{(1)}+\theta_1x_1^{(1)}+\dots+\theta_nx_n^{(1)}\\
\theta_0x_0^{(2)}+\theta_1x_1^{(2)}+\dots+\theta_nx_n^{(2)}\\
\vdots\\
\theta_0x_0^{(m)}+\theta_1x_1^{(m)}+\dots+\theta_nx_n^{(m)}
\end{bmatrix}
=
\begin{bmatrix}
x_0^{(1)} & x_1^{(1)} & \dots & x_n^{(1)}\\
x_0^{(2)} & x_1^{(2)} & \dots & x_n^{(2)}\\
\vdots & \vdots & \ddots & \vdots\\
x_0^{(m)} & x_1^{(m)} & \dots & x_n^{(m)}\\
\end{bmatrix}\cdot\begin{bmatrix}  
\theta_0\\  
\theta_1\\
\vdots\\
\theta_n
\end{bmatrix}=X\theta
$$

* Perspective 2:
$$
h_{\theta}(x)
=
\theta_0x_0+\theta_1x_1+\theta_2x_2+\dots+\theta_nx_n
=X\theta 
$$


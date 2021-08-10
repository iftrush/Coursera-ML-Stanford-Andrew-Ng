# Backpropagation

### Algorithm:
> Training Set = $[(x^{(1)},y^{(1)}),...,(x^{(m)},y^{(m)})]$
> $\forall l,i,j,\quad$set $\Delta_{i,j}^{(l)}=0$
> For $i=1\dots m$:
> $\qquad$set $a^{(1)}=x^{(i)}$
> $\qquad$For $l=2,3,...,L$:
> $\qquad\quad$Forward Propagation to compute $a^{(l)}$:
> $\qquad\qquad z^{(l)}=\Theta^{(l-1)}a^{(l-1)}$
> $\qquad\qquad a^{(l)}=g(z^{(l)})$
> $\qquad\,\delta^{(L)}=a^{(L)}-y^{(i)}$
> $\qquad$ For $l=L-1,L-2,\dots,2$:
> $\qquad\qquad g'(z^{(l)})=a^{(l)}\circ(1-a^{(l)})$
> $\qquad\qquad\delta^{(l)}=((\Theta^{l})^T\delta^{(l+1)})\circ g'(z^{(l)})$ 
> $\qquad\,\Delta_{ij}^{(l)}=\Delta_{ij}^{(l)}+a_j^{(l)}\delta_i^{(l+1)}$ 
> $D_{i,j}^{(l)}=\frac{1}{m}\left(\Delta_{i,j}^{(l)}+\lambda\Theta_{i,j}^{(l)}\right)$ if $j\neq 0$
> $D_{i,j}^{(l)}=\frac{1}{m}\Delta_{i,j}^{(l)}$ if $j=0$


### Gradient:
$$
\frac{\partial}{\partial\Theta_{i,j}^{(l)}}J(\Theta)
=D_{i,j}^{(l)}
$$

### Error $\delta_j^{(l)}$of node $j$ in layer $l$:
- Derivation:
$$
\begin{align}
\delta_j^{(L)}&=\frac{\partial J}{\partial z_j^{(L)}} \\
&=\sum_{k=1}^{k_L}\frac{\partial J}{\partial a_k^{(L)}}\frac{\partial a_k^{(L)}}{\partial z_j^{(L)}} \\
&=\frac{\partial J}{\partial a_j^{(L)}}\frac{\partial a_j^{(L)}}{\partial z_j^{(L)}} \\
&=\frac{\partial J}{\partial a_j^{(L)}}\frac{\partial}{\partial a_j^{(L)}}\left(g(z_j^{(L)})\right) \\
&=\frac{\partial J}{\partial a_j^{(L)}}g'(z_j^{(L)})
\end{align}
$$
- Vectorization:
$$
\delta^{(L)}=\nabla_{a^{(L)}}J\odot g'(z^{(L)})
$$


### Derive $\delta^{(l)}$:
- Derivation:
$$
\begin{align}
\delta_j^{(l)}&=\frac{\partial J}{\partial z_j^{l}} \\
&=\sum_{i=1}^{s_{l+1}}\frac{\partial J}{\partial z_i^{(l+1)}}\frac{\partial z_i^{(l+1)}}{\partial z_j^{(l)}} \\
&=\sum_{i=1}^{s_{l+1}}\delta_i^{(l+1)}\frac{\partial z_i^{(l+1)}}{\partial z_j^{(l)}} \\
&=\sum_{i=1}^{s_{l+1}}\delta_i^{(l+1)}\frac{\partial}{\partial z_j^{l}}\left(\sum_{j=1}^{s_{l}}\Theta_{i,j}^{(l)}a_j^{(l)}\right) \\
&=\sum_{i=1}^{s_{l+1}}\delta_i^{(l+1)}\frac{\partial}{\partial z_j^{l}}\left(\sum_{j=1}^{s_{l}}\Theta_{i,j}^{(l)}g(z_j^{(l)})\right) \\
&=\sum_{i=1}^{s_{l+1}}\delta_i^{(l+1)}\Theta_{i,j}^{(l)}g'(z_j^{(l)})
\end{align}
$$
- Vectorization:
$$
\delta^{(l)}=((\Theta^{l})^T\delta^{(l+1)})\circ g'(z^{(l)})
$$

### Gradient of Cost with respect to parameters $\Theta_{i,j}^{(l)}$:
- Derivation:
$$
\begin{align}
\frac{\partial J}{\partial\Theta_{i,j}^{(l)}}
&=\frac{\partial J}{\partial z_i^{(l+1)}}\frac{\partial z_i^{(l+1)}}{\partial\Theta_{i,j}^{(l)}} \\
&=\delta_i^{(l+1)}\frac{\partial}{\partial\Theta_{i,j}^{(l)}}\left(\sum_{j=1}^{s_{l+1}}\Theta_{i,j}^{(l)}a_j^{(l)}\right) \\
&=\delta_i^{(l+1)}a_j^{(l)}
\end{align}
$$

- Vectorization:
$$
\frac{\partial J}{\partial\Theta^{(l)}}=\delta^{l+1}(a^{(l)})^T
$$

- $\Delta_{i,j}^{(l)}$ Update:
$$
\Delta_{i,j}^{(l)}=\Delta_{i,j}^{(l)}+a_j^{(l)}\delta_i^{(l+1)}
$$

- Vectorization of $\Delta^{(l)}$ Update:
$$
\Delta^{(l)}=\Delta^{(l)}+\delta^{l+1}(a^{(l)})^T
$$

### Regularization:
- Gradient of $J_{reg}$:
$$
\begin{align}
J_{reg}&=\frac{\lambda}{2m}\sum_{l=1}^{L-1}\sum_{j=1}^{s_l}\sum_{i=1}^{s_{l+1}}(\Theta_{i,j}^{(l)})^2 \\
\frac{\partial J_{reg}}{\partial\Theta_{i,j}^{(l)}}
&=\frac{\lambda}{2m}2\Theta_{i,j}^{(l)} \\
&=\frac{\lambda}{m}\Theta_{i,j}^{(l)}\text{\quad if\quad} j\neq 0
\end{align}
$$
- Formula:
$$
\begin{align}
\frac{\partial}{\partial\Theta_{i,j}^{(l)}}J_{net}(\Theta)=D_{ij}^{(l)}
&=\frac{1}{m}\left(\Delta_{i,j}^{(l)}+\lambda\Theta_{i,j}^{(l)}\right)&\text{if\quad} j\neq 0 \\
&=\frac{1}{m}\Delta_{i,j}^{(l)}&\text{if\quad} j=0
\end{align}
$$
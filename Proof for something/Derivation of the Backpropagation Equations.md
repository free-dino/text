To derive the [[2. Training a Neural Network#^07a150|backpropagation equations]], consider the non-vectorized version of layer $l$:
$$
\begin{align}
&\begin{cases}
z_j^{(l)} = \sum_k W_{jk}^{(l)} q_k^{(l-1)} + b_j^{(l)}\\
q_j^{(l)} = h(z_j^{(l)})
\end{cases},  &\forall j=1, \dots, U^{(l)}. 
\end{align}
$$
^4bacb9

We can use the chain rule of calculus to write:
$$
\frac{\partial J}{\partial b_j^{(l)}} = \frac{\partial J}{\partial z_j^{(l)}} \underbrace{\frac{\partial z_j^{(l)}}{\partial b_j^{(l)}}}_{=1} = \frac{\partial J}{\partial z_j^{(l)}}
$$
$$
\frac{\partial J}{\partial W_{jk}^{(l)}} = \frac{\partial J}{\partial z_{j}^{(l)}} \underbrace{\frac{\partial z_j^{(l)}}{\partial W_{jk}^{(l)}}}_{= q_k^{(l-1)}} = \frac{\partial J}{\partial z_{j}^{(l)}} q_k^{(l-1)}, \ \ \ \ \ \ \ \ \forall j=1, \dots, U^{(l)}
$$
where the partial derivatives of $z_j^{(l)}$ with respect to $W_{jk}^{(l)}$ and $b_j^{(l)}$ can be directly derived from [[Derivation of the Backpropagation Equations#^4bacb9|this]] 

Use the chain rule to compute the partial derivative of $J(\vbs \theta)$ with respect to the post-activation hidden unit $q_k^{(l-1)}$ for layer $l-1$
$J(\vbs \theta)$ depends on $q_k^{(l-1)}$ via all the pre-activation hidden unit $\{ z_j^{(l)}\}_{j=1}^{U^{(l)}}$ in layer $l$; hence we get:
$$
\frac{\partial J}{\partial q_k^{(l-1)}} = \sum_{j} \frac{\partial J}{\partial z_j^{(l)}} \underbrace{\frac{\partial z_j^{(l)}}{\partial q_k^{(l-1)}}}_{W_{jk}^{(l)}}= \sum_j \frac{\partial J}{\partial z_j^{(l)}} W_{jk}^{(l)} \ \ \ \ \ \ \ \ \forall k=1,\dots, U^{(l-1)}
$$
Finally, we can also use the chain rule to express:
$$
\frac {\partial J}{\partial z_j^{(l)}} = \frac{\partial J}{\partial q_j^{(l)}} \frac{\partial q_j^{(l)}}{\partial z_j^{(l)}} = \frac{\partial J}{\partial q_j^{(l)}} h'(z_j^{(l)})
$$
Suppose that we have a function $f : \R^n \to \R^m$, which maps an $n$-dimensional input $\v x \in \R^n$ to an $m$-dimensional output $\v y \in \R^m$

One way to view this function is as a column vector of $m$-scalar-valued functions stacked one on top of each other: (? How can we know the order)

$$
f (\v x) = 
\begin{bmatrix} 
f_1(x_1, \dots x_n) \\
f_2(x_1, \dots, x_n) \\
\vdots \\
f_m(x_1, \dots, x_n)
\end{bmatrix}
$$

The Jacobian matrix $\mat J$ of $f$ is an $m \times n$ matrix, where each row contains the gradient of the $i$th 'scalar function' with respect to $\v x$, $\nabla_{\v x} f_i(\v x)$:
$$
\mat J  =
\begin{bmatrix}
\textemdash  &\nabla_{\v x}f_1(\v x) & \textemdash \\
\textemdash  &\nabla_{\v x}f_2(\v x) & \textemdash \\
& \vdots \\
\textemdash  &\nabla_{\v x}f_n(\v x) & \textemdash \\
\end{bmatrix}
= 
\begin{bmatrix}
\frac{\partial y_1}{\partial x_1} & \frac{\partial y_1}{\partial x_2} & \cdots & \frac{\partial y_1}{\partial x_n} \\
\vdots & \vdots &\ddots & \vdots \\
\frac{\partial y_m}{\partial x_1} & \frac{\partial y_m}{\partial x_2} & \cdots & \frac{\partial y_m}{\partial x_n} \\
\end{bmatrix}
$$

# 1. Vector-Jacobian product (VJP)
Given a vector $\v u \in \R^m$, the VJP is the following row vector:
$$
\v u^\top \mat J \in \R^{1\times n}
$$
Being $n$-dimensional, we have one VJP element for each of the function inputs, $\v x$ 

It tells us "in what direction should each of the inputs change, in order to get a change of $\v u$ in the outputs?"
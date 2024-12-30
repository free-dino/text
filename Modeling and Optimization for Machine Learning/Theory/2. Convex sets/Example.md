# 2.1
Solution set of linear equation:
The solution set of a system of linear equations, $C = \{\v x \mid \mat A \v x = \v b\}$ where $\mat A \in \R^{m\times n}$ and $\v b \in \R^m$, is an affine set.

*Solution*:
Suppose $\v x_1, \v x_2 \in C$, i.e., $\mat A \v x_1 = \v b, \mat A \v x_2 = \v b$. Then for any $\theta \in \R$, we have
$$
\begin {align}
\mat A (\theta \v x_1 + (1-\theta)\v x_2) &=  \theta \mat A \v x_1 + (1-\theta)\mat A \v x_2 \\
&= \theta \v b + (1-\theta)\v b \\
&= b,
\end{align}
$$

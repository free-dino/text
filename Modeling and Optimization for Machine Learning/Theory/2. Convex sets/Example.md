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
=> also in $C$. The subspace associated with the affine set $C$ is the nullspace of $\mat A$.
=> every affine set can be expressed as the solution set of a system of linear equations.

# 2.2
Consider a square in the $(x_1, x_2)$-plane in $\R^3$ defined as:
$$
C = \{ \v x \in \R^3 \mid -1 \le x_1 \le 1, -1 \le x_2 \le 1, x_3 = 0 \}
$$
Its affine hull is the $(x_1, x_2)$-plane, i.e., $\textbf{aff } C = \{\v x \in \R^3 \mid x_3 = 0\}$. The interior of $C$ is empty, but the relative interior is:
$$
\textbf{relint } C = \{ \v x \in \R^3 \mid -1 < x_1 <1, -1 < x_2 <1, x_3 = 0 \}
$$
Its boundary (in $\R^3$) is itself; its relative boundary is the wire-frame outline, 
$$
\{
\v x \in \R^3 \mid \max\{ |x_1| |x_2|\} = 1, x_3 = 0
\}
$$

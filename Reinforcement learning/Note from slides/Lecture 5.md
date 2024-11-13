MC: high variance, zero bias
TD: low variance, some bias

On- and Off- Policy
- Policy: the behavior we want to optimize
- Experiences: the knowledge from environment
How we get the experiences for learning:
- On policy: Experiences come directly from our optimizing policy
- Off policy: experiences come from other policy

$\epsilon$-greedy exploration:
$$
\pi (a \mid s) = 
\begin{cases}
\epsilon/m +1 - \epsilon & \text{if } a^* = \arg \max_{a\in A} Q(s,a) \\
\epsilon/m & \text{otherwise}
\end{cases}
$$

Sample $k$-th episode using $\pi : \{S_1, A_1, R_2, \dots, S_T\}\sim \pi$ 
For each state $S_t$ and action $A_t$ in the episode
$$
\begin{align}
N(S_t, A_t) &\leftarrow N(S_t, A_t)+1 \\
Q(S_t, A_t) &\leftarrow Q(S_t, A_t) + \frac 1 {N(S_t, A_t)}(G_t-Q(S_t, A_t))
\end{align}
$$
Improve policy:
$$
\begin{align}
\epsilon &\leftarrow \frac 1 k \\
\pi &\leftarrow \epsilon\text{-greedy}
\end{align}
$$

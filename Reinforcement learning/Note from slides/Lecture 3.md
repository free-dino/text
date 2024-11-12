3 state: Cool, Warm, Overheated
2 actions: Slow, Fast.
Rewards: Slow +1. Fast: +2
Overheated: -10
$\gamma =1$ 

$$
v_\pi (s) = \sum_{a \in A} \pi(a \mid s) \Bigg ( \mathcal R_s^a + \gamma \sum_{s' \in S} \mathcal P_{ss'}^a v_\pi (s')  \Bigg)
$$

Policy: 
$a = \pi (s) \iff \pi (a\mid s) = \mathbf P(A_t = a \mid S_t = s)$ 

Cool:
$$
\begin{align}
A &= \{\text{Slow, Fast}\} \\
S &= \{\text{Cool, Warm}\} \\
\mathcal R_\text{Cool}^\text{Slow} &= 1 \\
\mathcal R_\text{Cool}^\text{Fast} &= 2 \\
\mathcal P_\text{Cool - Cool}^\text{Slow} &= 1 \\
\mathcal P_\text{Cool - Warm}^\text{Slow} &= 0 \\
\mathcal P_\text{Cool - Cool}^\text{Fast} &= 0.5 \\
\mathcal P_\text{Cool - Warm}^\text{Fast} &= 0.5 \\
\end{align}
$$
$$
\begin{align}
\implies v_\pi^{\text{Slow}}(\text{Cool}) &= \pi(\text{Slow} \mid \text{Cool})\Bigg[ \mathcal R_\text{Cool}^\text{Slow} + \mathcal P_\text{Cool - Cool}^\text{Slow} v_\pi(\text{Cool}) + \mathcal P_\text{Cool - Warm}^\text{Slow}v_\pi(\text{Warm})\Bigg] \\
& = 0.5 \times \Bigg[ 1 +1\times v_\pi(\text{Cool})\Bigg] \\
& = 0.5 + 0.5v_\pi(\text{Cool})
\end{align}
$$

$$
\begin{align}
\implies v_\pi^{\text{Fast}}(\text{Cool}) &= \pi(\text{Fast} \mid \text{Cool})\Bigg[ \mathcal R_\text{Cool}^\text{Fast} + \mathcal P_\text{Cool - Cool}^\text{Fast} v_\pi(\text{Cool}) + \mathcal P_\text{Cool - Warm}^\text{Fast}v_\pi(\text{Warm})\Bigg] \\
& = 0.5 \times \Bigg[ 2 +0.5\times v_\pi(\text{Cool}) + 0.5 \times v_\pi(\text{Warm})\Bigg] \\
& = 1 + 0.25v_\pi(\text{Cool}) + 0.25v_\pi(\text{Warm})
\end{align}
$$
$$
\begin{align}
v_\pi (\text{Cool}) &= v_\pi^\text{Slow} (\text{Cool}) + v_\pi^\text{Fast}(\text{Cool}) \\
& = 1.5 + 0.75v_\pi(\text{Cool}) + 0.25 v_\pi(\text{Warm}) \\
\implies v_\pi (\text{Cool}) &= 6+v_\pi(\text{Warm})
\end{align}
$$

Warm:
$$
\begin{align}
A &= \{\text{Slow, Fast}\} \\
S &= \{\text{Cool, Warm, Overheat}\} \\
\mathcal R_\text{Warm}^\text{Slow} &= 1 \\
\mathcal R_\text{Warm}^\text{Fast} &= 2 \\
\mathcal P_\text{Warm - Cool}^\text{Slow} &= 0.5 \\
\mathcal P_\text{Warm - Warm}^\text{Slow} &= 0.5 \\
\mathcal P_\text{Warm - Cool}^\text{Fast} &= 0 \\
\mathcal P_\text{Warm - Warm}^\text{Fast} &= 0 \\
\mathcal P_\text{Warm - Overheat}^\text{Fast} &= 1 \\
\mathcal P_\text{Warm - Overheat}^\text{Slow} &= 0 \\
\end{align}
$$

$$
\begin{align}
\implies v_\pi^{\text{Slow}}(\text{Warm}) &= \pi(\text{Slow} \mid \text{Warm})\Bigg[ \mathcal R_\text{Warm}^\text{Slow} + \mathcal P_\text{Warm - Cool}^\text{Slow} v_\pi(\text{Cool}) + \mathcal P_\text{Warm - Warm}^\text{Slow}v_\pi(\text{Warm}) + P_\text{Warm - Overheat}^\text{Slow}v_\pi(\text{Overheat})\Bigg] \\
& = 0.5 \times \Bigg[ 1 +0.5\times v_\pi(\text{Cool}) + 0.5 \times v_\pi(\text{Warm})\Bigg] \\
& = 0.5 + 0.25v_\pi(\text{Cool}) + 0.25v_\pi(\text{Warm})
\end{align}
$$

$$
\begin{align}
\implies v_\pi^{\text{Fast}}(\text{Warm}) &= \pi(\text{Fast} \mid \text{Warm})\Bigg[ \mathcal R_\text{Warm}^\text{Fast} + \mathcal P_\text{Warm - Cool}^\text{Fast} v_\pi(\text{Cool}) + \mathcal P_\text{Warm - Warm}^\text{Fast}v_\pi(\text{Warm}) + P_\text{Warm - Overheat}^\text{Fast}v_\pi(\text{Overheat})\Bigg] \\
& = 0.5 \times \Bigg[ 2 +v_\pi(\text{Overheat})\Bigg] \\
& = 1 + 0.5 v_\pi(\text{Overheat})
\end{align}
$$
$$
\begin{align}
v_\pi (\text{Warm}) &= v_\pi^\text{Slow} (\text{Warm}) + v_\pi^\text{Fast} (\text{Warm}) \\
& = 1.5 + 0.25v_\pi(\text{Cool}) + 0.25 v_\pi(\text{Warm}) + 0.5 v_\pi(\text{Overheat}) \\
\implies v_\pi (\text{Warm}) &= 2+ \frac 1 3 v_\pi(\text{Cool}) + \frac 2 3 v_\pi(\text{Overheat})
\end{align}
$$

$v_\pi(\text{Overheat}) = -10$

$$
v_\pi(\text{Cool}) = 2 \qquad v_\pi(\text{Warm}) = -4
$$


$\implies v_\pi^{\text{Slow}}(\text{Cool}) = 1.5$
$\implies v_\pi^{\text{Fast}}(\text{Cool}) = 0.5$
$\implies v_\pi^{\text{Slow}}(\text{Warm}) = 0$
$\implies v_\pi^{\text{Slow}}(\text{Warm}) = -4$ 



now:

$$
\begin{align}
q_\pi(\text{Cool, Slow}) &= \mathcal R_\text{Cool}^\text{Slow} + \sum_{s' \in S} \mathcal P^\text{Slow}_\text{Cool - s'} \sum_{a' \in A} \pi(a' \mid s')q_\pi(s', a') \\
& = 1 + \mathcal P^\text{Slow}_\text{Cool - Cool} \sum_{a' \in A} \pi(a' \mid \text{Cool})q_\pi(\text{Cool}, a')  \\ 
& = 1+ \sum_{a' \in A} \pi(a' \mid \text{Cool})q_\pi(\text{Cool}, a')  \\ 
& = 1+0.5q_\pi(\text{Cool, Slow}) + 0.5q_\pi(\text{Cool, Fast}) \\
\implies q_\pi(\text{Cool, Slow}) &= 2 + q_\pi(\text{Cool, Fast}) 
\end{align}
$$
$$
\begin{align}
q_\pi(\text{Cool, Fast}) &= \mathcal R_\text{Cool}^\text{Fast} + \sum_{s' \in S} \mathcal P_\text{Cool - s'}^\text{Fast} \sum_{a' \in A} \pi(a' \mid s')q_\pi(s', a') \\
& = 2 +0.5 \sum_{a' \in A} \pi(a' \mid \text{Cool})q_\pi(\text{Cool}, a') + 0.5\sum_{a' \in A} \pi(a' \mid \text{Warm})q_\pi(\text{Warm}, a') \\
& = 2 + 0.5(\pi(\text{Slow} \mid \text{Cool})q_\pi(\text{Cool, Slow}) + \pi(\text{Fast} \mid \text{Cool})q_\pi(\text{Cool, Fast}))\\ &\qquad + 0.5 (\pi(\text{Slow} \mid \text{Warm})q_\pi(\text{Warm, Slow}) + \pi(\text{Fast} \mid \text{Warm})q_\pi(\text{Warm, Fast})) \\
& = 2 + 0.25q_\pi(\text{Cool, Slow}) + 0.25q_\pi(\text{Cool, Fast}) +0.25q_\pi(\text{Warm, Slow}) \\ & \qquad+ 0.25q_\pi(\text{Warm, Fast}) \\
\implies q_\pi(\text{Cool, Fast}) &= \frac 1 3 q_\pi(\text{Cool, Slow}) + \frac 1 3 q_\pi(\text{Warm, Slow})
\end{align}
$$

$$
\begin{align}
q_\pi(\text{Warm, Slow}) &= \mathcal R_\text{Warm}^\text{Slow} + \sum_{s' \in S} \mathcal P^\text{Slow}_\text{Warm - s'} \sum_{a' \in A} \pi(a' \mid s')q_\pi(s', a') \\
q_\pi(\text{Warm, Slow}) &= 1 + \mathcal P^\text{Slow}_\text{Warm - Cool}( \pi(\text{Slow} \mid \text{Cool})q_\pi(\text{Cool, Slow}) + \pi(\text{Fast} \mid \text{Cool})q_\pi(\text{Cool, Fast})) \\ & \quad + 
\mathcal P^\text{Slow}_\text{Warm - Warm}( \pi(\text{Slow} \mid \text{Warm})q_\pi(\text{Warm, Slow}) + \pi(\text{Fast} \mid \text{Warm})q_\pi(\text{Warm, Fast})) \\
& \quad + 
\mathcal P^\text{Slow}_\text{Warm - Overheat}( \pi(\text{Slow} \mid \text{Overheat})q_\pi(\text{Overheat, Slow}) + \pi(\text{Fast} \mid \text{Overheat})q_\pi(\text{Cool, Fast})) \\
q_\pi(\text{Warm, Slow}) &= 1 + 0.5(0.5q_\pi(\text{Cool, Slow}) + 0.5q_\pi(\text{Cool, Fast})) + \\
& \qquad + 0.5 (0.5q_\pi(\text{Warm, Slow}) + 0.5q_\pi(\text{Warm, Fast})) \\
& = 1 +0.25 q_\pi(\text{Cool, Slow}) + 0.25q_\pi(\text{Cool, Fast}) + 0.25 q_\pi(\text{Warm, Slow}) + 0.25q_\pi(\text{Warm, Fast}) \\
\implies q_\pi(\text{Warm, Slow}) &= \frac {-4} 3 + \frac 1 3 q_\pi(\text{Cool, Slow}) + \frac 1 3 q_\pi(\text{Cool, Fast})
\end{align}
$$


$$
\begin{align}
q_\pi(\text{Warm, Fast}) &= \mathcal R_\text{Warm}^\text{Fast} + \sum_{s' \in S} \mathcal P^\text{Fast}_\text{Warm - s'} \sum_{a' \in A} \pi(a' \mid s')q_\pi(s', a') \\
q_\pi(\text{Warm, Fast}) &= 1 + \mathcal P^\text{Fast}_\text{Warm - Cool}( \pi(\text{Slow} \mid \text{Cool})q_\pi(\text{Cool, Slow}) + \pi(\text{Fast} \mid \text{Cool})q_\pi(\text{Cool, Fast})) \\ & \quad + 
\mathcal P^\text{Fast}_\text{Warm - Warm}( \pi(\text{Slow} \mid \text{Warm})q_\pi(\text{Warm, Slow}) + \pi(\text{Fast} \mid \text{Warm})q_\pi(\text{Warm, Fast})) \\
& \quad + 
\mathcal P^\text{Fast}_\text{Warm - Overheat}( \pi(\text{Slow} \mid \text{Overheat})q_\pi(\text{Overheat, Slow}) + \pi(\text{Fast} \mid \text{Overheat})q_\pi(\text{Cool, Fast})) \\
q_\pi(\text{Warm, Fast}) &= 2 + -10 = -8
\end{align}
$$




$\gamma = 0.5$

$\v v^{k+1} = \mat R^{\v \pi}$ +    
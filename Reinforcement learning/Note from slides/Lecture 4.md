Given:
![[Pasted image 20241112204322.png]]

(a) Prefer the close exit (+1), risking the cliff (-10)
(b) Prefer the close exit (+1), but avoiding the cliff (-10)
(c) Prefer the distant exit (+10), risking the cliff (-10)
(d) Prefer the distant exit (+10), avoiding the cliff (-10)

(1): $\gamma = 0.1$, noise = $0.5$ -> (c)
(2): $\gamma=0.9$, noise = 0 -> (b)
(3): $\gamma = 0.9$, noise = $0.5$ -> (a)
(4): $\gamma = 0.1$, noise = $0$ -> (d)

## Monte Carlo method
To evaluate the state $s$
The first time-step $t$ that state $s$ is visited in an episode, 
Increment counter $N(s) \leftarrow N(s) +1$
Increment total return $S(s) \leftarrow S(s) + G(t)$
Value is estimated by mean return $V(s) = S(s)/N(s)$
By the law of large numbers, $V(s) \to v^\pi(s)$ as $N(s)\to \infty$

Episode: s -> a -> s' -> r

Episode 1
t=1
N(B) = 1
S(B) = -8
V(B) = -8
t=2
N(C) = 1
S(C) = -9
V(C) = -9
t=3
N(D) = 1
S(D) = 10
V(D) = 10

Episode 2:
t = 1
N(B) = 2
S(B) = 16
V(B) = 8
t=2
N(C) = 2
S(C) = 18
V(C) = 9
t=3
N(D) = 2
S(D) = 20
V(D) = 10

Episode 3:
t=1
N(E) = 1
S(E) = 8
V(E) = 8
t=2
N(C) = 3
S(C) = 27
V(C) = 9
t = 3
N(D) = 3
S(D) = 30
V(D) = 10

Episode 4:
t=1
N(E) = 2
S(E) = -4
V(E) = -2
t=2
N(C) = 4
S(C) = 16
V(C) = 4
t=3
N(A) = 1
S(A) = -10
V(A) = -10

-> V(A) = -10, V(B) = 8, V(C) = 4, V(D) = 10, V(E) = -2

# Temporal Different method

$V(S_t) \leftarrow V(S_t) + \a(G_t - V(S_t))$

$\a = 0.1$

Episode 1:
V(A) = $0$
V(B) = $0 + 0.1\times(8-0) = 0.8$
V(C) = $0 + 0.1\times(9-0) = 0.9$
V(D) = $0 +0.1\times(10-0) = 1$
V(E) = $0$

Episode 2:
V(A) = $0$
V(B) = $0.8 + 0.1\times(8-0.8) = 1.52$
V(C) = $0.9+0.1 \times (9-0.9)=1.71$
V(D) = $1+0.1 \times (10-1)=1.9$
V(E) = $0$

Episode 3:
V(A) = $0$
V(B) = $1.52$
V(C) = $1.71+0.1 \times (9-1.71)=2.439$
V(D) = $1.9+0.1 \times (10-1.9)=2.71$
V(E) = $0+0.1 \times (8-0)=0.8$

Episode 4:
V(A) = $0 + 0.1 (-10 +0 ) = -0.1$
V(B) = $1.52$
V(C) = $2.439 + 0.1 \times (-11 + 2.439) = 1.5829$
V(D) = $2.71$
V(E) = $0.8+0.1 \times (-12-0.8)=-0.48$

MC:
V(D) > V(B) > V(C) > V(E) > V(A)

TD:
V(D) > V(C) > V(B) > V(A) > V(E)
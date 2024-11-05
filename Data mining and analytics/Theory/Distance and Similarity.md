# 1. Introduction
## 1.1. Distance metric
Let $\mat X$ be a set or space. A distance metric on $\mat X$ is a function $d : \mat X \times \mat X \to [0, + \infty)$. $\forall \v x, \v y, \v z \in \mat X$, distance $d$ must satisfy the following axioms:
- Identity: $d(\v x, \v x) = 0$
- Positivity: $d(\v x, \v y) > 0$
- Symmetry: $d(\v x, \v y) = d(\v y, \v x)$
- Triangle inequality: $d(\v x, \v z) \leq d(\v x, \v y) + d(\v y, \v z)$ 
# 2. Similarity measures for numeric vectors
## 2.1. Minkowski distance
- Let $\v x = (x_1, x_2, \dots, x_m)$ and $\v y = (y_1, y_2, \dots, y_m)$ be two data points in $\R^m$. The distance: $$d_r(\v x, \v y) = \norm{\v x - \v y}_r = \bigg (\sum_{i=1}^m |x_i - y_i|^r\bigg)^\frac {1}{r}$$
- $d_r$ is a distance metric when $r \leq 1$. When $r < 1$, $d_r$ violates the triangle inequality.
### 2.1.1. Euclidean distance
- $$d_2(\v x, \v y) = \norm{\v x - \v y}_2 = \sqrt {\bigg (\sum_{i=1}^m |x_i - y_i|^2\bigg)}$$
- A line from $\v x$ to $\v y$.
### 2.1.2 Manhattan distance
$$d_1(\v x, \v y) = \norm{\v x - \v y}_1 = \sum_{i=1}^m |x_i - y_i|$$
## 2.2 Hamming distance
- Hamming distance between 2 numeric vectors is defined as the number of dimensions at which their values are different.
- Hamming distance satisfies the axioms.
## 2.3 Cosine distance
- $$\cos \theta = \frac {\v x \cdot \v y}{\norm {\v x} \norm {\v y}} = \frac {\sum_{i=1}^m x_i y_i}{\sqrt{\sum_{i=1}^m x_i^2} \sqrt{\sum_{i=1}^m y_i^2}}$$
- The cosine distance is defined as: $$d(\v x, \v y) = 1 - \cos \theta$$
- Cosine distance violates the identity axiom. 
- Cosine distance has the value in $[0, 2]$
# 3. Similarity measures for data distributions
## 3.1 Kullback-Leibler distance.
- Let $P = (p_1, p_2, \dots, p_m)$ and $Q = (q_1, q_2, \dots, q_m)$ be 2 discrete probability distribution. The Kullback-Leibler distance (KL divergence) from $Q$ to $P$ is defined as follows: $$D_{KL}(P \mid \mid Q) = \sum_{i=1}^m p_i \log \frac {p_i}{q_i}$$
- The above equation ignores position where $p_i = 0$ or $q_i = 0$.
- $D_{KL}(P \mid \mid Q) \geq 0$. $D_{KL}(P \mid \mid Q) = 0$ if the two distributions are identical. $D_{KL}(P \mid \mid Q)$ is small when the distributions have similar shapes, and large otherwise.
- KL divergence satisfies the identity and positivity, but does not satisfy the symmetry axiom because $D_{KL}(P \mid \mid Q)$.

In order to ensure the symmetry, let $S = (s_1, s_2, \dots, s_m)$ in which $s_i = \frac{p_i + q_i}{2}$. Then, the following distance is symmetric: 
$$
d_{KL}(P, Q) = D_{KL}(P \mid \mid S) + D_{KL}(Q \mid \mid S)
$$
Or 
$$
d_{KL}(P, Q) = \frac {D_{KL}(P \mid \mid Q) + D_{KL}(Q \mid \mid P)} 2
$$
# 4. Similarity measures for categorical data.
- A categorical attribute can take on 2 or more stages
- Let $\v x_i = (x_{i1}, x_{i2}, \dots, x_{im})$ and $\v x_j = (x_{j1}, x_{j2}, \dots, x_{jm})$ be 2 data instances represented in $m$ categorical attributes. The distance between the 2 instances is: $$d(\v x_i, \v x_j) = \frac {m-s} m$$ where $s$ is the number of matches, i.e., the number of attributes for which $\v x_i$ and $\v x_j$ are in the same state (same value).
- Weights for attributes can be used to highlight attributes that are more important than others.
# 5. Similarity measure for ordinal attributes

- Let an ordinal attribute $X_a$ has $K_a$ ordered states/values, representing the ranking $1,2,\dots,K_a$. Suppose a data instance $\v x_i$ has the value $x_{ia}$ on the attribute $X_a$. Replace $x_{ia}$ by its rank, $r_{ia} \in {1,2,\dots,K_a}$.
- Normalize its rank value onto $[0.0, 1.0]$: $$z_{ia} = \frac {r_{ia}-1}{K_a -1}$$
## 6. Jaccard distance
- Let $A$ and $B$ be 2 sets. The Jaccard index of $A$ and $B$ is defined as: $$J(A,B) = \frac {|A \cap B|} {|A \cup B|}$$
- Then, the Jaccard distance between $A$ and $B$ is defined as: $$d(A, B) = 1- J(A,B) = 1- \frac {|A \cap B|}{|A \cup B|}$$
- Jaccard satisfies all four axioms.

# 7. Levenshtein distance

$$
\begin{align}
d_{i,0} & = \sum_{k=1}^i w_\text{del} (a_k) \\
d_{0,j} & = \sum_{k=1}^j w_\text{ins} (b_k) \\
d_{i,j} & = 
\begin{cases}
d_{i-1, j-1} & \text{for } a_i = b_j \\
\min 
\begin{cases}
d_{i-1,j} + w_\text{del}(a_i) \\
d_{i,j-1} + w_\text{ins}(b_j) \\
d_{i-1,j-1} + w_\text{sub}(a_i,b_j)
\end{cases} & \text{for } a_i \not = b_j
\end{cases}
\end{align}
$$

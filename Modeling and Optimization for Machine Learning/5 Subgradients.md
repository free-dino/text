$\newcommand{\norm}[1]{\left \lVert #1 \right\rVert}$
## Subgradients
Recall that for convex and differentiable $f$,
$$
f(y) \ge f(x) + \nabla f(x)^T(y-x) \qquad \forall x,y
$$
That is, linear approximations always underestimates $f$

A subgradient of a convex function $f$ at $x$ is any $g \in \mathbb R^n$ such that
$$
f(y) \ge f(x) + g^T(y-x) \qquad \forall y
$$
* Always exists
* If $f$ differentiable at $x$, then $g = \nabla f(x)$ uniquely
* Same definition works for nonconvex $f$ (however, subgradients need not exist)
## Subdifferential
Set of all subgradients of convex $f$ is called the subdifferential:
$$\partial f(x) = \{ g \in \mathbb R^n : f(y) \ge f(x) + g^T(y-x) \quad \forall y \}$$
* Nonempty (only for convex $f$)
* $\partial f(x)$ is closed and convex (even for nonconvex $f$)
* If $f$ is differentiable at $x$, then $\partial f(x) = \{\nabla f(x) \}$
* If $\partial f(x) = \{g\}$ then $f$ is differentiable at $x$ and $\nabla f(x) = g$

## Connection to convex geometry
Convex set $C \subseteq \mathbb R^n$, consider indicator $I_C : \mathbb R^n \rightarrow \mathbb R$,
$$
I_C (x) = I\{x \in C\} = \begin{cases}
0 & \text{if } x\in C \\
\infty &\text{if } x \not \in C
\end{cases}
$$
For $x \in C$, $\partial I_C(x) = \mathcal N_C(x)$, the normal cone of $C$ at $x$ is, recall
$\mathcal N_C(x) = \{g \in \mathbb R^n: g^Tx \ge g^Ty \quad \text{for any } y \in C\}$

Why? By the definition of subgradient g,
$$
I_C(y) \ge I_C(x)+ g^T(y-x) \quad \text{for all } y
$$
* For $y \not \in C$, $I_C(y) = \infty$
* For $y \in C$, this means $0 \ge g^T(y-x)$
![[Pasted image 20240322160127.png]]

## Subgradient calculus
Basic rules for convex functions:
* Scaling: $\partial (af) = a \cdot \partial f$ provided $a>0$
* Addition: $\partial(f_1 + f_2) = \partial f_1 + \partial f_2$
* Affine composition: if $g(x) = f(Ax+b)$, then $$\partial g(x) = A^T \partial f(Ax+b)$$
* Finite pointwise maximum: if $f(x) = \max_{i=1,...,m} f_i(x)$, then $$\partial f(x) = \text{conv} \Big( \bigcup_{i:f_i(x)=f(x)} \partial f_i(x)\Big)$$ convex hull of union of subdifferentials of active functions at $x$
* General composition: if $$f(x) = h \big(g(x)\big) = h\big(g_1(x), ..., g_k(x)\big)$$ where $g: \mathbb R^n \rightarrow \mathbb R^k$, $h: \mathbb R^k \rightarrow \mathbb R$, $f: \mathbb R^n \rightarrow \mathbb R$, $h$ is convex and nondecreasing in each argument, g is convex, then $$ \partial f(x) \subseteq \big\{ p_1q_1 + ... + p_kq_k: p \in \partial h(g(x)),\space q_i \in \partial g_i(x), \space i=1,...,k \big\}$$
* General pointwise maximum: If $f(x) = \max_{s\in S} f_s(x)$, then $$ \partial f(x) \supseteq \text{cl}\Big\{ \text{conv} \Big( \bigcup_{s:f_x(x) = f(x)} \partial f_s(x)\Big)\Big\}$$ under some regularity conditions (on $S$, $f_s$), we get equality
* Norms: important special case. To each norm $\norm{\cdot}$, there is a dual norm $\norm{\cdot}_*$ such that $$ \norm{x} = \max_{\norm{z}_* \le 1} z^Tz$$ (For example, $\norm{\cdot}_p$ and $\norm{\cdot}_q$ are dual when $1/p + 1/q = 1$.). In fact, for $f(x) = \norm{x}$ (and $f_z(x)=z^Tx$), we get equality: $$\partial f(x) = \text{cl}\Big\{\text{conv} \Big ( \bigcup_{z:f_z(x)=f(x)} \partial f_z(x)\Big )\Big\}$$ Note that $\partial f_z(x)=z$. And if $z_1$, $z_2$ each achieve the max at $x$, which means that $z_1^T x = z_2^T x = \norm{x}$, then by linearity, so will $tz_1 + (1-t)z_2$ for any $t \in [0,1]$. Thus $$\partial f(x) = \arg \max_{\norm{z}_* \le 1} z^Tx$$
## Optimality condition
For any $f$ (convex or not),
$$f(x^*) = \min_x f(x) \iff 0 \in \partial f(x^*)$$
That is, x^* is a minimizer if and only if 0 is a subgradient of $f$ at $x^*$. This is called the subgradient optimality condition
Why?
Because $g=0$ being a subgradient means that for all $y$ 
$$f(y) \ge f(x^*) + 0^T (y-x^*) = f(x^*)$$
Note the implication for a convex and differentiable function $f$, with $\partial f(x) = \{\nabla f(x)\}$.

## Derivation of first-order optimality
Example of the power of subgradients: we can use what we have learned so far to derive the first-order optimality condition. Recall$$\min_x f(x) \quad \text{subject to } x\in C$$ is solved at $x$, for $f$ convex and differentiable, if and only if
$$
\nabla f(x)^T(y-x) \ge 0 \quad \forall y\in C
$$
Intuitively: says that gradient increases as we move away from $x$. 
Proof:
First recast problem as
$$\min_x f(x) + I_C(x)$$
Now apply subgradient optimality: $0 \in \partial(f(x)+I_C(x))$ 
Observe
$\qquad 0 \in \partial(f(x)+I_C(x))$
$$
\begin{align}
& \iff 0 \in \{\nabla f(x)\} + \mathcal N_C(x) \\
& \iff -\nabla f(x) \in \mathcal N_C(x) \\
& \iff -\nabla f(x)^Tx \ge -\nabla f(x)^Ty \quad \forall \space y \in C \\
& \iff \nabla f(x)^T(y-x) \ge 0 \quad \forall \space y \in C
\end{align}
$$
as desired
Note: the condition $0 \in \nabla f(x) + \mathcal N_C(x)$ is a fully general condition for optimality in convex problems. But it's not always easy to work with (KKT conditions, later, are easier)

## Example: lasso optimality conditions
Given $y \in \mathbb R^n$, $X \in \mathbb R^{n \times p}$, lasso problem can be parametrized as
$$\min_\beta \frac{1}{2} \norm{y-X\beta}_2^2 + \lambda \norm{\beta}_1$$
where $\lambda \ge 0$. Subgradient optimality:
$\quad 0 \in \partial \Big(\frac{1}{2} \norm{y-X\beta}_2^2 + \lambda \norm{\beta}_1\Big)$
$$
\begin{align}
& \iff 0 \in -X^T(y-X\beta) + \lambda \partial\norm{\beta}_1 \\
& \iff X^T(y-X\beta) = \lambda v
\end{align}
$$
for some $v \in \partial \norm{\beta}_1$, i.e.,
$$
v_i \in 
\begin{cases}
\{1\} & \text{if } \beta_i > 0 \\
\{-1\} & \text{if } \beta_i < 0, \quad i=1,...,p \\
[-1,1] & \text{if } \beta_i = 0
\end{cases}
$$
Write $X_1,...,X_p$ for columns of $X$. Then our condition reads:
$$
\begin{cases}
X^T_i(y-X\beta) = \lambda\cdot\text{sign}(\beta_i) & \text{if } \beta_i \not = 0 \\
|X_i^T(y-X\beta)|  \le \lambda & \text{if } \beta_i = 0
\end{cases}
$$
Note: subgradient optimality conditions don't lead to closed-form expression for a lasso solution ... However they do provide a way to check lasso optimality

They are also helpful in understanding the lasso estimator; e.g., if $|X^T_i (y-X\beta)| \le \lambda$, then $\beta_i = 0$ (used by screening rules, later?)

## Example soft-thresholding
Simplified lasso problem with $X=I$
$$
\min_\beta \frac{1}{2} \norm{y-\beta}_2^2 + \lambda \norm{\beta}_1
$$
This we can solve directly using subgradient optimality. Solution is $\beta = S_\lambda(y)$, where $S_\lambda$ is the soft-thresholding operator:
$$
[S_\lambda(y)]_i = 
\begin{cases}
y_i - \lambda &\text{if } y_i > \lambda \\
0 &\text{if } - \lambda\le y_i \le \lambda, \quad i=1,...,n \\
y_i + \lambda &\text{if } y_i < -\lambda
\end{cases}
$$
Check: from last slide, subgradient optimality conditions are
$$
\begin{cases}
y_i - \beta_i = \lambda \cdot \text{sign}(\beta_i) & \text{if } \beta_i \not = 0 \\
|y_i - \beta_i| \le \lambda & \text{if} \beta_i = 0
\end{cases}
$$
Now plug in $\beta = S_\lambda(y)$ and check these are satisfied:
* When $y_i > \lambda$, $\beta_i = y_i -\lambda > 0$, so $y_i - \beta_i = \lambda = \lambda \cdot 1$
* When $y_i < -\lambda$, argument is similar
* When $|y_i|\le \lambda$, $\beta_i = 0$, and $|y_i - \beta_i| = |y_i| \le \lambda$
![[Pasted image 20240322220231.png]]

## Example: distance o a convex set

Recall the distance function to a closed, convex set $C$:
$$
\text{dist}(x,C) = \min_{y \in C} \norm{y-x}_2
$$
This is a convex function. What are its subgradients?
Write $\text{dist}(x, C) = \norm{x-P_C(x)}_2$, where $P_C(x)$ is the projection of $x$ onto $C$. It turns out that when $\text{dist}(x,C) >0$,
$$
\partial \text{dist}(x,C) = \Big\{\frac{x-P_C(x)}{\norm{x-P_C(x)}}_2\Big\}
$$
Only has one element, so in fact $\text{dist}(x,C)$ is differentiable and this is its gradient.

We will only show one direction, i.e., that
$$ \frac{x-P_C(x)}{\norm{x-P_C(x)}}_2 \in \partial \text{dist}(x,C)$$
Write $u = P_C(x)$. Then by first-order optimality conditions for a projection,
$$(x-u)^T(y-u) \le 0 \qquad \forall \space y\in C$$
Hence
$$C \subseteq H = \{y: (x-u)^T(y-u) \le 0 \}$$
Claim:
$$\text{dist}(y,C) \ge \frac{(x-u)^T(y-u)}{\norm{x-u}_2} \quad \forall \space y$$
Check: first, for $y \in H$, the right-hand side is $\ge 0$
Now for $y \not \in H$, we have $(x-u)^T(y-u) = \norm{x-u}_2 \norm{y-u}_2 \cos \theta$ where $\theta$ is the angle between $x-u$ and $y-u$. Thus
$$
\frac{(x-u)^T(y-u)}{\norm{x-u}_2} = \norm{y-u}_2 \cos \theta = \text{dist}(y,H) \le \text{dist}(y,C)
$$
as desired
Using the claim, we have for any $y$
$$
\begin{align}
\text{dist}(y,C) & \ge \frac{(x-u)^T(y-x+x-u)}{\norm{x-u}_2} \\
& = \norm{x-u}_2 + \Big(\frac{x-u}{\norm{x-u}}_2\Big)^T (y-x)
\end{align}
$$
Hence $g = (x-u)/\norm{x-u}_2$ is a subgradient of $\text{dist}(x,C)$ at $x$.
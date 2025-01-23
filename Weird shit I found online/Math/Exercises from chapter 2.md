# 2.1
We consider $(\R \setminus \{ -1\}, \star)$, where
$$
a \star b := ab + a + b, \qquad a,b \in \R \setminus \{ -1\} 
$$
a. Show that $(\R \setminus \{-1\}, \star)$ is an Abelian group
b. Solve $$3 \star x \star x = 15$$ in the Abelian group $(\R \setminus \{ -1\}, \star)$ where $\star$ is defined as above.

--------------------------------------------------------

> #Theory: Groups
> Consider a set $\mathcal G$ and an operation $\otimes: \mathcal G \times \mathcal G \to \mathcal G$ defined on $\mathcal G$. Then $G:= (\mathcal G, \otimes)$ is called a group if following hold:
> 
> 1. Closure of $\mathcal G$ under $\otimes: \forall x, y \in \mathcal G: x \otimes y \in \mathcal G$
> 2. Associativity: $\forall x, y, z \in \mathcal G: (x \otimes y) \otimes z = x \otimes (y \otimes z)$
> 3. Neutral element: $\exists e \in \mathcal G$ $\forall x \in \mathcal G : x \otimes e = x$ and $e \otimes x = x$
> 4. Inverse element: $\forall x \in \mathcal G$ $\exists y \in \mathcal G: x \otimes y = e$ and $y \otimes x = e$, where $e$ is the neutral element. We often write $x^{-1}$ to denote the inverse element of $x$.
> If additionally $\forall x, y \in \mathcal G : x \otimes y = y \otimes x$, then $G = (\mathcal G, \otimes)$ is an Abelian group (commutative)

> #Solution:
> a. 
> **Closure of $(\R \setminus \{-1\}, \star)$ under $\star$**:
> Suppose $a \star b = ab + a+ b = -1$ $$ \begin{align}  \iff &ab +a +b +1 = 0 \\ \iff &\underbrace{(a+1)}_{\not = 0} \underbrace{(b+1)}_{\not = 0} = 0 \text{ (contradict)} \\ \implies &a \star b \not = -1\end{align}$$
> $\implies(\R \setminus \{-1\}, \star)$ is closed under $\star$.
> **Associativity**: 
> Suppose $a,b, c \in \R \setminus \{ -1\}$, we have 
> $$\begin{align} (a \star b) \star c &= (ab +a+b)\star c \\ &= (ab+a+b)c + ab+a+b+c \\ & = abc +ac+bc +ab +a +b+c\end{align} \tag{1}$$
> $$\begin{align} a \star (b \star c) &= a \star(bc + b+c)\\ &=abc + ac + bc + ab + a + b+ c   \end{align} \tag{2}$$
> From (1) and (2) $\implies (a \star b) \star c = a \star (b \star c)$
> **Neutral element**: 
> Suppose:
> $$\begin{align} a \star b = &  ab + a + b = a \\ \iff &ab + b = 0 \\ \iff & b(a+1) = 0 \\ \iff & b=0 \text{ (since } a, b \in \R \setminus \{-1\}) \end{align}$$
> 

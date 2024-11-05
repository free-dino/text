- **Commutativity**:
  Suppose $\alpha = a+bi$  and $\beta = c+di$,where $a,b,c,d \in \R$. 
  The [[1. Real space and Complex Space#^881fa0|definition of complex numbers]] show that:$$\begin{align}\a+\b &= (a+bi)+(c+di)\\ &=(a+c)+(b+d)i\end{align} \tag1$$and$$\begin{align}\b+\a &= (c+di)+(a+bi)\\ &=(c+a)+(d+b)i\end{align} \tag2$$ From $(1)$ and $(2) \implies \a+\b = \b+\a$, $\forall \a, \b \in \C$
   Similarly, $$\begin{align}\alpha \beta &= (a+bi)(c+di)\\  &= (ac-bd)+ (ad+bc)i\end{align} \tag3$$
   and $$\begin{align}\beta \alpha &= (c+di)(a+bi) \\ &= (ca-db)+(cb+da)i\end{align} \tag4$$
   From $(3)$ and $(4) \implies$ $\alpha \beta = \beta \alpha$, $\forall \a, \b \in \C$ ^da644a
- **Associativity**:
  Suppose $\a = a+bi$, $\b=c +di$ and $\ld = e +fi$, where $a,b,c,d,e,f \in \R$. The [[1. Real space and Complex Space#^881fa0|definition of complex numbers]] show that $$(\a+\b)+\ld =(a+c+e)+(b+d+f)i \tag5$$and$$\a+(\b+\ld)=(a+c+e)+(b+d+f)i\tag6$$From $(5)$ and $(6) \implies (\a +\b)+\ld=\a+(\b+\ld)$, $\forall \a,\b,\ld \in \C$
  Similarly, $$(\a \b)\ld = (ace-bde-adf-bcf)+(ade+bce+acf-bdf)i\tag 7$$and$$\a(\b\ld) = (ace-bde-adf-bcf)+(ade+bce+acf-bdf)i \tag 8$$From $(7)$ and $(8) \implies (\a\b)\ld = \a(\b\ld)$, $\forall \a, \b, \ld \in \C$   ^10ce7f
- **Identities**
  Suppose: $\ld= a+bi$, from the [[1. Real space and Complex Space#^881fa0|definition of complex numbers]] we know that $0 = 0 + 0i$, then$$\ld + 0 = (a+0)+(b+0)i = a+bi = \ld \tag 9$$So $\ld + 0 = \ld$, $\forall \ld \in \C$
  Similarly, we know that $1= 1 + 0i$, then $$\ld \cdot1 = (a+bi)(1+0i) = a+bi = \ld$$ So $\ld \cdot 1 = \ld$, $\forall \ld \in \C$ ^12d8d0
- Additive inverse
  Suppose there exist $\b, \ld \in \C$ such that $\a+\b = 0$ and $\a + \ld = 0$, so with [[#^12d8d0|identity property]], we have:$$\b = \b + 0 = \b + (a+\b) = \b + (\a+ \ld)$$ With [[#^da644a|commutativity]] and [[#^10ce7f|associativity]] properties, we have: $$\b + (\a +\ld) = (\b +\a) + \ld = \ld + 0 = \ld$$ So $\b = \ld \implies$ for every $\a \in \C$, there is a unique $\b \in \C$ such that $\a +\b =0$  ^3c5509
- Multiplicative inverse
  Suppose there exist $\b, \ld \in \C$ such that $\a \b =1$ and $\a \ld =1$, so with [[#^12d8d0|identity]] [[#^da644a|commutativity]] and [[#^10ce7f|associativity]] properties, we have:$$\b = \b \cdot 1 =\b \cdot(\a \b) = \b\cdot(\a \ld) = (\b\a)\ld = \ld$$ ^418982
- Distributive property:
  Suppose $\a = a+bi$, $\b=c +di$ and $\ld = e +fi$, where $a,b,c,d,e,f \in \R$. The [[1. Real space and Complex Space#^881fa0|definition of complex numbers]] show that:$$\begin{align}\ld(\a + \b) &= (e+fi)\big((a+c)+(b+d)i\big)\\ & = (ae+ce -fb -fd)+(af+cf+eb+ed)i\end{align} \tag {10}$$and$$\begin{align}\ld \a + \ld \b &= (e+fi)(a+bi)+(e+fi)(c+di) \\ &= (ae+ce-fb-fd)+(af+cf+eb+ed)i\end{align} \tag{11}$$From $(10)$ and $(11) \implies \ld(\a+\b) = \ld \a + \ld \b$, $\forall \ld, \a, \b \in \C$  ^512305
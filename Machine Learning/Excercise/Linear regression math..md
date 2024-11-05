1. Linear regression
   a. Assume that you record a scalar input $x$ and a scalar output $y$. First you record $x_1 = 2, y_1=-1$ and thereafter $x_2=3, y_2=1$. Assume a linear regression model $y= \theta_0 + \theta_1 x + \epsilon$ and learn the parameters with maximum likelihood $\hat \Theta$ with the assumption $\epsilon \sim \mathcal N(0, \sigma_\epsilon^2)$. Use the model to predict the output for the test input $x_*=4$, and add the model to the plot.
   $$
   \mathbf X = \begin{bmatrix} 1 & 2 \\ 1 &3 \end{bmatrix} \qquad \qquad \qquad  \vec{\mathbf y} =\begin{bmatrix} -1 \\ 1\end{bmatrix}
   $$
   We have:
   $$
   \mathbf X ^ \top \mathbf X = \begin{bmatrix} 1 & 1 \\ 2 & 3\end{bmatrix} \begin{bmatrix} 1 & 2 \\ 1 & 3\end{bmatrix} = \begin{bmatrix} 2 & 5 \\5 & 13\end{bmatrix}
   $$
   which is invertible because $\det{(\mathbf X ^ \top \mathbf X)}=1$. This implies that $\vec {\mathbf {\hat{\Theta}}}$ has a unique solution.
   Now we have the normal equation:
   $$
   \begin{align}
   \vec{\mathbf{\hat \Theta}} &= (\mathbf X ^ \top \mathbf X)^{-1} \mathbf X^ \top \vec{\mathbf y} \\
   &= \begin{bmatrix} 2 & 5 \\5 & 13\end{bmatrix}^{-1}\begin{bmatrix} 1 & 1 \\ 2 & 3\end{bmatrix}
   \begin{bmatrix} -1 \\ 1\end{bmatrix} \\
   &= \begin{bmatrix} 13 & -5\\ -5 & 2\end{bmatrix} \begin{bmatrix} 0 \\ 1\end{bmatrix} \\
   &= \begin{bmatrix} -5 \\ 2\end{bmatrix}
   \end{align}
   $$
   $$
   \implies \hat y_*(x_* = 4) = \begin{bmatrix} -5 & 2\end{bmatrix} \begin{bmatrix} 1 \\4\end{bmatrix} = 3
   $$
   b. Now assume you have made a third observation $y_3=2$ for $x_3=4$. Predict for $x_*=5$
   We have:
   $$
   \mathbf X = \begin{bmatrix} 1 & 2 \\ 1 &3 \\ 1& 4\end{bmatrix} \qquad \qquad \qquad \vec{\mathbf y}=\begin{bmatrix} -1 \\ 1 \\ 2\end{bmatrix}
   $$
   $$
   \mathbf X ^ \top \mathbf X = \begin{bmatrix} 1 & 1 & 1\\ 2 & 3 & 4\end{bmatrix} \begin{bmatrix} 1 & 2 \\ 1 & 3 \\ 1 & 4\end{bmatrix} = \begin{bmatrix} 3 & 9 \\9 & 29\end{bmatrix}
   $$
   which is invertible because $\det \mathbf X ^ \top \mathbf X = 6$. This implies that $\vec{\mathbf {\hat{\Theta}}}$ has a unique solution.
   Now we have the normal equation:
   $$
   \begin{align}
   \vec{\mathbf{\hat \Theta}} &= (\mathbf X ^ \top \mathbf X)^{-1} \mathbf X^ \top \vec{\mathbf y} \\
   &= \begin{bmatrix} 3 & 9 \\9 & 29\end{bmatrix}^{-1}
   \begin{bmatrix} 1 & 1 & 1\\ 2 & 3 & 4\end{bmatrix}
   \begin{bmatrix} -1 \\ 1 \\ 2\end{bmatrix} \\
   &= \begin{bmatrix} \frac{29}{6} & \frac{-3}{2}\\ \frac{-3}{2} & \frac{1}{2}\end{bmatrix} \begin{bmatrix} 2 \\ 9\end{bmatrix} \\
   &= \begin{bmatrix} \frac{-23}{6} \\ \frac{3}{2}\end{bmatrix}
   \end{align}
   $$
   $$
   \implies \hat y_*(x_* = 5) = \begin{bmatrix} \frac{-23}{6} & \frac 3 2\end{bmatrix} \begin{bmatrix} 1 \\5\end{bmatrix} = \frac{11}3
   $$
   c. Repeat b. but this time using a model without intercept term.
   $$
   \mathbf X = \begin{bmatrix} 2 \\ 3 \\ 4\end{bmatrix} \qquad \qquad \qquad \vec{\mathbf y}=\begin{bmatrix} -1 \\ 1 \\ 2\end{bmatrix}
   $$
   $$
   \mathbf X ^ \top \mathbf X = \begin{bmatrix}  2 & 3 & 4\end{bmatrix}
   	\begin{bmatrix} 2 \\ 3 \\ 4\end{bmatrix} = 29
   $$
   which is invertible because $\det \mathbf X ^ \top \mathbf X = 29$. This implies that $\vec{\mathbf {\hat{\Theta}}}$ has a unique solution.
   $$
   \begin{align}
   	\vec{\mathbf{\hat \Theta}} &= (\mathbf X ^ \top \mathbf X)^{-1} \mathbf X^ \top \vec {\mathbf y} \\
   	&=29^{-1}
   	\begin{bmatrix} 2 & 3 & 4\end{bmatrix}
   	\begin{bmatrix} -1 \\ 1 \\ 2\end{bmatrix} \\
   	&= \frac{1}{29}
   	\cdot9 \\
   	&= \frac 9 {29}
   	\end{align}
   $$
   d. Use Ridge regression:
   $$
   \begin{align}
   	\vec{\mathbf{\hat \Theta }} &= (\mathbf X ^ \top \mathbf X + \lambda \mathbf I_n)^{-1} \mathbf X ^ \top \vec{\mathbf y} \\
   	& = (\mathbf X ^ \top \mathbf X + \mathbf I_2)^{-1} \mathbf X ^ \top \vec{\mathbf y} \\
   	& = 
   	\Bigg(\begin{bmatrix} 1 & 2 \\ 1 & 3 \\ 1 & 4\end{bmatrix} ^ \top \begin{bmatrix} 1 & 2 \\ 1 & 3 \\ 1 & 4\end{bmatrix} + \begin{bmatrix} 1 & 0 \\ 0 & 1\end{bmatrix} \Bigg)^{-1} \begin{bmatrix} 1 & 2 \\ 1 & 3 \\ 1 & 4\end{bmatrix} ^ \top \begin{bmatrix} -1 \\ 1 \\ 2\end{bmatrix} \\
   	& = 
   	\Bigg(\begin{bmatrix} 1 & 1 & 1 \\ 2 & 3 & 4 \end{bmatrix} \begin{bmatrix} 1 & 2 \\ 1 & 3 \\ 1 & 4\end{bmatrix} + \begin{bmatrix} 1 & 0 \\ 0 & 1\end{bmatrix} \Bigg)^{-1} \begin{bmatrix} 1 & 1 & 1 \\ 2 & 3 & 4\end{bmatrix} \begin{bmatrix} -1 \\ 1 \\ 2\end{bmatrix} \\
   	& =
   	\Bigg(\begin{bmatrix} 3 & 9 \\ 9 & 29 \end{bmatrix} +  \begin{bmatrix} 1 & 0 \\ 0 & 1\end{bmatrix} \Bigg)^{-1}\begin{bmatrix} 2 \\ 9\end{bmatrix} \\
   	& = 
   	\begin{bmatrix} 4 & 9 \\ 9 & 30 \end{bmatrix}^{-1} \begin{bmatrix} 2 \\ 9\end{bmatrix} \\
   	& =
   	\begin{bmatrix} \frac{10}{13} & \frac{-3}{13} \\ \frac{-3}{13} & \frac{4}{39} \end{bmatrix} \begin{bmatrix} 2 \\ 9\end{bmatrix} \\
   	& = 
   	\begin{bmatrix} \frac{-7}{13} \\ \frac{6}{13}  \end{bmatrix} \\
   	\implies \hat y = \frac{-7}{13} + \frac{6}{13} \cdot 5 \approx 1.77
   	\end{align}
   $$
   e.  Multidimensional output $$
   \begin{align}
   \hat{\mathbf \Theta} &= ( \mathbf X ^ \top \mathbf X)^{-1} \mathbf X^\top \mathbf Y \\
   & = \Bigg(\begin{bmatrix} 1 & 2 \\ 1& 3 \\ 1& 4\end{bmatrix}^\top \begin{bmatrix} 1 & 2 \\ 1& 3 \\ 1& 4 \end{bmatrix} \Bigg)^{-1} \begin{bmatrix} 1 & 2 \\ 1& 3 \\ 1& 4\end{bmatrix} ^ \top \begin{bmatrix} -1 & 0 \\ 1& 2 \\ 2& -1\end{bmatrix} \\
   & = 
   \Bigg(
   \begin{bmatrix} 1 & 1 & 1 \\ 2 & 3 & 4 \end{bmatrix}
   \begin{bmatrix} 1 & 2 \\ 1& 3 \\ 1& 4 \end{bmatrix}
   \Bigg)^{-1} \begin{bmatrix} 1 & 1 & 1 \\ 2 & 3 & 4 \end{bmatrix}
   \begin{bmatrix} -1 & 0 \\ 1& 2 \\ 2& -1 \end{bmatrix} \\
   & = 
   \begin{bmatrix} \frac{29}{6} & \frac{-3}{2} \\ \frac{-3}{2} & \frac{1}{2} \end{bmatrix} \begin{bmatrix} 2 & 1 \\ 9 & 2 \end{bmatrix} \\
   & = 
   \begin{bmatrix} \frac{-23}{6} &\frac{11}{6} \\ 
   \frac{3}{2} & \frac{-1}{2}
   \end{bmatrix}
   \end{align}
   $$
2. Nonlinear transformations of input variables
   (a) is obviously a linear regression model
   (b) is obviously a linear regression model as $\vec{\mathbf x} = \begin{bmatrix} 1 \\ v \\ v^2 \\ v^3 \\ v^4 \end{bmatrix}$
   (c) is obviously a linear regression model as  $\vec{\mathbf x} = \begin{bmatrix} 1 \\ v \\ \cos(v) \\ \sin(v) \end{bmatrix}$
   (d) $c \sin (v + \phi) = \sin(v)\cos(\phi) + \sin(\phi)\cos(v) \implies y= \theta_0 + \sin(v)\cos(\phi) + \sin(\phi)\cos(v) + \epsilon \iff y= \theta_0 + \theta_1\sin(v) + \theta_2\cos(v) + \epsilon \implies$ this is a linear regression model
   (e) is unable to be written as a linear regression form
3. Deriving least squares from maximum likelihood
   $$
   \vec{\hat{\mathbf \Theta}} = \arg \min_{\mathbf \Theta} \Bigg \{  \sum_{i=1}^n (\theta_0 + \theta_1 x_{i1} + \cdots + \theta_{p} x _{ip} - y_i)^2 \Bigg \}
   $$
   With $y_i = \theta_0 + \theta_1 x_{i1} + \cdots + \theta_{p} x _{ip} + \epsilon \iff \epsilon = \theta_0 + \theta_1 x_{i1} + \cdots + \theta_{p} x _{ip} - y_i \sim \mathcal N(0, \sigma_\epsilon^2)$ So:
   $$
   \begin{align}
   \vec{\hat{\mathbf \Theta}} &= \arg \max_{\mathbf \Theta} p(\vec{\mathbf y}\mid \mathbf X; \vec{\mathbf \Theta}) \\
   & = \arg \max_{\mathbf \Theta} \prod_{i=1}^n p(y_i \mid \vec{\mathbf x}_i; \vec{\mathbf \Theta}) \\
   & = 
   \end{align}
   $$ 

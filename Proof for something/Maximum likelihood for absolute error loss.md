Maximum likelihood:
$$
\vbs \theta = \arg \max_{\vbs \theta} p(\v y \mid \mathbf X; \vbs \theta)
$$
Assume noise term $\epsilon$ are independent, with a Laplace distribution:
$$
\epsilon \sim \mathcal L(0, b_\epsilon) 
$$
Since $\v y = \mathbf X \vbs \theta + \vbs \epsilon$, and the noise term are independent, which implies all observed data points are independent, and $p(\v y \mid \mathbf X; \vbs \theta)$ can be factorize as:
$$
p(\v y \mid \mathbf X; \vbs \theta) = \prod_{i=1}^n p(y_i\mid \v x_i, \vbs \theta)
$$
Now we consider the normal distribution over the random variable $y_i$ with the mean of $y= \vbs \theta ^ \top \v x + \epsilon$
$$
\begin{align}
p(y_i \mid \v x_i; \vbs \theta) &= \mathcal L(y_i, \vbs \theta ^\top \v x_i; b_\epsilon) \\
& = \frac 1 {2b_\epsilon} \exp(-\frac{|y_i - \vbs \theta ^\top \v x_i|}{ b_\epsilon})
\end{align}
$$
Taking the $\ln()$ from both sides, we have:
$$
\begin{align}
\ln p(\v y \mid \mathbf X; \vbs \theta) &= \sum_{i=1}^n \ln p (y_i \mid \v x_i ; \vbs \theta) \\
& = \sum_{i=1}^n \Big(\ln (\frac 1 {2 b_\epsilon}) - \frac{|y_i - \vbs \theta ^\top \v x_i|}{ b_\epsilon} \Big ) \\
& =  \sum_{i=1}^n \Big(- \ln(2b_\epsilon) - \frac 1 {b_\epsilon} |y_i - \vbs \theta ^\top \v x_i| \Big) \\
& = -n \ln(2b_\epsilon) - \frac{n}{b_\epsilon}|y_i - \vbs \theta ^\top \v x_i| 
\end{align}
$$
Removing the terms and factor independent of $\vbs \theta$ does not change the maximizing argument and we rewrite the equation as:
$$
\hvbs \theta = \arg \max_{\vbs \theta} p(\v y\mid \mathbf X; \vbs \theta) = \arg \min_{\vbs \theta} \frac 1 n \sum_{i=1}^n |\vbs \theta ^ \top \v x_i - y_i|
$$
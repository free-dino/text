Let $\frac 1 B \sum_{b=1}^B z_b = \bar z$ 

## $\E[\bar z]$ 
$$
\begin{align}
\E[\bar z] &= \E\Bigg [\frac 1 B \sum_{b=1}^B z_b\Bigg] \\
&= \frac 1 B \Bigg( \E[z_1] + \E[z_2] + \dots + \E[z_B]\Bigg) \\
& = \frac 1 B (B \mu) \\
& = \mu
\end{align}
$$

## $\text{Var}[\bar z]$
$$
\begin{align}
\text{Var}[\bar z] &= \text{Var}\Bigg [\frac 1 B \sum_{b=1}^B z_b\Bigg] \\
& = \frac 1 {B^2} \text{Var} \Bigg [\sum_{b=1}^B z_b\Bigg]
\end{align}
$$
Using Linear combination of Variance, we have:
$$
\begin{align}
\text{Var}\Bigg [\sum_{b=1}^B z_b\Bigg] & = \sum_{b, b'=1}^{B} \text{Cov}(z_b, z_{b'}) \\
& = \sum_{b=1}^B \text{Var}[z_b] + \sum_{b \not = b'} \text{Cov}(z_b, z_{b'})
\end{align}
$$
We have:
$$
\rho_{z_b, z_{b'}} = \frac {\text{Cov}{(z_b, z_{b'})}}{ \sigma_{z_b} \sigma_{z_{b'}}} \iff \text{Cov}(z_b, z_{b'}) = \rho \sigma^2
$$
Thus, 
$$
\text{Var}\Bigg [\sum_{b=1}^B z_b\Bigg] = B \sigma^2 + B(B-1)\sigma^2 
$$
That means:
$$
\begin{align}
\text{Var}[\bar z] &= \frac 1 {B^2} (B \sigma^2 + B(B-1)\rho\sigma^2) \\
& = \frac 1 {B} (\sigma^2 + (B-1)\rho \sigma^2) \\
& = \frac {\sigma^2} B - \frac{\rho \sigma^2}{B} +\rho \sigma^2 \\
& = \frac{(1-\rho)}{B} \sigma^2 + \rho \sigma^2
\end{align}
$$

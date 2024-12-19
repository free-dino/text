The definition of conditional probability:
$$
\P (B \mid A) = \frac {\P(A,B)}{\P(A)} \iff \P(A,B)=\P(A)\cdot \P(B \mid A) 
$$
The general chain rule:
$$
\begin{align}
\P(X_1, X_2, \dots, X_n) &= \P(X_1)\P(X_2 \mid X_1)\P(X_3\mid X_2, X_1)\dots\P(X_n \mid X_{n-1} \dots X_1) \\
&= \prod_i \P(X_i\mid X_1, X_2,\dots,X_{i-1})
\end{align}
$$
Markov's assumption:
$$
\begin{align}
&\P(w_1w_2\dots w_n) \approx \prod_i\P(w_i \mid w_{i-k}\dots w_{i-1}) \\
\iff & \P(w_i \mid w_1w_2\dots w_{i-1} \approx \P(w_1 \mid w_{i-k} \dots w_{i-1})) 
\end{align}
$$
## Unigram
$$
\begin{align}
\P(w_1 w_2 \dots w_n) \approx \prod_i \P(w_i)
\end{align}
$$
## Bigram
$$
\begin{align}
\P(w_1 w_2 \dots w_n) \approx \prod_i \P(w_i\mid w_{i-1})
\end{align}
$$
In general this is inefficient because language has long-term dependencies. But we can get away with N-gram models

# 1. N-gram
Estimating bigram probability using Maximum likelihood estimation (MLE)
$$
\P(w_i \mid w_{i-k}) = \frac {\text{count}(w_{i-1}w_i)}{\text{count}(w_{i-1})}
$$
We should calculate the whole thing in log space:

$$
\log(\prod_i p_i) = \sum_i \log p_i
$$
# 2. Perplexity
$$
\begin{align}
PP(W) &= \P(w_1w_2 \dots w_n)^{-\frac 1 n} \\
&= \sqrt[n]{\frac{1}{\P(w_1w_2 \dots w_n)}} \\
Chain \ \ rule: & \sqrt[n]{\prod_i \frac{1}{\P(w_i \mid w_{1} \dots w_{i-1})}} 
\end{align}
$$

=> Minimizing Perplexity = Maximizing the probability
=> Lower perplexity = better model

# 3. The Shannon visualizing method

$$
\begin{align}
&1.&\text{<s> } &\text{I } \\
&2. & &\text{I } &\text{want } \\
&3. & & &\text{want } &\text{to } \\
&4. & & & &\text{to } &\text{eat } \\
&5. & & & & &\text{eat } &\text{Chinese } \\
&6. & & & & & &\text{Chinese } & \text{food }\\
&7. & & & & & & &\text{food } & \text{<s>} \\
&\implies &\text{<s> } &\text{I } &\text{want } &\text{to } &\text{eat } &\text{Chinese } &\text{food } &\text{<s>}
\end{align}
$$
# 4. Add-one smoothing
Estimating bigram probability using Add-1 smoothing estimation
$$
\P(w_i \mid w_{i-k}) = \frac {\text{count}(w_{i-1}w_i)+1}{\text{count}(w_{i-1})+V}
$$
With V is the number of unique toke in the corpus

$$
\text{count}(w_{n-1}w_n) = \frac{[\text{count}(w_{n-1}w_n)+1]\times \text{count}(w_{n-1})}{\text{count}(w_{i-1})+V}
$$

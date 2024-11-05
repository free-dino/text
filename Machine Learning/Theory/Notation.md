1. General Math

| Symbol                          | Meaning                                                                                       |
| ------------------------------- | --------------------------------------------------------------------------------------------- |
| a                               | [[1. Real space and Complex Space#^009b28\|Scalar]]                                           |
| $\mathbf {\vec{a}}$             | Vector                                                                                        |
| $\mathbf A$                     | Matrix                                                                                        |
| $^\top$                         | Transpose                                                                                     |
| $\text{sign}(x)$                | $-1$ if $x<0$ and $+1$ if $x>0$                                                               |
| $\nabla$                        | del operator, $\nabla f$ is the gradient of $f$                                               |
| $\normvec{a}_1$                 | 1st norm of $\v a$                                                                            |
| $\normvec{a}_2$                 | 2nd norm of $\v a$                                                                            |
| $p(z)$                          | probability density <br> probability mass                                                     |
| $p(z\mid x)$                    | probability density (or mass) for $z$ conditioned on $x$                                      |
| $\mathcal N (z, \mu, \sigma^2)$ | Normal probability distribution for random variable z with mean $\mu$ and variance $\sigma^2$ |
2. Supervised learning problem

| Symbol          | Meaning                                 |
| --------------- | --------------------------------------- |
| $\v x$          | input                                   |
| $y$             | output                                  |
| $\v x_*$        | test input                              |
| $y_*$           | test output                             |
| $\pred y {x_*}$ | a prediction                            |
| $\epsilon$      | noise                                   |
| $n$             | number data points of training data     |
| $\mathcal T$    | Training data $\{\v x_i, y_i\}^n_{i=1}$ |
| $L$             | loss function                           |
| $J$             | cost function                           |
3. Supervised learning methods
   
| Symbol                     | Meaning                                                   |
| -------------------------- | --------------------------------------------------------- |
| $\vec{\boldsymbol \theta}$ | parameters to be learned from training data               |
| $g(\v x)$                  | model of $p(y \mid \v x)$                                 |
| $\lambda$                  | regularization parameter                                  |
| $\phi$                     | link function                                             |
| $h$                        | activate function                                         |
| $\mathbf W$                | weight matrix                                             |
| $\v b$                     | offset vector                                             |
| $\gamma$                   | learning rate                                             |
| $B$                        | number of members in an ensemble method                   |
| $\kappa$                   | kernel                                                    |
| $\vec{\boldsymbol \phi}$   | nonlinear feature transformation                          |
| $d$                        | dimension of $\vec{\boldsymbol \phi}$; number of features |
4. Evaluation of supervised method

| Symbol         | Meaning                                               |
| -------------- | ----------------------------------------------------- |
| $E$            | error function                                        |
| $E_{new}$      | new data error                                        |
| $E_{train}$    | training data error                                   |
| $E_{k-fold}$   | estimate of $\E {new}$ from $k$-fold cross validation |
| $E_{hold-out}$ | estimate of $\E {new}$ from hold-out validation data  |

   
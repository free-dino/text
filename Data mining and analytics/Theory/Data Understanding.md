The nature and characteristics of data:
- Data types
- Noisy, incomplete, missing, imbalanced,... data
- Data summarization (descriptive statistics)
- Data shape and distribution
- Correlation in data ^d70d66
- Other explicit and implicit dependencies in data

# 1. CRISP-DM
Cross-industry standard process for data mining. 
6 phases:
- 1. Business understanding $\downarrow$
- 2. Data understanding $\uparrow \downarrow$
- 3. Data preparation $\downarrow$
- 4. Modeling $\uparrow \downarrow$
- 5. Evaluation $\downarrow$, $\downarrow \to 1$
- 6. Deployment.

## 1.1 CRISP-DM phase 1: Business understanding
- **1. Determine business objectives:** 
  What the customer/company really wants to accomplish -> define business success criteria.
- **2. Assess situation: Determine:**
  Determine resources availability, project requirements, assess risk and contingencies and conduct a cost-benefit analysis. 
- **3. Determine data mining goals:**
  What success looks like from a technical data mining perspective
- **4. Produce project plan:**
  Select technologies and tools and define detailed plans for each project phase.

## 1.2 CRISP-DM phase 2: Data understanding
- **1. Collect initial data:**
- **2. Describe data:**
  It's surface properties like data format, number of records or field identities.
- **3. Explore data:**
  Query it, visualize it, identify relationships among the data.
- **4. Verify data quality:**
  How clean is the data? Document any quality issues

## 1.3 CRISP-DM phase 3: Data preparation
- **1. Select data:**
  Determine which datasets will be used and document reasons for the inclusion/exclusion
- **2. Clean data:**
  Correct, impute or remove erroneous values.
- **3. Construct data:**
  Derive new attributes that will be helpful.
- **4. Integrate data:**
  Create new datasets by combining data from multiple sources.
- **5. Format data:**
  Re-format data as necessary.

# 2. Data attribute:
- is a data field, representing a characteristic or feature of a data object.
- Observed values for a given attribute are known as observation.

## 2.1 Attribute data types:
- Categorical (Nominal)
- Binary
- Ordinal
- Numeric:
  - Interval-scaled
  - Ratio-scaled
  - Discrete vs Continuous.

## 2.2 Multivariate data analysis
- Multivariate mean vector: $$\v \mu = \E[\mat X] = \begin{bmatrix} \E[\v X_1] \\ \E[\v X_2] \\ \vdots \\ \E[\v X_d] \end{bmatrix} = \begin{bmatrix} \mu_1 \\ \mu_2 \\ \vdots \\ \mu_d \end{bmatrix} $$
- Covariance matrix: $$\mat \Sigma = \E[(\mat X - \v \mu)(\mat X - \v \mu)] = \begin{bmatrix} \sigma_1^2 & \sigma_{12} & \cdots & \sigma_{1d} \\
   \sigma_{21} & \sigma_{2}^2 & \cdots & \sigma_{2d} \\
   \vdots & \vdots & \ddots & \vdots \\
   \sigma_{d1} & \sigma_{d2} & \cdots & \sigma_{d}^2 \\
   \end{bmatrix}$$
- Classification, regression, clustering, association mining, etc.
- Visualization

## 2.3  IID data:
-> independently and identically distributed

- In reality, data points have some explicit or implicit dependencies among them.
- The dependencies: temporal, spatial, structural, referential, etc.
- Data with dependencies: dependency-oriented data or complex and structured data:
  - Time-series:
    - Contextual attributes: Define the context on the basis of which the implicit dependencies occur in the data.
    - Behavioral attributes: Represent the values that are measured in a particular context.
  - Discrete sequences and strings
  - Spatial
  - Spatiotemporal
  - Network and graph
  - Other forms:
    - Text
    - Natural language
    - Speech
    - Image
    - Video

# 3. Measure the central tendency of data

^b823e9

Suppose $\mathcal D = \{x_1, x_2, \dots, x_n \}$ is a sample consisting of $n$ observations of a variable or attribute X.

## 3.1 Mean:

^43d071

$$
\bar x = \frac 1 n  \sum_{i=1}^n x_i = \frac {x_1 + x_2 + \dots + c_n} n
$$
-> (Arithmetic) mean

### 3.1.1 Weighted mean or weighted average
$$
\bar x = \frac {\sum_{i=1}^n w_i x_i}{\sum_{i=1}^n w_i}
$$
### 3.1.2 Issues:
* Sensitivity to extreme values.
* We can use trimmed mean: chopping off values at the high and low extreme.

## 3.2 Median:

^dd53f6

- For skewed (asymmetric) data.
- Middle value in a set of ordered data values -> separates into 2 half.
- $$\text{median} = \frac {x_a + x_b} 2  \qquad a = \bigg \lceil \frac n 2 \bigg \rceil, b = \bigg \lfloor \frac n 2 + 1\bigg \rfloor$$
## 3.3 Mode
- A set of data which occurs the most frequently in the set. 
## 3.4 Midrange.
$$
\text{midrange} = \frac {\text{min + max}}{2}
$$
- Even more affected by outlier.

#  4. Measuring the dispersion of data
## 4.1 Range:
$$
\text{range} = \text{max - min}
$$
## 4.2 Quantiles
Suppose $\mathcal D$ are sorted in increasing numeric order.
-> Split into equal-size consecutive sets/parts -> Quantiles are POINTS
$\text{k}^\text{th}$ q-quantile is the value $x$ such that at most $\frac k q$ of the data values are less than $x$ and at most $\frac {(q-k)} q$ of the data values are more than $x$, where $k$ is an integer such that $0 < k < q$. There are $q-1$ q-quantiles.

## 4.3 Quartiles:
$(Q_1, Q_2, Q_3)$ dividing the distribution into 4 equal-size consecutive part.

$Q_1 = 25\%$
$Q_2 = 50 \%$, the median
$Q_3 = 75\%$

## 4.4 Interquartile range

$$
\text{IQR} = Q_3 - Q_1
$$
## 4.5 Five-number summary: 
$$
\{\min, Q_1, \text{median}, Q_3, \max \}
$$
## 4.6 Boxplots
- The ends of the box are $Q_1$ and $Q_3$
- The line is the median
- Whiskers terminated at the most extreme observations occurring within $1.5 \times \text{IQR}$ of the quartiles.
- useful for showing the central tendency, the data dispersion, the skewness of data distribution.
## 4.7 Variance and standard deviation
- Are measures of data dispersion. They indicate how spread out a data distribution is.
- Low std = the data observed tend to be very close to the mean and reverse.
- Variance: $$\sigma^2 = \frac 1 n \sum_{i=1}^n (x_i - \bar x)^2  = \bigg(\frac 1 n \sum_{i=1}^n x_i^2 \bigg) - \bar x^2$$
- Standard deviation: $\sigma$.

# 5. Correlation:
Reflecting the strength and direction of association between 2 random variables or two data attributes.
- Positive correlation: change in the same direction.
- Negative correlation: change in the opposite directions.
- Zero correlation: no dependency or relationship between variables.
## 5.1 Pearson correlation:

^fb038f

Measure of linear correlation between 2 sets of data -> not robust for handling outliers, non-linear and skewed distribution
$$
\rho_{XY} = \frac {\cov X Y}{ \sigma_X \sigma_Y}
$$

With: 
$$
\cov X Y = \E [(X-\mu_X)(Y - \mu_Y)]
$$
$$
\implies \rho_{XY} = \frac {\E [(X-\mu_X)(Y - \mu_Y)]} {\sigma_X \sigma_Y}
$$
And:
$$
\begin{align}
& \mu_X = \E [X] \\
& \mu_Y = \E [Y] \\
& \sigma^2_X = \E [(X-E[X])^2] =  \E[X^2] - (\E[X])^2 \\
& \sigma^2_Y = \E [(Y-E[Y])^2] =  \E[Y^2] - (\E[Y])^2 \\
& \E [(X-\mu_X)(Y - \mu_Y)] = \E [(X-\E [X])(Y - \E [Y])] = \E[XY] - \E[X]\E[Y] \\
\end{align}
$$
$$
\implies \rho_{XY} = \frac {\E[XY] - \E[X]\E[Y]} {\sqrt{\E[X^2] - (\E[X])^2} \sqrt {\E[Y^2] - (\E[Y])^2}}
$$
$$
\iff r_{xy} = \frac {\sum_{i=1}^n (x_i - \bar x)(y_i -\bar y)}{\sqrt{\sum_{i=1}^n (x_i - \bar x)^2} \sqrt{\sum_{i=1}^n (y_i - \bar y)^2}}
$$
Let $a_i = x_i - \bar x$ and $b_i = y_i - \bar y$ for $1 \leq i \leq n$, we have:
$$
r_{xy} = \cos \theta = \frac {\v a \cdot \v b}{\normvec a \normvec b}
$$
## 5.2 Spearman's rank correlation
- Compute the index of each value in the sorted sample.
$$
r_s = \frac {\cov {\text{R}[X]}{\text{R}[Y]}}{\sigma_X \sigma_Y}
$$
if ranks are distinct integers:
$$
r_s = 1- \frac {6 \sum (\text{R}[X_i] - \text{R}[Y_i])^2}{n(n^2 -1)}
$$
## 5.3 Pearson's chi-square test for categorical data.
Suppose $X$ has $r$ distinct values, $a_i$. $Y$ has $c$ distinct values, $b_i$.
### 5.3.1 Contingency table
$$
\begin{array}{|c|cccc|c|c|}
\hline
       & b_1 & b_2 & \cdots & b_c & \text{Total} \\
\hline
a_1    & n_{11} & n_{12} & \cdots & n_{1c} & n_1 \\
a_2    & n_{21} & n_{22} & \cdots & n_{2c} & n_2 \\
\vdots & \vdots & \vdots & \ddots & \vdots & \vdots \\
a_r    & n_{r1} & n_{r2} & \cdots & n_{rc} & n_r \\
\hline
\text{Total} & m_1 & m_2 & \cdots & m_c & n \\
\hline
\end{array}
$$
where:
- $n_{ij}$ is the observed frequency
- $n_i = \sum_{j=1}^c n_{ij}$ is the number of data tuples in $\mathcal D$ where $X = a_i$
- $m_j = \sum_{i=1}^r n_{ij}$ is the number of data tuples in $\mathcal D$ where $Y = b_j$
- $n = \sum_{i=1}^r n_i = \sum_{j=1}^c m_j = \sum_{i=1}^r \sum_{j=1}^c n_{ij}$  
### 5.3.2 Pearson's chi-square test statistic calculation
$$
\chi ^2 = \sum_{i=1}^r \sum_{j=1}^c \frac {(n_{ij} - e_{ij})^2}{e_{ij}}
$$
where $e_{ij}$ is the expected frequency of the joint event $(X_i, Y_j)$:
$$
e_{ij} = \frac {\text{count}(X=a_i) \text{count}(Y = b_j)}{n} = \frac {n_i m_j}{n}
$$
Actually, $e_{ij}$ is computed under the assumption that $X$ and $Y$ are independent. $P(X = a_i) = \frac {n_i} n$ and $P(Y = b_j) = \frac {m_j} n$:
$$
e_{ij} = n P(X_i, Y_j) = nP(X=a_i)P(Y = b_j) = n \frac {n_i} n \frac {m_j} n = \frac {n_i m_j}{n}
$$
### 5.3.3 Pearson's chi-square test hypotheses

^efb620

Null hypothesis: $H_o$ : $X$ and $Y$ are independent
Alternative hypothesis: $H_a$ there is a correlation between $X$ and $Y$
Degrees of freedom: $(r-1)\times(c-1)$.

If 
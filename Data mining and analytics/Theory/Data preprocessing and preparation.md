# 1. Data cleaning
## 1.1. Handling missing values
### 1.1.1. Ignore tuples with missing values
- When class label is missing
- Not very effective.
### 1.1.2. Fill in the missing values manually
- Not feasible given a large data
### 1.1.3. Use a global constant to fill in the missing values
- Not reliable
### 1.1.4. Use a [[Data Understanding#^b823e9|measure of central tendency]] for the attribute
- For normal (symmetric) data distribution, the mean can be used, while skewed data distribution should employ the median
### 1.1.5. Use the most probable value to fill in the missing values
- Determined with [[1. Machine Learning Exemplified#^6e9242|regression]], inference-based tools using a Bayesian formalism, or [[3. A Rule-Based Method - Decision Trees|decision tree]] induction.
- -> Popular strategy -> using the most information from the present data to predict missing values.
### 1.1.6. Missing values may not errors in data!!!
- Missing values may not imply an error in the data.
- Fields may be intentionally left blank.
## 1.2. Handling incorrect and inconsistent values
### 1.2.1. Inconsistency detection
- When data is collected from various sources in different formats.
- Duplicate detection and inconsistency detection
- These topics are studied under the general umbrella of data integration.
### 1.2.2. Domain knowledge
Domain knowledge is needed to detect incorrect entries.
### 1.2.3. Data-centric methods
- The statistical behavior of the data is used to detect outliers.
- This may not always be the anomalies because they may be the result of interesting behavior of the underlying system.
- Sometimes is dangerous -> removal of useful knowledge.
## 1.3. Handling noisy data
Noise is a random error or variance in a measured variable.
We an use [[Data Understanding#4.5 Five-number summary|five-number summary]] and [[Data Understanding#4.6 Boxplots|boxplots]] to identify noise or outliers
### 1.3.1. Binning

^9b7475

- The sorted values are put into a number of "buckets", or *bins*.
- Smoothing by bin [[Data Understanding#^43d071|means]]: replace by mean
- Smoothing by bin [[Data Understanding#^dd53f6|medians]]: replace by median
- Smoothing by bin boundaries: each bin value is replaced by the closest boundary value (min or max).
### 1.3.2. Regression

^66803f

- [[1. Linear regression|Linear regression]] involves finding the best line to fit 2 attributes so that one attribute can be used to predict the other.
- [[1. Linear regression|Multiple linear regression]] is an extension of linear regression.
### 1.3.3. Outlier analysis
- Using clustering. ^adc954
# 2. Data integration
- Merging data from multiple data sources
- -> Reduce and avoid redundancies and inconsistencies
- -> Improve the accuracy and speed of the subsequent data mining process
## 2.1. Entity identification problem
- Meta-data can be used for schema matching
- Include:
  - Name of the attribute
  - Meaning or description of the attribute
  - Data type and range of values
  - Null rules for handling blank, zero, or null value.
## 2.2. Redundancy and [[Data Understanding#^d70d66|correlation]] analysis
- Inconsistent attribute naming an also cause redundancies in the resulting data.
- Some redundancies can be detected by correlation analysis
- Correlation analysis can measure how strongly one attribute implies the other.
- [[Data Understanding#^efb620|Chi-square test of independence]] for categorical data
- [[Data Understanding#^fb038f|Pearson correlation]] for numeric data.
## 2.3 Tuple duplication
- Inconsistencies often arise between various duplicates
### 2.4 Data value conflict detection and resolution
# 3. Data transformation
## 3.1. Data conversion and discretization
- Numeric to categorical: discretization
- Categorical to numerical: binarization
- Text to numeric data
- Time-series to discrete sequence data
### 3.1.1 Discretization
- Divide the value range of a numeric attribute into k sub ranges -> Label them from $1$ to $k$.
- Lose some information for the mining process.
#### Discretization challenges and techniques
- Data may be non-uniformly distributed across the different intervals.
##### Equi-width sub-ranges
- Each sub-range $[a, b]$ is chosen in such a way that $b-a$ is the same for each sub-range.
- Will not work for data sets that are distributed non-uniformly across the different sub-ranges.
- $[\min, \max]$ divided into $k$ sub-ranges of equal length.
##### Equi-log sub-ranges
- $[a,b]$ is chosen in such a way that $\log(a) - \log(b)$ has the same value.
- Useful when the attribute shows an exponential distribution across a range.
##### Equi-depth sub-ranges

^594461

- Each sub-ranges has an equal number of records
- First sorting it, then select the division points.
##### Clustering-based
### 3.1.2. Binarization
### 3.1.3. Text to numeric data
- Vector space model (a.k.a bags of words)
- N-gram model
- Latent semantic and topics models: LSA, LDA,...
- Text embeddings: Word2Vec, GloVe, Doc2Vec, etc.
### 3.1.4. Time-series to discrete sequence data
Using *Symbolic aggregate approximation* (SAX):
- **Step 1**: Window-based averaging: The series is divided in to widows of length $w$, and the average time-series value over each window is computed.
- **Step 2**: Value-based discretization: the averaged time-series values are discretized into a smaller number of [[#^594461|equi-depth]] intervals.
## 3.2. Data smoothing
* **Smoothing**: remove noise from data: [[#^9b7475|binning]], [[#^66803f|regression]], and clustering.
## 3.3. Data aggregation
- **Aggregation**: where summary or aggregation operations are applied to the data -> data cube.
## 3.4. Construction of attributes
- New attributes are constructed and added to help the mining process -> improving the accuracy and understanding of structure in.
- Help us to explore, observe and understand the data more easily.
## 3.5. Data scaling and normalization.
- Help the attribute can be comparable to one another.
### 3.5.1. Min-max normalization
- $x_i' = \frac {x_i - \min_X}{\max_X -\min_X} (\max_X^\text{new} - \min_X^\text{new})+\min_X^\text{new}$ 
- Range $[0,1]$ -> **range normalization**. 
### 3.5.2 Standard score normalization
$$
x_i' = \frac {x_i - \mu}{ \sigma}
$$
- The new attribute now has mean $\mu = 0$ and standard deviation $\sigma = 1$.
- The vast majority of the normalization values will typically lie in the range $[-3, 3]$.
### 3.5.3 Decimal scaling
$$
x_i' = \frac {x_i}{10^j}
$$
that:
$$
j = \arg\max_j |x'_i| < 1
$$
# 4. Data reduction
- Dimensionality reduction
- Numerosity reduction
## 4.1 Principal component analysis (PCA)
- A method of dimensionality reduction.
- $\mathcal D = m \times n$
- PCA searches for $k$ $n-$dimensional orthogonal vectors that can best be used to represent the data where $j \leq k$. The original data are thus projected onto a much smaller space, resulting in dimensionality reduction.
- PCA "combines" the essence of attributes by creating an alternative, smaller set of variables. The initial data can then be projected onto the smaller set.
- PCA often reveals relationships that were not previously suspected and thereby allows interpretations that would not ordinarily result.
### Steps:
- Normalized the data.
- Compute $k$ orthonormal vectors that provide a basis for the normalized input data. -> Unit vectors -> The input data are linear combination of the principal components.
- Sort the principal components in order of decreasing "significance" or strength. -> First axis show the most variance among the data, the second shows the next highest variance and so on.
- We can eliminate the weaker components.
PCA can handle sparse data and skewed data. Principal components may be used as inputs to regression and cluster analysis.
## 4.2. Attribute subset selection.
- Many attribute may be irrelevant to the mining task or redundant.
- Attribute subsets selection reduces the data set by
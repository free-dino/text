# 1. Word meaning
Lemma: the word
Sense/Concept: the meaning of the word
A lemma can be polysemous
## Relation between senses
### Synonym
Words that have the same meaning in some or all contexts
#### Similarity
Words with similar meanings but only sharing some element of meaning
#### Related
Words can be related in anyway, perhaps via a semantic frame or field.
- Semantic field:
	- Words that cover a particular semantic domain
	- bear structured relation with each other.
### Antonym
​Senses that are opposites with respect to only one feature of meaning
### Connotation (sentiment):
Words have affective meaning.
They seems to vary along 3 affective dimensions:
- **Valence**: the pleasantness of the stimulus
- **Arousal**: the intensity of emotion provoked by the stimulus
- **Dominance**: the degree of control exerted by the stimulus
# 2. Vector semantics
## tf-idf
Sparse vector (most element is 0)
$$w_{t,d} = tf_{t,d} \times idf_t
$$
Term frequency: $tf_{t,d} = \text{count}(t,d)$ --> squashing it :  $tf_{t,d} = \log_{10}(\text{count}(t,d)+1)$ 
Document frequency $df_t$ is the number of documents $t$ occurs in
$idf_t$ is the inverse document frequency: $\log_{10}\frac{N}{df_t}$ with $N$ is the total number of documents ​in the collection
## Word2Vec
Dense vector
In practice Dense vector work better. 
### Skip Gram with negative sampling
Goal: training a classifier that is given a candidate (**w**ord, **c**ontext)
$$
\begin{align}
&\P(+ \mid w, c) \\
&\P(-\mid w, c) = 1-\P(+\mid w,c) 
\end{align}
$$
Remember: 2 vector are similar if they have high dot product
- Cosine is just a normalized dot product

So: 
$$
\text{Similarity}(w, c) \propto w \cdot c
$$
We'll need to normalize to get a probability.

We'll use the sigmoid function from [[2. Classification and Logistic Regression|logistic regression]] :
$$
\begin{align}
\P(+\mid w,c) &= \sigma(w\cdot c) = \frac {1}{1+\exp(-c \cdot w)} \\
\P(- \mid w, c) &= 1- \P(+\mid w,c) = \sigma(-w \cdot c) = \frac {1}{1+\exp(c \cdot w)}
\end{align}
$$
How to compute:
$$
\begin{align}
\P(+\mid w, c_{1:L}) &= \prod_{i=1}^L\sigma(w \cdot c_i) \\
\log \P(- \mid w, c_{1:L}) &= \sum_{i=1}^{L} \log\sigma(w\cdot c_i)
\end{align}
$$
-> Estimate the probability that $w$ occurs in the this window
Loss function:
$$

$$


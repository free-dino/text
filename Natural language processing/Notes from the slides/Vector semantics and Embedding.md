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
Goal: training a classifier that is given a candidate

> [!def] Graph
> $\mathcal G = (\mathcal V, \mathcal E)$ with $\mathcal V$ is the set of nodes (vertices) and $\mathcal E$ is the set of edges.

> [!def] Adjacency matrix
> $\mat A \in \R^{n \times n}$ with $n$ is the total number of nodes. The main diagonal is 0 

> [!def] Node attributes matrix
> $\mat X \in \R^{n \times c}$ with $c$ is the number of features for each node

> [!def] Effective node representation
> $\mat H \in \R^{n \times f}$ with $f$ is the dimension of node representation.
> $\mat H^k \in \R^{n \times f}, k \in \set{1, 2, \dots, K}$ is the nodes representation at the $k$-th layer

-> The goal of GNN is to learn effective node representations by combining graph structure information and the node attributes, which are further used for node classification.

# Supervised GNNs
## General Frameworks of GNNs


> [!idea] 
> Iteratively update the node representations by combining the representations of their neighbors and their own representations


2 important functions:
- **Aggregate**: Aggregating the information from the neighbors of each node.
- **Combine**: Update the node representations by combining the aggregated information from neighbors with the current node representations.

The mathematical framework:
- Init: $\mat H^{(0)} = \mat X$
- For $k=1, 2, \dots, K$ $$\begin{align} \v a^{(k)}_v &= \textbf{AGGREGATE} \set{\v h_u^{(k-1)} : u \in \mathcal N(v)} \tag{1} \\ \v h^{(k)}_v &= \textbf{COMBINE}^k \set{\v h_v^{(k-1)}, \v a_v^{(k)}} \tag{2} \end{align}$$ where $\mathcal N(v)$ is the set of neighbors for the $v$-th node. The node representation $\mat H^K$ in the last layer can be treated as the final node representations.
- For node classification, the label of node $v$ can be predicted through a [[2. Classification and Logistic Regression#^8ff797|softmax function]], i.e., $$\hat y_v = \text{soft}\max (\mat W \v h_v^\top) \tag{3}$$ where $\mat W \in \R^{|\mathscr L| \times F}$, $|\mathscr L|$ is the number of labels in the output space.
- The whole model can be trained by minimizing the loss function: $$O = \frac 1 {n_\ell} \sum_{i=1}^{n_\ell}L(\hat y_i, y_i) \tag{4}$$ where $y_i$ it the ground truth label of node $i$, $n_\ell$ is the number of labeled nodes, $L(\cdot, \cdot)$ is a [[1. Linear regression#^8cd857|loss function]] such as [[2. Classification and Logistic Regression#^9b59fb|cross-entropy loss function]]. 

## Graph Convolutional Networks
The node representation in each layer is updated according to the following propagation rule:
$$
\mat H^{(k+1)} = \sigma (\tilde {\mat D} ^ {- \frac 1 2} \tilde{\mat A} \tilde{\mat D}^{- \frac 1 2} \mat H^{(k)} \mat W^{(k)}) \tag 5
$$
### Why and How?
Every layer of GNN can be written as a non-linear function: $$\mat H^{(k+1)} = f(\mat H^{(k)}, \mat A) \tag{5.1}$$
A simple form of a layer-wise propagation rule: $$f(\mat H^{(k)}, \mat A) = \sigma (\mat A \mat H^{(k)} \mat W^{(k)}) \tag{5.2}$$ where $\mat W^{(k)} \in \R^{f \times f'}$ is a weight matrix for the $k$-th layer

The function $(5.2)$ satisfies the general framework: 
- Aggregating information from neighbors (through the multiplication of $\mat A$ and $\mat H$)
- Combining aggregated information with the current representation

There is 2 limitations of this simple model: 
- The multiplication with $\mat A$ means that, for every node, we sum up all the feature vectors of all neighboring nodes but not the node itself. 
- $\mat A$ is typically not normalized and therefore the multiplication with $\mat A$ will completely change the scale of the feature vectors

So the trick is to: 
- Enforcing self loops in the graph: we simply add the identity matrix to $\mat A$: $\tilde{\mat A} = \mat A + \mat I_n$.
- Normalizing $\mat A$ such that all rows sum to 1, i.e. $\mat D^{-1} \mat A$ where $\mat D$ is the diagonal node degree matrix. This correspond to taking the average of neighboring node features.

In practice, we use symmetric normalization, i.e. $\mat D^{- \frac 1 2} \mat A \mat D^{- \frac 1 2}$. Each entry now becomes: $$(\mat D^{-\frac 1 2} \mat A \mat D ^{- \frac 1 2})_{ij} = \frac{a_{ij}}{\sqrt{d_{i}d_{j}}} \tag {5.3}$$
-> Each edge contribution is scaled by both node $i$'s and node $j$'s degrees.

Combine those trick, we now have the equation (5). We can further dissect it to understand the **AGGREGATE** and **COMBINE** function defined in GCN

$$
\begin{align}
\v h_i^{(k)} &= \sigma \left ( \sum_{j \in \set{ \mathcal N(i) \cup i}} \frac{\tilde a_{ij}}{\sqrt{\tilde d_{i} \tilde d_{j}}} \v h_j^{(k-1)} \mat W^{(k)} \right) \tag {5.4} \\
\v h_i^{(k)} &= \sigma \left ( \sum_{j \in \mathcal N(i)} \frac{a_{ij}}{\sqrt{\tilde d_{i} \tilde d_{j}}} \v h_j^{(k-1)} \mat W^{(k)} + \frac{1}{\tilde {d}_i} \v h_i^{(k-1)} \mat W^{(k)}\right) \tag{5.5}
\end{align}
$$

The fuck with (5.5)? Because: 

$$
\begin{align}
\sum_{j \in \set{\mathcal N(i) \cup i}} \frac{\tilde a_{ij}}{\sqrt{\tilde d_{i} \tilde d_{j}}} \v h_j= \sum_{j \in \set{\mathcal N(i)}} \frac{a_{ij}}{\sqrt{\tilde d_{i} \tilde d_{j}}} \v h_j + \frac {\tilde a_{ii}}{\sqrt{\tilde d_{i} \tilde d_{i}}} \v h_i = \sum_{j \in \set{\mathcal N(i)}}\frac{a_{ij}}{\sqrt{\tilde d_{i} \tilde d_{j}}} \v h_j + \frac{1}{\tilde d_i} \v h_i
\end{align}
$$

## Graph attention network
### Graph attention layer

Input: $\mat H^{(k-1)} = [\v h_1^{(k-1)}, \v h_2^{(k-1)}, \dots, \v h_n^{(k-1)}], \v h^{(k-1)}_i \in \R^f$
Output: $\mat H^{(k)} = [\v h^{(k)}_1, \v h^{(k)}_2, \dots, \v h^{(k)}_n], \v h^{(k)}_i \in \R^{f'}$ 
Weight matrix: $\mat W \in \R^{f' \times f}$
Self attention on the nodes: $a : \R^{f'} \times \R^{f'} \to \R$ computes attention coefficients: 
$$
e_{ij} = a (\mat W \v h_i, \mat W \v h_j)
$$
that indicate the importance of node $j$'s features to node $i$
Masked attention:
$$
\a_{ij} = \text{soft} \max_{j \in \mathcal N(i)} (e_{ij})= \frac{\exp(e_{ij})}{\sum_{k \in \mathcal N(i) \exp(e_{ik})}}
$$
In the paper they treated attention mechanism $a$ as a single layer feed forward neural network, parameterized by a weight vector $\v a \in \R^{2f'}$. The $\sigma()$ here, in this step calculation is the LeakyReLU with slope $\alpha=0.2$, the $\Vert$ is the concatenation operation.
$$
\a_{ij} = \frac{\exp \left(\sigma \left(\v a ^ \top [\mat W \v h_i \Vert \mat W \v h_j] \right) \right)}{\sum_{k \in \mathcal N(i)} \exp(\sigma(\v a ^ \top [\mat W \v h_i \Vert \mat W \v h_j]))}
$$
Now, we can do this
$$
\v h_i' = \sigma \left( \sum_{j \in \mathcal N(i)} \a_{ij} \mat W \v h_j\right)
$$
Multi-headed attention
$$
\v h'_j=\mathop{\Big \Vert}\limits_{k=1}^K \sigma \left( \sum_{j \in \mathcal N(i)} \a_{ij}^{(k)} \mat W^{(k)}\v h_j\right) 
$$
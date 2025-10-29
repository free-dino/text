
> [!def] Graph
> $\mathcal G = (\mathcal V, \mathcal E)$ with $\mathcal V$ is the set of nodes (vertices) and $\mathcal E$ is the set of edges.

> [!def] Adjacency matrix
> $\mat A \in \R^{N \times N}$ with $N$ is the total number of nodes. The main diagonal is 0 

> [!def] Node attributes matrix
> $\mat X \in \R^{N \times C}$ with $C$ is the number of features for each node

> [!def] Effective node representation
> $\mat H \in \R^{N \times F}$ with $F$ is the dimension of node representation.
> $\mat H^k \in \R^{N \times F}, k \in \set{1, 2, \dots, K}$ is the nodes representation at the $k$-th layer

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
- For $k=1, 2, \dots, K$ $$\begin{align} \v a^{(k)}_v &= \textbf{AGGREGATE} \set{\mat H_u^{(k-1)} : u \in N(v)} \tag{1} \\ \mat H^{(k)}_v &= \textbf{COMBINE}^k \set{\mat H_v^{(k-1)}, \v a_v^{(k)}} \tag{2} \end{align}$$ where $N(v)$ is the set of neighbors for the $v$-th node. The node representation $\mat H^K$ in the last layer can be treated as the final node representations.
- For node classification, the label of node $v$ can be predicted through a [[2. Classification and Logistic Regression#^8ff797|softmax function]], i.e., $$\hat y_v = \text{soft}\max (\mat W \mat H_v^\top) \tag{3}$$ where $\mat W \in \R^{|\mathscr L| \times F}$, $|\mathscr L|$ is the number of labels in the output space.
- The whole model can be trained by minimizing the loss function: $$O = \frac 1 {n_\ell} \sum_{i=1}^{n_\ell}L(\hat y_i, y_i) \tag{4}$$ where $y_i$ it the ground truth label of node $i$, $n_\ell$ is the number of labeled nodes, $L(\cdot, \cdot)$ is a [[1. Linear regression#^8cd857|loss function]] such as [[2. Classification and Logistic Regression#^9b59fb|cross-entropy loss function]]. 

## Graph Convolutional Networks
The node representation in each layer is updated according to the following propagation rule:
$$
\mat H^{(k+1)} = \sigma (\tilde {\mat D} ^ {- \frac 1 2} \tilde{\mat A} \tilde{\mat D}^{- \frac 1 2} \mat H^{(k)} \mat W^{(k)}) \tag 5
$$
### Why?
Every layer of GNN can be written as a non-linear function: $$\mat H^{(k+1)} = f(\mat H^{(k)}, \mat A)$$
A simple form of a layer-wise propagation rule: $$f(\mat H^{(k)}, \mat A) = \sigma (\mat A \mat H^{(k)} \mat W^{(k)}) \tag{5.1}$$ where $\mat W^{(k)}$ is a weight matrix for the $k$-th layer

The function $(5.1)$ satisfies the general framework: 
- Aggregating information from neighbors (through the multiplication of $\mat A$)
- Combining aggregated information with the current 
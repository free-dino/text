# 1. Formal Definition of CFG
- A grammar $G$ is the quadruple $(T, N, S, R)$, where:
	- $T$: a finite set of terminal symbols or tokens
	- $N$: a finite set of nonterminal symbols $(T \cap N = \emptyset)$   
	- $S$: a unique start symbol $(S\in N)$
	- $R$: a finite set of rules or productions of the form $(A, \a)$
	- where:
		- $A$ is a nonterminal
		- $\a$ is a string of 0s or more terminals and nonterminals?
			- zero means $\a = \epsilon$ is possible
# 2. Backus-Naur Form (BNF)
- A notation for writing CFG
- Each production $(A, \a)$ is written as: $$A \to \a$$ where the arrow means "is defined to be", "can have the form of", "may be replaced with" or "derives"
- Can be abbreviate the left to the right: $$\begin{aligned} A &\to \a_1 \\A &\to \a_2 \\ & \ \ \vdots \\ A &\to \a_n \end{aligned} \implies \begin{aligned} A &\to \a_1 \\ &\ \mid \ \ \a_2 \\ &\ \ \vdots \\ &\  \mid \ \ \a_n\end{aligned}$$ where:
	- $\a_1, \dots, \a_n$ are the alternatives of $A$
	- the vertical bar $\mid$ reads "or else"
- Non-terminals: Capital letters like A, B, and S
- The start symbol: S
- Strings drawn from $(T \cup N)^*$: lower case Greek letters
- Strings of terminals: Lower case Roman letters

Ex:
"Bò vàng gặm cỏ non"
"Trâu ăn cỏ"

Grammar: 
S -> NP VP
NP -> N | N A
VP -> V NP
N -> "bò" | "trâu" | "cỏ"
A -> "vàng" | "non"
V -> "gặm" | "ăn"

# 3. Derivations; Sentential Forms; Sentences; Languages

A grammar derives sentences by
1. Begining with the start symbol
2. Repeatedly replacing a nonterminal by the right-hand side of a production with that nonterminal on the left-hand side, until there are no more nonterminals to replace
# 4. The Structure of Parse Trees
- The start symbol is always at the root of the tree
- Nonterminals are always interior nodes
- Terminals are always leaves in the tree
- The sentence being analysed is the leaves read from left to right
# 5. Constructing a Simple Vietnamese CFG:
- Noun phrase
	- \<pre-modifier>\<head nound>\<post-modifier>
		- \<pre-modifier>: \<position -2> \<position -1>
		- \<post-modifier>: noun, adjective phrase, verb phrase, number, pronoun (at the end), prepositional phrase, subordinate clause.
- Verb phrase
	- \<pre-modifier>\<verb>\<post-modifier>
		- \<pre-modifier>: adverb
		- \<post-modifier>: 
			- Complement:
				- Noun phrase
				- Verb phrase
				- Prepositional phrase
				- Noun phrase and prepositional phrase
				- Clause
				- ...
			- Adjunct
				- Adverbs
				- Adjective phrases
				- Temporal noun phrases
				- Prepositional phrases
				- Or subordinate clauses
- Sentence
	- \<subject>\<predicate>:
		- Subject:
			- Noun phrase
			- Verb phrase
			- Clause
		- Predicate:
			- Verb phrase
			- Adjective phrase
			- Noun phrase
- Adverbial

# 6. Ambiguous Grammars
- A grammar is ambiguous if it permits:
	- more than one parse tree for a sentence
# 7. Coping with Ambiguous Grammars
1. Rewrite the grammar to make it unambiguous
2. Use disambiguating rules to throw away undesirable parse trees, leaving only one tree for each sentence

Example:

S -> NP VP | NP AP
NP -> N | N PP | P
VP -> V NP | V NP PP | V AP | R V NP R
PP -> E NP
AP -> A R | A R AP

P -> chúng tôi
N -> hàng | thuyền | ông | ông già | căng-tin | trường | cửa
V -> chuyển | mở | đi
E -> xuống | của
A -> già | nhanh
R -> đi | quá | mới | lại

Chúng tôi (P) chuyển (V) hàng (N) xuống (E) thuyền (N):
![[Pasted image 20241220233453.png]]

Ông(N) già(A) đi (R) nhanh (A) quá (R)

![[Pasted image 20241220234045.png]]

Ông già (N) đi (V) nhanh (A) quá (R):
![[Pasted image 20241220234335.png]]

Căng tin (N) của (E) trường (N) mới (R) mở (V) cửa (N) lại (R)
![[Pasted image 20241220235837.png]]

# 8. Chomsky Normal Form
- A CFG is in Chomsky normal form when every rule is of the form   A -> B C and A -> a
	- a is terminal
	- A, B, C are variables
	- B and C are not the start variables
- Additionally we permit the rule S -> $\epsilon$ where $S$ is the start variable, for technical reasons

The first step:
add a new start variable S0 and the rule S0 -> S
remove the $\epsilon$ rule. Suppose we are removing the rule A -> $\epsilon$
We have to have an A on the right side.
- For each occurrence of A on the right hand side, adding a rule (from the same starting variable) which has the A removed.
- further if A is the only thing occurring on the right, we replace this A with $\epsilon$. Of course this latter fact will have created a new $\epsilon$ rule.
Repeat the above process over and over again until all $\epsilon$ rules have been remove.

convert CFG -> have no $\epsilon$, all rule are either of the form variables goes to terminal, or of the form variable goes to string variables and terminals with 2 or more symbol

A -> u1u2...un => A -> u1A1, A1 -> u2A2 ....
if both are variables -> fine
any of them are terminals -> add 2 new variable and a new rule to take care of these
if A -> u1B => A -> U1B and U -> u1


OK:

S -> ASB
A -> aAS | a | $\epsilon$
B -> SbS | A | bb

S0 -> S
S -> ASB
A -> aAS | a | $\epsilon$
B -> SbS | A | bb

S0 -> S
S -> ASB | SB
A -> aAS | a | aS
B -> SbS | A | bb | $\epsilon$

S0 -> S
S -> ASB | SB | AS
A -> aAS | a | aS
B -> SbS | A | bb

S0 -> AU1 | SB | AS
S -> AU2 | SB | AS
A -> V1U3 | a | V1S
B -> SU4 | V2V2 | V1U5 | a | V1S

| word                                 |
| ------------------------------------ |
| N -> People \| fish \| tanks \| rods |
| V -> people \| fish \| tanks         |
| P -> with                            |
| S -> people \| fish \| tanks         |
| VP -> people \| fish \| tanks        |
|                                      |


S -> NP VP
VP -> V NP
S -> V NP
VP -> V NP PP
S -> V NP PP
VP -> V PP
S -> V PP
NP -> NP NP
NP -> NP PP
PP -> P NP

NP -> people
NP -> fish
NP -> tanks
NP -> rods
V -> People
S -> People
VP -> People
V -> Fish
S -> Fish
VP -> Fish
V -> tanks
S -> tanks
VP -> tanks
P -> with
PP -> with

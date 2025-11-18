# DENSE WORD REPRESENTATION CHEATSHEET - LECTURE 19
CS-6001: Indexing and Retrieving Text and Graphs

==============================================================================
TABLE OF CONTENTS
==============================================================================
1. The Lexical Gap Problem
2. Pseudo-Relevance Feedback (PRF)
3. Word Clusters & Distributional Vectors
4. Progression of Text Representations
5. Graph-Based Formulation
6. Linear Transformations & SVD
7. Low Rank Approximation
8. Term-Document Matrix & LSI
9. Random Walks on Word-Doc Graphs
10. Using SVD in Search
11. Non-Negative Matrix Factorization (NMF)
12. PLSI (Probabilistic LSI)
13. Comparison: TF-IDF vs LSI vs PLSI
14. Summary & Key Takeaways
15. Formulas Quick Reference
16. Examples Walkthrough


==============================================================================
1. THE LEXICAL GAP PROBLEM
==============================================================================

Definition: Mismatch between query words and document words even when semantically related

Two Forms:
- Synonymy: Different words, same meaning
  Example: car, automobile, vehicle, sedan  
  
- Polysemy: Same word, different meanings
  Example: jaguar (animal) vs jaguar (car brand)

Real Example:
Query: "cat habitat"
Doc1: "...cat...panther..."        → matches "cat" ✓
Doc2: "...habitat...panther..."    → relevant but no "cat" ✗

Problem: Exact word matching fails to capture semantic similarity


==============================================================================
2. PSEUDO-RELEVANCE FEEDBACK (PRF)
==============================================================================

Core Idea: Use top results to expand query automatically

Algorithm:
Step 1: User submits query Q = "cat habitat"
Step 2: Retrieve top K documents (typically K=10)
Step 3: Assume these K documents are relevant (pseudo assumption)
Step 4: Extract M important terms from these K docs
        Example: "feline", "panther", "territory", "den"
Step 5: Expand original query
        Q' = Q ∪ extracted_terms
        Q' = "cat habitat feline panther territory den"
Step 6: Re-run search with expanded query Q'
Step 7: Merge and rank results

Weighting Strategy:
- Original query terms: weight = 1.0
- Extracted terms: weight = 0.5 (lower to avoid query drift)

Final scoring:
score(doc) = 1.0 × match(original_terms) + 0.5 × match(extracted_terms)

Advantages:
+ Automatic query expansion
+ No manual intervention needed
+ Improves recall (finds more relevant docs)

Disadvantages:
- Computationally expensive (multiple queries)
- Can cause query drift (if top docs wrong)
- Magic parameters (K, M, weights)
- How many iterations?

Variants:
- Rocchio Algorithm: Vector space model version
- Relevance Models: Probabilistic version
- RM3: Modern implementation in search engines


==============================================================================
3. WORD CLUSTERS & DISTRIBUTIONAL VECTORS
==============================================================================

Fundamental Principle:
"You shall know a word by the company it keeps" - J.R. Firth (1957)

Distributional Hypothesis:
Words appearing in similar contexts have similar meanings

Example: Learning "tezgüino" (corn-based alcoholic beverage)

Context Sentences:
- "A bottle of tezgüino is on the table"
- "Everybody likes tezgüino"
- "Tezgüino makes you drunk"
- "We make tezgüino out of corn"

Step 1: Extract Context Words
Collect all words within window (e.g., 5 words on each side):
{bottle, table, likes, drunk, make, corn}

Step 2: Build Distributional Vector
Create sparse vector (size = vocabulary size, e.g., 50,000 dimensions):

tezgüino = [0, 0, ..., 1(bottle), 0, 1(corn), 0, 1(drunk), ..., 1(likes), 0, ...]

Step 3: Count Co-occurrences
bottle: 1
...

Step 4: Optional TF-IDF Weighting
Raw count → TF-IDF score
- Common words (the, is, a) get low weights
- Distinctive words (drunk, corn) get high weights

Step 5: Normalize
Scale to unit length: v_norm = v / ||v||

Step 6: Compare Similar Words
...

Brown Clustering:
Developed by IBM researchers (1992)
Algorithm:
1. Start: Each word in its own cluster
2. Repeat: Merge two clusters that minimize information loss
3. Stop: When desired number of clusters reached
4. Result: Hierarchical binary tree of words

Cluster Examples:
Cluster 347: {car, automobile, sedan, vehicle, SUV, truck}
Cluster 891: {cat, feline, panther, tiger, lion, jaguar(animal)}
Cluster 234: {run, jog, sprint, dash, race}

Application in NLP:
...

Benefits:
...


==============================================================================
4. PROGRESSION OF TEXT REPRESENTATIONS
==============================================================================

Evolution Timeline:
Stage 1: Sparse Symbolic (1960s-1990s)
...
Stage 2: Distributional Vectors (1990s)
...

Key Transition:
SPARSE → DENSE
DISCRETE → CONTINUOUS
SYMBOLIC → GEOMETRIC
COUNT-BASED → LEARNED


==============================================================================
5. GRAPH-BASED FORMULATION
==============================================================================

PRF as Associative Retrieval

Word-Document Bipartite Graph:
...

Applications:
- Spectral clustering
- Graph partitioning
- Community detection
- Diffusion processes
- Heat equation on graphs


==============================================================================
6. LINEAR TRANSFORMATIONS & SVD
==============================================================================

Matrix as Geometric Transformation
...

Key Properties:
...

Computing SVD:
Method 1: Eigenvalue decomposition
...


==============================================================================
7. LOW RANK APPROXIMATION
==============================================================================

Signal vs Noise Concept
...

Choosing k:
Method 1: Fixed k (e.g., k=300)
...


==============================================================================
8. TERM-DOCUMENT MATRIX & LSI
==============================================================================

Term-Document Matrix:
...

Latent Semantic Indexing (LSI):
...


==============================================================================
9. RANDOM WALKS ON WORD-DOC GRAPHS
==============================================================================

Spreading Activation Model
...

Advantages of Random Walk:
...


==============================================================================
10. USING SVD IN SEARCH
==============================================================================

LSI Search Pipeline:
...

Why LSI Search Works:
Example Query: "automobile"
...


==============================================================================
11. NON-NEGATIVE MATRIX FACTORIZATION (NMF)
==============================================================================

Motivation:
...

Algorithms:
...


==============================================================================
12. PLSI (PROBABILISTIC LSI)
==============================================================================

Motivation:
...

Example (k=2 topics):
...


==============================================================================
13. COMPARISON: TF-IDF vs LSI vs PLSI
==============================================================================

Detailed Comparison Table:
...

When to Use Each:
Use TF-IDF when:
...


==============================================================================
14. SUMMARY & KEY TAKEAWAYS
==============================================================================

The Lexical Gap Problem:
...


==============================================================================
15. FORMULAS QUICK REFERENCE
==============================================================================

TF-IDF:
...


==============================================================================
16. EXAMPLES WALKTHROUGH
==============================================================================

Example 1: Computing Distributional Vector
...


==============================================================================
STUDY CHECKLIST
==============================================================================

Core Concepts:
...

Connections to Modern NLP:
...


==============================================================================
END OF CHEATSHEET
==============================================================================

Total concepts covered: 50+
Total formulas: 15+
Total examples: 4 detailed walkthroughs
Pages: 16 sections

Good luck with your exam! Review each section systematically.
For exam prep:
1. First pass: Read through once
2. Second pass: Work through examples by hand
3. Third pass: Test yourself on checklist
4. Fourth pass: Explain concepts out loud to someone

Remember: Understanding > Memorization
Focus on intuition, not just formulas.

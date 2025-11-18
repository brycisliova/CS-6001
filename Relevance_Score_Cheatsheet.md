# Relevance Score Cheatsheet

## Table of Contents
1. [Term Frequency (TF)](#term-frequency-tf)
2. [Inverse Document Frequency (IDF)](#inverse-document-frequency-idf)
3. [TF-IDF](#tf-idf)
4. [BM25](#bm25)
5. [Cosine Similarity](#cosine-similarity)
6. [Evaluation Metrics](#evaluation-metrics)
   - [Precision](#precision)
   - [Recall](#recall)
   - [Mean Average Precision (MAP)](#mean-average-precision-map)
   - [Normalized Discounted Cumulative Gain (NDCG)](#normalized-discounted-cumulative-gain-ndcg)
7. [Length Normalization](#length-normalization)
8. [Quick Reference Tables](#quick-reference-tables)

---

## Term Frequency (TF)
The term frequency measures how frequently a term occurs in a document. It is often expressed as:  
\[ TF(t, d) = \frac{f_{t, d}}{\sum_{t' \in d} f_{t', d}} \]  
Where:  
- \( f_{t, d} \) = frequency of term \( t \) in document \( d \)  

Example: If the term "data" appears 3 times in a document of 100 words,  
\[ TF(data, d) = \frac{3}{100} = 0.03 \]

---

## Inverse Document Frequency (IDF)
IDF measures the importance of a term across the corpus. It is defined as:  
\[ IDF(t) = \log \left( \frac{N}{n_t} \right) \]  
Where:  
- \( N \) = total number of documents  
- \( n_t \) = number of documents containing term \( t \)  

Example: If there are 1000 documents and "data" appears in 100 of them,  
\[ IDF(data) = \log \left( \frac{1000}{100} \right) = 1 \]

---

## TF-IDF
The TF-IDF score combines TF and IDF and is defined as:  
\[ TFIDF(t, d) = TF(t, d) \times IDF(t) \]  

Example: For the above TF and IDF calculations,  
\[ TFIDF(data, d) = 0.03 \times 1 = 0.03 \]

---

## BM25
The BM25 model is an extension of the TF-IDF model that incorporates document length normalization, defined as:  
\[ BM25(t, d) = IDF(t) \times \frac{f_{t, d}(k_1 + 1)}{f_{t, d} + k_1 \left( 1 - b + b \frac{|d|}{avg|d|} \right)} \]  
Where:  
- \( |d| \) = length of document (number of terms)  
- \( avg|d| \) = average document length  
- \( k_1 \) and \( b \) are parameters (common values: \( k_1 = 1.5 \), \( b = 0.75 \))  

---

## Cosine Similarity
Cosine similarity measures the cosine of the angle between two non-zero vectors. It is defined as:  
\[ CosineSimilarity(A, B) = \frac{A \cdot B}{||A|| ||B||} \]  
Where \( A \cdot B \) is the dot product, and \( ||A|| \) and \( ||B|| \) are the magnitudes of vectors A and B, respectively.  

---

## Evaluation Metrics
### Precision
Precision is the ratio of relevant documents retrieved to the total documents retrieved:  
\[ Precision = \frac{TP}{TP + FP} \]  
Where:  
- \( TP \) = True Positives  
- \( FP \) = False Positives

### Recall
Recall is the ratio of relevant documents retrieved to the total relevant documents:  
\[ Recall = \frac{TP}{TP + FN} \]  
Where:  
- \( FN \) = False Negatives  

### Mean Average Precision (MAP)
MAP is the mean of the average precision scores for a set of queries:  
\[ MAP = \frac{1}{Q} \sum_{q=1}^{Q} AP(q) \]  
Where:  
- \( Q \) = total number of queries  
- \( AP(q) \) = Average Precision for query \( q \)  

### Normalized Discounted Cumulative Gain (NDCG)
NDCG measures the usefulness of a set of ranked documents:  
\[ NDCG_k = \frac{DCG_k}{IDCG_k} \]  
Where:  
- \( DCG_k \) = Discounted Cumulative Gain at rank k  
- \( IDCG_k \) = Ideal DCG at rank k  

---

## Length Normalization
Length normalization adjusts scores based on document length. A normalized TF can be expressed as:  
\[ TF_{norm}(t, d) = \frac{TF(t, d)}{|d|} \]

---

## Quick Reference Tables
| Formula | Definition |
|---------|------------|
| TF(t, d) | Term Frequency |
| IDF(t) | Inverse Document Frequency |
| TFIDF(t, d) | TF-IDF Score |
| BM25(t, d) | BM25 Score |
| CosineSimilarity(A, B) | Cosine Similarity |
| Precision | TP / (TP + FP) |
| Recall | TP / (TP + FN) |
| MAP | Mean Average Precision |
| NDCG_k | Normalized DCG |

---

This cheatsheet provides a concise overview of relevance scoring formulas commonly used in information retrieval. For more detailed explanations and implementations, refer to each specific topic as needed.

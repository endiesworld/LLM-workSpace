# Building a Search Engine

## What is Search?

Search means finding information from (documents, records, files, answers) that match a query.
Example: You type "python tutorial" on Youtube or google, you expect to get contents teaching Python. This is search in action, transforming your query into a form the computer can understand, and retrieving the matching documents efficiently. 

## Key Terms in Search

**Query:** What the user searches for.
**Document:** A searchable item (e.g PDF, blog post, email, etc.)
**Corpus:** The full collection of documents. 
**Index:** A preprocessed structure allowing fast search over documents.
**Ranking:** Ordering search results by how relevant they are to the query. 
**Relevance:** How closely a result matches the user's intent.
**Recall:** % of relevant items found by the search. 
**Precision:** % of retrieved items that are actually relevant

## Two Main Search Technologies

### 1. KeyWord Search (Lexical Search)
How it works:
+ Indexes words and their positions in documents (using inverted indexes).
+ Matches based on exact term overlap.
+ Uses algorithms like BM25 (an improvement over TF-IDF) for ranking. 

**Pros:**
- Fast
- Well-understood
- Works well for exact matches

**Cons:**
- Fails on synonyms or paraphrasing eg. "Fast car" =/ "quick vehicle"

### 2. Vector Search (Semantic Search) 
How it works:
+ Converts text into vectors (lists of numbers)
+ Vectors capture **meaning**, not just matches.
+ Searches by finding vectors **Closest** to the query vector (e.g., cosine similarity)

**Pros:**
+ Captures synonyms and meaning
+ Works better on natural questions or paraphrased content
+ Ideal for Retrieval-Augmented Generation (RAG)

**Cons:**
+ Slower than keyword search (needs optimization with ANN/HNSW)
+ Requires embedding models and extra storage
+ Harder to debug

### When to Use Vector Search
Vector search shines when:
+ Your users ask natural language questions
+ Your content uses varied vocabulary
+ You need meaning-aware results
+ You’re building a RAG system, chat assistant, or document Q&A bot

### Combining Both: Hybrid Search
Many systems today use hybrid search, blending:
+ BM25 for keyword precision
+ Vector similarity for semantic recall
This gives the best of both worlds and often improves search quality.

# 🔍 Embeddings in GenAI and LLMs

Embeddings are vector representations of text (or other data) used to capture meaning, context, or structure. Below is a concise overview of key embedding techniques.

---

## 🧱 Classical Embeddings

### 1. CountVectorizer (Bag of Words)
- **What**: Represents text by word occurrence counts.
- **Use Case**: Simple text classification, clustering, topic modeling.
- **Limitation**: Ignores context; sparse and high-dimensional.

### 2. TF-IDF (Term Frequency–Inverse Document Frequency)
- **What**: Weighs terms by frequency in a document vs. across all documents.
- **Use Case**: Keyword extraction, information retrieval.
- **Limitation**: Still context-free; improves relevance over BoW.

### 3. BM25
- **What**: A ranking function based on TF-IDF, tuned for retrieval.
- **Use Case**: Search engines, document ranking (e.g., Elasticsearch).
- **Limitation**: Term-based; no deep semantic understanding.

---

## 🤖 Neural Embeddings

### 4. Word2Vec
- **What**: Learns word embeddings via context prediction.
- **Use Case**: Semantic similarity, synonym detection.
- **Limitation**: Same embedding for a word regardless of context.

### 5. GloVe (Global Vectors)
- **What**: Learns embeddings from word co-occurrence statistics.
- **Use Case**: Similar to Word2Vec, interpretable analogies.
- **Limitation**: Static; not context-sensitive.

### 6. FastText
- **What**: Enhances Word2Vec with subword (character n-gram) info.
- **Use Case**: Handling rare words and morphology-rich languages.
- **Advantage**: Generates embeddings for out-of-vocabulary words.

### 7. Doc2Vec
- **What**: Extends Word2Vec to learn document-level vectors.
- **Use Case**: Document classification, retrieval.
- **Limitation**: Training complexity; less popular today.

### 8. BERT (Bidirectional Encoder Representations from Transformers)
- **What**: Contextual embeddings from transformer models.
- **Use Case**: QA, text classification, RAG, semantic search.
- **Advantage**: Embeddings change based on word usage/context.

### 9. SBERT (Sentence-BERT)
- **What**: Modified BERT for sentence-level embeddings.
- **Use Case**: Semantic similarity, sentence clustering, retrieval.
- **Advantage**: Optimized for speed and comparison tasks.

### 10. Universal Sentence Encoder (USE)
- **What**: Google’s encoder for sentence-level embeddings.
- **Use Case**: Text similarity, classification, transfer learning.
- **Advantage**: Lightweight and versatile.

### 11. OpenAI Embeddings (e.g., `text-embedding-ada-002`)
- **What**: High-quality, general-purpose dense embeddings.
- **Use Case**: RAG, search, clustering, summarization.
- **Advantage**: Fast, scalable, API-ready.

### 12. CLIP (Contrastive Language-Image Pretraining)
- **What**: Embeds images and text into a shared vector space.
- **Use Case**: Multimodal tasks (e.g., image captioning, search).
- **Advantage**: Cross-modal alignment (text ↔ image).

---

## ⚖️ Summary of Differences

- **Classical methods** (CountVectorizer, TF-IDF, BM25):
  - Fast, sparse, interpretable
  - No semantic or contextual understanding

- **Neural methods** (BERT, Word2Vec, SBERT, etc.):
  - Dense, learned from data
  - Context-aware, semantic-rich
  - Suitable for GenAI, LLMs, and retrieval-based generation

---

## ✅ When to Use What

- Use **TF-IDF or BM25** for traditional keyword-based search or small ML tasks.
- Use **SBERT or OpenAI Ada** for semantic similarity and GenAI search.
- Use **CLIP** when handling both images and text.
- Use **FastText** for rare words or morphologically complex languages.

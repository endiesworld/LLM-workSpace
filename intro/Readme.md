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
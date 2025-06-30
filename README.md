# VectorDatabase


```markdown
# 📖 Arabic Semantic Search with ChromaDB & FAISS

This project builds a semantic search system for Arabic documents using dense vector embeddings. It integrates **Hugging Face Datasets**, **Sentence Transformers**, **ChromaDB**, and **FAISS** to enable efficient document retrieval based on semantic similarity to a given question.

---

## 📌 What This Project Does

This code implements a full workflow for Arabic text semantic search:

1. **Load the Arabic Q&A Dataset**
   - Loads the `sadeem-ai/arabic-qna` dataset from Hugging Face.
   - Filters the data to keep only records where an answer is present.

2. **Prepare Text and Metadata**
   - Extracts Arabic question texts.
   - Collects document metadata such as `source` and `title`.
   - Generates a unique string ID for each document.

3. **Generate Embeddings Using Sentence Transformers**
   - Loads the `distiluse-base-multilingual-cased-v2` model from `sentence-transformers`.
   - Converts each text document into a dense numerical vector that captures its semantic meaning.

4. **Store Embeddings in ChromaDB**
   - Creates a persistent Chroma vector database.
   - Stores all documents, their embeddings, metadata, and unique IDs in a Chroma collection.
   - Enables efficient vector-based similarity search using cosine similarity.

5. **Query ChromaDB**
   - Encodes a sample Arabic question into an embedding.
   - Queries the ChromaDB collection for the most semantically similar documents.
   - Retrieves the top N matching documents.

6. **Build a FAISS Index for Fast Similarity Search**
   - Normalizes document embeddings for cosine similarity.
   - Creates a FAISS index and adds the embeddings with their corresponding document IDs.
   - Enables fast approximate nearest neighbor search in vector space.

7. **Query the FAISS Index**
   - Encodes and normalizes a question.
   - Uses the FAISS index to retrieve top similar document IDs based on inner product similarity (which acts as cosine similarity after normalization).

8. **Save the FAISS Index and Metadata**
   - Saves the FAISS index and associated document data (text, IDs, metadata) to disk using `pickle`.
   - Allows the system to reload these files later without rebuilding the index.

9. **Load the Saved Index**
   - Demonstrates how to reload the saved FAISS index and metadata for immediate use.

---

## 📊 Summary of Components

| Step                       | Purpose                                              |
|:---------------------------|:-----------------------------------------------------|
| Load dataset               | Retrieve Arabic Q&A data from Hugging Face Datasets. |
| Filter dataset             | Keep only relevant entries (with answers).           |
| Text & metadata extraction | Prepare documents, metadata, and unique IDs.         |
| Generate embeddings        | Convert text to dense numerical vectors.             |
| ChromaDB storage           | Persist vectors and metadata for vector-based search.|
| ChromaDB query             | Retrieve top similar documents using cosine similarity.|
| Build FAISS index          | Enable fast nearest neighbor search using FAISS.     |
| FAISS query                | Retrieve top matches for a question from FAISS index.|
| Save/load FAISS index      | Persist and reload the index and metadata with pickle.|

---

## 📌 Why This Is Useful

- Provides a practical framework for **semantic search** on Arabic-language documents.
- Leverages modern tools like **ChromaDB** and **FAISS** for fast, efficient similarity search.
- Demonstrates multilingual embedding with **SentenceTransformers** for non-English text.
- Shows how to **persist search indexes** for reuse without reprocessing.
- Can be easily extended for other languages and document collections.



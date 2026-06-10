---
name: ai-rag-implementation
description: "Design and implement Retrieval-Augmented Generation (RAG) systems. Master document chunking, vector database indexing, hybrid retrieval, and RAG evaluation metrics."
---

# AI RAG Implementation Skill

Build intelligence-driven applications that use external knowledge bases to provide accurate, context-aware, and verifiable responses.

## When to Use

Use this skill when the user wants to:
- Connect an LLM to private or real-time data (PDFs, databases, websites).
- Reduce LLM hallucinations by providing grounded context.
- Implement semantic search capabilities.
- Build knowledge management systems or "Chat with your Docs" applications.
- Optimize retrieval accuracy using re-ranking and hybrid search.

## Core Pillars

### 1. Data Ingestion & Preprocessing
- **Document Parsing**: Extracting text from diverse formats (PDF, Docx, HTML, Markdown) while preserving structure.
- **Chunking Strategies**:
    - **Fixed-size Chunking**: Dividing text into equal parts (may break sentences/paragraphs).
    - **Semantic Chunking**: Splitting based on meaning and logical boundaries.
    - **Overlapping Chunks**: Maintaining context continuity between adjacent chunks.
- **Metadata Enrichment**: Attaching relevant tags (source, date, author) to chunks for advanced filtering.

### 2. Embedding & Indexing
- **Embedding Models**: Selecting appropriate models (OpenAI, Cohere, HuggingFace) for the use case.
- **Vector Databases**: Implementing storage and indexing using tools like Pinecone, Weaviate, Milvus, Chroma, or FAISS.
- **Dimensionality Management**: Handling vector dimensions and similarity metrics (Cosine Similarity, Euclidean Distance, Dot Product).

### 3. Retrieval Optimization
- **Semantic Search**: Finding content based on conceptual meaning rather than keyword matching.
- **Hybrid Search**: Combining semantic vector search with traditional keyword search (BM25) for maximum precision.
- **Re-ranking**: Using a second-pass cross-encoder model to re-order retrieved chunks by relevance.
- **Query Transformation**: Using the LLM to rewrite/expand user queries to better match the index (e.g., HyDE - Hypothetical Document Embeddings).

### 4. Generation & Context Augmentation
- **Context Injection**: Constructing the final prompt by combining the user query with the most relevant retrieved chunks.
- **Grounding**: Instructing the LLM to answer *only* based on the provided context to minimize hallucinations.
- **Citation/Source Attribution**: Ensuring the model provides references to the original source material.

### 5. RAG Evaluation (RAGAS Framework)
- **Faithfulness**: Does the answer match the retrieved context? (Checking for hallucinations).
- **Answer Relevance**: Is the answer actually answering the user's question?
- **Context Precision**: Are the retrieved chunks highly relevant to the question?
- **Context Recall**: Did the retrieval process find all the necessary information needed to answer?

## Best Practices

- **Prioritize Chunk Quality**: The "Garbage In, Garbage Out" principle applies heavily. Better chunking leads to much better retrieval.
- **Implement Hybrid Search**: Pure semantic search can miss specific names or acronyms; hybrid search solves this.
- **Use Metadata Filtering**: Don't just rely on similarity; use metadata to filter by date, category, or user ID for speed and accuracy.
- **Handle "No Context" Gracefully**: Explicitly instruct the LLM to say "I don't know" if the context doesn't contain the answer.
- **Monitor and Evaluate**: Use automated frameworks like RAGAS to continuously measure and improve your pipeline.
- **Optimize for Latency**: Vector search is fast, but long context windows and re-ranking add latency. Balance accuracy vs. speed.

## Deliverables

- Data ingestion and chunking pipelines.
- Vector database schemas and indexing configurations.
- RAG retrieval and generation logic.
- RAG evaluation reports and performance metrics.
- Documentation of the knowledge base and embedding strategy.

## Quality Checklist

- [ ] Document parsing preserves semantic meaning.
- [ ] Chunking strategy maintains sufficient context (via overlap or semantic splits).
- [ ] Hybrid search is implemented (if needed for keyword precision).
- [ ] Re-ranking is used for high-precision requirements.
- [ ] The prompt enforces grounding and prevents hallucinations.
- [ ] Source citations are provided for transparency.
- [ ] RAG metrics (Faithfulness, Relevance, etc.) are monitored.

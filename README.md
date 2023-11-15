# Retriever-Reader-Model
Retriever-Reader models, particularly the Contextualized Retrieval-Augmented Generation (RAG) approach, represent a breakthrough in Large Language Models (LLMs) such as GPT-3. These models integrate a dual-process system:

- **The Retriever**: This component is responsible for extracting pertinent documents or passages, such as from Wikipedia, to provide contextual grounding for the LLM's response generation. It's the cornerstone for sourcing external information that enhances the depth and accuracy of the responses.
  
- **The Reader**: Following retrieval, this component assimilates the gathered information to produce responses that are not only relevant but also informed by the additional context. This functionality is crucial in question-answering scenarios, particularly in educational settings where precision and reliability are key.

## 1. **The RAG Components**

### Search Engine Integration

- **Pyserini with Apache Lucene**: We employ Pyserini, a Python toolkit, for its seamless integration with Apache Lucene, a renowned Java-based search library. Lucene's advanced full-text indexing and search capabilities, combined with Pyserini's Python-friendly interface, form the backbone of our retrieval system.

### Ranking Criterion

- **BM25 Scoring**: Our system utilizes Lucene's BM25 scoring function for text retrieval. BM25 optimizes document ranking by considering term frequency and document length, providing a balanced approach to information retrieval. This method is crucial for selecting the most relevant passages to inform the LLM's responses.

## 2. **LLM Integration**

In this demonstration, we integrate a 70-billion-parameter Large Language Model using the Llama2 structure. This model choice is strategic for its advanced capabilities in understanding and generating human-like responses. To accommodate computational constraints, we employ a flexible sharding technique.

Note: Please check this [sample kernel](https://www.kaggle.com/code/junxhuang/retriever-reader-model-with-flexible-sharding). More codes are currently being refactored and will be uploaded soon.

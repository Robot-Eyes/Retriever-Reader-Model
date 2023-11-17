# Retriever-Reader-Model
Retriever-Reader models, particularly the Contextualized Retrieval-Augmented Generation (RAG) approach, represent a breakthrough in Large Language Models (LLMs) such as GPT-3. These models integrate a dual-process system:

- **The Retriever**: This component is responsible for extracting pertinent documents or passages from a knowledge corpus, such as Wikipedia, to provide contextual grounding for the LLM's response generation. It's the cornerstone for sourcing external information that enhances the depth and accuracy of the responses.
  
- **The Reader**: Following retrieval, this component assimilates the gathered information to produce responses that are not only relevant but also informed by the additional context. This functionality is crucial in question-answering scenarios, particularly in educational settings where precision and reliability are key.

## 1. **The RAG Components**

### Why we need a RAG model

If we fine-tune a LLM with a knowledge corpus, it will leverage its logical reasoning abilities to comprehend the corpus, thereby enhancing its accuracy in answering related questions. The why we need a RAG model? In my opinion, the incorporation of the RAG component presents distinct advantages over merely fine-tuning the LLM:

1. Adaptability to Dynamic Data: In scenarios where the knowledge corpus frequently updates, the RAG model efficiently accesses information from the latest version of the corpus.

2. Ensuring Accuracy and Credibility: The RAG model helps mitigate potential inaccuracies or "hallucinations" common in LLMs by providing references to the original text. This feature ensures a higher degree of reliability in the model's responses.

3. Cost-Effectiveness and Versatility: Training a RAG model is generally more economical compared to the extensive fine-tuning of an LLM. Furthermore, a single RAG model can effectively function as a foundational layer for multiple LLMs, optimizing resource utilization and reducing overall costs.


### How the RAG model works

There's a growing awareness among practitioners that relying exclusively on vector databases is inadequate. This realization has led to the development of several innovative solutions, covering a broad spectrum of functionalities:

* To combat issues of content fragmentation, intelligent paragraph segmentation has been introduced.
* To improve the unpredictable quality of vector generation, the Instructor tool dynamically tailors vectors for various QA scenarios.
* For those seeking more than implicit dynamic vectors, the HyDE (Hypothetical Documents for Entity) framework steps in as an intermediary layer. It initially creates virtual or hypothetical documents to enhance recall rates.
* When vector-based recall proves insufficient, a hybrid approach combining traditional BM25 and vector HNSW (Hierarchical Navigable Small World) is used, integrating multiple recall methods.
* To mitigate the problem of excessive recall hampering answer generation, strategies include examining the 'Lost in the Middle' phenomenon, employing various tricks, or utilizing LLMLingua for effective compression.
* To simplify recall, consider expanding to a 100k window and fully integrating it into a large-scale model, as exemplified by LongLoRA.
* Finally, for those improvements mentioned, if manual effort seems daunting, the Self-RAG model offers automation of each step, streamlining the process.

#### Search Engine Integration

- **Pyserini with Apache Lucene**: We employ Pyserini, a Python toolkit, for its seamless integration with Apache Lucene, a renowned Java-based search library. Lucene's advanced full-text indexing and search capabilities, combined with Pyserini's Python-friendly interface, form the backbone of our retrieval system.

#### Ranking Criterion

- **BM25 Scoring**: Our system utilizes Lucene's BM25 scoring function for text retrieval. BM25 optimizes document ranking by considering term frequency and document length, providing a balanced approach to information retrieval. This method is crucial for selecting the most relevant passages to inform the LLM's responses.

- 

## 2. **LLM Integration**

In this demonstration, we integrate a 70-billion-parameter Large Language Model using the Llama2 structure. This model choice is strategic for its advanced capabilities in understanding and generating human-like responses. To accommodate computational constraints, we employ a flexible sharding technique.

Note: Please check this [sample kernel](https://www.kaggle.com/code/junxhuang/retriever-reader-model-with-flexible-sharding). More codes are currently being refactored and will be uploaded soon.

PDF Question Answering Bot using RAG, FAISS, and Sentence Transformers
Project Overview

This project implements a PDF Question Answering (QA) Bot using a Retrieval-Augmented Generation (RAG) pipeline. The system allows users to upload a PDF document and ask questions about its content. Instead of relying only on a language model's internal knowledge, the bot retrieves relevant information directly from the PDF and uses it to generate accurate answers.

Features
Extract text from PDF documents
Split large documents into smaller chunks
Generate semantic embeddings using Sentence Transformers
Store embeddings in a FAISS vector database
Retrieve the most relevant chunks for a user query
Answer questions based on retrieved document content
Interactive user interface built with Gradio
Technologies Used
Python
PyPDF2 – PDF text extraction
Sentence Transformers (all-MiniLM-L6-v2) – Text embeddings
FAISS – Vector similarity search
NumPy – Numerical operations
Gradio – User interface
Project Workflow
1. PDF Loading

The PDF document is loaded and text is extracted from each page using PyPDF2.

2. Text Chunking

The extracted text is divided into smaller overlapping chunks.

Chunk Size: 500 characters
Overlap: 50 characters

Chunking helps preserve context and improves retrieval accuracy.

3. Embedding Generation

Each chunk is converted into a numerical vector (embedding) using the Sentence Transformer model:

all-MiniLM-L6-v2

These embeddings capture the semantic meaning of the text.

4. FAISS Index Creation

The embeddings are stored inside a FAISS vector index.

FAISS enables efficient similarity search among document chunks.

5. Information Retrieval

When a user enters a question:

The question is converted into an embedding.
FAISS searches for the most similar document chunks.
The top relevant chunks are retrieved.
6. Question Answering (RAG)

The retrieved chunks are used as context for answer generation.

This follows the Retrieval-Augmented Generation (RAG) approach:

User Query
      ↓
Retrieve Relevant Chunks
      ↓
Provide Context to Model
      ↓
Generate Answer

RAG improves answer quality by grounding responses in the document content.

7. User Interface

A Gradio interface allows users to:

Upload a PDF
Enter a question
Receive an answer based on the document
Example Query
What this paper is talking about?
Example Answer
This paper studies Heat-Bath Random Walks on lattice points using Markov bases. It investigates graph diameters, mixing behavior, eigenvalue bounds, and conditions for rapid mixing of heat-bath random walks.
Challenges Faced
PDF Text Extraction

Some PDF files may contain formatting issues that affect text extraction.

Chunk Size Selection

Choosing an appropriate chunk size and overlap was important to balance context preservation and retrieval accuracy.

Understanding Embeddings

Embeddings represent semantic meaning as numerical vectors, which required understanding vector-based similarity search.

FAISS Integration

FAISS requires embeddings to have the correct data type (float32) and dimensions.

RAG Pipeline Understanding

Learning how retrieval and generation work together was one of the key conceptual challenges.

Future Improvements
Integrate advanced LLMs such as Gemini or OpenAI models
Support multiple PDF documents
Add citation and source highlighting
Improve chunking using LangChain text splitters
Implement conversational memory
Conclusion

This project demonstrates how RAG, embeddings, and vector databases can be combined to build an efficient document question-answering system. By retrieving relevant information before generating answers, the bot produces more accurate and context-aware responses compared to traditional approaches.

# LangChain Structure-Based Text Splitter

[![Python](https://img.shields.io/badge/Python-3.9%2B-blue)](https://www.python.org/)
[![LangChain](https://img.shields.io/badge/Framework-LangChain-green)](https://www.langchain.com/)
[![Text Splitting](https://img.shields.io/badge/Focus-Text%20Splitting-orange)](https://python.langchain.com/docs/concepts/text_splitters/)

A beginner-friendly implementation of structure-aware text splitting using LangChain's `RecursiveCharacterTextSplitter`. This project demonstrates how to divide long text into smaller, manageable chunks while attempting to preserve natural text boundaries.

---

## Project Overview

Text splitting is an important preprocessing step in Generative AI applications, especially in **Retrieval-Augmented Generation (RAG)** systems.

Large documents often exceed the context limits of language models. Before sending document content to an LLM or storing it in a vector database, we typically divide it into smaller chunks.

However, splitting text at arbitrary positions can break sentences and separate related information.

This project demonstrates how LangChain's `RecursiveCharacterTextSplitter` addresses this problem by attempting to split text using progressively smaller separators, preserving larger structural boundaries whenever possible.

## Key Concepts Implemented

### 1. RecursiveCharacterTextSplitter

The project uses LangChain's `RecursiveCharacterTextSplitter` to divide a sample text into smaller chunks.

It attempts to split text using a hierarchy of separators, generally prioritizing:

- Paragraph boundaries (`\n\n`)
- Line boundaries (`\n`)
- Spaces (` `)
- Individual characters as a last resort

This approach helps keep related content together instead of immediately splitting text at arbitrary character positions.

### 2. Chunk Size

The `chunk_size` parameter controls the target maximum size of each text chunk.

In this implementation:

```python
chunk_size=500
```

This sets the target chunk size to 500 characters.

### 3. Chunk Overlap

The `chunk_overlap` parameter determines how many characters are shared between consecutive chunks.

In this implementation:

```python
chunk_overlap=0
```

No overlap is intentionally added between consecutive chunks.

Overlap can be useful in RAG applications because it helps retain context near chunk boundaries.

### 4. Splitting and Inspecting Results

The `split_text()` method performs the actual splitting operation.

```python
chunks = splitter.split_text(text)

print(len(chunks))
print(chunks)
```

The implementation displays:
- The total number of generated chunks.
- The resulting text chunks.

---

## Project Workflow

```text
Input Text
    |
    v
RecursiveCharacterTextSplitter
    |
    v
Configure Chunk Size and Overlap
    |
    v
Split Text into Smaller Chunks
    |
    v
Display Number of Chunks
    |
    v
Inspect Generated Text Chunks
```

---

## Tech Stack

- **Language:** Python 3.9+
- **Framework:** LangChain
- **Library:** `langchain-text-splitters`

---

## Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/mani787060/structure-based-text-splitter.git
```

### 2. Navigate to the Project Directory

```bash
cd structure-based-text-splitter
```

### 3. Install Dependencies

```bash
pip install -U langchain-text-splitters
```

### 4. Run the Python File

```bash
python text_structure_based.py
```

The program will split the sample text and print the total number of chunks along with their contents.

---

## Why Text Splitting Matters in RAG

A typical RAG pipeline involves retrieving relevant information from a collection of documents and providing that information to an LLM.

Text splitting helps make this possible by:

- Breaking large documents into manageable pieces.
- Preparing content for embedding generation.
- Supporting efficient retrieval from vector databases.
- Helping preserve relevant context during retrieval.

The quality of document chunking can influence the relevance and usefulness of retrieved information.

---

## Learning Outcomes

By exploring this implementation, you will understand:

- Why text splitting is necessary in Generative AI applications.
- How `RecursiveCharacterTextSplitter` works.
- The role of chunk size and chunk overlap.
- How to split text using LangChain.
- Why preserving text structure matters in RAG preprocessing.

---

## Future Improvements

Possible extensions to this project include:

- Implementing `MarkdownHeaderTextSplitter` for Markdown documents.
- Exploring metadata preservation during document splitting.
- Comparing different chunk sizes and overlap configurations.
- Using `Document` objects instead of plain text.
- Integrating the generated chunks into a complete RAG pipeline.

---

## Repository

GitHub: https://github.com/mani787060/structure-based-text-splitter

**Note:** This repository currently demonstrates recursive character-based splitting. The additional techniques listed under Future Improvements are potential extensions, not existing implementations.

# LangChain Structure-Based Text Splitter
[![LangChain](https://img.shields.io/badge/Framework-LangChain-green)](https://www.langchain.com/)
[![Python](https://img.shields.io/badge/Python-3.9%2B-blue)](https://www.python.org/)
[![Semantic Chunking](https://img.shields.io/badge/Pipeline-Semantic%20Chunking-orange)](https://python.langchain.com/docs/modules/data_connection/document_transformers/)

## 🏗️ Project Overview
This repository tackles one of the most critical challenges in Retrieval-Augmented Generation (RAG): **Semantic Preservation**. Hard length limits often destroy context by cutting documents mid-sentence or mid-code block. This project demonstrates how to use LangChain's structure-aware splitters to intelligently chunk text based on its natural hierarchy (paragraphs, sentences, and Markdown headers), ensuring the LLM receives complete, coherent thoughts.

---

## 🛠️ Key Technical Implementations

### 1. Recursive Structural Splitting
* **`RecursiveCharacterTextSplitter`:** The enterprise standard for text chunking. It attempts to split on large structural boundaries first (like double newlines `\n\n` for paragraphs), only moving to smaller boundaries (like single newlines `\n` or spaces) if a specific paragraph exceeds the maximum chunk size. This keeps related concepts bundled together.

### 2. Hierarchy-Aware Chunking
* **`MarkdownHeaderTextSplitter`:** Scraping websites or reading documentation often yields Markdown text. This implementation splits the document purely based on its structure (e.g., `# Header 1` or `## Header 2`). It ensures that an entire section of a document stays together in the vector space.

### 3. Structural Metadata Injection
* **Contextual Tagging:** When splitting by headers, the splitter automatically adds the header names to the `metadata` dictionary of the resulting `Document` object. For example, a chunk will contain `{"Header 1": "Installation Guide"}`. This is crucial for enabling Hybrid Search (combining semantic search with hard metadata filtering) in downstream vector databases.

---

## 💻 Tech Stack
* **Language:** Python 3.9+
* **Framework:** LangChain Text Splitters (`langchain-text-splitters`)
* **Environment:** `python-dotenv`

---

## 🚀 Getting Started

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/your-username/langchain-structure-based-text-splitter.git](https://github.com/your-username/langchain-structure-based-text-splitter.git)

2. **Install Dependencies:**
   ```bash
   pip install -U langchain langchain-text-splitters python-dotenv

3. **Run the Implementation:**
   ```bash 
   python text_structure_based.py

   

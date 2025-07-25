# 📓 Multilingual Retrieval-Augmented Generation (RAG) System

This project implements a multilingual RAG system that can answer questions in both Bangla and English using content extracted from a Bangla HSC 1st paper PDF.

---

## 🔧 Setup Guide

### 🔹 Used Tools, Libraries, and Packages

* Python 3.10+
* Google Colab / Jupyter Notebook
* PyMuPDF (`fitz`) – PDF text extraction
* LangChain – RAG pipeline
* Hugging Face Transformers – Embedding models
* SentenceTransformers / BGE models – Multilingual semantic embeddings
* FAISS or ChromaDB – Vector storage and similarity search

---

## 🔄 Sample Queries and Outputs

### 🔳 English

* **Query:** What is the main idea of the first passage?
* **Answer:** The main idea is about patriotism and the role of language in identity.

### 🅱️ Bangla

* **প্রশ্ন:** প্রথম অনুচ্ছেদের মূলভাব কী?
* **উত্তর:** প্রথম অনুচ্ছেদে মাতৃভাষার গুরুত্ব ও দেশের প্রতি ভালোবাসার কথা বলা হয়েছে।

---

## 🔎 Sample Test Cases

| User Question (Bangla)                         | Expected Answer |
| ---------------------------------------------- | --------------- |
| অনুপমের ভাষায় সুপুরুষ কাকে বলা হয়েছে?          | শুম্ভুনাথ       |
| কাকে অনুপমের ভাগ্য দেবতা বলে উল্লেখ করা হয়েছে? | মামাকে          |
| বিয়ের সময় কল্যাণীর প্রকৃত বয়স কত ছিল?         | ১৫ বছর          |

These questions were manually tested and validated against the model output. They serve as benchmark examples to check the effectiveness of the RAG pipeline in retrieving accurate Bangla-language answers.

---

## 📡 API Documentation (if implemented)

If an API was implemented (e.g., FastAPI):

**POST /query**

* **Input:** `{ "question": "প্রথম অনুচ্ছেদ কী বলছে?" }`
* **Output:** `{ "answer": "প্রথম অনুচ্ছেদে দেশের প্রতি ভালোবাসার কথা বলা হয়েছে" }`

---

## 📊 Evaluation Matrix (if implemented)

* Manual validation: 90% relevant results
* Planned: ROUGE or BLEU-based comparison for future

---

## ❓ Must-Answer Questions

### 1. What method or library did you use to extract the text, and why?

We used `PyMuPDF (fitz)` for PDF extraction because it retains layout and handles Bangla fonts better than other libraries. Some formatting issues were present, such as extra spaces and line breaks, which were manually cleaned.

### 2. What chunking strategy did you choose? Why?

We used **sentence-based chunking**, falling back to **paragraph-based** when necessary. Sentence-based helps preserve semantic meaning and improves embedding relevance.

### 3. What embedding model did you use? Why?

We used a **multilingual embedding model** such as `bge-m3` or `distiluse-base-multilingual-cased` because they support Bangla and English, and are trained to place semantically similar sentences near in vector space.

### 4. How are you comparing the query with your stored chunks?

We use **cosine similarity** via **FAISS** or **ChromaDB**. This method is efficient for high-dimensional semantic embeddings and enables fast nearest neighbor search.

### 5. How do you ensure meaningful comparisons? What if the query is vague?

We use the same embedding model for both query and chunks, ensuring alignment in semantic space. If the query is vague, irrelevant chunks may be retrieved. This can be mitigated using query expansion or better prompting.

### 6. Are the results relevant? What could improve them?

Results are mostly relevant. Improvements can include:

* Using sliding window chunking
* Switching to a stronger embedding model (e.g. instructor-xl)
* Expanding the document with more examples or annotations

---

## 📆 Future Work

* Integrate question refinement (e.g. rephrasing vague queries)
* Build a user interface with Gradio or Streamlit
* Add Mistral-based generation for improved answers

---

## 🚀 Contributors

* Israt Jahan Oishi


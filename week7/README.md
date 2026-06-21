# Robotics Document Question Answering System (RAG)

## Overview

This project implements a complete Retrieval-Augmented Generation (RAG) pipeline for answering robotics-related questions using a custom knowledge base built from Wikipedia articles.

The system combines semantic retrieval, vector search, re-ranking, and large language model generation to provide context-aware answers grounded in retrieved documents.

---

## Project Objectives

* Build a robotics-focused knowledge base.
* Implement semantic document retrieval using vector embeddings.
* Improve retrieval quality through re-ranking.
* Generate answers using retrieved context.
* Evaluate system performance using multiple NLP metrics.
* Analyze the impact of chunking strategies on retrieval and generation quality.

---

## Dataset

The knowledge base was created using Wikipedia articles covering topics such as:

* Robotics
* Robot Operating System (ROS)
* Simultaneous Localization and Mapping (SLAM)
* Localization
* Path Planning
* Motion Planning
* Sensor Fusion
* LiDAR
* Computer Vision
* Monte Carlo Localization
* Reinforcement Learning
* Mobile Robots
* Autonomous Robots
* Humanoid Robots

### Corpus Statistics

* Documents: 20
* Total Words: ~82,000
* Chunked Documents: 680+ chunks (baseline configuration)

---

## System Architecture

```text
User Question
       │
       ▼
Query Embedding
       │
       ▼
FAISS Retrieval
(Top-K Chunks)
       │
       ▼
Cross-Encoder Re-ranking
       │
       ▼
Relevant Context
       │
       ▼
FLAN-T5 Generator
       │
       ▼
Final Answer
```

---

## Technologies Used

### Retrieval

* Sentence Transformers
* all-MiniLM-L6-v2
* FAISS

### Re-ranking

* cross-encoder/ms-marco-MiniLM-L-6-v2

### Generation

* Google FLAN-T5 Base

### Evaluation

* ROUGE
* BLEU
* BERTScore

### Data Processing

* Pandas
* NumPy
* Wikipedia API

---

## Project Workflow

### 1. Data Collection

* Retrieved robotics-related articles from Wikipedia.
* Stored article titles and content in a structured corpus.

### 2. Data Preprocessing

* Cleaned and standardized text.
* Removed formatting artifacts.
* Generated corpus statistics.

### 3. Chunking

Documents were split into overlapping chunks using Recursive Character Text Splitting.

Experiments were performed with:

* Chunk Size 300
* Chunk Size 500
* Chunk Size 800

### 4. Embedding Generation

Generated dense vector representations using:

```text
sentence-transformers/all-MiniLM-L6-v2
```

Embedding Dimension:

```text
384
```

### 5. Vector Database

Created a FAISS vector index for efficient similarity search.

### 6. Retrieval

Retrieved the most relevant document chunks for each user query.

### 7. Re-ranking

Applied a Cross-Encoder model to improve retrieval quality and context relevance.

### 8. Generation

Generated final answers using:

```text
google/flan-t5-base
```

while constraining responses to retrieved context.

### 9. Evaluation

Evaluated generated answers against manually created ground-truth responses.

---

## Evaluation Results

| Metric       | Score |
| ------------ | ----- |
| ROUGE-1      | 0.380 |
| ROUGE-2      | 0.255 |
| ROUGE-L      | 0.342 |
| BLEU         | 0.175 |
| BERTScore F1 | 0.885 |

---

## Chunk Size Experiment

| Chunk Size | Number of Chunks | BERTScore F1 |
| ---------- | ---------------- | ------------ |
| 300        | 2566             | 0.822        |
| 500        | 1390             | 0.826        |
| 800        | 799              | 0.829        |

### Observation

Larger chunk sizes preserved more contextual information and achieved slightly higher semantic similarity scores.

---

## Example Questions

* What is SLAM?
* What is ROS?
* How does LiDAR work?
* What is Sensor Fusion?
* What is Monte Carlo Localization?
* Why is SLAM important in robotics?
* How do autonomous robots avoid obstacles?

---

## Key Learnings

### Chunking

Chunk size significantly affects retrieval quality and downstream answer generation.

### Embeddings

Semantic embeddings allow retrieval based on meaning rather than exact keyword matches.

### Retrieval

FAISS enables efficient similarity search even with large document collections.

### Re-ranking

Cross-Encoder re-ranking improves retrieval precision by better matching query-document relevance.

### Generation

Prompt design and context quality strongly influence final answer quality.

### Evaluation

BERTScore provides a better measure of semantic correctness than purely lexical metrics such as BLEU and ROUGE.

## Prerequisites & Installation

### Clone the Repository

```bash
git clone https://github.com/meharbhanwra/celebal-excellence-internship-program-2026-mehar-bhanwra.git
cd celebal-excellence-internship-program-2026-mehar-bhanwra/week-7
```
```bash
pip install torch pandas numpy faiss-cpu \
sentence-transformers transformers \
langchain langchain-community \
datasets evaluate bert-score rouge-score \
wikipedia-api rank-bm25 matplotlib
```
```bash
jupyter notebook week7_Mehar_Bhanwra.ipynb
```

## Author

Mehar Bhanwra

B.Tech Computer Science & Engineering

Retrieval-Augmented Generation (RAG) Project - Robotics Domain

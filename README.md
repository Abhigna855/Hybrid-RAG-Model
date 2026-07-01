<div align="center">

# 🧠 Hybrid Retrieval-Augmented Generation (Hybrid RAG)
### Biomedical Question Answering with Dense Retrieval, BM25, and FLAN-T5 on PubMedQA

![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)
![Transformers](https://img.shields.io/badge/HuggingFace-Transformers-yellow)
![FAISS](https://img.shields.io/badge/FAISS-Vector_Search-green)
![BM25](https://img.shields.io/badge/BM25-Sparse_Retrieval-orange)
![SentenceTransformers](https://img.shields.io/badge/SentenceTransformers-Embeddings-red)
![License](https://img.shields.io/badge/License-Academic-lightgrey)

A hybrid Retrieval-Augmented Generation (RAG) framework for **biomedical question answering** that combines dense retrieval, sparse retrieval, and large language models to improve answer relevance, factual grounding, and generation quality.

</div>

---

## Overview

Large language models can produce fluent but inaccurate answers, especially in specialised domains such as healthcare. This project addresses that challenge by combining semantic retrieval with lexical retrieval before passing the most relevant evidence to a language model for answer generation.

The system was developed as part of an MSc dissertation and evaluated on the **PubMedQA** dataset. It compares three approaches:

- Baseline language model.
- Dense RAG using FAISS and sentence embeddings.
- Proposed Hybrid RAG using FAISS, BM25, and Reciprocal Rank Fusion.

---

## Project Highlights

- Hybrid dense + sparse retrieval pipeline.
- FAISS-based semantic search.
- BM25 keyword retrieval.
- Reciprocal Rank Fusion for result combination.
- FLAN-T5 Base for answer generation.
- Biomedical QA on PubMedQA.
- Retrieval, generation, accuracy, and latency evaluation.
- Side-by-side comparison of baseline, dense RAG, and hybrid RAG.

---

## Dataset

The project uses the **PubMedQA** dataset from Hugging Face. Each example contains:

- A biomedical question.
- Supporting scientific context.
- A long answer.
- A final decision: Yes, No, or Maybe.

Preprocessing includes:

- Context parsing.
- Text cleaning.
- Context aggregation.
- Tokenisation.
- Embedding generation.

---

## Hybrid Pipeline

```text
User Query
   │
   ▼
Text Cleaning
   │
   ▼
Sentence Transformer
(all-MiniLM-L6-v2)
   │
   ├───────────────┐
   ▼               ▼
Dense Retrieval    Sparse Retrieval
(FAISS)            (BM25)
   │               │
   └───────┬───────┘
           ▼
Reciprocal Rank Fusion
           │
           ▼
Top-K Evidence
           │
           ▼
FLAN-T5 Base
           │
           ▼
Generated Answer
           │
           ▼
Yes / No / Maybe
```

---

## Tech Stack

| Category | Technology |
|----------|------------|
| Language | Python |
| Dataset | Hugging Face PubMedQA |
| Embeddings | all-MiniLM-L6-v2 |
| Dense Retrieval | FAISS |
| Sparse Retrieval | BM25 |
| Fusion | Reciprocal Rank Fusion |
| Generator | FLAN-T5 Base |
| Visualisation | Matplotlib, Seaborn |
| ML / NLP | Scikit-learn, NLTK |
| Evaluation | BLEU, ROUGE, Exact Match, F1 |

---

## Results Visualisations

The repository includes the following result figures:

### 1. Performance Comparison

This figure compares the overall performance of the baseline, dense RAG, and hybrid RAG systems.

![Performance Comparison](images/performance_comparison.png)

### 2. Accuracy Comparison

This figure shows how accuracy changes across the compared systems.

![Accuracy Comparison](https://github.com/Abhigna855/Hybrid-RAG-Model/blob/main/05a413b6-4e22-4731-954c-d40d23ca8808.png?raw=true)

### 3. Latency Comparison

This figure compares the query response time of each approach.

![Latency Comparison](https://github.com/Abhigna855/Hybrid-RAG-Model/blob/main/6b2d91d7-3b37-42dc-a3df-e7d13a0ce8d4.png?raw=true)

### 4. Retrieval Metrics

This figure presents retrieval-quality metrics such as ranking and relevance performance.

![Retrieval Metrics](images/retrieval_metrics.png)

### 5. Generation Metrics

This figure shows answer-quality metrics for the generated responses.

![Generation Metrics](images/generation_metrics.png)

### 6. Latency Distribution

This figure shows the spread of response latencies across the evaluated systems.

![Latency Distribution](images/latency_distribution.png)

---

## Repository Structure

```text
Hybrid-RAG-PubMedQA
│
├── notebooks/
│   └── Hybrid_RAG.ipynb
│
├── images/
│   ├── performance_comparison.png
│   ├── accuracy_comparison.png
│   ├── latency_comparison.png
│   ├── retrieval_metrics.png
│   ├── generation_metrics.png
│   └── latency_distribution.png
│
├── docs/
│   └── Dissertation.pdf
│
├── requirements.txt
├── LICENSE
└── README.md
```

---

## Installation

Clone the repository:

```bash
git clone https://github.com/YOUR_USERNAME/Hybrid-RAG-PubMedQA.git
```

Move into the project directory:

```bash
cd Hybrid-RAG-PubMedQA
```

Install dependencies:

```bash
pip install -r requirements.txt
```

---

## Running the Project

Launch Jupyter Notebook:

```bash
jupyter notebook
```

Open and run:

```text
Hybrid_RAG.ipynb
```

The notebook includes:

- Dataset loading.
- Data preprocessing.
- Dense retrieval.
- Sparse retrieval.
- Hybrid retrieval.
- Answer generation.
- Evaluation.
- Visualisation of results.

---

## Evaluation Metrics

### Retrieval Metrics

- Precision@K.
- Recall@K.
- Mean Reciprocal Rank.
- nDCG.

### Generation Metrics

- Exact Match.
- F1 Score.
- BLEU.
- ROUGE.

### System Metrics

- Accuracy.
- Query latency.
- Retrieval speed.

---

## Future Improvements

- Cross-encoder re-ranking.
- Multi-embedding retrieval.
- Larger biomedical language models.
- GPU acceleration.
- Retrieval caching.
- Knowledge graph integration.
- Docker deployment.
- Streamlit web app.
- REST API integration.
- Clinical QA extension.

---

## References

- PubMedQA dataset.
- Hugging Face Datasets.
- FAISS.
- Sentence Transformers.
- BM25.
- FLAN-T5.
- Scikit-learn.
- NLTK.

---

## Author

**Abhigna Korapala**  
MSc Artificial Intelligence  
University Dissertation Project

# NLP for Legal Evidence Retrieval and Classification

## Background

Legal fact-checking involves determining whether a textual claim is **supported**, **refuted**, or **not verifiable** based on available evidence.  
This project explores how lightweight NLP techniques—ranging from symbolic retrieval to semantic embedding models and neural sequence classifiers—can facilitate legal verification tasks under limited computational resources.

The work focuses on building an end-to-end pipeline capable of retrieving relevant legal evidence and classifying the veracity of claims. By comparing multiple retrieval methods and neural architectures, the project aims to identify an effective and computationally efficient configuration for real-world legal fact-checking.

---

## Overview

This repository implements an NLP-based pipeline for **legal evidence retrieval** and **claim classification**.  
The system evaluates symbolic, semantic, and hybrid retrieval strategies (TF-IDF, FAISS, and TF-IDF+FAISS), and compares several neural classification models, including RNN, LSTM, GRU, and Transformer encoders.

Across all experiments, the **GRU model combined with hybrid retrieval** achieved the best balance between evidence relevance and claim accuracy.  
This configuration demonstrated the highest harmonic mean between evidence F-score and claim accuracy, and was therefore selected as the final system.

---

## Features

### **1. Evidence Retrieval**
The pipeline includes three retrieval mechanisms, each contributing unique strengths:

- **TF-IDF** — symbolic lexical retrieval, efficient and interpretable  
- **FAISS + SentenceTransformer embeddings** — semantic retrieval capturing contextual similarity  
- **Hybrid Retrieval (TF-IDF + FAISS)** — integrates symbolic precision and semantic generalization  
  - Achieves the strongest retrieval performance  
  - Provides robust coverage of relevant evidence

---

### **2. Classification Models**
Multiple neural architectures were implemented and evaluated:

- **RNN** — baseline sequential classifier  
- **LSTM** — improves long-range dependency modeling via gating structures  
- **GRU** — lightweight, stable, and highly effective alternative to LSTM  
- **Transformer Encoder** — attention-based architecture capable of parallel processing  

All models were trained using input sequences composed of claims concatenated with their Top-5 retrieved evidence passages.

---

### **3. Final Model Selection**
The **GRU + Hybrid Retrieval** configuration consistently provided the best overall results.  
It is computationally efficient, maintains strong retrieval recall, and offers balanced classification performance, making it the optimal system among all tested combinations.

---

## Experimental Results

### **Retrieval Performance**
Hybrid retrieval achieved the highest Top-5 hit rate and provided the strongest evidence coverage across all retrieval methods tested.

### **Classification Performance**

| Model + Retrieval | Claim Accuracy | Evidence F1 | Harmonic Mean |
|------------------|----------------|-------------|----------------|
| **GRU + Hybrid** | 0.4481 | 0.1782 | **0.2550** |
| GRU + FAISS | 0.4740 | 0.1612 | 0.2406 |
| LSTM + Hybrid | 0.4026 | 0.1782 | 0.2471 |
| Transformer + Hybrid | 0.4415 | 0.1782 | 0.2539 |

The GRU-Hybrid model offered the strongest overall performance and was selected as the final system.

---

## License

This project is intended for academic and research use.  
It may be used for coursework evaluation, replication, or portfolio presentation.

---

## Acknowledgements

This project builds on standard NLP approaches to retrieval and classification, informed by prior work in evidence-based fact-checking and efficient neural architectures.

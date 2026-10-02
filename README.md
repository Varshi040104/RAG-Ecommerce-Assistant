# 🛒 ShopKart: Grounded E-Commerce RAG Assistant & Recommender

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1di2yLFqjtjv8zT5pYbGTT4hk8IT3SqHp)

An end-to-end e-commerce data pipeline and Retrieval-Augmented Generation (RAG) product assistant built with **Python**, **Pandas**, **FAISS**, and the **Gemini 2.5 Flash API**. 

This project demonstrates how to turn raw e-commerce transaction data into intelligent features and leverage semantic vector search paired with LLM guardrails to deliver accurate, non-hallucinating product recommendations.

---

## 🌟 Key Features

* **Data Wrangling & Analytics:** Cleaned and merged transactional order histories, customer profiles, and product catalogs using Pandas and Seaborn.
* **RFM Segmentation:** Performed Recency, Frequency, and Monetary (RFM) analysis to segment customer behavior.
* **Semantic Vector Search:** Embedded catalog product attributes and indexed them using `FAISS` and `sentence-transformers` for fast semantic intent retrieval beyond simple keyword matching.
* **Grounded RAG Pipeline:** Constructed an automated prompt context pipeline using Gemini 2.5 Flash (`google-genai` SDK) that constrains answers strictly to available inventory.
* **LLM Guardrails:** Engineered strict system rules to cite product IDs, enforce budget constraints, and handle out-of-stock or missing queries gracefully.
* **Secure API Integration:** Integrated Google Colab Secrets (`userdata`) to safely handle API keys without exposure.

---

## 🛠️ Tech Stack

* **Language:** Python 3.13
* **Data Processing & ML:** Pandas, NumPy, Scikit-learn, FAISS, Sentence-Transformers
* **Generative AI:** Google Gemini 2.5 Flash API (`google-genai` / Colab Secrets)
* **Visualization:** Seaborn, Matplotlib

---

## 🚀 How It Works

1. **Query Processing:** The user asks a natural language shopping request (e.g., *"wireless noise-canceling earbuds under ₹2000"*).
2. **Dense Retrieval:** FAISS calculates vector similarity across the pre-computed catalog embeddings to retrieve the top $k$ relevant product matches.
3. **Context Augmentation:** The retrieved product details (ID, name, price, rating, description) are dynamically injected into a structured prompt template.
4. **Grounded Generation:** Gemini 2.5 Flash evaluates the prompt under guardrail constraints and generates a clear, cited recommendation.

---

## 📝 Example Output

```text
User Query: "Looking for budget-friendly wireless earbuds with good battery life under ₹1500"

Assistant Response:
Based on our catalog, here is the best match for you:

• Boat Wireless Earbuds (PRD017) — ₹1,299 | Rating: 4.3/5
  - Features: Deep bass, fast charging, and up to 30 hours of playback.
  - Why it fits: Fits comfortably under your ₹1500 budget while delivering top battery performance.  

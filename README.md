# Hybrid Recommender System for E-commerce Product Prediction

## Introduction
This repository contains code and resources for our project **"Forecasting of Customer’s Purchasing"**, developed as part of the *ECE 9063/ECE 9603 Data Analytics Foundations* course.  
We address the problem of generating **personalized product recommendations** by leveraging **collaborative filtering**, **content-based models**, and a **novel hybrid approach**.  
The hybrid method effectively mitigates challenges such as **data sparsity** and **cold-start problems** by integrating the strengths of four base algorithms.  

Our experiments on the **Amazon Reviews Dataset (Appliances)** show that the hybrid model outperforms the best individual method (enhanced content-based filtering) by **~115% in R@20** and **~32% in R@50**.

---

## Workflow Overview
![Workflow Diagram](images/workflow.png)  
*Overall pipeline: Data preprocessing → Feature engineering → Individual model training → Hybrid ranking integration → Evaluation.*

---

## Methodology

### Base Models
1. **User-based Collaborative Filtering**  
   - Finds k-nearest neighbors (KNN) using cosine similarity on normalized ratings.  
   - Adapts quickly to changing user preferences.  

2. **Item-based Collaborative Filtering**  
   - Identifies items similar to those a user liked.  
   - Efficient but more sensitive to data sparsity.  

3. **Model-based Collaborative Filtering (SVD)**  
   - Learns latent factors of users/items to capture hidden patterns.  

4. **Enhanced Content-based Filtering**  
   - Extracts item features from text (categories, title, description, details).  
   - Applies TF-IDF encoding and cosine similarity against user preference vectors.

---

### Hybrid Method
- Combines recommendations from all four base models into a **merged pool**.  
- Computes similarity between each candidate item and the user’s history (TF-IDF space).  
- Weights similarities by past ratings to produce a **final relevance score**.  
- Ranks and selects **Top-20, Top-50, Top-100** recommendations.

![Hybrid Method Diagram](images/hybrid_method.png)

---

## Dataset
- **Source:** [Amazon Reviews 2023 – Appliances Category](https://amazon-reviews-2023.github.io/)  
- **Raw Data:**  
  - *Reviews table:* ~2.1M entries, 8 features  
  - *Product metadata:* ~94k entries, 14 features  
- **Preprocessing Steps:**  
  - Remove null/invalid rows  
  - Merge review & metadata tables on product ID  
  - Filter users by history length (23–75 purchases)  
  - TF-IDF vectorization of concatenated text features  

---

## Training & Execution
### Requirements
```bash
pip install -r requirements.txt

# Forecasting of Customer's Purchasing
This project aims to leverage multiple recommendation algorithms to provide personalized product recommendations for e-commerce users, increasing purchase intent and overall sales.
Using Amazon Reviews Dataset user-item interaction data, we implemented four recommendation methods and proposed an innovative Hybrid Method, which significantly outperforms single models in recommendation accuracy.
# Implemented Recommendation Algorithms
**User-based Collaborative Filtering**  
**Item-based Collaborative Filtering**  
**Model-based Collaborative Filtering (SVD)**  
**Content-based Method (Improved)**  

Builds feature vectors from product text data (title, category, description, details).  
Uses TF-IDF encoding + cosine similarity.  
Pros: Handles cold-start problem, provides explainable recommendations.    
**Hybrid Method (Innovative)**  
Combines all four methods into a unified recommendation pool.
Re-ranks results using weighted similarity scores based on user history ratings.
Achieves >100% improvement in Recall and NDCG for Top-20 and Top-50 compared to the best single model.
# Dataset
Source: Amazon Reviews 2023
**Size:**

Review Table: 2,120,000 reviews, 8 attributes.

Product Meta Table: 94,000 products, 14 attributes.

**Preprocessing:**

Removed null and invalid values.

Merged review and product meta tables.

Filtered users with extreme activity levels.

Extracted and encoded text features using TF-IDF.
# Evaluation Metrics
**Recall@k** – measures the proportion of relevant items retrieved.

**NDCG@k** – measures ranking quality by considering both relevance and position.

**Evaluated for Top-20, Top-50, and Top-100 recommendations.**

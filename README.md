# 🛒 Ecommerce Product Recommendation System

A **Machine Learning-based Recommendation System** that provides personalized product suggestions to users based on their interaction history.  
This project implements **three different recommendation strategies** — Rank-Based, User-Based Collaborative Filtering, and Model-Based Collaborative Filtering (SVD).

---

## 🚀 Project Overview

The **Ecommerce Product Recommendation System** is designed to enhance user experience and engagement by suggesting products tailored to individual user preferences.  
It leverages collaborative filtering and ranking-based techniques to analyze user–product interaction data and generate relevant, data-driven recommendations.

---

## 📚 Approaches Implemented

### 1️⃣ Rank-Based Product Recommendation

**🎯 Objective:**
- Recommend the most popular products to all users.
- Target new customers (cold start) by showing trending or highly rated items.
- Solve the *cold start problem* where user-specific data is unavailable.

**🧩 Approach:**
1. Calculate the **average rating** and **total number of ratings** for each product.
2. Filter products having at least a minimum number of interactions (e.g., 50 or 100).
3. Sort products based on average ratings and number of ratings.
4. Recommend top-N products to users.

**📈 Output:**
- Top 5 most popular products (with at least 50/100 ratings).

---

### 2️⃣ User-Based Collaborative Filtering (Similarity-Based)

**🎯 Objective:**
- Provide **personalized recommendations** based on similar users’ behavior.
- Leverage **user–user similarity** using cosine similarity.

**🧩 Approach:**
1. Convert `user_id` to integer indices for efficient matrix operations.
2. **Find similar users**:
   - Compute cosine similarity between the target user and all other users.
   - Sort users by similarity score.
3. **Recommend products**:
   - Identify products rated by similar users but not by the target user.
   - Recommend top-N such products.

**⚙️ Key Functions:**
- `find_similar_users(user_id)` → returns list of most similar users and their similarity scores.
- `recommend_items(user_id, n)` → recommends top `n` products not yet rated by the target user.

**📈 Output:**
- Top 5 personalized product recommendations per user.

---

### 3️⃣ Model-Based Collaborative Filtering (SVD-Based)

**🎯 Objective:**
- Provide **scalable, high-quality recommendations** using matrix factorization.
- Overcome sparsity and scalability issues faced by memory-based methods.

**🧩 Approach:**
1. Convert the user–item rating matrix to a **Compressed Sparse Row (CSR)** matrix for memory efficiency.
2. Apply **Singular Value Decomposition (SVD)**:
   - Decompose the sparse matrix into **U**, **Σ**, and **Vᵗ**.
   - Retain `k = 50` latent features capturing hidden patterns between users and products.
3. Compute **predicted ratings**:
       `Ŕ = U × Σ × Vᵀ`

   Each cell in `Ŕ` represents the predicted rating of a user for a product.
4. Build a **recommendation function**:
   - Extract user’s actual and predicted ratings.
   - Filter out already-rated products.
   - Sort remaining products by predicted score.
   - Recommend top-N items.
5. **Evaluate model performance** using **Root Mean Square Error (RMSE)**:
   - Compare average actual ratings vs. average predicted ratings.
   - Lower RMSE indicates better prediction accuracy.

**📈 Output:**
- Top 5 product recommendations for each user.
- Model evaluation with RMSE score.

---

## 📊 Evaluation Metric

**Root Mean Square Error (RMSE)** is used to assess the accuracy of predicted ratings:
  `RMSE = sqrt( (1/n) * Σ (rᵢ - ŕᵢ)² )`

## 💡 Key Learnings
- How to handle sparse user–item rating matrices.
- Implementation of user similarity using **cosine similarity**.
- Understanding and applying **Singular Value Decomposition (SVD)** for latent factor modeling.
- Model evaluation using **RMSE**.
- Comparative study of rank-based, memory-based, and model-based recommenders.

---

## 🧰 Tech Stack

- **Python**
- **Libraries:**  
  `NumPy`, `Pandas`, `scikit-learn`, `SciPy`, `Matplotlib`
- **Algorithmic Techniques:**  
  - Rank-based popularity model  
  - User-based collaborative filtering (Cosine similarity)  
  - Model-based collaborative filtering (SVD)

---

## 🧑‍💻 Author

**Harshith Reddy**  
Machine Learning & Data Science Enthusiast

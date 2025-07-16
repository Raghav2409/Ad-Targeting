# 📊 URL Clustering for Ad Targeting

This repository contains an end-to-end pipeline for clustering 30,000 URLs using machine learning to enable precise **audience segmentation for advertising**. We used **unsupervised learning**, **PCA**, **K-Means**, and **GPT-4-based labeling** to uncover thematic groupings and generate actionable ad-targeting insights.

---

## 🧠 Project Overview

* **Goal**: Categorize large-scale URLs based on their content to enhance personalized ad delivery.
* **Data**: URL embeddings + page content + language metadata.
* **Output**:

  * `urls_with_clusters_v2.csv` → URL-to-cluster assignments
  * `cluster_labels.csv` → Human-readable cluster labels with top keywords

---

## 🧰 Technologies Used

* Python (Pandas, NumPy, Scikit-learn, UMAP, Seaborn, Matplotlib)
* NLP: NLTK, WordCloud
* Clustering: K-Means, DBSCAN, Hierarchical
* Dimensionality Reduction: PCA, UMAP
* LLM: OpenAI GPT-4 API

---

## 🚀 Pipeline Steps

### 1. Data Loading & Preparation

* Parsed URL embeddings from a parquet file.
* Preprocessed and converted embeddings to NumPy arrays.

### 2. Dimensionality Reduction

* Used **PCA (95% variance retained)** to reduce 768D vectors to \~241D.
* Also explored **UMAP** for clustering and visualization.

---

### 3. Clustering Approaches

| Method         | Coverage | Silhouette Score | Notes                                     |
| -------------- | -------- | ---------------- | ----------------------------------------- |
| K-Means (k=25) | ✅ 100%   | 0.019            | Best tradeoff of scale + interpretability |
| DBSCAN         | ❌ \~32%  | 0.041            | High noise (68%), limited coverage        |
| Hierarchical   | ✅ 100%   | 0.002            | Weak separation for dense data            |

📌 *Snapshot: elbow & silhouette analysis, cluster visualizations (PCA)*
<img width="909" height="313" alt="Screenshot 2025-07-16 at 4 06 59 PM" src="https://github.com/user-attachments/assets/7becc93c-e059-46c5-a684-56853137d77a" />

---

### 4. Cluster Interpretation

* Generated **word clouds** per cluster to visualize content themes.
* Cleaned multilingual text using custom stopword set (EN, FR, DE, etc.)

📌 *Snapshots: Cluster Word Clouds from notebook (Pages 15–23)*
<img width="481" height="747" alt="Screenshot 2025-07-16 at 4 08 16 PM" src="https://github.com/user-attachments/assets/43f2a3a8-4d06-492d-9c18-26d3bd4e0db4" />

---

### 5. GPT-4 Based Cluster Labeling

* Used OpenAI GPT-4 API to assign **human-readable names** to each cluster.
* Output format: `Language - Category Name`

| Cluster ID | Category                    | Language(s)    |
| ---------- | --------------------------- | -------------- |
| 0          | Word Games                  | English/French |
| 4          | Gaming Enthusiasts          | English        |
| 6          | Indian News & Entertainment | English/Hindi  |
| 17         | Cooking & Recipes           | English        |
| 24         | Automobile Comparison       | English/French |

📌 *Snapshot: Cluster labeling table (Page 26)*
<img width="474" height="819" alt="Screenshot 2025-07-16 at 4 08 56 PM" src="https://github.com/user-attachments/assets/073dbd1c-dc42-4bea-93af-e908a61fe35a" />

---

## 📈 Results Summary

* **25 Unique Clusters**
* **100% URL Coverage**
* **Highly Distinct Topics**: Word clouds validated topical separation
* **Languages Covered**: English, French, German, Hindi

📌 *Snapshot: Final Analysis Table (Page 27)*
<img width="429" height="210" alt="Screenshot 2025-07-16 at 4 09 34 PM" src="https://github.com/user-attachments/assets/d97d20b9-f7a2-4399-9f33-62730c189ab6" />

---

## 🎯 Business Impact

* ✅ Target-specific advertising based on content categories
* ✅ Enable multilingual ad campaigns
* ✅ Scalable framework for millions of URLs
* ✅ Clear keyword mapping for contextual ad targeting

---

## 📂 Files Included

| File Name                   | Description                                  |
| --------------------------- | -------------------------------------------- |
| `Solution.ipynb`            | Full Jupyter notebook with code & results    |
| `urls_with_clusters_v2.csv` | Cluster assignment for each URL              |
| `cluster_labels.csv`        | Human-readable labels & top keywords         |
| `dataset_2024.parquet`      | Raw URL embeddings input (not uploaded here) |

---

## 👤 Author

**Raghav Gupta**
Data Science & Machine Learning Enthusiast
🔗 [GitHub Profile](https://github.com/Raghav2409)

---

## 📌 How to Use

1. Clone the repo
2. Run the `Solution.ipynb` notebook
3. Check `urls_with_clusters_v2.csv` and `cluster_labels.csv` for outputs
4. Apply these insights to drive audience-specific advertising strategies

---

Let me know if you'd like this in Markdown format or need help embedding actual image snapshots into the README.

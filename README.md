# E-Commerce Product Delivery Predictor & SQL-ML Pipeline

This repository contains an end-to-end Machine Learning classification and SQL analysis project. It demonstrates proficiency in both software systems data handling (SQL data extraction and pipelines) and core Data Science/AI algorithms (model selection, feature engineering, and evaluation). 

This project is tailored for portfolio display to demonstrate capability in SDE, Data Science, and Machine Learning engineering roles.

---

##  Project Overview

The business goal is to predict shipping delays (`reached_on_time` = 1 or 0) for e-commerce products based on logistics, product properties, and customer interaction metrics.

###  Key Technical Features
1. **SQL Extraction Layer**: Leverages an in-memory SQL database (SQLite) built from raw transactions. SQL queries are used to pull, filter, and clean data before modeling—emulating production pipelines.
2. **Exploratory Data Analysis (EDA)**: Visualizations showing class balance, shipment mode statistics, and a feature correlation matrix.
3. **Machine Learning Benchmarking**: Side-by-side performance evaluation of 5 core classification algorithms:
   * **Logistic Regression** (Linear baseline)
   * **Decision Tree** (Non-linear rule-based classifier)
   * **Random Forest** (Ensemble of trees)
   * **K-Nearest Neighbors (KNN)** (Instance/distance-based classifier)
   * **Naive Bayes** (Probabilistic classifier)
4. **Evaluation Diagnostics**: Performance analysis using Accuracy, Precision, Recall, F1-Score, Confusion Matrices, and Feature Importance charts.

---

##  Model Evaluation Performance Matrix

The classification models were evaluated on a test set (20% split) and compared side-by-side:

| Model | Accuracy | Precision | Recall | F1-Score |
| :--- | :---: | :---: | :---: | :---: |
| **Random Forest** | **68.14%** | **81.23%** | 58.98% | **68.35%** |
| **Decision Tree** | **68.00%** | **81.05%** | 58.80% | **68.15%** |
| **Naive Bayes** | 65.00% | 70.42% | 69.01% | 69.71% |
| **K-Nearest Neighbors** | 63.86% | 69.74% | 67.25% | 68.47% |
| **Logistic Regression** | 63.45% | 68.81% | 68.31% | 68.56% |

---

##  Key Conclusions & Business Insights

### 1. Model Selection
* **Ensemble Superiority**: Tree-based models (**Random Forest** and **Decision Tree**) achieved the highest accuracy (~68%) and precision (~81%). They successfully capture the non-linear boundaries in the dataset.
* **Linear Model Constraints**: Logistic Regression and Naive Bayes performed worse, indicating that logistics features do not have a simple linear relationship with shipping delays.

### 2. Feature Importance Analysis (Random Forest)
* **Discounts Offered**: This is the single most important predictor. If the discount offered is above a certain threshold, the package is statistically much more likely to be delayed. This suggests that large discounted promotional orders bottleneck the fulfillment hubs.
* **Weight of the Product**: Bulkier packages have lower delivery speeds. Streamlining sorting operations for heavier shipments can solve this bottleneck.

### 3. Actionable Business Recommendations
* **Dynamic Scheduling**: Implement dynamic delivery scheduling. For heavy items or highly discounted promotions, the platform should proactively set realistic delivery expectations on the customer UI or optimize carrier routing for these items.
* **Prioritization**: High-importance items should be assigned dedicated courier channels to increase the precision of on-time delivery.

---

##  How to Run Locally

### Prerequisites
Make sure you have Python 3.8+ installed.

### 1. Clone this Repository
```bash
git clone <your-repo-link>
cd <repo-name>
```

### 2. Install Dependencies
```bash
pip install -r requirements.txt
```

### 3. Run the Notebook
Open your preferred editor (VS Code, Jupyter Lab, or Google Colab) and run the `classification_benchmark.ipynb` file.

*Note: If you run this notebook on **Kaggle**, it is pre-configured to automatically locate the dataset mount directory (`/kaggle/input/...`) and run smoothly.*

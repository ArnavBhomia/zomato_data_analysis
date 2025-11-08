# Zomato Data Analysis & Predictive Modeling

This is an end-to-end data science project that analyzes a large Zomato dataset to uncover key drivers of restaurant ratings, test hypotheses, and build machine learning models to predict ratings and segment the market.

The project moves from a raw, 9,500-row global dataset to a cleaned, analysis-ready file, culminating in a K-Means clustering model that identifies four distinct market segments.



---

### 🛠️ Tools & Libraries

* **Python**
* **Pandas & NumPy:** For data cleaning, manipulation, and feature engineering.
* **Matplotlib & Seaborn:** For data visualization (heatmaps, box plots, scatter plots, etc.).
* **Scikit-learn (sklearn):** For hypothesis testing (T-test, Chi-Square), regression modeling, and K-Means clustering.
* **Jupyter Notebook:** As the primary development environment.

---

### 📂 Project Workflow & Key Findings

This project followed a 6-phase data science workflow:

#### Phase 1: Data Cleaning & Scoping
* **Problem:** The raw dataset contained 9,551 restaurants from 12 different countries, making the `Average Cost for two` column unusable due to mixed currencies.
* **Solution:** Scoped the project by filtering for the Indian market, which represented ~90% (8,652 rows) of the data, ensuring a single, comparable currency (INR).
* **Key Action:** Correctly identified `0` values in `Aggregate rating` as "Not Rated" (a category, not a score) and `0` in `Average Cost for two` as missing data. Both were filtered out to create a 100% clean, analysis-ready dataset of 6,504 restaurants.

#### Phase 2: Exploratory Data Analysis (EDA)
* **Correlation:** A **Heatmap** revealed that `Votes` (0.40) and `Price range` (0.36) had the strongest positive correlations with `Aggregate rating`.
* **Visualization:** A **log-scaled Scatter Plot** showed a clear positive trend: as a restaurant gets more votes, its rating tends to be higher and more consistent.
* **Key Insight:** A **Box Plot** showed a *very strong* signal that restaurants offering `Has Table booking` have a significantly higher median rating than those that do not.

#### Phase 3: Inferential Statistics (Hypothesis Testing)
Statistically proved the findings from EDA using a significance level of $\alpha = 0.05$.

* **T-Test:** Proved that the difference in mean ratings between restaurants *with* and *without* table booking was **statistically significant** (p-value < 0.05).
* **Chi-Square ($\chi^2$) Test:** Proved there is a **statistically significant association** between a restaurant's `City` and its `Price range` (p-value < 0.05).

#### Phase 4: Simple Linear Regression
* **Goal:** To predict `Aggregate rating` using the strongest predictor, `log(Votes)`.
* **Model:** Built a Simple Linear Regression model as required by the project scope.
* **Evaluation:**
    * **R-squared ($R^2$): 0.4131**. This proves that `Votes` is a major factor, explaining 41% of the variance in a restaurant's rating.
    * **Mean Absolute Error (MAE): 0.2852 stars**. This shows the model's limitations, as it's too simple for production but excellent as a diagnostic tool.

#### Phase 5: K-Means Clustering
* **Goal:** To perform market segmentation by finding "natural" clusters of restaurants.
* **Method:**
    1.  Used the **Elbow Method** to determine the optimal number of clusters is **K=4**.
    2.  Ran a **K-Means** model on the `Average Cost for two` and `Aggregate rating` features.
* **Outcome:** Successfully segmented the market into four distinct groups:
    1.  **The "Average Crowd"** (Low Cost, Low/Avg Rating)
    2.  **The "Mainstream Hits"** (Low/Med Cost, High Rating)
    3.  **The "Budget Gems"** (Very Low Cost, High Rating)
    4.  **The "Premium & Luxury"** (High Cost, High Rating)

---

### 🚀 How to Run This Project

1.  Clone this repository:
    ```bash
    git clone [https://github.com/](https://github.com/)[ArnavBhomia]/[zomato_data_analysis].git
    ```
2.  Install the required libraries:
    ```bash
    pip install pandas numpy matplotlib seaborn scikit-learn jupyter
    ```
3.  Open the notebook file (`zomato.ipynb`) in Jupyter Notebook.
4.  The `zomato.csv` dataset is included in this repository, so you can run all cells from top to bottom.

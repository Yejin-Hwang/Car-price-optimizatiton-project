# 🚗 Car Dataset Analysis (Multivariate Statistical Analysis)

This project explores the relationships between vehicle features and their pricing using multivariate statistical methods. The main goal is to classify cars into price segments (Low, Mid, High) and uncover patterns using PCA, Factor Analysis, and Clustering.

---

## 📊 Dataset Overview

- **Source**: 11,000 car samples from 1990 to 2017  
- **Response Variable**: MSRP (Price), categorized into Low / Mid / High via 33% and 67% quantiles  
- **Features**: Year, Horsepower, MPG, Engine Cylinders, Popularity, etc.

---

## ⚠️ Challenges

- **Skewed Distribution**: MSRP and engine-related features were highly skewed  
- **Outliers**: Extreme luxury and electric vehicles skew the analysis  
- **Correlated Variables**:  
  - Year & MSRP: `r = 0.7`  
  - City MPG & Highway MPG: `r = 0.93`  
  - Cylinders & MPG: `r = -0.7`

---

## 🔧 Data Preprocessing

- Removed missing values (105 rows)
- Outliers: Kept EVs, excluded luxury car outliers using IQR
- Applied **log transformation** to skewed features
- **Standardized** numerical variables
- Reduced to 3,000 samples for efficiency

---

## 🧪 Methodology

### ✅ MANOVA & LDA

- **Normality violated** (via Q-Q plot, Anderson-Darling)
- **Box’s M test** failed → unequal covariance matrices
- Despite this, MANOVA showed significant group differences (p < 2.2e-16)
- But results should be interpreted cautiously due to assumption violations

---

### 📉 Principal Component Analysis (PCA)

- Selected PC1–PC3 based on eigenvalues > 1  
- Explained **81% of total variance**

| Component | Interpretation                        | Variance Explained |
|-----------|---------------------------------------|--------------------|
| PC1       | MSRP, Horsepower, Year (Performance) | 41.14%             |
| PC2       | City/Highway MPG (Efficiency)         | 27.61%             |
| PC3       | Minor factors                         | ~12%               |

> 📌 Visualized using biplots to observe variable contributions.

---

### 🧠 Factor Analysis

- 4 Factors explaining ~81% of variance  
- Scree plot & cumulative variance used for selection

| Factor   | Interpretation                        |
|----------|----------------------------------------|
| Factor 1 | Fuel Efficiency (MPG, Cylinders)       |
| Factor 2 | Power & Price (Horsepower, MSRP)       |
| Factor 3 | Popularity                             |
| Factor 4 | Basic Specs (Doors, Year)              |

---

### 🔗 Cluster Analysis (K-Means)

- Optimal clusters: **3** (elbow method)  
- Explained variance: **68.7%**

> 🚗 Cluster separation visualized with face and star plots

---

## 🧾 Conclusion

- **PCA** reduced dimensionality and revealed performance/efficiency traits  
- **Factor Analysis** identified interpretable hidden dimensions  
- **Clustering** successfully segmented cars into 3 unique groups  
- **MANOVA** showed statistical significance but lacked robustness

> This analysis supports strategic vehicle segmentation for manufacturers.

---

## 👩‍💻 Author

**Yejin Hwang**  
Graduate Student @ Texas A&M University - Corpus Christi  


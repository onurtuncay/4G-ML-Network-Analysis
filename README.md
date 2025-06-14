# 4G-ML-Network-Analysis

**Author:** Onur Tuncay

This project presents a comprehensive machine learning pipeline applied to real-world 4G LTE passive network measurements. It includes data preprocessing, exploratory data analysis, unsupervised clustering, classification, and model optimization using a genetic algorithm. The goal is to understand, segment, and predict network performance patterns across various mobility and signal conditions in an urban 4G environment.

## 📊 Dataset

The dataset used in this study is the **"4G - Passive Measurements"** subset of a larger mobile network measurement dataset:

- **Source:** IEEE Dataport  
- **Link:** [Large-Scale Dataset of 4G, NB-IoT, and 5G Non-Standalone Network Measurements](https://ieee-dataport.org/documents/large-scale-dataset-4g-nb-iot-and-5g-non-standalone-network-measurements)  
- **License:** Creative Commons Attribution 4.0  
- **Collection location:** Rome, Italy  
- **Records:** ~527,000 rows, 26 features  

> 📖 **Reference:**  
> Konstantinos Kousias, Mohammad Rajiullah, Giuseppe Caso, Usman Ali, Ozgu Alay, Anna Brunstrom, Luca De Nardis, Marco Neri, Maria-Gabriella Di Benedetto (2022).  
> *A Large-Scale Dataset of 4G, NB-IoT, and 5G Non-Standalone Network Measurements*.  
> DOI: [10.21227/7a8s-nt68](https://dx.doi.org/10.21227/7a8s-nt68)

---

## 🧠 Methodology

The study follows a structured ML pipeline:

### 🔧 Data Preprocessing
- Missing value handling using domain-informed median imputation
- Outlier detection via Z-Score and IQR methods
- Feature engineering from timestamps (e.g., day, hour, is_weekend)
- Label encoding of categorical features
- Standardization of numerical features (for classification only)

### 📈 Clustering
- **K-Means** and **Agglomerative Hierarchical Clustering**
- Optimal cluster selection using Elbow Method and Silhouette Score (best k=3)
- PCA visualizations and signal quality profiling across clusters

### 🎯 Classification
- Binary classification on `MNC` (mobile operator)
- Multiclass classification on `scenario` (e.g., indoor/outdoor)
- Models: **Random Forest** and **Logistic Regression**
- Evaluation via accuracy and F1-score
- SHAP analysis for explainability

### 🧬 Optimization
- Genetic Algorithm (GA) used to tune Random Forest hyperparameters
- Achieved improvement: **F1 increased from 0.91 to 0.949**

---

## 📈 Key Results

| Task                        | Best Model         | Score         |
|----------------------------|--------------------|---------------|
| Binary Classification      | Random Forest      | Accuracy: 0.89 |
| Multi-class Classification | Random Forest (GA) | F1: 0.949     |
| Clustering (Silhouette)    | K-Means / Agg.     | 0.62          |

---

## ⚙️ Installation

Install required dependencies:

```bash
pip install -r requirements.txt
```
### 📚 Citation
If you use this dataset, please cite:

Kousias, K., Rajiullah, M., Caso, G., Ali, U., Alay, Ö., Brunstrom, A., De Nardis, L., Neri, M., & Di Benedetto, M.-G. (2022).
A Large-Scale Dataset of 4G, NB-IoT, and 5G Non-Standalone Network Measurements.
DOI: 10.21227/7a8s-nt68


## 👤 Contributor
Developed and maintained by:
Onur Tuncay – Researcher in Machine Learning & NLP,  Senior Data Scientist and MSc Data Science Student at University of Gloucestershire


### 📝 License
This project is distributed under the MIT License.
Dataset is used under CC-BY 4.0 license.

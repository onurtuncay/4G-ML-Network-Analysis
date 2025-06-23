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
## 📏 Key Evaluation Metrics

Different evaluation metrics were used across the pipeline depending on the nature of the task and the data distribution. Below is a summary of the metrics used and the rationale behind each choice:

### 🔹 Clustering Tasks (K-Means, Agglomerative)
- **Metric Used:** Silhouette Score  
- **Why:** Clustering is unsupervised and lacks true labels. Silhouette Score evaluates the quality of clustering by measuring how similar an object is to its own cluster compared to other clusters. It balances intra-cluster cohesion and inter-cluster separation.

### 🔹 Binary Classification (Target: MNC)
- **Metrics Used:** Accuracy, F1-Score, Confusion Matrix, SHAP  
- **Why:** The MNC classes are balanced (~54% vs 46%), so accuracy is a valid performance metric. F1-Score complements it by balancing precision and recall. SHAP values were used to explain the feature contributions and enhance model interpretability.

### 🔹 Multiclass Classification (Target: Scenario)
- **Metrics Used:** Macro F1-Score, Confusion Matrix, SHAP  
- **Why:** The scenario variable is imbalanced (43%/41%/16%). Accuracy could be misleading, so macro F1-score was used to treat all classes equally. SHAP values and confusion matrices were used to interpret class-wise performance and understand feature impact.

### 🔹 Genetic Algorithm Optimization
- **Metric Used:** Weighted F1-Score (with 3-fold cross-validation)  
- **Why:** During hyperparameter tuning, weighted F1-score was used as a fitness function to ensure performance across all classes, especially the frequent ones. Cross-validation further helped reduce overfitting and improve generalization.

## 📈 Key Results

| Task                        | Best Model         | Score         |
|----------------------------|--------------------|---------------|
| Binary Classification      | Random Forest      | Accuracy: 0.89 |
| Multi-class Classification | Random Forest (GA) | F1: 0.949     |
| Clustering (Silhouette)    | K-Means / Agg.     | 0.62          |

---
## ⚠️ GitHub Preview Notice

Some parts of the Jupyter notebook may not render properly in GitHub's web-based preview due to platform limitations. In particular:

- Certain sections (e.g., *Handling Missing Values*, *Handling Categorical Columns*) may appear partially or completely blank.
- Wide content or large tables may require **horizontal scrolling** (slide right →) to be visible.

### ✅ Recommended Workarounds:
- Download and open the notebook locally using **Jupyter Notebook or JupyterLab**.
- Alternatively, view the **PDF version** available in this repository for a clean, complete view of all outputs and explanations.

👉 [Download the PDF report](./4G-ML-Network-Analysis-Outputs.pdf)

---

## ⚙️ Installation

Install required dependencies:

```bash
pip install -r requirements.txt
```

---

## 📁 Project Structure

4G-ML-Network-Analysis/

├── 4G-ML-Network-Analysis.ipynb # Main notebook with full pipeline

├── 4G-ML-Network-Analysis-Outputs.pdf # Clean report version of the notebook

├── requirements.txt # Required dependencies

└── README.md # Project documentation

---

## ▶️ How to Run This Project

1. Clone the repository  
```bash
git clone https://github.com/onurtuncay/4G-ML-Network-Analysis.git
cd 4G-ML-Network-Analysis
```
2. Install required packages

```bash
pip install -r requirements.txt
```
3. Open the notebook

```bash
jupyter notebook 4G-ML-Network-Analysis.ipynb
```

---

## 🧪 Experimental Setup

All experiments were conducted on a local machine with the following hardware and software specifications:

- **Device:** Acer Aspire A315-44P Laptop  
- **Processor:** AMD Ryzen 5 5500U (12 threads, ~2.1GHz)  
- **RAM:** 16 GB  
- **Operating System:** Windows 11 Pro (64-bit)  
- **Graphics:** DirectX 12 support  
- **Memory Management:** 38 GB page file  

This configuration offered a reliable and balanced environment for running machine learning models and genetic algorithm-based optimizations. It enabled medium-scale experimental workloads to be executed efficiently under constrained hardware resources.

---

### 📚 Citation
If you use this dataset, please cite:

Kousias, K., Rajiullah, M., Caso, G., Ali, U., Alay, Ö., Brunstrom, A., De Nardis, L., Neri, M., & Di Benedetto, M.-G. (2022).
A Large-Scale Dataset of 4G, NB-IoT, and 5G Non-Standalone Network Measurements.
DOI: 10.21227/7a8s-nt68

---

## 👤 Contributor
Developed and maintained by:

Onur Tuncay – Researcher in Machine Learning & NLP,  Senior Data Scientist and MSc Data Science Student at University of Gloucestershire

---

### 📝 License
This project is distributed under the MIT License.
Dataset is used under CC-BY 4.0 license.

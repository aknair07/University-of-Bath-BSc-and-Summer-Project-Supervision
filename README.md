# Domain-Based Preprocessing for Subject-Specific Clustering

This repository contains the code, datasets, and experiments from a research project supervised by myself at the University of Bath. The work investigates how **domain-based preprocessing** (such as tagging code excerpts and mathematical terms) affects the clustering of student questions using **Latent Dirichlet Allocation (LDA)** and the **Hierarchical Dirichlet Process (HDP)**.

The project corresponds to the paper:  
*“The Influence of Domain-Based Preprocessing on Subject-Specific Clustering”* (2020).  

---

## 📌 Project Overview

The rapid transition to online teaching during the Covid-19 pandemic resulted in an explosion of asynchronous student queries on platforms such as Teams, Blackboard, and Google Groups. Many queries were either duplicates or closely related, creating a heavy workload for academic staff.  

This project set out to explore whether **machine learning–based clustering** could reduce this burden by grouping similar questions together, enabling academics to respond more efficiently.  

Our research centred on:  
- **Text clustering using LDA** — a probabilistic topic modelling algorithm.  
- **Topic estimation using HDP** — a non-parametric Bayesian model that predicts the number of topics automatically.  
- **Domain-specific tagging** — identifying and tagging technical terms (e.g., code constructs like `for`, `if`, `while`, `print`, and mathematical terms like `BigO` and `modulo`) that would otherwise be discarded as stopwords.  

The experiments were run on a dataset of **~1300 questions and answers** from the University of Bath’s *Data Structures and Algorithms* module.  

The project explored both **tagged** and **untagged datasets**, multiple dataset permutations, and different HDP recursion strategies to assess how preprocessing influences clustering quality.  

---

## 📂 Repository Structure

```
University-of-Bath-BSc-and-Summer-Project-Supervision-main/
│
├── datasets/                # Raw and preprocessed student Q&A datasets
│   ├── questions_original.txt
│   ├── questions_tagged.csv
│   └── permutations/        # Randomised dataset versions for experiments
│
├── notebooks/               # Jupyter notebooks for experiments
│   ├── lda_clustering.ipynb
│   ├── hdp_topic_estimation.ipynb
│   ├── preprocessing_pipeline.ipynb
│   └── empirical_results.ipynb
│
├── scripts/                 # Python scripts for preprocessing & tagging
│   ├── text_to_csv.py
│   ├── tag_terms.py
│   └── utils.py
│
├── output/                  # Clustering results, figures, and logs
│
└── README.md                # Project overview (this file)
```

---

## ⚙️ Requirements

- Python 3.7+
- Key packages:
  - `pandas`
  - `gensim`
  - `nltk`
  - `matplotlib`
  - `scikit-learn`

Install dependencies with:

```bash
pip install -r requirements.txt
```

---

## 🚀 How to Reproduce

1. **Preprocess data**  
   - Convert raw `.txt` datasets into `.csv` using `text_to_csv.py`.  
   - Apply tagging with `tag_terms.py`.  

2. **Run notebooks**  
   - `preprocessing_pipeline.ipynb` → data cleaning and tagging steps.  
   - `hdp_topic_estimation.ipynb` → estimate optimal number of topics.  
   - `lda_clustering.ipynb` → perform clustering on both tagged and untagged datasets.  
   - `empirical_results.ipynb` → evaluate clustering efficiency and compare results.  

3. **Review outputs** in the `output/` folder, including topic distributions, visualisations, and comparison tables.  

---

## 📊 Summary of Findings

1. **Domain-based tagging improved clustering quality**:  
   - Clusters became more coherent when technical terms were preserved rather than discarded.  
   - Example: questions containing code excerpts were grouped more consistently after tagging `for`, `if`, `print`, `while`.  

2. **Mathematical tags clarified complexity-related queries**:  
   - Tagging `BigO` and `modulo` improved separation between clusters on runtime complexities, asymptotic notation, and hashing functions.  

3. **HDP-2 recursion provided better topic estimation**:  
   - One round of HDP (HDP-1) tended to under- or over-estimate topics.  
   - Two recursions (HDP-2) consistently yielded stable and more realistic estimates.  

4. **Tagged vs Untagged datasets**:  
   - Untagged datasets sometimes merged conceptually distinct queries (e.g., AVL trees with binary tree traversals).  
   - Tagged datasets achieved finer distinctions (e.g., separating AVL tree balancing questions into their own cluster).  

5. **Robustness**:  
   - Beyond tagging, LDA clustering remained stable across dataset permutations, showing reliability of the method.  

Overall, the results suggest that **domain-specific preprocessing is essential for clustering short, technical student queries** effectively.  

---

## 🔮 Future Directions

- Extend tagging methods to other specialised fields (e.g., legal or biomedical text).  
- Investigate automated detection of domain-specific terminology.  
- Integrate clustering models into real-time student support platforms to assist academic staff.  

---

## 📌 Acknowledgement

This repository was developed as part of undergraduate and summer projects at the University of Bath. A copy of our pre-print publication is available at: https://arxiv.org/abs/2011.08127

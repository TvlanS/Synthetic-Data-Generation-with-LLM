# LLM Generated Synthetic Data versus Real Data for Predicting Tuberculosis Treatment Duration

---

## Table of Contents

1. [Introduction](#introduction)
2. [Literature Review](#literature-review)
3. [Problem Statement](#problem-statement)
4. [Research Objectives & Research Questions](#research-objectives--research-questions)
5. [Research Methodology](#research-methodology)
6. [Results & Discussion](#results--discussion)
7. [Limitations & Recommendations](#limitations--recommendations)
8. [Conclusion](#conclusion)
9. [References](#references)
10. [Abbreviations](#abbreviations)

---

## Introduction

### Tuberculosis (TB) Overview


**What is TB:**
- A contagious **airborne disease** caused by *Mycobacterium tuberculosis*
- **Primarily affects the lungs** (pulmonary TB) but can also impact lymph, bones, and brain

**Global Impact:**
- **10.8 million new infections** estimated in 2023, **increased by 4.6%** from 2020
- **1.3 million deaths** worldwide *(WHO, 2023)*

**Treatment & Duration:**
- TB is **treatable** but may take **6–24 months** to treat; treatment duration is often unknown by patients or doctors *(CDC, 2023)*
- Continuous treatment is required to avoid **relapse risks**

**Why This Matters:**
- **Long treatment** increases **medical costs** and **physiological burden** to patients
- **Predictive tools are needed** for patient care planning and hospital management

---

### TB Variants and Treatment Duration

> **Definition:** Treatment Duration is the entire time frame between the first and last dose of anti-TB medication *(Paton et al., 2023)*. Treatment duration may vary from 6 months to 2 years depending on the TB category.

| TB Category | Key Characteristics | Treatment Duration |
|---|---|---|
| **Latent TB** *(CDC, 2023)* | Inactive infection; no symptoms; not contagious; can progress to active TB if untreated | Requires full treatment course |
| **Active TB** *(CDC, 2023)* | Has symptoms and is contagious; diagnosed through clinical and lab tests | Requires full treatment course |
| **Drug-Susceptible TB (DS-TB)** *(WHO, 2023)* | Drug-sensitive to first-line antibiotics; most common form globally | **6–9 months** |
| **Drug-Resistant TB (DR-TB)** *(Seung et al., 2015)* | Resistance to more than 2 primary drugs | **9–12 months** |

---

### Challenges of Real Data


> **Definition:** Real data in healthcare is patient information (e.g., clinical, imaging, genetic, demographic) collected from real-world clinical practice and maintained by healthcare institutions *(Qian et al., 2024)*.

**1. Lack of Public Datasets:**
- Privacy concerns often restrict access to real patient data, making it difficult to develop accurate models *(Törnqvist et al., 2025)*

**2. Small Datasets:**
- Imbalanced and small datasets, where some classes of data (e.g., patient groups with longer treatment durations) are underrepresented, can affect the performance of machine learning models *(Kim et al., 2024)*

**3. Logistic Issues:**
- Challenging data acquisition due to platform limitations and the prioritization of daily operational tasks over dataset development *(Rashidi et al., 2022)*

> These challenges hinder data acquisition for TB treatment duration, limiting the development of effective TB duration prediction models.

---

## Literature Review

### Synthetic Data Generation

> **Definition:** Synthetic data are data that are artificially generated to simulate the statistical properties and patterns of real-world data while preserving the privacy of individuals whose data would have been used, and with high utility *(Qian et al., 2024)*.

**Popular Models for Synthetic Tabular Data Generation in Healthcare:**

| Method | Description | Examples |
|---|---|---|
| **Probabilistic Models** *(Greenberg et al., 2023)* | Utilize probabilistic graphical models to model relationships between variables | Bayesian Networks, Gaussian Copulas |
| **Generative Adversarial Networks (GANs)** *(Beaulieu-Jones et al., 2019)* | Use a generator and discriminator to synthesize realistic tabular data | CTGAN, MedGAN, VeeGAN, TableGAN |
| **Variational Autoencoders (VAEs)** *(Kim et al., 2024)* | Encode input data into a probabilistic latent space and decode it back to reconstruct new data | TVAE (Tabular Variational Autoencoder) |

**Limitations of Traditional Approaches:**
- Computationally intensive *(Tornqvist et al., 2025)*
- Requires training data *(Tornqvist et al., 2025)*
- Requires large training datasets (5k–10k rows); more features = larger dataset needed
- Complex to implement and tune *(Smolyak et al., 2024)*
- Over-generalization and mode collapse *(Nagesh et al., 2025)*
- Difficult to model high-dimensional dependencies *(Lin et al., 2025)*

---

### LLM as Synthetic Data Generator

> **Definition:** A Large Language Model (LLM) is an advanced artificial intelligence system based on transformer architecture that is trained on massive text and tabular datasets to understand, generate, and reason with human language *(Wang et al., 2024)*.

LLM has been proven to **outperform probabilistic models, VAEs, and GAN models** in generating synthetic datasets in the healthcare domain, with overall best performance in terms of **Fidelity, Privacy, and Utility** *(Tornqvist et al., 2025; Fang et al., 2024)*.

**Advantages of LLM as Synthetic Tabular Data Generator** *(Barr et al., 2025; Ilaty et al., 2025; Lin et al., 2025)*:
- **Captures complex relationships** between features
- Relatively **lower complexity** to generate data
- **Faster** in generating data when commercial LLMs are used
- **Cleaned data** can be produced, eliminating the need for data cleaning
- Generates data with **small data sample or no sample**

---

### Real Data vs Synthetic Data Evaluation

Real vs synthetic data studies systematically evaluate how well synthetic datasets replicate the statistical properties (fidelity), privacy, and predictive utility of real-world data to gauge the feasibility of using synthetic data for practical applications.

| Metric | Function | Measures |
|---|---|---|
| **Fidelity** *(Xu et al., 2019; Greenberg et al., 2023; Wang et al., 2024)* | Gauge whether relational interdependence among features are retained and data has similar statistical distribution | Wasserstein Distance (WS), Inverse KL Divergence (IKL), Hamming Distance (HD) |
| **Privacy** *(Qi et al., 2024; Greenberg et al., 2023; Wang et al., 2024)* | Measures the risk of re-identification or leakage of sensitive information when data are shared based on data point similarity | k-Anonymity (KA), Nearest Neighbor Distance Ratio (NNDR), Membership Advantage (MA) |
| **Utility** *(Xu et al., 2019; Perets et al., 2025; Qi et al., 2024)* | Refers to how useful synthetic data are for downstream tasks such as training, validation, or clinical prediction | Area Under Curve (ROCAUC), Brier Score (Brier), F1 Score (F1) |

---

## Problem Statement

**1. Limited studies investigating TB duration prediction:**
- There are limited studies focusing on TB treatment duration. Existing studies use small datasets *(Balakrishnan et al., 2024)*. Other studies in TB primarily focus on TB diagnosis, TB incident prediction, and TB treatment success likelihood *(e.g., Chen et al., 2024; Yasir et al., 2024; Luo, 2023)*

**2. No studies have tested the feasibility of generating synthetic TB-related datasets with LLMs:**
- While LLMs have been applied to synthetic data generation in healthcare, existing studies *(e.g., Ilaty et al., 2025; Wang et al., 2024)* focus mainly on domains such as diabetes, leaving TB-related applications unexplored

---

## Research Objectives & Research Questions

| | Research Objective | Research Question |
|---|---|---|
| **RO 1 / RQ 1** | To generate TB prediction duration dataset with commercial LLM using prompt engineering | How to generate a TB dataset using commercial LLM through prompt engineering? |
| **RO 2 / RQ 2** | To test the fidelity and privacy of the synthetic data against the real TB dataset | What is the fidelity and privacy of LLM-generated synthetic data compared to the real TB dataset? |
| **RO 3 / RQ 3** | To develop a TB treatment duration prediction model using real and synthetic data | What steps are involved in developing a TB treatment duration prediction model using real and synthetic data? |
| **RO 4 / RQ 4** | To evaluate the performance of the machine learning model developed with synthetic data against a model developed with real TB data | How does a machine learning model developed with synthetic data compare with models built with the real TB dataset? |

---

## Research Methodology

### Methodology Flowchart

The research is structured across 5 phases:

- **Phase 1 — Real Data:** Data collection and preprocessing from UMMC
- **Phase 2 — Synthetic Data:** Synthetic dataset generation via LLM prompting
- **Phase 3 — Exploratory Data Analysis:** Fidelity and privacy testing
- **Phase 4 — Modelling:** ML model training, hyperparameter tuning, and utility testing
- **Phase 5 — Model Performance Evaluation:** Comparison of real vs synthetic model performance

--

### Phase 1: Real Dataset

| Attribute | Details |
|---|---|
| **Source** | University of Malaya Medical Centre (UMMC), Kuala Lumpur, Malaysia |
| **Records** | 1,182 patients with 110 features |
| **Data Period** | January 1, 2018 – September 30, 2021 |
| **Dataset Format** | Mix of categorical (integer-encoded) and continuous (integer or float) features |

### Phase 2: Synthetic Data Generation — LLM Model

**LLM Model Selected: ChatGPT-5.1 Plus**

Rationale:
- ChatGPT **outperforms** other primary commercial LLM models (Gemini Pro, Claude, Co-Pilot) in **understanding tuberculosis concepts** *(Dastani et al., 2025; Chiu et al., 2025)*
- **Superior performance** at generating tabulated data compared to Claude 3, Gemini Pro, and Mistral *(Barr et al., 2025)*
- **1,182 patients with 8 features** will be generated, mirroring the baseline study by *(Balakrishnan et al., 2024)*

---

### Phase 2: Prompting Configurations

Three prompting configurations are tested to simulate different real-world data availability scenarios:

| Acronym | Description | Prompt Content | Scenario |
|---|---|---|---|
| **Prompt F** | Few-shot prompting without sample | Boilerplate prompt (file type, size, column names & descriptions) + min/max range for target variable | Generated when **no real dataset** is available |
| **Prompt FT** | Few-shot prompting with few table samples | Boilerplate prompt + statistical properties (min, max, median, Q1, Q2) + 12-row data sample + images of data distribution (KDE plot, boxplot, bar chart) | Generated when real data is available **without public access** to the full table |
| **Prompt FT+** | Few-shot prompting with full table | Same as Prompt FT with the **full table** instead | Generated for **data augmentation** or **privacy preservation** |

---

### Phase 3: Fidelity Testing

#### Univariate Methods

**Wasserstein Distance** *(Continuous Features)*:
- Measures the minimum "work" to transform one distribution into another *(Ilaty et al., 2025)*
- Quantitatively measures the difference in data distribution of continuous features
- **Lower value → More similar distribution** (0 = identical)

$$W(P,Q) = \int_{-\infty}^{\infty} |F_P(x) - F_Q(x)| \, dx$$

**Kullback–Leibler Divergence** *(Categorical Features)*:
- Measures how one probability distribution diverges from a reference *(Kullback & Leibler, 1951)*
- Quantitatively compares real vs synthetic data distributions for categorical features
- **Lower value → More similar distributions** (0 = identical)

$$D_{KL}(P|Q) = \sum_i P(i) \log \frac{P(i)}{Q(i)}$$

---

**Spearman Correlation** *(Categorical Features)*:
- Compares the rank-order pattern between two variables
- **Higher value → More similar pattern** (1 = identical, −1 = opposite)

$$\rho = 1 - \frac{6\Sigma d_i^2}{n(n^2 - 1)}$$

where $d_i = Rank_{real} - Rank_{synthetic}$

**MAE of Mean Value** *(Continuous + Categorical Features)*:
- Measures the difference in mean value of classes
- **Lower value → More similar distribution** (0 = identical)

$$MAE_{mean} = |Mean_{real} - Mean_{synthetic}|$$

---

#### Multivariate Methods

**Correlation Similarity:**
- Compares synthetic and real data inter-feature dependencies *(Kim et al., 2024)*

**Measurement Steps:**
1. Compute correlation matrix of synthetic and real data using Pearson correlation
2. Compare matrices using Mean Absolute Error (MAE)

A **Weighted MAE** is used to penalize cases where desired synthetic data correlations are not statistically significant:

$$e_i = \begin{cases} |r_i^{real} - r_i^{syth}|, & \text{if } p_i^{syth} \leq 0.05 \\ 1, & \text{if } p_i^{syth} > 0.05 \end{cases} \quad MAE_{punished} = \frac{1}{n} \sum_{i=1}^{n} e_i$$

---

### Phase 3: Privacy Testing

**Nearest Neighbor Distance Ratio (NNDR):**
- Measures whether synthetic records are too close to real records, indicating potential privacy leakage *(Tornqvist et al., 2025)*

**Measurement Steps:**
1. For each synthetic record, compute distances to its nearest and second-nearest neighbors in the real dataset
2. Calculate: `NNDR = (distance to nearest) ÷ (distance to 2nd nearest)`
3. Analyze distribution of NNDR scores across all synthetic records

- **Low NNDR (< 0.2)** → Privacy Risk (synthetic record nearly identical to a real one)
- **NNDR > 0.25** → Privacy Preserved

---

### Phase 4: Utility Testing

Three training-testing schemes are used for utility evaluation:

| Training & Testing Method | Function |
|---|---|
| **Train Real, Test Real (TRTR)** | Baseline Performance |
| **Train Synthetic, Test Synthetic (TSTS)** | Evaluate if synthetic dataset has coherent patterns |
| **Train Synthetic, Test Real (TSTR)** | Evaluate generalization of model trained on synthetic data |

**ML Models Used** *(Balakrishnan et al., 2024)*:
- Linear Regression
- Ridge Regression
- Lasso Regression
- Gradient Boosting
- Support Vector Regression (SVR)
- Random Forest

**Hyperparameter Tuning:** Random Search  
**Train/Test Split:** 70% Training / 30% Testing  
**Evaluation Metrics:** MAE, RMSE, R²

---

## Results & Discussion

### Fidelity Testing: Treatment Duration (Continuous Feature)

| Prompt | Wasserstein Distance | MAE (Feature Mean Difference) |
|---|---|---|
| **F** | 34.387 | 23.513 |
| **FT** | 32.573 | 13.406 |
| **FT+** | **17.087** | **7.988** |

**Key Findings:**
- Both **FT & FT+** captured the small bimodal peak in the distribution, indicating GPT has successfully interpreted the statistical images
- **FT+** has the smallest Wasserstein Distance and closest mean value to the real data — **most similar data distribution**
- **Performance Order: FT+ → FT → F**

---

### Fidelity Testing: Discrete Features


| Attributes | KL Divergence F/FT/FT+ | Spearman Correlation F/FT/FT+ | MAE F/FT/FT+ | Best Prompt |
|---|---|---|---|---|
| Treatment Outcome | 0.190 / 0.000 / 0.008 | 0.448 / 0.981 / 0.848 | 69.604 / 14.770 / 20.446 | **FT** |
| Fixed Dose Combination (FDC) | 0.005 / 0.000 / 0.005 | 0.333 / 0.333 / 1.000 | 29.335 / 12.210 / 7.060 | **FT+** |
| Levofloxacin-based Regimen | 0.011 / 0.000 / 0.004 | 1.000 / 1.000 / 1.000 | 57.044 / 11.604 / 3.441 | **FT+** |
| Maintenance Phase Regime Isoniazid | 0.165 / 0.000 / 0.002 | 0.333 / 0.333 / 1.000 | 46.691 / 59.803 / 31.243 | **FT+** |
| Where was the Treatment Started | 0.004 / 0.000 / 0.001 | 0.333 / 1.000 / 1.000 | 30.624 / 14.786 / 2.559 | **FT+** |
| Chest X-ray CXR Findings | 0.155 / 0.000 / 0.004 | −0.833 / −0.167 / 0.767 | 49.254 / 16.915 / 12.077 | **FT+** |

**Key Findings:**
- **FT+** displays best statistical fidelity performance in **80%** of features (lowest KL, lowest MAE, highest Spearman)
- **Performance Order: FT+ → FT → F**

---

### Fidelity Testing: Correlation Similarity


| Prompt | Insignificant Features | Pearson MAE | Weighted Pearson MAE |
|---|---|---|---|
| **F** | 1 | 0.155 | 0.299 |
| **FT** | 5 | 0.096 | 0.801 |
| **FT+** | **1** | **0.026** | **0.189** |

**Key Findings:**
- **FT+** displays best statistical fidelity performance (lowest MAE and fewest insignificant features)
- **Prompt FT** is the weakest at capturing the linear relationship between features and target — having 5 insignificant features resulting in a heavily penalized weighted MAE
- **Performance Order: FT+ → F → FT**

---

### Fidelity Testing: Overall Summary


| Prompt | WD | MAE (Mean) | KL Divergence | Spearman | MAE (Discrete) | Weighted Pearson MAE | Total Score |
|---|---|---|---|---|---|---|---|
| **F** | 1 | 1 | 1 | 1 | 1 | 2 | **7** |
| **FT** | 2 | 2 | 3 | 2 | 2 | 1 | **12** |
| **FT+** | 3 | 3 | 2 | 3 | 3 | 3 | **19** |

*Scoring: 1st place = 3 pts, 2nd = 2 pts, 3rd = 1 pt*

> **Overall Performance Order: FT+ → FT → F**

---

### Privacy Testing: NNDR Results

| Prompt | NNDR Score | Privacy Status |
|---|---|---|
| **F** | 0.56 | ✅ Preserved |
| **FT** | 0.41 | ✅ Preserved |
| **FT+** | 0.43 | ✅ Preserved |

**Key Findings:**
- **All 3 prompts preserve privacy** (NNDR > 0.25 = privacy preserved)
- Highest privacy preservation is seen in **Prompt F** (NNDR = 0.56), which is expected as it has no exposure to real data
- **Prompt FT+** shows only a **2% variance** from Prompt FT, while the gap with F is larger at 14%
- **Performance Order (Privacy): F → FT+ → FT**

---

### Utility Testing: TSTS Modelling


| Prompts | Best Model | R² | MAE | RMSE |
|---|---|---|---|---|
| **Real (Baseline)** | Gradient Boosting | 0.385 | 66 | 100 |
| **F** | Linear Regression | 0.376 ↓ | 68 ↓ | 91 ↑ |
| **FT** | Gradient Boosting | **0.538** ↑ | **51** ↑ | **66** ↑ |
| **FT+** | Random Forest | 0.442 ↑ | 70 ↓ | 95 ↑ |

*↑ = Improved performance relative to real dataset; ↓ = Decreased performance*

**Key Findings:**
- **Performance Order: FT → FT+ → F**
- MAE Change (days): FT: −15, FT+: +4, F: +2
- RMSE vs MAE spread: Real: +51%, FT: +29%, FT+: +35%, F: +33%
- All prompt datasets show **coherent patterns**
- TSTS performance is **not conclusive** of overall utility performance

---

### Utility Testing: TSTR Modelling


| Prompts | Best Model | R² | MAE | RMSE |
|---|---|---|---|---|
| **Real (Baseline)** | Gradient Boosting | 0.385 | 66 | 100 |
| **F** | SVR | 0.150 ↓ | 85 ↓ | 117 ↓ |
| **FT** | Gradient Boosting | 0.366 ↓ | 67 ↓ | 101 ↓ |
| **FT+** | Random Forest | **0.376** ↑ | **66** — | **100** ↑ |

*↑ = Improved performance relative to real dataset; ↓ = Decreased performance*

**Key Findings:**
- **Performance Order: FT+ → FT → F**
- MAE Change (days): FT+: < −1, FT: +1, F: +19
- RMSE vs MAE spread: Real: +51%, FT+: +50%, FT: +51%, F: +37%
- **Prompt FT+ can be used in real applications** — its TSTR performance is virtually identical to TRTR with only a **0.6% difference overall**

---

## Limitations & Recommendations


**Limitations:**
- The GUI version of ChatGPT is **non-deterministic**, resulting in inconsistent output for every generation
- Risk of **data leakage** from higher-level prompts to lower-level prompts (e.g., Prompt FT+ to Prompt FT), as ChatGPT GUI carries memory from one query window to another
- **Small number of features** used in this study (6 features)

**Recommendations:**
- Use the **ChatGPT API** with `temperature = 0` to isolate queries from one another and achieve more consistent outputs
- Conduct the study with a **dataset with more significant features** to further validate the findings

---

## Conclusion

- This study addresses the **limited research on tuberculosis (TB) treatment duration prediction** and explores the feasibility of applying LLMs for synthetic dataset generation for TB-related studies.

- The main objective was to generate TB prediction duration datasets with **ChatGPT-5.1 Plus**, evaluate fidelity, privacy, and utility against real-world data, and build predictive models.

- **Fidelity results** show a clear improvement as more information is provided to the LLM — **Prompt FT+ achieved the highest statistical similarity** to the real dataset, followed by Prompt FT and Prompt F.

- **Privacy evaluation** using NNDR shows that **all three prompting configurations preserve patient privacy**, with no critical re-identification risk observed.

- **All prompts generate coherent patterns** based on TSTS findings.

- **Prompt FT+ achieved the best overall utility** (R²: 0.376, MAE: 66, RMSE: 100) with TSTR performance comparable to a model trained on real data, with only a **0.6% overall difference**, indicating strong generalization capability and real-world applicability.

- It is recommended to conduct the research using the **ChatGPT API with temperature = 0** and a **dataset with more significant features** to further validate these findings.

---

## Abbreviations

| Abbreviation | Full Form |
|---|---|
| AUC | Area Under the Curve |
| Brier | Brier Score |
| CDC | Centers for Disease Control and Prevention |
| COR | Correlation Similarity |
| CTGAN | Conditional Tabular Generative Adversarial Network |
| CXR | Chest X-Ray |
| DCR | Distribution Coverage Ratio |
| DPGAN | Differentially Private Generative Adversarial Network |
| DR-TB | Drug-Resistant Tuberculosis |
| DS-TB | Drug-Susceptible Tuberculosis |
| F | Few-shot prompting without sample |
| F1 | F1 Score |
| FDC | Fixed Dose Combination |
| FT | Few-shot prompting with few table samples |
| FT+ | Few-shot prompting with full table |
| GAN | Generative Adversarial Network |
| GC | Gaussian Copula |
| GPT | Generative Pre-trained Transformer |
| HD | Hellinger Distance |
| HIV | Human Immunodeficiency Virus |
| HPT | Hyperparameter Tuning |
| IKL | Inverse Kullback–Leibler Divergence |
| KA | k-Anonymity |
| KL | Kullback–Leibler Divergence |
| KSV | Kolmogorov–Smirnov Value |
| LLM | Large Language Model |
| MA | Membership Advantage / Mean Accuracy |
| MAE | Mean Absolute Error |
| MIMIC III | Medical Information Mart for Intensive Care III |
| NNDR | Nearest Neighbor Distance Ratio |
| PCR | Polymerase Chain Reaction |
| ROCAUC | Area Under the Receiver Operating Characteristic Curve |
| RQ | Research Question |
| SVR | Support Vector Regression |
| TB | Tuberculosis |
| TRTR | Train Real Test Real |
| TSTR | Train Synthetic Test Real |
| TSTS | Train Synthetic Test Synthetic |
| TVAE | Tabular Variational Autoencoder |
| TVC | Total Variation Correlation |
| UMMC | University of Malaya Medical Centre |
| VAE | Variational Autoencoder |
| WHO | World Health Organization |
| WS | Wasserstein Distance |

---

*This research was conducted using real TB patient data from the University of Malaya Medical Centre (UMMC), Kuala Lumpur, Malaysia.*

# Project: Track A – Data & AI - AWS Cloud Cost Analysis

📋 **Description**

This project, developed as part of Track A – Data & AI of ICT Itaú, creates a data ingestion and processing pipeline in Python using public AWS instance pricing data. It includes a machine learning model (linear regression) to predict costs (Linux on-demand price per hour) and exploratory analysis to identify usage patterns. The goal is to support strategic decision-making related to cloud costs.

👤 **Author**

Name: Lucas de Souza Lima

🎯 **Objectives**

* Develop a pipeline to ingest, clean, and analyze AWS instance pricing data.
* Apply linear regression to predict costs based on resources such as vCPUs, memory, storage, and GPUs.
* Perform exploratory data analysis with visualizations and descriptive statistics.
* Generate deliverables as specified (commented code, notebook, processed CSV, plots).

📂 **Project Structure**

* `Pipeline_Lucas_Lima.ipynb`: Jupyter Notebook with the ingestion pipeline, data cleaning, exploratory analysis, and visualizations.
* `regressão.ipynb`: Notebook with the machine learning model (linear regression) and evaluation.
* `aws_pricing_tratado.csv`: CSV file containing processed data after cleaning.
* `images/`: Directory with generated plots (e.g., Prediction vs Actual, Feature Importance).
* `README.md`: This documentation file.

🚀 **Functionalities**

* **Ingestion & Processing**: Loads and cleans missing values from the AWS dataset, saving results to `aws_pricing_tratado.csv`.
* **Exploratory Analysis**: Generates statistical summaries and visualizations (histograms, correlations) for resources such as vCPUs, memory, and GPUs.
* **Machine Learning Model**: Uses linear regression to predict Linux on-demand hourly price, evaluated with R² and RMSE.
* **Visualizations**: Includes prediction vs actual plots and feature importance charts.

## 📊 Results

### Exploratory Analysis

* **Resource Distribution:**

  * **vCPUs:** Concentrated in lower values (0–100), with a long tail up to 800 vCPUs, indicating high-performance instances for HPC and big data.
  * **Memory (memorySizeInGiB):** Mostly up to 5,000 GiB, but with extremes reaching 32 TiB, optimized for in-memory databases and machine learning.
  * **GPUs (gpuCount):** Predominantly 0 GPUs, with rare cases up to 8 GPUs, targeted at Deep Learning and rendering workloads.
  * **Total GPU Memory (gpuTotalGpuMemoryInGiB):** Almost all instances have 0 GiB, but some reach 1,400 GiB, suitable for large AI models.
  * **Network Interfaces (maxNetworkInterfaces):** Peaks between 2–15 ENIs, with up to 80 in highly scalable instances.

* **Statistical Summary:**

  * **vCPUs:** Mean 41.8, median 16, max 896.
  * **Memory:** Mean 272.8 GiB, median 96 GiB, max 32 TiB.
  * **Storage:** Mean 2,469.4 GB, median 0 GB, max 335 TB.
  * **GPUs:** Mean 0.12, median 0, max 8.
  * **ENIs:** Mean 8.3, median 8, max 80.

* **Initial Insights:** Most instances are basic (low CPU, moderate memory, no GPU), but there are specialized options for intensive computing, AI, and scalable networking.

### Correlation with Linux On-Demand Price

* **vCPUs vs Price:** Strong correlation (0.77), highlighting vCPUs as a cost driver.
* **RAM vs Price:** Very strong correlation (0.94), the most determining factor.
* **Storage vs Price:** Weak correlation (0.14), indicating costs are mostly separate (via EBS).
* **GPUs vs Price:** Weak correlation (0.23), with impact depending on the instance family.
* **Correlation Conclusion:** Pricing is dominated by CPU and memory, while storage and GPUs have secondary influence.

### Machine Learning Model

* **Linear Regression:**

  * **Target:** Linux on-demand hourly price (`onDemandLinuxHr`).
  * **Features:** `vCpus`, `memorySizeInGiB`, `storageTotalSizeInGB`, `gpuCount`.
  * **Performance:**

    * **R²:** 0.9303 (93% of price variability explained).
    * **RMSE:** 6.96 (low average error relative to price scale).
  * **Coefficients:**

    * `gpuCount`: 1.765 (highest impact).
    * `vCpus`: 0.0242.
    * `memorySizeInGiB`: 0.0092.
    * `storageTotalSizeInGB`: 0.000039 (minimal impact).

* **Visualizations:**

  * **Prediction vs Actual:** Plot shows close alignment between predicted and actual values, with the perfection line indicating good accuracy.
  * **Feature Importance:** `gpuCount` stands out as the main driver, followed by `vCpus` and `memorySizeInGiB`, confirming the correlation analysis.

### Overall Conclusion of Results

The pipeline demonstrated that:

* Most AWS instances serve basic workloads, but there are niches for high-performance (HPC, AI, intensive networking).
* Linear regression predicts costs with high accuracy (R² = 0.93), validating CPU, memory, and GPUs as primary cost drivers.
* Storage has negligible impact on on-demand pricing, aligned with AWS’s billing policies.

🛠️ **Technologies Used**

* **Language:** Python
* **Libraries:** pandas, numpy, seaborn, matplotlib, scikit-learn
* **Tools:** Jupyter Notebook, Git

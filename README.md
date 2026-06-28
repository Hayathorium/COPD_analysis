# A Bayesian Hierarchical Approach to Estimating PM2.5 Effects on COPD Prevalence

This repository contains the data, methodology, and analysis for the study titled **"A Bayesian Hierarchical Approach to Estimating PM2.5 Effects on COPD Prevalence Across the United States."**

## Key Findings

* **Strong Associations**: Posterior inference indicates positive associations between COPD prevalence and smoking rates ($\mathbb{E}[\beta_1] = 0.165$) and diabetes prevalence ($\mathbb{E}[\beta_2] = 0.460$).
* **Model Performance**: The hierarchical model (RMSE = 0.5617) significantly outperforms naive linear regression extrapolation (RMSE = 0.7767) in predicting 2020 COPD prevalence.
* **State-Level Diversity**: Large variations in state-specific latent effects ($u_i$) were observed, likely reflecting regional factors such as historical coal mining legacies in Appalachia and differences in ethnic composition.

## Data Sources

The analysis utilizes data from the following public health and census sources:

* **COPD Prevalence & Smoking/Diabetes Rates**: [Behavioral Risk Factor Surveillance System (BRFSS)](https://www.cdc.gov/brfss/)
* **Poverty Rates**: [U.S. Census Bureau (American Community Survey)](https://www.census.gov/programs-surveys/acs)
* **PM$_{2.5}$ Concentrations**: [National Environmental Public Health Tracking Network](https://www.google.com/search?q=https://www.cdc.gov/nceh/tracking/)

## Model Specification

To capture the persistent nature of COPD prevalence at the state level, we utilize the following Bayesian hierarchical structure:

$$Y_i = u_i + \beta_0 + \beta_1 X_1^i + \beta_2 X_2^i + \beta_3 X_3^i + \beta_4 X_4^i + \beta_5 (X_4^i)^2 + \epsilon$$

Where:

* $u_i \sim \mathcal{N}(0, \sigma_u)$ represents the state-specific latent effect.
* $\epsilon \sim \mathcal{N}(0, \sigma_Y)$ represents residual variation.

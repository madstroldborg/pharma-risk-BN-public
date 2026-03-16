## Pharmaceutical Risk Modelling using Bayesian Network
This repository accompanies the analysis for the manuscript (in preparation):
**“Probabilistic modelling of pharmaceutical pollution risk from sewage treatment work discharges using a Bayesian Network: application to a Scottish river catchment”**

It contains the Bayesian Network model (built in GeNIe software) as well as the R code and the processed input datasets (where shareable) required for running the model. The repository also contains Excel files with the excretion fraction data and wastewater removal efficiency data collated from literature.

### Citation
If you use this code or the associated datasets in your research, please cite:

Troldborg, M. et al. (2026). Probabilistic modelling of pharmaceutical pollution risk from sewage treatment work discharges using a Bayesian Network: application to a Scottish river catchment. *Water Research*. (submitted)

A preprint version of the paper is available at: [https://doi.org/10.31223/X5048T] 

---

### Project Overview

The analysis consists of the following main components:

1. **NHS Prescription Data**
   - Downloading and processing monthly prescription data for selected pharmaceuticals.
   - Aggregation and visualisation (e.g. histograms of prescription volumes).
   - **Note:** The code for this step is not included in this repository, but can be made available on request. The processed prescribing data is shared in `Data/processed`.

2. **Wastewater Treatment Works (WWTW) Data**
   - Processing catchment specific wastewater treatment work (WWTW) data and summarising into the format used in BN model.
   - **Note:** The code for this step is can be made available on request. Execution of this step requires access to Scottish Water WWTW data, not shared as part of this repository. However, the processed data required to run the BN model is shared in `Data/processed`. 

3. **Flow Data**
   - Loading and processing river flow data.
   - Derivation of flow statistics required for BN modelling.
   - **Note:** The code for this step can be made available on request. Execution of this step requires access to river flow timeseries for each monitoring point considered; these are not shared as part of this repository. However, the processed flow data (for the current climate scenario) required to run the BN model is shared in `Data/processed`. 

4. **Excretion Fractions**
   - Processing literature-derived excretion fraction datasets.
   - Visualisation of excretion fractions as boxplots by compound.
   - **Note:** The Excel file with the excretion fraction data is shared in `Data/raw`. The processed excretion data have been built into the BN model as fitted beta probability distributions, shared in `Data/model`. The code for the processing and visualisation can be made available on request. 

5. **Wastewater treatment work removal efficiencies**
   - Processing wastewater influent and effluent data to estimate removal efficiencies.
   - Integration with literature-reported removal rates.
   - Removal efficiencies visualised as boxplots by compound and treatment category.
   - **Note:** The Excel file with the removal efficiency data is shared in `Data/raw`. The processed removal efficiency data have been built into the BN model as fitted beta probability distributions, shared in `Data/model`. The code for the processing and visualisation can be made available on request. However, execution of this step requires access to data from the UK Chemical Investigation Programme (CIP); these are not shared as part of this repository. 

6. **Bayesian Network Pharmaceutical Risk Model**
   - Implementation of a BN model (built in GeNIe software) via the `rSMILE` package.
   - Inputs include processed prescription data, flow data, wastewater removal data,
     excretion fractions, and sewage treatment works (STW) population equivalents.
   - Outputs include simulated pharmaceutical concentrations and risk metrics.
   - **Note:** The BN model is shared in `Data/model`. However, execution of this step requires licensed GeNIe software (free for academic use) and an rSMILE license and cannot be fully reproduced from this repository alone.

7. **Comparison of Simulated and Observed Data**
   - Processing of observed environmental concentration data.
   - Quantitative comparison of simulated vs observed concentrations.
   - Generation of all manuscript figures comparing observations and simulations.
   - **Note:** Execution of this step requires access to observed concentration data from the catchment, not shared as part of this repository. The processing scripts can be made available on request.

---

### 📁 Repository Structure
```
pharma-risk-BN-public/
├── README.md
├── .gitignore
├── LICENSE
├── renv.lock
├── renv/
├── R/
│ ├── rSMILE_run_pharma_bn.Rmd
│ └── utils.R
├── data/
│ ├── raw/
│ │ └── (shareable input data)
│ ├── processed/
│ │ └── (generated intermediate datasets)
├── Data_private/
│ └── (restricted / licensed data; not tracked by git)
└── Outputs/
  └── figures/
```

- **NOTE:** The `Data_private/` directory is intentionally excluded from version control. In order to run the model script, an rSMILE license needs to be obtained and placed in this folder. SMILE license keys can be obtained from https://download.bayesfusion.com/. 

---


### 📦 Reproducible R Environment

This project uses the `{renv}` package to ensure reproducibility of the R environment.

To install required packages:

```r
install.packages("renv")
renv::restore()
```

This will install the exact package versions used in the original analysis.


---


### 🧠 Bayesian Network Model (rSMILE / GeNIe)

The BN model is implemented using the rSMILE R package, which interfaces with
the GeNIe Modeler software.

GeNIe is proprietary software and requires a valid license, but is free to use for academics. It can be downloaded from https://download.bayesfusion.

A license for rSMILE is required in order to read the BN model in R. SMILE license keys can be obtained from https://download.bayesfusion.com/. 


---

### 📜 License

This code is released under the MIT License. See `LICENSE` for details.


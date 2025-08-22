# Bias Correction of Climate Projection Data

<p align="center">
  <b>Hajar BADRAOUI</b> <br>
  Data Analyst Intern @ ARVALIS – 2025
</p>

---

## 🌾 Project Context – CLIMODIF

This repository was developed during my master’s internship at ARVALIS – Institut du végétal, within the framework of the **CLIMODIF** project (“Climatic change, modelling and adaptation of cropping systems”).  
**CLIMODIF** aims to provide the agricultural sector with robust, actionable climate intelligence by producing, correcting, and distributing high-resolution climate projections for France.  
A key challenge addressed in this project is the **systematic bias** present in raw outputs from regional climate models, which can distort the estimation of risks and the design of adaptation strategies for crops and agricultural practices.



## 🧑‍💻 Motivation & Objectives

Climate model outputs (e.g., from EURO-CORDEX) often exhibit statistical biases when compared to observations or high-resolution reanalysis (like SAFRAN).  
These biases can lead to **incorrect assessments of future climatic risks**, affecting both operational decisions and research.

**This project aims to:**
- **Evaluate and compare** state-of-the-art bias correction methods, focusing on univariate (CDF-t) and multivariate (dOTC) approaches.
- **Quantify the improvements** provided by each method for key agro-climatic variables at the station scale.
- **Deliver a reproducible and automated workflow** for generating bias-corrected climate projections usable by researchers, agronomists, and decision-makers.



## 🛠️ Methods

Bias correction is performed with the [SBCK](https://github.com/yrobink/SBCK) Python library, which implements:
- **CDF-t** (Cumulative Distribution Function transform): univariate, distribution-based adjustment to match reference data.
- **dOTC** (distributional Optimal Transport Correction): multivariate, optimal transport-based adjustment, preserving inter-variable dependencies.

**Workflow:**
- Extraction of daily historical and projected climate data (1976–2100) for 40 meteorological stations across France.
- Correction of the following variables: precipitation (`pr`), wind speed (`sfcWind`), minimum/maximum temperature (`tasmin`, `tasmax`), relative humidity (`hurs`), solar radiation (`rsds`), potential evapotranspiration (`ETP`).
- Monthly correction applied on moving 30-year windows, ensuring stability and robustness of the correction across climate regimes.
- Application of specific post-processing for precipitation (log-exp, SSR).



## 📊 Value Added & Outcomes

- **Rigorous comparative analysis**: Detailed evaluation of CDF-t vs dOTC for marginal (mean, variance) and joint (correlation, dependency) statistics.
- **Trend preservation**: Cross-validation and regression analyses demonstrating the ability of corrections to preserve climate model trends—crucial for robust scenario analysis.
- **Operational transferability**: The code and workflows are designed for easy extension to new stations, variables, or regions.
- **Enhanced data quality for agriculture**: Results directly support the development of reliable agro-climatic indicators and risk assessment tools for stakeholders.
- **Open science and reproducibility**: All code, data processing steps, and analyses are documented and reproducible for the research and agricultural communities.

## 📚 References

- Robin, Y., Corre, L., Marson, P., Bernus, S., Vrac, M., & Thao, S. (2024). [Projections climatiques régionalisées : correction de biais et changements futurs](https://doi.org/10.57745/KXRB5B)
- [SBCK documentation](https://sbck.readthedocs.io/en/latest/)
- SAFRAN reanalysis: [Météo-France SAFRAN](https://opensource.umr-cnrm.fr/projects/safran)

---

## 👤 Author & Contact

**Hajar BADRAOUI**  
M2 Applied Statistics & Decision Analysis  
Université de Caen Normandie, France  
Data Analyst Intern @ ARVALIS  
📧 hajar.badraoui01@gmail.com  
🔗 [github.com/badraouihajar](https://github.com/badraouihajar)


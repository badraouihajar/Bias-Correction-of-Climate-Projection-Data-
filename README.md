# Bias Correction of Climate Projection Data

<p align="center">
  <b>Hajar BADRAOUI</b> <br>
  Data Analyst Intern @ ARVALIS – 2025
</p>

---

## 🌾 Project Context – CLIMODIF

This repository was developed during my master’s internship at ARVALIS – Institut technique agricole, within the framework of the **CLIMODIF** project.  
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
- Robin, Y., Vrac, M., Naveau, P., & Yiou, P. (2019). [Multivariate stochastic bias corrections with optimal transport. *Hydrology and Earth System Sciences*, 23(2), 773–786.](https://hess.copernicus.org/articles/23/773/2019/)
- François, B., Vrac, M., Cannon, A.J., Robin, Y., & Allard, D. (2020). [Multivariate bias corrections of climate simulations: which benefits for which losses? *Earth System Dynamics*, 11(2), 537–562.](https://esd.copernicus.org/articles/11/537/2020/)
- [SBCK documentation](https://sbck.readthedocs.io/en/latest/)  
  &nbsp;&nbsp;— [GitHub: yrobink/SBCK-python](https://github.com/yrobink/SBCK-python)
- [SAFRAN reanalysis: Météo-France SAFRAN](https://opensource.umr-cnrm.fr/projects/safran)
- [DRIAS – Les futurs du climat](https://www.drias-climat.fr/commande) — [EXPLORE2 Climate Simulations (2022)](https://www.drias-climat.fr/accompagnement/sections/354)
- [CORDEX climate projections — Copernicus Data Store](https://cds.climate.copernicus.eu/datasets/projections-cordex-domains-single-levels)
- Michelangeli, P.-A., Vrac, M., & Loukos, H. (2009). Probabilistic downscaling approaches: Application to wind cumulative distribution functions. *Geophysical Research Letters*, 36(11). [doi:10.1029/2009GL038401](https://doi.org/10.1029/2009GL038401)
- Thrasher, B., Maurer, E.P., McKellar, C., & Duffy, P.B. (2012). Bias correcting climate model simulated daily temperature extremes with quantile mapping. *Hydrology and Earth System Sciences*, 16(9), 3309–3314. [doi:10.5194/hess-16-3309-2012](https://doi.org/10.5194/hess-16-3309-2012)
- Haagmans, V. (2021). Modelling the significance of snow-vegetation interactions for active layer dynamics in an Arctic permafrost region subjected to tundra shrubification. *Master's thesis*, ETH Zurich.
- Vrac, M., Noël, T., & Vautard, R. (2016). Bias correction of precipitation through Singularity Stochastic Removal: Because occurrences matter. *Journal of Geophysical Research: Atmospheres*, 121(10), 5237–5258. [doi:10.1002/2015JD024511](https://doi.org/10.1002/2015JD024511)
- Cannon, A.J. (2016). Multivariate Bias Correction of Climate Model Output: Matching Marginal Distributions and Intervariable Dependence Structure. *Journal of Climate*, 29(19), 7045–7064. [doi:10.1175/JCLI-D-15-0679.1](https://doi.org/10.1175/JCLI-D-15-0679.1)
- Global Carbon Project (2023). Données mondiales sur les émissions de carbone.  
  In: Ministère de la Transition écologique, «La France face aux neuf limites planétaires».
  [Voir en ligne](https://www.statistiques.developpement-durable.gouv.fr/edition-numerique/la-france-face-aux-neuf-limites-planetaires/4-changement-climatique)
- Vidal, J.-P., Martin, E., Franchistéguy, L., Baillon, M., & Soubeyroux, J.-M. (2010). A 50-year high-resolution atmospheric reanalysis over France with the Safran system. *International Journal of Climatology*, 30(11), 1627–1644.
- Quintana-Segui, P., Le Moigne, P., Durand, Y., Martin, E., Habets, F., Baillon, M., Canellas, C., Franchistéguy, L., & Morel, S. (2008). Analysis of near-surface atmospheric variables: Validation of the SAFRAN analysis over France. *Journal of Applied Meteorology and Climatology*, 47(1), 92–107.
- Allen, R.G., Pereira, L.S., Raes, D., & Smith, M. (1998). Crop evapotranspiration – Guidelines for computing crop water requirements – FAO Irrigation and Drainage Paper 56. FAO, Rome.
- Haddad, Z.S., & Rosenfeld, D. (1997). Optimality of empirical Z–R relations. *Quarterly Journal of the Royal Meteorological Society*, 123(541), 1283–1293.



---

## 👤 Author & Contact

**Hajar BADRAOUI**  
France   
📧 hajar.badraoui01@gmail.com  
🔗 [github.com/badraouihajar](https://github.com/badraouihajar)


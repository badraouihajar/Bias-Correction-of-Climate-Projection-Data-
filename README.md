# 🌍 Correction de biais des projections climatiques

<p align="center">
  <b>Hajar BADRAOUI</b> <br>
  Stagiaire Data Analyst @ ARVALIS – 2025
</p>

---

> **Projet réalisé dans le cadre du stage de Master 2 à ARVALIS – Institut technique agricole (Projet CLIMODIF).**

---

## 🗂️ Table des matières
- [Contexte](#contexte)
- [Motivation & Objectifs](#motivation--objectifs)
- [Méthodes](#méthodes)
- [Valeur ajoutée & Résultats](#valeur-ajoutée--résultats)
- [Structure du dépôt](#structure-du-dépôt)
- [Références](#références)
- [Auteur & Contact](#auteur--contact)

---

## 🌾 Contexte

Ce dépôt a été développé lors de mon stage de Master au sein du projet **CLIMODIF** chez ARVALIS.  
CLIMODIF vise à fournir aux agriculteurs des outils pour mieux anticiper et s'adapter au changement climatique.  
Mon travail porte sur la correction des biais des projections climatiques, pour rendre les données plus fiables et exploitables dans le secteur agricole.

---

## 🧑‍💻 Motivation & Objectifs

Les simulations issues des modèles climatiques (EURO-CORDEX) présentent des biais par rapport aux données de référence SAFRAN (Météo-France).  
Ces biais faussent l’évaluation des risques futurs et la prise de décision.

**Objectifs du projet :**
- Évaluer et comparer des méthodes avancées de correction de biais appliquées aux projections climatiques, notamment une méthode univariée (CDF-t) et une méthode multivariée (dOTC).
- Gagner en autonomie dans l’application, la validation et l’automatisation de ces méthodes statistiques, afin de pouvoir traiter différents jeux de données.
- Intégrer les données climatiques corrigées dans des modèles agronomiques internes, pour analyser l’impact concret des corrections sur des indicateurs agronomiques : stades de développement des cultures, stress hydrique etc.

---

## 🛠️ Méthodes

- **Correction de biais** réalisée avec [SBCK](https://github.com/yrobink/SBCK)
  - `CDF-t` : correction univariée par ajustement des distributions
  - `dOTC` : correction multivariée via transport optimal (préservation des dépendances inter-variables et corrélations spatiales)
- **Workflow :**
  - Extraction des données journalières (1976–2100) pour 40 points de la grille SAFRAN, réparties sur le territoire Français.
  - Correction des variables : `pr`, `sfcWind`, `tasmin`, `tasmax`, `hurs`, `rsds`, `etpFAO (calculé)`
  - Correction mensuelle sur fenêtres glissantes de 30 ans
  - Post-traitement spécifique pour la précipitation (`log-exp`, SSR : Singularity Stochastic Removal)

---

## 📊 Valeur ajoutée & Résultats

- **Comparaison rigoureuse** : Analyse détaillée CDF-t vs dOTC (biais, variance, dépendances)
- **Validation croisée** : Analyse de la capacité des corrections à préserver les tendances des modèles climatiques
- **Transférabilité** : Workflow facilement adaptable à d’autres stations ou variables
- **Qualité accrue pour l’agriculture** : Résultats utilisables pour les indicateurs de risque agro-climatique


---

## 📁 Structure du dépôt

| Fichier / Dossier                                   | Description                                                                 |
|-----------------------------------------------------|-----------------------------------------------------------------------------|
| `40stations.png`                                    | Carte des 40 points de la grille SAFRAN                                       |
| `CDFT_finally_all_vars_1976_2100.csv`               | Données corrigées par la méthode CDF-t (1976–2100)                          |
| `dOTC_final_all_vars_1976_2100.csv`                 | Données corrigées par la méthode dOTC (1976–2100)                           |
| `boigneville-CNRM-CERFACS-CM5_CNRM-ALADIN63-hist.csv` | Données du modèle climatique (historique, ALADIN63)                         |
| `boigneville-CNRM-CERFACS-CM5_CNRM-ALADIN63-rcp45.csv`| Données du modèle climatique (projection RCP 4.5, ALADIN63)                 |
| `boigneville_SAFRAN.csv`                            | Données de référence SAFRAN (Météo-France) pour Boigneville                 |
| `grilleSafran_utile_drias2021.csv`                  | Grille spatiale pour l’appariement SAFRAN/EURO-CORDEX                             |
| `Collecte.ipynb`                                    | Notebook Jupyter : extraction des données EURO-CORDEX d'après la plateforme CDS : Climate Data Store                    |
| `Debiaisage.ipynb`                                  | Notebook Jupyter : analyse des méthodes de correction de biais              |
| `README.md`                                         | Ce fichier de présentation (guide du dépôt)                                 |

---

## 📚 Références

- Robin, Y., Corre, L., Marson, P., Bernus, S., Vrac, M., & Thao, S. (2024). [Projections climatiques régionalisées : correction de biais et changements futurs](https://doi.org/10.57745/KXRB5B)
- Robin, Y., Vrac, M., Naveau, P., & Yiou, P. (2019). [Multivariate stochastic bias corrections with optimal transport. *Hydrology and Earth System Sciences*, 23(2), 773–786.](https://hess.copernicus.org/articles/23/773/2019/)
- François, B., Vrac, M., Cannon, A.J., Robin, Y., & Allard, D. (2020). [Multivariate bias corrections of climate simulations: which benefits for which losses? *Earth System Dynamics*, 11(2), 537–562.](https://esd.copernicus.org/articles/11/537/2020/)
- [SBCK documentation](https://sbck.readthedocs.io/en/latest/) — [GitHub: yrobink/SBCK-python](https://github.com/yrobink/SBCK-python)
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

## 👤 Auteur & Contact

**Hajar BADRAOUI**  
France  
📧 hajar.badraoui01@gmail.com  
🔗 [github.com/badraouihajar](https://github.com/badraouihajar)

---

<sub>⭐️ N’hésitez pas à ouvrir une issue ou à me contacter pour toute question ou suggestion !</sub>

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

Les simulations issues des modèles climatiques (EURO-CORDEX, etc.) présentent des biais par rapport aux observations (SAFRAN).  
Ces biais faussent l’évaluation des risques futurs et la prise de décision.

**Objectifs du projet :**
- Évaluer et comparer des méthodes avancées de correction de biais, univariée (**CDF-t**) et multivariée (**dOTC**)
- Quantifier les améliorations pour chaque variable agro-climatique (précipitation, température, vent, etc.)
- Fournir un workflow reproductible et automatisé, directement réutilisable par les chercheurs, agronomes et décideurs

---

## 🛠️ Méthodes

- **Correction de biais** réalisée avec [SBCK](https://github.com/yrobink/SBCK)
  - `CDF-t` : correction univariée par ajustement des distributions
  - `dOTC` : correction multivariée via transport optimal (préservation des dépendances inter-variables)
- **Workflow :**
  - Extraction des données journalières (1976–2100) pour 40 stations en France
  - Correction des variables : `pr`, `sfcWind`, `tasmin`, `tasmax`, `hurs`, `rsds`, `ETP`
  - Correction mensuelle sur fenêtres glissantes de 30 ans
  - Post-traitement spécifique pour la précipitation (`log-exp`, SSR)

---

## 📊 Valeur ajoutée & Résultats

- **Comparaison rigoureuse** : Analyse détaillée CDF-t vs dOTC (biais, variance, dépendances)
- **Préservation des tendances** : Validation croisée, régression des tendances (robustesse des scénarios)
- **Transférabilité** : Workflow facilement adaptable à d’autres stations, variables, ou régions
- **Qualité accrue pour l’agriculture** : Résultats utilisables pour les indicateurs de risque agro-climatique
- **Reproductibilité & ouverture** : Tout est documenté pour la communauté scientifique et agricole

---

## 📁 Structure du dépôt

| Fichier / Dossier                       | Description                                                                |
|-----------------------------------------|----------------------------------------------------------------------------|
| `40stations.png`                        | Carte des 40 stations météorologiques                                      |
| `CDFT_finally_all_vars_1976_2100.csv`   | Données corrigées par la méthode CDF-t (1976–2100)                         |
| `dOTC_final_all_vars_1976_2100.csv`     | Données corrigées par la méthode dOTC (1976–2100)                          |
| `boigneville_...csv`                    | Données climatiques pour la station de Boigneville (modèle/obs/corrigées)  |
| `boigneville_SAFRAN.csv`                | Observations SAFRAN pour Boigneville                                       |
| `grilleSafran_utile_drias2021.csv`      | Grille spatiale utilisée pour l’appariement SAFRAN/DRIAS                   |
| `Collecte.ipynb`                        | Notebook Jupyter : extraction et préparation des données                   |
| `Debiaisage.ipynb`                      | Notebook Jupyter : correction des biais                                    |
| `README.md`                             | Ce fichier de présentation (guide du dépôt)                                |

---

## 📚 Références

- Robin, Y., Corre, L., Marson, P., Bernus, S., Vrac, M., & Thao, S. (2024). [Projections climatiques régionalisées : correction de biais et changements futurs](https://doi.org/10.57745/KXRB5B)
- Robin, Y., Vrac, M., Naveau, P., & Yiou, P. (2019). [Multivariate stochastic bias corrections with optimal transport. *HESS*, 23(2), 773–786.](https://hess.copernicus.org/articles/23/773/2019/)
- François, B., Vrac, M., Cannon, A.J., Robin, Y., & Allard, D. (2020). [Multivariate bias corrections of climate simulations: which benefits for which losses? *ESD*, 11(2), 537–562.](https://esd.copernicus.org/articles/11/537/2020/)
- [Documentation SBCK](https://sbck.readthedocs.io/en/latest/) — [GitHub](https://github.com/yrobink/SBCK-python)
- [SAFRAN reanalysis – Météo-France](https://opensource.umr-cnrm.fr/projects/safran)
- [DRIAS – Les futurs du climat](https://www.drias-climat.fr/commande)
- [CORDEX – Copernicus Data Store](https://cds.climate.copernicus.eu/datasets/projections-cordex-domains-single-levels)
- Michelangeli, P.-A., Vrac, M., & Loukos, H. (2009). *GRL*, 36(11). [doi:10.1029/2009GL038401](https://doi.org/10.1029/2009GL038401)
- Thrasher, B., et al. (2012). *HESS*, 16(9), 3309–3314. [doi:10.5194/hess-16-3309-2012](https://doi.org/10.5194/hess-16-3309-2012)
- ...et autres références détaillées dans le projet

---

## 👤 Auteur & Contact

**Hajar BADRAOUI**  
France  
📧 hajar.badraoui01@gmail.com  
🔗 [github.com/badraouihajar](https://github.com/badraouihajar)

---

<sub>⭐️ N’hésitez pas à ouvrir une issue ou à me contacter pour toute question ou suggestion !</sub>


# Mini-Projet 4 : Prévision des Précipitations à partir de Données Climatiques

**Année universitaire 2025-2026**  
**Encadrant : Pr. Soumia Ziti**  
**Étudiants : HENOVI Komla Alban et DIOP Asta Walo**  
**Projet sélectionné : Projet 4 – Prédiction binaire de la pluie demain (RainTomorrow)**

## Contexte et Objectif

Ce mini-projet fait partie des travaux d’initiation à l’analyse avancée de données spatiales et environnementales demandés dans le cadre du cours d’Intelligence Artificielle.

**Objectif principal** :  
Développer un modèle de classification binaire robuste capable de prédire si **il pleuvra demain** (`RainTomorrow = Yes/No`) à partir des observations météorologiques du jour, en utilisant le dataset **Rain in Australia** (Kaggle).

**Dataset** :
- Nom : `weatherAUS.csv`
- Source : https://www.kaggle.com/datasets/jsphyg/weather-dataset-rattle-package?resource=download
- Période : ~10 ans d’observations quotidiennes dans 49 villes australiennes
- ~145 000 lignes, 23 colonnes
- Variables clés : MinTemp, MaxTemp, Rainfall, Evaporation, Sunshine, WindGustDir, Humidity9am/3pm, Pressure9am/3pm, Cloud9am/3pm, Temp9am/3pm, RainToday, **RainTomorrow** (cible)

**Importance scientifique** :  
La prévision à court terme des précipitations (nowcasting) est cruciale pour l’agriculture, la gestion des risques d’inondation et la prise de décision en zone semi-aride comme l’Australie.

## Cadre Méthodologique Suivi

Nous respectons strictement les étapes obligatoires du projet :

1. Présentation du contexte spatial et du dataset
2. Inspection et qualité des données
3. Prétraitement (gestion des manquants/aberrants, encodage catégoriel, normalisation)
4. Analyse exploratoire (univariée, bivariée, ACP, visualisations)
5. Modélisation : comparaison de plusieurs algorithmes (LogisticRegression, RandomForest, XGBoost, etc.)
6. Évaluation : focus sur **Recall** (ne pas manquer les jours de pluie) + F1-score, Accuracy, AUC
7. Interprétation physique des résultats (variables les plus importantes : humidité, pression, etc.)
8. Bonus : courbe de calibration, réseau de neurones (en Python d’abord)

**Note importante** : Le livrable final doit être réalisé **exclusivement** avec **Orange Data Mining** (`.ows`).

Ce dépôt contient d’abord un prototype complet en Python (Jupyter Notebook) pour tester, valider et comprendre les étapes avant de recréer le workflow dans Orange.

## Structure du Repository

> Remarque : seuls `README.md` et `data/weatherAUS.csv` sont requis pour démarrer. Les dossiers ci-dessous sont la structure cible.

```
Projet4_Rain_in_Australia/
├── data/
│   └── weatherAUS.csv                ← dataset
├── notebooks/
│   └── Projet4_Prevision_Pluie.ipynb ← notebook principal Python (à créer)
├── reports/
│   └── rapport_IMRADC_draft.pdf      ← brouillon du rapport final (optionnel)
├── orange_workflows/                 ← dossier pour les .ows (à remplir)
├── requirements.txt                  ← dépendances Python
└── README.md                         ← ce fichier
```

## Prérequis (prototype Python)

### Dépendances

Voir `requirements.txt`.

Installation :

```bash
pip install -r requirements.txt
```

### Dataset

Le fichier `data/weatherAUS.csv` est déjà présent dans ce dépôt.

Source originale (référence) : https://www.kaggle.com/datasets/jsphyq/weather-dataset-rattle-package

## Comment exécuter le prototype Python

1. (Optionnel) Créer un environnement virtuel puis installer les dépendances.
2. Ouvrir le notebook :

```bash
jupyter notebook notebooks/Projet4_Prevision_Pluie.ipynb
```

3. Suivre les sections dans l’ordre :
	- Chargement et inspection
	- Prétraitement (beaucoup de NaN, variables catégorielles liées au vent)
	- EDA (boxplots Humidity/Pressure vs RainTomorrow, corrélations, ACP)
	- Modèles : LogisticRegression → RandomForest → XGBoost
	- Évaluation et focus Recall/F1
	- Feature importance (interprétation physique)

## Prochaines étapes (transition vers Orange)

1. Reproduire le même workflow dans **Orange Data Mining** :
	- File → Import CSV
	- Preprocess (impute, normalize, discretize)
	- PCA
	- Logistic Regression, Random Forest, XGBoost (si widget disponible), Neural Network
	- Test & Score, Confusion Matrix, Calibration Plot, etc.
2. Exporter le workflow (`.ows`) annoté
3. Rédiger le rapport final au format **IMRADC** (Introduction, Méthode, Résultats, Analyse & Discussion, Conclusion)
4. Ajouter les captures d’écran/graphiques Orange dans le PDF

## Auteurs

- HENOVI Komla Alban (@AlbanHenovi)

## Licence

MIT (ou selon ce que vous décidez en groupe)

---

Si tu veux, je peux aussi :
- Générer un notebook Jupyter “squelette” (chargement, prétraitement, EDA, modèles, métriques)
- Proposer un plan de prétraitement robuste (imputation KNN, encodage des directions du vent, gestion du déséquilibre)
- Donner une checklist exacte pour reconstruire le pipeline dans Orange


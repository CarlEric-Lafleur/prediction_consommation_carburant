> **Note:** An English version follows the French description.

# Prédiction de la Consommation de Carburant

Ce projet a été réalisé dans le cadre du cours **MTH3302 - Méthodes probabilistes et statistiques pour l'intelligence artificielle** à Polytechnique Montréal (Automne 2024).

## Objectif
L'objectif principal est de prédire la consommation de carburant (en L/100km) de différents véhicules récents en utilisant des techniques d'apprentissage automatique et d'analyse statistique.

## Contenu du Dépôt
*   `main.ipynb` : Le notebook Jupyter (écrit en **Julia**) contenant l'intégralité du pipeline : exploration des données, prétraitement, entraînement des modèles et génération des prédictions.
*   `data/` : Dossier contenant les jeux de données d'entraînement (`train.csv`) et de test (`test.csv`).

## Méthodologie

### 1. Exploration et Prétraitement des Données
Une analyse approfondie des données a été menée pour comprendre les facteurs influençant la consommation :
*   **Nettoyage** : Conversion des types de données et vérification de l'intégrité des données (valeurs manquantes).
*   **Ingénierie des fonctionnalités (Feature Engineering)** :
    *   Création de la variable `volume_gaz` (produit du nombre de cylindres et de la cylindrée).
    *   Estimation du poids (`weight`) basé sur le type de véhicule.
    *   Regroupement des catégories de véhicules (`general_type`) pour réduire la dimensionnalité.
*   **Analyse Statistique** : Étude de la colinéarité (VIF), visualisation des relations entre variables et détection/traitement des valeurs aberrantes (outliers).

### 2. Modèles Évalués
Plusieurs approches de régression ont été implémentées et comparées sur la base de la métrique **RMSE** (Root Mean Square Error) :
*   Régression Linéaire
*   Régression Ridge
*   Régression SVD
*   Régression Polynomiale
*   Arbre de Régression
*   Forêt Aléatoire (Random Forest)

### 3. Modèle Final Sélectionné
La solution retenue est une **approche hybride** inspirée des modèles "Mixture of Experts", combinant deux stratégies :
1.  **Estimation par Paires (Matching)** : Exploitation des similarités directes entre les données de test et d'entraînement. Les véhicules du jeu de test partageant des caractéristiques identiques (ou très proches) avec ceux du jeu d'entraînement se voient attribuer la consommation moyenne observée.
2.  **Forêt Aléatoire de Régression** : Utilisée pour capturer les non-linéarités et généraliser les prédictions pour les cas où aucune correspondance directe n'est trouvée.

La prédiction finale est obtenue par une combinaison pondérée de ces deux méthodes.

## Résultats
Cette approche a permis d'atteindre un **RMSE de 0.78455** sur la plateforme de compétition Kaggle et de remporter le concours.

---
*Réalisé par une équipe de 4 étudiants.*

---

# Fuel Consumption Prediction

This project was carried out as part of the course **MTH3302 - Probabilistic and Statistical Methods for Artificial Intelligence** at Polytechnique Montréal (Fall 2024).

## Objective
The main objective is to predict the fuel consumption (in L/100km) of various recent vehicles using machine learning and statistical analysis techniques.

## Repository Content
*   `main.ipynb`: The Jupyter notebook (written in **Julia**) containing the entire pipeline: data exploration, preprocessing, model training, and prediction generation.
*   `data/`: Folder containing the training (`train.csv`) and test (`test.csv`) datasets.

## Methodology

### 1. Data Exploration and Preprocessing
An in-depth analysis of the data was conducted to understand the factors influencing consumption:
*   **Cleaning**: Data type conversion and integrity check (missing values).
*   **Feature Engineering**:
    *   Creation of the `volume_gaz` variable (product of cylinder count and displacement).
    *   Weight estimation (`weight`) based on vehicle type.
    *   Grouping of vehicle categories (`general_type`) to reduce dimensionality.
*   **Statistical Analysis**: Collinearity study (VIF), visualization of relationships between variables, and outlier detection/treatment.

### 2. Evaluated Models
Several regression approaches were implemented and compared based on the **RMSE** (Root Mean Square Error) metric:
*   Linear Regression
*   Ridge Regression
*   SVD Regression
*   Polynomial Regression
*   Regression Tree
*   Random Forest

### 3. Selected Final Model
The chosen solution is a **hybrid approach** inspired by "Mixture of Experts" models, combining two strategies:
1.  **Pair Matching**: Exploiting direct similarities between test and training data. Vehicles in the test set sharing identical (or very close) characteristics with those in the training set are assigned the observed average consumption.
2.  **Random Forest Regression**: Used to capture non-linearities and generalize predictions for cases where no direct match is found.

The final prediction is obtained by a weighted combination of these two methods.

## Results
This approach achieved an **RMSE of 0.78455** on the Kaggle competition platform and won the competition.

---
*Realized by a team of 4 students.*

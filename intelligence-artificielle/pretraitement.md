---
icon: arrow-progress
cover: >-
  https://images.unsplash.com/photo-1737914111975-b4d513d783e0?crop=entropy&cs=srgb&fm=jpg&ixid=M3wxOTcwMjR8MHwxfHJhbmRvbXx8fHx8fHx8fDE3NDE1NTI3NDh8&ixlib=rb-4.0.3&q=85
coverY: 0
---

# Prétraitement

## Introduction

Le prétraitement des données est une étape essentielle dans le processus d'entraînement des modèles d'IA. Il consiste à nettoyer, normaliser et transformer les données brutes en un format adapté à l'entraînement des modèles.&#x20;

Le prétraitement des données peut avoir un impact significatif sur les performances des modèles d'IA, en particulier lorsqu'il s'agit de données non structurées ou de grande taille. Dans le monde de l'embarqué, le prétraitement des données est d'autant plus important, car les ressources matérielles sont limitées et la qualité des données peut avoir un impact direct sur les performances des modèles.

## Techniques de Prétraitement

### 1. Normalisation et Standardisation

**Pourquoi ?**\
Les modèles d'IA sont sensibles aux échelles des variables. Des valeurs trop grandes ou trop petites peuvent biaiser l'apprentissage.

**Techniques :**

* **Normalisation (Min-Max Scaling)** : Ramène les valeurs entre 0 et 1 selon la formule :

$$
X' = \frac{X - X_{min}}{X_{max} - X_{min}}
$$

* **Standardisation (Z-score Scaling)** : Centre et réduit les valeurs : où _mu_ est la moyenne et _sigma_ l'écart-type.

$$
X' = \frac{X - \mu}{\sigma}
$$

### 2. Encodage des Variables Catégoriques

**Pourquoi ?**\
Les modèles de machine learning et les réseaux de neurones ne comprennent que des valeurs numériques.

**Techniques :**

* **One-Hot Encoding** : Transforme chaque catégorie en une colonne binaire.
* **Label Encoding** : Remplace chaque catégorie par un nombre entier (utile pour les modèles basés sur les arbres).

### 3. Gestion des Valeurs Manquantes

**Pourquoi ?**\
Les valeurs manquantes peuvent fausser les analyses et réduire la performance des modèles.

**Techniques :**

* **Suppression des lignes ou colonnes incomplètes** (si peu de valeurs manquantes).
* **Imputation par la moyenne/médiane/mode** pour remplacer les valeurs manquantes.
* **Utilisation de modèles prédictifs** (comme KNN ou régression) pour estimer les valeurs manquantes.

***

Ces techniques permettent d'améliorer la qualité des données et d'assurer de meilleures performances pour les modèles d'IA.

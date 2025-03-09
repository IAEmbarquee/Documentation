---
icon: binary
cover: >-
  https://images.unsplash.com/photo-1506555191898-a76bacf004ca?crop=entropy&cs=srgb&fm=jpg&ixid=M3wxOTcwMjR8MHwxfHNlYXJjaHwxfHxudW1iZXJzfGVufDB8fHx8MTc0MTU1Mjc2OHww&ixlib=rb-4.0.3&q=85
coverY: 0
---

# Quantification

#### Introduction

La quantification est une technique qui permet de réduire la taille des modèles d'IA en convertissant les poids des réseaux de neurones en nombres entiers. Cette technique est particulièrement utile pour les applications embarquées où la mémoire est limitée. La quantification peut être réalisée de différentes manières, en fonction des besoins de l'application et des contraintes matérielles. Dans ce guide, nous allons explorer les différentes techniques de quantification et comment les appliquer à vos modèles d'IA.

#### Techniques de quantification

Il existe plusieurs techniques de quantification qui peuvent être utilisées pour réduire la taille des modèles d'IA. Voici quelques-unes des techniques les plus courantes :

1. **Post-training quantization** : Cette technique consiste à quantifier les poids d'un modèle d'IA après son entraînement. Les poids sont convertis en nombres entiers à l'aide d'un algorithme de quantification, ce qui permet de réduire la taille du modèle tout en préservant sa précision.
2. **Quantization-aware training** : Cette technique consiste à entraîner un modèle d'IA en utilisant des poids quantifiés dès le départ. Cela permet d'optimiser le modèle pour une quantification ultérieure, ce qui peut améliorer sa précision et sa taille.

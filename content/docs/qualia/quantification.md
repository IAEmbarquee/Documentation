---
weight: 32
title: "Quantification"
description: "Quantification des modèles d'IA."
icon: compress
lead: ""
date: 2022-10-10T02:21:15+00:00
lastmod: 2022-10-10T02:21:15+00:00
draft: false
images: []
---

### Introduction

La quantification est une technique qui permet de réduire la taille des modèles d'IA en convertissant les poids des réseaux de neurones en nombres entiers. Cette technique est particulièrement utile pour les applications embarquées où la mémoire est limitée. La quantification peut être réalisée de différentes manières, en fonction des besoins de l'application et des contraintes matérielles. Dans ce guide, nous allons explorer les différentes techniques de quantification et comment les appliquer à vos modèles d'IA.

### Techniques de quantification

Il existe plusieurs techniques de quantification qui peuvent être utilisées pour réduire la taille des modèles d'IA. Voici quelques-unes des techniques les plus courantes :

1. **Post-training quantization** : Cette technique consiste à quantifier les poids d'un modèle d'IA après son entraînement. Les poids sont convertis en nombres entiers à l'aide d'un algorithme de quantification, ce qui permet de réduire la taille du modèle tout en préservant sa précision.
2. **Quantization-aware training** : Cette technique consiste à entraîner un modèle d'IA en utilisant des poids quantifiés dès le départ. Cela permet d'optimiser le modèle pour une quantification ultérieure, ce qui peut améliorer sa précision et sa taille.

### Qualia

Qualia est un outil développé par le LEAT (Laboratoire d'Electronique, Antennes et Télécommunications) qui permet de quantifier les modèles d'IA de manière à les rendre compatibles avec les contraintes matérielles des applications embarquées.
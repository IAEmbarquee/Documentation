---
icon: image
cover: >-
  https://images.unsplash.com/photo-1606502497430-26309bc0cc7e?crop=entropy&cs=srgb&fm=jpg&ixid=M3wxOTcwMjR8MHwxfHNlYXJjaHwyfHx0cmFmZmljJTIwc2lnbnxlbnwwfHx8fDE3NDE1NTI3ODF8MA&ixlib=rb-4.0.3&q=85
coverY: -130
---

# Jeu de données

#### Introduction

Le jeu de données GTSRB ([German Traffic Sign Recognition Benchmark](https://benchmark.ini.rub.de/gtsrb_dataset.html)) est un jeu de données largement utilisé pour l'entraînement et l'évaluation des modèles de reconnaissance de panneaux de signalisation. Il contient plus de 50 000 images de panneaux de signalisation allemands, réparties en 43 classes différentes. Chaque image est de petite taille et est associée à une classe correspondant au type de panneau de signalisation qu'elle représente.

{% hint style="info" %}
Pour notre projet, nous allons utiliser une version customisée du dataset pour éviter de télécharger les quelques gigas du dataset original.
{% endhint %}

#### Téléchargement

[Télécharger](https://simai32.hugofnm.fr/download?q=dataset) le jeu de données customisé.

#### Structure

Le jeu de données customisé est structuré de la manière suivante :

```plaintext
dataset/
├── Train/ # Jeu de données d'entraînement
│   ├── 0/
│   │   ├── 00000_00000_00000.png
│   ├── ...
│   ├── 42/
├── Test/ # Jeu de données de test
│   ├── ...
├── Meta/ # Métadonnées (panneaux de signalisation)
│   ├── 0.png
│   ├── ...
│   ├── 42.png
```

#### Classes

Les classes du jeu de données correspondent aux types de panneaux de signalisation et actions à réaliser suivants :

| Panneau Meta                | Numéro | Comportement                             |
| --------------------------- | ------ | ---------------------------------------- |
| 20                          | 0      | < 20km/h                                 |
| 30                          | 1      | < 30km/h                                 |
| 50                          | 2      | < 50km/h                                 |
| 60                          | 3      | < 60km/h                                 |
| 70                          | 4      | < 70km/h                                 |
| 80                          | 5      | < 80km/h                                 |
| 100                         | 6      | < 100km/h                                |
| 120                         | 7      | < 120km/h                                |
| Sens interdit               | 8      | Stop                                     |
| Stop                        | 9      | Stop pendant T=5s avant reprise          |
| Cédez le passage            | 10     | Stop pendant T=2s avant reprise          |
| Danger                      | 11     | Diminuer la vitesse de 20%               |
| Danger virage à gauche      | 12     | Diminuer la vitesse de 20%               |
| Danger virage à droite      | 13     | Diminuer la vitesse de 20%               |
| Danger virage double        | 14     | Diminuer la vitesse de 30%               |
| Danger chaussée glissante   | 15     | Diminuer la vitesse de 20%               |
| Danger passage piéton       | 16     | Diminuer la vitesse de 20%               |
| Danger vélo                 | 17     | Diminuer la vitesse de 20%               |
| Danger passage d'animaux    | 18     | Diminuer la vitesse de 20%               |
| Danger feu de signalisation | 19     | Diminuer la vitesse de 20%               |
| Danger dos d'âne            | 20     | Diminuer la vitesse de 50%               |
| Danger travaux              | 21     | Diminuer la vitesse de 75%               |
| Tout droit / Droite         | 22     | Tourner à droite ou continuer tout droit |
| Tout droit / Gauche         | 23     | Tourner à gauche ou continuer tout droit |
| Tourner à droite            | 24     | Tourner à droite                         |
| Tourner à gauche            | 25     | Tourner à gauche                         |
| Tout droit                  | 26     | Continuer tout droit                     |
| End                         | 27     | Fin du jeu                               |

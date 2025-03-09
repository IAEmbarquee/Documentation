---
icon: image
cover: >-
  https://images.unsplash.com/photo-1606502497430-26309bc0cc7e?crop=entropy&cs=srgb&fm=jpg&ixid=M3wxOTcwMjR8MHwxfHNlYXJjaHwyfHx0cmFmZmljJTIwc2lnbnxlbnwwfHx8fDE3NDE1NTI3ODF8MA&ixlib=rb-4.0.3&q=85
coverY: -130
---

# Jeu de données

## Introduction

Le jeu de données GTSRB ([German Traffic Sign Recognition Benchmark](https://benchmark.ini.rub.de/gtsrb_dataset.html)) est un jeu de données largement utilisé pour l'entraînement et l'évaluation des modèles de reconnaissance de panneaux de signalisation. Il contient plus de 50 000 images de panneaux de signalisation allemands, réparties en 43 classes différentes. Chaque image est de petite taille et est associée à une classe correspondant au type de panneau de signalisation qu'elle représente.

{% hint style="info" %}
Pour notre projet, nous allons utiliser une version customisée du dataset pour éviter de télécharger les quelques gigas du dataset original.
{% endhint %}

## Téléchargement

[Télécharger](https://gitlab.hugofnm.fr/simai32/simai32/-/tree/master/Dataset%20GTSRBC/) le jeu de données customisé.

## Structure

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

## Classes

Les classes du jeu de données correspondent aux types de panneaux de signalisation et actions à réaliser suivants :

<table><thead><tr><th width="236">Panneau Meta</th><th width="260">Numéro</th><th>Comportement</th></tr></thead><tbody><tr><td>20</td><td>0</td><td>&#x3C; 20km/h</td></tr><tr><td>30</td><td>1</td><td>&#x3C; 30km/h</td></tr><tr><td>50</td><td>2</td><td>&#x3C; 50km/h</td></tr><tr><td>60</td><td>3</td><td>&#x3C; 60km/h</td></tr><tr><td>70</td><td>4</td><td>&#x3C; 70km/h</td></tr><tr><td>80</td><td>5</td><td>&#x3C; 80km/h</td></tr><tr><td>100</td><td>6</td><td>&#x3C; 100km/h</td></tr><tr><td>120</td><td>7</td><td>&#x3C; 120km/h</td></tr><tr><td>Sens interdit</td><td>8</td><td>Stop</td></tr><tr><td>Stop</td><td>9</td><td>Stop pendant T=5s avant reprise</td></tr><tr><td>Cédez le passage</td><td>10</td><td>Stop pendant T=2s avant reprise</td></tr><tr><td>Danger</td><td>11</td><td>Diminuer la vitesse de 20%</td></tr><tr><td>Danger virage à gauche</td><td>12</td><td>Diminuer la vitesse de 20%</td></tr><tr><td>Danger virage à droite</td><td>13</td><td>Diminuer la vitesse de 20%</td></tr><tr><td>Danger virage double</td><td>14</td><td>Diminuer la vitesse de 30%</td></tr><tr><td>Danger chaussée glissante</td><td>15</td><td>Diminuer la vitesse de 20%</td></tr><tr><td>Danger passage piéton</td><td>16</td><td>Diminuer la vitesse de 20%</td></tr><tr><td>Danger vélo</td><td>17</td><td>Diminuer la vitesse de 20%</td></tr><tr><td>Danger passage d'animaux</td><td>18</td><td>Diminuer la vitesse de 20%</td></tr><tr><td>Danger feu de signalisation</td><td>19</td><td>Diminuer la vitesse de 20%</td></tr><tr><td>Danger dos d'âne</td><td>20</td><td>Diminuer la vitesse de 50%</td></tr><tr><td>Danger travaux</td><td>21</td><td>Diminuer la vitesse de 75%</td></tr><tr><td>Tout droit / Droite</td><td>22</td><td>Tourner à droite ou continuer tout droit</td></tr><tr><td>Tout droit / Gauche</td><td>23</td><td>Tourner à gauche ou continuer tout droit</td></tr><tr><td>Tourner à droite</td><td>24</td><td>Tourner à droite</td></tr><tr><td>Tourner à gauche</td><td>25</td><td>Tourner à gauche</td></tr><tr><td>Tout droit</td><td>26</td><td>Continuer tout droit</td></tr><tr><td>End</td><td>27</td><td>Fin du jeu</td></tr></tbody></table>

---
description: Il est préférable d'utiliser l'IDE VSCode !
icon: code-simple
cover: >-
  https://images.unsplash.com/photo-1517055729445-fa7d27394b48?crop=entropy&cs=srgb&fm=jpg&ixid=M3wxOTcwMjR8MHwxfHNlYXJjaHwxMHx8YXJkdWlub3xlbnwwfHx8fDE3NDE1NDQ1NjR8MA&ixlib=rb-4.0.3&q=85
coverY: 0
---

# IDE Arduino

## [Veuillez utiliser VSCode !](ide-vscode.md)

## Introduction

L'IDE Arduino est un environnement de développement intégré (IDE) qui permet de programmer des cartes Arduino ou dans notre cas, des ESP32. Il est basé sur le langage de programmation C++ et utilise une bibliothèque logicielle qui facilite l'écriture de code pour les microcontrôleurs. L'IDE Arduino est un outil puissant et polyvalent qui convient à une grande variété de projets, des plus simples aux plus complexes.

## Installation

{% tabs %}
{% tab title="Via WinGET (recommandé)" %}
Une façon simple d'installer l'IDE Arduino est d'utiliser le gestionnaire de packages WinGet intégré à Windows. Pour ce faire, ouvrez une invite de commande en tant qu'administrateur et exécutez la commande suivante :

```shell
winget install --id=ArduinoSA.IDE.stable  -e
```
{% endtab %}

{% tab title="Via le site officiel" %}
Méthode traditionnelle d'installation de l'IDE Arduino. Téléchargez le fichier d'installation depuis le site officiel d'Arduino et suivez les instructions d'installation.

[Télécharger Arduino IDE](https://www.arduino.cc/en/software)
{% endtab %}
{% endtabs %}

## Configuration

Une fois l'IDE Arduino installé, il est nécessaire de configurer l'environnement de développement pour qu'il puisse reconnaître les cartes ESP32. Pour ce faire, ouvrez l'IDE Arduino et suivez les étapes suivantes :

1. Ouvrez le menu <kbd>Fichier</kbd> et sélectionnez <kbd>Préférences</kbd>.
2. Dans le champ <kbd>URL de gestionnaire de cartes supplémentaires</kbd>, entrez l'URL suivante :

```shell
https://static-cdn.m5stack.com/resource/arduino/package_m5stack_index.json
```

3. Cliquez sur `OK` pour enregistrer les modifications.
4. Ouvrez le menu <kbd>Outils</kbd>, sélectionnez <kbd>Type de carte</kbd> et cliquez sur <kbd>Gestionnaire de cartes</kbd>.
5. Recherchez <kbd>M5Stack</kbd> dans la barre de recherche et installez le package.

On peut maintenant sélectionner la carte ESP32 dans le menu <kbd>Outils > Carte > M5Stack > M5CoreS3</kbd>.

✅ Voilà, l'IDE Arduino est maintenant configuré pour programmer des cartes ESP32. On peut maintenant passer à la suite...

---
weight: 23
title: "IDE Arduino"
description: "Installation et configuration de l'IDE Arduino."
icon: terminal
date: "2024-08-02T16:40:08+02:00"
lastmod: "2024-08-02T16:40:08+02:00"
draft: false
toc: true
---

### Introduction

L'IDE Arduino est un environnement de développement intégré (IDE) qui permet de programmer des cartes Arduino ou dans notre cas, des ESP32. Il est basé sur le langage de programmation C++ et utilise une bibliothèque logicielle qui facilite l'écriture de code pour les microcontrôleurs. L'IDE Arduino est un outil puissant et polyvalent qui convient à une grande variété de projets, des plus simples aux plus complexes.

### Installation

{{< tabs tabTotal="2">}}
{{% tab tabName="WinGet" %}}

Une façon simple d'installer l'IDE Arduino est d'utiliser le gestionnaire de packages WinGet intégré à Windows 10. Pour ce faire, ouvrez une invite de commande en tant qu'administrateur et exécutez la commande suivante :

```shell
winget install --id=ArduinoSA.IDE.stable  -e
```

{{% /tab %}}
{{% tab tabName="Windows, Linux et macOS" %}}

Méthode traditionnelle d'installation de l'IDE Arduino. Téléchargez le fichier d'installation depuis le site officiel d'Arduino et suivez les instructions d'installation.

[Télécharger Arduino IDE](https://www.arduino.cc/en/software)

{{% /tab %}}
{{< /tabs >}}

### Configuration

Une fois l'IDE Arduino installé, il est nécessaire de configurer l'environnement de développement pour qu'il puisse reconnaître les cartes ESP32. Pour ce faire, ouvrez l'IDE Arduino et suivez les étapes suivantes :

1. Ouvrez le menu `Fichier` et sélectionnez `Préférences`.
2. Dans le champ `URL de gestionnaire de cartes supplémentaires`, entrez l'URL suivante : 
```shell
https://static-cdn.m5stack.com/resource/arduino/package_m5stack_index.json
```
3. Cliquez sur `OK` pour enregistrer les modifications.
4. Ouvrez le menu `Outils`, sélectionnez `Type de carte` et cliquez sur `Gestionnaire de cartes`.
5. Recherchez `M5Stack` dans la barre de recherche et installez le package.

On peut maintenant sélectionner la carte ESP32 dans le menu `Outils` > `Carte` > `M5Stack` > `M5CoreS3`.

✅ Voilà, l'IDE Arduino est maintenant configuré pour programmer des cartes ESP32. On peut maintenant passer à la suite...
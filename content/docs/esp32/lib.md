---
weight: 24
title: "Librairies"
description: "Nécessaire avant de commencer."
icon: settings
date: "2024-08-02T16:40:08+02:00"
lastmod: "2024-08-02T16:40:08+02:00"
draft: false
toc: true
---

Afin d'installer les librairies nécessaires pour ce projet, il faut ouvrir l'IDE Arduino et se rendre dans le menu `Outils` > `Gérer les bibliothèques...`. Une fenêtre s'ouvre alors et il suffit de rechercher les librairies suivantes et de les installer :

### AsyncTCP
De : *me-no-dev*

La librairie `AsyncTCP` est une librairie de gestion de la communication TCP asynchrone pour les cartes ESP32. Elle permet de créer des serveurs et des clients TCP de manière asynchrone, ce qui signifie que les connexions TCP peuvent être gérées de manière non bloquante. Cela permet de gérer plusieurs connexions simultanément sans bloquer le programme principal.

{{< alert context="danger" text="Il va falloir modifier quelques fichiers de cette librairie pour éviter certains crashs dûs au watchdog qui fait planter l'ESP32." />}}

Nous allons donc modifier le fichier `AsyncTCP.h` qui se trouve dans le répertoire `C:\Users\%USERNAME%\Documents\Arduino\libraries\Async_TCP\src` et modifier à la main les lignes suivantes :

```cpp
//If core is not defined, then we are running in Arduino or PIO
#ifndef CONFIG_ASYNC_TCP_RUNNING_CORE
#define CONFIG_ASYNC_TCP_RUNNING_CORE 1 // On place la fonction dans le core 1
#define CONFIG_ASYNC_TCP_USE_WDT 1 // On active le watchdog
#endif

#ifndef CONFIG_ASYNC_TCP_STACK_SIZE
#define CONFIG_ASYNC_TCP_STACK_SIZE 8192 * 10 // On augmente la taille de la pile TRÈS IMPORTANT !!!
#endif

#ifndef CONFIG_ASYNC_TCP_PRIORITY
#define CONFIG_ASYNC_TCP_PRIORITY 10 // On augmente la priorité
#endif

#ifndef CONFIG_ASYNC_TCP_QUEUE_SIZE
#define CONFIG_ASYNC_TCP_QUEUE_SIZE 1024 // On augmente le nombre de paquets en attente
#endif

#ifndef CONFIG_ASYNC_TCP_MAX_ACK_TIME
#define CONFIG_ASYNC_TCP_MAX_ACK_TIME 2500 // On augmente le temps d'attente
#endif
```

### ESPAsyncWebServer
De : *lacamera*

La librairie `ESPAsyncWebServer` est une librairie de gestion de serveur web asynchrone pour les cartes ESP32. Elle permet de créer des serveurs web de manière asynchrone grâce à la librairie `AsyncTCP`. Cette librairie est très utile pour créer des interfaces web pour les projets IoT basés sur les cartes ESP32.

### M5Unified
De : *M5Stack*

La librairie `M5Unified` est une librairie de gestion des périphériques M5Stack pour les cartes ESP32. Elle permet de contrôler les différents périphériques de la carte M5Stack, tels que l'écran, les boutons, les LEDs, etc. Cette librairie est très utile pour créer des projets basés sur les cartes M5Stack.

{{< alert context="info" text="Il est aussi recommandé d'installer la librairie connexe `M5CoreS3`." />}}

### PNGDec
De : *Larry Bank*

La librairie `PNGDec` est une librairie de décodage des images PNG pour les cartes ESP32. Elle permet de décompresser les images PNG et de les stocker dans la RAM.
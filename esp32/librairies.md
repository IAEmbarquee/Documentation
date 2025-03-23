---
icon: book-open-cover
cover: >-
  https://images.unsplash.com/photo-1585779034823-7e9ac8faec70?crop=entropy&cs=srgb&fm=jpg&ixid=M3wxOTcwMjR8MHwxfHNlYXJjaHw1fHxsaWJyYXJ5fGVufDB8fHx8MTc0MTU1MjM4Mnww&ixlib=rb-4.0.3&q=85
coverY: 0
---

# Librairies

{% tabs %}
{% tab title="IDE Arduino" %}
Afin d'installer les librairies nécessaires pour ce projet, il faut ouvrir l'IDE Arduino et se rendre dans le menu <kbd>Outils > Gérer les bibliothèques</kbd>. Une fenêtre s'ouvre alors et il suffit de rechercher les librairies suivantes et de les installer :
{% endtab %}

{% tab title="IDE VSCode" %}
Afin d'installer les librairies nécessaires pour ce projet, il faut ouvrir l'IDE VSCode et cliquer sur l'icône PlatformIO sur la barre à gauche. Cliquez sur <kbd>PIO Home > Librairies</kbd>. Une fenêtre s'ouvre alors et il suffit de rechercher les librairies suivantes et de les installer :
{% endtab %}
{% endtabs %}

### AsyncTCP

De : _ESP32Async_

La librairie <kbd>AsyncTCP</kbd> est une librairie de gestion de la communication TCP asynchrone pour les cartes ESP32. Elle permet de créer des serveurs et des clients TCP de manière asynchrone, ce qui signifie que les connexions TCP peuvent être gérées de manière non bloquante. Cela permet de gérer plusieurs connexions simultanément sans bloquer le programme principal.

### ESPAsyncWebServer

De : _ESP32Async_

La librairie <kbd>ESPAsyncWebServer</kbd> est une librairie de gestion de serveur web asynchrone pour les cartes ESP32. Elle permet de créer des serveurs web de manière asynchrone grâce à la librairie <kbd>AsyncTCP</kbd>. Cette librairie est très utile pour créer des interfaces web pour les projets IoT basés sur les cartes ESP32.

{% hint style="warning" %}
Parfois, l'installation de ces deux librairies peut entraîner des erreurs de compilation (des librairies en trop sont installées en tant que dépendances, ou bien les bonnes versions ne sont pas installées).

Il est donc préférable de modifier directement le fichier <kbd>platformio.ini</kbd> et rajouter ces lignes :&#x20;

```ini
[env:m5stack-cores3]
platform = espressif32
board = m5stack-cores3
framework = arduino
lib_deps = 
	ESP32Async/AsyncTCP
  	ESP32Async/ESPAsyncWebServer
      	...
```
{% endhint %}

### PNGDec

De : _Larry Bank (bitbank2)_

La librairie <kbd>PNGDec</kbd> est une librairie de décodage des images PNG pour les cartes ESP32. Elle permet de décompresser les images PNG et de les stocker dans la RAM.

### M5Unified

De : _M5Stack_

La librairie <kbd>M5Unified</kbd> est une librairie de gestion des périphériques M5Stack pour les cartes ESP32. Elle permet de contrôler les différents périphériques de la carte M5Stack, tels que l'écran, les boutons, les LEDs, etc. Cette librairie est très utile pour créer des projets basés sur les cartes M5Stack.

{% hint style="info" %}
Il est aussi recommandé d'installer la librairie connexe <kbd>M5GFX</kbd>.
{% endhint %}

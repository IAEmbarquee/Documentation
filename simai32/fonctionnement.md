---
icon: gear-complex-code
cover: >-
  https://images.unsplash.com/photo-1597008641621-cefdcf718025?crop=entropy&cs=srgb&fm=jpg&ixid=M3wxOTcwMjR8MHwxfHNlYXJjaHwzfHxmdW5jdGlvbnxlbnwwfHx8fDE3NDE1NTI4OTV8MA&ixlib=rb-4.0.3&q=85
coverY: 0
layout:
  cover:
    visible: true
    size: full
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Fonctionnement

## Modes

Le simulateur SimAI32 possède 3 modes de fonctionnement :

* Mode <kbd>Label</kbd>&#x20;
  * L’ESP récupère l’image (le panneau) et renvoie le label (la classe de panneau prédite) à Unity&#x20;
  * La gestion de la vitesse est contrôlée par un PID gérée depuis le simulateur (Unity)&#x20;
  * 50% des points possibles
* Mode <kbd>Managed Speed</kbd>&#x20;
  * L’ESP récupère l’image (le panneau) et renvoie la vitesse du véhicule uniquement (entre 0 et 130km/h) à Unity
  * &#x20;La gestion de la vitesse est contrôlée par un PID gérée depuis le simulateur (Unity)&#x20;
  * 100% des points possibles&#x20;
* Mode <kbd>Speed-Break</kbd>
  * &#x20;L’ESP récupère l’image (le panneau) et gère le contrôle de la pédale d’accélération (valeur comprise entre 0 et 1) et de la pédale de frein (valeur comprise entre 0 et 1)&#x20;
  * Ces informations (pédale d’accélération et de frein) sont renvoyées au simulateur Unity.
  * 200% des points possibles

## Envoi et réception de données

<figure><img src="../.gitbook/assets/SchémaSimu.png" alt=""><figcaption></figcaption></figure>

L’ESP32 fait office de serveur HTTP et reçoit des données du simulateur.&#x20;

* Dans un premier temps, on reçoit une image du simulateur (à l’adresse <kbd>/image</kbd>)
  * L'image est au format png (une opération de décompression est donc nécessaire)
  * Vous pouvez choisir la taille de l'image (par défaut sur 32x32)
  * Image en RGB !
* Puis le simulateur envoie des données (à l’adresse <kbd>/data</kbd>) qui devront être parsées correctement suivant ces variables  :&#x20;
  * `speed` (int)&#x20;
  * `odometer` (int)&#x20;
  * `carinfront` (int) | Radar simulé pour déterminer la distance entre un obstacle proche
  * `redlight` (bool) | Est à l’état haut si un feu rouge est proche&#x20;
  * Total : 32 bits
* Enfin, vous renvoyez vos données selon le mode que vous aurez choisi !

## Exemple de payload envoyée par le simulateur

[<kbd><mark style="background-color:blue;">**XXXXXXXX**<mark style="background-color:blue;"></kbd>](#user-content-fn-1)[^1] [<kbd><mark style="background-color:purple;">**XXXXXXXXXXXXXXXX**<mark style="background-color:purple;"></kbd>](#user-content-fn-2)[^2] [<kbd><mark style="background-color:orange;">**XXXXXXX**<mark style="background-color:orange;"></kbd>](#user-content-fn-3)[^3] [<kbd><mark style="background-color:green;">**X**<mark style="background-color:green;"></kbd>](#user-content-fn-4)[^4]&#x20;

Passez votre souris sur les bits 😇

[^1]: **Vitesse (8 bits : max. 256 km/h)**&#x20;

[^2]: **Odomètre (16 bits : max. 65536 m)**

[^3]: **Ultrason (7 bits : max. 128 m)**

[^4]: **Feu rouge en approche (1 bit : booléen)**

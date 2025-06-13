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

## Options

Le simulateur SimAI32 autorise la modification de quelques paramètres de simulation tels que :

* <kbd>Enable NPC</kbd>
  * Permet d'activer/désactiver la présence de voitures IA (ou PNJ) lors de la simulation
* <kbd>Scénario</kbd>
  * Permet de choisir l'un des parcours effectués par la voiture. Actuellement, le simulateur comporte deux parcours :
    * Autoroute | Trajet classique
    * Panneaux en folie | Trajet favorisant le debug, la voiture roule en ligne droite et plein de panneaux sont disposés
* <kbd>Bypass Speed Limits</kbd>
  * Permet de forcer la voiture à rouler à 50 km/h constants (évite de trop accélérer/ralentir la voiture)

{% hint style="warning" %}
Uniquement disponible en mode "Labels". La voiture peut freiner tout de même avec une voiture en face.
{% endhint %}

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

[<kbd><mark style="background-color:blue;">**XXXXXXXX**<mark style="background-color:blue;"></kbd>](#user-content-fn-1)[^1] [<kbd><mark style="background-color:purple;">**XXXXXXXXXXXXXXXX**<mark style="background-color:purple;"></kbd>](#user-content-fn-2)[^2] [<kbd><mark style="background-color:orange;">**XXXXXXX**<mark style="background-color:orange;"></kbd>](#user-content-fn-3)[^3] [<kbd><mark style="background-color:green;">**X**<mark style="background-color:green;"></kbd>](#user-content-fn-4)[^4]  - 32 bits sous forme de `uint32_t`

Cliquez sur les bits pour en savoir plus...😇

## Exemple de payload envoyée par l'ESP32

#### Pour le mode Label

&#x20;[<kbd><mark style="background-color:blue;">XX<mark style="background-color:blue;"></kbd>](#user-content-fn-5)[^5] - réponse sous forme de `int`

#### Pour le mode ManagedSpeed

[<kbd><mark style="background-color:green;">XXX<mark style="background-color:green;"></kbd>](#user-content-fn-6)[^6] - réponse sous forme de `int`

#### Pour le mode Speed/Brake

[<kbd><mark style="background-color:yellow;">XXX<mark style="background-color:yellow;"></kbd>](#user-content-fn-7)[^7]<kbd>,</kbd>[<kbd><mark style="background-color:red;">XXX<mark style="background-color:red;"></kbd>](#user-content-fn-8)[^8] - réponse sous forme de `string`

## Résumé d'un "tick" dans le jeu

Dès lors que vous appuyez sur le bouton "Start", ces actions seront réalisées jusqu'à l'arrêt de la simulation. (par le clic sur le bouton STOP, ou la fin du circuit)

{% stepper %}
{% step %}
### Le simulateur envoie une image à l'ESP32 toutes les 100 ms (10 fps)

Image RGB 32x32 au format PNG
{% endstep %}

{% step %}
### Le simulateur envoie les données voiture à l'ESP32 toutes les 500 ms

Voir [#envoi-et-reception-de-donnees](fonctionnement.md#envoi-et-reception-de-donnees "mention")
{% endstep %}

{% step %}
### L'ESP32 répond avec le bon format de données

Voir [#envoi-et-reception-de-donnees](fonctionnement.md#envoi-et-reception-de-donnees "mention")
{% endstep %}
{% endstepper %}



[^1]: **Vitesse (8 bits : max. 256 km/h)**&#x20;

[^2]: **Odomètre (16 bits : max. 65536 m)**

[^3]: **Ultrason (7 bits : max. 128 m)**

[^4]: **Feu rouge en approche (1 bit : booléen)**

[^5]: Classe du panneau

[^6]: Vitesse désirée (valeur entre 0 et 255)

[^7]: Accélérateur (valeur entre 0.00 et 1.00)

[^8]: Frein (valeur entre 0.00 et 1.00)

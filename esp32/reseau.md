---
icon: chart-network
cover: >-
  https://images.unsplash.com/photo-1545987796-200677ee1011?crop=entropy&cs=srgb&fm=jpg&ixid=M3wxOTcwMjR8MHwxfHNlYXJjaHwxfHxuZXR3b3JrfGVufDB8fHx8MTc0MTU0NDc5Mnww&ixlib=rb-4.0.3&q=85
coverY: 0
---

# Réseau

## Introduction

Afin de pouvoir communiquer avec l'ESP32, quatre protocoles de communication sont disponibles : la liaison série à travers le port USB-C, le Bluetooth (trop lent pour assurer la transmission d'images), ESP-NOW (communication entre les ESP) et enfin le réseau Wi-Fi. Ce dernier possède une latence faible et un débit élevé ce qui en fait le parfait candidat pour ce projet.

Nous allons donc avoir besoin d'un routeur Wi-Fi pour connecter l'ESP32 à l'ordinateur.

## Configuration du réseau Wi-Fi

* **SSID** : <kbd>SimAI32</kbd>
* **Mot de passe** : <kbd>Le même que pour accès TailScale</kbd>&#x20;
* **Bande de fréquence** : <kbd>2.4 GHz</kbd> (Wi-Fi 4 ou 802.11n)

{% hint style="danger" %}
L'ESP32 que nous possédons peut techniquement se connecter à un réseau 5GHz mais pour des raisons de stabilité il est impératif de régler le réseau Wi-Fi uniquement sur la bande 2.4 GHz.
{% endhint %}

Plutôt facile, non ? Vous pouvez maintenant passer à la suite.

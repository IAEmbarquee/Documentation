---
weight: 22
title: "Réseau"
description: "Communication entre ESP32 et l'ordinateur."
icon: lan
date: "2024-08-02T16:40:08+02:00"
lastmod: "2024-08-02T16:40:08+02:00"
draft: false
toc: true
---

### Introduction

Afin de pouvoir communiquer avec l'ESP32, quatre protocoles de communication sont disponibles : la liaison série à travers le port USB-C, le Bluetooth (trop lent pour assurer la transmission d'images), ESP-NOW (communication entre les ESP) et enfin le réseau Wi-Fi. Ce dernier possède une latence faible et un débit élevé ce qui en fait le parfait candidat pour ce projet.

Nous allons donc avoir besoin d'un routeur Wi-Fi pour connecter l'ESP32 à l'ordinateur. Voici les caractéristiques du réseau que vous devez configurer (petits souvenirs de RC3) :

### Configuration du réseau Wi-Fi

- **SSID** : `SimAI32-TableX` (X étant le numéro de la table)
- **Mot de passe** : `TableX` (X étant le numéro de la table)
- **Bande de fréquence** : `2.4 GHz` (Wi-Fi 4 ou 802.11n)

{{< alert context="warning" text="L'ESP32 que nous possédons peut techniquement se connecter à un réseau 5GHz mais pour des raisons de stabilité il est impératif de régler le réseau Wi-Fi uniquement sur la bande 2.4 GHz." />}}

### Configuration des adresses IP

- **Adresse IP de l'ESP32** : `IP Statique en 192.168.1.50`
- **Adresse IP de l'ordinateur** : `DHCP`

### Schéma final

![](https://raw.githubusercontent.com/MetrixMedia/EmbeddedAI-Documentation/main/assets/images/networking.png)

Plutôt facile, non ? Vous pouvez maintenant passer à la suite.
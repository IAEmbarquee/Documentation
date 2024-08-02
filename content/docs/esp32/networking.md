---
weight: 22
title: "Réseau"
description: "Communication ESP-32 et Ordinateur"
icon: lan
date: "2024-08-02T16:40:08+02:00"
lastmod: "2024-08-02T16:40:08+02:00"
draft: false
toc: true
---

Afin de pouvoir communiquer avec l'ESP-32, quatre protocoles de communication sont disponibles : la liaison série à travers le port USB-C, le Bluetooth (trop lent pour assurer la transmission d'images), ESP-NOW (communication entre les ESP) et enfin le réseau Wi-Fi. Celui-ci possède une latence faible et un débit élevé ce qui en fait le parfait candidat pour ce projet.
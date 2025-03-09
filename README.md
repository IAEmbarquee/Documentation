---
noIndex: true
noRobotsIndex: true
icon: house
cover: >-
  https://images.unsplash.com/photo-1644688389824-adbf547b229f?crop=entropy&cs=srgb&fm=jpg&ixid=M3wxOTcwMjR8MHwxfHNlYXJjaHw4fHxzaW11bGF0aW9ufGVufDB8fHx8MTc0MTU2MDIzMnww&ixlib=rb-4.0.3&q=85
coverY: 0
layout:
  cover:
    visible: true
    size: full
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: false
  outline:
    visible: false
  pagination:
    visible: false
---

# SimAI32

## Documentation pour le module d’IA Embarquée enseigné à l’I.U.T. Nice Côte d’Azur

Le simulateur **SimAI32** est un outil de simulation pour véhicules autonomes avec plusieurs trajets prédéfinis et trois modes de fonctionnement. Selon le mode (Label, Managed Speed ou Speed-Break), l’ESP analyse les panneaux de signalisation grâce à un modèle de classification CNN et ajuste soit le label, la vitesse ou le contrôle total de l'accélération et du freinage, influençant ainsi le score obtenu.

Démarrez ici :

{% content-ref url="introduction.md" %}
[introduction.md](introduction.md)
{% endcontent-ref %}

### Version 1.0.1 - **Open Source** MIT Licensed.

© 2025 hugofnm / LEAT / Université Côte d’Azur

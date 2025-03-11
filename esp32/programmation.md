---
icon: computer-classic
cover: >-
  https://images.unsplash.com/photo-1525547719571-a2d4ac8945e2?crop=entropy&cs=srgb&fm=jpg&ixid=M3wxOTcwMjR8MHwxfHNlYXJjaHwzfHxjb21wdXRlcnxlbnwwfHx8fDE3NDE1NDQ2NTZ8MA&ixlib=rb-4.0.3&q=85
coverY: 0
---

# Programmation

Veuillez récupérer le squelette de programme suivant pour commencer à programmer l'ESP32 :

[Télécharger le squelette de programme](https://gitlab.hugofnm.fr/simai32/simai32/-/tree/master/ESP32/)

## Squelette de programme - Phase 1

### Informations sur les panneaux inclus

<table data-view="cards"><thead><tr><th></th><th data-hidden data-card-cover data-type="files"></th></tr></thead><tbody><tr><td>Panneau 70</td><td><a href="../.gitbook/assets/panneau1.png">panneau1.png</a></td></tr><tr><td>Panneau Chaussée Glissante</td><td><a href="../.gitbook/assets/panneau2.png">panneau2.png</a></td></tr><tr><td>Panneau Tout Droit</td><td><a href="../.gitbook/assets/panneau3.png">panneau3.png</a></td></tr></tbody></table>

### Code

{% hint style="warning" %}
Ne comprend pas tout le code. Veuillez le télécharger depuis le lien au-dessus.
{% endhint %}

<pre class="language-cpp"><code class="lang-cpp">/*
    ESP32 - IA Embarquée - GTSRB
    Université Côte d'Azur
    Hugo Meleiro - LEAT
*/

#include &#x3C;Arduino.h> // Include the Arduino library
#include "model.h" // Include the model header file
#include "trafficsigns.h"

static input_t inputs;
static output_t outputs;

unsigned long StartTime;
unsigned long CurrentTime;

int cpt = 0;

void setup() {
    Serial.begin(115200);
    Serial.println("Ready !");
    
    for (int i = 0; i &#x3C; 32; i++) {
        for (int j = 0; j &#x3C; 32; j++) {
            for (int k = 0; k &#x3C; 3; k++) {
                inputs[i][j][k] = trafficsign1[i * 32 * 3 + j * 3 + k];
            }
        }
    }
}

void loop() {
    if (cpt == 0) {
        // Cette fonction réalise l'inférence du modèle
        cnn(inputs,outputs);
    
        // TODO : Ajoutez ici votre code pour calculer le softmax,
        // afficher la classe prédite  
        // et calculer le temps d'inférence
    
        // TODO ...
        int label = 0;
        float softmax[99];
    
        // Print the label predicted
        if(softmax[label] >= 0.9) {
<strong>            switch(label){
</strong>                case 0 : Serial.println("Class Predicted : 20 km/h"); break;
                case 1 : Serial.println("Class Predicted : 30 km/h"); break;
                case 2 : Serial.println("Class Predicted : 50 km/h"); break;
                case 3 : Serial.println("Class Predicted : 60 km/h"); break;
                case 4 : Serial.println("Class Predicted : 70 km/h"); break;
                case 5 : Serial.println("Class Predicted : 80 km/h"); break;
                case 6 : Serial.println("Class Predicted : 100 km/h"); break;
                case 7 : Serial.println("Class Predicted : 120 km/h"); break;
                case 8 : Serial.println("Class Predicted : Wrong way"); break;
                case 9 : Serial.println("Class Predicted : Stop"); break;
                case 10 : Serial.println("Class Predicted : Yield"); break;
                case 11 : Serial.println("Class Predicted : Danger"); break;
                case 12 : Serial.println("Class Predicted : Dangerous left turn"); break;
                case 13 : Serial.println("Class Predicted : Dangerous right turn"); break;
                case 14 : Serial.println("Class Predicted : Winding road"); break;
                case 15 : Serial.println("Class Predicted : Slippery road"); break;
                case 16 : Serial.println("Class Predicted : Crosswalk"); break;
                case 17 : Serial.println("Class Predicted : Bicycles"); break;
                case 18 : Serial.println("Class Predicted : Animals"); break;
                case 19 : Serial.println("Class Predicted : Red light"); break;
                case 20 : Serial.println("Class Predicted : Road bumps"); break;
                case 21 : Serial.println("Class Predicted : Workers ahead"); break;
                case 22 : Serial.println("Class Predicted : Right or Forward"); break;
                case 23 : Serial.println("Class Predicted : Left or Forward"); break;
                case 24 : Serial.println("Class Predicted : Right"); break;
                case 25 : Serial.println("Class Predicted : Left"); break;
                case 26 : Serial.println("Class Predicted : Forward"); break;
                case 27 : Serial.println("Class Predicted : End of game"); break;
                default : Serial.println("Error !"); break;
            }
            cpt++;
        } else {
            Serial.println("No class detected");
        }
    }
}
</code></pre>

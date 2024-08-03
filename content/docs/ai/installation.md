---
weight: 32
title: "Installation et configuration"
description: "Docker et JupyterLab."
icon: download
lead: ""
date: 2022-10-10T02:21:15+00:00
lastmod: 2022-10-10T02:21:15+00:00
draft: false
images: []
---

Afin de pouvoir entraîner et déployer des modèles d'IA sur Qualia, vous aurez besoin d'installer et de configurer Docker et JupyterLab sur votre machine. Dans ce guide, nous allons vous montrer comment installer ces outils et les configurer pour travailler avec Qualia.

### Installation de Docker

Docker est un outil de virtualisation qui permet de créer des conteneurs légers et portables pour exécuter des applications. Pour installer Docker sur votre machine, suivez les instructions ci-dessous :

{{< tabs tabTotal="3">}}
{{% tab tabName="Installation compatible avec les GPUs" %}}

1. Tout d'abord, vérifiez que votre machine est compatible avec WSL 2 (Windows Subsystem for Linux 2). Pour cela, ouvrez une invite PowerShell en tant qu'administrateur et exécutez la commande suivante :

    ```bash
    wsl --set-default-version 2
    wsl --install -d Debian
    ```

    Si vous obtenez une erreur, cela signifie que votre machine n'est pas compatible avec WSL 2. Dans ce cas, vous devrez mettre à jour votre système d'exploitation vers Windows 10 version 2004 ou supérieur (Build 19041 ou supérieur) or Windows 11.

2. Téléchargez l'exécutable sur le site officiel de Docker à l'adresse suivante : [Docker](https://desktop.docker.com/win/main/amd64/Docker%20Desktop%20Installer.exe).
3. Lorsque vous y êtes invité, assurez-vous que l'option Utiliser WSL 2 au lieu d'Hyper-V sur la page de configuration est sélectionnée.
4. Suivez les instructions d'installation pour terminer le processus.
5. Ouvrez Docker Desktop pour démarrer le service Docker.
6. Désormais, ouvrez une invite de commande et exécutez les commandes suivantes pour lancer un conteneur TensorFlow avec prise en charge GPU :

    ```bash
    docker run -d --gpus all -it -u root -p 8888:8888 -v $(pwd):/workspace --shm-size=256m tensorflow/tensorflow:2.14.0-gpu
    ```

{{% /tab %}}
{{% tab tabName="Installation CPU" %}}

1. Téléchargez l'installateur Docker Desktop pour Windows à partir du site officiel de Docker : [Docker Desktop](https://desktop.docker.com/win/main/amd64/Docker%20Desktop%20Installer.exe).
2. Suivez les instructions d'installation pour terminer le processus.
3. Ouvrez Docker Desktop pour démarrer le service Docker.
4. Désormais, ouvrez une invite de commande et exécutez les commandes suivantes pour lancer un conteneur TensorFlow :

    ```bash
    docker run -it --rm -p 8888:8888 tensorflow/tensorflow:2.14.0
    ```

{{% /tab %}}
{{% tab tabName="Google Collab" %}}

Vous pouvez également utiliser Google Collab pour entraîner vos modèles d'IA. 
Téléchargez le fichier Jupyter Notebook sur votre ordinateur et importez-le dans Google Collab pour l'exécuter.

[Google Collab](https://colab.research.google.com/)

{{% /tab %}}
{{< /tabs >}}

### Installation de JupyterLab

1. Une fois le conteneur Docker lancé, ouvrez une invite de commande et exécutez la commande suivante :

    ```bash
    docker ps -a
    ```

    Vous devriez voir un conteneur en cours d'exécution avec l'image TensorFlow. Notez l'ID du conteneur.

    ```bash
    Sortie :
    CONTAINER ID        IMAGE                              COMMAND             CREATED             STATUS              PORTS                    NAMES
    f95b6ac4e565        tensorflow/tensorflow:latest-gpu   "/bin/bash"         4 seconds ago       Up 2 seconds        0.0.0.0:8888->8888/tcp   competent_robinson
    ```

2. Exécutez la commande suivante pour accéder à l'interface JupyterLab :

    ```bash
    docker exec -it -u root CONTAINER_ID bash
    ```

    ```bash
    Sortie :
    ________                               _______________                
    ___  __/__________________________________  ____/__  /________      __
    __  /  _  _ \_  __ \_  ___/  __ \_  ___/_  /_   __  /_  __ \_ | /| / /
    _  /   /  __/  / / /(__  )/ /_/ /  /   _  __/   _  / / /_/ /_ |/ |/ / 
    /_/    \___//_/ /_//____/ \____//_/    /_/      /_/  \____/____/|__/


    WARNING: You are running this container as root, which can cause new files in
    mounted volumes to be created as the root user on your host machine.

    To avoid this, run the container by specifying your user's userid:

    $ docker run -u $(id -u):$(id -g) args...

    root@f95b6ac4e565:/# 
    ```

3. Exécutez les commandes suivantes pour mettre à jour les paquets et installer JupyterLab :

    ```bash
    apt update; apt -y upgrade
    mkdir .local .jupyter .cache .cache/pip
    chmod 777 .local .jupyter .cache .cache/pip
    pip install jupyterlab
    exit
    ```

4. Exécutez la commande suivante pour démarrer JupyterLab :

    ```bash
    docker exec -it -u $(id -u):$(id -g) CONTAINER_ID bash
    ```

    ```bash
    Sortie :
    ________                               _______________                
    ___  __/__________________________________  ____/__  /________      __
    __  /  _  _ \_  __ \_  ___/  __ \_  ___/_  /_   __  /_  __ \_ | /| / /
    _  /   /  __/  / / /(__  )/ /_/ /  /   _  __/   _  / / /_/ /_ |/ |/ / 
    /_/    \___//_/ /_//____/ \____//_/    /_/      /_/  \____/____/|__/


    You are running this container as user with ID 1000 and group 1000,
    which should map to the ID and group for your user on the Docker host. Great!

    tf-docker / >
    ```

5. Exécutez la commande suivante pour définir un mot de passe pour JupyterLab :

    ```bash
    export PATH=/.local/bin:$PATH
    jupyter lab password
    ```

6. Enfin, exécutez la commande suivante pour démarrer JupyterLab :

    ```bash
    cd workspace
    jupyter lab --no-browser --ip=*
    ```

7. Ouvrez un navigateur web et accédez à l'URL suivante pour accéder à l'interface JupyterLab : [http://localhost:8888/lab](http://localhost:8888/lab).

### Télécharger le notebook

Vous pouvez télécharger le notebook qui va servir de ligne de base pour votre projet d'IA Embarquée en cliquant sur le lien suivant : [Télécharger le notebook](https://simai32.hugofnm.fr/download?q=notebook).
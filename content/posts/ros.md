---
title: "Installation de ROS pour le Niryo Ned²"
date: 2023-03-09T19:00:56+01:00
draft: false
subtitle: ""
---

## Matériel et logiciels nécessaires

- Ordinateur compatible avec Ubuntu 18.04 (une patate peut suffir)
- Clé USB de plus de 8Go pour l'installation de Linux

## Procédure d'installation

### 1 - Installation d'Ubuntu 18.04

Premièrement, nous installons la version d'Ubuntu 18.04.5 LTS que nous téléchargeons sur le [site](https://ubuntu.com) officiel Ubuntu.

### 2 - Installation de ROS sur Ubuntu

Pour faire cela, nous allons sur la [page d'installation](https://docs.niryo.com/dev/ros/v4.1.1/en/source/installation/ubuntu_18.html) officielle de Niryo afin d'avoir toutes les commandes nécessaires pour l'installation.

Voici les commandes à exéctuer dans l'ordre :

```sh
# Mettre à jour le système avant toute installation.
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

```sh
# Installation des paquets pré-requis.
sudo apt-get install build-essential sqlite3 ffmpeg
```

```sh
# Cloner le répertoire du robot depuis Github et entrer dans le dossier
git clone https://github.com/NiryoRobotics/ned_ros
cd ned_ros
```

```sh
# Installation de l'environnement Python pour ROS
pip2 install -r requirements_ned2.txt
```

```sh
# Mise en place de ROS
# à l'aide de la commande suivante, nous devons créer un dossier source
mkdir -p ~/catkin_ws_niryo_ned/src
```

```sh
# On clone le répertoire dans le dossier qu'on vient de créer
cd catkin_ws_niryo_ned
git clone https://github.com/NiryoRobotics/ned_ros src
```

### 3 - Installation de ROS Melodic

À partir du [site](http://wiki.ros.org/melodic/Installation/Ubuntu) officiel de la documentation de ROS, on va installer l'environnement de travail ROS

Commandes à exécuter : 

```sh
# Ajouter de dépôt de ROS
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
```

```sh
# Installer curl si il ne l'est pas déjà
sudo apt install curl
# Ajouter les clés GPG pour les paquets ROS
curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
```

```sh
# On met à jour les dépôts pour ensuite installer les logiciels ROS
sudo apt update
```

```sh
# Installation complète de ROS incluant les logiciels de simulation
sudo apt install ros-melodic-desktop-full
```

### 4 - Environnement de travail

Pour utiliser ROS, on doit lancer le fichier /opt/ros/melodic/setup.bash à chaque démarrage. Pour cela, il faut ajouter la commande pour le lancer dans ~/.bashrc avec cette commande :

```sh
echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc
```

### 5 - Gestion des paquets ROS

Pour utiliser la commande `rosinstall` il faut installer quelques paquets préliminaires.

```sh
sudo apt install python-rosdep python-rosinstall python-rosinstall-generator python-wstool build-essential
```

```sh
# Installation de rosdep
sudo apt install python-rosdep

# Initialisation de rosdep
sudo rosdep init
# À l'initialisation, il vous sera demandé de mettre à jour rosdep
rosdep update
```

```sh
# Il faut ensuite installer d'autres paquets avec rosdep
rosdep update
rosdep install --from-paths src --ignore-src --default-yes --rosdistro melodic --skip-keys "python-rpi.gpio"
```

### 6 - Mise en place de l'environnement de travail Ned²

Pour simuler le robot Ned², il faut mettre en place un dossier contenant la configuration du robot.

```sh
#Se déplacer dans le dossier catkin
cd ~/catkin_ws_niryo_ned
```

```sh
# Installer l'environnement de travail catkin
catkin_make
```

Il faudra ensuite préparer le terminal à lancer la simulation. Il est conseillé de mettre cette commande dans le fichier ~/.bashrc si vous utilisez ROS sur une machine dédiée.

```sh
# Exécuter une seule fois
source devel/setup.bash

# Exécution automatique
echo "source ~/catkin_ws_niryo_ned/devel/setup.bash" >> ~/.bashrc
```

## Lancement de la simulation

On lancera la simulation avec le logiciel Gazebo, car il supporte la physique de l'environnement, comme la gravité ou encore le vent.

Dans un terminal il faut lancer le coeur de la simulation avec la commande `roscore`

Dans un autre terminal il faut lancer la visualisation du Ned² avec cette commande : 

```sh
roslaunch niryo_robot_bringup desktop_gazebo_simulation.launch hardware_version:=ned2
```

L'option `hardware_version` sert à spécifier la version du robot à simuler, comme le Ned, Ned2 et le One.

## Conclusion

Si tout c'est bien passé, la simulation fonctionne et on peut contrôler le robot avec Niryo Studio en le connectant avec l'IP 127.0.0.1
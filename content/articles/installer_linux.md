---
title: "Comment installer Linux ?"
date: 2022-07-17T14:16:28+02:00
draft: true
subtitle: "Guide pour installer Linux"
---

### Introduction

Installer Linux peut sembler complexe, mais nous allons voir dans ce guide que la réalité est toute autre.

### Pourquoi diable installer Linux ?

Si vous avez un ordinateur qui commence à ralentir sans raison, c'est peut être votre système d'exploitation qui en demande toujours plus. En effet, les recommandations pour Windows 11 forcent beaucoup d'utilisateurs à changer d'ordinateur en raison de leur configuration "insuffisante"

![Recommandations système pour Windows 11](img_article/installer_linux/recommandations_win11.png)
*Configuration système requise pour Windows 11*

La différence avec Linux est que la configuration système requise est bien moindre. Par exemple, Les Raspberry Pi, des ordinateurs à 40€ fonctionnent sous Linux, et ces ordinateurs sont utilisables au quotidien.

### Choisir sa distribution

Si vous débutez, il est préférable de choisir une distribution prévue pour les nouveaux utilisateurs, comme par exemple [Linux Mint](https://linuxmint.com/) si vous venez de Windows, ou [Elementary OS](https://elementary.io/fr/) pour ceux habitués à MacOS. Si votre but est de jouer sur Linux, [Pop!_OS](https://pop.system76.com/) est un bon choix car cette distribution est facile à utiliser et facilite beaucoup de choses pour installer les drivers de carte graphique par exemple.

Pour ce guide nous allons installer Linux Mint dans sa version Cinnamon, car c'est la distribution que je conseillerai au plus grand nombre de personnes. Mais vous pouvez également installer la version XFCE si votre ordinateur n'est pas très performant, la procédure d'installation ne change en aucun point.

### Tester avant de franchir le pas

Avant de se lancer dans l'installation d'une distribution Linux, il est intéressant de la tester dans une machine virtuelle, grâce à un logiciel comme [VirtualBox](https://www.virtualbox.org/).

Le procédé pour installer Linux sur une machine virtuelle et sur un ordinateur réel est sensiblement le même, donc je détaillerai seulement l'installation sur machine virtuelle.

#### Télécharger les prérequis

Pour installer une distribution Linux, il vous faudra une image ISO, téléchargeable la plupart du temps sur le site de la distribution. Pour Linux Mint, voici [le lien](https://linuxmint.com/download.php).

Pour l'installation sur une machine virtuelle, il va falloir installer un logiciel de virtualisation, ici VirtualBox. Téléchargez et installez donc grâce à [ce lien](https://www.virtualbox.org/wiki/Downloads).

Si vous souhaitez installer sur un ordinateur réel, il vous faudra une clé USB de 8Go ou plus, et un logiciel comme [Etcher](https://www.balena.io/etcher/) pour flasher l'ISO sur la clé USB.

#### Préparer la machine virtuelle

Ouvrez VirtualBox, et créez une nouvelle machine avec ce bouton

![Bouton nouvelle machine](img_article/installer_linux/new.png)

### Pour de vrai maintenant
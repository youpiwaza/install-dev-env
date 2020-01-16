# Mise à jour de l'environnement de développement

Histoire de partir sur de bonnes bases.

Installation complète d'un environnement de dev sous Windows.

*Lexique* :

- WLS / Windows Linux Subsystem (Ubuntu "natif" sur windows)
- ZSH / Un terminal (ligne de commande)
- OMZ / Oh-My-Zsh, moteur de thème pour ZSH ^

## Installer ubuntu pour windows

- [Windows Subsystem for Linux Installation Guide for Windows 10](https://docs.microsoft.com/en-us/windows/wsl/install-win10)
  - [MS store ubuntu](https://www.microsoft.com/en-us/p/ubuntu/9nblggh4msv6)

1. Télécharger
2. Lancer
3. Choisir username & password
4. [Mise à jour de l'OS](sudo apt update && sudo apt upgrade) / Maj & update package list

> sudo apt update && sudo apt upgrade

## Installation du terminal

[Readme dédié](01-terminal/README.md)

*Note* : Cela comprend l'installation d'ansible grâce au script utilisé.

## Installation de docker et ses potes

[Readme dédié](02-docker/README.md)

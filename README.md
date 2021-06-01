# Mise à jour de l'environnement de développement

Histoire de partir sur de bonnes bases.

Installation complète d'un environnement de dev sous Windows.

*Lexique* :

- WLS / Windows Linux Subsystem (Ubuntu "natif" sur windows)
- ZSH / Un terminal (ligne de commande)
- OMZ / Oh-My-Zsh, moteur de thème pour ZSH ^

## Installer ubuntu pour windows

- [Kwaksé](https://docs.microsoft.com/fr-fr/windows/wsl/about)
- [Windows Subsystem for Linux Installation Guide for Windows 10](https://docs.microsoft.com/fr-fr/windows/wsl/install-win10)
  - [MS store ubuntu](https://www.microsoft.com/fr-fr/p/ubuntu-2004-lts/9n6svws3rx71)

1. Télécharger
2. Lancer
3. Choisir username & password
4. [Mise à jour de l'OS](sudo apt update && sudo apt upgrade) / Maj & update package list

```bash
# Mettre à jour la liste des paquets, puis mettre à jour les paquets
#   Note: Ca prend un peu de temps mais besoin de confirmer avec "Y" alors attention
sudo apt update && sudo apt upgrade
```

## Installer le terminal sur Windows > WSL (Windows Sub Linux > Ubuntu 20) : OMZ & p10K

[Readme dédié](01-terminal/README.md)

*Note* : Cela comprend l'installation d'ansible grâce au script utilisé.

## Installation de docker et ses potes

[Readme dédié](02-docker/README.md)

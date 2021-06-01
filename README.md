# Mise à jour de l'environnement de développement

Histoire de partir sur de bonnes bases.

Installation complète d'un environnement de dev sous Windows.

*Lexique* :

- WSL / 🐧 Windows Linux Subsystem (Ubuntu "natif" sur windows)
- ZSH / 🖥️ Un terminal (ligne de commande, comme *shell*/*bash* may mieux)
- OMZ / 💅 Oh-My-Zsh, moteur de thème pour ZSH ^
- p10k / 🐲 Le thème *PowerLevel10k* pour OMZ

## Installer ubuntu LTS pour windows 10

- [Kwaksé](https://docs.microsoft.com/fr-fr/windows/wsl/about)
- [Windows Subsystem for Linux Installation Guide for Windows 10](https://docs.microsoft.com/fr-fr/windows/wsl/install-win10)
  - [MS store ubuntu](https://www.microsoft.com/fr-fr/p/ubuntu-2004-lts/9n6svws3rx71)

1. Télécharger
2. Lancer
3. Choisir username & password
4. Mise à jour de l'OS

```bash
## Mettre à jour la liste des paquets/packages, puis mettre à jour les paquets
##   Note: Ca prend un peu de temps mais besoin de confirmer avec "Y" vers le début
sudo apt update && sudo apt upgrade
```

## Installer le terminal sur Windows > WSL (Windows Sub Linux > Ubuntu 20) : OMZ & p10K

[Readme dédié](01-terminal/README.md)

*Note* : Cela comprend l'installation d'Ansible grâce au script utilisé.

## Installation de docker et ses potes

[Readme dédié](02-docker/README.md)

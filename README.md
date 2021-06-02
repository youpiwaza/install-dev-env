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
sudo apt update && sudo apt upgrade -y && sudo apt-get update && sudo apt-get install -y

## Note: Vos DD/fichiers sont accessibles depuis la racine > mnt/
# cd ../..
cd /mnt/c
ls -la
# total 71688
# drwxrwxrwx 1 youpiwaza youpiwaza      512 Jul  1  2018 '$Recycle.Bin'
# drwxrwxrwx 1 youpiwaza youpiwaza      512 Jun  1 21:05  .
# drwxr-xr-x 5 root      root          4096 Jun  1 21:14  ..
# lrwxrwxrwx 1 youpiwaza youpiwaza       12 Jul  1  2018 'Documents and Settings' -> /mnt/c/Users
# drwxrwxrwx 1 youpiwaza youpiwaza      512 Apr  6 08:40 'Program Files'
# drwxrwxrwx 1 youpiwaza youpiwaza      512 Apr  8 10:16 'Program Files (x86)'
# drwxrwxrwx 1 youpiwaza youpiwaza      512 Nov 30  2020  Users
# drwxrwxrwx 1 youpiwaza youpiwaza      512 May 27 08:59  Windows
```

## Installer le terminal sur Windows > WSL (Windows Sub Linux > Ubuntu 20) : OMZ & p10K

[Readme dédié](01-terminal/README.md)

*Note* : Cela comprend l'installation d'Ansible grâce au script utilisé.

## Installation de docker et ses potes

[Readme dédié](02-docker/README.md)

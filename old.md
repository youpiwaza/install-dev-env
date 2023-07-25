# 👴 *deprecated* Ancienne installation de WSL (2022)

1. Passer les [pré-requis via Powershell](https://docs.microsoft.com/fr-fr/windows/wsl/install-manual#step-4---download-the-linux-kernel-update-package), ne faire que les étapes 1 à 3
2. [Installer WSL 2 via Powershell](https://docs.microsoft.com/fr-fr/windows/wsl/install)
3. [Config alakon](https://docs.microsoft.com/fr-fr/windows/wsl/setup/environment) user & pass root
4. Pour les mises à jour, passer par les recos habituelles, mon github > todo > tâches récurrentes, sinon ci-dessous

Puis, sous le terminal nouvellement installé..

```bash
## Mettre à jour la liste des paquets/packages, puis mettre à jour les paquets
sudo apt update && sudo apt --fix-broken install && sudo apt -y upgrade

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

---

## (Optionnel) Switcher sur l'utilisateur root par défaut

Parce que l'utilisateur normal peut déconner/merder au niveau de l'attribution des droits, et parce que `sudo` c'relou en local

```bash
## Depuis un INVITE DE COMMANDE WINDOWS, lancé en administrateur
##    https://superuser.com/questions/1107986/how-to-sign-into-root-account-by-default-on-windows-subsystem-for-linux-bash-t#comment2465514_1291457
## Ubuntu 18
ubuntu config --default-user root

## Ubuntu 20+
ubuntu2004 config --default-user root
```

(Relancer le terminal WSL > Ubuntu)

---

## Mise à jour vers la dernière version d'Ubuntu

Un [article](https://linuxconfig.org/how-to-upgrade-ubuntu-to-22-04-lts-jammy-jellyfish) dédié.

```bash
# Assurer les dernières maj & suppressions des paquets deprecated
sudo apt dist-upgrade && sudo apt -y autoremove

# Installation du paquet de maj
sudo apt install update-manager-core

# Installer la dernière version, même si elle n'est pas encore sortie (~22.04)
#   🚨 Attention, besoin d'actions manuelles de validation
sudo do-release-upgrade -d

# (Restart du terminal)

# Vérifier la version
lsb_release -a

# Dernière maj paquets au cazou
sudo apt update && sudo apt --fix-broken install && sudo apt -y upgrade && sudo apt dist-upgrade && sudo apt -y autoremove
```

---

## (Optionnel) Installation des paquets usuels

- NodeJs, npm, yarn
- python

```bash
# Installations chainées
echo "deb https://dl.yarnpkg.com/debian/ stable main" && \
sudo apt update && \
sudo apt -y install nodejs && \
sudo apt -y install npm && \
sudo apt -y install yarn && \
sudo apt -y install software-properties-common && \
sudo add-apt-repository ppa:deadsnakes/ppa -y && \
sudo apt -y install python3.11

# Vérifications
echo "test node: " && nodejs -v && \
echo "test npm: " && npm -v && \
echo "test python3: " && python3.11 --version && \
echo "test yarn: " && yarn --version
```

---

## Installer le terminal sur Windows > WSL (Windows Sub Linux > Ubuntu 22) : OMZ & p10K

[Readme dédié](01-terminal/README.md)

*Notes* :

- Comprend l'installation d'Ansible grâce au script utilisé.
- Comprend l'stallation du CLI github, via homebrew (installé également)

---

## (Nouveau) Terminal windows

La [doc officielle](https://docs.microsoft.com/fr-FR/windows/terminal/install).

1. 💩 Lancer l'installation depuis le store crosoft
   1. Téléchargement KO lel

---

## (Optionnel) Mise en place de connexion SSH depuis WSL

Permet un accès direct au serveur depuis WSL. En gros partager les fichiers de clés de windows via un lien.

WSL2 a besoin d'un peu plus de conf:

- [SO / Ubuntu on windows 10 wsl2 - chown chmod doesn't work on copied files](https://stackoverflow.com/questions/63600692/ubuntu-on-windows-10-wsl2-chown-chmod-doesnt-work-on-copied-files)
- ['crosoft > Sharing SSH keys between Windows and WSL 2](https://devblogs.microsoft.com/commandline/sharing-ssh-keys-between-windows-and-wsl-2/)
- [old article, but see comments](https://florianbrinkmann.com/en/ssh-key-and-the-windows-subsystem-for-linux-3436/).

```bash
## Ajouter la gestion des metadatas à wsl
nano /etc/wsl.conf
```

Rajouter dans la conf..

```ini
[automount]
enabled = true
options = "metadata,uid=1000,gid=1000,umask=0022,fmask=11,case=off"
mountFsTab = false
crossDistro = true

[filesystem]
umask = 0022

[network]
generateHosts = true
generateResolvConf = true

[interop]
enabled = true
appendWindowsPath = true
```

Puis **forcer le redémarrage** du terminal WSL via **(WINDOWS) > CMD** (en admin) > `wsl --shutdown`.

```bash
## Dossier de l'utilisateur courant
cd

## Création du lien symbolique vers les clés SSH windows
# ln -s /mnt/c/Users/WINDOWS_USER/.ssh ~/.ssh
ln -s /mnt/c/Users/masam/.ssh ~/.ssh

## Ajustement des droits
# chown UBUNTU_USER:UBUNTU_USER ~/.ssh 
# chown UBUNTU_USER:UBUNTU_USER ~/.ssh/*
chown root:root ~/.ssh 
chown root:root ~/.ssh/*
## Note: Si les clés ne sont pas chmod 600 (ou moins), c'est considéré comme une faille de sécurité et elles ne fonctionnent pas
chmod 600 ~/.ssh/*

ls -la
# ...
# lrwxrwxrwx  1 UBUNTU_USER UBUNTU_USER    26 Jun  2 11:49 .ssh -> /mnt/c/Users/WINDOWS_USER/.ssh

ls -lah ~/.ssh/
```

Note: Toujours pas de solution miracle pour connexion en 1 commande (`.ssh/config` redemande la passphrase systématiquement..)

cf. [Repo dédié](https://github.com/youpiwaza/server-related-tutorials/tree/master/02-ansible/01-configuration-ssh) pour les détails.

---

## Installation de docker et ses potes

[Readme dédié](02-docker/README.md)

---

## Recos supplémentaires de nick

cf. l'[article correspondant](https://nickjanetakis.com/blog/the-tools-i-use).

- [PowerToys](https://github.com/microsoft/PowerToys) / Plein d'utilitaires pour les tâches courantes / Alt + space > lancer un programme
- 💖 [Ditto](https://ditto-cp.sourceforge.io/) / Copier collers multiples + recherche dans historique / [Setup avec terminal](https://nickjanetakis.com/blog/boosting-software-developer-productivity-with-a-clipboard-manager)

---

### Maintenance docker & WSL

#### Maj Docker Desktop

1. Lancer le bousin
2. Attendre qu'il soit effectivement lancé
3. Barre des tâches > Icône > Clic droit > ~"Check for updates"
4. Attendre et lui tenir la main pendant approximativement 107 ans
5. ..
6. Profits

#### Restreindre WSL2 en RAM

[blah](https://youtu.be/idW-an99TAM?t=1515)

```bash
nano /mnt/c/Users/WINDOWS_USER/.wslconfig
```

Y ajouter

```ini
[wsl2]
memory=6GB
```

Redémarrer WSL

#### A la mano

```bash
## Docker > Remove everything not used, no need to confirm
docker system prune -af
```

[WSL2](https://nickjanetakis.com/blog/reclaiming-tons-of-diskspace-by-compacting-your-docker-desktop-wsl-2-vm)

Powershell > run as admin

```bash
# Close all WSL terminals and run this to fully shut down WSL.
## Notification > NON je ne veux pas redémarrer, pour le moment
wsl.exe --shutdown

# Replace Nick with your Windows user name. This is where Docker stores its VM file.
cd C:\Users\WINDOWS_USER\AppData\Local\Docker\wsl\data\

# Compact the Docker Desktop WSL VM file and you're done.
# NOTE: This may not work with Windows Home edition (read below).
optimize-vhd -Path .\ext4.vhdx -Mode full
```

Relancer docker desktop

---

## Mise en place de l'éditeur de texte / VSCode

[wesh](04-vscode/README.md)

---

## Troubleshootings / Problems

### WSL Can't connect to the internet

Can happen randomly..

[SO Resource](https://stackoverflow.com/questions/62314789/no-internet-connection-on-wsl-ubuntu-windows-subsystem-for-linux)

Run Cmd or Powershell as administrator

You can check `/etc/resolv.conf` to assure IPs have changed after the manipulations (no point in manual edit IMO).

```bash
# No need to reboot if you shutdown WSL beforehand
wsl --shutdown
netsh winsock reset
netsh int ip reset all
netsh winhttp reset proxy
ipconfig /flushdns
```

### 👴 Old / Installation de WSL ~2020

- [Windows Subsystem for Linux Installation Guide for Windows 10](https://docs.microsoft.com/fr-fr/windows/wsl/install-win10)
  - [MS store ubuntu](https://www.microsoft.com/fr-fr/p/ubuntu-2004-lts/9n6svws3rx71)

1. Télécharger
2. Lancer
3. Choisir username & password
4. Mise à jour de l'OS

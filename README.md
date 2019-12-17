# Mise à jour de l'environnement de développement

Histoire de partir sur de bonnes bases. Basé sur windows > ubuntu linux base shell

*Lexique*

- WLS / Windows Linux Subsystem (Ubuntu "natif" sur windows)
- ZSH	/ Un terminal (ligne de commande)
- OMZ / Oh-My-Zsh, moteur de thème pour ZSH ^



## Installer ubuntu pour windows

- [Windows Subsystem for Linux Installation Guide for Windows 10](https://docs.microsoft.com/en-us/windows/wsl/install-win10)
	- [MS store ubuntu](https://www.microsoft.com/en-us/p/ubuntu/9nblggh4msv6)

1. Télécharger
2. Lancer
3. Choisir username & password
4. [Mise à jour de l'OS](sudo apt update && sudo apt upgrade) / Maj & update package list

> sudo apt update && sudo apt upgrade



## Installer le terminal

Choix porté sur zosh/oh-my-zsh & tmux

Utilisation de ansible-galaxy histoire de pas y passer 1000 ans

Choix d'un repo avec une bonne pertinence [zsh repo + oh-my + theme](https://galaxy.ansible.com/viasite-ansible/zsh)

Récupération de la commande en one shot (dans l'onglet README) qui comporte l'installation d'ansible et tout x)

> curl https://raw.githubusercontent.com/viasite-ansible/ansible-role-zsh/master/install.sh | bash 

**Relancer le terminal**

// FONTS KO



## Installer les polices pour le terminal WLS

https://github.com/microsoft/WSL/issues/91#issuecomment-220369715

1. Choix d'une police

**Prendre une TTF !** / et attention aux [restrictions](https://superuser.com/questions/583835/adding-microsoft-console-cmd-font-in-registry-does-not-work-with-eastern-asian) windaube.

[Powerline fonts preview](https://github.com/powerline/fonts/blob/master/samples/All.md)

DejaVuSansMono, reco par le mec ansible // **La seule qui marche sur 4-5 de testées**.

~~Meslo LG M, thème reco OMZ~~ // KO Parce que nique la logique
~~Source code + FA~~ // KO

2. Installation pour windows, via le registre..

*(Accès au registre > Windows "demarrer" > Taper "Registr"..)*

- Télécharger [les polices](https://github.com/powerline/fonts) via github
- Extraire > Installer
- Editeur de registre > Ordinateur\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Fonts
	- Récupérer le nom de la police, sans (TrueType), ex: "DejaVu Sans Mono for Powerline" (C/C depuis Registre > Renommer)
- Editeur de registre > Ordinateur\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Console\TrueTypeFont
	- Nouvelle entrée > 00 (ou 000, 0000, 00000, etc. si déjà pris)
	- "DejaVu Sans Mono for Powerline"
- Rebooter le pc

3. Utilisation dans WLS

- WLS > Barre du haut > Clic droit > Propriétés > Polices > "DejaVu Sans Mono for Powerline"
- yay


### Liens..

- [WSL issue / Oh-my-zsh's icons don't show correctly #1517](https://github.com/Microsoft/WSL/issues/1517)
- [Windows Change console font](https://superuser.com/questions/5035/how-to-change-the-windows-xp-console-font)



## Configurer oh-my-zsh

Parce que ca ressemble toujours a de la merde pour le moment

[Doc OMZ](https://github.com/ohmyzsh/ohmyzsh#themes) / C'est normal, thème par défaut ultra basique

**Choisir un thème**

- [Agnoster](https://github.com/ohmyzsh/ohmyzsh/wiki/Themes#agnoster)
- [Powerlevel10k](https://gist.github.com/kevin-smets/8568070#powerlevel9k--powerlevel10k) / Plus facile a configurer
	- Pas de font icons sur windows a priori (restrictions)

Les deux ont les trucs git et tout. je reste sur PL10k car le chemin des dossiers est tronqué (Wia WLS, si on bosse en local, il faut accéder à ses projets via `/mnt/c/Users/MONNOM/.../` ce qui prend pas mal de place).


### Mise en place du thème de base (agnoster)

**Mise en place**

[Lien cookbook galaxy](https://galaxy.ansible.com/viasite-ansible/zsh) > Rechercher "Configure"

.. et ne pas suivre les recos, ça ne marche pas.

**Rappel vi** / L'éditeur de texte de base du terminal

- Par défaut on est pas en mode insertion (on ne peut pas modifier)
- "i" pour insérer/modifier du texte, puis échap pour revenir au mod normal
- ":wq" / sauvegarder et quitter

> ~~sudo cp ~/.zshrc /etc/zshrc.local~~ 
> ~~sudo vi /etc/zshrc.local~~ 
> ~~sudo cp ~/.zshrc ~/.zshrc.local~~ 
> ~~sudo vi ~/.zshrc.local~~ 

> sudo vi ~/.zshrc 

Remplacer `ZSH_THEME="robbyrussell"` par `ZSH_THEME="agnoster"`, avec vi.

Et c'est toujours aussi dégeulasse.


### Mise en place des couleurs de terminal

A éditer à la main à partir des sources ([theme solarized](https://ethanschoonover.com/solarized/)) dans le registre windaube.

Ou sinon un mec l'a déjà fait en édition 1 clic : [solarized for windaube](https://github.com/nsilvestri/solarized-dark-for-wsl).

Possibilité de fixer de la transparence également.


### Optionnel > theme Powerlevel10k

*Note : Je ne sais pas si le fait d'avoir installé l'autre thème avant joue..*

[Reco](https://gist.github.com/kevin-smets/8568070#powerlevel9k--powerlevel10k)

> sudo git clone https://github.com/romkatv/powerlevel10k.git $ZSH_CUSTOM/themes/powerlevel10k

Then edit your ~/.zshrc and set ZSH_THEME="powerlevel10k/powerlevel10k".

Relancer terminal, et suivre l'installation de la configuration.

Valider.























//

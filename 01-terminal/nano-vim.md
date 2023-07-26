# Nano & Vim

Deux éditeurs de textes assez connus pour terminal.

Présentations & commandes de bases.

Personnellement je recommande d'utiliser `nano` que je trouve plus intuitif.

Le but ici est de voir *simplement* comment éditer le contenu d'un fichier ~= le minimum syndical.

## Installations

Par défaut l'éditeur installé est `vi`, dont `vim` est une version améliorée.

Installations classiques via le gestionnaire de paquets.

```bash
apt install vim
apt install nano
```

---

## 📝 Notes

Par défaut les raccourcis copiers/collers ne fonctionnent pas de la même manière sous le terminal.

En effet la commande `Ctrl` + `C` arrête l'exécution du programme en cours.

2 possibilités pour copier coller :

1. Avec le clic droit
   1. Faire une sélection via la souris sur le terminal > Clic droit pour copier
   2. Placer le curseur > Clic droit pour coller
      1. La copie peut provenir d'en dehors du terminal
2. En modifiant les options du terminal
   1. En suivant les tutos de ce repo > `Ctrl` + `Shift` + `C` ou `V`

---

## nano

🔍 Le lien vers le [site officiel](https://www.nano-editor.org/)

Avantage : très facile à prendre en main.

L'ensemble des commandes est affiché en bas : utiliser `Ctrl` + la lettre indiquée.

Ex: `Ctrl` + `G` : Afficher l'aide

```bash
## Commandes de base
# Lancer l'éditeur sur un fichier
nano LE_NOM_DU_FICHIER

# (Rentrer du texte)
bonjour tout le monde !

# Enregistrer
(Ctrl + O)
(Entrée afin de confirmer le nom de fichier)

# Rechercher dans le fichier
(Ctrl + W)
(Le terme à rechercher)
(Entrée, plusieurs fois pour chaque occurence)

# Quitter nano pour retourner au terminal classique
(Ctrl + X)
(Peut être besoin d'enregistrer si modifications non sauvegardées)
  (Y)

# Vérifier le contenu
cat LE_NOM_DU_FICHIER
```

---

## VIM

🔍 Le lien vers le [site officiel](https://www.vim.org/), qui a mal vieilli x).

Avantage : hautement personnalisable, raccourcis de l'espace, *ex: incrémenter le premier chiffre de la ligne*.

L'éditeur dispose de deux modes : un d'**affichage** pour rechercher / parcourir, et un d'**édition**.

```bash
## Commandes de base
# Lancer l'éditeur sur un fichier
vim LE_NOM_DU_FICHIER

## 🚨 Par défaut on est en mode d'affichage : on ne peut rien modifier
# Rentrer en mode d'édition, ~= insertion
i

# (Rentrer du texte)
bonjour tout le monde !

# Sortir du mode d'insertion
(echap)

## Pour enregistrer, il faut passer par le mode de commande via :
#     Puis on enregistre avec "w", ~= write
#     Enfin on quitte vim pour retourner au terminal classique avec "q", ~= quit
:wq
(entrée)

# Vérifier le contenu
cat LE_NOM_DU_FICHIER
```

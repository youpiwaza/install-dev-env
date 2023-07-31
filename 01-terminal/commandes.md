# 📝 Quelques commandes de terminal usuelles, sous linux

Afin de pouvoir effectuer quelques manipulations de base.

Note : Certaines commandes diffèrent sous le terminal windows.

Petit jeu en ligne, en français : [Terminus](https://luffah.xyz/bidules/Terminus/).

[L'ancien temps, plein](https://github.com/youpiwaza/notes-installation-serveur-web-docker/blob/master/docs/06-Commandes.md)

---

```bash
# Afficher le contenu du répertoire courant
#   = list
ls

# Afficher le contenu du répertoire courant, avec plus de détails et les fichiers cachés
ls -lah

# Affichage verticla du contenu du répertoire courant
ll

# Ou suis-je dans l'arborescence
pwd

# Se déplacer des les répertoires
#   = change directory
cd LE_REPERTOIRE

# Je suis quel utilisateur ? Pour les droits
whoami

# Créer un répertoire
#   = make directory
mkdir LE_NOM_DU_REPERTOIRE_A_CREER

# Créer un fichier
touch LE_NOM_DU_FICHIER_A_CREER

# Afficher le contenu d'un fichier
cat LE_NOM_DU_FICHIER

# Déplacer / renommer un fichier
#   = move
mv ANCIEN_NOM_OU_EMPLACEMENT NOUVEAU_NOM_OU_EMPLACEMENT

# Supprimer un fichier
#   = remove
rm LE_NOM_DU_FICHIER_A_SUPPRIMER

# Supprimer un répertoire et toute son arborescence, son contenu
#   -r = de manière récursive
rm -r LE_NOM_DU_REPERTOIRE_A_SUPPRIMER

# 🧹 Supprimer ce qui est affiché sur le terminal
clear

# Exécuter VSCode à partir de cet emplacement
#       Très utile pour lancer depuis WSL2
code .
```

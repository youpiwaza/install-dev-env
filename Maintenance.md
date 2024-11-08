# Opérations récurrentes afin de garder son matos à jour

Histoire d'éviter l'entropie et de tout maintenir à jour.

Le but est de dupliquer ce fichier, d'effectuer chacune des opérations puis de les valider en remplaçant ⏳ par ✅.

En l'effectuant régulièrement cela évite les mauvaises surprises, et cela reste peu chronophage.

Prévu pour Windows + environnement de développement via WSL2 & Docker desktop.

## Légende

- 🚀 En cours
- ✅ Terminé
- ♻️ Récurrent
- 💩 KO
- ⏳ en attente

---

## La liste à copier / coller / ou versionner

Tâches à *vérifier au moins une fois par semaine*, afin d'éviter un bordel plus tard/exponentiel

- ⏳ Virer ce qui traine
  - ⏳ sur le bureau
  - 💩 dans le dossier _shame du bureau
  - 💩 Lel ~(local)/_dev/_shame
  - ⏳ Vider corbeille
  - ⏳ Vider téléchargements
  - ⏳ Dans les mails
- ⏳ Navigateur > Virer/ranger les onglets qui traînent
- ⏳ Maj locales / Environnement de dev / Dernière maj le 01/06/21 / lel
  - ⏳ CHKDSK / Besoin de param `/f` ou [ne répare pas](https://docs.microsoft.com/fr-fr/windows-server/administration/windows-commands/chkdsk), `/r` également
    1. Invite de commande ou Powershell **en admin**
    2. `chkdsk c: /f /r` (et en fonction de vos disques.. && `chkdsk d: /f /r`, etc.)
    3. `>Blah blah besoin de redémarrer O/n` >> `O`
    4. Redémarrer / Attendre 5 ans et demi sauf si t'as un SSD/Nvme
  - ⏳ Windaube
    - ⏳ Update alakon
    - ⏳ [.net](https://dotnet.microsoft.com/download) > Runtime
    - ⏳ Panneau de conf > "Fichiers temporaires" > "Fichiers temporaires" (dans les catégories) > Supprimer
  - ⏳ Drivers > [detection auto](https://www.touslesdrivers.com/index.php?v_page=29) > Lancer éxécutable, ça ouvre une page recap, et suivre liens dl
  - ⏳ Firmware SSDs / Dépend du constructeur > Voir site officiel, avec un peu de chance logiciel auto
    - ⏳ Dell support assist
    - ⏳ Alienware update
    - ⏳💸 System mechanic
  - ⏳ Docker desktop (tray > icône > RC > Check for updates) / Attention, besoin de redémarrer a la main pour installation
  - ⏳ Logiciels alakon
    - ⏳ Ouvrir VScode > Auto update plugins etc.
    - ~~Filezilla~~ ⏳ WinSCP, ⏳ OBS, ⏳ VLC, [Xnview classic (Pas MP)](https://www.xnview.com/fr/xnview/#downloads)
    - ~~Powershell~~ Pris en compte par Windows update
      - [sans prise de tête](https://aka.ms/powershell-release?tag=stable) > ~`PowerShell-VERSION-win-x64.msi`.
      - ( [Doc](https://docs.microsoft.com/fr-fr/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-7.1) )
    - ⏳ Nvidia driver
  - ⏳ Supprimer les fichiers temporaires
    - Exec > `temp` // Devrait ouvrir `~c:Windows\Temp`
    - Supprimer tout, Ignorer ceux utilisés
  - ⏳ WSL 2
    - Version Ubuntu
      - Si majeure, ré-effectuer [install-dev-env](https://github.com/youpiwaza/install-dev-env)
    - Packages & terminal

```bash
omz update
# One liner, go triple click
git -C ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k pull && sudo apt update && sudo apt --fix-broken install && sudo apt -y upgrade && sudo apt -y clean && sudo apt -y autoremove && docker system prune -af && npm install -g npm@latest && sudo sh -c "/usr/bin/echo 3 > /proc/sys/vm/drop_caches" && swapoff -a && swapon -a && printf '\n%s\n' 'Ram-cache and Swap Cleared'
```

- ⏳ Téléphone
  - ⏳ Maj de la base
  - ⏳ Maj des applications
  - ⏳ Tous les 6 mois > reset usine
- ⏳ Tout est versionné, pas de WIP qui traîne
- ⏳♻️ majs tous les wordpress
- ⏳ Dashlane > Surveillance dark web > changer mots de passe

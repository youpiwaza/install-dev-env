# 🖥️ Configuration de VSCode

[Télécharger](https://code.visualstudio.com/) & installer

⚡️ Je recommande également la mise place (via l'OS ou un soft dédié, cf. en bas) des copiers / collers multiples (Windows 10+ : touche "Windows" + V).

## Configuration

File > Preferences > Settings

"bracketPairColorization" > Enable. Remplace l'ancien plugin en résolvant les problèmes de performance.

---

## Liste des plugins

Désactivez/désinstallez ceux dont vous ne servez pas

🚨⚡️ Ne pas hésiter à tester, si des problèmes de performances se font sentir après l'installation de certains plugins (lags, touches inactives, etc.)

---

### Common

⚡️ / Très gros gain de productivité

- Auto rename tag
- (Beautify)
- Better comments
- Bookmarks
- ⚡️ Change case
- Code Spell Checker
  - French - Code Spell Checker // Besoin reboot & activation
- Color info
- 🚨 Github Copilot
  - [Démo fermée](https://copilot.github.com/)
  - Code partagé en vue d'amélioration, attention à la confidentialité
- ESLint
- Indent rainbow
- Markdown all in one
- Markdown preview enhanced
- Markdown lint
- Material Icon Theme
- Todo Tree
- ⚡️ Toggle Quotes

Rajouter les plugins/linters liés aux langages dans lesquels vous codez.

---

### Ponctuels

- Beautify    // Linter
- Easy Sass   // Compilateur
- Live server // Serveur local
- Live share  // Partage d'écran
- Polacode    // Code screenshots

---

### Languages dependants

Ce dont vous avez besoin, activer en fonction. Ca bouge assez souvent donc prenez les plus utilisés/récents

- Ansible
  - Ansible
    - note: Les plugins sur le langage sont en ruine, au pire prendre le DEPRECATED de microsoft
  - Better Jinja
  - language-ansible // Syntaxe
- Docker
- Javascript
  - ESLint
  - JavaScript Booster
  - Quokka // JS/TS playground
- Python
- Sass

---

### 📌 A testay

- CacheQuality

---

#### Liens recos

- [dev.to / Awesome VS Code setup](https://dev.to/pas8/best-vs-code-setup-20fe)
- [dev.to / 5 VS Code Extensions That Make Refactoring Easy](https://dev.to/alexomeyer/5-vs-code-extensions-that-make-refactoring-easy-1ccb)
- [dev.to / Best VS Code extensions for Front End Dev](https://dev.to/labib/best-vs-code-extension-for-front-end-dev-dj4)
- [VSCode ext / package++](https://marketplace.visualstudio.com/items?itemName=juninhosilva.package-plus-plus)

& les commentaires associés

---

## Bonnes pratiques

Enfin surtout éviter que VSCode soit en PLS au démarrage.

- Désactivez/désinstallez les plugins dont vous ne vous servez pas
- Ne pas faire un seul gros dossier contenant tous vos projets (notamment ceux avec des gestionnaires de paquets ~npm/composer/etc.) pour éviter de mettre git à genoux.
  - Au pire faire un gros dossier avec tous les projets clonés et une 2eme dossier contenant les projets sur lesquels vous bossez
  - Le mieux restant de n'ouvrir qu'un seul projet à la fois..

---

## Raccourcis de ninjas

- [dev.to / Raccourcis & gifs de demo](https://dev.to/alebian/text-editor-tips-and-tricks-to-boost-your-productivity-2gc5)
- [Fireship / 25 VS Code Productivity Tips and Speed Hacks](https://www.youtube.com/watch?v=ifTF3ags0XI) // Raccourcis usuels
- ~multi-curseurs, utilisez avec les raccourcis peu fréquents (début / fin de ligne, Ctrl + flèche)

---

## Recos supplémentaires de nick

cf. l'[article correspondant](https://nickjanetakis.com/blog/the-tools-i-use).

- [PowerToys](https://github.com/microsoft/PowerToys) / Plein d'utilitaires pour les tâches courantes / Alt + space > lancer un programme
- 💖 [Ditto](https://ditto-cp.sourceforge.io/) / Copier collers multiples + recherche dans historique / [Setup avec terminal](https://nickjanetakis.com/blog/boosting-software-developer-productivity-with-a-clipboard-manager)

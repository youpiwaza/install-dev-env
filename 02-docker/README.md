# Installation de Docker et ses potes sur windows

**Attention** : Même si maintenant c'est rarement un problème, vérifier que vous avez quelques Go de disponibles sur le disque d'installation.

Durée: ~3-5mn en comptant les installations.

1. [Linux pour Windows](/README.md) déjà installé
2. Installer [Docker desktop](https://docs.docker.com/docker-for-windows/install/)
3. Avoir lu/regardé le [nouvel article dédié a WSL2](https://nickjanetakis.com/blog/a-linux-dev-environment-on-windows-with-wsl-2-docker-desktop-and-more)

Edit 2021: bah putain c'est quand même plus simple.

Après avoir installé docker desktop, le lancer, aller dans la configuration et cocher..

- General > ✅ Start Docker Desktop when you log in
- General > ✅ Use the WSL 2 based engine
- Resources > WSL integration > ✅ Enable integration with my default WSL distro
- Resources > WSL integration > ✅ Ubuntu-20.04

et.. c'est tout.

```bash
## Test sur WSL2
docker info
# blah² les infos docker

docker-compose --version
# docker-compose version 1.29.1, build c34c88b2

## Test avec un mini serveur local alakon
##    Lancer un nginx avec sur index.html le nom du conteneur + une image
##    Sur le port 80, en mode interactif (s'arrête via ctrl+c), et sera supprimé après utilisation
docker run -it \
  -p 8080:80 \
  --rm \
  nginx:alpine

# Unable to find image 'nginx:alpine' locally
# alpine: Pulling from library/nginx
# 540db60ca938: Pull complete
# Digest: sha256:0f8595aa040ec107821e0409a1dd3f7a5e989501d5c8d5b5ca1f955f33ac81a0
# Status: Downloaded newer image for nginx:alpine

## Aller sur http://localhost:8080/
# 172.17.0.1 - - [02/Jun/2021:09:15:06 +0000] "GET / HTTP/1.1" 200 612 "-" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/91.0.4472.77 Safari/537.36" "-"
# 2021/06/02 09:15:06 [error] 32#32: *2 open() "/usr/share/nginx/html/favicon.ico" failed (2: No such file or directory), client: 172.17.0.1, server: localhost, request: "GET /favicon.ico HTTP/1.1", host: "localhost:8080", referrer: "http://localhost:8080/"
# 172.17.0.1 - - [02/Jun/2021:09:15:06 +0000] "GET /favicon.ico HTTP/1.1" 404 555 "http://localhost:8080/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/91.0.4472.77 Safari/537.36" "-"

## Profit

## Ctrl + C pour couper le conteneur de test
```

![Test WSL2 > docker run > nginx](../docs/images/test-docker-nginx-ok.png)

Note: En cas d'erreur `docker: Error response from daemon: Head [...] unauthorized: incorrect username or password.`

```bash
# Se connecter soit via docker desktop, doit via terminal ; avec identifiant dockerhub
docker login --username TON_USERNAME_WESH
```

---
---
---

## Old 👴💩

Durée : ~30mn-1h.

## Faire marcher Docker et ses potes avec WSL

En gros, WSL ne peut pas installer le Docker daemon. Mais on le connecte à celui de Docker desktop :)

Basé sur cet [excellent article](https://nickjanetakis.com/blog/setting-up-docker-for-windows-and-wsl-to-work-flawlessly), dont je recommande la lecture avant de procéder à l'installation. Puis suivre les instructions ci-dessous car il y a des pétouilles.

**Ouksé** / Les opérations suivantes se feront sur le terminal Ubuntu de WSL (pas le terminal ni le powershell windows).

### Installation de Docker

Installation de docker (ce), 🚨utiliser la [documentation officielle](https://docs.docker.com/install/linux/docker-ce/ubuntu/)🚨, qui est maintenue.

*Notes* :

- Ce code est peut être 💩obsolète💩, vérifier sur la doc.
- Je rajoute l'ensemble des lignes de code par convénience (réinstallation), les explications approfondies seront sur les pages citées :)

```bash
> sudo apt remove docker docker-engine docker.io containerd runc

> sudo apt update

> sudo apt install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common

> curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

> sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"

> sudo apt update

> sudo apt install docker-ce docker-ce-cli containerd.io

> sudo usermod -aG docker $USER
```

*Notes* :

- Je pars sur la version stable
- Tout faire jusqu'a `sudo docker run hello-world` qui ne marchera pas > `docker: Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running?.`
  - Ce qui est normal, car le docker daemon n'est pas (encore) connecté

Ajouter `sudo usermod -aG docker $USER` (dernières lignes de commandes de l'installation docker dans le tuto).

### Installation de Docker compose

Suivre [cette installation](https://stackoverflow.com/questions/36685980/docker-is-installed-but-docker-compose-is-not-why/36689427#36689427) recommandée plutôt que celle (via pip) de l'article.

```bash
> sudo curl -L "https://github.com/docker/compose/releases/download/1.22.0/docker-compose-$(uname -s)-$(uname -m)"  -o /usr/local/bin/docker-compose
> sudo mv /usr/local/bin/docker-compose /usr/bin/docker-compose
> sudo chmod +x /usr/bin/docker-compose
```

### Suivre la suite du tutoriel

On peut ensuite effectuer les [dernières actions](https://nickjanetakis.com/blog/setting-up-docker-for-windows-and-wsl-to-work-flawlessly#install-docker-compose) du tutoriel.

```bash
> nano ~/.profile

# Ajouter la ligne suivante en fin de fichier, puis Ctrl+O (sauvegarder), puis Ctrl+X (sortir de l'éditeur)
export PATH="$PATH:$HOME/.local/bin"

> source ~/.profile

> echo "export DOCKER_HOST=tcp://localhost:2375" >> ~/.bashrc && source ~/.bashrc

> sudo nano /etc/wsl.conf

# Ajouter les lignes suivantes en fin de fichier, puis Ctrl+O (sauvegarder), puis Ctrl+X (sortir de l'éditeur)
[automount]
root = /
options = "metadata"
```

## Vérifications

```bash
# Tester la connexion avec docker
> docker info

# Tester l'installation de docker compose
> docker-compose --version

# Lancer un conteneur
> docker run hello-world

```

### Docker build & run

Créer un dossier projets (pour ma part, dans "Mes documents/_dev/tests-docker/" de windows).

```bash
# Optionnel, se déplacer dans un dossier de test
> cd /c/Users/MON_USER_WINDOWS/Documents/MON_DOSSIER_PROJETS/tests-docker/

# Création d'un build depuis un repo git
>  docker build \
  -t some-repo-content-nginx \
  https://github.com/youpiwaza/test-min-static-site.git#master:site

# Lancement du container
> docker run -d \
  --name test-repo-nginx  \
  -p 8081:80  \
  some-repo-content-nginx
```

Test sur [localhost:8081](http://localhost:8081/)

```bash
# Arrêt du container
> docker container stop test-repo-nginx
> docker container rm test-repo-nginx
```

### Docker compose

Récupérer un [exemple](https://github.com/youpiwaza/server-related-tutorials/tree/master/01-docker/04-my-tests/02-compose-nginx-php).

```bash
# Aller dans le dossier ou l'exemple se situe
> cd WTV/02-compose-nginx-php/
> docker-compose up -d
```

Test sur [localhost:8080](http://localhost:8080/)

```bash
# Arrêter
> docker-compose down
```

### Docker swarm

Possibilité de réutiliser l'exemple précédent :

```bash
# Monter le service
> docker stack deploy -c docker-compose.yml test-swarm
```

Test sur [localhost:8080](http://localhost:8080/)

```bash
# Arrêter
> docker stack rm test-swarm
```

### Cleaner

Supprimer les builds, containers arrêtés. & éventuels networks.

```bash
> docker system prune
```

## Problèmes rencontrés

### Impossible de se connecter à Docker

Attention ! Il y a un petit temps de latence lors du démarrage de votre bécane, docker desktop doit lancer le daemon avant que ce dernier soit accessible.

*C'est très con mais je me suis fait avoir une paire de fois après un reboot..*

Vérifiez dans votre barre des tâche que le daemon n'est pas en cours de lancement (animation sur l'icône + texte au survol).

Une notification windows apparaît quand il est lancé normalement.

### Impossible de se connecter à Docker 2

La manipulation `echo "export DOCKER_HOST=tcp://localhost:2375" >> ~/.bashrc && source ~/.bashrc` peut merdouiller.

Essayer de rajouter directement :

```bash
> export DOCKER_HOST=tcp://localhost:2375

# Vérifications
> echo "Docker Host is set to ${DOCKER_HOST}"
> docker info
```

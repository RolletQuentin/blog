+++
title = 'Comment configurer Nginx'
date = 2023-09-25T19:00:00+02:00
draft = false
weight = 1
+++

Auto-héberger un serveur web chez soi peut être solution économique pour ne pas à payer des serveurs distants. On peut faire ce que l'on veut dessus et utiliser les technologies que l'on souhaite.

Cependant, configurer un serveur peut être compliqué. Nous allons voir au fil de différents articles comment mettre en place son propre serveur.

## Le serveur

Pour ma part, je suis sous Fedora 37 et mon serveur tourne sur un Raspberry Pi.

Les commandes qui seront donnés fonctionneront donc pour Fedora 37, mais seront à adaptées si vous êtes sous une autre distribution.

## Installation

Nous allons utiliser Nginx (prononcé Engine-X) en tant que reverse-proxy et serveur web.

Nous allons commencer par installer Nginx :
```shell
sudo dnf install nginx
```

Il faut ensuite activer le service et l'autoriser au démarrage du serveur :
```shell
sudo systemctl start nginx
sudo systemctl enable nginx
```

Pour vérifier si Nginx tourne bien, on peut d'abord regarder le statut du service, puis vérifier s'il expose bien le port 80. Pour cela, on va faire une requête `curl` sur le localhost et vérifier qu'il nous renvoie bien une page html :
```shell
sudo systemctl status nginx
curl -v 127.0.0.1:80
```

Si du code html s'affiche, c'est que Nginx a bien démarré et expose sur le port 80.


## Configuration

Nous allons voir maintenant comment configurer Nginx. Pour cela, nous allons créer un répertoire `nginx/conf` pour accueillir la configuration de Nginx.

```shell
mkdir -p nginx/conf
cd nginx/conf
```

Maintenant que ceci est fait, nous allons créer un **lien symbolique** vers le dossier censé contenir les fichiers de configuration Nginx.

```shell
ln -s /etc/nginx/conf.d
```

C'est dans ce dossier que nous mettrons tout les fichiers de configuration.

Nous allons aussi créer un lien symbolique avec le fichier principal de configuration Nginx, qui va en fait inclure tout les autres fichiers de configuration contenu dans `conf.d`.

```shell
ln -s /etc/nginx/nginx.conf
```

### Servir des fichiers statiques

Dans le dossier `conf.d`, nous allons créer un fichier un fichier de configuration. Appelons ce fichier `servername.conf`.

```bash 
server {

    server_name     servername.com www.servername.com;
    listen          80;
    listen          [::]:80;

    location / {
        root /usr/share/nginx/html;
        try_files $uri $uri/ =404;
    }

    location /portfolio {
        root /usr/share/nginx/www;
        try_files $uri $uri/ =404;
    }

    location /blog {
        root /usr/share/nginx/www;
        try_files $uri $uri/ =404;
    }
}
```

Ici, nous aurons deux répertoires dans le répertoire `/usr/share/nginx/www` qui se nomment respectivement `portfolio` et `blog`. Il faut s'assurer qu'à la racine de ces deux dossiers se trouve un fichier `index.html` pour pouvoir afficher le site web. Si ce n'est pas le cas, vous aurez probablement une erreur `403 Forbidden` de la part de Nginx.

Le premier `location` permet d'afficher la page par défaut de Nginx. Vous pouvez modifier cette page par défaut en modifiant le fichier `/usr/share/nginx/html/index.html` ou bien décider de faire une redirection vers `http://servername.com/portfolio` si vous voulez afficher par exemple votre portfolio par défaut.

## Certifier son site

Avoir un certificat SSL est très important, car une fois installé sur le serveur, il permet d'activer le protocole `https` permettant une connexion sécurisée entre le serveur web et le navigateur.

En plus de son importance, il est extrêmement simple à installer grâce à [Certbot](https://certbot.eff.org/instructions) ! Il suffit de suivre les différentes étapes et cela créera automatiquement les certificats SSL et la redirection vers `https` en modifiant la configuration Nginx. 

## Références
 - [Documentation Fedora](https://doc.fedora-fr.org/wiki/Nginx)
 - [Grafikart](https://grafikart.fr/tutoriels/nginx-692)


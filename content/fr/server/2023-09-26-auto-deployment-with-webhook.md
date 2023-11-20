+++
title = 'Auto-déploiement avec Webhook'
date = 2023-09-26T22:58:22+02:00
draft = false
weight = 2
+++

Auto-déployer son application, c'est ce simplifier la vie au quotidien. En effet, une fois que le déploiement est configuré, nous n'avons plus besoin de revenir sur le serveur à chaque fois qu'une nouvelle version de l'application est créée.

## Configurer Github

Nous allons d'abord commencer par configurer votre répertoire Github. Pour cela, aller dans les `Paramètres` puis dans l'onglet `Webhooks`, puis appuyer en haut à droite de l'écran pour ajouter un webhook.

![Ajouter un webhook](/blog/images/server/add_webhook.png)

Une fois que cela est fait, renseignez une clé secrète pour que Github puisse s'authentifier à votre serveur. Cocher aussi l'option `Send me everything` pour que Github vous envoie à chaque modification de votre répertoire une requête `http` qui permettra de déployer votre code.

![Configurer le webhook](/blog/images/server/set_up_webhook.png)

Le début de la configuration sur Github est terminée, nous reviendrons dessus à la fin de l'article pour finir la configuration.


## Configurer l'endpoint du webhook

Nous allons maintenant configurer le **webhook** sur notre serveur. Nous allons d'abord créer un fichier `hooks.json` permettant de configurer nos **hooks** :

```shell
vim hooks.json
```

```json
[
  {
    "id": "portfolio-app",
    "execute-command": "/home/qrollet/redeploy.sh",
    "pass-arguments-to-command": [{
        "source": "string",
        "name": "portfolio-app"
    }],
    "command-working-directory": "/home/qrollet/portfolio-app",
    "trigger-rule": {
      "and": [
        {
          "match": {
            "type": "payload-hash-sha1",
            "secret": "YOUR GITHUB SECRET",
            "parameter": {
              "source": "header",
              "name": "X-Hub-Signature"
            }
          }
        },
        {
          "match": {
            "type": "value",
            "value": "refs/heads/main",
            "parameter": {
              "source": "payload",
              "name": "ref"
            }
          }
        }
      ]
    }
  },
]
```

Ce fichier correspond à un tableau `JSON` avec différent hooks.- Voyons plus en détail comment cela fonctionne :
- `id` correspond au nom du hook;
- `execute-command` correspond à la commande que le hook doit exécuter lorsque le hook est appelé;
- `pass-arguments-to-command` sert à passer des argument à la commande. Cela peut être utile si le script que vous utiliser pour déployer votre application prend des arguments;
- `command-working-directory` est le répertoire où sera exécuter la commande;
- `trigger-rule` permet de lire la requête `http` et matcher si oui ou non la commande associé au hook s'exécute. À la place de `YOUR GITHUB SECRET`, il faut renseigner la clé que vous donner à Github pour qu'il puisse s'authentifier, sinon n'importe qui pourrait déclencher votre hook.

## Écrire le script de déploiement

Voici un exemple de script pour déployer automatiquement une application node :

```bash
#!/bin/bash

log_file="/var/log/nginx/deployment.log"

# To verify if the id is given in parameter
if [ $# -eq 0 ]; then
        echo "Usage: $0 <id>" >> "$log_file"
        exit 1
fi

id="$1"

if [ "$id" =  "portfolio-app" ]; then
        # change the workdir
        cd ~/portfolio-app

        # update the project
        git checkout main >> "$log_file"
        git pull origin main >> "$log_file"

        # install the dependencies
        npm install >> "$log_file" 2>&1

        # delete problematic file
        rm tsconfig.tsbuildinfo >> "$log_file" 2>&1

        # build the application
        npm run build >> "$log_file" 2>&1

        # copy dist folder to nginx html folder
        \cp -Rf dist/. /usr/share/nginx/www/portfolio
fi

echo "The project '$id' is deployed with succes !" >> "$log_file"
```

Il faut ensuite exécuter la commande suivante pour que Webhook puisse exécuter le script :
```shell
chmod +x redeploy.sh
```

## Lancer le serveur Webhook

Maintenant, il faut créer le serveur webhook. Pour cela, il faut d'abord installer le repository Github [webhook](https://github.com/adnanh/webhook) et de le compiler. Il faut au préalable s'assurer que le langage `Go` soit installer sur le serveur :

```shell
sudo dnf install golang
git clone https://github.com/adnanh/webhook
cd webhook
go build
```

Maintenant, vous pourrez facilement lancer un serveur webhook sur votre serveur.

Il faut maintenant lancer le serveur grâce à la commande suivante, à adapter selon la manière où vous avre stocker vos répertoires. Je lance personnellement cette commande depuis la racine où se situe mon fichier `hooks.json` et le répertoire `webhook`.

```shell
webhook/webhook -hooks hooks.json &
```

C'est bon, votre serveur webhook est opérationnel ! Vous pouvez y accéder en local sur le `port 9000`.

Pour accéder à votre webhook depuis l'extérieur, il faut ajouter une route à votre serveur Nginx. Nous allons modifier le fichier de configuration et utiliser Nginx comme reverse proxy :
```shell
server {

    server_name     servername.com www.servername.com;

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

    location /hooks {
        proxy_pass http://127.0.0.1:9000$uri;
    }
}
```

Il ne faut pas oublier de redémarrer le serveur Nginx :
```shell
sudo systemctl restart nginx.service
```

Et voilà ! Votre webhook est maintenant accessible à partir de l'extérieur !

## Fin de la configuration sur Github

Maintenant que votre serveur est configuré, revenons sur la configuration de Github. Vous avez juste à renseigner l'URL pour accéder à votre serveur, et bien faire attention à ce que la case `Active` soit cochée. Vous pouvez ensuite enregistrer les modifications.

![Finir le setup du webhook](/blog/images/server/finish_setup.png)

Dans l'onglet `Recent Deliveries`, vous pourrez voir si la connexion entre Github et votre serveur s'est bien déroulée, et regarder le détail de chaque requêtes que Github a fait sur votre serveur.

## Conclusion

Grâce à cet article, plus besoin de se prendre la tête pour déployer votre application à chaque fois que vous faîtes une mise à jour ! Grâce aux webhooks et au reverse proxy de Nginx, tout cela se fait automatiquement !

## Références
- [Maxim Orlov](https://maximorlov.com/automated-deployments-from-github-with-webhook/)
- [Webhook repository](https://github.com/adnanh/webhook)
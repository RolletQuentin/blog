+++
title = "Degooglisation : Reprendre le contrôle de vos données"
description = "Découvrer comment j'ai dégooglisé (en partie) ma vie numérique."
[taxonomies]
categories = ["Article", "Retour d'expérience"]
tags = ["Open Source", "Degooglisation", "Vie privée"]
+++

## Introduction

Bienvenue sur mon premier article de blog ! Aujourd'hui, j'aimerais vous partager un sujet qui me tient particulièrement à cœur : le respect de ma vie privée. Il y a quelques années, j'ai reçu mon premier Raspberry Pi, et j'ai en même temps découvert le monde de l'open source. Déployer mon propre serveur m'a permis de comprendre que des solutions alternatives aux services proposés par les géants du web existent, et qu'elles sont souvent plus respectueuses de la vie privée.

C'est ainsi que j'ai commencé petit à petit à "degoogliser" ma vie numérique. Dans cet article, je vais vous expliquer les étapes que j'ai suivies pour réduire ma dépendance aux services de Google et d'autres grandes entreprises technologiques, et comment cela a amélioré ma vie en ligne.

## Qu'est-ce que la dégooglisation ?

Avant toute chose, il est important de comprendre ce qu'est la dégooglisation. Il s'agit à l'origine une démarche visant à réduire l'utilisation des services de Google. Cependant, le concept peut être étendu à d'autres entreprises qui collectent et exploitent nos données personnelles à des fins publicitaires ou commerciales. L'objectif principal de la dégooglisation est d'abord de prendre conscience de l'ampleur de la collecte de données, puis de chercher des alternatives plus respectueuses de la vie privée.

Il faut néanmoins garder à l'esprit que la dégooglisation totale est un objectif difficile à atteindre, et je ne pense pas qu'il faut en arriver à cet extrême. Étant un gros consommateur de Youtube (Google) et de Twitch (Amazon), j'ai conscience que ces services ne sont pas remplaçables. Je ne dis pas non plus qu'il faut arrêter les réseaux sociaux, mais qu'il faut être conscient de ce que l'on utilise et pourquoi.

## Étapes de ma dégooglisation

### Changement de navigateur et moteur de recherche

Google est avant toute chose connu pour son moteur de recherche et son navigateur Chrome. Pour le navigateur, je me suis naturellement tournée vers Mozilla Firefox, un navigateur open source qui respecte un peu plus la vie privée des utilisateurs. Il existe d'autres navigateurs comme Brave ou Opera, mais ceux-ci utilisant le moteur de rendu Chromium (utilisé par Google Chrome), j'ai préféré opter pour une alternative plus indépendante.

Pour le moteur de recherche, j'ai également cherché une option plus respectueuse de la vie privée. Pour ma part, j'ai opté pour [DuckDuckGo](https://duckduckgo.com/), qui ne collecte pas de données personnelles et ne suit pas les utilisateurs à travers le web. D'autres options populaires incluent [Qwant](https://www.qwant.com/) et [Startpage](https://www.startpage.com/).

### Migration de Gmail vers Proton Mail

Les emails représentent une mine d'or pour les entreprises qui cherchent à collecter des données. S'inscrire sur un site web ou à une newsletter avec une adresse Gmail, c'est informer directement Google de vos activités en ligne. Pour cette raison, j'ai décidé de commencer ma migration vers [Proton Mail](https://proton.me/fr/mail), un service de messagerie sécurisé et respectueux de la vie privée. Proton Mail offre un chiffrement de bout en bout, ce qui signifie que seuls l'expéditeur et le destinataire peuvent lire les messages.

C'est malgré tout l'étape la plus difficile, car il est chronophage de migrer toutes ses adresses email, et pour certains services c'est même impossible. De plus, le bouton "Se connecter avec Google" est omniprésent sur le web, et il est tentant de l'utiliser pour gagner du temps. Il faut ainsi être patient et méthodique dans cette démarche, qui peut prendre plusieurs mois voire années selon l'utilisation que l'on fait de son adresse email.

J'ai profité d'avoir une adresse mail Proton pour migrer mon calendrier vers Proton Calendar, qui propose un calendrier toutefois encore un peu limité en fonctionnalités par rapport à Google Calendar, mais qui m'est amplement suffisant.

On peut cependant se poser deux questions :
1. Pourquoi avoir une adresse email Proton, alors que eux aussi peuvent savoir sur quels sites on s'inscrit ?
2. Pourquoi ne pas avoir choisi un service de messagerie auto-hébergé ?

Pour la première question, c'est avant tout une question de confiance. Proton est une entreprise suisse, et la Suisse a des lois sur la protection de la vie privée plus strictes que la plupart des pays en Europe. La Suisse ne fait pas non plus partie des pays de l'[alliance "14 Eyes"](https://tuta.com/fr/blog/fourteen-eyes-countries), qui partagent des informations de surveillance entre eux (bien que les autorités suisses puissent coopérer avec d'autres pays dans certains cas). Dans tout les cas, seuls les adresses mails et les objets des mails sont visibles par Proton, le contenu des mails étant chiffré de bout en bout.

Pour la deuxième question, j'ai envisagé d'auto-héberger mon propre serveur de messagerie, mais cela demande du temps de maintenance. En plus de cela, il faut s'assurer que le serveur n'est pas sur une liste noire, ce qui peut très vite arriver si une autre messagerie décide de signaler votre serveur comme source de spam. Enfin, si son serveur de messagerie tombe en panne, on ne peut plus recevoir d'emails, ce qui peut être problématique. J'ai donc préféré opter pour une solution clé en main, même si cela implique de faire confiance à un tiers.

### Immich : une alternative à Google Photos

Google Photos est un service très pratique pour sauvegarder et organiser ses photos. Je ne pense pas qu'il y ait une analyse des photos pour en extraire des données, sinon ce serait vraiment très limite de la part de Google. Mais quitte à se dégoogliser, autant le faire jusqu'au bout ! J'ai donc décidé d'auto-héberger [Immich](https://immich.app/), une alternative open source à Google Photos. Immich permet de sauvegarder automatiquement les photos de son téléphone, de les organiser et de les partager avec ses proches, le tout en gardant le contrôle sur ses données. Un des avantages majeurs d'une solution auto-hébergée est l'espace de stockage, qui est souvent limité sur les services gratuits comme Google Photos, mais qui dépend uniquement de la capacité de son propre serveur.

Des fonctionnalités sympathiques comme la reconnaissance faciale ou une carte interactive sont également présentes, ce qui rend l'expérience utilisateur très agréable.

### Nextcloud : un cloud personnel

Comment ne pas citer [Nextcloud](https://nextcloud.com/) lorsqu'on parle de dégooglisation ? Nextcloud est une suite d'applications auto-hébergées qui permet de créer son propre cloud personnel en remplacement des services comme Google Drive, Dropbox ou iCloud. Avec Nextcloud, on peut stocker et synchroniser des fichiers, gérer un calendrier, des contacts, et même collaborer sur des documents en ligne. Bien que je n'ai pas encore sauté le pas pour l'instant n'ayant pas encore de besoin, Nextcloud est une solution très complète et flexible qui mérite d'être explorée.

### Home Assistant : la domotique respectueuse de la vie privée

Pour ceux qui s'intéressent à la domotique, [Home Assistant](https://www.home-assistant.io/) est une plateforme open source qui permet de contrôler et d'automatiser les appareils connectés dans sa maison. Contrairement à des solutions propriétaires comme Google Home ou Amazon Alexa, Home Assistant peut être auto-hébergé, ce qui signifie que les données restent chez soi et ne sont pas envoyées à des serveurs externes. N'ayant pas encore d'objets connectés, j'utilise Home Assistant comme une plateforme d'expérimentation, notamment avec des assistants vocaux basés sur des LLMs open source.

### Supprimer Google de son téléphone

C'est clairement l'étape la plus difficile, surtout si on utilise un smartphone Android. En effet, dans la plus grande majorité des cas, les smartphones Android sont livrés avec les services Google préinstallés, et il est souvent impossible de les désinstaller sans rooter son téléphone. Pire que ça, Google est administrateur de l'appareil alors que vous ne l'êtes pas. Cependant, des OS alternatifs comme [GrapheneOS](https://grapheneos.org/) ou [CalyxOS](https://calyxos.org/) existent, et permettent d'avoir un téléphone Android sans les services Google. Ces OS sont basés sur le projet AOSP (Android Open Source Project), mais avec des modifications pour améliorer la sécurité et la vie privée.

J'utilise personnellement GrapheneOS sur un Pixel 9, et je suis très satisfait de cette expérience. Il y a tellement de choses à dire sur GrapheneOS et sur la manière qu'il a modifié mon utilisation du téléphone que j'écrirais un article dédié à ce sujet.

## Quelques points à considérer

Se dégoogliser c'est bien, mais il faut aussi être conscient de certains points :
- **La nécessité d'avoir un serveur** : J'ai eu l'occasion de présenter ici plusieurs services auto-hébergés, mais j'ai bien conscience que tout le monde n'a pas un serveur à disposition. Des alternatives hébergés existent, mais elles sont souvent payantes pour pouvoir financer le service.
- **La courbe d'apprentissage** : Utiliser des services alternatifs peut demander un certain temps d'adaptation. Les interfaces peuvent être moins intuitives, et certaines fonctionnalités peuvent manquer par rapport aux services grand public.
- **Le risque d'indisponibilité** : En auto-hébergeant ses services, on dépend de la disponibilité de son propre serveur. Si celui-ci tombe en panne, on peut perdre l'accès à ses données. Il faut aussi penser à faire des sauvegardes régulières, monitorer les mises à jour de sécurité, etc. C'est un peu plus de maintenance, mais c'est aussi une bonne occasion d'apprendre et de mieux comprendre comment fonctionnent ces services.

## Conclusion

La dégooglisation est un processus qui demande du temps et de la patience, mais qui peut grandement améliorer la vie privée en ligne. En choisissant des alternatives plus respectueuses de la vie privée, on reprend le contrôle sur ses données et on réduit sa dépendance aux géants du web. Il ne s'agit pas de rejeter complètement les services populaires, mais plutôt de faire des choix éclairés et de privilégier les solutions qui respectent nos valeurs. J'espère que cet article vous a donné envie de réfléchir à votre propre utilisation des services en ligne, et peut-être même de commencer votre propre démarche de dégooglisation !
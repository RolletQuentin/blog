+++
title = "Mon expérience avec GrapheneOS"
description = "Un retour d'expérience sur l'utilisation de GrapheneOS pour une meilleure vie privée numérique."
[taxonomies]
categories = ["Article", "Retour d'expérience"]
tags = ["Open Source", "Degooglisation", "Vie privée", "GrapheneOS"]
+++

Dans mon dernier article sur la [degooglisation](@/blog/2025-10-15_degooglisation.md) dans lequel j'ai partagé mes réflexions sur la réduction de ma dépendance aux services Google, j'ai mentionné que j'avais décidé d'essayer GrapheneOS comme système d'exploitation pour mon smartphone. Après plusieurs mois d'utilisation, je souhaite partager mon expérience et mes impressions sur cette alternative axée sur la vie privée.

## Qu'est-ce que GrapheneOS ?

Quand on parle de système d'exploitation alternatif pour smartphones, plusieurs noms reviennent souvent : [LineageOS](https://lineageos.org/), [e/OS](https://e.foundation/e-os/), [GrapheneOS](https://grapheneos.org/) et bien d'autres. GrapheneOS se distingue par son accent mis sur la sécurité et la vie privée. Basé sur Android Open Source Project (AOSP), il intègre des améliorations de sécurité avancées et des fonctionnalités conçues pour protéger les données des utilisateurs contre les menaces potentielles. Un des gros avantages est qu'il n'inclut pas les services Google par défaut, et grâce à son système de sandbox et de permissions strictes, il limite l'accès des applications aux données sensibles.

## Installation et configuration

L'installation est très facile, cela se fait en branchant son téléphone à son ordinateur, et grâce à leur outil d'installation directement depuis un navigateur web, on peut flasher le téléphone en quelques clics. Un des problèmes que je trouve avec GrapheneOS, c'est qu'il est uniquement compatible avec les appareils Google Pixel. Donc pour pouvoir me dégoogliser, j'ai dû donner de l'argent à Google, ce qui peut paraître un peu paradoxal 😬. Cependant, comme je disais dans mon dernier article, l'objectif est de comprendre comment les données personnelles peuvent être récupérées et utilisées, sans pour autant rejeter toutes les technologies qui sont disponibles.

Les Google Pixel restent des appareils très performants et réputés pour leur qualité photographique, ce qui en fait en couplant avec GrapheneOS un choix intéressant pour ceux qui cherchent à allier performance et vie privée.

## Utilisation quotidienne

Passons aux choses sérieuses : est-ce que GrapheneOS est pertinent au quotidien et est-ce que je m'y plais à utiliser ce système. Globalement, mon expérience est très positive ! L'interface est très proche d'un Android standard, toutes les fonctionalités que l'on recherche sur un smartphone sont présentes, et la fluidité est au rendez-vous. Ne pas avoir une flopée d'applications et de services Google préinstallés est un réel soulagement, et ne pas avoir de surcouche constructeur rend l'expérience utilisateur plus épurée.

Parmis les fonctionnalités que j'apprécie particulièrement, il y a la gestion fine des permissions des applications, qui me permet de contrôler précisément quelles données chaque application peut accéder. Il est possible de désactiver les permissions à tout moment, mais il est aussi possible de désactiver automatiquement les permissions pour les applications qui n'ont pas été utilisées depuis un certain temps, ce qui est un plus pour la sécurité. De plus, la caméra et le microphone peuvent être désactivés globalement, et un indicateur visuel apparaît lorsqu'une application y accède. Enfin, les applications sont isolées les unes des autres grâce à un système de sandboxing renforcé, ce qui fait que même si l'on utilise les services Google, ceux-ci n'ont pas accès aux données des autres applications.

> ℹ️ Il faut savoir que sur votre appareil Android standard, les services Google sont considérés comme des applications système, ce qui leur donne un accès privilégié aux données et aux fonctionnalités de l'appareil. Il faut voir cela comme si Google était administrateur de votre téléphone, et vous un simple utilisateur.
>
> Sous GrapheneOS, les services Google sont installés en tant qu'applications utilisateur, ce qui limite considérablement leur accès aux données et aux fonctionnalités de l'appareil.

Il y a aussi la possibilité de créer des profils utilisateurs séparés. Cela me permet d'avoir un profil principal où aucun compte Google n'est connecté, et un profil secondaire auquel j'ai associé mon compte Google pour les applications qui en ont besoin.

## Inconvénients

Cependant, j'aimerais mesurer un peu mes propos et vous partager quelques inconvénients que j'ai pu rencontrer :
- **Compatibilité des applications** : Certaines applications dépendent fortement des services Google pour fonctionner correctement. En soit il est toujours possible de les utiliser par exemple dans un profil séparé, mais cela peut être contraignant.
- **Indisponibilité de certaines applications** : Certaines applications ne peuvent tout simplement pas fonctionner. Certaines applications bancaires, par mesure de sécurité, refusent de fonctionner sur des appareils non certifiés par Google. Je ne suis personnellement pas concerné par ce problème, mais il faut absolument s'assurer que les applications que vous utilisez au quotidien sont compatibles avant de faire le saut.
- **La configuration initiale** : Bien que l'installation est très simple, la configuration initiale peut être un peu plus compliqué pour les utilisateurs moins expérimentés. Je dirais que ça m'a pris environ une semaine pour tout configurer à mon goût, et je conseille d'avoir quelqu'un de plus expérimenté à côté pour aider si besoin (savoir changer les Paramètres sont suffisants, pas besoin d'être un expert en informatique).
- **Le système de notifications** : Malheureusement, la très grande majorité des applications utilisent les services de notifications push de Google (Firebase Cloud Messaging), ce qui fait que sans les services Google installés avec la permission d'accéder à internet, les notifications ne fonctionnent pas. Personnellement, j'ai choisi cette solution sur mon profil principal, sans pour autant associer un compte Google, mais cela est un compromis à prendre en compte.
- **Certaines applications manquent d'alternatives** : Le seul exemple qui me vient en tête est Google Maps. Il existe des alternatives open source tel que [Organic Maps](https://organicmaps.app/) qui est une super application basée sur OpenStreetMap, mais qui n'est pas aussi complète que Google Maps (avis sur les restaurants directement dans l'application et intégration de la navigation des transports en commun par exemple).

## Conclusion

Malgré ce dernier paragraphe, je ne peux que recommander à ceux qui hésitent à sauter le pas de tester GrapheneOS. Bien que ce ne soit pas parfait à cause des nombreuses entreprises qui dépendent directement des services Google, c'est une excellente alternative pour ceux qui cherchent à améliorer leur vie privée numérique. Il reste possible d'être complètement dégooglisé en utilisant ce système d'exploitation pour les plus courageux, mais aussi de trouver un bon compromis en utilisant les services Google de manière limitée et contrôlée.

Si vous avez des questions sur des aspects que je n'ai pas abordés, ou si vous voulez que je rentre plus en détail sur certains points, n'hésitez pas à laisser un commentaire&nbsp;!
+++
title = 'Introduction aux cryptomonnaies'
date = 2024-01-19T08:00:00+01:00
draft = false
+++

Les premières monnaies existent depuis maintenant de nombreuses années. La première monnaie, selon les historiens, aurait été inventée par Crésus en Asie Mineure, qui a régné de -561 à -546 avant Jésus-Christ.

La définition de ce que l'on appelle monnaie est la suivante : pièce de métal frappée par l'autorité souveraine pour servir aux échanges. On a donc l'idée d'un objet physique permettant des échanges entre des personnes ou des groupes, et qui est contrôlée par l'État. Or, les cryptomonnaies sont assez différentes de cette définition. Nous allons donc nous pencher un peu plus sur le concept des cryptomonnaies, comment elles fonctionnent, qui les utilise et comment, et qui les contrôle.

# Qu'est ce qu'une cryptomonnaie ?

Une cryptomonnaie est une monnaie électronique émise de pair à pair, sans nécessité de banque ou banque centrale, utilisable au moyen d'un réseau informatique décentralisé.

Expliquons plus en détail ce que cela veut dire. La cryptomonnaie est émise de pair à pair, que l'on appelle aussi _peer to peer_ ou _P2P_. Cela signifie que toutes les transactions vont se passer entre un particulier et un autre particulier, sans passer par un serveur central. Comme il n'y a pas la nécessité d'un serveur central, il n'y a pas non plus besoin de banques qui gèrent les transactions. Les transactions seront écrites dans un grand livre ouvert, appelé _blockchain_, sur lequel nous reviendrons plus tard. Le tout est alors décentralisé.

# L'histoire de la cryptomonnaie

Avant de voir comment fonctionne la cryptomonnaie et comment l'utiliser, il est intéressant de connaître son histoire. Pourquoi elle a été créée, qui est son créateur et quelles sont les cryptomonnaies historiques.

La cryptomonnaie telle qu'on la connaît a été théorisée par Satoshi Nakamoto (dont on ne connaît pas l'identité, ce serait peut-être même un groupe de personnes) dans un livret blanc appelé _Bitcoin - A Peer to Peer Electronic Cash System_. Vous l'aurez donc compris, le Bitcoin est la première cryptomonnaie qui a existé. Au début, le Bitcoin ne valait rien. En effet, il n'y avait pas de réel intérêt de posséder du Bitcoin si personne ne l'utilisait. Nous le verrons après, mais la valeur d'une cryptomonnaie est plus ou moins liée à la croyance que l'on a en celle-ci. La première transaction de Bitcoin a été faite pour l'achat de pizzas, la valeur d'un Bitcoin était alors aux alentours de 30 centimes. S'ensuivent plusieurs périodes pour le Bitcoin et les cryptomonnaies : de 2010 à 2014, le marché commence à prendre forme. La valeur du Bitcoin augmente, d'autres cryptomonnaies voient le jour et le monde des cryptomonnaies se porte pour le mieux. Entre 2014 et 2016, certaines escroqueries permettent de voler des Bitcoins, mais cela a surtout servi de prévention vis-à-vis des plateformes d'échange, qui ont donc amélioré la sécurité de leurs sites. C'est ensuite entre 2016 et 2018 que les cryptomonnaies deviennent mondialement connues, le Bitcoin mais aussi l'Ethereum qui est actuellement la deuxième cryptomonnaie la plus utilisée au monde.

# Comment la cryptomonnaie fonctionne-t-elle ?

Les cryptomonnaies ne fonctionnent pas toutes exactement de la même manière, mais le principe général reste plus ou moins similaire. À titre d'exemple, je vais prendre le principe général du Bitcoin, qui est la cryptomonnaie la plus connue et la plus utilisée dans le monde.

La technologie utilisée pour faire fonctionner le Bitcoin est un peu compliquée, mais la structure reste simple. Dans un premier temps, nous pouvons parler du livre blanc.


## Le livre blanc

Le livre blanc est en quelque sorte le mode d'emploi de la monnaie, ce qui pourrait correspondre plus ou moins à de la documentation pour un développeur. Le livre blanc est connu de tous les utilisateurs et pose les règles de la cryptomonnaie. Le livre blanc, en plus des règles, peut aussi définir l'origine du concept, le contenu, l'évolution du projet et les références techniques. Pour donner un exemple, nous allons voir quelques règles par rapport au Bitcoin :

1. Le nombre maximum d'unités de Bitcoin est limité à 21 millions.
2. À l'état initial, miner 1 bloc pour la blockchain rapporte 50 Bitcoins.
3. Tous les 4 ans environ, la récompense est divisée par 2.
4. La complexité des calculs est telle qu'il faut en moyenne 10 minutes pour résoudre un problème mathématique.

Nous pourrons revenir sur l'intérêt des règles citées après avoir vu plus en détail comment fonctionne le Bitcoin.

## La blockchain

La blockchain est littéralement une chaîne de blocs, où chaque bloc contient un ensemble de transactions. Une transaction est l'envoi d'une certaine somme d'un individu A vers un individu B.

Lors de l'émission de la transaction, on ne sait pas si l'individu A possède assez de Bitcoin pour les donner à l'individu B. Dans le cadre de la monnaie classique, ce sont les banques qui vérifient si la transaction est possible. Dans le cas des cryptomonnaies, c'est la communauté qui va vérifier si cette transaction est possible.

Si on résume, la blockchain est une sorte de grand livre ouvert où toutes les transactions sont notées. Il suffit donc de lire le livre depuis son début pour connaître la somme de Bitcoin que chaque individu possède.

## Émettre une transaction

Pour émettre une transaction, rien de plus simple. Un message numérique contenant les détails de la transaction, le montant à envoyer, l'adresse du destinataire, etc., est envoyé sur le réseau. Le message est signé cryptographiquement avec la clé privée de l'émetteur, ce qui permet de prouver son autorisation. Il est donc impossible de se faire passer pour autrui et de dérober des fonds à un autre utilisateur.

## Validation de la transaction

La validation de la transaction consiste à s'assurer que la personne possède les fonds nécessaires. Pour cela, la transaction va passer par des nœuds, des machines qui vont lire la blockchain pour savoir si l'individu possède bien les fonds.

Une fois la transaction vérifiée, un nœud passe la transaction à son voisin pour obtenir plusieurs vérifications (il ne faudrait pas que l'émetteur de la transaction possède un nœud et qu'il valide la transaction alors qu'il n'a pas les fonds).

Après avoir passé plusieurs nœuds, la transaction est considérée comme vérifiée et mise dans un _mempool_, un endroit où les transactions sont mises en attente avant d'être ajoutées à la blockchain.

## Inclusion dans un bloc et minage

Les mineurs sélectionnent plusieurs transactions (souvent celles avec les frais les plus élevés) pour les inclure dans le prochain bloc qu'ils vont miner.

Pour miner un bloc, il faut résoudre un problème mathématique complexe. Le système fait en sorte que le temps moyen pour résoudre un problème mathématique soit d'environ 10 minutes. Cela signifie que plus il y a de puissance de calcul sur le réseau, plus le problème mathématique sera difficile à résoudre.

La question que l'on pourrait se poser est pourquoi s'embêter à résoudre un problème mathématique pour ajouter un bloc dans la blockchain ? En fait, c'est une question de sécurité. Les mineurs sont mis en compétition pour pouvoir créer un bloc. Un mineur malveillant pourrait, par exemple, vouloir réécrire la blockchain. Cependant, pour faire cela, il doit réécrire tous les blocs suivants, puisque chaque bloc dépend du précédent. Cela nécessiterait trop de puissance de calcul, ce qui est impossible. Il y a aussi l'attaque à 51%. Si un mineur malveillant possède plus de 51% du réseau, il pourrait faire plus ou moins ce qu'il veut. Néanmoins, c'est impossible vu la puissance de calcul totale sur le réseau, et en plus, il n'aurait aucun intérêt à le faire, puisque tout le monde s'en rendrait compte, la blockchain étant publique, les utilisateurs perdraient confiance en la monnaie, et celle-ci n'aurait donc plus aucune valeur. En somme, il est impossible de tricher à cause de la puissance de calcul sur le réseau.

Il faut noter que les mineurs ne font pas ce travail gratuitement, tout travail mérite son dû. Si un mineur est le premier à créer miner son bloc, c'est-à-dire résoudre en premier le problème mathématique pour l'ajouter à la blockchain, il est récompensé. Cela se fait de deux manières différentes. Il obtient d'abord des Bitcoins grâce à la récompense de bloc (voir les règles 2 et 3 citées précédemment). Depuis 2020, nous sommes à 6.25 Bitcoins par bloc miné, et cette somme devrait être divisée par 2 courant 2024. Les frais de transactions sont la deuxième récompense pour avoir miné un bloc. Plus les frais de transaction sont élevés, plus l'on a de chances qu'un mineur les inclue dans son bloc et plus la transaction passe rapidement.

Voici plus ou moins les principaux points concernant le minage.

## Validation du bloc

Une fois l'étape du minage faite, les nœuds vérifient le bloc hashé. C'est un processus rapide qui permet de vérifier si le bloc est valide. S'il l'est, le bloc est ajouté à la blockchain.

Nous avons vu lors de cette section les grandes lignes concernant le fonctionnement du Bitcoin. Il faut cependant noter que le tout est plus complexe que cela, et que l'on ne peut pas généraliser ce mode de fonctionnement à toutes les cryptomonnaies.

# Comment celle-ci a de la valeur ?

Maintenant que l'on a vu le fonctionnement du Bitcoin, on peut se demander comment la valeur d'une cryptomonnaie est déterminée.

En fait, celle-ci fonctionne un peu comme tous les biens dans le monde, suivant l'offre et la demande et à quel point une personne est prête à mettre le prix dans une unité.

Si nous reprenons l'exemple de la pizza du début, le vendeur de pizza a accepté de vendre deux pizzas pour 30 Bitcoins. Ce sont l'acheteur et le vendeur de pizza qui ont convenu du prix. En regardant combien coûte une pizza en euros, un simple calcul permet de connaître la valeur d'un Bitcoin.

Ensuite, plus il y a de personnes qui croient dans une cryptomonnaie, et plus celle-ci prend de la valeur.

Comme la valeur d'une cryptomonnaie dépend de l'offre et la demande, on peut comprendre les règles établies pour le Bitcoin :

1. Le nombre maximum d'unités de Bitcoin est limité à 21 millions.
2. À l'état initial, miner 1 bloc pour la blockchain rapporte 50 Bitcoins.
3. Tous les 4 ans environ, la récompense est divisée par 2.
4. La complexité des calculs est telle qu'il faut en moyenne 10 minutes pour résoudre un problème mathématique.

La règle 1 permet de ne pas créer de la monnaie à l'infini et la règle 3 permet de rendre de plus en plus rare le Bitcoin au fil du temps. Enfin, la règle 4 permet de régler plus ou moins la période sur laquelle on peut créer des Bitcoins. Le dernier fragment de Bitcoin devrait être créé aux alentours de 2140.

# Comment utiliser de la cryptomonnaie ?

Voici maintenant un court paragraphe permettant de savoir comment utiliser sa cryptomonnaie.

La cryptomonnaie s'utilise en fait comme une monnaie. Notre cryptomonnaie peut être stockée dans un portefeuille puis être utilisée pour des achats en ligne ou des transactions entre individus. Certains services permettent aussi de payer directement avec une carte bancaire sans que le commerçant s'en aperçoive. Il existe certaines cartes avec un taux de change, par exemple, ce qui permet au commerçant de recevoir ses euros alors que vous avez utilisé une cryptomonnaie. Il est donc temps d'aller chercher son pain en le payant avec des Bitcoins !

# Conclusion

Les cryptomonnaies permettent donc de s'affranchir des banques et d'avoir une devise qui n'est pas souveraine. Ce sont peut-être les monnaies de notre futur.

Certains se servent des cryptomonnaies pour investir et gagner de l'argent, d'autres les utilisent pour la croyance dans la technologie derrière et s'affranchir du système des banques. Quoi qu'il en soit, les cryptomonnaies ont marqué un tournant dans l'économie mondiale, pour le meilleur ou pour le pire.

En effet, je ne l'ai pas mentionné, mais l'utilisation des cryptomonnaies nécessite beaucoup de puissance de calcul et, par conséquent, beaucoup d'énergie. Dans le contexte du réchauffement climatique, est-il judicieux de démocratiser l'utilisation des cryptomonnaies ?

# Références

- [Wikipédia](https://fr.wikipedia.org/wiki/Cryptomonnaie)
- [RadioFrance](https://www.radiofrance.fr/franceculture/podcasts/le-pourquoi-du-comment-histoire/pourquoi-et-comment-la-monnaie-a-t-elle-ete-inventee-4000920)
- [Cryptovantage](https://www.cryptovantage.com/fr/guides/une-breve-histoire-de-la-cryptomonnaie/)
- [Coinhouse - Comment miner du Bitcoin facilement](https://www.coinhouse.com/fr/academie/bitcoin/minage-bitcoin/)
- [Coinhouse - Comment est déterminée la valeur du Bitcoin](https://www.coinhouse.com/fr/academie/bitcoin/determiner-valeur-bitcoin/)
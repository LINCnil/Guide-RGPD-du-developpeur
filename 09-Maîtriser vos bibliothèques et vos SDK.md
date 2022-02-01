# Fiche n°9 : Maîtriser vos bibliothèques et vos SDK

#### Vous utilisez des bibliothèques, kits de développement (« SDK » en anglais), ou d’autres composants logiciels écrits par des tiers ? Voici quelques conseils pour intégrer ces outils tout en gardant la maîtrise de vos développements.

## Faire un choix éclairé

* **Évaluez l’intérêt de l’ajout de chaque dépendance.** Certaines briques logicielles couramment utilisées ne font que quelques lignes. Cependant chaque élément rajouté est une augmentation de la surface d’attaque de vos systèmes. Dans le cas où une seule bibliothèque propose plusieurs fonctionnalités, n’intégrez que les fonctionnalités dont vous avez effectivement besoin : en activant le minimum de fonctionnalités, vous réduisez le nombre de bugs potentiels qui pourraient survenir.


* **Choisissez des logiciels, bibliothèques et SDK maintenus :**

    * Si vous souhaitez utiliser du logiciel libre ou *open source*, essayez de choisir des projets ou des solutions avec une communauté active, des mises à jour régulières et une bonne documentation ;

    * Si vous utilisez d’autres types de solutions avec un support commercial, assurez-vous contractuellement que le code sera maintenu et mis à jour pendant toute la durée de vie de votre projet.

* **Prenez en compte la question de la vie privée.** Certains SDK et certaines bibliothèques collectent des données personnelles depuis les applications et les sites sur lesquels ils sont intégrés. Vérifiez les engagements pris par le fournisseur de ces solutions, les directives mise en œuvre fournies. Assurez-vous enfin que l'intégration respecte les conditions suivantes :
    
    * l’utilisateur final est informé de ces opérations de traitements ;

    * un mécanisme est prévu pour recueillir le consentement des utilisateurs lorsqu’une collecte de données non strictement nécessaires pour la fourniture du service est mis en œuvre depuis son terminal ;

    * les éventuels transferts de données hors de l’union européenne sont correctement encadrés ;

    * la relation avec le tiers est encadré par un contrat de sous-traitance conforme à l’article 28 du RGPD.

* **Ces obligations s'appliquent particulièrement aux « SDK » permettant [d’afficher de la publicité ciblée sur les terminaux](https://www.cnil.fr/fr/applications-mobiles-mise-en-demeure-absence-de-consentement-geolocalisation-ciblage-publicitaire-2)**. Ils s'appliquent également à **certains outils de sécurisation des terminaux et des sites web**, tel que le système de détection d'utilisateurs reCAPTCHA de Google, qui indique dans ses conditions d’utilisation qu’en raison des traitements mise en œuvre, son usage est soumis au [consentement des utilisateurs](https://www.google.com/about/company/user-consent-policy/).

* **Si vous utilisez des mécanismes cryptographiques, il est fortement déconseillé d’implémenter des algorithmes ou des protocoles cryptographiques vous-mêmes.** Essayez plutôt de choisir des bibliothèques cryptographiques maintenues, reconnues et faciles d’utilisation.

## Évaluer les éléments choisis

* **Lisez leur documentation et changez leur configuration par défaut.** Il est important de connaître le fonctionnement de vos dépendances. Les bibliothèques et SDK tiers sont souvent fournis avec des fichiers de configuration par défaut, qui ne sont que trop rarement modifiés par manque de temps, ce qui provoque de nombreuses failles de sécurité ;

* **Auditez vos bibliothèques et SDK.** Savez-vous vraiment ce que font toutes les bibliothèques et SDK que vous intégrez ? Quelles sont les données qui sont envoyées à travers ces dépendances et quelles sont les destinataires de ces données ? Cet audit vous permettra de déterminer les obligations à respecter en matière de protection des données et d’établir la responsabilité des acteurs ;

* **Cartographiez vos dépendances.** Les bibliothèques et SDK tiers peuvent également intégrer d’autres composants : auditer leur code vous permettra de mieux cartographier toutes vos dépendances et de mieux agir si un problème affecte l’une d’elles. Il est aussi recommandé de faire des audits sécurité de vos composants tiers et d’effectuer une veille sur ceux-ci ;

<details>
     <summary> <em> Les outils de visualisation des dépendances des applications </em> </summary>
<br>

Les gestionnaires de dépendances intègrent des fonctionnalités de suivi et d'audit. A titre d'exemple, la commande `npm audit` affiche un rapport des vulnérabilités connues de chaque dépendance d'un projet _node.js_.

La visualisation des dépendances des applications compilées, ou "packagées", nécessitent des outils plus élaborés. En voici quelques exemples :

* L'[association Exodus Privacy](https://exodus-privacy.eu.org/fr/) met librement à disposition la plateforme d'analyse des applications Android εxodus.

* L'outil [otool](https://www.unix.com/man-page/osx/1/otool/) liste les dépendances des bibliothèques d'applications macOS et iOS.

* L'outil [dependency-cruiser](https://github.com/sverweij/dependency-cruiser) affiche sous forme de graphique les dépendances de projet _javascript_.


</details>
<br>

* **Faites attention aux tentatives de [*typosquattage*](https://fr.wikipedia.org/wiki/Typosquattage) et autres techniques malveillantes.** Vérifiez les noms des dépendances, ainsi que de leurs propres dépendances pour éviter des attaques. Ne copiez-collez pas de lignes de commandes depuis des sites inconnus.


## Maintenir les bibliothèques et SDK

* **Utilisez des systèmes de gestion de dépendances** (tels que yum, apt, maven, pip, etc.) afin de maintenir une liste à jour de vos dépendances.

* **Gérez les mises à jour de vos dépendances,** particulièrement dans le cas de mises à jour de sécurité qui corrigent des vulnérabilités. Vous devez mettre en place une procédure documentée pour les gérer et les déployer le plus vite possible ;

* **Faites attention aux versions des bibliothèques et SDK en fin de support** qui ne seront plus maintenues : essayez de trouver une autre solution (choisir une nouvelle bibliothèque, renouveler un support commercial) ;

* **Surveillez les statuts des projets open-source,** notamment le changement de propriétaire du domaine ou du package, certaines attaques utilisant des mises à jour malicieuses de dépendances populaires.

## Ressources utiles

* La [base de données des faiblesses du code CWE](https://cwe.mitre.org), maintenue par l'organisme MITRE, liste les vulnérabilités que l'on peut rencontrer dans les logiciels et les dépendances.


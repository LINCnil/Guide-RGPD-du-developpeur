# Fiche n°1 : Identifier les données à caractère personnel

#### Comprendre les notions de « données personnelles », de « finalité » et de « traitement » est indispensable pour le développement d’une application respectueuse de la loi et des données des utilisateurs. Attention, à ne pas confondre « anonymisation » et « pseudonymisation » qui ont des définitions précises dans le RGPD.

## Définition
* La notion de **données à caractère personnel** (couramment désignées comme “données personnelles”) est définie dans le [règlement général sur la protection des données](https://www.cnil.fr/fr/comprendre-le-rgpd) (RGPD) comme « [toute information se rapportant à une personne physique identifiée ou identifiable (dénommée “personne concernée”)](https://www.cnil.fr/fr/reglement-europeen-protection-donnees/chapitre1#Article4) ». Elle couvre un large périmètre qui comprend à la fois des données directement identifiantes (nom et prénom par exemple) et indirectement identifiantes (numéro de téléphone, plaque d’immatriculation, identifiant de terminal, etc.).

* Toute opération sur ce type de données (collecte, enregistrement, transmission, modification, diffusion, etc.) constitue **un traitement au sens du RGPD** et doit donc répondre aux exigences fixées par ce règlement. Ces traitements doivent être licites et avoir un objectif (une « finalité ») déterminée. Les données personnelles collectées et traitées doivent être pertinentes et limitées à ce qui est strictement nécessaire pour atteindre la finalité.

## Exemples de données à caractère personnel

* Lorsqu’elles sont relatives à des personnes physiques, **les données suivantes sont des données à caractère personnel** :
    * nom, prénom, pseudonyme, date de naissance ;
    * photos, enregistrements sonores de voix ;
    * numéro de téléphone fixe ou portable, adresse postale, adresse e-mail ;
    * adresse IP, identifiant de connexion informatique ou identifiant de cookie ;
    * empreinte digitale, réseau veineux ou palmaire de la main, empreinte rétinienne ;
    * numéro de plaque d’immatriculation, numéro de sécurité sociale, numéro d’une pièce d’identité ;
    * données d’usage d’une application, des commentaires, etc.

* **L’identification des personnes physiques peut se réaliser** :
    * à partir d’une seule donnée (exemples : nom et prénom) ;
    * à partir du croisement d’un ensemble de données (exemple : une femme vivant à telle adresse, née tel jour et membre de telle association).

* Certaines données sont considérées comme **particulièrement sensibles**. Le RGPD interdit de recueillir ou d’utiliser ces données, sauf, notamment, si la personne concernée a donné son consentement exprès (démarche active, explicite et de préférence écrite, qui doit être libre, spécifique, et informée).

* Ces exigences concernent les données suivantes :
    * les données relatives à la **santé des individus** ;
    * les données concernant la **vie sexuelle** ou l’**orientation sexuelle** ;
    * les données qui révèlent une prétendue **origine raciale** ou **ethnique** ;
    * les **opinions politiques**, les **convictions religieuses**, **philosophiques** ou l’**appartenance syndicale** ;
    * les **données génétiques** et **biométriques utilisées aux fins d’identifier une personne de manière unique**.

## L’anonymisation des données à caractère personnel

* Un **processus d’anonymisation de données à caractère personnel** vise à rendre impossible toute identification des individus au sein de jeux de données. Il s’agit donc d’un processus irréversible. Lorsque cette anonymisation est effective, les données ne sont plus considérées comme des données personnelles et les exigences du RGPD ne sont plus applicables.

* Par défaut, nous vous recommandons de ne **jamais considérer des jeux de données brutes comme anonymes**. Un jeu de données anonyme doit nécessairement résulter d’un processus d’anonymisation qui éliminera toute possibilité de ré-identification des individus, que ce soit par :
    * _individualisation_ : il n’est pas possible d’isoler une partie ou la totalité des enregistrements relatifs à un individu ;
    * _corrélation_ : le jeu de données ne permet pas de relier deux enregistrements se rapportant à une même personne ou à un groupe de personnes ;
    * _inférence_ : il est impossible de déduire la valeur d’un attribut d’une personne depuis des informations internes ou externes au jeu de données.

* Ces traitements de données impliquent dans la plupart des cas une **perte de qualité sur le jeu de données produit**. L’[avis G29 sur les techniques d’anonymisation](https://www.cnil.fr/fr/le-g29-publie-un-avis-sur-les-techniques-danonymisation) décrit les principales techniques d’anonymisation utilisées aujourd’hui, ainsi que des exemples de jeux de données considérés à tort comme anonymes. Il est important de signaler qu’il n’existe pas de solution universelle pour l’anonymisation des données à caractère personnel. Le choix d’anonymiser ou non les données ainsi que la sélection d’une technique d’anonymisation doit se faire au cas par cas selon les contextes d’usage et de besoin (nature des données, utilité des données, risques pour les personnes, etc.).

<details>
     <summary> <em> En savoir plus sur les techniques d'anonymisation </em> </summary>
<br>

Le [projet CabAnon](https://linc.cnil.fr/fr/cabanon-un-projet-dexploration-et-de-visualisation-de-donnees-anonymisees), développé par le Laboratoire d'Innovation Numérique de la CNIL en 2017, évalue les performances de différentes techniques d’anonymisation sur des trajets des taxis tels que rendus publics par la New-York TLC. Ce projet présente [différents scénarios d’usages](https://linc.cnil.fr/fr/cabanon-quels-usages-pour-les-donnees-anonymisees) pour lesquels les techniques d'anonymisation utilisées n’altèrent pas significativement la qualité du résultat final. Le code utilisé pour anonymiser ces données est également publié sous [licence libre](https://github.com/LINCnil/Cabanon/tree/master/Anon).
</details>

## La pseudonymisation des données à caractère personnel

* La **pseudonymisation constitue un compromis entre la conservation de données brutes et la production de jeux de données anonymisées**.

* Elle se réfère à un traitement de données personnelles réalisé de manière à ce qu’**on ne puisse plus attribuer les données relatives à une personne physique sans avoir recours à des informations supplémentaires**. Le RGPD insiste sur le fait que ces informations supplémentaires doivent être conservées séparément et être soumises à des mesures techniques et organisationnelles afin d’éviter la ré-identification des personnes concernées. Contrairement à l’anonymisation, la pseudonymisation est un processus réversible.

* En pratique, un processus de pseudonymisation consiste à **remplacer les données directement identifiantes (nom, prénom, etc.) d’un jeu de données par des données indirectement identifiantes** (alias, numéro dans un classement, etc.) afin d’en réduire leur sensibilité. Elles peuvent résulter d’un [hachage cryptographique des données](https://www.cnil.fr/fr/comprendre-les-grands-principes-de-la-cryptologie-et-du-chiffrement) des individus, tels que son adresse IP, son identifiant utilisateur, son adresse e-mail.

* Les données résultant d’une pseudonymisation sont considérées comme des **données à caractère personnel et restent donc soumises aux obligations du RGPD**. Toutefois, le règlement européen encourage l’utilisation de la pseudonymisation dans le cadre du traitement des données à caractère personnel. Par ailleurs le RGPD considère que la pseudonymisation permet de réduire les risques pour les personnes concernées et de contribuer à la mise en conformité au règlement.

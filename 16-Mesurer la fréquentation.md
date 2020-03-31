# Fiche n°16 : Mesurer la fréquentation de vos sites web et de vos applications

#### Les outils de mesures d’audience sont utilisés afin d’obtenir des informations sur la navigation des visiteurs sur un site web ou une application mobile. Ils permettent notamment de comprendre comment les utilisateurs arrivent sur un site et de reconstituer leur parcours. Utilisant des cookies, ils sont soumis à la règle du consentement, sauf dans un cas particulier.

## Obtenir le consentement

* De manière générale, **avant de déposer ou lire un cookie ou traceur,** les éditeurs de sites ou d’applications doivent :

    * informer les internautes de la finalité des cookies ;

    * obtenir leur consentement ;

    * leur fournir un moyen de les refuser.

* Sauf à rentrer exactement dans le périmètre défini ci-après, **cette obligation s’applique aux traceurs utilisés pour la mesure d’audience**.

## Bénéficier de l’exemption de consentement

* **Sous réserve d’un certain nombre de conditions**, les cookies utilisés pour la mesure d’audience sont dispensés de consentement.

* **Ces conditions, comme précisé dans les [lignes directrices sur les cookies et autres traceurs](https://www.legifrance.gouv.fr/affichTexte.do?cidTexte=JORFTEXT000038783337), sont** :

    * d’informer les utilisateurs de leur utilisation ;

    * de leur donner la faculté de s’y opposer ;

    * de limiter le dispositif aux seules finalités suivantes :

        * la mesure d’audience,

        * l’A/B testing ;

    * de ne pas recouper les données traitées avec d’autres traitements (fichiers clients, statistiques de fréquentation d’autres sites...) ;

    * de limiter la portée du traceur à un seul éditeur de site ou d’application ;

    * de tronquer le dernier octet de l’adresse IP ;

    * de limiter la durée de vie des traceurs à 13 mois.

* Dans la mesure où les conditions sont respectées, **on passe donc d'un régime d'opt-in à un régime d'opt-out**.

* Il est par ailleurs possible pour un même tiers (sous-traitant) de fournir un service de mesure d’audience comparatif à de multiples éditeurs, sous réserve que **les données soient collectées, traitées et stockées de manière indépendante pour chaque éditeur et que les traceurs soient indépendants les uns des autres**.

## En pratique

* **Les offres de mesure d’audience n’entrent pas dans le périmètre de l’exemption notamment lorsque les fournisseurs indiquent réutiliser les données pour leur propre compte.** C’est le cas notamment de plusieurs grandes offres de mesure d’audience disponibles sur le marché (voir notamment les politiques de confidentialité de [Google Analytics](https://support.google.com/analytics/answer/6004245?hl=fr), de [Quantcast Analytics](https://www.quantcast.com/terms/measure-terms-service/) ou encore de [Facebook Analytics](https://developers.facebook.com/policy)). Dans certains cas il peut être possible de configurer ces outils pour désactiver la réutilisation des données, vérifiez auprès du fournisseur de votre outil.

* Pour pouvoir bénéficier de cette exemption de consentement rapprochez-vous de votre éditeur de solution ou bien utilisez un logiciel libre tel que [Matomo](https://matomo.org/) (anciennement Piwik) que vous pouvez configurer vous-même.

# Fiche n°16 : Analyser les pratiques en matière de traceurs sur vos sites et vos applications

#### La directive européenne ePrivacy requiert le consentement de l’utilisateur avant toute action visant à stocker des informations - via des cookies, identifiants ou autres traceurs (empreintes logiciels, pixels) - ou à accéder à des informations stockées dans l’équipement terminal de l’utilisateur. Afin de se conformer à ses obligations, tout éditeur de site ou d'application doit analyser ses pratiques en terme d'usage des traceurs selon les principes présentés ci-après. 


## Les traceurs visés par l'obligation du recueil du consentement préalablement à leur usage

* **Cette obligation s’applique à toutes les solutions techniques reposant sur des opérations de lecture ou écriture dans le terminal et désignées par la CNIL sous le terme de « traceur »**. Elles s'appliquent notamment aux cookies, mais aussi aux « local shared objects » appelés parfois les « cookies Flash », le « local storage » mis en œuvre au sein du standard HTML 5, les identifications par calcul d’empreinte du terminal ou « fingerprinting », les identifiants générés par les systèmes d’exploitation (qu’ils soient publicitaires ou non : IDFA, IDFV, Android ID, etc.) ou les navigateurs (identifiants de cohorte,etc.), les identifiants matériels (adresse MAC, numéro de série ou tout autre identifiant d’un appareil), etc.

* La CNIL a identifié cinq catégories de finalité qui **nécessitent obligatoirement un consentement préalable de l'utilisateur avant leur dépôt**:
	* la publicité personnalisée ;
	* la mesure de la publicité (non ciblée) ;
	* la publicité geolocalisée ;
	* la personnalisation du contenu (éditorial ou en termes de produits) ;
	* le partage sur les réseaux sociaux. 

## Les traceurs qui ne sont pas visés par ces obligations

* **Certains traceurs peuvent être exemptés du recueil de consentement** : les traceurs destinés à l’authentification auprès d’un service, ceux destinés à garder en mémoire le contenu d’un panier d’achat sur un site marchand, certains traceurs visant à générer des statistiques de fréquentation, ou encore ceux permettant aux sites payants de limiter l’accès gratuit à un échantillon de contenu demandé par les utilisateurs.

* Le fait d'utiliser **un seul traceur pour de multiples finalités n’exonère pas de recueillir le consentement pour chacune des finalités qui le nécessite**. Par exemple, si un cookie d’authentification est également utilisé à des fins de ciblage publicitaire, le consentement de l’internaute devra être recueilli pour cette dernière finalité, de la même manière que pour un site non « loggué ».

* [Sous certaines conditions](#Fiche_n°16%c2%a0:_Mesurer_la_fréquentation_de_vos_sites_web_et_de_vos_applications), les cookies relatifs à la mesure d'audience **peuvent être exempté du recueil de consentement**. La CNIL a mis en place un programme permettant de connaître [les configurations à suivre pour différents outils](https://www.cnil.fr/fr/solutions-de-mesure-daudience-exemptees-de-consentement-la-cnil-lance-un-programme-devaluation). 

* Qu'ils soient exemptés ou non du recueil de consentement, les traitements mis en œuvre avec les informations collectées grâce à ces cookies **doivent être intégralement conformes au RGPD**. Ils doivent notamment disposer d'une base légale adéquate, d'une information et des droits associés. La fiche [Prendre en compte les bases légales dans l’implémentation technique](#Fiche_n°15_:_Prendre_en_compte_les_bases_légales_dans_l’implémentation_technique) vous accompagnera dans la bonne mise en oeuvre de ces traitements.

* Le chargement de ressources statiques sans traceurs, c'est-à-dire les images, les scripts et les feuilles de styles, **n’est pas considéré en tant que tel comme un accès ou une inscription de données dans le terminal d’utilisateur au sens de ePrivacy**, et n’est pas soumis à des obligations spécifiques à ce titre. 

## En pratique 

* Si vous utilisez des traceurs visées par ces obligations, **il vous faut suivre les étapes suivantes** :

	1- **Lister les traceurs utilisés** (tous les types de traceurs) et les classer par finalité en fonction des catégories identifiées.
	
	2- **Lister les tiers** qui déposent ces traceurs.
	
	3- **Mettre en place un blocage** des scripts ou appels HTTP déposant et accédant aux traceurs nécessitant le consentement afin de s'assurer de l'absence d'opération avant tout consentement ou bien mettre en place une solution technique permettant de garantir l’absence d’opération de lecture ou écriture tant que l’utilisateur n’a pas consenti..
	
	4- **Mettre en place une interface** qui propose à l'utilisateur de consentir au dépôt de ces traceurs.
	
	5- Sur chaque page, **intégrer une icône ou lien pour faire réapparaitre l'interface** afin de permettre le retrait du consentement.
	
	6- Régulièrement, **tester  votre site ou votre application** pour bien s'assurer qu'aucun traceur non nécessaire n'est déposé sans consentement et documentez votre conformité.

* Les finalités choisies doivent être formulées **de manière intelligible et dans un langage adapté et suffisamment clair pour permettre aux utilisateurs de comprendre précisément ce à quoi ils consentent**.

* Il est fortement recommandé de hiérarchiser les informations délivrées à l'utilisateur sur plusieurs niveaux pour plus de clarté. 

* **Le premier niveau** de l'interface doit comprendre :
	* une liste des finalités poursuivies,
	* un lien vers la liste les tiers,
	* une explication des conséquences qui s'attachent à une acceptation ou un refus,
	* un bouton pour accepter et refuser (refuser les traceurs devant être aussi aisé que de les accepter).

<p align="center"><img src="https://raw.githubusercontent.com/LINCnil/Guide-RGPD-du-developpeur/main/annexes/Bandeau-Cookie-Niveau-1.jpg" width="50%" align="middle" alt="Exemple de bannière cookie détaillant l'utilisation faite par le site web, la durée de consevation et le partage à des tiers. Trois boutons : Personnaliser mes choix, Tout refuser, Tout accepter"></p>


* Le second niveau d'interface doit **permettre à l'utilisateur de faire un choix sur la finalité de traceurs**:
<p align="center"><img src="https://raw.githubusercontent.com/LINCnil/Guide-RGPD-du-developpeur/main/annexes/Bandeau-Cookie-Niveau-2.jpg" width="30%" align="middle" style="display:inline-block;" alt="Exemple de bannière cookie permettant de donner son consentement avec des cases à cocher pour chaque finalité. Boutons Tout accepter et Tout refuser ainsi que Valider mes choix">
<img src="https://raw.githubusercontent.com/LINCnil/Guide-RGPD-du-developpeur/main/annexes/Bandeau-Cookie-Niveau-2-details.jpg" width="30%" align="middle" style="display:inline-block;" alt="Même bannière cookie que l'image précédente mais avec l'affichage de plus d'informations concernant la finalité Publicité personnalisée">
</p>

* [D'autres exemples d'interface](https://www.cnil.fr/sites/default/files/atoms/files/recommandation-cookies-et-autres-traceurs.pdf), notamment pour les applications, sont disponibles dans la recommandation de la CNIL proposant des modalités pratiques de mise en conformité en cas de recours aux "cookies et autres traceurs".

* Des sociétés proposent également des outils de _Consent Management Platform_ (CMP) ou des _Tag Managers_ pour **faciliter la mise en conformité des sites**.

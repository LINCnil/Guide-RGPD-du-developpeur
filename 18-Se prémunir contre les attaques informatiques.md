# Fiche n°18 : Se prémunir contre les attaques informatiques

#### La destruction, la perte, l'altération, ou la divulgation non autorisée de données à caractère personnel transmises, conservées ou traitées par un organisme constituent une violation de données personnelles. En tant que développeuse ou développeur, vous êtes tenu•e•s de mettre en œuvre toutes les mesures nécessaires dans vos applications pour prévenir les attaques ou les négligences pouvant entrainer de telles violations.

#### Cette fiche dresse une liste non-exhaustive de vulnérabilités ayant conduit à des violations de données notifiées à la CNIL. Elle liste des exemples de mesures qui auraient permis de les éviter.

## Manipulation d'URL

* **La manipulation d’URL** consiste à modifier les éléments d’une URL dans le navigateur en vue d’accéder à une ressource non ou mal sécurisée et auquel l’internaute ne devrait normalement pas avoir accès (page web, document accessible en ligne…).

* **Différents modes opératoires existent** :

    * **modification d’un ou de plusieurs paramètres apparaissant dans l’URL**. Elle est facilitée lorsque les paramètres permettant d’accéder à une ressource sont numériques ou alphanumériques et consécutifs (suite de chiffres ou de lettres), on parle alors « d’URL incrémentale » ;

    * **test des noms de répertoires** (/phpmyadmin/, /admin, /.git) ou de fichiers (.bak) connus dans les configurations par défaut, voire dans les informations provenant du fichier robots.txt ;

    * **test du chemin de l’arborescence affichée dans l’URL** (« path traversal ») en remontant celui-ci en vue d’obtenir du serveur un accès à des répertoires non protégés du site.

* **Des mesures permettent de limiter ce risque** :

    * **vérifier que l’émetteur de cette requête est autorisé à accéder à la ressource associée** ;

    * **valider et vérifier la bonne construction des paramètres reçus en entrée** au sein de l’URL (coté serveur) ;

    * utiliser des identifiants de ressource **qui ne soient ni uniquement numériques, ni consécutifs**, et ayant une construction aléatoire, impossible à découvrir pour les attaquants ;

    * **rendre le « path traversal » inopérant** par la mise en place d’un mécanisme de « chroot », la restriction de l’utilisation des caractères utilisés par les attaquants tels que « ../ », désactiver la fonction de « directory browsing », neutraliser les messages d'erreur en affichant un message générique de type « erreur 404" » ;


### Ressources :

* [OWASP: Path traversal](https://owasp.org/www-community/attacks/Path_Traversal)
* [Webappsec: Predictable Resource Location](http://projects.webappsec.org/w/page/13246953/Predictable%20Resource%20Location)


## Bourrage d’identifiants (“Credential stuffing”)

* Le bourrage d’identifiants (“**credential stuffing**”) consiste à réaliser des tentatives d’authentification massives sur des sites et services web à partir de couples identifiants/mots de passe. Il est le plus souvent la conséquence de violations de données ayant préalablement affecté d’autres sites web, par le biais desquelles des listes de couples d’identifiants/mots de passe sont alors disponibles en très grande quantité au sein du web caché (« dark web »).

* Il est rendu possible par la réutilisation par les utilisateurs de couples d'identifiants/mots de passe communs pour des services en ligne différents, et permet aux attaquants de prendre le contrôle de comptes utilisateurs parfois sensibles (emails, banque, réseaux sociaux)

* **Des mesures permettent de limiter ce risque** :

    * **sensibiliser régulièrement les utilisateurs aux risques d’utiliser un même mot de passe pour plusieurs comptes** ;

    * **proposer un mécanisme de double authentification** ;

    * **limiter la capacité des robots à multiplier les requêtes**, en utilisant un captcha, en limitant la fréquence des requêtes par IP et autre mesures adéquates ;

    * **prévenir les utilisateurs par courriel en cas de connexion à leur compte à partir d’un nouvel appareil**. Pour les traitements les plus sensibles, une notification pourra être envoyée à l’utilisateur à chaque connexion.

### Ressources :

* [OWASP: Credential Stuffing Attack, Credential Stuffing Prevention Cheat Sheet](https://github.com/OWASP/CheatSheetSeries/blob/master/cheatsheets/Credential_Stuffing_Prevention_Cheat_Sheet.md)
* [Retailers: Protecting Against Credential Stuffing Attacks](https://www.lexology.com/library/detail.aspx?g=453778d7-ccb7-424a-838f-d65155d55044)


## Attaques par force brute et par dictionnaire

* L’attaque par **force brute (bruteforce attack)** consiste à tester, l’une après l’autre, les combinaisons possibles d’un mot de passe ou d’une clé associé à un utilisateur sur un service en ligne, sur un fichier protégé. L’attaque par **dictionnaire** optimise cette recherche en utilisant des dictionnaires thématiques (par exemple, le dictionnaire des mots de passe les plus courants). Elle repose ainsi sur le postulat que les personnes utilisent majoritairement des mots de passe des mots ayant une signification (par exemple : un prénom, une couleur, un lieu).


* **Des mesures permettent de limiter ce risque** :

    * forcer l'utilisateur à utiliser des mots de passe conformes aux recommandations en vigueur et empêcher l’utilisation de données fréquentes (noms, prénoms et dates de naissance) et les mots de passes les plus courants (password, 12345678,…) ;

    * limiter le nombre de tentatives successives sur une période de temps données et bloquer l'accès après un trop grand nombre d’essais infructueux ;

    * inviter voire contraindre l'utilisateur à utiliser une authentification multi-facteurs (OTP, clé USB, carte à puce,…) suivant la sensibilité des données accédées ;

    * prévenir les utilisateurs par courriel en cas de en cas de connexion à leur compte à partir d’un nouvel appareil. Pour les traitements les plus sensibles, une notification pourra être envoyée à l’utilisateur à chaque connexion ;

    * afficher la date et l’heure de la dernière connexion sur l’interface de l’utilisateur.
    
### Ressources :
* [ANSSI : Recommandations relatives à l'authentification multifacteur et aux mots de passe - v2.0 du 08/10/2021](https://www.ssi.gouv.fr/uploads/2021/10/anssi-guide-authentification_multifacteur_et_mots_de_passe.pdf)
* [OWASP: Bruteforce attack](https://owasp.org/www-community/attacks/Brute_force_attack)

## Injection de code indirecte (“Cross-Site Scripting”/XSS)

* Les attaques par « injection de code indirecte » (de l'anglais **Cross-Site Scripting**, abrégé XSS) consistent à insérer un contenu malveillant dans une page d'un serveur de confiance afin qu’il soit affiché sur le navigateur de la victime.

* Ces injections peuvent permettrent **l’exécution de scripts malveillants sur le navigateur de l'internaute**. Elle peuvent notamment donner lieu : à l’affichage d’une fausse fenêtre d’authentification afin de dérober les identifiants et le mot de passe de l’utilisateur, à l’exécution de commandes système, à la redirection vers un site malveillant, à la récupération des cookies présents sur la machine (ex : cookie d’authentification), au téléchargement de programmes malveillants ou encore à l’enregistrement des frappes clavier (key logging), etc.

* Ces injections peuvent prendre plusieurs formes :

    * le contenu malveillant peut être **injecté directement sur le site** par l'attaquant, par exemple dans ses champs de commentaires ;

    * le contenu malveillant peut être inclus dans les paramètres des **requêtes envoyées aux serveurs** afin d'exploiter ses vulnérabilités, par exemple pour obtenir un accès complet à sa base de données ;

    * le contenu malveillant peut être injecté dans les paramètres d'une URL et affiché sur le navigateur de l’utilisateur comme un contenu "légitime" du site.

* **Des mesures permettent de limiter ces risques** :

    * mettre à jour les composants logiciels régulièrement ;

    * diligenter des audits de sécurité (tests de pénétration) de façon périodique et après chaque mise à jour significative ;

    * neutraliser les caractères utilisés pour l’insertion de script (> < /) lorsque c’est possible (cf. nettoyage « HTML escape ») ;

    * vérifier les éléments récupérés en paramètre et rejeter tous ceux qui ne sont pas attendus par l’application ;

    * vérifier que les téléversements (upload) légitimes (photos de profil, par exemple) sur le serveur soient au format attendu et placés dans un répertoire ne permettant pas leur exécution ;

    * exécuter des outils automatisés de détection de failles et de flux « anormaux » (présence de scripts dans les journaux et requêtes serveurs).

### Ressources :
* [CAPEC-63: Cross-Site Scripting](https://capec.mitre.org/data/definitions/63.html)
* [CERT-FR: Cross-Site Scripting](https://www.cert.ssi.gouv.fr/information/CERTA-2002-INF-001/)
* [OWASP: Cross-Site Scripting (XSS)](https://owasp.org/www-community/attacks/xss/)
* [ANSSI: Recommandations pour la sécurisation des sites web (XSS)](hhttps://www.ssi.gouv.fr/uploads/2013/05/anssi-guide-recommandations_mise_en_oeuvre_site_web_maitriser_standards_securite_cote_navigateur-v2.0.pdf#section.5.2)

## Injection SQL (SQLi)

* **L’injection SQL** est une technique permettant d’injecter du code de type SQL (langage utilisé pour manipuler certaines bases de données) dans les données envoyées au serveur web au lieu de données valides. Par exemple, un attaquant peut injecter du code SQL dans les champs des formulaires HTML ou dans les URL des pages web.

* De cette façon, les attaquants outrepassent les contrôles de sécurité et peuvent consulter ou modifier des éléments présents dans une base de données. D'autres types d'injection de code sont également possibles (par exemple : les injections LDAP, si le serveur web contacte un annuaire via une requête LDAP, ou du code bash si le serveur appelle une commande externe en passant les paramètres à un *shell*).

* **Des mesures permettent de limiter ce risque** :

    * utiliser des requêtes préparées (*Prepared Statements*) exclusivement, lorsque cela est possible ;

    * échapper les caractères susceptibles de provoquer une injection, en utilisant des fonctions spécialisées ;

    * restreindre et contrôler les entrées externes autant que possible. Par exemple, si l’identifiant est un chiffre, n’accepter que des chiffres ;

    * vérifier les données externes (notamment lorsqu’il est impossible de les restreindre ou lorsque certains caractères spéciaux utilisés en SQL sont des données acceptables en entrée) ;

    * mettre en œuvre une gestion fine des droits d’accès à la base de données. Par exemple, il est inutile d’accorder un accès total en lecture et écriture à un service qui ne fait que lire des données. Il est également possible de restreindre les droits de l'utilisateur à une seule table ou une seule base de données ;

    * neutraliser les messages d’erreur afin d’éviter la divulgation d’informations techniques recherchées par les attaquants (en affichant un message de type « erreur 403 », par exemple).

### Ressources :

* [CAPEC-66: SQL Injection](https://capec.mitre.org/data/definitions/66.html)
* [CERT-FR: Injection de données](https://www.cert.ssi.gouv.fr/information/CERTA-2004-INF-001/)
* [OWASP: Injection](https://owasp.org/Top10/A03_2021-Injection/)
* [OWASP: Prévention des injections SQL)](https://cheatsheetseries.owasp.org/cheatsheets/SQL_Injection_Prevention_Cheat_Sheet.html)

## Les programmes malveillants et les rançongiciels

* Un **malware**, ou **logiciel malveillant**, est un terme générique utilisé pour caractériser tout type de logiciel ayant pour but de nuire à un système informatique et le plus souvent à voler, modifier ou supprimer les données qui s’y trouvent. Parmi les programmes malveillants connus figurent notamment les chevaux de Troie (Trojan horse), les virus, les vers et les « espiogiciels » (spyware). Les programmes malveillants les plus fréquents ces dernières années sont les rançongiciels (“ransomware” ou “cryptolocker”).

* Ainsi, tout téléchargement ne provenant pas d’une source fiable est potentiellement un programme malveillant. Dans la majorité des cas, il est téléchargé en :

    * ouvrant la pièce jointe d’un email provenant d’une source inconnue ;

    * ou en téléchargeant un logiciel mis à disposition sur un site inconnu (ou n’étant pas de confiance) ;

    * ou en téléchargeant des logiciels associés à un logiciel connu ou provenant d’une source non fiable ;

    * ou en visitant un site web malveillant.

* Le **rançongiciel** (**ransomware**, **cryptolocker**) se transmet souvent via une pièce jointe de courriel ou via des liens permettant le téléchargement de logiciels ou de contenus. Une fois présent sur son hôte, ce programme va progressivement chiffrer tous les fichiers qui lui sont accessibles afin de les rendre illisibles par les utilisateurs. Dans le cas d’un réseau d’entreprise, le logiciel va chercher à se propager sur les ressources accessibles via le réseau en utilisant des failles connues, des mots de passe faibles ou réutilisés. L’attaquant demande alors une rançon à la personne ou à l’organisme victime en échange de la clé permettant de déchiffrer les fichiers. 

* Le rançongiciel est un malware très répandu car très rentable pour les attaquants. En effet, celui-ci exige une rançon rapide et le plus souvent en cryptomonnaie. Si ce type d’attaque est parfois opportuniste, pour des rançons correspondant généralement à quelques centaines d’Euros, certains attaquants ciblent également depuis plusieurs années des entités de tailles importantes (grandes entreprises, collectivités, etc.) pour des montants pouvant atteindre plusieurs dizaines de millions d’Euros.

* **Les mesures à mettre en œuvre afin de réduire le risque d’attaque sont surtout d’ordre organisationnel** :

    * maintenir à jour ses systèmes et logiciels (antivirus, équipements pare-feu, etc.) ; 

    * faire des sauvegardes régulières des données, les tester régulièrement et en conserver au moins une copie hors du réseau de l’organisme ;

    * sensibiliser les utilisateurs aux risques et aux bonnes pratiques : ne pas ouvrir les pièces jointes, ni cliquer sur les liens présents dans les courriels dont la provenance n’est pas fiable (surtout lorsque les pièces jointes ont une extension suspecte), ne pas installer d’application ou de programme dont l’origine n’est pas de confiance, éviter les sites non sûrs ou illicites ;

    * ne pas utiliser de compte ayant des droits « administrateur » pour l’usage quotidien (le recours aux droits « administrateur » doit être limité aux seules actions le nécessitant) ;

    * ne pas installer de logiciels piratés ou issus de sources non fiables ;

    * cloisonner son réseau interne, notamment au moyen de VLAN afin de limiter la propagation de l’attaquant, le cas échéant ;
    
    * utiliser un proxy web permettant de bloquer les sites pouvant diffuser de tels logiciels.

### Ressources :

* [Cybermalveillance : Les rançongiciels (ransomwares)](https://www.cybermalveillance.gouv.fr/tous-nos-contenus/fiches-reflexes/rancongiciels-ransomwares)
* [ANSSI: Alerte – campagne de rançongiciels](https://www.ssi.gouv.fr/actualite/alerte-campagne-de-rancongiciel/)
* [ANSSI: Etat de la menace rançongiciel](https://www.cert.ssi.gouv.fr/uploads/CERTFR-2020-CTI-001.pdf)
* [NoMoreRansom!](https://www.nomoreransom.org/fr/index.html)

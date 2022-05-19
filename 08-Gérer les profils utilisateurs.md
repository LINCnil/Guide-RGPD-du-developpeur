# Fiche n°8 : Gérer les utilisateurs

#### La manière de gérer les profils de vos collaborateurs et de vos utilisateurs finaux doit être pensée en amont de vos développements. Elle consiste à définir différents profils d’accès et d’habilitation afin que chaque personne ne puisse accéder qu’aux seules données dont il a effectivement besoin.


## Les bonnes pratiques de gestion des utilisateurs

* Tout commence par l’**utilisation d’identifiants uniques et propres à chaque individu**, qu’ils soient utilisateurs de votre application ou collaborateurs dans le développement.

* Veillez à **imposer une authentification** avant tout accès à des données personnelles, conformément aux [recommandations de la CNIL](https://www.cnil.fr/fr/mots-de-passe-des-recommandations-de-securite-minimales-pour-les-entreprises-et-les-particuliers).

* Pour vous assurer que chaque personne (utilisateur ou collaborateur) ne puisse accéder qu’**aux données dont il a effectivement besoin**, votre système doit prévoir dès la conception des **politiques de gestion d’accès aux données différenciées** (lecture, écriture, suppression, etc.) suivant les personnes et les besoins. Un mécanisme de gestion des profils utilisateurs global vous permettra de regrouper différents droits en fonction d’un rôle exercé par un groupe d’utilisateurs au sein de l’application.

* La gestion des profils utilisateurs peut s’accompagner d’**un système de journalisation** (c’est-à-dire un enregistrement dans des « fichiers journaux » ou « logs ») **afin de tracer les activités, et détecter toutes anomalies ou évènements liés à la sécurité**, comme les accès frauduleux et les utilisations abusives de données personnelles. L’utilisation de ces dispositifs ne doit en aucun cas servir à d’autres fins que celles de garantir le bon usage du système informatique et les _logs_ ne doivent pas être conservés plus longtemps que nécessaire. Ces systèmes de journalisation ne doivent pas amener à stocker des données au-delà de leur durée de conservation. De manière générale, une durée de six mois est adéquate. Assurez-vous enfin que ces traces ne comportent aucune donnée sensible.

* Vous pouvez également prévoir des audits de code ou des tests d’intrusion au sein de votre environnement de développement afin de vous **assurer de la robustesse de votre système de gestion des profils**.

## Fluidifier la gestion des profils d’habilitation

* Prévoyez de **documenter ou automatiser les procédures de mouvement de vos collaborateurs,** **d’inscription et de désinscription de vos utilisateurs**. Par exemple, ces procédures doivent encadrer les actions à mener lorsque les personnes ne sont plus habilitées à accéder à un local ou à une ressource informatique, ou à la fin de leur contrat.

* La gestion de vos utilisateurs et collaborateurs implique **une revue régulière des droits** accordés suivant l’évolution des usages et des mouvements organisationnels au sein de votre projet. L’utilisation de services d’annuaire, comme _Lightweight Directory Access Protocol_ (_LDAP_), vous aidera à suivre ces évolutions et vous permettra d’affiner vos stratégies d’accès, par exemple en attribuant des rôles suivant les profils d’usage. Cela vous permet de mieux respecter le principe de moindre privilège.


* **L’utilisation de compte "suprême" (type _root_, administrateur, etc.) est à proscrire pour les opérations conventionnelles**, car elle constitue la clé de voute de votre système et une cible privilégiée pour un éventuel attaquant externe. Nous vous recommandons d’y associer une politique de mot de passe fort (suite de 10 à 20 caractères ou multifacteur) et de limiter à son plus strict nécessaire le nombre de personnes ayant connaissance de celui-ci.


* **Favorisez l’usage d’un gestionnaire de mots de passe au sein de votre projet** et privilégiez le passage à une authentification forte lorsque c’est possible. Évitez également les comptes génériques partagés entre plusieurs personnes.

<details>
     <summary> <em> Les gestionnaires de mot de passe en pratique </em> </summary>
<br>

* Les gestionnaires de mots de passe permettent de **centraliser l'ensemble des identifiants et des mots de passe** dans une base de données unique. Certains d'entres permettent également de tester la robustesse des mots de passe et d'en générer automatiquement et de manière aléatoire tout en répondant aux contraintes imposées par les systèmes. Assurez-vous avant tout usage que les mots de passes conservées par le logiciel sont chiffrés et protégés par un mot de passe suffisamment robuste. 

* Le gestionnaire de mots de passe libre [KeePass](https://keepass.info/), dans sa en version 2.10, a obtenu la [Certification de Sécurité de Premier Niveau](https://www.ssi.gouv.fr/administration/produits-certifies/cspn/) (CSPN) de l'ANSSI.

* Les gestionnaires de mots de passe intégrés aux navigateurs sont particulièrement **exposés aux vulnérabilités des sites**, par exemple les attaques de type [Cross Site Scripting](https://www.cert.ssi.gouv.fr/information/CERTA-2002-INF-001/) (XSS) ou [Cross-Site Request Forgery](https://www.cert.ssi.gouv.fr/information/CERTA-2008-INF-003/) (CSRF). La fiche 18 [Se prémunir contre les attaques informatiques](#Fiche_n°18%c2%a0:_Se_prémunir_contre_les_attaques_informatiques) illustre en détail le fonctionnement de cette attaque.

</details>

## Ressources utiles

* La [recommandation relative à la journalisation](https://www.cnil.fr/fr/la-cnil-publie-une-recommandation-relative-aux-mesures-de-journalisation) de la CNIL qui délivre des conseils pour déterminer les mesures à prendre selon le type de traitement de données.


# Fiche n°6 : Sécuriser vos sites web, vos applications et vos serveurs

#### Tout site web, application ou serveur doit intégrer les règles élémentaires de sécurité à l'état de l'art, tant sur les communications que sur les authentifications ou son infrastructure.

## Sécuriser les communications

* **Mettez en œuvre le protocole TLS version 1.2 ou 1.3** (en remplacement de SSL) sur tous les sites web et pour les transmissions de données de vos applications mobiles, par exemple avec [LetsEncrypt](https://letsencrypt.org/fr/), en utilisant uniquement les versions les plus récentes et en vérifiant sa bonne mise en œuvre.

* **Rendez l’utilisation de TLS obligatoire** pour toutes les pages de votre site et pour vos applications mobiles.

* **Limitez les ports de communication** strictement nécessaires au bon fonctionnement des applications installées. Si l’accès à un serveur web n'est possible qu'à l'aide du protocole HTTPS, seul les ports 443 et 80 de ce serveur doivent être accessibles, tous les autres ports ayant été bloqués au niveau du pare-feu.

* **L’ANSSI a publié sur son site des [recommandations spécifiques](https://www.ssi.gouv.fr/entreprise/bonnes-pratiques/)** pour [mettre en œuvre TLS](https://www.ssi.gouv.fr/entreprise/guide/recommandations-de-securite-relatives-a-tls/) ou [pour sécuriser un site web](https://www.ssi.gouv.fr/entreprise/guide/recommandations-pour-la-securisation-des-sites-web/).

## Sécuriser les authentifications

* **Suivre [la recommandation de la CNIL sur les mots de passe](https://www.cnil.fr/fr/mots-de-passe-des-recommandations-de-securite-minimales-pour-les-entreprises-et-les-particuliers)**. Pensez notamment à limiter le nombre de tentatives d'accès.

* **Ne stockez jamais les mots de passe en clair**. Stockez-les sous forme de hash au moyen d'une librairie éprouvée, comme [bcrypt](https://en.wikipedia.org/wiki/Bcrypt).

* **Dans le cas où des cookies sont utilisés pour permettre l'authentification**, il est recommandé :

    * de forcer l'utilisation d'HTTPS via l'[HSTS](https://fr.wikipedia.org/wiki/HTTP_Strict_Transport_Security) ;

    * d'utiliser l'indicateur `secure` ;

    * d'utiliser l'indicateur `HttpOnly`.

* **Testez les suites cryptographiques installées sur les systèmes** et désactivez les suites obsolètes (RC4, MD4, MD5 etc.). Favorisez l'utilisation de l'AES256. [Lire la note de l'ANSSI sur le sujet](https://www.ssi.gouv.fr/uploads/2014/11/RGS_v-2-0_B1.pdf)

* **Adoptez une politique spécifique de mots de passe pour les administrateurs**. Changez les mots de passe, au moins, lors de chaque départ d’un administrateur et en cas de suspicion de compromission. Favorisez l'authentification forte lorsque c'est possible.

* **Limitez l’accès aux outils et interfaces d’administration aux seules personnes habilitées.** Favoriser l'usage des comptes de moindres privilèges pour les opérations courantes.

* **L'accès depuis Internet aux interfaces d'administration doit faire l'objet de mesures de sécurité renforcées.** Par exemple, pour les serveurs internes, la mise en œuvre d'un VPN avec authentification forte de l'utilisateur ainsi que du poste qu'il utilise peut être une bonne solution.

## Sécuriser les infrastructures

* **Effectuez des sauvegardes, si possible chiffrées et vérifiées régulièrement**. C'est particulièrement utile en cas d'attaque d'un rançongiciel sur vos systèmes, le fait de disposer de sauvegardes pour tous vos systèmes sera la seule mesure qui pourra vous permettre de remettre en état vos systèmes.

* **Limitez le nombre de composants mis en œuvre,** et pour chacun de ces composants :

    * **installez les mises à jour critiques** sans délai en programmant une vérification automatique hebdomadaire ;
    * **automatisez une veille des vulnérabilités** par exemple en s'inscrivant au bulletin [CERT-FR](https://www.cert.ssi.gouv.fr/).

* **Utilisez des outils de détection des vulnérabilités** pour les traitements les plus critiques afin de détecter d’éventuelles failles de sécurité. Des systèmes de détection et prévention des attaques sur des systèmes ou serveurs critiques peuvent aussi être utilisés. Ces tests doivent être menés régulièrement et avant toute mise en production d’une nouvelle version logicielle.

* **Restreignez ou interdisez l’accès physique et logique aux ports de diagnostic et de configuration à distance.** Vous pouvez par exemple lister l'ensemble des ports ouverts au moyen de l'outil *netstat*.

* **Protégez les bases de données que vous rendez accessibles sur Internet**, au moins en restreignant au maximum les accès (par exemple par filtrage IP) et en changeant le mot de passe par défaut du compte administrateur.

* En matière de gestion de bases de données, les bonnes pratiques sont notamment de :

    * **utiliser des comptes nominatifs** pour l’accès aux bases de données et créer des comptes spécifiques à chaque application ;
    * **révoquer les privilèges d'administration** des comptes nominatifs ou applicatifs pour empêcher la modification de la structure de la base de données des applications (tables, vues, procédures, etc.) ;
    * mettre en œuvre des mesures contre les attaques par injection de code SQL, de scripts, etc. ;
    * favoriser le chiffrement des données sur les disques de stockage et dans les bases de données.

# Fiche n°6 : Sécuriser vos sites web, vos applications et vos serveurs

#### Tout site web, application ou serveur doit intégrer les règles élémentaires de sécurité à l’état de l’art, tant sur les communications que sur les authentifications ou son infrastructure.

## Sécuriser les communications

* **Mettez en œuvre le protocole TLS version 1.2 ou 1.3** (en remplacement de SSL) sur tous les sites web et pour les transmissions de données de vos applications mobiles en utilisant uniquement les versions les plus récentes et en vérifiant sa bonne mise en œuvre.

* **Rendez l’utilisation de TLS obligatoire** pour toutes les pages de votre site et pour vos applications mobiles.

* **Limitez les ports de communication** strictement nécessaires au bon fonctionnement des applications installées. Si l’accès à un serveur web n’est possible qu’à l’aide du protocole HTTPS, seul le ports 443 de ce serveur, et éventuellement le port 80 afin de rediriger vers le protocole HTTPS, doit être accessible sur Internet. Les autres ports doivent alors être bloqués au niveau du pare-feu.

* **L’ANSSI a publié sur son site des [recommandations spécifiques](https://www.ssi.gouv.fr/entreprise/bonnes-pratiques/)** pour [mettre en œuvre TLS](https://www.ssi.gouv.fr/entreprise/guide/recommandations-de-securite-relatives-a-tls/) ou [pour sécuriser un site web](https://www.ssi.gouv.fr/uploads/2013/05/anssi-guide-recommandations_mise_en_oeuvre_site_web_maitriser_standards_securite_cote_navigateur-v2.0.pdf).

<details>
     <summary> <em> En savoir plus sur la mise en place de TLS</em> </summary>
<br>

La sécurisation des communications des sites et applications mobiles nécessite d'utiliser le protocole "TLS". La combinaison de ce protocole avec le protocole "HTTP" permet un échange par "HTTPS". Certains algorithmes cryptographiques employés dans TLS, et ses versions précédentes "SSL", sont réputées vulnérables à différentes attaques. Vous pouvez vous faire accompagner dans le choix de ces algorithmes au moyen de **générateurs de configuration TLS**. Celui de [Mozilla](https://ssl-config.mozilla.org/) supporte par exemple de très nombreux serveurs.

Deux exemples de configuration [Apache](annexes/conf_tls_apache.txt) et [Nginx](annexes/conf_tls_nginx.txt) commentés sont disponibles en annexe de ce guide. Vous pouvez vous référer au [Wiki Mozilla](https://wiki.mozilla.org/Security/Server_Side_TLS) pour plus de détails.

</details>

## Sécuriser les authentifications

* **Suivez [les recommandations de la CNIL sur les mots de passe](https://www.cnil.fr/fr/mots-de-passe-des-recommandations-de-securite-minimales-pour-les-entreprises-et-les-particuliers)**. Pensez notamment à limiter le nombre de tentatives d’accès.

<details>
     <summary><em>Voir une implémentation Frontend de vérification de force de mot de passe</em></summary>
<br>

Dans sa délibération du 10 janvier 2017 portant adoption d'une recommandation relative aux mots de passe, la CNIL spécifie que si le mot de passe n'est pas utilisé en conjonction avec un second facteur, et sans blocage de fréquence ("frequency capping"), un mot de passe devrait être constitué de 12 caractères et comprendre majuscule, minuscule, chiffres et caractères spéciaux.

En conséquence, pour vérifier l'adhérence à ces règles, le code suivant est adéquat :
```javascript
function checkPassword(pass) {
    if (!pass)
        return false;
    var expectations = [
	    /\d/.test(pass),
	    /[a-z]/.test(pass),
	    /[A-Z]/.test(pass),
	    /\W/.test(pass),
	    pass.length>=12
    ];
    return !expectations.includes(false);
}
```
Cela doit également s'accompagner d'une vérification backend de la force du mot de passe.

</details>

* **Ne stockez jamais les mots de passe en clair**. Stockez-les sous forme de hachage (hash) au moyen d’une librairie éprouvée, comme _Argon2_, _yescrypt_, _scrypt_, _balloon_, _bcrypt_ et, dans une moindre mesure, _PBKDF2_.

<details>
     <summary><em>Voir des modalités pratiques de hashage des mots de passe</em></summary>
<br>

Il ne faut jamais stocker les mots de passe des utilisateurs en clair dans vos bases de données, il faut systématiquement les hasher, avec un sel specifique. En pratique, bcrypt est sans doute la solution la plus simple d'utilisation. Elle utilise un sel aléatoire pour chaque hash et l'inclue dans le hash résultant pour la vérification d'un mot de passe.

Par exemple en node.js :

```javascript
#Pour installer:
npm install bcrypt
#Pour utiliser:
const bcrypt = require('bcrypt');
const saltRounds = 10; // Niveau de difficulté de bcrypt
#Enregistrer un mot de passe en DB
const passwordAStocker = '*********';
bcrypt.genSalt(saltRounds, function(err, salt) {
    bcrypt.hash(passwordAStocker, salt, function(err, hash) {
        // stockez le résultat 'hash' en DB
    });
});
#Verifier un mot de passe
const passwordAVerifier = '*********';
bcrypt.compare(passwordAVerifier, hash, function(err, result) {
    // 'result' vaut true si le mot de passe est le bon
});
```

</details>

<details>
     <summary> <em> En savoir plus sur les fonctions de hachage à clé </em> </summary>
<br>

* Les fonctions de hachage permettent d’assurer **l’intégrité des données**. Elles doivent reposer sur un algorithme **reconnu et sûr**. La famille de fonctions _SHA-2_ (par exemple _SHA-256_ et _SHA-512_) comporte des fonctions de hachage génériques qu’il ne faut pas utiliser directement pour certaines tâches spécifiques.En revanche, elles sont tout à fait acceptables comme fonction de base pour des fonctions de hachage spécialisées. Par exemple, la fonction HMAC utilisée avec SHA-256 ou SHA-512 est adaptée à la signature numérique. 

* Pour stocker les mots de passe, les fonctions adaptées sont les suivantes : _Argon2_, _yescrypt_, _scrypt_, _balloon_, _bcrypt_ et, dans une moindre mesure, _PBKDF2_. À noter que les fonctions _balloon_ et _PBKDF2_ peuvent êtres utilisées avec plusieurs fonctions de hachage sous-jacentes, le choix devant donc être fait sur une fonction reconnue (par exemple une fonction des familles _SHA-2_, _SHA-3_, _Blake2_ ou _Blake3_). 

* N'utilisez jamais d'algorithmes obsolètes, comme les chiffrements DES et 3DES ou les fonctions de hachage MD5 et SHA1. Leur utilisation peut permettre à un attaquant ayant connaissance du mot de passe haché de déchiffrer celui-ci sans difficulté et en un temps très court.

* Les fonctions de hachage à clé permettent de rendre le calcul de l’empreinte différent en fonction de la clé utilisée. Pour deux clés différentes **l’empreinte obtenue sur un même message sera différente**.

* Utilisez **des tailles de clés suffisantes**, _au minimum de 128 bits_ suivant l'algorithme utilisé. Protégez ces clés secrètes, au minimum par la **mise en œuvre de droits d’accès restrictifs** et d’**un mot de passe sûr**.

* Rédiger une procédure indiquant la manière dont les clés vont être gérés en prenant en compte **les cas d’oubli de mot de passe de déverrouillage**.

* Par exemple, le code Python suivant permet de **générer un sel aléatoire et un haché d'un mot de passe ainsi que de vérifier la validité de celui-ci** depuis la bibliothèque [bcrypt](https://pypi.org/project/bcrypt/) :

```python
import bcrypt #importation de la bibliothèque bcrypt

sel = bcrypt.gensalt() #Génération d'un sel aléatoire à conserver de manière sécurisée

hache_du_mot_de_passe = bcrypt.hashpw(mot_de_passe, sel) #Génération du hachage du mot de passe avec le sel généré

mot_de_passe_valide = bcrypt.checkpw(mot_de_passe, hache_du_mot_de_passe) #Test de la validité du mot de passe depuis son haché
```

</details>

* **Dans le cas où des cookies sont utilisés pour permettre l’authentification**, il est recommandé :

    * de protéger les cookies contre des lectures via des canaux de non chiffrées, en forcant l’utilisation d’HTTPS via l’[HSTS](https://fr.wikipedia.org/wiki/HTTP_Strict_Transport_Security), ainsi que par l'utilisation des indicateurs `Secure` et `HttpOnly` ;
    
    * d'utiliser des protections contre des [injections de requêtes illégitimes par rebond](https://www.cert.ssi.gouv.fr/information/CERTA-2008-INF-003) (cross-site request forgery ou CSRF) en utilisant des mesures de protection comme le CSRF Token et l'indicateur `SameOrigin` sur les requêtes. L'indicateur `SameSite` des cookies doit avoir la valeur `Strict` lorsque c'est possible ;
    
    * d'utiliser un sous-domaine spécifique pour déposer le token d'authentification avec l'indicateur `domain` des cookies laissés vides pour exclure les domaines tiers dans le cas où de la délégation de sous-domaine est utilisée (par exemple à travers l'usage de CNAME), ou bien des serveurs avec un faible niveau de sécurité sont destinataires des requêtes HTTP sur le domaine principal.

* **Testez les suites cryptographiques installées sur les systèmes** et désactivez les suites obsolètes (RC4, MD4, MD5, SHA1, etc.). Favorisez l’utilisation de l’AES256. [Lire la note de l’ANSSI sur le sujet](https://www.ssi.gouv.fr/uploads/2021/03/anssi-guide-selection_crypto-1.0.pdf).

* **Adoptez une politique spécifique de mots de passe pour les administrateurs**. Changez les mots de passe, au moins, lors de chaque départ d’un administrateur et en cas de suspicion de compromission. Favorisez l’authentification forte lorsque c’est possible.

* **Limitez l’accès aux outils et interfaces d’administration aux seules personnes habilitées.** Favoriser l’usage des comptes de moindres privilèges pour les opérations courantes.

* **L’accès depuis Internet aux interfaces d’administration doit faire l’objet de mesures de sécurité renforcées.** Par exemple, pour les serveurs internes, la mise en œuvre d’un VPN avec authentification forte de l’utilisateur ainsi que du poste qu’il utilise peut être une bonne solution.

## Limiter la divulgation d’information sur les comptes existants
Concevoir les processus d'authentification, de réinitialisation des mots de passe et de création de compte de manière à ce qu'un attaquant ne puisse savoir si une adresse mail spécifique possède un compte utilisateur. 

* **Généraliser les messages d'erreurs d'authentification** pour ne pas divulguer d'information sur l'existence d'un compte : _"ce couple identifiant/mot de passe est inconnu"_. 
* **Ne pas confirmer l'existence d'un compte utilisateur** en cas d'utilisation de la fonctionnalité de réinitialisation des mots de passe : _"Si un compte existe avec cette adresse un mail de réinitialisation lui a été envoyé"_
* **Faire valider l'adresse mail du compte utilisateur en tant que première étape de la création d'un compte utilisateur** avant toute collecte d'autres données personnelles, et envoyer soit un mail de validation de l'adresse si celle-ci ne dispose pas encore d'un compte, soit un mail de réinitialisation du mot de passe si l'adresse existe, en n'affichant qu'un message générique sur le service : _"un mail de validation de votre adresse ou de réinitialisation de votre mot de passe vous a été envoyé"_ 


## Sécuriser les infrastructures

* **Effectuez des sauvegardes, si possible chiffrées et vérifiées régulièrement**. C’est particulièrement utile en cas d’attaque d’un rançongiciel sur vos systèmes, le fait de disposer de sauvegardes pour tous vos systèmes sera la seule mesure qui pourra vous permettre de remettre en état vos systèmes.

* **Limitez le nombre de composants mis en œuvre,** et pour chacun de ces composants :

    * **installez les mises à jour critiques** sans délai en programmant une vérification automatique hebdomadaire ;
    
    * **automatisez une veille des vulnérabilités** par exemple en s’inscrivant au bulletin [CERT-FR](https://www.cert.ssi.gouv.fr/).

* **Utilisez des outils de détection des vulnérabilités** pour les traitements les plus critiques afin de détecter d’éventuelles failles de sécurité. Des systèmes de détection et prévention des attaques sur des systèmes ou serveurs critiques peuvent aussi être utilisés. Ces tests doivent être menés régulièrement et avant toute mise en production d’une nouvelle version logicielle.

<details>
     <summary> <em> Choisir et utiliser des outils de détection des vulnérabilités</em> </summary>
<br>

Les **outils de détection des vulnérabilités**, comme [OpenVAS](https://github.com/greenbone/openvas) et [Metasploit](https://github.com/rapid7/metasploit-framework), permettent d'identifier certaines vulnérabilités connus au sein d'applications. Certaines solutions se spécialisent sur des services particuliers, par exemple [Wordpress](https://github.com/wpscanteam/wpscan) ou [Joomla](https://github.com/rezasp/joomscan).

Il est recommandé de vérifier l'état et la fraicheur des bases de données des vulnérabilités. Ces analyses peuvent également nuire au bon fonctionnement des serveurs, elles sont donc plutôt à réaliser sur des environnements en préproduction.
</details>

* **Restreignez ou interdisez l’accès physique et logique aux ports de diagnostic et de configuration à distance.** Vous pouvez par exemple lister l’ensemble des ports ouverts au moyen de l’outil [*netstat*](https://fr.wikipedia.org/wiki/Netstat).

<details>
     <summary> <em> Auditer les ports ouverts en pratique</em> </summary>
<br>

La commande _netstat_ permet de lister les ports TCP ou UDP ouverts sur un serveur. Sur l'exemple suivant, les ports standards HTTP, HTTPS et SSH d'un serveur sont ouverts vers l'extérieur, un serveur de base de données (MariaDB) est en écoute local et des tentatives connexions sont en cours sur les ports SSH et HTTPS :

```
$ netstat -alpe --ip
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       User       Inode      PID/Program name
tcp        0      0 localhost:mysql         0.0.0.0:*               LISTEN      mysql      14492      -
tcp        0      0 0.0.0.0:http            0.0.0.0:*               LISTEN      root       50278      -
tcp        0      0 0.0.0.0:ssh             0.0.0.0:*               LISTEN      root       12948      -
tcp        0      0 0.0.0.0:https           0.0.0.0:*               LISTEN      root       50280      -
tcp        0      0 mon-serveur.fr:https adresse1.fr:38056 TIME_WAIT   root       0          -
tcp        0      0 mon-serveur.fr:ssh adresse2.com:45302  TIME_WAIT   root       0          -
tcp        0      0 mon-serveur.fr.:https adresse3.eu:56277 FIN_WAIT2   root       0          -
tcp        0      0 mon-serveur.fr:https adresse4.be:56306 ESTABLISHED www-data   380689     -
tcp        0    524 mon-serveur.fr:ssh adresse1.fr:65137 ESTABLISHED root       382490     -
```



Le logiciel [Nmap](https://nmap.org/) permet de réaliser cette analyse depuis un réseau de communication. Sur l'exemple suivant, le protocole d'administration SSH du serveur est accessible sur Internet.

```
$ nmap mon-serveur.fr
Starting Nmap 7.80 ( https://nmap.org ) at 2020-06-11 18:13 CEST
Nmap scan report for mon-serveur.fr
Host is up (0.011s latency).
Not shown: 997 filtered ports
PORT    STATE SERVICE
22/tcp  open  ssh
80/tcp  open  http
443/tcp open  https

Nmap done: 1 IP address (1 host up) scanned in 4.99 seconds
```
Il nécessite donc une attention particulière, comme l'utilisation d'une authentification forte et/ou d'un filtrage par IP.

</details>
<br>

* **Protégez les bases de données que vous rendez accessibles sur Internet**, au moins en restreignant au maximum les accès (par exemple par filtrage IP) et en changeant le mot de passe par défaut du compte administrateur.

* En matière de gestion de bases de données, les bonnes pratiques sont notamment de :

    * **utiliser des comptes nominatifs** pour l’accès aux bases de données et créer des comptes spécifiques à chaque application ;

    * **révoquer les privilèges d’administration** des comptes nominatifs ou applicatifs pour empêcher la modification de la structure de la base de données des applications (tables, vues, procédures, etc.) ;

    * mettre en œuvre des mesures contre les attaques par injection de code SQL, de scripts, etc. ;

    * favoriser le chiffrement des données sur les disques de stockage et dans les bases de données.

* Compartimentez vos différents environnements d’exécution afin d'être en mesure d'appliquer le [principe de moindre privilège sur chaque sous-partie des ces environnements](https://www.ssi.gouv.fr/uploads/2017/12/guide_cloisonnement_systeme_anssi_pg_040_v1.pdf).

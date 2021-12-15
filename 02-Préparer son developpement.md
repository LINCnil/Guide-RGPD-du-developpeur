# Fiche n°2 : Préparer son développement

#### Les principes de la protection des données à caractère personnel doivent être intégrés aux développements informatiques dès les phases de conception afin de protéger la vie privée des personnes dont vous allez traiter les données, et de leur offrir une meilleure maîtrise de leurs données et de limiter les erreurs, pertes, modifications non autorisées, ou mauvais usages de celles-ci dans les applications.

## Choix méthodologiques

* **Mettez la protection de la vie privée au cœur de vos développements** en adoptant une méthodologie de [Privacy By Design](https://edpb.europa.eu/our-work-tools/public-consultations-art-704/2019/guidelines-42019-article-25-data-protection-design_en).

* Si vous utilisez des méthodes agiles pour vos développements, pensez à **intégrer la sécurité au cœur de votre processus**. L’ANSSI a rendu disponible un guide [« sécurité & agilité numériques »](https://www.ssi.gouv.fr/uploads/2018/11/guide-securite-numerique-agile-anssi-pa-v1.pdf) qui indique comment conduire vos développements dans le cadre d’une méthode agile tout en prenant en compte les aspects sécurité. N’hésitez pas à vous en inspirer.

* Pour tout développement à destination du grand public, **menez une réflexion sur les paramètres relatifs à la vie privée**, et notamment sur le paramétrage par défaut, par exemple les caractéristiques et les contenus des utilisateurs visibles par défaut.

* **Réalisez une [analyse d’impact sur la protection des données (AIPD)](https://www.cnil.fr/fr/RGPD-analyse-impact-protection-des-donnees-aipd)**. Pour [certaines opérations de traitement](https://www.cnil.fr/sites/default/files/atoms/files/liste-traitements-avec-aipd-requise-v2.pdf), elle est obligatoire. Dans les autres cas c’est une bonne pratique qui vous permettra d’identifier et de traiter tous les risques en amont de vos développements. La CNIL dispose d’une section spéciale sur son site et elle met à disposition un [logiciel gratuit](https://www.cnil.fr/fr/outil-pia-telechargez-et-installez-le-logiciel-de-la-cnil) consacré à ce type d’analyse.


## Choix technologiques

#### Architecture et fonctionnalités

* **Intégrez la protection de la vie privée, y compris les exigences de sécurité des données, dès la conception de l’application ou du service**. Ces exigences doivent influer sur les [choix d’architecture](#Fiche_n°5%c2%a0:_Faire_un_choix_éclairé_de_son_architecture) (par exemple décentralisée vs centralisée) ou de fonctionnalités (par exemple anonymisation à bref délai, minimisation des données). Le paramétrage par défaut de l’application doit respecter les exigences minimales de sécurité et être en conformité avec la loi. Par exemple, la complexité par défaut des mots de passe doit respecter à minima la [recommandation de la CNIL relative aux mots de passe](https://www.legifrance.gouv.fr/affichCnil.do?oldAction=rechExpCnil&id=CNILTEXT000033929210&fastReqId=1726469546&fastPos=3).

* **Gardez la maîtrise de votre système**. Il est important de garder la maîtrise de votre système, autant afin d’en assurer le bon fonctionnement que de garantir un haut niveau de sécurité. Garder un système simple permet d’en comprendre précisément les rouages et d’identifier ses points de fragilité. Dans le cas où une certaine complexité est nécessaire, il est conseillé de démarrer d’un système simple, correctement conçu et sécurisé. Ensuite, il est possible d’en augmenter la complexité petit à petit, tout en continuant de sécuriser les nouveautés qui s’ajoutent.

* **Ne vous reposez pas sur une seule ligne de défense**. Malgré toutes les dispositions prises pour concevoir un système sécurisé, il peut arriver que certains composants rajoutés ultérieurement ne soient pas suffisamment sécurisés. Pour minimiser les risques sur les utilisateurs finaux, il est conseillé de défendre le système en profondeur. Exemple : contrôler les données entrées dans un formulaire en ligne fait partie des défenses de périphérie. Dans le cas où cette défense est détournée, une protection des requêtes en base de données pourra prendre le relais.

#### Outils et pratiques

* **Utilisez des normes de programmation prenant en compte la sécurité**. Souvent, des listes de normes, bonnes pratiques ou guides de codage améliorant la sécurité de vos développements sont déjà disponibles. Des outils annexes peuvent également être intégrés dans vos environnements de développement intégrés (« **IDE** » en anglais) afin de vérifier automatiquement que votre code respecte les différentes règles faisant partie de ces normes ou bonnes pratiques. Vous trouverez facilement sur internet des listes de bonnes pratiques pour votre langage de programmation favori. Par exemple [ici](https://wiki.sei.cmu.edu/confluence/display/seccode/SEI+CERT+Coding+Standards) pour C, C++ ou Java. Pour le développement d’application web, des guides de bonnes pratiques spécifiques existent, tels que ceux publiés par [l’OWASP.](https://www.owasp.org/index.php/Main_Page)

* **Le choix des technologies utilisées est crucial**. Un certain nombre de points sont à prendre en compte :

    * En fonction du domaine d’application ou de la fonctionnalité développée, un langage ou une technologie peut être plus approprié qu’une autre.

    * Les langages et technologies éprouvés sont plus sûrs. Ils ont fait, en général, l’objet d’audits afin de corriger les vulnérabilités les plus connues. Il faut cependant faire attention à utiliser les dernières versions de chacune des briques technologiques que vous utiliserez.

    * Il faut à tout prix éviter de coder sa solution définitive dans un langage tout juste appris et pas encore maîtrisé. Dans le cas contraire, vous vous exposez à un risque accru de faille de sécurité du fait du manque d’expérience.

* **Mettez en place un environnement de développement sécurisé et permettant le versionnage du code**, en suivant la [fiche dédiée](#Fiche_n°3%c2%a0:_Sécuriser_son_environnement_de_développement) de ce guide.

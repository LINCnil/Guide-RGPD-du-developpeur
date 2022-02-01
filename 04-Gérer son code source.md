# Fiche n°4 : Gérer son code source

#### Quelle que soit l’ampleur de votre projet, il est très fortement recommandé d’utiliser un outil de gestion de code source pour suivre dans le temps ses différentes versions.

## Paramétrez efficacement votre gestionnaire de code source, en pensant à sa sécurité

* Un gestionnaire de code source est un logiciel permettant de stocker **l’ensemble de votre code source et des fichiers associés**, tout en conservant la **chronologie de toutes les modifications** qui ont été apportées. Un simple serveur FTP ne constitue pas un gestionnaire de code source.

* Paramétrez correctement votre environnement en utilisant les fonctionnalités proposées par votre gestionnaire de code source. Il est recommandé de mettre en place une **authentification forte** et/ou une **authentification par clés SSH** dès le début de votre projet.

<details>
     <summary><em> Mise en place d'une authentification forte sur les services de gestion de développement de logiciels </em></summary>
<br>

* Le logiciel libre [GitLab](https://docs.gitlab.com/) offre des fonctionnalités de [double authentification](https://docs.gitlab.com/ee/user/profile/account/two_factor_authentication.html) et [d'accès par jeton d'authentification avec gestion des droits](https://docs.gitlab.com/ee/user/profile/personal_access_tokens.html). Ces deux fonctionnalités se retrouvent également sur des services web comme [GitHub](https://help.github.com/en/github/authenticating-to-github/configuring-two-factor-authentication).

*  **Pensez à sauvegarder vos codes de récupération dans un endroit sûr**, par exemple un gestionnaire de mot de passe ou conservez leur impression dans un endroit sécurisé.

</details>
<br>

* Par ailleurs, attribuez aux utilisateurs de votre gestionnaire de code source des *niveaux d’accès* à votre projet et définissez pour chacun des niveaux les **permissions** correspondantes (par exemple, un niveau « invité » avec des droits limités en lecture, un niveau « équipe de développement » avec des droits en écriture, etc.).

* Faites des **sauvegardes** régulières de votre système de gestion de code source. En particulier, pensez à sauvegarder votre serveur principal où toutes les modifications sont enregistrées.

* Mettez en place des procédures de développement pour travailler efficacement même si **plusieurs personnes développent en même temps**. Par exemple, vous pouvez décider de ne pas travailler sur la même branche (_master_ ou _main_), mais de mettre en place des branches par fonctionnalité, qui seront fusionnées dans la branche principale au fur et à mesure du développement. De telles stratégies de développement sont déjà bien documentées, par exemple dans [Git Flow](https://nvie.com/posts/a-successful-git-branching-model/). Par ailleurs, certains gestionnaires de code source proposent de configurer des **branches protégées** qui empêchent des modifications non autorisées sur les fichiers contenus dans ces branches.


## Soyez vigilant sur le contenu de votre code source

* Mettez en œuvre des **outils de métriques de qualité de code** qui scanneront votre code dès son _commit_ pour vérifier sa bonne qualité. Vous pouvez également ajouter des scripts de contrôle de ces métriques dans la [configuration du gestionnaire de code source](https://git-scm.com/book/uz/v2/Customizing-Git-Git-Hooks) : le _commit_ sera alors annulé si le code source n’est pas d’une qualité suffisante.

* Conservez vos secrets et mots de passe en dehors de votre dépôt de code source :

    * dans des **fichiers à part, qui n’ont pas fait l’objet d’un _commit_**. Pensez à utiliser les fichiers spéciaux de votre gestionnaire de code source (tels que _.gitignore_ pour _Git_) afin de ne pas _commiter_ les fichiers sensibles par erreur.

    * dans des **variables d’environnement**, en prenant soin de vérifier que les variables d’environnement ne sont pas accidentellement écrites dans des *logs* ou affichées lors d’une erreur de l’application.

    * en les stockant dans des **enclaves sécurisées** ou des **dépots séparés avec accès restreint** que vous pourrez appeler comme dépendance externe de votre projet.

    * en utilisant des **logiciels spécifiques de gestion de secrets ou de gestion de configuration** (par exemple [Vault](https://github.com/hashicorp/vault) de la société HashiCorp, [Keywhiz](https://square.github.io/keywhiz) de la société Square ou [Knox](https://github.com/pinterest/knox) de la société Pinterest).

    * Enfin, si vous devez inclure de telles données dans votre dépôt, pensez à **chiffrer/déchiffrer automatiquement** les fichiers en utilisant un *greffon* de votre gestionnaire de code source (par exemple [_git-crypt_](https://github.com/AGWA/git-crypt)).

* Après un _commit_ qui contient des données personnelles ou d’autres données critiques, n’oubliez pas de [purger](https://git-scm.com/book/en/v2/Git-Tools-Rewriting-History) [complètement](https://help.github.com/en/github/authenticating-to-github/removing-sensitive-data-from-a-repository#purging-a-file-from-your-repositorys-history) le dépôt de code source : même après modification, les données peuvent rester disponibles dans l’historique de votre dépôt.

* Faites preuve de prudence avant de **publier en ligne** votre code source. Passez en revue **l’intégralité de son contenu** afin de vous assurer qu’aucune donnée personnelle, mot de passe ou autre secret n’est présent, y compris dans tout l’historique des modifications.

## Exemples d’outils

* À l’inverse d’outils tels que [Subversion](https://subversion.apache.org/), qui ont besoin d’un serveur central pour fonctionner, les principaux gestionnaires de code source ([Git](https://git-scm.com/), [Mercurial](https://www.mercurial-scm.org/) par exemple) sont **décentralisés**.

* Pour la plupart de ces outils, une **interface web et des outils annexes** (gestion des bugs, wiki pour votre documentation, etc.) sont proposés. Ces solutions peuvent soit être accessibles par internet ([GitHub](https://github.com/), [Bitbucket](https://bitbucket.org/), etc.), soit être installées en interne sur vos serveurs ([GitLab](https://about.gitlab.com/)).

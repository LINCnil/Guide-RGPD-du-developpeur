# Fiche n°3 : Sécuriser son environnement de développement

#### La sécurité des serveurs de production, de développement, d'intégration continue ainsi que les postes de travail des développeuses et développeurs doit être une priorité car ils centralisent l'accès à un grand nombre de données.

## Évaluez vos risques et adoptez les mesures de sécurité adéquates

* **Évaluez les risques** dans les outils et les processus utilisés pour vos développements. Recensez vos mesures de sécurité existantes et définissez un plan d'action permettant d'améliorer la couverture de vos risques. Désignez une personne responsable de sa mise en œuvre.

* Pensez à prendre compte les risques sur tous les outils que vous utilisez, notamment les risques liés aux **outils SaaS** (_Software as a Service_) et collaboratifs dans le _cloud_ (type [Slack](https://slack.com), [Trello](https://trello.com), [GitHub](https://github.com), etc.).

## Sécurisez vos serveurs et vos postes de travail d'une façon homogène et reproductible

* Des listes de **recommandations** concernant la sécurisation des serveurs, postes de travail et réseaux internes sont disponibles dans les [fiches n°5 à 8](https://www.cnil.fr/fr/principes-cles/guide-de-la-securite-des-donnees-personnelles) du **guide sécurité des données personnelles** de la CNIL.

* Rédigez un **document regroupant ces mesures et expliquant leur configuration** : il permet de s'assurer d'une mise en place homogène des mesures de sécurité sur les serveurs et les postes de travail. Afin de réduire la charge de travail, des **outils de gestion de configuration**, tels qu'[Ansible](https://github.com/ansible/ansible), [Puppet](https://github.com/puppetlabs/puppet) ou [Chef](https://github.com/chef/chef), peuvent être utilisés.

* Mettez à jour les serveurs et postes de travail, si possible de manière automatique. Vous pouvez vous constituer une liste de veille recensant les vulnérabilités les plus importantes, par exemple les [alertes de sécurité](https://www.cert.ssi.gouv.fr/alerte/), [avis de sécurité](https://www.cert.ssi.gouv.fr/avis/) et les [bulletins d'actualité](https://www.cert.ssi.gouv.fr/actualite/) du CERT-FR.

## Maîtrisez vos accès et tracez les opérations

* Documentez la gestion de vos **clés SSH** (utilisation d'algorithmes de cryptographie et de longueur de clés à l'état de l'art, protection des clés privées par une _passphrase_, rotation des clés). Pour des exemples de bonnes pratiques, consulter [le document sur l'usage sécurisé d'(open)SSH](https://www.ssi.gouv.fr/uploads/2014/01/NT_OpenSSH.pdf).

<details>
     <summary> <em>La gestion de clés SSH en pratique</em></summary>
<br>

Si vous devez vous connecter à un service en ligne ou à l'un de vos serveurs, faites le choix d'algorithme asymétriques, ECDSA ou bien RSA.

Par exemple en utilisant l'outil ssh-keygen (disponible sous linux et OSX), utiliser les commandes :
```bash
ssh-keygen -t ed25519
```
Cette commande va créer ou utiliser votre répertoire de clés SSH, par exemple sur Linux `/home/username/.ssh/`), et y écrire deux éléments : une clé privée et une clé publique.

Vous pouvez alors soit envoyer la clé publique au serveur pour le configurer (si vous avez un moyen d'authentification préexistant), soit la copier dans votre presse-papier pour la fournir au service que vous souhaitez utiliser :

```bash
#Pour envoyer :
ssh-copy-id -i ~/.ssh/key.pub user@host
#Pour copier sur des systèmes Debian ou Ubuntu:
sudo apt install xclip
xclip -sel clip < ~/.ssh/key.pub
```
La clé privée ne doit jamais être envoyée ou partagée avec un tiers. Pour plus d'info sur les mesures organisationnelles à mettre en place pour une bonne gestion des clés, voir la norme [NISTIR 7966](https://nvlpubs.nist.gov/nistpubs/ir/2015/NIST.IR.7966.pdf).

</details>
<br>

* Favorisez une **authentification forte** sur les services utilisés par l'équipe de développement.

* **Tracez** les accès à vos machines et, si possible, mettez en place une **analyse automatique des journaux**. Afin de conserver des traces fiables, l'usage de compte générique est à proscrire.

* La plupart des services centralisés (Gitlab ou Jenkins par exemple) nécessite la création de jetons individuels pour authentifier les requêtes (“Webhook”). Il est recommandé d'associer une durée de vie limitée à ces jetons et de les révoquer lorsqu'ils ne sont plus utilisés.

# Fiche n°11 : Tester vos applications

#### Tester son produit permet de s’assurer de son bon fonctionnement, d’une bonne expérience utilisateur et de l'absence de certaines erreurs avant et après sa mise en production. Tester son produit permet également de réduire les risques d’atteinte aux données personnelles.

## Automatisez les tests

* Les **tests de développement** (unitaires, fonctionnels, etc.) vont vérifier l’adéquation entre les spécifications et le fonctionnement du produit. Les **tests de sécurité** (tests à données aléatoires aussi appelés « _fuzzing_», _scan_ de vulnérabilités, etc.), vont vérifier que le produit continue d’avoir un fonctionnement acceptable quand on s’éloigne de son utilisation normale et qu'il ne présente pas de vulnérabilité qui pourrait permettre à des tiers de compromettre sa sécurité. Ces deux types de tests sont importants pour le bon fonctionnement de votre application.

* Mettez en place un **système d'intégration continue** afin de lancer les tests automatiquement après chaque modification dans votre code source.

## Intégrez les tests dans votre stratégie d'entreprise

* Dans la mise en place de l’environnement de tests dans la stratégie de l’entreprise, les **métriques acceptables** doivent être définies conjointement par toutes les parties avant le développement.

* Les métriques auxquelles il faut réfléchir sont par exemple :

    * le **taux de couverture** des tests et leur type ;
    * le **taux de réplication** du code ;
    * le **nombre de vulnérabilités** (au sens de ce que détectent les outils) et leur type, etc.

## Attention aux données de test !

* Les données « réelles » de production ne **doivent pas être utilisées** pendant la phase de développement et de test. Utiliser les données personnelles issues de votre base de production à des fins de tests revient à les **détourner de leur finalité initiale**.

* En cas d'utilisation de données personnelles hors production, il faut souligner que les **risques de sécurité** sont également **augmentés** : accès aux données par des personnes qui n'ont pas le besoin d'en connaître, multiplication des lieux de stockage, etc.

* Construisez donc un **jeu de données fictives** qui ressemblera aux données qui seront traitées par votre application. Un jeu de données fictives permettra de s'assurer qu'une divulgation de ces données n'entraînera aucun impact pour les personnes.

* Si vous avez besoin d'**importer des configurations existantes** depuis la production dans vos scénarios de test, pensez à **anonymiser les données personnelles** qui peuvent être présentes.

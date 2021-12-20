# Fiche n°11 : Tester vos applications

#### Tester son produit permet de vérifier son bon fonctionnement, de s’assurer d’une bonne expérience utilisateur ainsi que de trouver et prévenir des défauts avant sa mise en production. Tester son produit permet également de réduire les risques d’atteinte aux données personnelles.

## Automatisez les tests

* Les **tests de développement** (unitaires, fonctionnels, etc.) vont vérifier l’adéquation entre les spécifications et le fonctionnement du produit. Les **tests de sécurité** (tests à données aléatoires aussi appelés « _fuzzing_ », _scan_ de vulnérabilités, etc.), vont vérifier que le produit continue d’avoir un fonctionnement acceptable quand on s’éloigne de son utilisation normale et qu’il ne présente pas de vulnérabilité qui pourrait permettre à des tiers de compromettre sa sécurité. Ces deux types de tests sont importants pour le bon fonctionnement de votre application.

* Mettez en place un **système d’intégration continue** afin de lancer les tests automatiquement après chaque modification dans votre code source.

<details>
     <summary> <em> Mise en œuvre de systèmes d'intégration continue </em> </summary>
<br>

* Les logiciels d'intégration continue permettent d'automatiser les vérifications de code et d'y associer des métriques à chaque modification de code source. Cette pratique vise à détecter les problèmes d'intégration au plus tôt dans le stade de développement comme des modifications à la mise en production.

* Des solutions propriétaires et libres existent pour interfacer cette automatisation avec les outils de gestion de code source, entre autres [Jenkins](https://www.jenkins.io/) et [GitLab CI/CD](https://docs.gitlab.com/ee/ci/).

* Une attention particulière doit être portée sur la sécurisation de ce type de solution. Veillez notamment à ce que la solution dispose pas d'accès privilégiés au gestionnaire de code source ou aux systèmes les hébergeant.

</details>
<br>

## Intégrez les tests dans votre stratégie d’entreprise

* Dans la mise en place de l’environnement de tests dans la stratégie de l’entreprise, les **métriques acceptables** doivent être définies conjointement par toutes les parties avant le développement.

* Les métriques auxquelles il faut réfléchir sont par exemple :

    * le **taux de couverture** des tests et leur type ;

    * le **taux de réplication** du code ;
    
    * le **nombre de vulnérabilités** (au sens de ce que détectent les outils) et leur type, etc.

## Attention aux données de test !

* Les données « réelles » de production ne **doivent pas être utilisées** pendant la phase de développement et de test. Utiliser les données personnelles issues de votre base de production à des fins de tests revient à les **détourner de leur finalité initiale** ;

* En cas d’utilisation de données personnelles hors production, il faut souligner que les **risques de sécurité** sont également **augmentés** : accès aux données par des personnes qui n’ont pas le besoin d’en connaître, multiplication des lieux de stockage, etc. ;

* Construisez donc un **jeu de données fictives** qui ressemblera aux données qui seront traitées par votre application. Un jeu de données fictives permettra de s’assurer qu’une divulgation de ces données n’entraînera aucun impact pour les personnes ;

<details>
     <summary><em>Les outils de génération de données fictives</em></summary>
<br>

Lors du développement de votre service, il est toujours préférable d'utiliser des données fictives. A défaut, les environnement des tests doivent faire l’objet des mêmes mesures de sécurité que l’environnement de production.

La génération de données fictives peut se faire au travers d'outils construits pour tester vos services en générant des données variées et parfois inattendues. Par exemple, en python, la librairie  [**Faker**](https://pypi.org/project/Faker/) permet simplement de générer de nombreux types de données :

```python
from faker import Faker
# Définit une instance localisée en France
fake = Faker("fr_FR")
# Numéro de téléphone
fake.phone_number()
# '+33 3 38 24 21 94'
# Adresse email
fake.ascii_email()
# 'lorraineboutin@live.com'
# Numéro de carte de crédit
fake.credit_card_number()
# '180009753513939'
# IBAN
fake.iban()
# 'FR05660487647593824219489241'
```

</details>
<br>

* Si vous avez besoin d’**importer des configurations existantes** depuis la production dans vos scénarios de test, pensez à **anonymiser les données personnelles** qui peuvent être présentes.

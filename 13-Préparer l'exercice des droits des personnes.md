# Fiche n°13 : Préparer l'exercice des droits des personnes

#### Les personnes dont vous traitez les données ont des droits sur ces données : droit d’accès, de rectification, d’opposition, d’effacement, à la portabilité et à la limitation du traitement. Vous devez leur donner les moyens d’exercer effectivement leurs droits et prévoir dans vos systèmes informatiques les outils techniques qui permettront la bonne prise en compte de leurs droits.

#### Préparer en amont la façon dont ils vous contacteront et dont vous traiterez leurs demandes vous permettra de gérer efficacement l’exercice de ces droits.


## Les mesures minimales à mettre en place

* Tous les organismes qui utilisent des données personnelles ont **l’obligation d'indiquer où et comment** les personnes peuvent exercer leurs droits relatifs à ces données. Vous pouvez par exemple mentionner une adresse e-mail ou un formulaire web au moment de l'information des personnes, ainsi que dans votre politique de vie privée.

* Afin de faciliter l’exercice des droits des personnes, ceux-ci peuvent être aussi **implémentés**, totalement ou en partie, directement dans **l’application ou le logiciel que vous développez**. Cette implémentation spécifique n’est pas obligatoire, mais elle permet de répondre aux attentes des utilisateurs et de réduire le temps et la complexité de traitement de ce type de demandes.

* Avant tout, en cas d'accès ou d'opérations directement effectuées par une personne pour exercer ses droits, n'oubliez pas de gérer son **authentification** de façon sécurisée. De manière générale, **tracez** également toutes les opérations ayant un impact sur ses données personnelles.

## Voici quelques exemples de droits et leur possible implémentation

* **Droit d’accès** : les personnes ont le droit d'obtenir une copie de toutes les informations que vous avez à leur sujet. Cela permet, entre autres, à une personne de savoir si des données la concernant sont traitées et d’en obtenir une copie lisible dans un format compréhensible. Il permet notamment de contrôler l’exactitude des données.  
**_Possible implémentation_** : prévoyez une fonctionnalité permettant d'afficher toutes les données relatives à une personne. S’il y a beaucoup de données, vous pouvez scinder ses données en plusieurs affichages. Si les données sont trop volumineuses, proposez à la personne de télécharger une archive contenant toutes ses données.

* **Droit à l'effacement** : les personnes ont le droit de  demander l’effacement de l'intégralité des données que vous détenez sur elles.  
**_Possibles implémentations_** :
    1. Prévoyez une fonctionnalité permettant d’effacer toutes les données relatives à une personne.
    2. Prévoyez aussi une notification automatique des sous-traitants afin qu’ils effacent eux aussi les données relatives à cette personne.
    3. Prévoyez un effacement des données également dans les sauvegardes, ou une autre solution permettant de ne pas restaurer les données effacées relatives à cette personne.

* **Droit d'opposition** : les personnes ont le droit de de s’opposer dans certains cas à ce que leurs données soient utilisées pour un objectif précis.  
**_Possible implémentation_** : prévoyez une fonctionnalité permettant à la personne concernée de s’opposer au traitement. Lorsque la personne exerce son droit d’opposition par ce biais, le responsable de traitement doit supprimer les données déjà collectées, et ne doit par la suite plus collecter de données associées à cette personne.

* **Droit à la portabilité** : les personnes ont le droit de récupérer leurs données dans un format lisible par machine, pour leur propre usage ou pour les fournir à un autre organisme.  
**_Possible implémentation_** : prévoyez une fonctionnalité permettant à la personne concernée de télécharger ses données dans un format standard lisible par un ordinateur (CSV, XML, JSON, etc.)

* **Droit à la rectification** : Les personnes ont le droit de demander la modification de leurs données lorsque celles-ci sont incorrectes afin de limiter l’utilisation ou la diffusion d’informations erronées.  
**_Possible implémentation_** : permettez de pouvoir modifier directement les données dans le compte utilisateur.

* **Droit à la limitation du traitement** : les personnes ont le droit de demander à ce que le traitement de leurs données soit bloqué pendant un certain temps, par exemple le temps d’examiner une contestation de sa part sur l’utilisation de ses données ou une demande d’exercice de droits.  
**_Possible implémentation_** : permettez à des administrateurs de mettre des données relatives à une personne en « quarantaine » : ces données ne pourront alors plus être lues ou modifiées.

## En conclusion

* Le site [Données & Design](https://design.cnil.fr) développé par le Laboratoire d'Innovation Numérique de la CNIL développe ces concepts et contient des [exemples d'interfaces d'exercice des droits](https://design.cnil.fr/concepts/exercice-des-droits/).

* Enfin, soyez **inventifs** ! (En cas de doute, demandez conseil à la CNIL.)

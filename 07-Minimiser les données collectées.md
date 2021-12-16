# Fiche n°7 : Minimiser les données collectées

#### Vous ne devez collecter que les données personnelles qui sont adéquates, pertinentes et nécessaires au regard des finalités de votre traitement telles que définies au moment de la collecte.

## Avant la collecte, pensez aux différents types de données que vous devez collecter et essayez de restreindre votre collecte au strict nécessaire

* Réfléchissez aux différents **types de données** qui devront être collectées avant la mise en place d’une application et **documentez** cette réflexion.

* Si des données spécifiques ne sont pas **nécessaires pour une certaine catégorie de personnes**, ne les collectez pas.

* Traitez et stockez les données de façon à **réduire leur précision** (à l’instar de la pseudonymisation). Par exemple, stockez seulement l’année de naissance au lieu d’une date de naissance complète si l’application n’a besoin que de l’année.

* En cas de collecte de données particulièrement sensibles, par exemple celles relatives à la **santé ou à des condamnations pénales**, veillez bien à ne collecter que le **minimum requis**. En raison de ces contraintes réglementaires, le plus simple est encore de **ne pas les collecter** si vous pouvez vous en passer.

* Minimisez la quantité de données collectées également dans les **données de journalisation** et n’y stockez pas de données sensibles ou critiques (données de santé, mots de passe, etc.).

* Certaines fonctionnalités peuvent permettre d’améliorer l’expérience utilisateur, mais ne sont **pas strictement nécessaires au bon fonctionnement de votre application** (par exemple la géolocalisation afin de simplifier une recherche géographique). Dans ce cas, l’utilisateur final doit pouvoir **choisir d’utiliser ou non** cette fonctionnalité. Dans le cas où il l’utilise, les données que vous êtes amené à collecter pour son fonctionnement ne doivent être conservées que pendant la durée strictement nécessaire à son fonctionnement et ne jamais être utilisées à d’autres fins.

* Pensez à associer des **durées de conservation** pour chaque catégorie de données, en fonction de la finalité du traitement et des obligations légales ou réglementaires relative à leur conservation. Les journaux doivent également avoir une durée de conservation. Documentez les durées de conservation définies. Vous devrez être en mesure de les justifier.

## Une fois les données collectées, mettez en place des mécanismes d’effacement automatique

* Mettez en œuvre un système de **purge automatique** à l’expiration de la durée de conservation. Vous pouvez également mettre en place des revues manuelles des données stockées de façon périodique.

<details>
     <summary><em>Exemple d'implémentation de purge automatique en MySQL</em></summary>
<br>

En MySQL, l'_event scheduler_ permet de supprimer les données périmées automatiquement. Par exemple :

```sql
CREATE EVENT e_mensuel
    ON SCHEDULE
      EVERY 30 DAY
    COMMENT 'supprime automatiquement les lignes inscrites de plus d un an'
    DO
      BEGIN
        DELETE from votreTable
   			WHERE datediff(now(), votreTable.votreColonneDate) > 365;
      END
```
Son pré-requis est d'associer une date d'inscription à chacune des lignes de la base de données afin de permettre le calcul de sa date de péremption.

</details>
<br>

* Afin de garantir un effacement complet, effacez **physiquement** toutes les données qui ne sont plus nécessaires grâce à des outils spécialisés ou en détruisant les supports physiques.

* Si les données sont encore utiles, vous pouvez réduire leur sensibilité en les **pseudonymisant**, voire en les **anonymisant**. En cas de pseudonymisation, ces données restent soumises à la réglementation sur les données personnelles ([voir la fiche 1](#Fiche_n°1%c2%a0:_Identifier_les_données_à_caractère_personnel)).

* Journalisez les **procédures d’effacement automatique**. Les journaux correspondants pourront être utilisés comme **preuve d’effacement** d’une donnée.

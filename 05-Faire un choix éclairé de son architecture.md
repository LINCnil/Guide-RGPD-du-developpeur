# Fiche n°5 : Faire un choix éclairé de son architecture

#### Lors de la conception de l’architecture de votre application, vous devez identifier les données personnelles qui seront collectées et définir un parcours et un cycle de vie pour chacune d’entre elles. Le choix des supports de données (stockage local, serveur, service cloud) est une étape cruciale, qui doit être adaptée à vos besoins, mais aussi à vos connaissances techniques. Le registre des activités de traitement et une analyse d’impact peuvent vous accompagner dans ce choix.

## Étudier le parcours de ses données

* Représentez et décrivez en amont du projet le fonctionnement attendu de votre projet, avec un schéma des flux de données et la description détaillée des processus mis en œuvre et des supports utilisés.

* Lorsque les données sont uniquement **stockées sur le terminal de l’utilisateur** (stockage local) ou restent **confinées sur des réseaux de communication intégralement sous la maîtrise de l’utilisateur** (par exemple, le Wi-Fi ou autre réseau local), le principal point d’attention est celui de la sécurité des données. Les durées de conservation sur ces données peuvent être déterminées par la personne elle-même ; elle doit cependant être en mesure de supprimer ces données à tout moment.

* **Lorsque les données doivent transiter par un service en ligne**, le choix d’héberger soi-même ces données ou de passer par un prestataire doit se faire en fonction de vos connaissances en sécurité et de la qualité de service attendue. Les offres de cloud reconnues peuvent présenter des niveaux de sécurité supérieurs. Cependant, elles génèrent de nouveaux risques qui doivent être maîtrisées. Pour vous aider, vous pouvez vous appuyer sur la [recommandation de la CNIL sur le Cloud computing](https://www.cnil.fr/sites/default/files/typo/document/Recommandations_pour_les_entreprises_qui_envisagent_de_souscrire_a_des_services_de_Cloud.pdf).

<details>
     <summary> <em> Quelques exemples d'étude du parcours de la donnée par la CNIL</em> </summary>
<br>

Les packs de conformité sectoriels sur les [compteurs communicants](https://www.cnil.fr/sites/default/files/typo/document/Pack_de_Conformite_COMPTEURS_COMMUNICANTS.pdf), [les véhicules connectés](https://www.cnil.fr/sites/default/files/atoms/files/pack_vehicules_connectes_web.pdf) et [la silver économie](https://www.cnil.fr/sites/default/files/atoms/files/pack_silver_economie_v4.pdf), ainsi que le [livre blanc sur les assistants vocaux](https://www.cnil.fr/sites/default/files/atoms/files/cnil_livre-blanc-assistants-vocaux.pdf) peuvent vous accompagner dans l'identification des parcours de données de votre produit.

Chaque cas d'usage met ainsi en œuvre des parcours distincts pour lesquels la création d'un compte et l'intervention d'un ou plusieurs acteurs externes peuvent être nécessaires.

La conformité de ces parcours est étudiée suivant 3 étapes :

* l'identification du traitement, du responsable et de sa base légale,
* l'identification des données collectées ainsi que de leur durée de conservation,
* l'information et la garantie des droits des personnes concernées.
 

Ces analyses peuvent vous accompagner dans l'identification des développements à prévoir, suivant les caractéristiques du traitement, la base juridique applicable et l'identification des données qui nécessitent une attention particulière du fait de leur caractère sensible.

</details>

## En cas de recours à un prestataire pour l’hébergement

* **Choisir un prestataire garantissant la mise en place de mesures de sécurité et de confidentialité appropriées, et suffisamment transparentes**. La CNIL vous propose des [modèles de clauses de confidentialité](https://www.cnil.fr/sites/default/files/typo/document/Recommandations_pour_les_entreprises_qui_envisagent_de_souscrire_a_des_services_de_Cloud.pdf).

* **S’assurer de connaître la localisation géographique des serveurs qui vont héberger vos données**. Vous pouvez être amené⋅e à effectuer des transferts de données hors de l’Union européenne (UE) et de l’espace économique européen (EEE). Si les données peuvent circuler librement dans l’UE/EEE, les transferts hors de cet espace sont possibles, à condition d’assurer un [niveau de protection des données suffisant et approprié](https://www.cnil.fr/fr/transferer-des-donnees-hors-de-lue). La CNIL fournit sur site une carte permettant de visualiser les [différents niveaux de protection des données des pays dans le monde](https://www.cnil.fr/fr/la-protection-des-donnees-dans-le-monde).

* **Si vous devez recourir à un prestataire pour héberger des données de santé**, assurez-vous que celui-ci est [certifié](https://esante.gouv.fr/labels-certifications/hds/liste-des-herbergeurs-certifies) ou [agréé](https://esante.gouv.fr/labels-certifications/hds/liste-des-herbergeurs-agrees) pour cette activité.

* Les autres points de vigilance sont notamment :
    - l’existence d’une politique de sécurité accessible ;
    - les mesures de sécurité et sûreté physique sur le site d’hébergement ;
    - le chiffrement des données et les autres procédés garantissant que le prestataire n’a pas accès aux données qui lui sont confiées ;
    - la gestion des mises à jour, la gestion des habilitations, l’authentification des personnels et la sécurité des développements applicatifs ;
    - la réversibilité/portabilité aisée des données dans un format structuré et couramment utilisé, sur demande et à tout moment.

# Fiche n°15 : Prendre en compte les bases légales dans l’implémentation technique

#### Pour pouvoir être mis en œuvre, les traitements de données personnelles doivent se fonder sur l’une des « bases légales » mentionnées à l’[article 6 du RGPD](https://www.cnil.fr/fr/reglement-europeen-protection-donnees/chapitre2#Article6). La base légale d’un traitement est en quelque sorte la justification de l’existence même du traitement. Le choix d’une base légale va directement impacter les conditions de mise en œuvre du traitement et [les droits des personnes](#Fiche_n°13_:_Préparer_l’exercice_des_droits_des_personnes). Ainsi, prévoir en amont d’un développement les bases légales des traitements prévus dans le projet vous permettra d’intégrer au mieux les fonctions nécessaires à la conformité à la loi de ces traitements et au respect des droits des personnes.

## Définition des bases légales prévues par le RGPD

* Dans le cadre d’un développement pour un organisme privé (entreprises, associations, etc.), les bases légales les plus souvent utilisées sont :
    * **le contrat** : le traitement est nécessaire à l’exécution ou à la préparation d’un contrat entre la personne concernée et l’organisme mettant en place le traitement ;
    * **l’intérêt légitime** : l’organisme mettant en place le traitement poursuit un intérêt "légitime" à mettre en place le traitement et celui-ci n’est pas susceptible d’affecter les droits et libertés des personnes concernées ;
    * **le consentement** : la personne concernée a explicitement consenti au traitement.

* Si vous êtes une autorité publique ou un organisme poursuivant des missions d’intérêt public, d’autres bases légales peuvent également être utilisées :
    * **l’obligation légale** : le traitement est imposé par des textes réglementaires;
    * **la mission d’intérêt public** : le traitement est nécessaire à l’exécution d’une mission d’intérêt public.

* Vous trouverez sur le site de la CNIL un [ensemble de fiches pratiques](https://www.cnil.fr/fr/les-bases-legales) qui vous permettra de vous accompagner dans le choix des bases légales les plus adaptées à vos traitements.

* Enfin, dans des cas très spécifiques, la **sauvegarde des intérêts vitaux** peut être retenue comme base légale, par exemple lorsque le traitement est nécessaire pour suivre la propagation d’épidémies ou dans les cas d’urgence humanitaire.

* Dans un premier temps, vérifiez sur le site de la CNIL qu’**un texte n’impose pas des contraintes particulières** (par exemple : [prospection commerciale par voie électronique](https://www.cnil.fr/fr/la-prospection-commerciale-par-courrier-electronique), [certains cookies et autres traceurs](https://www.cnil.fr/fr/site-web-cookies-et-autres-traceurs), etc.).

## Choisir la base légale adéquate

* **Une seule base légale doit être choisie** pour une finalité donnée. Les bases légales ne peuvent être cumulées pour une même finalité. Un même traitement de données peut poursuivre plusieurs finalités, c’est-à-dire plusieurs objectifs, et une base légale devra alors être définie pour chacune d’elles.

* Comme évoqué ci-dessus, si vous êtes un **organisme public**, l’obligation légale et la mission d’intérêt public seront les plus pertinentes dans la majorité des cas.

* Si votre traitement s’inscrit dans une relation contractuelle et que sa finalité est objectivement et strictement nécessaire à la fourniture du service de l’utilisateur (par exemple, le nom, le prénom et l’adresse pour créer un compte sur un site de e-commerce) alors **la base légale du contrat devrait être appropriée**.

* Si votre traitement ne s’inscrit pas dans une relation contractuelle avec l’utilisateur, alors **les bases légales du consentement ou de l’intérêt légitime** peuvent être mobilisées. Si votre traitement est potentiellement intrusif (profilage, collecte de données de géolocalisation, etc.), le consentement est susceptible d’être la base légale appropriée.

* Lorsque votre traitement contient des **données sensibles** (données de santé, données relatives à la vie ou à l’orientation sexuelle, etc.), alors vous devrez identifier, en plus de la base légale, une exception prévue par l’[article 9 du RGPD](https://www.cnil.fr/fr/reglement-europeen-protection-donnees/chapitre2#Article9).

## Les exercices des droits et les modalités d’information à prévoir suivant la base légale

* Le tableau suivant récapitule les exercices des droits à prévoir suivant les bases légales choisies :

|                       | Droit d’accès | Droit de rectification | Droit à l’effacement | Droit à la limitation du traitement | Droit à la portabilité | Droit d’opposition          |
|:---------------------:|:-------------:|:----------------------:|:--------------------:|:-----------------------------------:|:----------------------:|:---------------------------:|
| **Consentement**      | ✔             | ✔                      | ✔                    | ✔                                   | ✔                      | **retrait du consentement** |
| **Contrat**           | ✔             | ✔                      | ✔                    | ✔                                   | ✔                      | ✘                           |
| **Intérêt légitime**  | ✔             | ✔                      | ✔                    | ✔                                   | ✘                      | ✔                           |
| **Obligation légale** | ✔             | ✔                      | ✘                    | ✔                                   | ✘                      | ✘                           |
| **Intérêt public**    | ✔             | ✔                      | ✘                    | ✔                                   | ✘                      | ✔                           |
| **Intérêts vitaux**   | ✔             | ✔                      | ✔                    | ✔                                   | ✘                      | ✘                           |

* Les bases légales utilisées doivent **toujours figurer dans les informations transmises à la personne**.

* **Lorsque votre traitement est fondé sur l’intérêt légitime**, vous devrez également indiquer les intérêts légitimes poursuivis (lutte contre la fraude, sécurité du système, etc.)

* Il est recommandé de **documenter le choix de vos bases légales**. Ces choix peuvent par exemple être indiqués dans une cartographie des traitements ou associés à votre documentation technique.


## Le cas spécifique des cookies et autres traceurs

* La directive européenne ePrivacy requiert le consentement de l’utilisateur avant toute action visant à stocker des informations - via des cookies, identifiants ou autres traceurs (empreintes logiciels, pixels) - ou à accéder à des informations stockées dans l’équipement terminal de l’utilisateur.

* Une exception existe néanmoins lorsque les cookies ont pour finalité exclusive de permettre ou faciliter la communication par voie électronique, ou sont strictement nécessaires à la fourniture d’un service demandé par l’utilisateur.

* [Sous certaines conditions](#Fiche_n°16_:_Mesurer_la_fréquentation_de_vos_sites_web_et_de_vos_applications), les cookies relatifs à la mesure d'audience peuvent également être exemptés de consentement. 

* Par ailleurs, le fait d’utiliser un seul traceur pour de multiples finalités n’exonère pas de recueillir le consentement pour les finalités qui le nécessitent. Par exemple, si un cookie d’authentification est également utilisé à des fins de ciblage publicitaire, le consentement de l’internaute devra être recueilli pour cette dernière finalité, de la même manière que pour un site non « loggué ».

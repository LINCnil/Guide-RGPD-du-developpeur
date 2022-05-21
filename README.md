<p align="center"><img src="https://github.com/LINCnil/Guide-RGPD-du-developpeur/raw/main/templates/BANNIERE.JPG" width="100%" align="middle" alt="Logo Guide RGPD CNIL pour l'équipe de développement"></p>


# Guide RGPD de l'équipe de développement
#### La CNIL publie un guide RGPD pour les développeuses et développeurs

Afin de vous accompagner dans la mise en conformité de vos développements projet web ou applicatif, la CNIL a élaboré un guide de bonnes pratiques des développements en open source.

Ce guide est publié sous [licence GPLv3](https://www.gnu.org/licenses/gpl-3.0.html) et sous [licence ouverte 2.0](https://www.etalab.gouv.fr/wp-content/uploads/2017/04/ETALAB-Licence-Ouverte-v2.0.pdf) (explicitement compatible avec [CC-BY 4.0 FR](https://creativecommons.org/licenses/by/4.0/deed.fr)). Vous pouvez donc librement contribuer à son enrichissement.

#### Ce guide s’adresse-t-il uniquement aux développeuses et développeurs ?

Que vous travailliez seul(e) ou en équipe au développement d'un projet, que vous soyez amené(e) à gérer une équipe de développement, que vous soyez un prestataire, ou simplement curieux, ce guide contient une première approche des grands principes du RGPD et des différents points d’attention à prendre en compte dans le déploiement d’applications respectueuse de la vie privée de ses utilisateurs.

Il propose des conseils et des bonnes pratiques, et offre ainsi des clés de compréhension du RGPD utiles pour tous les acteurs, quelle que soit la taille de leur structure. Il peut également faire l’objet d’échanges au sein des services et dans la relation avec vos clients.

#### Que contient le guide ?

Ce guide est découpé en **18 fiches thématiques** et complété par **des exemples de codes** qui couvrent la plupart des besoins des développeuses et développeurs pour les accompagner à chaque étape de leur projet, de la préparation du développement au déploiement de nouveaux services.

Le règlement général sur la protection des données (ou RGPD) précise que la protection des droits et libertés des personnes physiques exige de prendre des **« mesures techniques et organisationnelles appropriées afin de garantir que les exigences du présent règlement sont respectées »** (considérant 78).

La détermination de ces mesures est forcément **liée au contexte des traitements mis en place**, et le responsable de traitement (l'entité publique ou privée qui traite des données personnelles) doit à ce titre assurer la sécurité des données qu'il est amené à traiter.

Les bonnes pratiques de ce guide **n’ont donc pas vocation à couvrir l’ensemble des exigences des règlementations ni à être à prescriptives**, elles apportent un premier niveau de mesures permettant de prendre en compte les problématiques de protection de la vie privée dans les développements informatiques qui ont vocation à être appliquées à tous les projets traitant des données. En fonction de la nature des traitements opérés, des mesures complémentaires devront être mises en œuvre dans certains cas afin de respecter pleinement la réglementation.

## Tables des matières

0. [Développer en conformité avec le RGPD](#Fiche_n°0%c2%a0:_Développer_en_conformité_avec_le_RGPD)

1. [Identifier les données à caractère personnel](#Fiche_n°1%c2%a0:_Identifier_les_données_à_caractère_personnel)

2. [Préparer son développement](#Fiche_n°2%c2%a0:_Préparer_son_développement)

3. [Sécuriser son environnement de développement](#Fiche_n°3%c2%a0:_Sécuriser_son_environnement_de_développement)

4. [Gérer son code source](#Fiche_n°4%c2%a0:_Gérer_son_code_source)

5. [Faire un choix éclairé de son architecture](#Fiche_n°5%c2%a0:_Faire_un_choix_éclairé_de_son_architecture)

6. [Sécuriser vos sites web, vos applications et vos serveurs](#Fiche_n°6%c2%a0:_Sécuriser_vos_sites_web,_vos_applications_et_vos_serveurs)

7. [Minimiser les données collectées](#Fiche_n°7%c2%a0:_Minimiser_les_données_collectées)

8. [Gérer les profils utilisateurs](#Fiche_n°8%c2%a0:_Gérer_les_utilisateurs)

9. [Maîtriser vos bibliothèques et vos SDK](#Fiche_n°9%c2%a0:_Maîtriser_vos_bibliothèques_et_vos_SDK)

10. [Veiller à la qualité de votre code et sa documentation](#Fiche_n°10%c2%a0:_Veiller_à_la_qualité_de_votre_code_et_sa_documentation)

11. [Tester vos applications](#Fiche_n°11%c2%a0:_Tester_vos_applications)

12. [Informer les utilisateurs](#Fiche_n°12%c2%a0:_Informer_les_personnes)

13. [Préparer l'exercice des droits des personnes](#Fiche_n°13%c2%a0:_Préparer_l’exercice_des_droits_des_personnes)

14. [Gérer la durée de conservation des données](#Fiche_n°14%c2%a0:_Gérer_la_durée_de_conservation_des_données)

15. [Prendre en compte les bases légales dans l’implémentation technique ](#Fiche_n°15%c2%a0:_Prendre_en_compte_les_bases_légales_dans_l’implémentation_technique)

16. [Analyser les pratiques en matière de traceurs sur vos sites et vos applications](#Fiche_n°16%c2%a0:_Analyser_les_traceurs)

17. [Mesurer la fréquentation de vos sites web et de vos applications](#Fiche_n°17%c2%a0:_Mesurer_la_fréquentation_de_vos_sites_web_et_de_vos_applications)

18. [Se prémunir contre les attaques informatiques](#Fiche_n°18%c2%a0:_Se_prémunir_contre_les_attaques_informatiques)

## Comment contribuer à ce guide ?

**Ce guide est disponible en deux versions** :

* Une [version web sur le site de la CNIL](https://cnil.fr/developpeur), et un export PDF dans l'onglet ["Releases"](https://github.com/LINCnil/Guide-RGPD-du-developpeur/releases) de ce repository ;
* Cette [version GitHub](https://github.com/LINCnil/Guide-RGPD-du-developpeur), qui offre la possibilité à tous d’y contribuer.

**La contribution se fait en quelques étapes** :

* Inscrivez-vous sur la plateforme Github ;
* Rendez-vous sur la page du projet ;
* Vous pouvez :
    * Utiliser l’onglet "Issue" pour ouvrir des commentaires ou participer à la discussion
    * Utiliser l'option "Fork" pour faire vos propres modifications et proposer leur inclusion via le bouton "Pull Requests"

**Votre proposition de contribution sera examinée par la CNIL avant sa publication**. La version web du guide RGPD de l'équipe de développement sera régulièrement mise à jour.

## Usage

Pour faire vous-même une « release » de ce repository, vous pouvez utiliser l’outil **Pandoc**. Cet outil vous permettra de convertir les fiches en un fichier docx ou bien un document HTML.

Vous pouvez retrouver les instructions pour installer cet outil [ici]( https://pandoc.org/installing.html)

* **Pour générer un fichier .docx** :
```bash
pandoc -s --toc --toc-depth=1 -o Guide_RGPD_developpeur.docx [0-9][0-9]*.md
```

* **Pour générer un fichier .html** :
```bash
pandoc -s --template="templates/mytemplate.html" -H templates/pandoc.css  -o index.html README.md [0-9][0-9]*.md
```

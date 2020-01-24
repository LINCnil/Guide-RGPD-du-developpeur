# Fiche n°10 : Veiller à la qualité de votre code et sa documentation
#### Il est indispensable d'adopter au plus tôt une bonne hygiène d'écriture de code. Une bonne lisibilité de votre code permettra de réduire l'effort de maintenance, d'audit et de corrections des bugs dans le temps, que vous, vos collaborateurs ou vos futurs contributeurs devront fournir.


## Documentez le code et l’architecture

* La documentation est parfois laissée de côté au moment du développement, par manque de temps ou de visibilité sur l'ensemble du projet. Elle est pourtant **cruciale pour la maintenabilité de votre projet** : elle permet de comprendre globalement le fonctionnement du code, et de savoir quelles parties du code sont affectées par une modification.

* **Documentez l’architecture, pas uniquement le code** : vous devez être en capacité de garder une vision d’ensemble lorsque vous écrivez votre documentation et d'aider les développeurs à comprendre de manière globale le fonctionnement de tous vos composants. En conséquence, privilégiez les schémas et des explications claires lorsque vous documentez votre projet.

* **Maintenez la documentation en même temps que le code** : la meilleure façon d’avoir une documentation à jour est de la modifier au fil de l'eau en même temps que le code.

* **« Versionnez » la documentation avec le code** : si vous utilisez un gestionnaire de code source vous pouvez pour chaque « _commit_ » modifiant votre code inclure également les changements de documentation (voir notamment [la fiche "Gérer son code source"](#Fiche_n°4_:_Gérer_son_code_source)).

* **Pensez à aborder la sécurité dans votre documentation** : n’oubliez pas d’envisager la dimension sécurité dans la documentation utilisateur ou développeur. Vous pouvez notamment documenter les différents choix de configuration de votre application, et expliquer quels sont les réglages les plus sécurisés.

## Contrôlez la qualité de votre code et de sa documentation

* Un code de qualité passe par l'**adoption de bonnes pratiques et de conventions de codage** appliquées de manière cohérente sur l'ensemble de votre programme. Pour choisir votre convention de codage, le mieux est de se référer à des [conventions existantes](https://github.com/Kristories/awesome-guidelines). Voici quelques exemples de bonnes pratiques supplémentaires :
    * **Utiliser des noms de variables et de fonctions explicites** permet de comprendre plus facilement ce qu’il se passe au premier regard.
    * **Correctement indenter son code** permet de percevoir la structure du code plus rapidement.
    * **Éviter la redondance de code** permet de réduire les efforts de correction qui doivent être apportés en plusieurs endroits. Un oubli est vite arrivé.

* **Des outils existent pour aider à contrôler la qualité d’un code**. Une fois correctement paramétrés, ils éviteront de relire le code pour vérifier la bonne mise en place des conventions de codage.

* **Des outils peuvent vous aider à contrôler la qualité de votre code**, par exemple :

    * Les **environnements de développement intégrés** (« _IDE_ »), éventuellement à l’aide de greffons (« _plugins_ »), peuvent être configurés pour respecter les règles d’indentation du code, les sauts de ligne entre les différentes portions de code ou encore la position des accolades et autres parenthèses.
    * Les **logiciels de mesure de la qualité du code source** peuvent signaler les duplications de code, le respect des règles de programmation ou des bugs potentiels.

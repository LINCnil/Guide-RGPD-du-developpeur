# Fiche n°10 : Veiller à la qualité de votre code et sa documentation

#### Il est indispensable d’adopter au plus tôt une bonne hygiène d’écriture de code. Une bonne lisibilité de votre code permettra de réduire l’effort de maintenance, d’audit et de corrections des bogues dans le temps, que vous, vos collaborateurs ou vos futurs contributeurs devront fournir.


## Documentez le code et l’architecture

* La documentation est parfois laissée de côté au moment du développement, par manque de temps ou de visibilité sur l’ensemble du projet. Elle est pourtant **cruciale pour la maintenabilité de votre projet** : elle permet de comprendre globalement le fonctionnement du code, et de savoir quelles parties du code sont affectées par une modification.

* **Documentez l’architecture, pas uniquement le code** : vous devez être en capacité de garder une vision d’ensemble lorsque vous écrivez votre documentation et d’aider les développeuses et développeurs à comprendre de manière globale le fonctionnement de tous vos composants. En conséquence, privilégiez les schémas et des explications claires lorsque vous documentez votre projet.

* **Maintenez la documentation en même temps que le code** : la meilleure façon d’avoir une documentation à jour est de la modifier au fil de l’eau en même temps que le code.

* **« Versionnez » la documentation avec le code** : si vous utilisez un gestionnaire de code source vous pouvez pour chaque « _commit_ » modifiant votre code inclure également les changements de documentation (voir notamment [la fiche « Gérer son code source »](#Fiche_n°4%c2%a0:_Gérer_son_code_source)).

<details>
     <summary> <em> Les outils de documentation intégrés au code </em> </summary>
<br>

Certains systèmes de documentation utilisent le **code lui-même** comme support. La documentation est ainsi écrite directement dans les commentaires du programme. 

[Doxygen](https://www.doxygen.nl/index.html), par exemple, offre une syntaxe permettant de générer de la documentation, qui est compatible avec les langages de programmation les plus utilisés. L'exemple suivant est une classe C++ commentée suivant son paradigme :

```
//!  Une classe d'exemple
/*!
  Description plus approfondie de la classe.
  (Et n'oubliez pas de documenter sans mettre de descriptions génériques dans votre projet.)
*/
 
class Example
{
  public:

    //! Le constructeur de la classe
    /*!
      Description plus approfondie du constructeur.
    */
    Example();
 
    //! Le destructeur de la classe.
    /*!
      Description plus approfondie du destructeur.
    */
    virtual ~Example();
    
    //! Une méthode qui fait quelque chose
    /*!
      \param param1 un paramètre important
      \param param2 un deuxième paramètre aussi important
      \return le résultat qui dépend des deux paramètres et de l'état interne de l'instance
    */
    int doSomething(int param1, const char *param2);
   
    //! Une variable membre publique
    /*!
      Description plus approfondie de la variable membre.
    */
    int attr_;
};
```

Certains langages de programmation supportent également nativement l'utilisation des commentaires pour documenter du code. Par exemple, les "docstrings" en Python :

```
class Example:
  """Une classe d'exemple
  Description plus approfondie de la classe.
  """
  
  def __init__(self):
    """Le constructeur de la classe
    Description plus approfondie du constructeur.
	"""
    self.attr = None
  
  def do_something(self, param1, param2):
    """Une méthode qui fait quelque chose
    param1: un paramètre important
    param2: un deuxième paramètre aussi important
    return: le résultat qui dépend des deux paramètres et de l'état interne de l'instance
	"""
    [...]
    return result
	
help(Example)
# affiche la documentation complète de la classe, qui est générée en partie à partir des docstrings
help(Example.do_something)
# affiche uniquement la documentation de la méthode
```
</details>

* **Pensez à aborder la sécurité dans votre documentation** : n’oubliez pas d’envisager la dimension sécurité dans la documentation utilisateur ou développeur. Vous pouvez notamment documenter les différents choix de configuration de votre application, et expliquer quels sont les réglages les plus sécurisés.

## Contrôlez la qualité de votre code et de sa documentation

* Un code de qualité passe par l’**adoption de bonnes pratiques et de conventions de codage** appliquées de manière cohérente sur l’ensemble de votre programme. Pour choisir votre convention de codage, le mieux est de se référer à des [conventions existantes](https://github.com/Kristories/awesome-guidelines). Voici quelques exemples de bonnes pratiques supplémentaires :

    * **utiliser des noms de variables et de fonctions explicites** permet de comprendre plus facilement ce qu’il se passe au premier regard ;

    * **correctement indenter son code** permet de percevoir la structure du code plus rapidement ;

    * **éviter la redondance de code** permet de réduire les efforts de correction qui doivent être apportés en plusieurs endroits. Un oubli est vite arrivé.

* **Des outils peuvent vous aider à contrôler la qualité de votre code**. Une fois correctement paramétrés, ils éviteront de relire le code pour vérifier la bonne mise en place des conventions de codage. En voici quelques exemples :  

    * les **environnements de développement intégrés** (« _IDE_ »), éventuellement à l’aide de greffons (« _plugins_ »), peuvent être configurés pour respecter les règles d’indentation du code, les sauts de ligne entre les différentes portions de code ou encore la position des accolades et autres parenthèses ;
    
    * les **logiciels de mesure de la qualité du code source** peuvent signaler les duplications de code, le respect des règles de programmation ou des bugs potentiels.

<details>
     <summary> <em> Les outils de mesure de la qualité d'un code </em> </summary>
<br>

Certains langages de programmation disposent d'un **style de programmation standard**, par exemple [PEP8](https://www.python.org/dev/peps/pep-0008/) pour le langage Python. Des outils automatiques peuvent contrôler le respect de ces styles, par exemple [pep8.py](https://pep8.readthedocs.io/en/release-1.7.x/intro.html) pour la PEP8. Pour les langages ne disposant pas de styles de programmation standard, différents styles ont été créés, avec des outils automatiques permettant de les vérifier, par exemple [SonarQube](https://github.com/SonarSource/sonarqube) ou [checkstyle](https://checkstyle.org/) pour Java.

Des **outils de qualité de code plus généraux** peuvent détecter un certain nombre de problèmes : variables non utilisées ou non définies, duplication de code, etc. Par exemple [ESLint](https://eslint.org) pour Javascript ou [Clippy](https://github.com/rust-lang/rust-clippy) pour Rust.

Enfin, des **outils d'analyse statique** permettent une analyse plus fine du code, afin d'évaluer son comportement sans pour autant exécuter le programme, par exemple [SpotBugs](https://spotbugs.github.io/) pour Java ou [Frama-C](http://frama-c.com/) pour le C.
</details>

% Premiers pas en Java

Contexte général
=========================

Un peu d'histoire
-----------------------------------------

Java a été développé dans les années 1990 par des ingénieurs de Sun Microsystems insatisfaits du langage C++, pour les systèmes embarqués :

  - Gestion de la mémoire souvent source d'erreur (pointeurs)

  - Nécessité de nettoyer soi-même la mémoire en désallouant explicitement les objets : pas de ramasse-miettes (garbage collector en anglais)

  - Non original : oak (chêne)


-----------------------------------------

  - 1995 : présentation officielle sous le nom de Java

  - Exécution de code dans des pages web au moyen "d'applets"

  - Nécessité d'avoir du code portable, compatible avec n'importe quel OS
  
  - Utilisation de la JVM

-----------------------------------------

  - Depuis 2000 : sortie d'une version majeure de Java tous les deux ans
  
  - 2009 : rachat de Sun Microsystems par Oracle

  - Employé largement dans le développement des premières App. Android

  - Langage le plus "populaire" selon l'indice Tiobe...

Principes de Java 
------------------------------------------

Compilation du code une fois pour toute !

  - Fichiers sources : " *.java "
  
  - Après compilation : " *.class " : 
  
    -  bytecode **indépendant** du système d'exploitation 
    
    -  Destiné à être exécuté par la **JVM** (Java Virtual Machine)

  - Une fonction **principale** pour l'exécution : **main**


Java : les promesses 
------------------------------------------

  - Déploiement **facile** des applications :

    - Le bytecode généré fonctionne sur tout OS,
    
    - Une seule compilation / archivage avant la distribution 

 - Pas de gestion compliquée de la mémoire

 - Paradigme objet facile à appréhender (pas d'héritage multiple)

Objectifs de cette session : 
-----------------------------------------

  - Introduction aux différents **types** en Java

  - Introduction aux opérations de base

  - Introduction aux instructions de **flow control**

  - Introduction à la fonction main

Les types Java 
=======================================

Types de base
--------------------------------------
Java est un langage fortement typé. Presque tous les types sont objets.

À l'exception de 8 types de base : 


  - **byte**, **short**, **int**, **long**

  - **float**, **double**

  - **boolean**

  - **char**
  
 Les différents entiers
-------------------------------------

  - **byte** : entier signé sur 8 bits $[-128,127]$

  - **short** : entier signé sur 16 bits $[-32768,32767]$

  - **int** : entier signé sur 32 bits $[-2^{31},2^{31}-1]$

  - **long** : entier signé sur 64 bits $[-2^{63},2^{63}-1]$ 

Les entiers littéraux
-------------------------------------

  - Par défaut des **int** (ex. : 1, 2, 3,...)

  - **byte**, **short**, **int** et **long** peuvent être initialisés avec un entier littéral

  - Les **long** avec des valeurs supérieures à $2^31$ peuvent être initialisés avec des littéraux finissant par "L" (ex. : 1000000000L)

  - Possibilité d'ajouter des underscores "_" pour la lisibilité (ex. : 1_100) 


À essayer dans l'interpréteur BlueJ
------------------------------------
*Note : sans point-virgule, on récupère directement le résultat* 
    
    1_000_000 // On va afficher l'entier 1 million
    int i = 1_000_000 ; 
    10_000_000_000 // On essaye d'afficher 10 milliards (> 2^31)
    10_000_000_000L  
    int j = 10_000_000_000L // Que passe-t-il ?
    long k = 10_000_000_000L
    byte b = 128 ; // On tente d'affecter 128 à un byte
    byte b2 = 127 ;
    b2 = b2+1 ;  // Que se passe-t-il ?
    b2

Les différentes bases d'entiers 
----------------------------------

    // Le nombre 26 en décimal 
    int decVal = 26;
    //  Le nombre 26, en hexadécimal
    int hexVal = 0x1a;
    // Le nombre 26, en binaire
    int binVal = 0b11010;


Les flottants
-----------------------------------

  - **float** : Nombres flottants simple précision codés sur 32 bits 
  - **double** : Nombres flottants double précision codés sur 64 bits.

Exemples :

    double a = 1 ; 
    double b = 1.0 ;
    double c = 1.3e3 ;

Attention aux expressions littérales 
-----------------------------------
À tester dans BlueJ...

    double a = 3 ;
    double b = 2 ;
    double c = a/b ;

    double d = 3/2 ; // Que se passe-t-il ?


Les booléens
-----------------------------------

  - **boolean** : ne peut valoir que **true** or **false**

  - "*Use this data type for simple flags that track true/false conditions. This data type represents one bit of information, but its "size" isn't something that's precisely defined.*"

Les caractères
-----------------------------------

  - **char** : caractère unicode codé sur 16 bits

  - Va de *\\u0000* à *\\uFFFF* 

  Exemple dans BlueJ : 

      char a = 0 ;
      a 
      char capitalC = 'C' ;
      C
      (int)capitalC  // Conversion de capitalC en entier (code unicode)

Le pendant Objet des entiers et flottants
-----------------------------------

Il s'agit des classes **Byte**, **Short**, **Integer**, **Long**, **Float**, **Double**

Exemple :

    a = new Integer(3) ;

    Integer (4) // Puis exporter dans le "Object bench"


Exercice 
--------------------

  - Essayer de voir avec BlueJ le nom du champ qui contient la valeur d'un entier dans **Integer**.
  - Essayer de lire cette valeur à l'aide de l'interpréteur
  - Trouver la méthode permettant de réaliser cette opération.

Les tableaux 
--------------------

Les tableaux (**array**) permettent de stocker un nombre **connu** d'objets en mémoire. Ils peuvent être de n'importe quel type.

 Déclaration :

    TYPE[] tableau ; // TYPE peut être n'importe quoi (int, double ou une classe)

Initialisation :

    tableau = new TYPE[N] ; // N est un entier

Accès : 

    tableau[i] ; // i < N

---------------------------- 

Une autre façon d'initialiser un tableau lorsqu'on connaît les éléments : 

    int[] tableauInt= {3,4,5,6} ;

Les tableaux peuvent être modifiés directement :

    tableauInt[0] = 0 ;

----------------------------

Comment connaître la taille d'un tableau ?

  - Rappel : le type d'un tableau d'entier est int[] : la taille n'est pas mentionnée. 

  - **length** : attribut qui stocke la longueur du tableau. Accessible de façon publique. Il s'agit d'une valeur immuable pour un tableau.

 
        System.out.println(tableauInt.length) ; // afficher la taille dans le terminal

------------------------

Il est possible de créer des tableaux sur plusieurs dimensions. Il s'agit alors d'un tableau de tableau.

    int[][] tableau2dim = {{1 , 2 , 3},{4 , 5 , 6}} ;

Exercice :

  - Que vaut alors **tableau2dim.length**?

  - Vérifier avec l'interpréteur BlueJ

  - Que vaut **tableau2dim[1][0]** ?

  - Vérifier avec l'interpréteur BlueJ 

    
La classe **String**
--------------------

La classe **String** permet de manipuler les chaînes de caractère.

    String chaine = Hello World "; // Déclaration et initialisation

Méthodes utiles...
------------------

  - *int* **length**() : donne la longueur de la chaîne

  - *char* **charAt**(*int* i) : retourne la caractère à l'emplacement i 

  - *String* **concat**(*String* str) : retourne une **nouvelle** chaîne correspondant à la concaténation de l'instance en cours et de l'argument str.

------------------

Les chaînes de caractères Java sont immuables :

  - Il n'existe aucun moyen de modifier le contenu d'une chaîne.

  - L'opération *chaine = " Hello World bis " revient à placer une **nouvelle** chaîne de caractères dans la variable chaine.

  - Autre exemple : la méthode **concat** ne modifie pas la chaîne initiale. 

----------------

Avec l'interpréteur BlueJ

    String s1 = " Hello " ;
    s1.at(1) = 'B' ; // Voir ce que cela donne

    s1.concat("World")  // Sans le point-virgule

    String s2 = s1 + " World " ; 
    s2 // sans le point-virgule

    " World ".replace("Wor","Bo")

Les instructions de base en Java
===========================

Déclaration / Affectation
-------------------------

  - Déclaration : fournir le nom du type et de la variable

        String s ;

  - Affectation : avec le signe **=** 

        s = "Hello" ;
        s = new String("Hello") // Création de l'objet String avec new

  - Combinaison déclaration/affectation  :

        String s = "Hello";

Opérations mathématiques 
--------------------------

  - Opérations mathématiques de base  **+ , - , * , /** (avec les priorités mathématiques habituelles)

  
  - Opérations d'incrémentation/décrémentation  **++/-\-**

        i ++ ; // Comparer avec ++ i ;
  
  - Reste de la division entière **\%**

        int i = 11 % 3 ; // i vaut 2
  


Tests et logique booléenne
-------------------------------
  - Test d'égalité **==** ou de non égalité **!=**

        if (i==3) ... 
  
  - Tests comparatifs **<=**, **<**, **>=** et **>**

        if (i>=3) ...

  - Opération de négation **!** 

        Boolean a = !true ; // a = false donc...

  - Le ET et OU logique **&&** / **||**

        Boolean b = true && false ; // false !


Le Flow Control en Java
========================

 
--------------------------------------

Il s'agit ici de définir l'ordre d'exécution des instructions. 

Par défaut, au sein d'une méthode, les instructions sont exécutées **les une après les autres**. 


Le mot-clé **return**
--------------------------

Le mot-clé **return** permet d'interrompre définitivement l'exécution d'une méthode et de retourner la valeur précisée après le mot clé.

    int renvoie1(){
      return 1;
    }

Ce mot clé est obligatoire pour les méthodes qui retournent autre chose que *void*

Les instructions **if/else**
-------------------

    instruct1 ;
    if (x == 4)
    {
      instruct2 ;
    }else
    {
      instruct3 ;
    }
    instruct4 ;

  - Si $x=4$, on aura instruct1 $\longrightarrow$ instruct2$\longrightarrow$ instruct4
  
  - Si $x\neq 4$, on aura instruct1 $\longrightarrow$ instruct3 $\longrightarrow$ instruct4

  - On peut également avoir **if** sans **else** 


Les boucles **for**
-----------------


Les boucles **while**
--------------------


Les boucles **do while**
--------------------

Le mot clé **break**
--------------------


L'instruction **switch**
--------------------

La structure d'une application Java
=====================================

La fonction =ain()
---------------------------











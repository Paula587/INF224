# INF224

Ce projet a été réalisé par Anna van Elst

***

## Build & Run 

Commencer par lancer le serveur : 
Ouvrir un terminal et aller dans le répertoir "cpp" puis taper "make run".

Le serveur se mettra en écoute sur le port 3331.

Puis lancer le client swing : 
Ouvrir un autre terminal et aller dans le répertoir "swing" puis taper "make run".

(Il faut bien lancer le serveur avant le client.)

***

Les étapes réalisées sont celles de 1 à 11 de la partie 1 ainsi que les 4 étapes de la partie 2.

## Partie C++

### Etape 1 : 

Le projet a été réalisé sur l'IDE QtCreator. 

### Etape 2 :

La classe de base s'appelle Multimedia (Multimedia.h pour le fichier header et Multimedia.cpp pour le fichier source. La classe possède deux variables d'instances (nom de l'objet et nom du fichier).
Elle possède une méthode "printVariables" qui permet d'afficher les variables de l'objet.

### Etape 3 :

Les tests effectués se trouver dans les commentaires du fichier main.cpp.

### Etape 4 :

La méthode play de la classe multimedia est une fonction virtuelle pure (ou abstraite) puisqu'elle ne peut pas être implémentée : chaque objet nécessite un utilitaire différent et le comportement devra être précisé dans les sous-classes. Il faut la déclarer avec le mot clé "virtual" au début.
La classe Multimedia est devenue abstraite puisqu'elle contient une méthode virtuelle, il n'est donc plus possible de l'instancier. 

### Etape 5 : Traitement générique (en utilisant le polymorphisme) 

La propriété caractéristique de l'orienté objet qui permet de faire cela est le polymorphisme. En effet, nous n'avons pas eu besoin de préciser le type précis de l'objet pour que le programme appelle la bonne fonction dans la boucle. Cela permet de traiter de manière uniforme les objets de type Photo et ceux de type Video avec les mêmes fonctions play et printVariables (sans connaître leur implémentation). 

En c++, il faut déclarer les méthodes de la classe mère virtual (sinon la liaison est statique et il utilise la définition de la classe mère et non de la classe fille). Les élements du tableau sont des pointeurs. Les pointeurs sont nécessaires car les objets du tableau ne sont pas tous de même taille. 

Java utilise automatiquement des références (équivalent aux pointeurs mais la valeur de l'adresse est cachéé).

### Etape 6 : Films et tableaux

Pour que l'objet Film ait plein contrôle sur ses données et que son tableau de durées ne puisse pas être modifié à son insu, il faut que le contenu du tableau passé en paramètre soit copié. De plus, pour que le contenu du tableau renvoyé par un accesseur ne soit pas modifié, il suffit d'utiliser le mot clé const (signature : const int * getChapters) et d'effectuer une copie du tableau. 
Il faut que la copie en soit pas superficielle. Pour cela, on peut créer un opérateur de copie et surcharger l'opérateur d'affectation.

### Etape 7 : Destruction et copie des objets

Pour éviter toute fuite mémoire, il faut appeler delete dans le desctructeur de Film puisque nous avons créer un nouvel objet avec new (tableau des durées). La copie d'objet peut poser problème si l'on créé un nouvel objet et qu'on oublie de le supprimer. Il ne faut pas oublier d'appeler delete.

### Etape 8 : Créer des groupes

La class group hérite de la classe template list<>.
Il faut des pointeurs d'objets car les objets ne sont pas tous de même taille. 
En Java, des références (similaires à des pointeurs) sont automatiquement utilisées.

### Etape 9 : Gestion automatique de la mémoire

Par la suite, nous utiliserons des smarts pointers (shared_ptr<type>).
Un objet est détruit s'il n'appartient plus à aucun groupe.

### Etape 10 : Gestion cohérente des données

On crée une classe Data capable de gérer les objets Multimedia et les groupes. Cela permet une meilleur cohérence des données.
Cette classe permet de créer tout type d'objet multimedia, un groupe, de rechercher et d'afficher un objet multimedia et un groupe à partir de son nom et de jouer l'objet multimedia. La classe permet également de supprimer un objet multimedia ou un groupe à partir de son nom (l'objet est totalement détruit s'il n'appartient plus à aucune table).


### Etape 11 : Client / serveur

On ajoute la méthode processRequest à notre classe Data qui permet de traiter les requêtes.
On retourne le résultat dans le string "response" donné en paramètres.

***

## Partie Java Swing

### Etape 1: 

La deuxième stratégie pour spécifier le comportement des boutons a été implémenté dans la classe 'Window'. On peut remarquer que si l'on oublie de mettre la zone de texte dans un 'scrollPane' (qui dispose d'un ascenseur), on ne voit plus le texte affiché à partir d'un certain de lignes affichées.  

### Etape 2:  Menus, barre d'outils et actions

La deuxième étape (différente de la première) a été implémenté dans la classe 'ControlWindow'.
J'ai choisi d'utiliser les actions afin de spécifier toutes les caractéristiques des boutons.
On crée donc des sous-classes de 'AbstractAction' imbriquée dans notre 'ControlWindow'.


### Etape 3: Intéraction client/serveur

Nous utilisons le code Client.java pour communiquer avec le serveur C++.
Les insctructions d'utilisations de la fenêtre de contrôle sont spécifiées dans la zone de texte. En plus des boutons, j'ai utilisé une zone de texte supplémentaire (JTextField) permettant d'entrer le nom de l'objet demandé.
 


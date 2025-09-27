<!-- Copyright 2025 Maxime Jan <maxime.jan@edufr.ch> -->
<!-- SPDX-License-Identifier: CC-BY-NC-SA-4.0 -->

```{metadata}
solutions: dynamic
```
# Introduction

## Qu'est-ce qu'une base de données ?

Une base de données peut être définie comme un **ensemble structuré et organisé d’informations**, stockées de manière à pouvoir être consultées, modifiées et exploitées de façon efficace. Contrairement à un simple fichier texte où l'on noterait des données en vrac, une base de données repose sur une logique de structuration qui permet de non seulement retrouver une information rapidement, mais également de limiter la quantité de données enregistrer.

## Tables
Dans le cadre des bases de données relationnelles, qui constituent aujourd’hui le modèle le plus répandu, les informations sont représentées sous forme de tableaux (appelés *tables*). Un tableau représente une *entité* (du monde réel). L'entité possède certaines caractéristiques qui sont représentées par les *colonnes* du tableau, également appelées *attributs*. 
Dans un tableau rempli d'informations concrètes, les lignes sont appelées *instances*, *entrées* ou encore *tuples*. Les lignes sont les occurrences concrètes de l'entité (généralisée).
Dans l'exemple ci-dessous, nous avons le tableau « Match_de_foot » qui représente les matchs de football, et les colonnes représentent certaines caractéristiques importantes d'un match. 

 Table: **Match_de_foot**
| id_match | équipe_1         | équipe_2   | score_équipe_1 | score_equipe_2| date |
|--------------|----------------------|----------------|--------------------|--------------------|------------------------|
| 1            | USA                  | Suisse         | 0                  | 4                  | 2025-06-10             |
| 2            | Mexique              | Suisse         | 2                  | 4                  | 2025-06-07             |
| 3            | Suisse               | Luxembourg     | 3                  | 1                  | 2025-03-25             |
| 4            | Northern Ireland     | Suisse         | 1                  | 1                  | 2025-03-21             |
| 5            | Suisse               | Islande        | 2                  | 0                  | 2025-07-06             |

## Clefs primaires
Dans un tableau provenant d'une base de données relationnelle, nous aurons (presque) toujours une colonne (attribut) qui identifie de manière unique une instance. Dans l'exemple donné, l'attribut d'identification est la colonne id_match. Chaque nouveau match de football aura un nouvel identifiant (unique) et nous pouvons identifier un match particulier grâce à cet identifiant.
La colonne d'identification est appelée **clé primaire**.
Il est important pour nous de faire la différence entre la structure de l'information (nom du tableau et colonnes) et l'information particulière (par exemple, le match entre la Suisse et l'Islande le 6.07.25, etc.).


 ## Relations entre tables - clé primaire, clé étrangère

 Les tables des bases de données relationnelles sont rarement indépendantes. Celles-ci sont *reliées* entre elles par le biais de certaines colonnes contenant les mêmes valeurs. L'exemple de base de données ci-dessous contient une table représentant des films, et une deuxième contenant des critiques sur ces films.

 | id_film | titre                  | réalisateur       | année |
|---------|------------------------|------------------|-------|
| 1       | Inception              | Christopher Nolan | 2010  |
| 2       | Avatar: The Way of Water | James Cameron    | 2022  |


| id_critique | id_film | nom_critique | note | commentaire                          |
|-------------|---------|--------------|------|--------------------------------------|
| 1           | 1       | Sarah        | 9    | Un film captivant et intelligent.     |
| 2           | 2       | Tom          | 7    | Très intéressant mais un peu complexe.|
| 3           | 2       | Lucas        | 8    | Superbes images, mais un peu long.    |
| 4           | 1       | Inès         | 9    | Magnifique expérience visuelle !      |
| 5           | 2       | Ahmed        | 10   | Meilleur film que j’ai vu cette année.|

Ici, les deux tables partagent l'attribut **id_film**. Cela permet à un critique de faire référence à un film. (Vous vous demandez peut-être pourquoi les films ne sont pas référencés par leur titre dans le tableau critic. Les titres peuvent être identiques pour différents films, tandis que l'identifiant id_film est unique pour chaque film. De plus, si le tableau critic contient de nombreux critiques pour le même film, nous devrions répéter le titre de ce film plusieurs fois, ce qui prendrait plus de place que de simplement répéter son identifiant, qui est un simple numéro.)

Comme la colonne id_film du tableau Critique fait référence à la clé primaire du tableau Film, id_film dans Critique est appelé une **clé étrangère**. Cette fois, les informations dans la colonne de clé étrangère peuvent se répéter (nous pouvons avoir plusieurs critiques pour le même film), mais elles doivent faire référence à une entité existante (nous ne pouvons pas avoir de critique pour id_film=3).
Une clé étrangère est une colonne (attribut) d'une table qui fait référence à la colonne de clé primaire d'une autre table et qui nous permet d'établir des relations entre les tables.

Grâce à la relation utilisant la clé primaire et la clé étrangère entre les tables Critique et Film, nous pouvons déduire que, Inception a reçu 2 critiques, alors que Avatar en a reçu 3.



## Schémas relationnels

Lorsque la taille des bases de données relationnelles devient importante, il peut être difficile de se repérer entre toutes ses tables. Pour cette raison, on dessine un schéma pour expliquer l'organisation des tables et la manière dont elles sont reliées entre elles. Pour l'exemple précédent de la base de données des films, le schéma relationnel est le suivant : 

```{image} images/movie_schema.png
:width: 50%
:alt: Schéma relationnel de la base de données des films
:align: center
```

Ce schéma nous permet d'observer les éléments suivants :

- La base de données contient 2 tables. Une table représente l'entité généralisée (concept) film avec ses attributs (colonnes) et l'autre table représente un critique avec ses attributs. 
- Ainsi, un rectangle correspond à une table. Le nom en haut du rectangle est le nom de la table. Les mots listés sont alors les colonnes (attributs).
- Les attributs soulignés sont des **clefs primaires**. Une clef primaire est un attribut dont la valeur sera unique pour chaque entité.
- Le schéma relationnel représente uniquement la structure d'une base de données et non les instances concrètes des données (par exemple, Avatar : La Voie de l'eau).
- Nous voyons la relation entre deux tables grâce à la **flèche** qui part de la clé étrangère (de la table critique) et pointe vers la clé primaire (de la table Film). Cela permet de comprendre que ces deux colonnes reliées contiendront les mêmes valeurs permettant de faire le lien entre un film et une critique.
- Une table peut avoir plusieurs clés étrangères, comme nous le verrons dans d'autres exemples.

```{image} images/movie_schema_fk_pk.png
:width: 70%
:alt: Schéma relationnel de la base de données des films
:align: center
```



## Exercices

### Exercice {num1}`exercice`
La base de données partielle ci-dessous contient des données relatives à l'organisation de Paléo 2025. En lisant manuellement ces données, répondez à ces questions.

```{role} input(quiz-input)
:right: width: 18rem; clear: right;
:check: split lowercase
```

```{quiz}
1. {input}`suisse`
De quel pays vient *Me & George* ?

2. {input}`22:45`
A quelle heure est programmé *David Guetta* ?

3. {input}`3`
Combien de concerts sont programmés sur la *Grande Scène* ?

4. {input}`Trinix`
Quel artiste se produit-il sur la scène *Les Arches* ?
```


| id_artiste | nom                       | pays    |
|------------|---------------------------|---------|
| 1          | Queens of the Stone Age   | USA     |
| 2          | Zaho de Sagazan           | France  |
| 3          | David Guetta              | France  |
| 4          | Trinix                    | France  |
| 5          | Me & George               | Suisse  |

| id_scene | nom           | capacite_approx |
|----------|---------------|-----------------|
| 1        | Grande Scène  | 35000           |
| 2        | Belleville    | 10000           |
| 3        | Les Arches    | 8000            |


| id_prog | artiste | scene | heure_debut |
|---------|------------|------------|-------------|
| 1       | 2          | 2          | 21:00       |
| 2       | 1          | 1          | 23:45       |
| 3       | 5          | 1          | 20:40       |
| 4       | 4          | 3          | 23:45       |
| 5       | 3          | 1          | 22:45       |


### Exercice {num1}`exercice`
Sur un bout de papier, ou de manière numérique, établissez le schéma relationnel de la base de données de Paléo de l'exercice précédent.

````{solution}
```{image} images/ex2.png
:width: 60%
:alt: Solution exercice 2
:align: center


```
````

### Exercice {num1}`exercice`
Dessinez le schéma relationnel de la base de données d'une version "light" d'Instagram, telle qu’elle pouvait l'être dans les premières années d'existence de l'application.
- Instagram possède des utilisateurs qui, en s’inscrivant, doivent donner un pseudo, une adresse e-mail et un mot de passe.
- Les utilisateurs peuvent poster des photos et des vidéos. Les postes de cette version d’Instagram ne peuvent contenir qu’une seule image ou une seule vidéo, ainsi qu’une description, et une localisation. Il faut noter qu’il est impossible de stocker une image ou une vidéo dans un tableau. A la place on stocke le chemin d’accès (par exemple C:/Users/…/photo4193.jpeg).
- Chaque poste peut être commenté par d’autres utilisateurs.


````{solution}
Pour cet exercice, des solutions alternatives proches de celle ci-dessous sont possibles. Notamment, la clef primaire de la table `Utilisateur` pourrait être l'email ou un nouveau champ `id_utilisateur`. En revanche, la colonne `mot_de_passe` ne peut pas être clef primaire car plusieurs utilisateurs pourraient avoir le même mot de passe.

En ce qui concerne la table `Post`, il est impératif de créer un `id_post` pour faire office de clef primaire, car aucune des autres colonnes n'est garantie comme étant unique.

Finalement, la table des commentaires doit bien contenir 2 clefs étrangères (référençant le post sur lequel le commentaire est fait, et quel utilisateur l'a écrit) en plus du texte en lui-même. Cette table ne doit pas forcément contenir de clef primaire, mais on peut y ajouter un `id_commentaire` si besoin.
```{image} images/ex3.png
:width: 60%
:alt: Solution exercice 2
:align: center
```
````
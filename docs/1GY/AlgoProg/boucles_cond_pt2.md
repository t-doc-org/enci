```{metadata}
solutions: dynamic
```
# Boucles conditionnelles Pt.2

## Répéter quelque chose une fois sur deux (une fois sur trois, une fois sur n) en boucle

```{exec} python
:linenos:
compteur = 1
while compteur <= 10 :
    print(compteur)
    compteur =compteur + 1
```
Nous avons l'exemple du chapitre précédent avec la séquence affichée des nombres de 1 à 10. Comment ajouter un petit message après chaque nombre pair comme ci-dessous?

```{code-block} text
1
2 est pair
3
4 est pair
5
6 est pair
7
8 est pair
9
10 est pair
```
Pour cela, nous utiliserons l'opérateur modulo `%`.
Nous l'avons brièvement vu dans le chapitre « Variables ».

Il nous donne le reste de la division de deux nombres entiers.

Pour vérifier si un nombre est pair, nous devons vérifier si le reste de sa division par 2 est égal à 0.

Avec un nombre simple, cela donne ceci (vous pouvez modifier la valeur de « nombre » pour effectuer plusieurs tests) :
```{exec} python
:linenos:
nombre = 5
if nombre % 2 == 0:
    print(nombre, "est pair")
else:
    print(nombre, "est impair")
```
Dans l'exemple précédent, avec l'affichage du message « est pair », nous utiliserons le modulo comme suit :

```{exec} python
:linenos:
compteur = 1
while compteur <= 10 :
    if compteur %2==0:
        print(compteur, "est pair")
    else:
        print(compteur)
    compteur =compteur + 1
```

Si nous voulons répéter une action toutes les trois fois, par exemple, nous pouvons procéder comme suit.
```{exec} python
:linenos:
compteur = 1
while compteur <= 10 :
    if compteur %3==0:
        print(compteur, "est divisible a 3")
    else:
        print(compteur)
    compteur =compteur + 1
```

Pour les prochains exercices, nous utiliserons également le fait que si nous multiplions une valeur de chaîne par un nombre entier, cela répète la valeur de la chaîne autant de fois que la valeur entière.
```{exec} python
:linenos:
text = "XO"
n = 4
print(text*n)
```

Les prochains exercices utiliseront le fait que nous pouvons multiplier des valeurs de chaîne, ainsi que l'idée de répéter quelque chose toutes les n fois.
Vous pouvez prendre l'exemple suivant comme point de départ.

```{exec} python
:linenos:
compteur = 1
value = 5
symbol = "+"
while compteur <= 10 :
    if compteur %2==0:
        print(symbol * value)
    else:
        print(symbol * value * 2)
    compteur =compteur + 1
```

### Exercice {num1}`exercice`
Il existe différents symboles permettant de réaliser ce qu'on appelle l'« art ASCII ». Plus tard dans l'année, nous aborderons la définition de l'ASCII et la manière dont les symboles sont représentés sous forme de codes sur un ordinateur.

Voici une liste de différents symboles graphiques permettant de créer des motifs intéressants.
■	Black Square	&#9632;	&#x25A0;
□	White Square	&#9633;	&#x25A1;
▢	White Square With Rounded Corners	&#9634;	&#x25A2;
▣	White Square Containing Black Small Square	&#9635;	&#x25A3;
▤	Square With Horizontal Fill	&#9636;	&#x25A4;
▥	Square With Vertical Fill	&#9637;	&#x25A5;
▦	Square With Orthogonal Crosshatch Fill	&#9638;	&#x25A6;
▧	Square With Upper Left To Lower Right Fill	&#9639;	&#x25A7;
▨	Square With Upper Right To Lower Left Fill	&#9640;	&#x25A8;
▩	Square With Diagonal Crosshatch Fill	&#9641;	&#x25A9;
▪	Black Small Square	&#9642;	&#x25AA;
▫	White Small Square	&#9643;	&#x25AB;
◧	Square With Left Half Black	&#9703;	&#x25E7;
◨	Square With Right Half Black	&#9704;	&#x25E8;
◩	Square With Upper Left Diagonal Half Black	&#9705;	&#x25E9;
◪	Square With Lower Right Diagonal Half Black	&#9706;	&#x25EA;
◫	White Square With Vertical Bisecting Line	&#9707;	&#x25EB;
◰	White Square With Upper Left Quadrant	&#9712;	&#x25F0;
◱	White Square With Lower Left Quadrant	&#9713;	&#x25F1;
◲	White Square With Lower Right Quadrant	&#9714;	&#x25F2;

Les motifs ci-dessous utilisent certains de ces symboles.

Votre tâche consiste maintenant à observer chaque motif et à concevoir un programme comportant une boucle « while » qui le reproduise. Votre programme doit utiliser autant de variables et d'instructions conditionnelles que nécessaire, afin d'être clair, efficace et facile à lire.

Observez attentivement les motifs : vous devrez parfois afficher un certain nombre de symboles, parfois faire attention au nombre d'espaces.



```{code-block} text
1
□□□□□
□□□□□
□□□□□
□□□□□
□□□□□
2
□
□□
□□□
□□□□
□□□□□
3
□□□□□□□
□□□□□□
□□□□□
□□□□
□□□
□□
□
4
□□□□□□□
 □□□□□□
  □□□□□
   □□□□
    □□□
     □□
      □
5
+++++
-----
+++++
-----
+++++
6
▤▤▤▤▤
▣▣▣▣▣
▤▤▤▤▤
▣▣▣▣▣
▤▤▤▤▤
7
/////////
\\\\\\\\\
|||||||||
/////////
\\\\\\\\\
|||||||||
/////////
\\\\\\\\\
|||||||||
```
```{exec} python
:editor: 09821gya00d-f7e0-7b9e-b226-626e25d2dfb8
#Ecrivez votre code ici

```

<!--  
compteur = 1
const = 5
while compteur <= const:

    #print("■"*const)
    print("□"*const)
    compteur += 1

compteur = 1
const = 5
while compteur <= const:

    #print("■"*const)
    print("□"*const)
    compteur += 1

compteur = 7
while compteur >= 1:

    #print("■"*const)
    print("□"*compteur)
    compteur -= 1

compteur = 7
limit = compteur
while compteur >= 1:

    #print("■"*const)
    print(" "*(limit-compteur)+"□"*compteur)
    compteur -= 1

compteur = 1
const = 5
while compteur <= const:
    if compteur %2==1:
        print("▤"*const)
    else:
        print("▣"*const)
    compteur += 1

compteur = 1
const = 9
while compteur <= const:
    if compteur %3==1:
        print("/"*const)
    elif compteur % 3 == 2:
        print("\\"*const)
    else:
        print("|"*const)
    compteur += 1

compteur = 1
while compteur <= 10 :
    if compteur %3==0:
        print(compteur, "est divisible a 3")
    else:
        print(compteur)
    compteur =compteur + 1

-->

### Exercice {num1}`exercice`
Partie 1 : Remplacement des multiples de 3 par "Fizz"

Vous allez écrire un programme qui affiche les nombres de 1 à 13, en remplaçant les nombres divisibles par 3 par le mot "Fizz".

Utilisez une boucle `while` pour parcourir les nombres de 1 à 13.
Pour chaque nombre :

-   Si le nombre est divisible par 3, affichez "Fizz".
-   Sinon, affichez le nombre lui-même.

Exemple de sortie attendue :
```{code-block} text
1
2
Fizz
4
5
Fizz
7
8
Fizz
10
11
Fizz
13
```

Partie 2 : Remplacement des multiples de 3 et 5
Vous allez maintenant écrire un programme qui affiche les nombres de 1 à 14, en remplaçant :

les nombres divisibles par 3 par "Fizz",
les nombres divisibles par 5 par "Buzz".

Consignes :

Utilisez une boucle while pour parcourir les nombres de 1 à 14.
Pour chaque nombre :

Si le nombre est divisible par 3, affichez "Fizz".
Si le nombre est divisible par 5, affichez "Buzz".
Si le nombre n’est divisible ni par 3 ni par 5, affichez le nombre lui-même.



Exemple de sortie attendue :
```{code-block} text
1
2
Fizz
4
Buzz
Fizz
7
8
Fizz
Buzz
11
Fizz
13
14
```

Partie 3:
Affichez la séquence de nombres de 1 à 31, en appliquant des règles de remplacement spécifiques.
Pour chaque nombre de 1 à 31 :

-   Si le nombre est divisible par 3, affichez "Fizz" à la place du nombre.
-   Si le nombre est divisible par 5, affichez "Buzz" à la place du nombre.
-   Si le nombre est divisible à la fois par 3 et 5, affichez "FizzBuzz".
-   Sinon, affichez simplement le nombre.

Vous devez utiliser une boucle `while` et des instructions conditionnelles (if, elif, else).
Affichez chaque résultat sur une ligne distincte.

Exemple de sortie attendue:
```{code-block} text
1
2
Fizz
4
Buzz
Fizz
7
8
Fizz
Buzz
11
Fizz
13
14
FizzBuzz
...
FizzBuzz
31
```

```{exec} python
:editor: 0198a00d-f7e0-7b9e-b226-626e25d2dfb8
#Ecrivez votre code ici

```

````{solution}

```{exec} python
:linenos:
counter = 1
while counter <=100:
    if counter % 15 == 0:
        print("FizzBuzz")
    elif counter % 3 == 0:
        print("Fizz")
    elif counter % 5 == 0:
        print("Buzz")
    else:
        print(counter)
    counter = counter + 1

```
````


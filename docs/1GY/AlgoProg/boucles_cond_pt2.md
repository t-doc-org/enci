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

Les consignes détaillés sont à venir, pour l'instant, considérez ce qui suit comme des exercices. À chaque fois, votre objectif est de produire l'affichage donné en utilisant une boucle while, certaines conditions à l'intérieur et certaines variables qui contiennent le nombre de certains aspects de votre « dessin ».

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
▤▤▤▤▤
▣▣▣▣▣
▤▤▤▤▤
▣▣▣▣▣
▤▤▤▤▤
6
+++++
-----
+++++
-----
+++++
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


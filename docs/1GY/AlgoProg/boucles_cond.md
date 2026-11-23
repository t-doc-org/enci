# Boucles conditionnelles

## Qu'est-ce qu'une boucle conditionnelle ?

Dans un programme, certaines instructions doivent s'exécuter plusieurs fois. Imaginez un programme dans lequel l'utilisateur doit entrer son mot de passe pour se connecter. Ici, l'instruction `print("Mot de pas incorrect")` doit être potentiellement exécutée plusieurs fois **tant que** l'utilisateur entre un mauvais mot de passe. C'est une boucle conditionnelle qui nous permettra de répéter des instructions de cette manière. Grâce à celle-ci, un bloc d'instructions peut être répété *en boucle* tant qu'une condition est respectée. 

En pseudocode, l'exemple du programme de connexion avec une boucle conditionnelle pourrait donc s'écrire de la manière suivante :
```{code-block} text
:linenos:
Demander le mot de passe à l'utilisateur et le stocker dans la variable mdp
Tant que mdp est différent de "Fr1B0urg"
    Afficher "Mot de passe incorrect"
    Redemander le mot de passe et le stocker dans mdp
Afficher "Connexion réussie"
```

Dans ce pseudocode, quand l'exécution arrive à la ligne 2, la condition est évaluée pour déterminer si l'on entre dans la boucle ou non. Dans le cas où le résultat de la condition est vrai (c'est-à-dire que le mot de passe est incorrect), on entre dans la boucle. Cela signifie que le bloc d'instruction indenté en dessous est exécuté. Au terme de l'exécution de ce bloc, on remonte à la ligne 2 pour réévaluer la condition. Si elle est vraie, on entre à nouveau dans la boucle et le bloc d'instruction indenté est réexécuté. Lorsqu'en revanche la condition de la ligne 2 est fausse, le bloc indenté est ignoré et la ligne 5 est exécutée.

## La boucle while

En Python, une boucle conditionnelle s'écrit avec le mot-clef `while` (littéralement *tant que*). Ce mot-clef est suivi d'une condition qui détermine si l'on entre dans la boucle (quand la condition est `True`) ou si on en sort (quand la condition est `False`). Quand on entre dans la boucle, le bloc d'instructions indenté sous le `while` est exécuté. Au terme de cette exécution, on *remonte* à la ligne du `while` et la condition est réévaluée pour déterminer si l'on entre à nouveau dans la boucle ou non.

L'exemple du programme de connexion décrit précédemment en pseudocode peut alors s'écrire de la manière suivante.


```{exec} python
:linenos:
mdp = input("Entrez le mot de passe")
while mdp != "Fr1B0urg" :
    print("Mot de passe incorrect")
    mdp = input("Entrez à nouveau le mot de passe")
print("Mot de passe correct")
```

Le boucle `while` peut également être utilisée pour répéter un bloc d'instructions un nombre déterminé de fois, comme dans le programme ci-dessous qui permet de compter jusqu'à 10.

```{exec} python
:linenos:
compteur = 1
while compteur <= 10 :
    print(compteur)
    compteur += 1
```

## Exercices

### Exercice {num1}`exercice`
Sans les exécuter, lisez attentivement les programmes ci-dessous. Leur seule différence est le `if` ou `while` de la ligne 3. Quel sera l'affichage de chacun de ses programmes ? Quelle est la différence entre un `if` et un `while` ?

```{exec} python
:when:
:caption: Programme 1
:linenos:
n = 5
if n < 10:
    n += 1
    print(n)
```

```{exec} python
:when:
:caption: Programme 2
:linenos:
n = 5
while n < 10:
    n += 1
    print(n)
```


````{solution} 
Comme le premier programme utilise un `if`, le bloc d'instruction indenté en dessous n'est exécuté qu'une seule fois. Ce programme affichera simplement `6`. Dans le 2ème programme, l'exécution revient à la ligne du while après avoir exécuté une première fois le bloc indenté en dessous et réévalue l'expression conditionnelle. Le bloc est donc exécuté en boucle tant que `n` est plus petit que `10`. Ainsi, ce programme affiche 6, puis 7, puis 8, puis 9, puis 10. Si cela n'est pas clair pour vous, suivez le programme en complétant un tableau d'état pour vous convaincre de cet affichage.
````

### Exercice {num1}`exercice`
Etablissez le tableau d'état du programme suivant.

```{exec} python
:linenos:
x = 0
y = 20
while x < y:
    y -= x * 2
    x = x + 2
x += 1
```

````{solution}
Tableau d'état :

|ligne| x  | y  |
|:--| :--| :--|
|1| 0  |    |
|2| 0  | 20 |
|4| 0  | 20 |
|5| 2  | 20 |
|4| 2  | 16 |
|5| 4  | 16 |
|4| 4  | 8  |
|5| 6  | 8  |
|4| 6  | -4 |
|5| 8  | -4 |
|6| 9  | -4 |

````

### Exercice {num1}`exercice`
Etablissez le tableau d'état du programme suivant.
```{exec} python
:linenos:
n = 30
x = 0
while n != 20:
    n -= 2
    if n < 26:
        x += 2
    else:
        x -= 1
    x = x * 2
```


````{solution}
|ligne| n  | x  |
|:--| :--| :--|
|1| 30  |    |
|2| 30  | 0 |
|4| 28  | 0 |
|8| 28  | -1 |
|9| 28  | -2 |
|4| 26  | -2 |
|8| 26  | -3  |
|9| 26  | -6  |
|4| 24  | -6 |
|6| 24  | -4 |
|9| 24  | -8 |
|4| 22  | -8 |
|6| 22  | -6 |
|9| 22  | -12 |
|4| 20  | -12 |
|6| 20  | -10 |
|9| 20  | -20 |
````

### Exercice {num1}`exercice`
1.  Écrivez un programme utilisant seulement 2 instructions `print()` affichant un compte à rebours de 100 jusqu'à 0. L'exécution du programme ressemblera à ceci :
```{code-block} text
100
99
98
...
2
1
0
BOOM
```

```{exec} python
:editor: 01989fce-6486-7c83-8083-caa7d192000d
#Ecrivez votre code ici
```

2.  Complétez le programme précédent avec un `if ... else ...` dans le `while` de manière qu'à chaque fois qu'un nombre inférieur à 10 est affiché, le texte `"FUYEZ !"` le suive :
```{code-block} text
100
99
98
...
2 FUYEZ
1 FUYEZ
0 FUYEZ
BOOM
```

````{solution}
1. 
```{exec} python
:linenos:
compte_a_rebours = 1000
while compte_a_rebours >= 0:
    print(compte_a_rebours)
    compte_a_rebours -= 1
print("BOOM")
```

2. 
```{exec} python
:linenos:
compte_a_rebours = 1000
while compte_a_rebours >= 0:
    if compte_a_rebours < 10:
        print(compte_a_rebours, "FUYEZ !")
    else:
        print(compte_a_rebours)
    compte_a_rebours -= 1
print("BOOM")
```
````

### Exercice {num1}`exercice`
Écrivez un programme dans lequel l'utilisateur peut choisir un nombre pour lequel il souhaite voir apparaître sa table de multiplication. Un message d'au revoir sera également affiché à la fin. Votre programme ne doit utiliser que **une seule** instruction `print()`. Un exemple d'exécution pourrait être le suivant :

```{code-block} text
Quelle table de multiplication voulez-vous voir ? <--- [4]
1x4 = 4
2x4 = 8
3x4 = 12
...
10x4 = 40
```


```{exec} python
:editor: 01989fd5-85e7-7b82-998d-9ba09a6bd320
#Ecrivez votre code ici

```

````{solution}
Il y a deux manières différentes pour résoudre ce problème. Toutefois, à moins d'être très à l'aise, je vous conseille de rester sur la première solution, car la 2ème est moins intuitive.


```{exec} python
:caption: Solution 1
:linenos:
n = int(input("Quelle table de multiplication voulez-vous voir ?"))
multiplicateur = 1
while multiplicateur <= 10:
    print(multiplicateur, "*", n, "=", multiplicateur * n)
    multiplicateur += 1
```

```{exec} python
:caption: Solution 2
:linenos:
n = int(input("Quelle table de multiplication voulez-vous voir ?"))
nombre_de_base = n
compteur = 0
while compteur < 10:
    compteur += 1
    print(compteur, "*", nombre_de_base, "=", n)
    n += nombre_de_base
```
````


### Exercice {num1}`exercice`
1.  Écrivez un programme dans lequel l'utilisateur peut consécutivement entrer les notes qu'il a faites dans une branche. À la fin, le programme affichera le nombre de notes insuffisantes qui ont été entrées. Les notes invalides seront simplement ignorées. Pour terminer le programme, l'utilisateur entrera la note `99`. Un exemple d'exécution peut être le suivant.

```{code-block} text
Entrez une note : 4.5
Entrez une note : 3.4
Entrez une note : 6
Entrez une note : 3.9
Entrez une note : 5.1
Entrez une note : 99
Vous avez fait 2 notes insuffisantes
```
```{exec} python
:editor: 0198a00c-91d5-75cd-8043-0b2021e0ba04
#Ecrivez votre code ici

```

````{solution}
```{exec} python
:linenos:
nb_notes_insuf = 0
note = 0
while note != 99:
    note = float(input("Entrez une note"))
    if note >= 1 and note < 4:
        nb_notes_insuf += 1
print("Vous avez fait", nb_notes_insuf, "notes insuffisantes")
```
ou
```{exec} python
:linenos:
note = float(input("une note: "))
nombre_note = 0
while note !=99:
    if note <4 and note >=1:
        nombre_note = nombre_note + 1
    note = float(input("une note: "))
print("Les notes moin que 4 sont:",nombre_note)
```
````
2.  **Élaboration des exercices précédents:** À présent, nous souhaitons toujours compter les notes valides mais insuffisantes, mais nous aimerions également calculer et afficher leur moyenne à la fin. De plus, si une note valide est saisie et qu'elle est suffisante, nous affichons un petit message du type : « Bravo pour ta note suffisante ». Nous souhaitons également afficher un message adapté pour les saisies qui ne correspondent pas à des notes valides, par exemple : « Note non valide ». Et bien sûr, le programme cesse de demander d'autres notes lorsque l'utilisateur saisit 99. 
À la fin, le programme affiche le nombre de notes insuffisantes (et valides) ainsi que leur moyenne. 
**Ajoutez une condition à la fin** pour n'afficher la moyenne que si le nombre de notes insuffisantes (valides) est supérieur à 0, afin d'éviter une erreur de division par 0.

```{exec} python
:editor: 0378a00c-91d5-75cd-8043-5z2051e0ba04
#Ecrivez votre code ici

```
````{solution}
```{exec} python
:linenos:
note = float(input("Entrez une note différente de 99: "))
nb_notes_insuf = 0
somme_insuf = 0
while note !=99:
    if note >=1 and note < 4:
        nb_notes_insuf = nb_notes_insuf + 1
        somme_insuf = somme_insuf + note
    elif note <=6 and note >= 4:
        print("Bravo, mais ca compte pas.")
    else:
        print("Note pas valable.")
    note = float(input("entrez une note differente que 99"))
print("Nombre de notes insuffisantes",nb_notes_insuf)
#pour éviter la division par 0
if nb_notes_insuf>0:
    print("Moyenne de notes insuffisantes", somme_insuf/nb_notes_insuf)
```
````


### Exercice {num1}`exercice`
Ecrivez un programme correspondant à une mini machine à calculer. Dans celle-ci, l'utilisateur pourra choisir de faire une addition, soustraction ou multiplication entre 2 nombres. Le programme demandera alors à l'utilisateur quel type d'opération il souhaite faire, avant de lui demander les 2 nombres à utiliser. Le programme demandera à l'utilisateur des opérations à faire en boucle, jusqu'à ce que celui-ci écrive "STOP". Un exemple d'utilisation est donné ci-dessous.

```{code-block} text
Bienvenue dans la mini calculatrice !
Quelle opération souhaitez-vous effectuer ?addition
Quel est le premier nombre ?4
Quel est le deuxième nombre ?7
Le résultat de 4 + 7 est 11

Quelle opération souhaitez-vous effectuer ?multiplication
Quel est le premier nombre ?9
Quel est le deuxième nombre ?11
Le résultat de 9 * 11 est 99

Quelle opération souhaitez-vous effectuer ?STOP
Au revoir !
```

```{exec} python
:editor: 0198a00d-f7e0-7b9e-a166-626e25d2dfb8
#Ecrivez votre code ici

```

````{solution}

```{exec} python
:linenos:
print("Bienvenue dans la mini calculatrice !")
operation = ""
while operation != "STOP":
    operation = input("Quelle opération souhaitez-vous effectuer ?")
    if operation == "STOP":
        print("Au revoir !")
    else:
        nombre1 = float(input("Quel est le premier nombre ?"))
        nombre2 = float(input("Quel est le deuxième nombre ?"))
        if operation == "addition":
            resultat = nombre1 + nombre2
            print("Le résultat de", nombre1, "+", nombre2, "est", resultat)
        elif operation == "soustraction":
            resultat = nombre1 - nombre2
            print("Le résultat de", nombre1, "-", nombre2, "est", resultat)
        elif operation == "multiplication":
            resultat = nombre1 * nombre2
            print("Le résultat de", nombre1, "*", nombre2, "est", resultat)
        else:
            print("Opération non reconnue")

```
````





```{metadata}
solutions: dynamic
```
# Représentation des caractères

En informatique, les caractères (lettres, signes de ponctuation, ...) sont représentés grâce à un tableau de correspondance. Au fil des années, plusieurs de ces tableaux ont été créés pour représenter différents jeux de caractères. Certains de ces tableaux sont aujourd'hui tombés dans l'oubli, alors que d'autres sont devenus des standards utilisés par la plupart de nos systèmes modernes.

## La table ASCII

La table ASCII (American Standard Code for Information Interchange) est l'un des premiers standards universels de codage des caractères. Créée en 1963 et standardisée en 1967, elle utilise 7 bits pour représenter 128 (2<sup>7</sup>) caractères différents. Ces caractères incluent :

- Les lettres majuscules et minuscules de l'alphabet latin (A-Z, a-z).
- Les chiffres (0-9).
- Les signes de ponctuation et caractères spéciaux (par exemple, `!`, `@`, `#`).
- Des caractères de contrôle  (comme `ACK`, `SYN`, ou `LF` pour indiquer un saut de ligne).

ASCII a servi de base à de nombreux autres systèmes de codage, mais il présente des limitations importantes, notamment son incapacité à représenter des caractères accentués, des alphabets non latins, ou d'autres symboles'. Ce tableau de correspondance est donné ci-dessous

| ASCII | BITS     | ASCII | BITS     | ASCII | BITS     | ASCII | BITS     |
| :---- | :------- | :---- | :------- | :---- | :------- | :---- | :------- |
| NUL   | 0000000  | SP    | 0100000  | @     | 1000000  | `     | 1100000  |
| SOH   | 0000001  | !     | 0100001  | A     | 1000001  | a     | 1100001  |
| STX   | 0000010  | "     | 0100010  | B     | 1000010  | b     | 1100010  |
| ETX   | 0000011  | #     | 0100011  | C     | 1000011  | c     | 1100011  |
| EOT   | 0000100  | $     | 0100100  | D     | 1000100  | d     | 1100100  |
| ENQ   | 0000101  | %     | 0100101  | E     | 1000101  | e     | 1100101  |
| ACK   | 0000110  | &     | 0100110  | F     | 1000110  | f     | 1100110  |
| BEL   | 0000111  | '     | 0100111  | G     | 1000111  | g     | 1100111  |
| BS    | 0001000  | (     | 0101000  | H     | 1001000  | h     | 1101000  |
| HT    | 0001001  | )     | 0101001  | I     | 1001001  | i     | 1101001  |
| LF    | 0001010  | *     | 0101010  | J     | 1001010  | j     | 1101010  |
| VT    | 0001011  | +     | 0101011  | K     | 1001011  | k     | 1101011  |
| FF    | 0001100  | ,     | 0101100  | L     | 1001100  | l     | 1101100  |
| CR    | 0001101  | -     | 0101101  | M     | 1001101  | m     | 1101101  |
| SO    | 0001110  | .     | 0101110  | N     | 1001110  | n     | 1101110  |
| SI    | 0001111  | /     | 0101111  | O     | 1001111  | o     | 1101111  |
| DLE   | 0010000  | 0     | 0110000  | P     | 1010000  | p     | 1110000  |
| DC1   | 0010001  | 1     | 0110001  | Q     | 1010001  | q     | 1110001  |
| DC2   | 0010010  | 2     | 0110010  | R     | 1010010  | r     | 1110010  |
| DC3   | 0010011  | 3     | 0110011  | S     | 1010011  | s     | 1110011  |
| DC4   | 0010100  | 4     | 0110100  | T     | 1010100  | t     | 1110100  |
| NCK   | 0010101  | 5     | 0110101  | U     | 1010101  | u     | 1110101  |
| SYN   | 0010110  | 6     | 0110110  | V     | 1010110  | v     | 1110110  |
| ETB   | 0010111  | 7     | 0110111  | W     | 1010111  | w     | 1110111  |
| CAN   | 0011000  | 8     | 0111000  | X     | 1011000  | x     | 1111000  |
| EM    | 0011001  | 9     | 0111001  | Y     | 1011001  | y     | 1111001  |
| SUB   | 0011010  | :     | 0111010  | Z     | 1011010  | z     | 1111010  |
| ESC   | 0011011  | ;     | 0111011  | [     | 1011011  | {     | 1111011  |
| FS    | 0011100  | <     | 0111100  | \     | 1011100  | \|     | 1111100  |
| GS    | 0011101  | =     | 0111101  | ]     | 1011101  | }     | 1111101  |
| RS    | 0011110  | >     | 0111110  | ^     | 1011110  | ~     | 1111110  |
| US    | 0011111  | ?     | 0111111  | _     | 1011111  | DEL   | 1111111  |

### Unicode

Bien que la table ASCII était très populaire dans les débuts de l'informatique, celle-ci est devenue obsolète lorsque les ordinateurs sont devenus accessibles au grand public. En effet, avec ASCII, il est impossible de représenter des caractères accentués (é, è, ê, à, â, ü, ù, ö, ô, etc...), ou des caractères d'autres alphabets (cyrillique, grec, hébreux, japonais, etc...).

Une initiative, nommée Unicode, a donc été mise en place dès 1991 afin de recenser tous les caractères que l'on souhaiterait représenter. Unicode définit un identifiant unique pour tous les systèmes d'écriture que l'on pourrait souhaiter représenter. Aujourd'hui, environ 150'000 caractères possèdent un identifiant Unicode, y compris des emojis, des lettres d'alphabets antiques, des pièces d'échec, et bien d'autres caractères exotiques. Ces identifiants commencent toujours par "U+" et sont suivis d'un nombre hexadécimal. En voici quelques exemples :

| Caractère | Unicode |
|-----------|---------|
| Œ         | U+0152  |
| Ů         | U+016E  |
| ©         | U+00A9  |
| ¶         | U+00B6  |

```{admonition} Note sur Unicode 
:class: note
Attention ! Unicode n'est pas un système permettant de représenter les caractères sous forme informatiques avec des bits. Il s'agit d'un standard de codage permettant de recenser et d'identifier tous les caractères existants.
```

### UTF-8
Le standard de représentation des caractères est aujourd'hui UTF-8. Il s'agit d'un système de codage de caractères qui permet de représenter tous les caractères définis dans Unicode tout en étant compatible avec les systèmes plus anciens, tels que ceux utilisant la table ASCII.

 - Compatibilité : Les premiers 128 caractères (U+0000 à U+007F), qui incluent tous les caractères de base de l'ASCII, sont représentés de la même manière en UTF-8 et en ASCII (c'est-à-dire avec un octet).
 - Longueur variable : Les caractères Unicode au-delà de U+007F sont encodés avec deux, trois ou quatre octets. Par exemple, un caractère comme "é" (U+00E9) sera codé en deux octets, tandis qu'un caractère comme "😊" (U+1F60A) sera codé en quatre octets. L'idée est de représenter les caractères les plus fréquemment utilisés avec moins de bits de manière à rendre les fichiers les moins lourds possible.
 
 La table UTF-8 est trop grande pour être affichée au complet ici, mais vous trouvez ci-dessous quelques exemples de caractères avec leur Unicode et leur représentation binaire UTF-8.

 | Caractère | Unicode    | UTF-8 (binaire)                              |
|-----------|------------|---------------------------------------------|
| A         | U+0041     | 01000001                                    |
| ñ         | U+00F1     | 11000011 10110001                           |
| €         | U+20AC     | 11100010 10000010 10101100                  |
| 😀        | U+1F600    | 11110000 10011111 10011000 10000000         |
| 中        | U+4E2D     | 11100100 10111000 10101101                  |
| أ         | U+0623     | 11011000 10100011                           |
| ♫         | U+266B     | 11100010 10011001 10101011                  |
| 🌍        | U+1F30D    | 11110000 10011111 10001100 10001101         |

Pour la lecture d'un texte encodé avec ASCII, il suffisait de séparer les bits 7 par 7 avant de les convertir. Avec UTF-8 c'est un peu plus compliqué. En regardant les exemples ci-dessus, vous noterez que les caractères encodés avec un octet commencent par un 0, que les caractères encodés avec deux octets commencent par deux 1, avec trois octets avec trois 1, et quatre octets avec quatre 1. Il faut donc lire ces premiers bits pour faire la séparation avant de convertir le code binaire.

## Exercices

### Exercice 1
A l'aide de la table ASCII qui se trouve sur cette page, déchiffrez le message suivant :
100011111100101100001110001111001010100000100100011011111110000111000011001011110010
````{admonition} Solution
:class: note dropdown
Le message est : "Grace Hopper"

Grace Hopper était une informaticienne qui a joué un rôle extrêmement important dans l'histoire
de l’informatique. Elle est surtout connue pour avoir contribué à la création de l'un des premiers compilateurs
de langages de programmation et pour avoir popularisé l'utilisation des termes "débogage"
et "bug" en cachant un insecte mort dans un ordinateur défectueux.
````
### Exercice 2
A l'aide de la table ASCII qui se trouve sur cette page, encodez le mot "Suisse".
````{admonition} Solution
:class: note dropdown
1010011 1110101 1101001 1110011 1110011 1100101
````

### Exercice 3
a) Si on écrit dans un fichier texte de notre ordinateur le message "Hello World !", quel sera la taille de ce fichier (en octets), sachant que celui-ci sera encodé avec UTF-8 ?


b) Ouvrez réellement un fichier texte (.txt) avec le bloc-note de votre ordinateur et écrivez le texte "Hello World !". Enregistrez ce fichier, puis faites un clic-droite dessus et sélectionnez les propriétés pour inspecter la propriété de la taille et vérifier votre réponse à la question précédente.


c) Effacez ensuite le contenu de ce fichier et écrivez le texte "Où as-tu mangé à midi ?" à la place. A nouveau, sachant que le fichier est encodé avec UTF-8, pouvez-vous prédire la taille du fichier ? Contrôlez votre réponse en consultant la taille du fichier sur votre ordinateur.


d) Réécrivez ce même texte dans un fichier Microsoft Word (.docx) et consultez ensuite sa taille. Ce fichier est-il plus lourd ou plus léger que le fichier .txt ? Quelle est l'explication de ce résultat ?

### Exercice 4

a) En utilisant la [page Wikipédia d'Unicode](https://en.wikipedia.org/wiki/List_of_Unicode_characters), déterminez les Unicodes des caractères suivants :
 - K
 - à
 - ጬ
 - ♕
 - ♛

 b) En Python, il est possible d'utiliser Unicode dans un `print()` pour afficher la représentation de ce caractère. Par exemple `print("\u0040")` affiche le symbole `@`. Ouvrez Thonny et écrivez 2 lignes de code pour afficher les pièces d'échecs de la dame blanche et de la dame noire.

 ### Exercice 5

 a) Le texte ci-dessous est encodé en UTF-8. Comme vous le savez, UTF-8 encode les caractères avec des séquences de 1, 2, 3, ou 4 octets. Commencez par grouper les octets appartenant à la même séquence.

 01010011 01100011 01101000 11000011 10110110 01101110 00100000 11110000 10011111 10010000 10111011

 b) En utilisant [cette table UTF-8](https://www.utf8-chartable.de/unicode-utf8-table.pl?number=1024&utf8=bin), décodez ce texte. N'hésitez pas à utiliser de la fonction "recherche" avec CTRL+F (ou CMD+F sur Mac). Indice : le dernier caractère se trouve dans la catégorie *Miscellaneous Symbols and Pictographs*
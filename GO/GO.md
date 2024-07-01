#GO 

## GO COMMAND 

# go run :
Compile les fichier go dans un dossiers temporaires, execute le "binary" et supprime apres l'avoir fait.

```go
go run hello.go
```
## go build : 
compile le programme dans un binary, possibilité de choir le nom du binaire mais par default c'est le nom du fichier ou du dossier ou le chemin dans lequel ou dans un chemin choisi. 

```go
go build -o surprise main.go
```
## go install
Les programmes Go peuvent être distribués sous forme de binaires précompilés ou construits à partir du code source et installés via la commande go install. Contrairement à d'autres langages, Go ne dépend pas d'un service centralisé comme Maven Central ou NPM, mais utilise des dépôts de code source pour partager des projets. La commande go install nécessite l'emplacement du dépôt et la version de l'outil (par exemple, @latest pour la dernière version) et installe l'outil dans le répertoire $GOPATH/bin.

```go
go install github.com/rakyll/hey@latest
```

## FORMATTING :
Les programmes Go peuvent être distribués sous forme de binaires précompilés ou construits à partir du code source et installés via la commande go install. Contrairement à d'autres langages, Go ne dépend pas d'un service centralisé comme Maven Central ou NPM, mais utilise des dépôts de code source pour partager des projets. La commande go install nécessite l'emplacement du dépôt et la version de l'outil (par exemple, @latest pour la dernière version) et installe l'outil dans le répertoire $GOPATH/bin.

En plus de go install, Go offre plusieurs autres outils utiles :

    go fmt : formate automatiquement le code selon les conventions Go.
    go imports : nettoie les imports non utilisés et formate les imports restants.
    go lint : aide à respecter les guidelines de style et de bonnes pratiques.
    go vet : détecte les erreurs potentielles dans le code, telles que les variables non utilisées.

Ces outils aident à maintenir un code propre, bien formaté et conforme aux standards de la communauté Go.

## GO PRIMITIVE:

## La valeur zéro :
Go, comme la plupart des langages modernes, attribue une valeur zéro par défaut à toute variable

## GO lITERAUX :
Littéraux en Go

En Go, un littéral fait référence à l'écriture explicite d'un nombre, d'un caractère ou d'une chaîne de caractères dans le code. Il existe quatre types courants de littéraux que vous trouverez dans les programmes Go, et un cinquième type rare que nous aborderons en discutant des nombres complexes.
Littéraux entiers

Les littéraux entiers sont des séquences de chiffres. Par défaut, ils sont en base 10, mais Go utilise différents préfixes pour indiquer d'autres bases :

    Binaire (base 2) : préfixe 0b (par exemple, 0b1010).
    Octal (base 8) : préfixe 0o (par exemple, 0o12).
    Hexadécimal (base 16) : préfixe 0x (par exemple, 0x1A).

Vous pouvez utiliser des lettres majuscules ou minuscules pour les préfixes (0x ou 0X). Notez qu'un 0 initial sans lettre après (012) représente également un littéral octal en Go, mais il est déconseillé d'utiliser cette notation car elle est source de confusion.
Utilisation des underscores

Pour rendre les littéraux entiers longs plus lisibles, Go permet l'utilisation d'underscores _ au milieu du littéral. Par exemple, vous pouvez regrouper les chiffres par milliers en base 10 comme suit : 1_234_567. Les underscores n'ont aucun effet sur la valeur du nombre.
Limitations des underscores

    Les underscores ne peuvent pas être placés au début ou à la fin des nombres.
    Ils ne peuvent pas être adjacents (1__234 est invalide).

Vous pouvez théoriquement mettre un underscore entre chaque chiffre (1_2_3_4), mais cela est fortement déconseillé. Utilisez-les plutôt pour améliorer la lisibilité en divisant les nombres en base 10 par milliers ou en divisant les nombres binaires, octaux ou hexadécimaux à des frontières de 1, 2 ou 4 octets.

Exemples :

    Base 10 : 1_000_000
    Binaire : 0b1010_1101
    Octal : 0o755_123
    Hexadécimal : 0x1A3F_FF

En suivant ces conventions, vous rendrez vos littéraux numériques plus clairs et plus faciles à lire pour les autres développeurs.

Littéraux à virgule flottante en Go

Les littéraux à virgule flottante en Go utilisent des points décimaux pour indiquer la partie fractionnaire de la valeur. Ils peuvent également inclure un exposant, spécifié avec la lettre e suivie d'un nombre positif ou négatif.
Exemples en notation décimale :

    6.03e23 (équivalent à 6.03×10236.03×1023)
    1.5 (simplement 1.5)

Il est également possible d'écrire des littéraux à virgule flottante en notation hexadécimale en utilisant le préfixe 0x et la lettre p pour indiquer l'exposant.
Exemples en notation hexadécimale :

    0x1.91eb851eb851fp+1 (équivalent à 1.10111010111000000000000000000000000000000000000000002×211.10111010111000000000000000000000000000000000000000002​×21)

Comme pour les littéraux entiers, vous pouvez utiliser des underscores _ pour formater vos littéraux à virgule flottante et les rendre plus lisibles.
Exemples avec underscores :

    1_000.000_001 (milliers séparés par des underscores)
    6.03e2_3 (exposant avec un underscore)
    0x1.91eb_851f_p+1 (partie hexadécimale et exposant avec des underscores)

Ces notations rendent les nombres plus faciles à lire et à comprendre, améliorant ainsi la clarté du code.

## Littéraux de runes et chaînes en Go :

Les littéraux de runes représentent des caractères et sont entourés de guillemets simples. Contrairement à de nombreux langages, les guillemets simples et doubles ne sont pas interchangeables en Go. Voici quelques façons de les écrire :

    Caractère Unicode simple : 'a'
    Numéros octaux 8 bits : '\141'
    Numéros hexadécimaux 8 bits : '\x61'
    Numéros hexadécimaux 16 bits : '\u0061'
    Numéros Unicode 32 bits : '\U00000061'

Les littéraux de runes incluent aussi des caractères échappés avec des backslashes, comme le saut de ligne ('\n'), la tabulation ('\t'), le guillemet simple ('\''), le guillemet double ('\"'), et le backslash ('\\').
Littéraux de chaînes

Il existe deux façons d'indiquer les littéraux de chaînes en Go :

    Chaînes interprétées : Utilisez des guillemets doubles pour créer des chaînes interprétées ("Hello, World!"). Elles peuvent contenir des littéraux de runes, mais pas de backslashes, de sauts de ligne ou de guillemets doubles non échappés. Exemple :

    go

"Bonjour\n\"le Monde\""

Chaînes brutes : Utilisez des backquotes (`) pour les chaînes brutes qui peuvent contenir n'importe quel caractère sauf le backquote. Exemple :

go

    `Bonjour
    "le Monde"`

Utilisation des littéraux

    Les littéraux en Go sont non typés par défaut et peuvent interagir avec n'importe quelle variable compatible.
    Vous ne pouvez pas assigner un littéral de chaîne à une variable numérique ou un littéral numérique à une variable de chaîne.
    Les littéraux numériques ne peuvent pas dépasser la capacité de la variable cible, sinon cela génère une erreur à la compilation.

Par exemple, pour assigner un littéral à une variable :

go

var f float64 = 42 // OK
var b byte = 1000 // Erreur : dépassement de capacité

Lorsque le type n'est pas explicitement déclaré, Go utilise un type par défaut pour le littéral, comme nous le verrons dans la section sur l'affectation des variables.
 
## NUMERIC TYPE
 ## Types Entiers

Go propose des entiers signés et non signés de différentes tailles, allant d'un à quatre octets :

| Type   | Plage de valeurs                       |
|--------|----------------------------------------|
| int8   | -128 à 127                             |
| int16  | -32768 à 32767                         |
| int32  | -2147483648 à 2147483647               |
| int64  | -9223372036854775808 à 9223372036854775807 |
| uint8  | 0 à 255                                |
| uint16 | 0 à 65535                              |
| uint32 | 0 à 4294967295                         |
| uint64 | 0 à 18446744073709551615               |

La valeur zéro pour tous les types entiers est 0.

## The special integer Types
Un bytes est un alias the uint8, it is legal to assign, compare, or perform mathematical operations
between a byte and a uint8.

dans une archicture 64 int prend deviens int64 signed et dans une architecture 32 il deviens un int32 signed
The third special name is uint. It follows the same rules as int, only it is
unsigned

f you are working with a binary file format or network protocol that
has an integer of a specific size or sign, use the corresponding integer
type.
If you are writing a library function that should work with any integer
type, write a pair of functions, one with int64 for the parameters and
variables and the other with uint64. (We talk more about functions
and their parameters in
sinon utilisez int

# Floating Point Types

Il existe deux types de nombres à virgule flottante en Go :

| Type     | Valeur absolue maximale                                      | Valeur absolue minimale (non nulle)                           |
|----------|--------------------------------------------------------------|---------------------------------------------------------------|
| float32  | 3.40282346638528859811704183484516925440e+38                 | 1.401298464324817070923729583289916131280e-45                 |
| float64  | 1.797693134862315708145274237317043567981e+308               | 4.940656458412465441765687928682213723651e-324                |

Comme pour les types entiers, la valeur zéro pour les types de nombres à virgule flottante est 0.

Les nombres à virgule flottante en Go fonctionnent de manière similaire à ceux des autres langages de programmation. Go utilise la spécification IEEE 754, offrant une large gamme et une précision limitée. Le choix du type de nombre flottant à utiliser est simple : sauf si vous devez être compatible avec un format existant, utilisez `float64`. Les littéraux de nombres flottants ont par défaut le type `float64`, donc utiliser toujours `float64` est l'option la plus simple. Cela aide également à atténuer les problèmes de précision des nombres flottants, car un `float32` n'a que 6 ou 7 chiffres décimaux de précision.

WARNING
A floating-point number cannot represent a decimal value exactly. Do not use them to
represent money or any other value that must have an exact decimal representation!
on ne peut pas utilser modulo avec les floats

While Go lets you use == and != to compare floats, don’t do it. Due to the
inexact nature of floats, two floating point values might not be equal when you
think they should be. Instead, define a minimum allowed variance and see if the
difference between two floats is less than that

## A Taste of Strings and Runes : 
Strings in Go are immutable; you can reassign the value of a string variable, but
you cannot change the value of the string that is assigned to it.

## TYPE 
. Since all type conversions in
Go are explicit, you cannot treat another Go type as a boolean.
```go
var x int = 10
if x {
        //Do some
    } // do not do this
//Do
if x != 0 {
    // Do something
    }
```

You can declare multiple variables at once with var, and they can be of the
same type:
```go
var x, y int = 10, 20
var x, y  = 10, "HELLO "
var (
x int = 10
m = "dll"
)
```
you can declare multiple variables at once using :=.
```go
x, y := 10, "hello"
```

Comment savoir quel style utiliser ? Comme toujours, choisissez ce qui rend votre intention la plus claire possible. Le style de déclaration le plus courant dans les fonctions est :=. En dehors d'une fonction, utilisez des listes de déclarations lors des rares occasions où vous déclarez plusieurs variables au niveau du package.

Il y a certaines situations dans les fonctions où vous devez éviter := :

    Lors de l'initialisation d'une variable à sa valeur zéro, utilisez var x int. Cela indique clairement que la valeur zéro est intentionnelle.
    Lorsque vous assignez une constante non typée ou une valeur littérale à une variable et que le type par défaut de cette constante ou de cette valeur littérale n'est pas celui que vous souhaitez pour la variable, utilisez la forme longue var avec le type spécifié. Bien qu'il soit légal d'utiliser une conversion de type pour spécifier le type de la valeur et utiliser := pour écrire x := byte(20), il est plus idiomatique d'écrire var x byte = 20.

Parce que := permet d'assigner à la fois à de nouvelles variables et à des variables existantes, il peut parfois créer de nouvelles variables alors que vous pensez réutiliser des variables existantes (voir "Variables Ombrées" pour plus de détails). Dans ces situations, déclarez explicitement toutes vos nouvelles variables avec var pour rendre clair quelles variables sont nouvelles, puis utilisez l'opérateur d'affectation (=) pour assigner des valeurs aux variables nouvelles et anciennes.

## ARRAY 
If you have a sparse array (an array where most elements are set to their zero
value), you can specify only the indices with values in the array literal:
var x = [12]int{1, 5: 4, 6, 10: 100, 15}
This creates an array of 12 int s with the following values: [1, 0, 0, 0,
0, 4, 6, 0, 0, 0, 100, 15].

When using an array literal to initialize an array, you can leave off the numberand use … instead:
var x = [...]int{10, 20, 30}

You can use == and != to compare arrays:
var x = [...]int{1, 2, 3}
var y = [3]int{1, 2, 3}
fmt.Println(x == y) // prints true
Go only has one-dimensional arrays, but you can simulate multi-dimensional
arrays:
```go
var x [2][3]int
```
Earlier I said that arrays in Go are rarely used explicitly. This is because they
come with an unusual limitation: Go considers the size of the array to be part of
the type of the array. This makes an array that’s declared to be [3]int a
different type from an array that’s declared to be [4]int. This also means that
you cannot use a variable to specify the size of an array, because types must be
resolved at compile time, not at runtime.

## APPEND BUILT IN 
One slice is appended onto another by using the … operator to expand the source
slice into individual values (we’ll learn more about the … operator in “Variadic
Input Parameters and Slices”):
y := []int{20,30,40}
x = append(x, y...)
It is a compile-time error if you forget to assign the value returned from
append. You might be wondering why as it seems a bit repetitive. We will talk
about this in greater detail in Chapter 5, but Go is a call by value language.
Every time you pass a parameter to a function, Go makes a copy of the value
that’s passed in. Passing a slice to the append function actually passes a copy
of the slice to the function. The function adds the values to the copy of the slice,
and returns the copy. You then assign the returned slice back to the variable in

## Capacity
As we’ve seen, a slice is a sequence of values. Each element in a slice is
assigned to consecutive memory locations, which makes it quick to read or write
these values. Every slice has a capacity, which is the number of consecutive
memory locations reserved. This can be larger than the length. Each time you
append to a slice, one or more values is added to the end of the slice. Each value
added increases the length by one. When the length reaches the capacity, there’s
no more room to put values. If you try to add additional values when the length
equals the capacity, the append function uses the Go runtime to allocate a new
slice with a larger capacity. The values in the original slice are copied to the new
slice, the new values are added to the end, and the new slice is returned

## MAKE 
the built-in make function. It allows us to specify the type, length, and, optionally, the capacity.

## WHA TOO CHOOSE  Declaring Your Slice
Now that we’ve seen all these different ways to create slices, how do you choose
which slice declaration style to use? The primary goal is to minimize the number
of times the slice needs to grow. If it’s possible that the slice won’t need to grow
at all (because your function might return nothing), use a var declaration with
no assigned value to create a nil slice:

If you have some starting values, or if a slice’s values aren’t going to change,
then a slice literal is a good choice:
Example 3-3. Declaring a slice with default values
data := []int{2, 4, 6, 8}

If you have a good idea of how large your slice needs to be, but don’t know what
those values will be when you are writing the program, use make.

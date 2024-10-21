# Work Unit: Compter le nombre de bits à 1

## Contexte du problème
L'objectif est de créer une fonction qui prend en entrée un entier non négatif et retourne le nombre de bits qui sont égaux à 1 dans la représentation binaire de cet entier.

### Exemple
Pour un entier donné, tel que 1234, la représentation binaire est `10011010010`. Il y a 5 bits qui sont égaux à 1 dans cette représentation, donc la fonction doit renvoyer 5.

## Algorithme proposé

1. Initialiser un compteur (`count`) à 0 pour compter les bits égaux à 1.
2. Tant que l'entier n'est pas nul :
   - Vérifier si le bit le moins significatif est égal à 1 en utilisant l'opérateur `&`.
   - Si oui, incrémenter le compteur.
   - Décaler les bits de l'entier vers la droite avec l'opérateur de décalage `>>`.
3. Retourner le compteur une fois tous les bits traités.

### Complexité
La complexité temporelle de cet algorithme est **O(log n)**, où `n` est la valeur de l'entier en entrée, car le nombre d'itérations dans la boucle est proportionnel au nombre de bits nécessaires pour représenter cet entier.

## Solution en C

```c
#include <stddef.h>

// Fonction pour compter les bits à 1 dans la représentation binaire
size_t countBits(unsigned value)
{
    size_t count = 0;
    while (value)
    {
        count += value & 1;  // Incrémente si le bit est à 1
        value >>= 1;         // Décale les bits vers la droite
    }
    return count;
}

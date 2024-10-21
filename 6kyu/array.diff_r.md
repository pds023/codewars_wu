# Work Unit (WU): Fonction de différence entre deux listes

## Description du problème

L'objectif est d'implémenter une fonction de différence qui soustrait une liste (ou tableau) d'une autre et retourne le résultat.

La fonction doit supprimer de la liste **a** toutes les valeurs présentes dans la liste **b**, tout en conservant l'ordre des éléments restants.

### Exemple :

- `array_diff(c(1, 2), 1)` retourne `c(2)`
- `array_diff(c(1, 2, 2, 2, 3), 2)` retourne `c(1, 3)`

### Contraintes :
- Si une valeur est présente dans **b**, toutes ses occurrences doivent être supprimées de **a**.
- L'ordre des éléments restants dans **a** doit être conservé.

## Plan de la solution :

1. **Suppression des éléments communs** :
   - Utiliser une opération de filtrage pour éliminer les éléments de **a** qui sont présents dans **b**.

2. **Retourner la liste modifiée** :
   - Retourner la liste **a** sans les éléments qui sont dans **b**.

## Fonction en R :

```r
array_diff <- function(a, b) {
  # Filtrer les éléments de 'a' qui ne sont pas dans 'b'
  return(a[!a %in% b])
}
```

### Explication :
- La fonction utilise l'opérateur %in% pour vérifier quels éléments de a sont présents dans b.
- Ensuite, elle filtre ces éléments en retournant uniquement ceux qui ne sont pas dans b.
- L'ordre des éléments restants est conservé grâce à l'opération de filtrage.

### Complexité :
- Temps : O(n * m), où n est la taille de a et m est la taille de b. Chaque élément de a est comparé à tous les éléments de b.
- Espace : O(1), car la fonction retourne directement une nouvelle liste filtrée sans utiliser de structures supplémentaires importantes.
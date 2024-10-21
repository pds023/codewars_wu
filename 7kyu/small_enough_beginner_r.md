# Write Up : Vérification des valeurs sous une limite

## Description du problème

On vous donne un tableau de nombres et une valeur limite. Vous devez vérifier que toutes les valeurs dans le tableau sont inférieures ou égales à cette limite. Si c'est le cas, retournez **True**. Sinon, retournez **False**.

### Contraintes :
- Tous les éléments du tableau sont des nombres.
- Le tableau peut être de n'importe quelle longueur.

## Plan de la solution :

1. **Vérification des valeurs** :
   - Utiliser une opération de filtrage pour sélectionner toutes les valeurs inférieures ou égales à la limite.
   - Comparer la longueur de ce sous-ensemble avec la longueur totale du tableau.

2. **Retour du résultat** :
   - Si toutes les valeurs sont inférieures ou égales à la limite, retourner **True**.
   - Sinon, retourner **False**.

## Fonction en R :

```r
small_enough <- function(vector, limit) {
  # Filtrer les éléments du tableau qui sont inférieurs ou égaux à la limite
  return(length(vector[vector <= limit]) == length(vector))
}
```

### Explication :
- La fonction filtre les éléments du tableau qui respectent la condition d'être inférieurs ou égaux à la limite donnée.
- Elle compare ensuite la longueur du tableau filtré avec la longueur totale du tableau d'origine.
- Si toutes les valeurs respectent la limite, la fonction retourne True, sinon elle retourne False.

### Complexité :
- Temps : O(n), où n est la taille du tableau. Chaque élément est vérifié une seule fois.
- Espace : O(1), car la vérification se fait directement sur le tableau sans créer de structures supplémentaires significatives.
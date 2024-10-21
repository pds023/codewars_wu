# Write up : Détection de Pangramme

## Description du problème

Un pangramme est une phrase qui contient chaque lettre de l'alphabet au moins une fois. Par exemple, la phrase **"The quick brown fox jumps over the lazy dog"** est un pangramme car elle utilise les lettres de A à Z au moins une fois (la casse des lettres n'est pas prise en compte).

### Objectif :

Étant donné une chaîne de caractères, l'objectif est d'écrire une fonction qui détecte si cette chaîne est un pangramme ou non. La fonction doit retourner **True** si la chaîne est un pangramme, sinon **False**. Les chiffres et les signes de ponctuation doivent être ignorés.

## Plan de la solution :

1. **Prétraitement** :
   - Enlever les espaces et les signes de ponctuation.
   - Convertir la chaîne en minuscules pour ignorer la casse.

2. **Vérification du pangramme** :
   - Compter les lettres uniques dans la chaîne après le prétraitement.
   - Comparer ces lettres avec l'alphabet complet (26 lettres).

### Fonction en R :

```r
is_pangram <- function(s){
  # Suppression des espaces
  s <- gsub(s, pattern = " ", replacement = "")
  
  # Conversion en minuscules
  s <- tolower(s)
  
  # Vérification de la longueur minimale (26 lettres)
  if(nchar(s) < 26) {
    return(FALSE)
  }
  
  # Suppression de la ponctuation
  s <- gsub("[[:punct:]]", "", s, ignore.case = TRUE)
  
  # Découpage de la chaîne en caractères individuels
  s <- unlist(strsplit(s, ""))
  
  # Vérification si toutes les lettres de l'alphabet sont présentes
  result <- sum(base::letters %in% s) == length(base::letters)
  
  return(result)
}
```

### Explication :
- La chaîne est d'abord nettoyée des espaces et des signes de ponctuation.
- Elle est ensuite convertie en minuscules.
- Si la longueur de la chaîne est inférieure à 26, on retourne directement False car elle ne peut pas contenir toutes les lettres de l'alphabet.
- Ensuite, on vérifie si chaque lettre de l'alphabet est présente dans la chaîne transformée.
- Enfin, la fonction retourne True si la chaîne contient toutes les lettres, sinon False.

### Complexité :
- Temps : O(n), où n est la longueur de la chaîne donnée.
- Espace : O(1), car la vérification se fait en comparant le nombre de lettres présentes avec l'alphabet qui a une taille fixe.
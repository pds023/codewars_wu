# Write up : Validation de la durée d'une promenade en ville

## Description du problème

Vous vivez dans la ville de Cartesia où toutes les routes sont disposées en grille parfaite. Vous arrivez dix minutes trop tôt à un rendez-vous, et vous décidez de faire une petite promenade. La ville met à disposition de ses habitants une application génératrice de promenade qui vous envoie un tableau de chaînes de caractères d'une seule lettre représentant les directions à suivre (par exemple : ['n', 's', 'w', 'e']). Vous marchez d'un bloc pour chaque lettre (direction) et il vous faut une minute pour traverser un bloc de la ville. Créez une fonction qui retourne **True** si la promenade donnée par l'application dure exactement dix minutes et vous ramène à votre point de départ. Retournez **False** dans le cas contraire.

### Contraintes :
- Vous recevez toujours un tableau valide contenant un ensemble aléatoire de lettres de direction ('n' pour nord, 's' pour sud, 'e' pour est, 'w' pour ouest).
- Le tableau ne sera jamais vide.

## Plan de la solution :

1. **Vérification de la durée** :
   - Si la longueur du tableau n'est pas exactement de 10, retourner immédiatement **False**.

2. **Calcul des déplacements** :
   - Initialiser une position de départ à (0, 0).
   - Parcourir le tableau et mettre à jour les coordonnées en fonction des directions :
     - **n** (nord) ajoute +1 à la coordonnée y.
     - **s** (sud) soustrait -1 à la coordonnée y.
     - **e** (est) ajoute +1 à la coordonnée x.
     - **w** (ouest) soustrait -1 à la coordonnée x.

3. **Retour au point de départ** :
   - Si après avoir parcouru toutes les directions, les coordonnées sont revenues à (0, 0), retourner **True**.
   - Sinon, retourner **False**.

## Fonction en R :

```r
isValidWalk <- function(walk){
  # Initialisation de la position de départ
  pos <- c(0, 0)
  
  # Vérification si la durée de la marche est bien de 10 minutes
  if(length(walk) != 10){
    return(FALSE)
  }
  
  # Parcours du tableau et mise à jour des coordonnées
  for (i in 1:length(walk)) {
    if (walk[i] == "n") {
      pos[1] <- pos[1] + 1  # Déplacement vers le nord
    }
    if (walk[i] == "s") {
      pos[1] <- pos[1] - 1  # Déplacement vers le sud
    }
    if (walk[i] == "e") {
      pos[2] <- pos[2] + 1  # Déplacement vers l'est
    }
    if (walk[i] == "w") {
      pos[2] <- pos[2] - 1  # Déplacement vers l'ouest
    }
  }
  
  # Vérification du retour au point de départ
  if (pos[1] == 0 && pos[2] == 0) {
    return(TRUE)
  } else {
    return(FALSE)
  }
}
```

### Explication :
- Initialisation : La position initiale est définie comme (0, 0).
- Parcours : Chaque direction modifie les coordonnées x ou y en fonction du tableau d'entrées.
- Validation : Si la longueur du tableau est différente de 10, la fonction retourne False directement. Sinon, elle vérifie si le chemin ramène à la position initiale après 10 minutes.

### Complexité :
- Temps : O(n), où n est la taille du tableau (ici, 10 au maximum).
- Espace : O(1), car seules deux variables (les coordonnées) sont utilisées pour suivre la position.
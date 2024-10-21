# Write Up : Convertir des mots délimités par des tirets ou des underscores en camelCase

## Contexte du problème
L'objectif est de compléter une fonction qui prend en entrée une chaîne de caractères contenant des mots délimités par des tirets (`-`) ou des underscores (`_`) et retourne une chaîne formatée en camelCase.

### Exemples
- `"the-stealth-warrior"` doit être converti en `"theStealthWarrior"`.
- `"The_Stealth_Warrior"` doit être converti en `"TheStealthWarrior"`.
- `"The_Stealth-Warrior"` doit être converti en `"TheStealthWarrior"`.

### Règles
- Le premier mot doit rester en minuscules si l'original est en minuscules.
- Tous les mots suivants doivent commencer par une majuscule.
- Les délimiteurs (`-` ou `_`) doivent être supprimés.

## Algorithme proposé

1. Initialiser une chaîne vide `result` pour stocker le résultat.
2. Utiliser un booléen `capitalizeNext` pour savoir quand capitaliser un caractère. Ce booléen est mis à `true` lorsqu'un tiret ou un underscore est rencontré.
3. Parcourir chaque caractère de la chaîne d'entrée :
   - Si le caractère est un tiret (`-`) ou un underscore (`_`), activer `capitalizeNext`.
   - Sinon, ajouter le caractère courant en le capitalisant si nécessaire (selon la valeur de `capitalizeNext`), puis désactiver `capitalizeNext`.
4. Retourner la chaîne formée après traitement.

### Complexité
- **Complexité temporelle** : O(n), où `n` est la longueur de la chaîne d'entrée. Chaque caractère est traité une seule fois.
- **Complexité spatiale** : O(n), où `n` est la longueur de la chaîne d'entrée, pour stocker la chaîne résultante.

## Solution en C++

```cpp
#include <string>
#include <cctype>

std::string to_camel_case(std::string text) {
    std::string result;
    bool capitalizeNext = false; // Indicateur pour savoir si on doit capitaliser le prochain caractère

    for (size_t i = 0; i < text.size(); ++i) {
        if (text[i] == '-' || text[i] == '_') {
            capitalizeNext = true; // On doit capitaliser la lettre suivante
        } else {
            if (capitalizeNext) {
                result += std::toupper(text[i]); // On capitalise la lettre
                capitalizeNext = false;
            } else {
                result += text[i]; // On garde la lettre telle qu'elle est
            }
        }
    }
    return result;
}

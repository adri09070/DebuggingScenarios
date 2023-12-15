# Scénarios

Je ferais ces points dans l'ordre : 1) donne un vrai scénario, 2) décrit et illustre tout ce qui est possible avec Chest, 3) décrit un scénario spécifique.

## 1) Comparaison d'objets inter-outils

Dans ce scénario, j'ai deux outils ouverts comme un inspecteur et un debugger ou bien deux inspecteurs.
J'observe d'abord un objet dans un inspecteur.
Puis, je debug un programme lié à cet objet, et j'observe dans le debugger ou bien un nouvel inspecteur un autre objet.

La question que je me pose est la suivante : est-ce que les deux objets que j'observe sont en réalité le même objet ?

Avec Chest, on peut passer la référence d'un des objets dans l'autre inspecteur et comparer avec un ==.

**Note :** Peut on envisager d'ajouter une entrée dans le menu de l'inspecteur pour faire "clic droit sur self (ou dans l'évaluateur) -> compare with -> sélection d'un objet dans Chest" et qui retournerait un booléen printé dans l'évaluateur ? (pour éviter les comparaisons via l'exécution de code dans l'évaluateur)

Bien sûr j'ai d'autres moyens de vérifier cela, comme par exemple :
- imprimer le hash de chaque objet dans son inspecteur et les comparer
- modifier un des objets pour vérifier si la modification est reportée dans l'autre
Ceci dit, ça casse le flow d'utilisation de l'IDE car ça me force à trouver des hacks pour obtenir la même info.
Avec Chest, on a une API et un outil intégré.

## 2) Variable globale avec une API

Finalement, Chest c'est une API autour d'une variable globale et avec des tests unitaires, pour éviter d'avoir à gérer ce besoin de manière ad-hoc.

Présentation :
- Stockage d'objets dans le Chest à partir de différentes sources (inspecteur, debugger, etc.)
- Réutilisation d'objets dans différents outils (inspecteur, debugger, etc.)
- Type de stockage (weak ou pas)
- Intégration dans le debugger
- API de Chest (programmatique)


## 3) Copie d'objets

Il s'agit d'outillage autour de l'API.

Là on veut : 
- copier des références d'objets rapidement pour les réutiliser ailleurs ctrl+c -> ctrl+v
- copier des objets pour en obtenir rapidement des duplicatas
    - copie simple (shallow copy)
    - copie complète (deep copy)

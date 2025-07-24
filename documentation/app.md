## Composant `App.vue` (continue)

### Explications des balises utilisées

* `v-model` : c'est une directive Vue.js qui permet de lier une propriété du composant avec l'état d'un élément de contrôle, tels que les inputs ou les checkboxes. Ici, elle est utilisée pour récupérer la valeur renseignée dans le champ `newTodo` lorsque l'utilisateur soumet le formulaire.
* `:key` : c'est une directive qui permet d'identifier un élément unique dans la liste des éléments à afficher. Ici, il est utilisé pour éviter les erreurs de rendu dans Vue.js lorsque la liste des éléments change dynamiquement.
* `:class` : c'est une directive qui permet de lier un classe CSS avec un élément HTML en fonction d'une condition. Ici, elle est utilisée pour ajouter la classe CSS `completed` aux éléments de la liste qui ont été marqués comme terminées (via l'utilisation du composant Checkbox).

### Description des méthodes et des propriétés utilisées

* `ref` : c'est une fonction Vue.js qui permet de créer une référence à un élément du DOM, pour pouvoir y accéder par la suite dans le script du composant. Ici, elle est utilisée pour stocker les propriétés et les états des différents éléments du composant (`hideCompleted`, `todos`, `newTodo`, etc.).
* `computed` : c'est une fonction Vue.js qui permet de créer une propriété calculée à partir d'autres propriétés ou méthodes du composant. Ici, elle est utilisée pour calculer le nombre restant de tâches non terminées (`remainingTodos`) et pour trier les éléments de la liste selon leur état (`sortedTodo`).
* `@submit.prevent` : c'est une directive Vue.js qui permet d'empêcher la soumission du formulaire en utilisant l'événement `submit`. Ici, elle est utilisée pour empêcher la page de recharger lorsque l'utilisateur clique sur le bouton de soumission du formulaire.
* `filter` : c'est une méthode JavaScript qui permet de filtrer un tableau en fonction d'une condition. Ici, elle est utilisée pour filtrer les éléments du tableau `todos` en fonction de leur état (terminé ou non).
* `toSorted` : c'est une méthode JavaScript qui permet de trier un tableau selon une fonction de comparaison. Ici, elle est utilisée pour trier les éléments du tableau `todos` en fonction de leur état (terminé ou non).
* `Array.prototype.push` : c'est une méthode JavaScript qui permet d'ajouter un élément à la fin d'un tableau. Ici, elle est utilisée pour ajouter un nouvel élément au tableau `todos` lorsque l'utilisateur soumet le formulaire.
* `Array.prototype.filter` : c'est une méthode JavaScript qui permet de filtrer un tableau en fonction d'une condition. Ici, elle est utilisée pour filtrer les éléments du tableau `todos` en fonction de leur état (terminé ou non).
* `Array.prototype.toSorted` : c'est une méthode JavaScript qui permet de trier un tableau selon une fonction de comparaison. Ici, elle est utilisée pour trier les éléments du tableau `todos` en fonction de leur état (terminé ou non).
* `Date.now` : c'est une propriété JavaScript qui renvoie la date et l'heure actuelle en millisecondes depuis le 1 janvier 1970 à minuit UTC. Ici, elle est utilisée pour assurer que chaque nouvel élément ajouté au tableau `todos` a une date unique.
# Documentation de l'application Vue.js

## Composant `Checkbox.vue`

Ce composant est un élément de contrôle utilisateur (UI component) qui représente une case à cocher. Il permet d'indiquer si une action a été effectuée ou non.

### Structure du composant

Le composant contient trois balises :

* `template` : définit la structure HTML de la case à cocher.
* `script setup` : utilise la syntaxe Vue 3 pour initialiser les données et les événements associés au composant.
* `style scoped` : définit le style spécifique à ce composant.

### Données du composant

Le composant a plusieurs propriétés reçues via props et émises via events :

* `props.label` : un string contenant le label de la case à cocher (titre).
* `model` : un boolean reflètant l'état de la case à cocher. Si elle est cochee, il a une valeur `true`, sinon `false`. Il est géré par la directive `v-model`.

### Événements du composant

* `onChange` : appelé lorsqu'une modification sur l'état de la case à cocher est effectuée. Les événements sont émis en utilisant les méthodes `emit`.

Pour plus d'informations sur les composants Vue.js, je vous invite à consulter la [documentation officielle](https://vuejs.org/v2/guide/).
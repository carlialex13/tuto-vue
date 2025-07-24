# tuto-vue

This template should help get you started developing with Vue 3 in Vite.

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur).

## Customize configuration

See [Vite Configuration Reference](https://vite.dev/config/).

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```

Bien sûr ! Voici un résumé détaillé et fusionné de la structure, des fonctions, des hooks et des concepts Vue.js utilisés dans ton fichier App.vue, combiné avec le mémo précédent. Ce document te servira de référence rapide pour tes futurs projets.

---

# 📄 Résumé détaillé de App.vue

## 1. Structure du composant

- **Utilisation du composant `Layout`**  
  Organisation de la page via des slots nommés :
  - `header` : En tete
  - `aside` : Aside
  - `main` : Main
  - `footer` : Footer

- **Bouton personnalisé**  
  Utilisation du composant `<Button>` avec slot pour contenu personnalisé.

- **Formulaire d’ajout de tâche**  
  - Champ texte lié à `newTodo` via `v-model`
  - Bouton désactivé si le champ est vide
  - Soumission du formulaire déclenche `addTodo`

- **Affichage conditionnel**  
  - Si aucune tâche : message spécifique
  - Sinon : liste des tâches, gestion de l’affichage selon l’état

- **Liste des tâches**  
  - Boucle sur `sortedTodo`
  - Utilisation du composant `<Checkbox>` lié à `todo.completed` via `v-model`
  - Affichage dynamique du nombre de tâches restantes

- **Filtre des tâches terminées**  
  - Checkbox liée à `hideCompleted` via `v-model`

---

## 2. Fonctions et propriétés réactives

- **`ref()`**  
  - `hideCompleted` : booléen pour masquer/afficher les tâches terminées
  - `todos` : tableau d’objets tâche (titre, état, date)
  - `newTodo` : contenu du champ texte (⚠️ devrait être `ref('')` et non `ref([])`)

- **`computed()`**  
  - `remainingTodos` : nombre de tâches non terminées
  - `sortedTodo` : liste triée (non terminées d’abord, filtrée si besoin)

- **Fonction `addTodo`**  
  Ajoute une nouvelle tâche à la liste, puis vide le champ texte.

---

## 3. Concepts Vue.js utilisés

### Réactivité

- **`ref()`**  
  Pour les valeurs primitives ou objets simples à rendre réactifs.
- **`computed()`**  
  Pour les valeurs calculées dépendant d’autres données réactives.

### Liaison de données

- **`v-model`**  
  Liaison bidirectionnelle entre les inputs et les propriétés réactives (`newTodo`, `hideCompleted`, `todo.completed`).

### Slots

- **Slots nommés**  
  Permettent de personnaliser les différentes parties du layout via `<template #nom>`.

### Affichage conditionnel

- **`v-if` / `v-else`**  
  Pour afficher ou masquer des éléments selon l’état de l’application.

### Boucles

- **`v-for`**  
  Pour générer dynamiquement la liste des tâches.

---

## 4. Bonnes pratiques et remarques

- **Initialisation de `newTodo`**  
  Corrige la ligne suivante pour éviter un bug :
  ````js
  // filepath: /src/App.vue
  const newTodo = ref('') // au lieu de ref([])
  ````

- **Ajout de tâche : date**  
  Corrige l’ajout de la date pour qu’elle soit bien dynamique :
  ````js
  // filepath: /src/App.vue
  date: Date.now() // au lieu de Date.now
  ````

---

## 5. Mémo rapide sur les fonctions et hooks Vue 3

| Fonction         | Utilité principale                                 | Quand l’utiliser ?                                 | Exemple rapide                                      |
|------------------|---------------------------------------------------|----------------------------------------------------|-----------------------------------------------------|
| `ref()`          | Variable réactive (primitif ou objet simple)      | Champs de formulaire, états locaux                 | `const x = ref(0)`                                  |
| `reactive()`     | Objet/array réactif profond                       | Objets complexes, tableaux                         | `const obj = reactive({ a: 1 })`                    |
| `computed()`     | Valeur calculée réactive                          | Filtres, totaux, formattage                        | `const total = computed(() => a.value + b.value)`   |
| `watch()`        | Réagir à un changement de valeur                   | Effets secondaires, API, logs                      | `watch(x, (nv, ov) => { ... })`                     |
| `onMounted()`    | Code à l’initialisation du composant              | Appels API, timers, initialisation JS              | `onMounted(() => { ... })`                          |
| `onUnmounted()`  | Nettoyage avant destruction du composant          | Stopper timers, removeEventListener                | `onUnmounted(() => { ... })`                        |
| `defineProps()`  | Déclarer les props reçues                         | Composants enfants                                 | `const props = defineProps(['label'])`              |
| `defineEmits()`  | Déclarer les événements émis                      | Composants enfants                                 | `const emit = defineEmits(['check'])`               |
| `defineModel()`  | Créer un v-model personnalisé                     | Composants contrôlés (Checkbox, Input custom)      | `const model = defineModel()`                       |

---

## 6. Exemples d’utilisation dans App.vue

- **Ajout d’une tâche**  
  ````js
  const addTodo = () => {
    todos.value.push({
      title: newTodo.value,
      completed: false,
      date: Date.now()
    })
    newTodo.value = '';
  }
  ````

- **Tri et filtrage des tâches**  
  ````js
  const sortedTodo = computed(() => {
    const sorted = todos.value.toSorted((a, b) => a.completed > b.completed ? 1 : -1)
    return hideCompleted.value ? sorted.filter(t => !t.completed) : sorted
  })
  ````

---

## 7. À retenir

- Utilise toujours `.value` pour accéder/modifier un `ref` dans le script.
- Privilégie `computed` pour les valeurs dérivées, évite les fonctions dans le template.
- Les hooks (`onMounted`, etc.) sont à utiliser dans `<script setup>`.
- Les slots nommés permettent une grande flexibilité de layout.

---

**Astuce** :  
Garde ce document dans ton projet (`SUMMARY.md` ou `VUE_API.md`) pour retrouver rapidement la signification et l’usage de chaque fonction ou concept Vue 3 utilisé dans tes fichiers principaux.

---

Si tu veux un format spécifique (tableau, liste, etc.) ou un focus sur d’autres fichiers, précise-le !

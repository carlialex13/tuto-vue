<template>

<form action="" @submit.prevent="addTodo">
  <fieldset role="group">
    <input
      v-model="newTodo"
      type="text" 
      placeholder="Tache a effectuer"
    >
    <button :disabled="newTodo.length === 0">Ajouter</button>
  </fieldset>
</form>
<div v-if="todos.length === 0">Vous n'avez pas de tache</div>

<div v-else>
  <ul>
    <li
      :key="todo.date"
      v-for="todo in sortedTodo"
      :class="{completed: todo.completed}"
    >
      <label>
        <input type="checkbox" v-model="todo.completed">
      </label>
      {{ todo.title }}
    </li>
  </ul>
  <label>
    <input type="checkbox" v-model="hideCompleted"> Masquer les taches terminées
  </label>
</div>
<div v-if="remainingTodos > 0">
  {{ remainingTodos}} tâche{{ remainingTodos > 1 ? 's' : ''}} à réaliser
</div>

  <Checkbox label="bonjour"/>
</template>

<script setup>
import {computed, ref} from 'vue';
import Checkbox from "@/Checkbox.vue";

const hideCompleted = ref(false)
const todos = ref([{
      title: 'Tache de test',
      completed: true,
      date: 1
  },{
      title: 'Tache à faire',
      completed: false,
      date: 2
  }
])

const newTodo = ref([])

const addTodo = () => {
  todos.value.push({
    title: newTodo.value,
    completed: false,
    date: Date.now
  })
  newTodo.value = '';
}

const remainingTodos = computed(() => {
  return todos.value.filter( t => t.completed === false).length
})

// Ne doit pas $etre utilise car call a chaque modification de la page, exemple, a chaque fois que l'user tape un caractere dans l'input, la fonction est call
// const sortedTodo = () => {
//   const sortedTodo = todos.value.toSorted( (a,b) => a.completed > b.completed ? 1 : -1 )
//
//   if(hideCompleted.value === true){
//     return sortedTodo.filter(t => t.completed === false)
//   }
//   return sortedTodo
// }

const sortedTodo = computed( () => {
  const sortedTodo = todos.value.toSorted( (a,b) => a.completed > b.completed ? 1 : -1 )

  if(hideCompleted.value === true){
    return sortedTodo.filter(t => t.completed === false)
  }
  return sortedTodo
})
</script>


<style>
.completed {
  opacity: .5;
  text-decoration: line-through;
}
</style>

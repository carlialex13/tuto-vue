<template>
  <!-- v-bind:id="`${}`" Exemple pour modifier a la volé un ID ou un autre attribut-->
  <!-- <p 
  :class="{active: count > 5}"
  :style="{color: count > 5 ? 'red' : 'green'}" 
  v-bind:id="`p-${count}`"
  >
  Compteur : {{ count }} 
  </p>

  <div v-html="firstName"></div>

  <div v-show="count >= 5">Bravo vous avez clique plus de 5 fois</div>

  <!-- v-if supprime l'element du DOM -->
  <!--<div v-if="count >= 5">Bravo vous avez clique plus de 5 fois</div>
  <div v-else="count < 5">Vous avez clique moins de 5 fois</div>

  <button @click="increment">Incrementer</button>
  <button @click="decrement">Décrémenter</button>
  <hr>
  <button @click="sortMovies">Reorganiser</button>
  <form action="" @submit.prevent="addMovie">
      <input type="text" placeholder="Nouveau film" v-model="movieName">
      <button>Ajouter</button>
  </form>

  <ul>
    <li 
    v-for="movie in movies"
    :key="movie"
    >
      {{ movie }} <button @click="deleteMovie(movie)">Supprimer</button>
    </li>
  </ul> -->

  <!-- <ul>
    <li>{{ person.firstname }}</li>
    <li>{{ person.lastname }}</li>
    <li>{{ person.age }}</li>
  </ul>
<button @click.prevent="randomAge">Change age</button> -->

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
      v-for="todo in sortedTodo()"
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

</template>

<script setup>
import { ref } from 'vue';

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
  newTodo.value = ''
}

const sortedTodo = () => {
  const sortedTodo = todos.value.toSorted( (a,b) => a.completed > b.completed ? 1 : -1 )

  if(hideCompleted.value === true){
    return sortedTodo.filter(t => t.completed === false)
  }
  return sortedTodo
}
// const person = ref({
//   firstname: 'John',
//   lastname: 'Doe',
//   age: 20
// })

// const randomAge = () => {
//   person.value.age = Math.round(Math.random() * 100)
// }

  // const firstName = '<span>Alex</span>'

  // const count = ref(0)
  // const increment = () => {
  //   count.value++
  // }

  // const decrement = () => {
  //   count.value--
  // }

  // const movieName = ref('')

  // const movies = ref([
  //   'Matrix',
  //   'Lilo & Stich',
  //   'Titanic'
  // ])
  
  // const deleteMovie = (movie) => {
  //   movies.value = movies.value.filter( m => m !== movie)
  // }

  // const addMovie = () => {
  //   movies.value.push(movieName.value)
  //   movieName.value = ''
  // }

  // const sortMovies = () => {
  //   movies.value.sort((a,b) => a > b ? 1 : -1)
  // }
  
</script>


<style>
.completed {
  opacity: .5;
  text-decoration: line-through;
}
</style>

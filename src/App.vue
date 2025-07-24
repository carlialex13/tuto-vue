<template>

  <input type="text" v-model="page.title">
  Temps ecoulé : {{  time }}

  <button @click="reset">Reset</button>

</template>

<script setup>
import { ref, watch, watchEffect } from 'vue';
import {useTimer} from './composable/userTimer.js';

const page = ref({
  title: ''
});

// watch( () => page.value.title, (newValue, oldValue) => {
//   document.title = newValue
// }, { immediate: true });


watchEffect(() => {
  document.title = page.value.title;
});

const { time, reset } = useTimer()
</script>
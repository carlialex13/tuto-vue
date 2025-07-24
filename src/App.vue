<template>

  <input type="text" v-model="name">

</template>

<script setup>
import { ref } from 'vue';

const name = ref('');

watch(name, (newValue, oldValue) => {
  document.title = newValue
})
</script>
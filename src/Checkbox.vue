<script setup>
const props = defineProps({
  label: String
})

console.log(props.label)
</script>

<template>
  <label>
    <input type="text"> Lorem ipsum
  </label>
</template>

<style scoped>

</style>
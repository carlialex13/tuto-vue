<template>
  <label>
    <!-- <input type="checkbox" @change="onChange"> {{ label }} -->
    <input type="checkbox" v-model="model"> {{ label }}
  </label>
</template>

<script setup>
const props = defineProps({
  label: String
})

const emit = defineEmits(['check', 'uncheck'])

const onChange = (event) => {
  if(event.currentTarget.checked){
    emit('check', event.currentTarget)
  } else {
    emit('uncheck', event.currentTarget)
  }
}

const model = defineModel()
</script>

<style scoped>


</style>
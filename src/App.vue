<template>
  <div>
    <tarea-component/>
  </div>
</template>

<script>
import TareaComponent  from './components/Tarea.vue'

export default {
  name: 'App',
  components: {
    'tarea-component': TareaComponent
  }
}
</script>

<style scoped>

</style>

<template>
  <div class="bg-auto  h-screen flex justify-center items-center  bg-gradient-to-r from-cyan-400 to-blue-500">
    <ToDoList />
  </div>
</template>

<script>
import ToDoList from './components/ToDoList.vue'

export default {
  name: 'app',
  components: {
    ToDoList
  }
}
</script>
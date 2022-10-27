<template>
  <div class="bg-auto  h-screen flex justify-center items-center"
    style="background-image: url('./images/bg-pastel.jpg')">
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
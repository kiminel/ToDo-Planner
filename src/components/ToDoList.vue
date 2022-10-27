<template>
  <div class="bg-white bg-opacity-60 rounded-3xl p-6 w-96 space-y-4">
    <div class=" flex justify-center">
      <p class="font-medium">TO-DO LIST:</p>
    </div>
    <input type="text" class="block mb-2 text-sm font-medium text-gray-900 bg-white w-full p-2 rounded-2xl pl-3"
      placeholder="Add a new task" v-model="todoInput" @keydown.enter="addTodo" />
    <ul class="space-y-2">
      <ToDo v-for="(todo, index) in todos" :key="index" :todo="todo" @delete="deleteToDo" />
    </ul>

  </div>
</template>

<script>
import ToDo from './ToDo.vue'

export default {
  name: 'ToDoList',
  components: {
    ToDo
  },
  data() {
    return {
      todoInput: '',
      todos: [
        { name: "Learn basic vue.js", done: true },
        { name: "Add Tailwind", done: true },
        { name: "Update README", done: false },
      ],
    }
  },
  methods: {
    addTodo() {
      this.todoInput.trim() === '' ? '' : this.todos.push({ name: this.todoInput, done: false })
      this.todoInput = ''
    },
    deleteToDo(index) {
      this.todos.splice(index, 1)
    }
  }
}
</script>
<template>
  <div class="container flex items-center justify-center bg-teal-lightest font-sans w-full">
    <div class="bg-white rounded shadow p-6 m-4 w-full lg:w-3/4 lg:max-w-lg">
      <div class="mb-4">
        <h1 class="text-gray-900 font-bold text-2xl">Todo List</h1>
        <div class="flex mt-4">
          <input
              v-model.trim="newTodo"
              class="shadow appearance-none border rounded w-full py-2 px-3 mr-4 text-grey-800"
              placeholder="Add Todo"
              @keyup.enter="AddNewTodo">
          <button
              class="flex-no-shrink p-2 border-2 rounded text-teal-500 border-teal-500 hover:text-white hover:bg-teal-500"
              @click="AddNewTodo">
            Add
          </button>
        </div>
      </div>
      <div>
        <div v-if="todos.length === 0">
          <p class="text-gray-900 font-bold text-l">To-do list is empty. Add a new to-do</p>
        </div>

        <todo-list
            v-for="todo in todos"
            :key="todo"
            :todos="todo"
            @remove-todo="deleteTodo"
        />

      </div>
    </div>
  </div>
</template>

<script>
import TodoList from "@/components/TodoList";

export default {
  components: {TodoList},
  data() {
    return {
      todos: ['Buy products', 'Go to the cinema', 'Do homework'],
      newTodo: '',
    }
  },
  methods: {
    AddNewTodo() {
      if (this.newTodo.length > 0) {
        this.todos.push(this.newTodo)
        this.newTodo = ''
      }
    },
    deleteTodo(index) {
      this.todos.splice(index, 1)
    }
  },

}
</script>

<style scoped>
.list-item {
  display: inline-block;
  margin-right: 10px;
}

.list-enter-active,
.list-leave-active {
  transition: all 1s ease;
}

.list-enter-from,
.list-leave-to {
  opacity: 0;
  transform: translateY(30px);
}
</style>
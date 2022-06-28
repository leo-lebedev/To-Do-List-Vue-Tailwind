<template>
  <div class="flex mb-4 items-center">
    <p :class="doneClass">
      {{ todos }}
    </p>
    <button
        class="flex-no-shrink p-2 ml-4 mr-2 border-2 rounded hover:text-white text-green-500 border-green-500 hover:bg-green-500"
        @click="todoDone">
      Done
    </button>
    <button
        class="flex-no-shrink p-2 ml-2 border-2 rounded text-red-500 border-red-500 hover:text-white hover:bg-red-500"
        @click="$emit('removeTodo')">
      Remove
    </button>
  </div>
</template>

<script>
export default {
  name: "TodoList",
  props: ['todos'],
  emit: [],
  data() {
    return {
      done: false,
    }
  },
  methods: {
    todoDone() {
      this.done = !this.done;
    },
  },
  computed: {
    doneClass() {
      if (this.done) {
        return 'w-full line-through text-green-500'
      }
      return 'w-full text-grey-darkest'
    }
  },
}
</script>

<style scoped>

</style>
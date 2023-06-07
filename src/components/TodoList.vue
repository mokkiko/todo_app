<template>
  <div v-if="todos.length > 0">
    <h2 style="color:darkblue"> Спиcoк постов </h2>
    <todo-item 
      v-for="todo in todos" 
      :key="todo.id" 
      :todo="todo"
      @remove="$emit('remove', todo)"/>
  </div>
  <h2 v-else style="color:darkred"> Task list emtpy!!!</h2>
</template>

<script>
import TodoItem from "@/components/TodoItem";

export default {
  components: {TodoItem},
  props: {
    todos: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style scoped>

</style>

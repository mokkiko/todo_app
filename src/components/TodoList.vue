<template>
  <div v-if="todos.length > 0">
    <h2 style="color:darkblue"> ToDo list </h2>
    <transition-group name="todo-list">
      <todo-item 
      v-for="todo in todos" 
      :key="todo.id" 
      :todo="todo"
      @remove="$emit('remove', todo)"/>
    </transition-group>
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
.todo-list-item {
  display: inline-block;
  margin-right: 10px;
}
.todo-list-enter-active,
.todo-list-leave-active {
  transition: all 0.41s ease;
}
.todo-list-enter-from,
.todo-list-leave-to {
  opacity: 0;
  transform: translateX(30px);
}
.todo-list-move {
  transition: transform 0.8s ease;
}

</style>

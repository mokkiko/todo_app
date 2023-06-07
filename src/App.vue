<template>
  <div class="app">
    <h1 style="color:darkblue ">MY TODO</h1>
    <my-button
      @click="showDialog"
    >
      Сreate ToDo task
    </my-button>
    <my-dialog v-model:show="dialogVisible">
      <todo-form 
        @create = "createTodo"
      />
    </my-dialog>

    <todo-list 
      :todos="todos" 
      @remove="removeTodo"
    />
  </div>
</template>

<script>
import TodoForm from "@/components/TodoForm";
import TodoList from "@/components/TodoList";

export default {
  components: {
    TodoForm,
    TodoList,
  },
  data() {
    return {
      todos: [
        { id: 1, title: "open eyes", description: "We need to open our eyes))", priority_level: 3 },
        { id: 2, title: "get up from bed", description: "The early bird that catches the worm.", priority_level: 3},
        { id: 3, title: "wash up", description: "New day, fresh and cheerful", priority_level: 2},
        { id: 4, title: "make breakfest", description: "something delicious with a cup of coffee ", priority_level: 2},
      ],
      dialogVisible: false

    };
  },

  methods: {
    createTodo(todo) {
      this.todos.push(todo);
      this.dialogVisible = false;
    },
    removeTodo(todo) {
      this.todos = this.todos.filter(p => p.id !== todo.id)
    },
    showDialog() {
      this.dialogVisible = true;
    }
  }
}

</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Roboto', Verdana, Geneva, Tahoma, sans-serif;
  word-spacing: 5px;
}

.app {
  padding: 20px;
}


</style>

<template>
  <div class="app">
    <h1 style="color:darkblue ">Base ToDo list already here... You can add some task if you need!</h1>
    <my-input
      v-model="searchQuery"
      placeholder="filter your todos"
      />

    <div class="nav__buttonts">
      <my-button
      @click="showDialog"
      >
      Create ToDo task
      </my-button>
      <my-select 
      v-model="selectedSort" 
      :options="sortOptions"/>

    </div>

    <my-dialog v-model:show="dialogVisible">
      <todo-form 
        @create = "createTodo"
      />
    </my-dialog>

    <todo-list 
      :todos="sortedAndSearchedTodos" 
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
        { id: 1, title: "open eyes", description: "We need to open our eyes))", priority_level: '3' },
        { id: 2, title: "get up from bed", description: "The early bird that catches the worm.", priority_level: '2'},
        { id: 3, title: "wash up", description: "New day, fresh and cheerful", priority_level: '3'},
        { id: 4, title: "make breakfest", description: "something delicious with a cup of coffee ", priority_level: '2'},
        { id: 5, title: "watch news", description: "something really worthless", priority_level: '1'},
        { id: 6, title: "get update", description: "update your phine app", priority_level: '1'},
      ],
      dialogVisible: false,
      selectedSort: '',
      searchQuery: '',
      sortOptions:[
        {value: 'title', name: 'By name'},
        {value: 'priority_level', name: 'By priority'},     
      ]

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
    },

    
  },
  watch: {

  },
  computed:{
    sortedTodos() {
      return [...this.todos].sort((todo1, todo2) => todo1[this.selectedSort]?.localeCompare(todo2[this.selectedSort]))
    },
    sortedAndSearchedTodos() {
      return this.sortedTodos.filter(todo => todo.title.toLowerCase().includes(this.searchQuery.toLowerCase()) || todo.description.toLowerCase().includes(this.searchQuery.toLowerCase()))
    },

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

.nav__buttonts {
  display: flex;
  justify-content: space-between;
}
</style>

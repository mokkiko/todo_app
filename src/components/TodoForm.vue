<template>
  <form @submit.prevent>
    <h3>Add ToDo</h3>
    <my-input
      v-model="todo.title"
      type="text"
      placeholder="Название"
    />
    <my-input
      v-model="todo.description"
      type="text"
      placeholder="Описание"
    />
    <my-input
      v-model="todo.priority_level"
      type="integer"
      placeholder="priority from 1..3"
    />
    <my-button 
      class="btn" 
      @click="createtodo"
    >
      Create
    </my-button>
  </form>


</template>

<script>

  export default {
    data() {
      return {
        todo: {
          title: '',
          description: '',    
        }
      }
    },
    methods: {
      createtodo() {
        this.todo.id = Date.now();
        this.$emit('create', this.todo)
        this.todo = {
          title: '',
          description: '', 
        }  
      }
    }
  }
</script>

<style scoped>

form {
  display: flex;
  flex-direction: column;
}

</style>

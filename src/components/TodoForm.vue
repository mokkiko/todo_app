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

    <select 
    v-model="todo.priority_level"
    placeholder="Описание"
    >
      <option disabled value="">priority task level</option>
      <option
        v-for="priorityOption in priorityOptions"
        :key="priorityOption.value"
        :value="priorityOption.value"
      >
        {{ priorityOption.value }}
      </option>
     </select>


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
        },
        priorityOptions:[
          {value: '1'},
          {value: '2'},     
          {value: '3'},   
        ]
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

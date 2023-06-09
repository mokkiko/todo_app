<template>
  <div class="todo">
    <div>
      <div><strong>Title  </strong>{{ todo.title }}</div>
      <div><strong>Description  </strong>{{ todo.description }}</div>
    </div>
    <div 
      :class ="{
        'red_priority': todo.priority_level === '3',
        'green_priority': todo.priority_level === '1',       
      }"
    >
        <my-priority-block>
          Priority = 
        {{ todo.priority_level }}
        </my-priority-block>
    </div>
    <div class="todo_btn">
      <my-button
        @click="$emit('remove', todo)"
      >
      Удалить</my-button>
    </div>
  </div>
</template>

<script>

  export default {
    props: {
      todo: {
        type: Object,
        required: true,
      }
    }
  }

</script>

<style scoped>
.todo {
  border: 2px solid green;
  padding: 10px;
  margin: 4px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  border-radius: 8px;
}

.red_priority {
  border : 2px solid salmon;
  border-radius: 8px;
}
.green_priority {
  border : 2px solid rgb(120, 214, 101);
  border-radius: 8px;
}
</style>



<template>
  <div class="todo">
    <div>
      <div><strong>Title  </strong>{{ todo.title }}</div>
      <div><strong>Description  </strong>{{ todo.description }}</div>
    </div>
    <div>
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
  padding: 10px 10px;
  margin: 4px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  border-radius: 8px;
}

</style>



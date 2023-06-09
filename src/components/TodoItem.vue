<template>

  <div class="todo">
    <div class="row">
      <div class="col-7">
        <div>
          <div><strong>Title  </strong>{{ todo.title }}</div>
          <div><strong>Description  </strong>{{ todo.description }}</div>
        </div>
      </div>
      <div class="col-1">
        <div 
          :class ="{
            'red_priority': todo.priority_level === '3',
            'green_priority': todo.priority_level === '1',       
          }">
            <my-priority-block>
              Priority = 
            {{ todo.priority_level }}
          </my-priority-block>
        </div>
      </div>
      <div class="col-3"></div>
      <div class="col-1">
          <div>
            <my-button
              @click="$emit('remove', todo)">
            Удалить</my-button>
          </div>
        </div>
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
  margin: 8px;
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



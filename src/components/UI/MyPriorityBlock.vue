<template>
  <button class="priority__block">
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: 'my-priority-block',
  props: {
      todo: {
        type: Object,
        required: true,
      }
    }
}
</script>

<style scoped>

.priority__block {
  margin: 4px;
  align-self: flex-end;
  padding: 16px 16px;
  background: none;
  color: rgb(89, 5, 138);
  border-radius: 8px;
}



</style>

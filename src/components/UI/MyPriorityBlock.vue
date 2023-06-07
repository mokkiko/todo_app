<template>
  <button class="priority__block">
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: 'my-priority-block'
}
</script>

<style scoped>

.priority__block {
  margin-top: 8px;
  align-self: flex-end;
  padding: 16px 16px;
  background: none;
  color: rgb(89, 5, 138);
  border: 1px solid rgb(78, 113, 179);
  border-radius: 4px;
}

</style>

<template>
  <button class="btn">
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: 'my-button'
}
</script>

<style scoped>

.btn {
  margin-top: 8px;
  align-self: flex-end;
  padding: 16px 16px;
  background: none;
  color: rgb(89, 5, 138);
  border: 1px solid rgb(78, 113, 179);
  border-radius: 4px;
}
.btn:hover {
  background-color: rgb(0, 90, 60);
  color: aliceblue;
}

</style>

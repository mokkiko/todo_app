<template>
  <select :value="modelValue" @change="changeOption" class="search_field">
    <option disabled value="">Choose sort type</option>
    <option
      v-for="option in options"
      :key="option.value"
      :value="option.value"
    >
      {{ option.name }}
    </option>
  </select>
</template>

<script>
export default {
  name: 'my-select',
  props: {
    modelValue: {
      type: String
    },
    options: {
      type: Array,
      default: () => []
    }
  },
  methods: {
    changeOption(event) {
      this.$emit('update:modelValue', event.target.value);
    }
  }
}
</script>

<style scoped>

.search_field {
  margin: 8px; 
  border-radius: 4px;
  background-color: rgb(255, 255, 255);
  border: 1px solid rgb(78, 113, 179);
}
</style>
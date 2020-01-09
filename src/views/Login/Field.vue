<template>
  <label>
    <input v-bind:value="value" v-on:input="$emit('input', $event.target.value)" :type="type"
           :placeholder="placeholder">
  </label>
</template>

<script>
export default {
  name: "Field",
  props: {
    type: {
      default: 'text',
    },
    placeholder: {
      default: '',
    },
    value: String,
  }
}
</script>

<style lang="scss" scoped>
  input {
    background: none;
    display: block;
    margin: 20px auto;
    text-align: center;
    border: 2px solid #3498db;
    padding: 14px 10px;
    width: 200px;
    outline: none;
    color: white;
    border-radius: 24px;
    transition: 0.25s;

    &:focus {
      width: 280px;
      border-color: #2ecc71;
    }
  }
</style>

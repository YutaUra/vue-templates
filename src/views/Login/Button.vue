<template>
  <input :style="style" type="submit" :value="value">
</template>

<script>
export default {
  name: "Field",
  props: {
    value: {
      default: '',
    },
    valid: {
      default: null,
    }
  },
  computed: {
    color () {
      if (this.valid == null) {
        return '#3498db'
      } else {
        return this.valid ?
          '#2ecc71' :
          '#CC191D'
      }
    },
    style () {
      return {
        '--color': this.color,
        '--border': `2px solid ${this.color}`,
      }
    }
  }
}
</script>

<style lang="scss" scoped>
  input {
    background: none;
    display: block;
    margin: 20px auto;
    text-align: center;
    border: var(--border);
    padding: 14px 40px;
    outline: none;
    color: white;
    border-radius: 24px;
    transition: 0.25s;
    cursor: pointer;

    &:hover {
      background: var(--color);
    }
  }
</style>

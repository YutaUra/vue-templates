<template>
  <div class="home">
    <h1 id="title">Templates</h1>
    <Link v-for="link in links" :to="link.to" :label="link.label" :key="link.key"/>
  </div>
</template>

<script>
import Link from './Link'

export default {
  name: 'home',
  components: {
    Link,
  },
  data () {
    return {
      links: [
        {to: {name: 'login'}, label: 'Login', key: 'login'},
      ]
    }
  }
}
</script>

<style lang="scss" scoped>
  .home {
    background-color: #2ecc71;
  }

  h1 {
    text-align: center;

    &#title {
      margin-top: 40px;
    }
  }
</style>

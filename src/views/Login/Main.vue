<template>
  <div>
    <!--  This Program is affected by https://www.youtube.com/watch?v=HV7DtH3J2PU, the author is https://www.youtube.com/channel/UCD3KVjbb7aq2OiOffuungzw  -->
    <form class="login-form" action="" method="GET">
      <h1>Login</h1>
      <Field v-model="username" type="text" placeholder="Username"/>
      <Field v-model="password" type="password" placeholder="Password"/>
      <Button value="Login" :valid="valid"/>
    </form>
  </div>

</template>

<script lang="ts">
import Field from './Field.vue'
import Button from './Button.vue'

export default {
    name: "Login",
    components: {
        Field,
        Button,
    },
    data() {
        return {
            username: '',
            password: '',
            valid: null,
        }
    },
}
</script>

<style lang="scss" scoped>
  div {
    width: 100vw;
    height: 100vh;
    font-family: sans-serif;
    background: #34495e;
  }

  .login-form {
    width: 300px;
    padding: 40px;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background: #191919;
    text-align: center;

    h1 {
      color: white;
      text-transform: uppercase;
      font-weight: 500;
    }
  }
</style>

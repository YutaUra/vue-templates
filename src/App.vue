<template>
  <div id="app">
    <div id="arrow" @click="toggleArrow">
      <div :class="arrowClass"></div>
    </div>
    <transition>
      <div id="nav" v-if="isNavHidden">
        <router-link class="link" to="/">Home</router-link>
        <router-link class="link" to="/login">Login</router-link>
      </div>
    </transition>
    <router-view class="page"/>
  </div>
</template>

<script>
export default {
  data () {
    return {
      arrowClass: 'up',
      isMoving: false,
    }
  },
  computed: {
    isNavHidden () {
      return this.arrowClass !== 'down';
    }
  },
  methods: {
    toggleArrow () {
      if (this.arrowClass === 'up') {
        this.arrowClass = 'down'
      } else {
        this.arrowClass = 'up'
      }
    },
  }
}
</script>


<style lang="scss">
  body {
    margin: 0;
  }

  #arrow {
    background-color: rgba(80, 80, 80, 0.2);
    border-radius: 50%;
    display: inline-block;
    width: 30px;
    height: 30px;
    position: fixed;
    transition-duration: 0.3s;
    top: 0;
    left: 15%;
    z-index: 2;

    &:hover {
      transform: scale(1.2);
    }

    div {
      position: absolute;
      width: 15px;
      height: 15px;
      border-top: solid 3px #697b91;
      border-right: solid 3px #697b91;
      transition-duration: 0.5s;
      top: 50%;
      left: 50%;

      &.up {
        -webkit-transform: translate(-50%, -50%) rotate(-45deg);
        transform: translate(-50%, -50%) rotate(-45deg);
      }

      &.down {
        -webkit-transform: translate(-50%, -50%) rotate(135deg);
        transform: translate(-50%, -50%) rotate(135deg);
      }
    }
  }

  #nav {
    display: inline-block;
    position: fixed;
    height: 30px;
    top: 0;
    left: 20%;
    margin: 4px 0;
    z-index: 2;


    .link {
      text-decoration: none;
      color: black;

      &:nth-child(1n+2) {
        &:before {
          content: " | ";
        }
      }
    }

    &.v-enter, &.v-leave-to {
      /*非表示*/
      opacity: 0;
      transform: translateY(-30px);
    }

    &.v-enter-to, &.v-leave {
      opacity: 1;
    }

    &.v-enter-active, &.v-leave-active {
      /*表示中*/
      transition: all 500ms;
    }
  }

  .page {
    position: absolute;
    width: 100vw;
    height: 100vh;
  }
</style>

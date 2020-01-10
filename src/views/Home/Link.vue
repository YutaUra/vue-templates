<template>
  <div class="root">
    <div class="link">
      <div class="link-text">
        {{ label }}
      </div>
      <div class="frame-view">
        <iframe frameborder="no" scrolling="no" :src="fullPath" height="500px"/>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Link',
  props: {
    to: {
      required: true,
      type: [String, Object],
    },
    label: {
      required: true,
      type: String,
    }
  },
  data () {
    return {
      frameShow: true,
    }
  },
  computed: {
    fullPath () {
      return this.$router.resolve(this.to).href
    }
  },
  methods: {
    mouseOver () {
      this.frameShow = true
    },
    mouseLeave () {
      // this.frameShow = false
    }
  }
}
</script>

<style lang="scss" scoped>

  $transition-sec: 0.5s;

  .root {
    text-align: center;
    position: relative;
    height: 80px;

  }

  .link {
    width: 250px;
    height: 60px;
    background-color: #3498db;
    border: 2px solid #42b983;
    border-radius: 30px;
    cursor: pointer;
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    margin: 10px auto auto;
    transition-duration: $transition-sec;
    pointer-events: none;

    &:hover {
      right: 250px;
    }


    .link-text {
      font-weight: bold;
      font-size: 30px;
      text-decoration: none;
      width: 100%;
      height: 100%;
      border-radius: 30px;
      pointer-events: auto;


      &:hover + .frame-view {
        opacity: 0.9;

        iframe {
          width: initial;
        }
      }

    }
  }

  .frame-view {
    border-radius: 8px;
    position: relative;
    top: 0;
    right: 0;
    bottom: 0;
    left: 30px;
    width: 0;
    transform: translate(250px, -60px);
    opacity: 0;
    transition-duration: $transition-sec;
    z-index: 1;

    iframe {
      width: 0;
    }

    &:after {
      border-right: 20px solid black;
      border-top: 10px solid transparent;
      border-bottom: 10px solid transparent;
      left: -20px;
      top: 30px;
      content: "";
      position: absolute;
    }
  }

  @media screen and (max-width: 400px) {
    .link {
      width: 100px;

      &:hover {
        right: 0;
        left: -250px;
      }
    }
    .frame-view {
      transform: translate(100px, -60px);
    }
  }

</style>

<template>
  <div id="app">
   <Demo :active="active"/>
  </div>
</template>

<script>
import Demo from '@/pages/demo'
import Swiper from 'swiper'
export default {
  name: 'app',
  components: {
    Demo
  },
  data () {
    return {
      active: ''
    }
  },
  methods: {
    InitSwiper () {
      let that = this
      let mySwiper = new Swiper('.swiper-container', {
        direction: 'vertical',
        autoplay: true,
        // loop: true,
        effect: 'coverflow',
        height: window.innerHeight,
        width: window.innerWidth,
        on: {
          resize () {
            this.params.width = window.innerWidth
            this.params.height = window.innerHeight
            this.update()
          },
          slideChange () {
            that.active = this.activeIndex
          }
        }
      })
    }
  },
  mounted () {
    this.InitSwiper()
  }
}
</script>

<style>
@import url('../node_modules/swiper/dist/css/swiper.min.css');
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
body{
  margin: 0;
}
</style>

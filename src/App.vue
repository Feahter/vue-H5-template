<template>
  <div id="app">
    <!-- loading -->
    <transition
    appear
    enter-active-class="animated fadeIn"
    leave-active-class="animated fadeOut"
    appear-class="animated swing"
    :duration="3000">
    <Loading v-if="showload"/>
      </transition>
   <Demo :active="active" />
<Arrow v-if="showarrow"/>
  </div>
</template>

<script>
import Loading from '@/components/loading'
import Arrow from '@/components/arrow'
import Demo from '@/pages/demo'
import Swiper from 'swiper'
export default {
  name: 'app',
  components: {
    Loading,
    Arrow,
    Demo
  },
  data () {
    return {
      showload: true,
      showarrow: true,
      active: ''
    }
  },
  methods: {
    InitSwiper () {
      let that = this
      let mySwiper = new Swiper('.swiper-container', {
        direction: 'vertical',
        // autoplay: true,
        // loop: true,
        effect: 'coverflow',
        height: window.innerHeight,
        width: window.innerWidth,
        on: {
          init () {
            setTimeout(() => { that.showload = false }, 1000)
          },
          resize () {
            this.params.width = window.innerWidth
            this.params.height = window.innerHeight
            this.update()
          },
          slideChange () {
            that.active = this.activeIndex
            if (this.activeIndex) {
              that.showarrow = false
            }else {
              that.showarrow = true
            }
          }
        }
      })
    }
  },
  mounted () {
    let that = this
    that.InitSwiper()
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
button:focus,i:focus{
    outline: none;
}
</style>

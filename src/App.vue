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
    each (object, callback) {
      let type = (function () {
        switch (object.constructor) {
          case Object:
            return 'Object'
            break
          case Array:
            return 'Array'
            break
          case NodeList:
            return 'NodeList'
            break
          default:
            return 'null'
            break
        }
      })()
      if (type === 'Array' || type === 'NodeList') {
        [].every.call(
          object, function (v, i) {
            return callback.call(v, i, v) !== false
          })
      } else if (type === 'Object') {
        for (var i in object) {
          if (callback.call(object[i], i, object[i]) === false) {
            break
          }
        }
      }
    },
    initAnimationItems () {
      let that = this
      let items = document.querySelectorAll('.swiper-container .animated')
      that.each(items, (i, e) => {
        let name = e.getAttribute('data-name')
        let duration = e.getAttribute('data-duration')
        let delay = e.getAttribute('data-delay')
        e.classList.add(name)
        e.style.visibility = 'hidden'
        e.style.transitionDuration = duration
        e.style.transitionDelay = delay
        // console.log(val.style, name, duration, delay)
      })
    },
    playAnimation (swiper) {
      let that = this
      that.clearAnimation()
      let items = swiper.slides[swiper.activeIndex].querySelectorAll('.swiper-container .animated')
      that.each(items, (i, e) => {
        let name = e.getAttribute('data-name')
        e.classList.add(name)
        e.style.visibility = 'visible'
      })
    },
    clearAnimation () {
      let that = this
      let items = document.querySelectorAll('.swiper-container .animated')
      that.each(items, (i, e) => {
        let name = e.getAttribute('data-name')
        e.classList.remove(name)
        e.style.visibility = 'hidden'
      })
    },
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
            setTimeout(() => {
              that.showload = false
              that.initAnimationItems()
              that.playAnimation(this)
            }, 500)
          },
          // resize () {
          //   this.params.width = window.innerWidth
          //   this.params.height = window.innerHeight
          //   this.update()
          // },
          transitionEnd () {
            that.playAnimation(this)
          },
          slideChange () {
            that.active = this.activeIndex
            if (this.activeIndex) {
              that.showarrow = false
            } else {
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

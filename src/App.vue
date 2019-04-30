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
          case Array:
            return 'Array'
          case NodeList:
            return 'NodeList'
          default:
            return 'null'
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
        e.style.animationDuration = duration
        e.style.animationDelay = delay
        // console.log(e.style)
      })
    },
    playAnimation (swiper) {
      let that = this
      that.clearAnimation()
      let items = swiper.slides[swiper.activeIndex].querySelectorAll('.swiper-container .animated')
      that.each(items, (i, e) => {
        e.style.visibility = 'visible'
        let old = e.classList.item(2)
        let name = e.getAttribute('data-name')
        if (old) { e.classList.replace(old, name) } else {
          e.classList.add(name)
        }
      })
    },
    clearAnimation () {
      let that = this
      let items = document.querySelectorAll('.swiper-container .animated')
      that.each(items, (i, e) => {
        let old = e.classList.item(2)
        e.style.visibility = 'hidden'
        e.classList.remove(old)
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
              that.initAnimationItems()
              that.showload = false
              that.playAnimation(this)
            }, 800)
          },
          resize () {
            this.params.width = window.innerWidth
            this.params.height = window.innerHeight
            this.update()
          },
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
      console.log(mySwiper)
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

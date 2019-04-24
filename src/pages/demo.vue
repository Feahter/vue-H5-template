<template>
  <!-- Swiper -->
  <div class="swiper-container">
    <div class="swiper-wrapper">
      <div
        class="swiper-slide"
        :style="'background-color:'+nowcolor"
        v-for="(item,index) in 5"
        :key="index"
      >
        <p
          class="item-text animated"
          data-name="slideInLeft"
          data-duration="1s"
          data-delay="0.5s"
        >Slide {{index}}</p>
        <p
          class="item-text animated"
          data-name="slideInLeft"
          data-duration="1s"
          data-delay="0.5s"
        >I'm a coder!</p>
      </div>
      <!-- <div class="swiper-slide" :style="'background-color:'+nowcolor">
        <p class="item-text animated"  data-name="slideInLeft" data-duration="1s" data-delay="0.5s">Slide 1</p>
        <p class="item-text animated" data-name="slideInLeft" data-duration="1s" data-delay="0.5s">I'm a coder!</p>
      </div>
        <div class="swiper-slide" :style="'background-color:'+nowcolor">
        <p class="item-text animated"  data-name="slideInRight" data-duration="1s" data-delay="0.5s">Slide 2</p>
        <p class="item-text animated" data-name="slideInRight" data-duration="1s" data-delay="0.5s">I'm a coder!</p>
      </div>
        <div class="swiper-slide" :style="'background-color:'+nowcolor">
        <p class="item-text animated"  data-name="slideInUp" data-duration="1s" data-delay="0.5s">Slide 3</p>
        <p class="item-text animated" data-name="slideInUp" data-duration="1s" data-delay="0.5s">I'm a coder!</p>
      </div>
      <div class="swiper-slide" :style="'background-color:'+nowcolor">
        <p class="item-text animated"  data-name="slideInDown" data-duration="1s" data-delay="0.5s">Slide 4</p>
        <p class="item-text animated" data-name="slideInDown" data-duration="1s" data-delay="0.5s">I'm a coder!</p>
      </div>-->
    </div>
    <!-- music -->
    <Music/>
  </div>
</template>

<script>
import Music from '../components/music'
export default {
  props: ['active'],
  components: { Music },
  data () {
    return {
      nowcolor: '#000',
      arrClass: [
        'bounce',
        'flash',
        'pulse',
        'rubberBand',
        'shake',
        'headShake',
        'swing',
        'tada',
        'wobble',
        'jello',
        'bounceIn',
        'bounceInDown',
        'bounceInLeft',
        'bounceInRight',
        'bounceInUp',
        'bounceOut',
        'bounceOutDown',
        'bounceOutLeft',
        'bounceOutRight',
        'bounceOutUp',
        'fadeIn',
        'fadeInDown',
        'fadeInDownBig',
        'fadeInLeft',
        'fadeInLeftBig',
        'fadeInRight',
        'fadeInRightBig',
        'fadeInUp',
        'fadeInUpBig',
        'fadeOut',
        'fadeOutDown',
        'fadeOutDownBig',
        'fadeOutLeft',
        'fadeOutLeftBig',
        'fadeOutRight',
        'fadeOutRightBig',
        'fadeOutUp',
        'fadeOutUpBig',
        'flipInX',
        'flipInY',
        'flipOutX',
        'flipOutY',
        'lightSpeedIn',
        'lightSpeedOut',
        'rotateIn',
        'rotateInDownLeft',
        'rotateInDownRight',
        'rotateInUpLeft',
        'rotateInUpRight',
        'rotateOut',
        'rotateOutDownLeft',
        'rotateOutDownRight',
        'rotateOutUpLeft',
        'rotateOutUpRight',
        'hinge',
        'jackInTheBox',
        'rollIn',
        'rollOut',
        'zoomIn',
        'zoomInDown',
        'zoomInLeft',
        'zoomInRight',
        'zoomInUp',
        'zoomOut',
        'zoomOutDown',
        'zoomOutLeft',
        'zoomOutRight',
        'zoomOutUp',
        'slideInDown',
        'slideInLeft',
        'slideInRight',
        'slideInUp',
        'slideOutDown',
        'slideOutLeft',
        'slideOutRight',
        'slideOutUp',
        'heartBeat'
      ]
    }
  },
  methods: {
    getColor () {
      return '#' + Math.floor(Math.random() * 0xffffff).toString(16)
    },
    getAnimate () {
      console.log(111)
    }
  },
  watch: {
    active (cur, old) {
      let that = this
      if (cur !== old) {
        that.nowcolor = that.getColor()
      }
    }
  }
}
</script>

<style>
.swiper-container {
  max-height: 100vh;
  overflow: hidden;
}
.swiper-slide {
  display: flex;
  justify-content: center;
  align-items: center;
  color: #fff;
  font-size: 30px;
}
</style>

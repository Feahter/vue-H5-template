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
          :data-name="nowclass"
          data-duration="1s"
          data-delay="0.5s"
        >Slide {{index+1}}</p>
        <div class="item-img animated" :data-name="nowclass" data-duration="1s" data-delay='0s' >
          <img src="../assets/loading.svg" alt="">
        </div>
        <p
          class="item-text animated"
          :data-name="nowclass"
          data-duration="1s"
          data-delay="1s"
        >{{nowclass}} Now!</p>
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
      nowclass: 'rubberBand',
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
        'fadeIn',
        'fadeInDown',
        'fadeInDownBig',
        'fadeInLeft',
        'fadeInLeftBig',
        'fadeInRight',
        'fadeInRightBig',
        'fadeInUp',
        'fadeInUpBig',
        'flip',
        'flipInX',
        'flipInY',
        'lightSpeedIn',
        'rotateIn',
        'rotateInDownLeft',
        'rotateInDownRight',
        'rotateInUpLeft',
        'rotateInUpRight',
        'jackInTheBox',
        'rollIn',
        'zoomIn',
        'zoomInDown',
        'zoomInLeft',
        'zoomInRight',
        'zoomInUp',
        'slideInDown',
        'slideInLeft',
        'slideInRight',
        'slideInUp',
        'heartBeat'
      ],
      outlist: [
        'bounceOut',
        'bounceOutDown',
        'bounceOutLeft',
        'bounceOutRight',
        'bounceOutUp',
        'lightSpeedOut',
        'flipOutX',
        'flipOutY',
        'slideOutDown',
        'slideOutLeft',
        'slideOutRight',
        'slideOutUp',
        'zoomOut',
        'zoomOutDown',
        'zoomOutLeft',
        'zoomOutRight',
        'zoomOutUp', 'rollOut',
        'rotateOut',
        'rotateOutDownLeft',
        'rotateOutDownRight',
        'rotateOutUpLeft',
        'rotateOutUpRight',
        'fadeOut',
        'fadeOutDown',
        'fadeOutDownBig',
        'fadeOutLeft',
        'fadeOutLeftBig',
        'fadeOutRight',
        'fadeOutRightBig',
        'fadeOutUp',
        'fadeOutUpBig',
        'hinge'
      ]
    }
  },
  methods: {
    getColor () {
      return '#' + Math.floor(Math.random() * 0xffffff).toString(16)
    },
    getAnimate () {
      let that = this
      let list = that.arrClass
      let index = Math.floor(Math.random() * list.length)
      return list[index]
    }
  },
  watch: {
    active (cur, old) {
      let that = this
      if (cur !== old) {
        that.nowcolor = that.getColor()
        that.nowclass = that.getAnimate()
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
  flex-flow:column wrap;
}
</style>

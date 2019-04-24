<template>
<!-- Swiper -->
  <div class="swiper-container">
    <div class="swiper-wrapper">
      <div class="swiper-slide" :style="'background-color:'+nowcolor" v-for="(item,index) in 5" :key="index">
          Slide {{index}}
          </div>
    </div>
<Music/>
  </div>
</template>

<script>
import Music from '../components/music'
export default {
  props: [ 'active' ],
  components: { Music },
  data () {
    return {
      nowcolor: ''
    }
  },
  methods: {
    getColor () {
      return '#' + Math.floor(Math.random() * 0xffffff).toString(16)
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
.swiper-container{
  max-height: 100vh;
  overflow:hidden;
}
.swiper-slide{
    display: flex;
    justify-content: center;
    align-items: center;
    color: #fff;
    font-size: 30px;
}
</style>

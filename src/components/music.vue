<template>
<div class="music">
    <button class="btn-music" :class="play?'':'paused'" @click="Toggle">
        <i class="icon-note">M</i>
    </button>
    <audio loop>
    <source src="https://panteng.github.io/wechat-h5-boilerplate/audios/background.mp3" type="audio/mpeg">
</audio>
</div>
</template>

<script>
export default {
  data () {
    return {
      play: true
    }
  },
  mounted () {
    let music = document.querySelector('audio')
    music.play()
  },
  methods: {
    Toggle () {
      let that = this
      let music = document.querySelector('audio')
      if (that.play) {
        music.pause()
      } else {
        music.play()
      }
      that.play = !that.play
    }
  }
}
</script>

<style>
button:focus,i:focus{
    outline: none;
}
.btn-music {
  width: 2rem;
  height: 2rem;
  background-color: transparent;
  position: fixed;
  top: 1.5rem;
  right: 1.5rem;
  z-index: 999;
  border: 0.125rem solid #fff;
  border-radius: 50%;
  padding: 0;
  animation: btnMusicAni 3s infinite linear;
}
.btn-music i {
  width: 2rem;
  height: 2rem;
  text-align: center;
  line-height: 2rem;
  color: #fff;
  font-size: 1rem;
  position: absolute;
  top: -0.125rem;
  left: -0.125rem;
}
.btn-music.paused {
  opacity: 0.4;
  animation-play-state: paused;
}
@keyframes btnMusicAni {
  0% {
    transform: rotate(0deg);
  }

  100% {
    transform: rotate(360deg);
  }
}
</style>

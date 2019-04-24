<template>
    <div class="loading">
    <img :src="imgUrl" alt="">
    </div>
</template>

<script>
export default {
  data () {
    return {
      imgUrl: require('../assets/loading.svg')
    }
  }
}
</script>

<style>
.loading{
    position: fixed;
    width: 100%;
    height: 100%;
    background-color: #000;
    z-index: 9999;
}
.loading img {
        width: 10rem;
        height: 10rem;
        margin: auto;
        position: absolute;
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
    }
</style>

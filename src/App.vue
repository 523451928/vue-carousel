<template>
  <div id="app">
    <carousel :imgArr="imgArr" clientType="mobile">
    </carousel>
    <!--<v-carousel :bannerData="bannerData"></v-carousel>-->
  </div>
</template>

<script>
  import Carousel from './components/Carousel.vue'
  import VCarousel from './components/Vcarousel.vue'
  export default {
    name: 'app',
    data() {
      return {
        imgArr: [
          '../static/bnr-1.jpg',
          '../static/bnr-3.jpg',
          '../static/bnr-4.jpg',
          '../static/bnr-5.jpg',
          '../static/bnr-2.jpg'
        ],
        bannerData: ['../static/bnr-2.jpg','../static/bnr-4.jpg','../static/bnr-1.jpg'],
      }
    },
    components: {
      Carousel,
      VCarousel
    }
  }
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
  }
</style>

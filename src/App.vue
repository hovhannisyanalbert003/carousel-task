<template>
  <div id="app">
    <carousel-component 
      :carouselItems="carouselItems"
    />
  </div>
</template>

<script>
import axios from 'axios'
import CarouselComponent from './components/CarouselComponent.vue'

export default {
  name: 'App',
  components: {
    CarouselComponent
  },
  data() {
    return {
      carouselItems: []
    }
  },
  async mounted() {
    try {
      const { data } = await axios.get('https://api.thecatapi.com/v1/images/search?limit=10');
      this.carouselItems = data;
    } catch(e) {
      console.log(e);
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
  justify-content: center;
}
</style>

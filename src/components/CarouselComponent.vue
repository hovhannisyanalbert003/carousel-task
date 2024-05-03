<template>
  <div>
    <div ref="carousel-container" class="carousel-conatienr">
      <CarouselItem 
        v-for="item in carouselItems"
        :key="`carousel-item-${item.id}`"
        :imgUrl="item.url"
        :width="item.width"
        :height="item.height"
      />
    </div>
    <div class="carousel-actions">
      <button @click="hanldeCarouselAction('prev')">Prev</button>
      <button @click="hanldeCarouselAction('next')">Next</button>
    </div>
  </div>
</template>

<script>
import CarouselItem from './CarouselItem.vue'

export default {
  name: 'carousel-component',
  components: {
    CarouselItem
  },
  props: {
    carouselItems: Array,
  },
  data() {
    return {
      carouselContainerWidth: 1200,
      carouselItemWidth: 400,
      activeView: 0, 
    }
  },
  methods: {
    hanldeCarouselAction(action) {
      if(action === 'next') {
        this.activeView++;
        if(this.activeView >= this.carouselItems.length - 2) {
          this.activeView = 0
        }
      } else {
        this.activeView--;
        if(this.activeView === -1) {
          this.activeView = this.carouselItems.length - 3;
        }
      }
      this.$refs['carousel-container'].scrollTo({ 
        left: this.activeView*this.carouselItemWidth,
        behavior: 'smooth'
      })
    },
  },
}
</script>

<style scoped>
.carousel-conatienr {
  max-width: 1200px;
  width: 100%;
  height: 500px;
  display: flex;
  align-items: center;
  overflow-x: auto;
}
.carousel-actions {
  display: flex;
  gap: 20px;
  margin-top: 20px;
}
</style>

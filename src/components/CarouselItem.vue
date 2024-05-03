<template>
  <div class="carousel-item">
    <img 
      :src="imgUrl"
      alt=""
    >
  </div>
</template>

<script>
export default {
  name: 'carousel-item',
  props: {
    imgUrl: String,
    width: Number,
    height: Number,
  }
}
</script>

<style scoped>
.carousel-item img {
  width: 400px;
  height: 400px;
}
</style>

<template>
  <div class="home">
    <Carousel class="carousel" #="{ currentSlide }">
      <Slide v-for="(slide, index) in carouselSlides" :key="index">
        <div v-show="currentSlide === index + 1" class="slide-info">
          <img :src="require(`../assets/${slide}.jpg`)" alt="" />
        </div>
      </Slide>
    </Carousel>
  </div>
</template>

<script>
import Carousel from "../components/Carousel.vue";
import Slide from "../components/Slide.vue";
export default {
  name: "Home",
  components: { Carousel, Slide },
  setup() {
    const carouselSlides = ["bg-1", "bg-2", "bg-3"];

    return { carouselSlides };
  },
};
</script>

<style lang="scss" scoped>
.carousel {
  position: relative;
  height: 100vh;
  max-height: 100vh;
  .slide-info {
    position: absolute;
    top: 0%;
    left: 0%;
    width: 100%;
    height: 100%;
    max-height: 100%;
    img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
  }
}
</style>

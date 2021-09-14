<template>
  <div class="carousel">
    <slot :currentSlide="currentSlide"> </slot>

    <div class="navigation">
      <span class="material-icons md-24"> chevron_left </span>
      <span class="material-icons md-24"> chevron_right </span>
    </div>
  </div>
</template>

<script>
import { ref } from "vue";
export default {
  setup() {
    const currentSlide = ref(3);

    return {
      currentSlide,
    };
  },
};
</script>

<style lang="scss" scoped>
.navigation{
    position: absolute;
}
</style>
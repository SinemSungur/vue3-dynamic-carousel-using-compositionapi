<template>
  <div class="carousel">
    <slot :currentSlide="currentSlide"> </slot>

    <div class="navigation">
      <div @click="prevSlide" class="toggle-page left">
        <span class="material-icons md-24"> chevron_left </span>
      </div>
      <div @click="nextSlide" class="toggle-page right">
        <span class="material-icons md-24"> chevron_right </span>
      </div>
    </div>

    <div class="pagination">
      <span
        @click="goToSlide(index)"
        v-for="(slide, index) in getSlideCount"
        :key="index"
        :class="{ active: index + 1 === currentSlide }"
      >
      </span>
    </div>
  </div>
</template>

<script>
import { ref, onMounted } from "vue";
export default {
  setup() {
    const currentSlide = ref(1);
    const getSlideCount = ref(null);

    const nextSlide = () => {
      if (currentSlide.value === getSlideCount.value) {
        currentSlide.value = 1;
        return;
      }
      currentSlide.value += 1;
    };

    const prevSlide = () => {
      if (currentSlide.value === 1) {
        currentSlide.value = 1;
        return;
      }
      currentSlide.value -= 1;
    };

    const goToSlide = (index) => {
      currentSlide.value = index + 1;
    };

    onMounted(() => {
      getSlideCount.value = document.querySelectorAll(".slide").length;
    });

    return {
      currentSlide,
      getSlideCount,
      nextSlide,
      prevSlide,
      goToSlide,
    };
  },
};
</script>

<style lang="scss" scoped>
.navigation {
  position: absolute;
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 0 16px;

  .toggle-page {
    display: flex;
    flex: 1;
  }

  .right {
    justify-content: flex-end;
  }

  span.material-icons {
    cursor: pointer;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: rgba(12, 66, 12, 0.74);
    border-radius: 50%;
    color: white;
    width: 40px;
    height: 40px;
  }
}

.pagination {
  position: absolute;
  bottom: 24px;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 16px;

  span {
    cursor: pointer;
    width: 20px;
    height: 20px;
    border-radius: 50%;
    background-color: #fff;
  }

  .active {
    background-color: rgb(12, 66, 12);
  }
}
</style>
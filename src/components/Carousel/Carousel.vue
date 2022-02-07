<template>
  <div class="container-carousel">
    <div class="content">
      <div class="nav-side">
        <button @click="prev" class="prev">
          <v-img class="arrowLeft" :src="imgArrowLeft" height="100px"></v-img>
        </button>
      </div>
      <div class="carousel">
        <slot></slot>
      </div>
      <div class="nav-side">
        <button @click="next" class="next">
          <v-img class="arrowRight" :src="imgArrowRight" height="100px"></v-img>
        </button>
      </div>
    </div>
  </div>
</template>
<script>
import imgArrowLeft from "../../assets/Archive/arrow_left.png";
import imgArrowRight from "../../assets/Archive/arrow_right.png";

export default {
  name: "Carousel",
  props: ["visibleSlide"],
  data: function () {
    return {
      imgArrowLeft,
      imgArrowRight,
    };
  },
  methods: {
    next: function () {
      this.$emit("next");
    },
    prev: function () {
      this.$emit("prev");
    },
  },
};
</script>

<style scoped>
.arrowRight,
.arrowLeft {
  animation: flasher 3s ease infinite;
}

.arrowRight:hover,
.arrowLeft:hover {
  animation: scaleArrow 1s infinite;
}

@keyframes flasher {
  0% {
    transform: scale(1);
  }

  50% {
    transform: scale(0.7);
  }

  100% {
    transform: scale(1);
  }
}

@keyframes scaleArrow {
  from,
  to {
    transform: scale(0.7);
  }
}

.content {
  display: flex;
}
.nav-side {
  display: flex;
  align-items: center;
  margin-top: 1.2rem;
}
.carousel {
  position: relative;
  width: 660px;
  height: 365px;
  overflow: hidden;
}

button {
  height: 100px;
  width: 100px;
  border: none;
}
button:focus,
button:hover {
  outline: none;
  cursor: pointer;
}

.next {
  right: 0;
}
.prev {
  left: 0;
}
</style>
